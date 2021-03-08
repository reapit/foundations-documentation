---
description: Technical guidance for working with webhooks for real time event notifications
---

# Webhooks

{% hint style="warning" %}
Please note that apps and integrations developed using Webhooks for topics other than application install/uninstall will only be visible in the Marketplace to customers who have been migrated to AWS. 
{% endhint %}

## Introduction

Webhooks allow you set up an endpoint in your own application to receive programmatical notifications from the Foundations Platform about changes to our customers data as it happens. 

Rather than requiring you to pull information via our APIs, webhooks will **push** information to your endpoint. When one of those events is triggered \(eg. a new offer is added\), our Platform will send this notification as an HTTP `POST` request to the endpoint\(s\) you configure.

Applications that use webhooks benefit from greater efficiency, reduced costs and the ability to respond to customer driven events in real-time.

## Getting started

### Registering your app

The first step to start receiving webhooks is to register your app within our Marketplace. You don't need to list the application at this stage, but note that some [subscription topics](webhooks.md#subscription-topics) require that your app is granted an associated scope. Please see our [developer portal documentation](../developer-portal.md) for more information on submitting an app.

### Provide an endpoint

You must provide an endpoint to receive the payload the Platform will send to your app. The endpoint should:

* Be a publicly available valid URI
* Use the `https` scheme
* Accept `POST` requests
* Accept a request body with an `application-json` content type

