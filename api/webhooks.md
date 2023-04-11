---
description: Technical guidance for working with webhooks for real time event notifications
---

# Webhooks

{% hint style="warning" %}
Please note that apps and integrations developed using Webhooks for topics other than application install/uninstall will only be visible in the AppMarket to customers who have been migrated to AWS.
{% endhint %}

## Introduction

Webhooks allow you set up an endpoint in your own application to receive programmatical notifications from the Foundations Platform about changes to our customers data as it happens.

Rather than requiring you to pull information via our APIs, webhooks will **push** information to your endpoint. When one of those events is triggered (eg. a new offer is added), our Platform will send this notification as an HTTP `POST` request to the endpoint(s) you configure.

Applications that use webhooks benefit from greater efficiency, reduced costs and the ability to respond to customer driven events in real-time.

## Getting started

### Registering your app

The first step to start receiving webhooks is to register your app within our AppMarket. You don't need to list the application at this stage, but note that some [subscription topics](webhooks.md#subscription-topics) require that your app is granted an associated scope. Please see our [developer portal documentation](../developer-portal.md) for more information on submitting an app.

### Provide an endpoint

You must provide an endpoint to receive the payload the Platform will send to your app. The endpoint should:

* Be a publicly available valid URI tha
* Use the `https` scheme
* Accept `POST` requests
* Accept a request body with an `application-json` content type

{% hint style="info" %}
**You can use a third party service** to quickly get to grips with webhooks. Services like [RequestBin](https://www.requestbin.com) and [Webhook.site](https://webhook.site) instantly setup a secure URL to receive the `POST` request on your behalf and provide a UI to review what data has been sent.
{% endhint %}

### Securing your endpoint

**Legacy Method**

{% hint style="warning" %}
This method has been superseded by cryptographically signed requests. Both mechanisms will run side by side for a period of team before the legacy method described below is removed. Communication will be sent in good time before this feature becomes obsolete.
{% endhint %}

We provide your application with a simple means of verifying that requests to your webhook's endpoint are for the correct application and they originate from Reapit Foundations.

Any requests sent from our platform will include a `Reapit-Webhook-Signature`header containing a base64 representation of your application's unique client id. You should make sure that this header matches your own base64 representation of client id before processing a webhook `POST` request.

You can obtain your client id by clicking your applications details in the developer portal.

**Cryptographic Signing**

Asymmetric request signing with a public/private key pair has now been introduced and should be used over the legacy method above, which will become obsolete at some point in the future.

When a new webhook is setup in the [DeveloperPortal](https://developers.reapit.cloud/webhooks/new), a public/private key pair will be generated and stored for the app that the webhook is associated with. The keys are associated to the app, rather than the webhook itself, so if you have two webhooks for the same app, they will be signed with the same key.

As each event is prepared to be sent to your endpoint, it will be signed using the private key which is stored securely and only visible to the Platform Webhooks services. Once the message reaches you, you can verify it has come from the Reapit Platform by using the public key to check it's authenticity. To do this, complete the following steps

1. Read the `X-Signature` header from the request. This will be in the following format:\
   \
   `s:keyId:timestamp:signature`\
   \
   Full example:\
   \
   `s:98da2881-0540-48db-8ffa-45d7003f1412:1650934596:LLD5mr9ynFEvjz8dVmwO4vNmEva32ZV6TjAcPzdIDO93Jhc82EhysiQPcw9ZdlbCcCUjDsaeHZUsFEMUVKbGBg`\

2.  Retrieve the public key for your app by using one of the following methods:\
    \
    A) Use the `Public Key` option in the DeveloperPortal to retrieve the key for your app or\
    B) Make a call to `GET https://platform.reapit.cloud/webhooks/signing/{id}` where {id} is the id obtained from the X-Signature header (segment 2)\
    \
    Data from this endpoint will be returned in the following format:\


    ```
    {
      "keys": [
        {
          "kid": "08da3720-99e7-42c3-8531-58bdc8f32ecf",
          "crv": "Ed25519",
          "x": "ijz3_2n1gmlfhqAa2XH_5uYmcL2L2VHb1IqDbRDLBnU"
        }
      ]
    }
    ```

    \
    Calls to this endpoint must include the Authorization header containing a valid Bearer token. It is only possible to retrieve keys associated to the calling app when accessing the key programmatically.\

3. Decode the `x` value from the results using the Base64 URL scheme (if using method A above, this is the value displayed to you in the DeveloperPortal)
4. Combine the timestamp (segment 3) from the `X-Signature` header and the webhook message body (do not include a separation character)
5. Verify the signature (segment 4 of the `X-Signature` header) using the Ed25519 curve, using the public key and a combination of the timestamp/message body as above.

There are various packages available for many popular programming languages that allow you to easily verify signatures generated using the Ed25519 curve. Whilst this algorithm is less widely used than RSA, it is considered more secure hence it's use in the Platform. The code examples below can be used as a reference point, but should not be considered production ready code:

{% tabs %}
{% tab title="NodeJS with Express" %}
The following example uses Node JS with Express, Node Forge and Body Parser npm packages

```javascript
const express = require('express');
const crypto = require('node-forge');
const bodyParser = require('body-parser');

// Configure Express
const app = express();
const port = 5000;

// Be sure to read the raw request body, rather than
// using a JSON pre-processor/JSON.stringify()
app.use(bodyParser.raw({ inflate: true, type: 'application/json' }));

// Setup POST handler
app.post('/', function (req, res) {
    const ED25519 = forgeCrypto.pki.ed25519;

    // Read the X-Signature header
    const sigHeader = req.header("x-signature");
    const sigParts = sigHeader.split(":");
    
    // Read the signature segments
    const keyId = sigParts[1];
    const timestamp = sigParts[2];
    const signature = sigParts[3];

    // The message to verify is a concatenation of the timestamp (from the X-Signature header)
    // and the raw request body, with no delimiting characters
    const msgToVerify = `${timestamp}${req.body.toString()}`;

    // Retrieve the public key from the respective endpoint
    // or store OUTSIDE your code. This is an example only
    const publicKeyBase64 = "ijz3_2n1gmlfhqAa2XH_5uYmcL2L2VHb1IqDbRDLBnU";

    // Verify the signature
    const verified = ED25519.verify({
        message: msgToVerify,
        encoding: "utf8",
        signature: Buffer.from(signature, "base64"),
        publicKey: Buffer.from(publicKeyBase64, "base64")
    });

    if (verified) {
        console.log("Signature is valid");

        // Continue to process webhook
    }
    else {
        console.log("Signature is invalid");
    }

    res.send("Webhook processing complete");
});

// Start the server
app.listen(port, () => {
    console.log(`Now listening on port ${port}`);
}); 
```
{% endtab %}

{% tab title=".NET Core" %}
The following example uses C# .NET Core with the BouncyCastle.NETCore NuGet package\


```csharp
using System;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.WebUtilities;
using Microsoft.Extensions.Logging;
using Microsoft.Extensions.Primitives;
using Org.BouncyCastle.Crypto.Parameters;
using Org.BouncyCastle.Crypto.Signers;

namespace WebhookHandlerExample.Controllers
{
    [ApiController]
    [Route("/")]
    public class WebhookHandlerController : ControllerBase
    {
        private readonly ILogger<WebhookHandlerController> logger;

        public WebhookHandlerController(ILogger<WebhookHandlerController> logger)
        {
            this.logger = logger ?? throw new ArgumentNullException(nameof(logger));
        }

        [HttpPost]
        public async Task<IActionResult> PostHandler([FromBody] dynamic body)
        {
            if (Request.Headers.TryGetValue("X-Signature", out StringValues signatureHeader))
            {
                string[] sigParts = signatureHeader.First().Split(":");

                // Read the signature segments
                var keyId = sigParts[1];
                var timestamp = sigParts[2];
                var signature = sigParts[3];

                // The message to verify is a concatenation of the timestamp (from the X-Signature header)
                // and the raw request body, with no delimiting characters
                var msgToVerify = $"{timestamp}{body}";

                // Retrieve the public key from the respective endpoint
                // or store OUTSIDE your code. This is an example only
                var publicKeyBase64 = "ijz3_2n1gmlfhqAa2XH_5uYmcL2L2VHb1IqDbRDLBnU";

                CryptographyService cryptoService = new CryptographyService();

                bool verified = cryptoService.VerifySignature(msgToVerify, publicKeyBase64, signature);

                if (verified)
                {
                    this.logger.LogInformation("Signature is valid");

                    // Continue to process webhook
                }
                else
                {
                    this.logger.LogError("Signature is invalid");
                }

                return Ok("Webhook processing complete");
            }

            return Ok("No signature was found in the message header collection");
          
        }
    }

    internal class CryptographyService
    {
        /// <summary>
        /// Verifies the specified signature against the public key supplied
        /// </summary>
        /// <param name="message">The message used to generate the isngautre</param>
        /// <param name="encodedPublicKey">The encoded public key</param>
        /// <param name="signature">The signature to verify</param>
        /// <returns>True if the signature is valid, else false</returns>
        public bool VerifySignature(string message, string encodedPublicKey, string signature)
        {
            byte[] decodedPublicKey = WebEncoders.Base64UrlDecode(encodedPublicKey);
            byte[] messageBytes = Encoding.ASCII.GetBytes(message);
            byte[] signatureBytes = WebEncoders.Base64UrlDecode(signature);

            // Setup validator using Ed25519 curve
            var keyParams = new Ed25519PublicKeyParameters(decodedPublicKey, 0);

            var validator = new Ed25519Signer();
            validator.Init(false, keyParams);
            validator.BlockUpdate(messageBytes, 0, messageBytes.Length);

            bool isValidSignature = validator.VerifySignature(signatureBytes);

            return isValidSignature;
        }
    }
}
```
{% endtab %}
{% endtabs %}