{% hint style="info" %}
**You can use a third party service** to quickly get to grips with webhooks. Services like [RequestBin](https://www.requestbin.com/) and [Webhook.site](https://webhook.site/) instantly setup a secure URL to receive the `POST` request on your behalf and provide a UI to review what data has been sent.
{% endhint %}

### Securing your endpoint

We provide your application with a simple means of verifying that requests to your webhook's endpoint are for the correct application and they originate from Reapit Foundations. 

Any requests sent from our platform will include a `Reapit-Webhook-Signature`header containing a base64 representation of your application's unique client id. You should make sure that this header matches your own base64 representation of client id before processing a webhook `POST`  request.

You can obtain your client id by clicking your applications details in the developer portal. 

## Managing webhooks

We offer a user interface to allow you to manage webhooks in a simple and straightforward way. You're able to create, update and remove webhooks for all of your applications in a single place. 

![](../.gitbook/assets/image%20%2833%29.png)

### Creating a webhook

First, select the application that you want to create a webhook for. You'll then be given the option to 'Add New Webhook', as above. The modal below allows you to [input the endpoint](webhooks.md#provide-an-endpoint) where information should be pushed.

![Unchecking the &apos;Active&apos; flag will stop notifications from being sent](../.gitbook/assets/image%20%2834%29.png)

Our webhooks system is designed to flexibly work with how your application is built and deployed. If you wish, you can set up a single endpoint to catch all **topics** for all **customers**. Alternatively, you may wish to set up a different webhook subscription per topic or per customer.

### Subscribe to topics

As part of creating a new webhook, you need to specify which of the available **topics** \(type of event\) that your application needs to respond to. If any application makes a change to a customers data that corresponds to a topic that your app is listening for, you'll receive a notification to describe the event.

Data changes from any application will result in a notification being sent to your endpoint\(s\), including:

* [Reapit Agency Cloud](https://www.reapit.com/agency-cloud)
* [Reapit Property Cloud](https://www.reapit.com/property-cloud/)
* Any other Reapit Marketplace application

For example, if a new offer is added in our Agency Cloud CRM and your application has a webhook set up containing the **offers.created** topic, your endpoint will be sent a specific, descriptive payload containing the full details of the new offer.

{% hint style="success" %}
**We recommend** registering your webhooks in an inactive state and using the **Ping** function. This allows you to test that your endpoint works as expected before opting to receive live customer updates. 
{% endhint %}

We currently support the following topics, but this will increase over time. Please note that you will only be  presented topics if your application has been assigned the associated scope.

### Available topics

| Topic | Description | Required scopes |
| :--- | :--- | :--- |
| **application.install** | Occurs when a customer installs an application in the Marketplace | None |
| **application.uninstall** | Occurs when a customer uninstalls an application in the Marketplace | None |
| **applicants.created** | Occurs when a new [applicant](https://foundations-documentation.reapit.cloud/platform-glossary#applicant) is created | `applicants.read` |
| **applicants.modified** | Occurs when an existing [applicant](https://foundations-documentation.reapit.cloud/platform-glossary#applicant) is modified, or any of the associated [contacts](https://foundations-documentation.reapit.cloud/platform-glossary#contact) are modified | `applicants.read` |
| **appointments.created** | Occurs when a new [appointment](https://foundations-documentation.reapit.cloud/platform-glossary#appointment) is created | `appointments.read` |
| **appointments.modified** | Occurs when an existing [appointment](https://foundations-documentation.reapit.cloud/platform-glossary#appointment) is modified | `appointments.read` |
| **companies.created** | Occurs when a new [company](https://foundations-documentation.reapit.cloud/platform-glossary#company) is created | `companies.read` |
| **companies.modified** | Occurs when an existing [company](https://foundations-documentation.reapit.cloud/platform-glossary#company) is modified | `companies.read` |
| **contacts.created** | Occurs when a new [contact](https://foundations-documentation.reapit.cloud/platform-glossary#contact) is created | `contacts.read` |
| **contacts.modified** | Occurs when an existing [contact](https://foundations-documentation.reapit.cloud/platform-glossary#contact) is modified | `contacts.read` |
| **identitychecks.created** | Occurs when a new [identity check](https://foundations-documentation.reapit.cloud/platform-glossary#identity-check) is created against an existing [contact](https://foundations-documentation.reapit.cloud/platform-glossary#contact) | `identitychecks.read` |
| **identitychecks.modified** | Occurs when an existing [identity check](https://foundations-documentation.reapit.cloud/platform-glossary#identity-check) is modified | `identitychecks.read` |
| **landlords.created** | Occurs when a new [landlord](https://foundations-documentation.reapit.cloud/platform-glossary#landlord) is created | `landlords.read` |
| **landlords.modified** | Occurs when an existing [landlord](https://foundations-documentation.reapit.cloud/platform-glossary#landlord) is modified, or any of the associated [contacts](https://foundations-documentation.reapit.cloud/platform-glossary#contact) are modified | `landlords.read` |
| **offers.created** | Occurs when a new [offer](https://foundations-documentation.reapit.cloud/platform-glossary#offer) is created | `offers.read` |
| **offers.modified** | Occurs when an existing [offer](https://foundations-documentation.reapit.cloud/platform-glossary#offer) is modified | `offers.read` |
| **properties.created** | Occurs when a new [property](https://foundations-documentation.reapit.cloud/platform-glossary#property) is created | `properties.read` |
| **properties.modified** | Occurs when an existing [property](https://foundations-documentation.reapit.cloud/platform-glossary#property) is modified | `properties.read` |
| **propertyimages.created** | Occurs when a new [property image](https://foundations-documentation.reapit.cloud/platform-glossary#property-image) is created | `propertyimages.read` |
| **propertyimages.modified** | Occurs when an existing [property image](https://foundations-documentation.reapit.cloud/platform-glossary#property-image) is modified or re-ordered | `propertyimages.read` |
| **tasks.created** | Occurs when a new [task](https://foundations-documentation.reapit.cloud/platform-glossary#task) is created | `tasks.read` |
| **tasks.modified** | Occurs when an existing [task](https://foundations-documentation.reapit.cloud/platform-glossary#task) is modified | `tasks.read` |
| **tenancies.created** | Occurs when a new [tenancy](https://foundations-documentation.reapit.cloud/platform-glossary#tenancy) is created | `tenancies.read` |
| **tenancies.modified** | Occurs when an existing [tenancy](https://foundations-documentation.reapit.cloud/platform-glossary#tenancy) is modified, or any of the associated contacts are modified | `tenancies.read` |
| **vendors.created** | Occurs when [vendor](https://foundations-documentation.reapit.cloud/platform-glossary#vendor) information has been associated with a sales property for the first time | `vendors.read` |
| **vendors.modified** | Occurs when vendor information is modified or any of the associated [vendor](https://foundations-documentation.reapit.cloud/platform-glossary#vendor) contacts are modified | `vendors.read` |
| **worksorders.created** | Occurs when a new [works order](https://foundations-documentation.reapit.cloud/platform-glossary#works-order) is created | `worksorders.read` |
| **worksorders.modified** | Occurs when an existing [works order](https://foundations-documentation.reapit.cloud/platform-glossary#works-order) is modified | `worksorders.read` |

### Subscribe to customers

You must configure the customer\(s\) that your webhook will respond to events for. Only customers who have installed your listed application will appear here. 

* Specify one or more customers to receive only event originating from those customers
* Specify 'SBOX' to listen to events triggered from our sandbox \(useful for testing\)
* Leave this field blank to respond to events for all customers who have installed your application. You will immediately receive events for new customers who install your application without any configuration change required. This does not include sandbox events.

### Optional webhook behaviour

By default, webhooks will not be emitted when only the entity's eTag and modified timestamp has changed. If you would prefer to receive notifications in this situation, please use the **Include notifications where only the eTag has been modified option** when configuring your webhook

{% hint style="info" %}
**To test your webhook end to end with real data**, use the sandbox database available to you in the Developer Portal. Set up a webhook to listen to 'SBOX' events and make changes to the sandbox using our APIs or Interactive API Explorer.
{% endhint %}

## Receiving events

### Example payload

We use a consistent schema to describe any event that we broadcast in a descriptive and self-contained way. The notifications we emit indicate that an **event has happened** - but additionally and where appropriate -  we provide details about the actual data change that has occurred.  This allows your application to ascertain **granular details about the event** without needing additional API calls.

Below is an example of what a **contacts.modified** webhook event might look like

```text
{
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

| Property | Description |
| :--- | :--- |
| `eventId` | A unique identifier for the event. Some events will trigger multiple notifications \(for example if the name of a contact changes, you'll also receive a notification for each of their associated roles. These will share the same event identifier\) |
| `entityId` | If applicable, the unique identifier of the entity that the event is associated to. Please note that by itself this is _not_ a globally unique identifier. Uniqueness can be achieved by also including the `customerId` |
| `customerId` | The unique identifier of the Reapit customer whom the data event is associated with |
| `eventTime` | The UTC date and time the event was emitted from our Platform |
| `topicId` | The topic the event is associated with. See the list outlined in the [Subscription topics ](webhooks.md#subscription-topics)section |
| `new` | The new version of the entity, if applicable - this property will be null if a user has deleted or archived the entity. |
| `old` | The old version of the entity, if applicable - this property will be null in the event of a _.created_ event. |
| `diff` | A diff outlining the exact changes between the new/old payloads. The diff is only populated for _.modified_ events where both `new`/`old` representations of the entity are available. |

The content of the `new`, `old`, and `diff` properties in the webhook event payload use the same schema that the respective API endpoints use. For example, if the payload received has a `topicId` of `contacts.modified` then these payload properties will use the same schema as the `GET /contacts` API endpoints

### Testing

When you have an endpoint configured, you can test it by using the **Ping** function. This will send a test event with an example payload to the URL stored against the webhook for the selected topic. You will only be able to select topics that are applicable to the webhook being tested. 

![](../.gitbook/assets/image%20%2840%29.png)

The user interface will show a success or failure based on the response back from the endpoint. In the event of a success response, you will have received the example payload to the configured endpoint.

We also recommend testing your webhooks using our sandbox environment before applying them to customers.

{% hint style="info" %}
**All events submitted from the Ping function** use example data and will have a `customerId` of 'webhook-test' and an `entityId` of '9e7e4181-6210-49ea-abf5-d5ce16d23647'. Receiving services need to handle this appropriately and not treat the payload as production event 
{% endhint %}

## Additional information

* Events are generated in near real-time and though extremely unlikely, we do not guarantee that you will only get a single notification for an event. 
* We do not guarantee that webhooks will be sent in the exact order that the events occurred. You can use the `eventTime` to determine when each event occurred.
* Webhooks originated requests contribute to developer analytics and billing in the same way as regular API requests do

{% hint style="info" %}
**We will be introducing** an automatic retry policy with exponential backoff as [an additional feature in due course](https://github.com/reapit/foundations/issues/1299)
{% endhint %}