## Managing webhooks in the user interface

We offer a user interface to allow you to manage webhooks in a simple and straightforward way. You're able to create, update and remove webhooks for all of your applications in a single place.

![](<../.gitbook/assets/Webhook 1.png>)

### Creating a webhook

First, select the application that you want to create a webhook for. You'll then be given the option to 'Add New Webhook', as above. The modal below allows you to [input the endpoint](webhooks.md#provide-an-endpoint) where information should be pushed.

![](<../.gitbook/assets/Webhook 2.png>)

Our webhooks system is designed to flexibly work with how your application is built and deployed. If you wish, you can set up a single endpoint to catch all **topics** for all **customers**. Alternatively, you may wish to set up a different webhook subscription per topic or per customer.

### Subscribe to topics

As part of creating a new webhook, you need to specify which of the available **topics** (type of event) that your application needs to respond to. If any application makes a change to a customers data that corresponds to a topic that your app is listening for, you'll receive a notification to describe the event.

Data changes from any application will result in a notification being sent to your endpoint(s), including:

* [Reapit Agency Cloud](https://www.reapit.com/agency-cloud)
* [Reapit Property Cloud](https://www.reapit.com/property-cloud/)
* Any other Reapit AppMarket application

For example, if a new offer is added in our AgencyCloud CRM and your application has a webhook set up containing the **offers.created** topic, your endpoint will be sent a specific, descriptive payload containing the full details of the new offer.

{% hint style="success" %}
**We recommend** registering your webhooks in an inactive state and using the **Ping** function. This allows you to test that your endpoint works as expected before opting to receive live customer updates.
{% endhint %}

We currently support the following topics, but this will increase over time. Please note that you will only be presented topics if your application has been assigned the associated scope.

### Available topics

> Webhook payload types are available from `@reapit/foundations-ts-definitions` [see here for more info](https://foundations-documentation.reapit.cloud/app-development/foundations-ts-defintions#webhook-types)

If you have a requirement to target very specific events in a customer's system, you may wish to look at [building your own event filter](webhooks.md#building-event-filters) to build on the default topic capability.

| Topic                                     | Description                                                                                                                                                                                                                                                                                     | Required scopes       |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| **application.install**                   | Occurs when a customer installs an application in the AppMarket                                                                                                                                                                                                                                 | None                  |
| **application.uninstall**                 | Occurs when a customer uninstalls an application in the AppMarket                                                                                                                                                                                                                               | None                  |
| **applicants.created**                    | Occurs when a new [applicant](https://foundations-documentation.reapit.cloud/platform-glossary#applicant) is created                                                                                                                                                                            | `applicants.read`     |
| **applicants.modified**                   | Occurs when an existing [applicant](https://foundations-documentation.reapit.cloud/platform-glossary#applicant) is modified, or any of the associated [contacts](https://foundations-documentation.reapit.cloud/platform-glossary#contact) are modified                                         | `applicants.read`     |
| **appointments.cancelled**                | Occurs when a new [appointment ](../platform-glossary.md#appointment)is created as cancelled, or an existing appointment is cancelled                                                                                                                                                           | `appointments.read`   |
| **appointments.confirmed**                | Occurs when an [appointment ](../platform-glossary.md#appointment)is created or modified and all required parties have confirmed attendance                                                                                                                                                     | `appointments.read`   |
| **appointments.created**                  | Occurs when a new [appointment](https://foundations-documentation.reapit.cloud/platform-glossary#appointment) is created                                                                                                                                                                        | `appointments.read`   |
| **appointments.modified**                 | Occurs when an existing [appointment](https://foundations-documentation.reapit.cloud/platform-glossary#appointment) is modified                                                                                                                                                                 | `appointments.read`   |
| **companies.created**                     | Occurs when a new [company](https://foundations-documentation.reapit.cloud/platform-glossary#company) is created                                                                                                                                                                                | `companies.read`      |
| **companies.modified**                    | Occurs when an existing [company](https://foundations-documentation.reapit.cloud/platform-glossary#company) is modified                                                                                                                                                                         | `companies.read`      |
| **contacts.created**                      | Occurs when a new [contact](https://foundations-documentation.reapit.cloud/platform-glossary#contact) is created                                                                                                                                                                                | `contacts.read`       |
| **contacts.modified**                     | Occurs when an existing [contact](https://foundations-documentation.reapit.cloud/platform-glossary#contact) is modified                                                                                                                                                                         | `contacts.read`       |
| **contacts.optedout**                     | Occurs when a new [contact ](../platform-glossary.md#contact)is created with marketing consent set to deny, or the marketing consent state of an existing contact is changed to deny                                                                                                            | `contacts.read`       |
| **conveyancing.modified**                 | Occurs when an existing [conveyancing ](../platform-glossary.md#conveyancing)(sales progression) entity is modified                                                                                                                                                                             | `conveyancing.read`   |
| **documents.created**                     | Occurs when a new [document ](../platform-glossary.md#document)is created                                                                                                                                                                                                                       | `documents.read`      |
| **documents.modified**                    | Occurs when an existing [document](../platform-glossary.md#document) is modified                                                                                                                                                                                                                | `documents.read`      |
| **enquiries.accepted**                    | Occurs when an existing [enquiry](../platform-glossary.md#enquiry) has a status change to added                                                                                                                                                                                                 | `enquiries.read`      |
| **enquiries.created**                     | Occurs when a new [enquiry ](../platform-glossary.md#enquiry)is created                                                                                                                                                                                                                         | `enquiries.read`      |
| **enquiries.modified**                    | Occurs when an existing [enquiry](../platform-glossary.md#enquiry) is modified                                                                                                                                                                                                                  | `enquiries.read`      |
| **enquiries.rejected**                    | Occurs when an existing [enquiry](../platform-glossary.md#enquiry) has a status change to rejected                                                                                                                                                                                              | `enquiries.read`      |
| **identitychecks.created**                | Occurs when a new [identity check](https://foundations-documentation.reapit.cloud/platform-glossary#identity-check) is created against an existing [contact](https://foundations-documentation.reapit.cloud/platform-glossary#contact)                                                          | `identitychecks.read` |
| **identitychecks.modified**               | Occurs when an existing [identity check](https://foundations-documentation.reapit.cloud/platform-glossary#identity-check) is modified                                                                                                                                                           | `identitychecks.read` |
| **landlords.created**                     | Occurs when a new [landlord](https://foundations-documentation.reapit.cloud/platform-glossary#landlord) is created                                                                                                                                                                              | `landlords.read`      |
| **landlords.modified**                    | Occurs when an existing [landlord](https://foundations-documentation.reapit.cloud/platform-glossary#landlord) is modified, or any of the associated [contacts](https://foundations-documentation.reapit.cloud/platform-glossary#contact) are modified                                           | `landlords.read`      |
| **offers.accepted**                       | Occurs when a new [offer ](../platform-glossary.md#offer)is created in an accepted state, or the status of an existing offer is changed to accepted                                                                                                                                             | `offers.read`         |
| **offers.created**                        | Occurs when a new [offer](https://foundations-documentation.reapit.cloud/platform-glossary#offer) is created                                                                                                                                                                                    | `offers.read`         |
| **offers.modified**                       | Occurs when an existing [offer](https://foundations-documentation.reapit.cloud/platform-glossary#offer) is modified                                                                                                                                                                             | `offers.read`         |
| **offers.rejected**                       | Occurs when a new [offer ](../platform-glossary.md#offer)is created in a withdrawn state, or the status of an existing offer is changed to withdrawn                                                                                                                                            | `offers.read`         |
| **offers.withdrawn**                      | Occurs when a new [offer ](../platform-glossary.md#offer)is created in a rejected state, or the status of an existing offer is changed to rejected                                                                                                                                              | `offers.read`         |
| **offices.created**                       | Occurs when a new [office](https://foundations-documentation.reapit.cloud/platform-glossary#office) is created                                                                                                                                                                                  | `offices.read`        |
| **offices.modified**                      | Occurs when an existing [office](https://foundations-documentation.reapit.cloud/platform-glossary#office) is modified                                                                                                                                                                           | `offices.read`        |
| **properties.created**                    | Occurs when a new [property](https://foundations-documentation.reapit.cloud/platform-glossary#property) is created                                                                                                                                                                              | `properties.read`     |
| **properties.modified**                   | Occurs when an existing [property](https://foundations-documentation.reapit.cloud/platform-glossary#property) is modified                                                                                                                                                                       | `properties.read`     |
| **properties.selling.askingpricechanged** | Occurs when the asking price of an existing sales [property](../platform-glossary.md#property) is changed                                                                                                                                                                                       | `properties.read`     |
| **properties.selling.completed**          | Occurs when a new sales [property ](../platform-glossary.md#property)is created with a status of completed, or an existing sales property's status is changed to completed                                                                                                                      | `properties.read`     |
| **properties.selling.exchanged**          | Occurs when a new sales [property ](../platform-glossary.md#property)is created with a status of exchanged, or an existing sales property's status is changed to exchanged                                                                                                                      | `properties.read`     |
| **properties.selling.withdrawn**          | Occurs when a new sales [property ](../platform-glossary.md#property)is created with a status of withdrawn, or an existing sales property's status is changed to withdrawn                                                                                                                      | `properties.read`     |
| **properties.selling.instructed**         | Occurs when a new sales [property ](../platform-glossary.md#property)is created with a status of forSale or forSaleUnavailable, or an existing sales property's status is changed to forSale or forSaleUnavailable, and the previous status was one of preAppraisal, valuation or paidValuation | `properties.read`     |
| **properties.selling.lostinstruction**    | Occurs when a new sales [property ](../platform-glossary.md#property)is created in a lost instruction state, or an existing sales property's lost instruction data has been set for the first time                                                                                              | `properties.read`     |
| **properties.selling.underoffer**         | Occurs when a new sales [property ](../platform-glossary.md#property)is created with a status of underOffer or underOfferUnavailable, or an existing sales property's status is changed to underOffer or underOfferUnavailable                                                                  | `properties.read`     |
| **propertyimages.created**                | Occurs when a new [property image](../platform-glossary.md#property-image) has been created                                                                                                                                                                                                     | `properties.read`     |
| **propertyimages.modified**               | Occurs when an existing [property image](../platform-glossary.md#property-image) has been modified                                                                                                                                                                                              | `properties.read`     |
| **referrals.created**                     | Occurs when a new [referral ](../platform-glossary.md#referral)has been created                                                                                                                                                                                                                 | `referrals.read`      |
| **referrals.modified**                    | Occurs when an existing [referral ](../platform-glossary.md#referral)has been modified                                                                                                                                                                                                          | `referrals.read`      |
| **tenancies.created**                     | Occurs when a new [tenancy ](../platform-glossary.md#tenancy)has been created                                                                                                                                                                                                                   | `tenancies.read`      |
| **tenancies.modified**                    | Occurs when an existing [tenancy ](../platform-glossary.md#tenancy)has been modified                                                                                                                                                                                                            | `tenancies.write`     |
| **vendors.created**                       | Occurs when [vendor](https://foundations-documentation.reapit.cloud/platform-glossary#vendor) information has been associated with a sales property for the first time                                                                                                                          | `vendors.read`        |
| **vendors.modified**                      | Occurs when vendor information is modified or any of the associated [vendor](https://foundations-documentation.reapit.cloud/platform-glossary#vendor) contacts are modified                                                                                                                     | `vendors.read`        |
| **worksorders.cancelled**                 | Occurs when a new [works order](../platform-glossary.md#works-order) is created in a cancelled state, or the status of an existing works order is changed to cancelled                                                                                                                          | `worksorders.read`    |
| **worksorders.complete**                  | Occurs when a new [works order](../platform-glossary.md#works-order) is created in a complete state, or the status of an existing works order is changed to complete                                                                                                                            | `worksorders.read`    |
| **worksorders.modified**                  | Occurs when an existing [works order](https://foundations-documentation.reapit.cloud/platform-glossary#works-order) is modified                                                                                                                                                                 | `worksorders.read`    |
| **worksorders.raised**                    | Occurs when a new [works order](../platform-glossary.md#works-order) is created in a raised state, or the status of an existing works order is changed to raised                                                                                                                                | `worksorders.read`    |

### Subscribe to customers

You must configure the customer(s) that your webhook will respond to events for. Only customers who have installed your listed application will appear here.

* Specify one or more customers to receive only event originating from those customers
* Specify 'SBOX' to listen to events triggered from our sandbox (useful for testing)
* Leave this field blank to respond to events for all customers who have installed your application. You will immediately receive events for new customers who install your application without any configuration change required. This does not include sandbox events.

### Building event filters

There are several scenarios where the list of available topics results in a large number of irrelevant events being submitted to your endpoint. In response to a high frequency of requests of additional topics, or more granular filtering capabilities, it is possible to attach one or more event schema filters to your webhooks. This is an advanced feature that allows you to build on top of the default topic availability and target specific events. Please note that this is still in beta testing and not generally available

Webhook event filters are based on the [JSON Schema specification](https://json-schema.org/) and, put simply, a schema is used to validate the content of an event from our customer's systems which will only be sent to your endpoint in the event that validation is successful. This mechanism gives you the ability to define specific rules, for example if you want to target specific appointment types when listening to appointments.created and/or appointments.modified topics. An event filter is tied to a single specific topic so it is not necessary to check the topic id as part of the filter, however if can be good practice to include this, as is shown in the Starter Template. The tabs below provide some examples of event filters that can be used as a starting point.

It is possible to stack event filters to keep each individual filter quite lightweight. For example, if you wanted to build a filter that ensured that an appointment was of valuation type AND associated to one of a defined list of negotiator ids, this could be achieved by creating two separate filters (one for each rule) or a single filter with both rules applied. All filters must pass validation for the event to be sent to your endpoint

{% tabs %}
{% tab title="Starter Template" %}
```javascript
{
    "$schema": "https://json-schema.org/draft/2019-09/schema",
    "description": "Filter Starter Template",
    "type": "object",
    "properties": {
        "new": {
        },
        "topicId": {
            "type": "string",
            "oneOf": [
                {
                    "pattern": "appointments.modified"
                },
                {
                    "pattern": "appointments.created"
                }
            ]
        }
    },
    "required": [
        "topicId",
        "new"
    ]
}
```
{% endtab %}

{% tab title="Specific Appointment Types" %}
The following schema will target appointments with a typeId of VL (valuation). Note that whilst the topicId validation is done against both appointments.modified AND appointments.created events, the filter can only be applied to a single topic, and so would need to be configured twice, once for each topic

```javascript
{
    "$schema": "https://json-schema.org/draft/2019-09/schema",
    "description": "Valuation Appointments",
    "type": "object",
    "properties": {
        "new": {
            "type": "object",
            "properties": {
                "typeId": {
                    "type": "string",
                    "oneOf": [
                        {
                            "pattern": "VL"
                        }
                    ]
                }
            },
            "required": [
                "typeId"
            ]
        },
        "topicId": {
            "type": "string",
            "oneOf": [
                {
                    "pattern": "appointments.modified"
                },
                {
                    "pattern": "appointments.created"
                }
            ]
        }
    },
    "required": [
        "topicId"
    ]
}
```
{% endtab %}

{% tab title="New Instructions Above Price" %}
The following schema will target modified properties that have just been instructed with an asking price of 500,000 or greater. This might be used to specifically target high value properties for a more luxury property portal.

```javascript
{
    "$schema": "https://json-schema.org/draft/2019-09/schema",
    "description": "Instructions above 500,000",
    "type": "object",
    "properties": {
        "new": {
            "type": "object",
            "properties": {
                "selling": {
                    "type": "object",
                    "properties": {
                        "price": {
                            "type": "number",
                            "minimum": 500000
                        },
                        "status": {
                            "type": "string",
                            "oneOf": [
                                {
                                    "pattern": "^forSale.*"
                                }
                            ]
                        }
                    },
                    "required": [
                        "price",
                        "status"
                    ]
                }
            },
            "required": [
                "selling"
            ]
        },
        "diff": {
            "type": "object",
            "properties": {
                "selling": {
                    "type": "object",
                    "properties": {
                        "price": {
                            "type": "array",
                            "items": [
                                {
                                    "type": "number"
                                },
                                {
                                    "type": "number",
                                    "minimum": 500000
                                }
                            ]
                        },
                        "status": {
                            "type": "array",
                            "items": [
                                {
                                    "type": "string"
                                },
                                {
                                    "type": "string",
                                    "oneOf": [
                                        {
                                            "pattern": "^forSale.*"
                                        }
                                    ]
                                }
                            ]
                        }
                    },
                    "required": [
                        "status"
                    ]
                }
            },
            "required": [
                "selling"
            ]
        }
    },
    "anyOf": [
        {
            "required": [
                "new"
            ]
        },
        {
            "required": [
                "new",
                "diff"
            ]
        }
    ]
}
```
{% endtab %}

{% tab title="Changes to Latitude or Longitude" %}
The following schema detects changes to either the latitude or longitude on a property resource. This might used by systems that generate map or geospatial data based on property information in a customers' database

```
{
  "$schema": "https://json-schema.org/draft/2019-09/schema",
  "description": "Changes to latitude or longitude",
  "type": "object",
  "properties": {
    "diff": {
      "type": "object",
      "properties": {
        "address": {
          "type": "object",
          "properties": {
            "geolocation": {
              "type": "object",
              "properties": {
                "latitude": { "type": "array" },
                "longitude": { "type": "array" }
              },
              "anyOf": [
                { "required": [ "latitude" ] },
                { "required": [ "longitude"] }
              ]
            }
          },
          "required": [ "geolocation" ]
        }
      },
      "required": [ "address" ]
    }
  },
  "required": [ "diff" ]
}
```
{% endtab %}
{% endtabs %}

Once your event schema has been built, post it to the appropriate resthooks endpoint. If you wish to test your filter against a given event once it has been saved, the test endpoint can be used to validate your filter against the specified event payload, which you can take from the _Ping_ webhooks function, or by using a real event already being received by your endpoint

{% hint style="warning" %}
When using event filters, it is important to keep in mind that certain events will no longer be sent to you. As the diff is generated for each specific event (rather than being based on the last version you received as a consumer) you will likely encounter scenarios where it is necessary to use the `new` object to understand all changes to a resource since the last time you received an update
{% endhint %}

### Optional webhook behaviour

By default, webhooks will not be emitted when only the entity's eTag and modified timestamp has changed. If you would prefer to receive notifications in this situation, please use the **Ignore notifications where only the eTag has been modified** toggle option when configuring your webhook

{% hint style="info" %}
**To test your webhook end to end with real data**, use the sandbox database available to you in the Developer Portal. Set up a webhook to listen to 'SBOX' events and make changes to the sandbox using our APIs or Interactive API Explorer.
{% endhint %}

## Managing webhooks using REST API

We also provide a REST API to allow webhooks to be programmatically created for the customer/application that your access token has been issued on behalf of. Please see the swagger documentation for technical details on how to integrate.

## Receiving events

### Example payload

We use a consistent schema to describe any event that we broadcast in a descriptive and self-contained way. The notifications we emit indicate that an **event has happened** - but additionally and where appropriate - we provide details about the actual data change that has occurred. This allows your application to ascertain **granular details about the event** without needing additional API calls.

Below is an example of what a **contacts.modified** webhook event might look like

```
{
  "SendAttempts": 1,
  "eventId": "9e7e4181-6210-49ea-abf5-d5ce16d23647",
  "entityId": "RPT20000029",
  "customerId": "webhook-test",
  "eventTime": "2020-05-13T09:33:16.8811358Z",
  "topicId": "contacts.modified",
  "new": {
    "id": "RPT20000029",
    "created": "2020-05-13T09:32:24Z",
    "modified": "2020-05-13T09:33:10Z",
    "title": "Mr",
    "forename": "John",
    "surname": "Smith",
    "dateOfBirth": null,
    "active": true,
    "marketingConsent": "notAsked",
    "identityCheck": "unchecked",
    "source": null,
    "homePhone": null,
    "workPhone": null,
    "mobilePhone": "07123 456789",
    "email": "john.smith@reapitestates.net",
    "primaryAddress": {
      "type": "primary",
      "buildingName": "",
      "buildingNumber": "12",
      "line1": "High Street",
      "line2": "Clacton-On-Sea",
      "line3": "Essex",
      "line4": "",
      "postcode": "CO15 1AE",
      "countryId": "GB"
    },
    "secondaryAddress": null,
    "workAddress": null,
    "officeIds": ["RPT"],
    "negotiatorIds": ["RPT"],
    "_eTag": "\"4DF107A6EB05D792EEAFDF1432F6E275\""
  },
  "old": {
    "id": "RPT20000029",
    "created": "2020-05-13T09:32:24Z",
    "modified": null,
    "title": "Mr",
    "forename": "John",
    "surname": "Smith",
    "dateOfBirth": null,
    "active": true,
    "marketingConsent": "notAsked",
    "identityCheck": "unchecked",
    "source": null,
    "homePhone": null,
    "workPhone": null,
    "mobilePhone": null,
    "email": "john.smith@reapitestates.net",
    "primaryAddress": {
      "type": "primary",
      "buildingName": "",
      "buildingNumber": "1",
      "line1": "High Street",
      "line2": "Clacton-On-Sea",
      "line3": "Essex",
      "line4": "",
      "postcode": "CO15 1AE",
      "countryId": "GB"
    },
    "secondaryAddress": null,
    "workAddress": null,
    "officeIds": ["RPT"],
    "negotiatorIds": ["RPT"],
    "_eTag": "\"65D680519E9762519D203891A694B85B\""
  },
  "diff": {
    "modified": [null, "2020-05-13T09:33:10Z"],
    "mobilePhone": [null, "07123 456789"],
    "primaryAddress": {
      "buildingNumber": ["1", "12"]
    },
    "_eTag": ["\"65D680519E9762519D203891A694B85B\"", "\"4DF107A6EB05D792EEAFDF1432F6E275\""]
  }
}
```

### Payload schema

The following table outlines the purpose of each property in the payload

| Property       | Description                                                                                                                                                                                                                                          |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `SendAttempts` | The number of attempts it took to successfully deliver the message. Please see [failure handling](webhooks.md#failure-handling-and-exponential-backoff) section regarding retry policy with exponential backoff                                      |
| `eventId`      | A unique identifier for the event. Some events will trigger multiple notifications (for example if the name of a contact changes, you'll also receive a notification for each of their associated roles. These will share the same event identifier) |
| `entityId`     | If applicable, the unique identifier of the entity that the event is associated to. Please note that by itself this is _not_ a globally unique identifier. Uniqueness can be achieved by also including the `customerId`                             |
| `customerId`   | The unique identifier of the Reapit customer whom the data event is associated with                                                                                                                                                                  |
| `eventTime`    | The UTC date and time the event was emitted from our Platform                                                                                                                                                                                        |
| `topicId`      | The topic the event is associated with. See the list outlined in the [Subscription topics ](webhooks.md#subscription-topics)section                                                                                                                  |
| `new`          | The new version of the entity, if applicable - this property will be null if a user has deleted or archived the entity.                                                                                                                              |
| `old`          | The old version of the entity, if applicable - this property will be null in the event of a _.created_ event.                                                                                                                                        |
| `diff`         | A diff outlining the exact changes between the new/old payloads. The diff is only populated for _.modified_ events where both `new`/`old` representations of the entity are available.                                                               |

The content of the `new`, `old`, and `diff` properties in the webhook event payload use the same schema that the respective API endpoints use. For example, if the payload received has a `topicId` of `contacts.modified` then these payload properties will use the same schema as the `GET /contacts` API endpoints

### Testing

When you have an endpoint configured, you can test it by using the **Ping** function. This will send a test event with an example payload to the URL stored against the webhook for the selected topic. You will only be able to select topics that are applicable to the webhook being tested.

![](<../.gitbook/assets/Webhook 3.png>)

The user interface will show a success or failure based on the response back from the endpoint. In the event of a success response, you will have received the example payload to the configured endpoint.

We also recommend testing your webhooks using our sandbox environment before applying them to customers.

{% hint style="info" %}
**All events submitted from the Ping function** use example data and will have a `customerId` of 'webhook-test' and an `entityId` of '9e7e4181-6210-49ea-abf5-d5ce16d23647'. Receiving services need to handle this appropriately and not treat the payload as production event
{% endhint %}

### Failure handling and exponential backoff

As with any integrated system, there's always a possibility of the endpoint we try to send a webhook notification to being unavailable at certain periods. For this reason a retry policy with exponential backoff has been built so that small periods of downtime do not result in messages not being delivered to you.

Where we fail to deliver a webhook on the first attempt, we will retry up to 5 times at the following intervals (6 delivery attempts in total):

| Delivery attempt | Delivery delay (seconds/minutes)                                                                                     |
| ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| 2                | 60s (1m) after the first delivery attempt                                                                            |
| 3                | 120s (2m) after the second delivery attempt                                                                          |
| 4                | 300s (5m) after the third delivery attempt                                                                           |
| 5                | 600s (10m) after the fourth delivery attempt                                                                         |
| 6                | 900s (15m) after the fifth delivery attempt. No more attempts to deliver the message will be made after this attempt |

The number of attempts it took to deliver the message is available in the payload. See the [Example payload](webhooks.md#example-payload) for more information.

Please note that we will not retry to send messages that were not delivered on the first attempt in the following scenarios:

* Where the webhook event is associated to Sandbox data
* Where the response code we received from your configured endpoint was 4XX. This is indicative of a misconfigured webhook or authentication problem on the target system

## Additional information

* Events are generated in near real-time and though extremely unlikely, we do not guarantee that you will only get a single notification for an event.
* We do not guarantee that webhooks will be sent in the exact order that the events occurred. You can use the `eventTime` to determine when each event occurred.
* Webhooks originated requests contribute to developer analytics and billing in the same way as regular API requests do

{% hint style="info" %}
**We will be introducing** an automatic retry policy with exponential backoff as [an additional feature in due course](https://github.com/reapit/foundations/issues/1299)
{% endhint %}
