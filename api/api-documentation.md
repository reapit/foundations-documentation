---
description: Complete technical guidance on how to work with the Foundations REST APIs
---

# Platform

{% hint style="warning" %}
The Foundations REST API will in-time replace our existing REST and SOAP web services, however, **the existing REST and SOAP web services are not at this time being deprecated** and will continue to operate side-by-side until appropriate notice given.
{% endhint %}

## Introduction

The Foundations API is organised around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). Our API has predictable resource-oriented URLs using standard HTTP response codes and verbs. All requests and responses, including errors, are [JSON-encoded](http://www.json.org/).

You can immediately start testing our APIs in [sandbox mode](api-documentation.md#sandbox-mode) by using our [Interactive API Explorer](https://dev.marketplace.reapit.cloud/developer/swagger). Please see our [help page](https://dev.marketplace.reapit.cloud/developer/help) for support and information on preview / upcoming changes. 

The current version of our APIs is **2020-01-31.**

{% hint style="success" %}
**Our Platform is in** **alpha** and we'll be continually building new features during this phase. Please see our [help section](https://dev.marketplace.reapit.cloud/developer/help) to view our milestones or to submit a feature request or bug.
{% endhint %}

## REST

### Request methods

Our APIs present a uniform interface for performing CRUD \(create, retrieve, update, delete\) operations. Each endpoint adheres to REST guidelines to map the correct verb to the operation being performed. 

Our APIs support the following HTTP request methods:

| Method | Action |
| :--- | :--- |
| `GET` | Retrieve a resource or collection of resources |
| `POST` | Create a new resource |
| `PATCH` | Partially update an existing resource by only including the fields to replace in payload |
| `DELETE` | Soft delete an existing resource |

### Response codes

We use standardized HTTP status codes to indicate the outcome of a request. Below is a listing of the codes our APIs may return and their meaning.

* Codes in the `2xx` range indicate that the request was fulfilled successfully. 
* Codes in the `4xx` range indicate an error caused by the information provided.
* Codes in the `5xx` range indicate an error with our APIs which will be logged and investigated.

| Code | Description |
| :--- | :--- |
| `200 OK` | The request has been fulfilled. |
| `201 Created` | The request has been fulfilled and a new resource has been created.  |
| `204 No Content` | The request has been fulfilled but there is no need to send any data back.  |
| `400 Bad Request` | The request was not understood by the server. This is generally due to bad request syntax. |
| `401 Unauthorized` | The provided authentication credentials are incorrect or not present. Generally, this is due to the lack of an "Authorization" header |
| `403 Forbidden` | The authentication credentials request do not provide sufficient scope to fulfill the request |
| `404 Not Found` | The requested resource was not found. |
| `412 Precondition Failed` | The was not fulfilled because preconditions provided by the client could not be met. Usually occurs [optimistic concurrency control ](api-documentation.md#optimistic-concurrency)rejects the request.    |
| `422 Unprocessable Entity` | A validation error has occurred. The error response body will provide additional information on the failure\(s\). |
| `429 Too Many Requests` | The request was not accepted because the application has exceeded the rate limit.  |
| `500 Internal Error` | The request triggered an unexpected error which will be logged and investigated. |

### Errors

In addition to the relevant response code, unsuccessful requests will return a JSON encoded error response as outlined below:

| Attribute | Description |
| :--- | :--- |
| `statusCode` | The integer response code issued by this response |
| `dateTime` | UTC formatted timestamp of when error response was issued |
| `description` | Human readable message providing details about the error. |
| `errors` | A collection of validation issues with the provided payload. Only populated for `422 Unprocessable Entity` responses. |

{% hint style="info" %}
**All responses** are issued with a unique request id, regardless of whether they were successful or not. You can find this in the `x-amzn-RequestId` response header. If you [report a bug](https://dev.marketplace.reapit.cloud/developer/help) be sure to include this id to allow us to examine your problem in greater depth.
{% endhint %}

## Authentication

The Foundations platform uses [OpenID Connect](https://openid.net/connect/faq/) for authenticating requests. OpenID Connect is a protocol for authenticating users, built on top of the OAuth 2.0 specification.

### Registering your app

Submitting your application to our Marketplace is the first step for it to be able to interact with our clients data. After you have [successfully submitted your app](https://dev.marketplace.reapit.cloud/developer/submit-app), you will be issued with a **client id** and **secret.** You can obtain these by clicking your app in the [My Apps](https://dev.marketplace.reapit.cloud/developer/apps) area of our developer portal.

{% hint style="info" %}
**For more information** on how to register your application with our Marketplace, please see our [welcome guide](https://dev.marketplace.reapit.cloud/developer/welcome).
{% endhint %}

### Customer installation

You can immediately access our [sandbox environment](https://foundations-documentation.reapit.cloud/api/api-documentation#sandbox-mode) but in order to be authorized to access a customers data, they must choose to install it.

Customer administrators are able to control your applications access to their companies data by opted to install it once it has been listed in our Marketplace. As part of this process, they will grant your application with any permissions \(scopes\) it requires to interact with Foundations API endpoints.

### OAuth 2.0 Grants

We support the use of two different OAuth 2.0 grants for applications built on our Platform:

| Grant | Description |
| :--- | :--- |
| Authorization code flow | For use by client and server side applications that have a user in context. Allows the implementing application to be authenticated on the behalf of the user. **To use this grant, please see the documentation for our** [**Reapit Connect**](reapit-connect.md#overview) **service.** |
| Client credentials flow | For use by server side machine to machine applications that do not have a user in context. Allows the implementing application to be authenticated on behalf of itself. |

### Client credentials flow

To obtain tokens for your application to interact with our protected endpoints, you must send a `POST` request to our token endpoint, as below:

`https://dev.connect.reapit.cloud/oauth2/token`

| Request payload | Description |
| :--- | :--- |
| `client_id` | The unique client id that was issued to your application after registration |
| `grant_type` | Must be set to `client_credentials` |

Additionally, the `Authorization` header should be set to `Basic <base64 secret>`where `<base64 secret>` is the **base64 representation of the client id and secret concatenated with a colon**. You can obtain **client id** and **secret** by clicking your app in the [My Apps](https://dev.marketplace.reapit.cloud/developer/apps) area of our developer portal.

If your request is properly formed and valid, you'll receive a response similar to below.

```text
HTTP/1.1 200 OK
Content-Type: application/json

{ 
 "access_token" : "eyJz9sdfsdfsdfsd", 
 "token_type" : "Bearer", 
 "expires_in" : 3600
}
```

| Response payload | Description |
| :--- | :--- |
| `access_token` | Token to grant access to protected Foundations endpoints |
| `expires_in` | The number of seconds that the access token is valid for |
| `token_type` | The type of tokens issued. Will always be set to `bearer` |

{% hint style="danger" %}
**Client credentials flow** must not be used for applications that are client side only. A server side component is required to be able to safely store credentials. 
{% endhint %}

### Using access tokens

Access tokens \(also known as bearer tokens\) are designed to provide your application with access to protected resources.

Once you have been issued an access token from our token endpoint, your application can access Foundations APIs by including it in a`Authorization` header. Our servers will validate this token and fulfill the request, subject to your application application requesting the relevant endpoint scope during registration.

### Accessing customer data

Requests issued with access codes gained from the client credentials flow must also indicate which customers data they wish to interact with. 

You must additionally include a `reapit-customer` header in your request so that it can be fulfilled appropriately. The header should be set to the customers unique id which becomes available to view after a customer has chosen to install your application. This information is available in the [Analytics](https://dev.marketplace.reapit.cloud/developer/analytics) area of the developer portal.

If a customer chooses to uninstall your application then your access to their data will be revoked.

## Sandbox mode

You can use the Foundations APIs in Sandbox mode which provides a set of demonstration data that can be interacted with without requiring a customer to install your application. Sandbox mode supports processing of all read and write requests so that you can build and test in confidence without impacting customer data. 

To access the sandbox, you just need to be registered as a developer on our Portal. 

* You can use **authorization code flow** by providing your developer portal credentials to our [Reapit Connect](reapit-connect.md#overview) service
* You can use **client credentials flow** by providing `SBOX` as your `reapit-customer` request header

{% hint style="info" %}
**For a quick start experience**, our [interactive API explorer](https://dev.marketplace.reapit.cloud/developer/swagger) is connected to the sandbox automatically
{% endhint %}

## Issuing requests

### Timestamps

The Foundations platform exclusively works with UTC date times to allow us to present a uniform interface and ensure that behavior remains predictable, regardless of your application or user timezone.

Our APIs enforce that any date time information that your application issues to us adheres to the [ISO-8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. If you provide a request body, query string or header that does not adhere to this standard, you will receive a validation error reporting the problem. Any date times issued from our endpoints will be returned to you in the same format. 

Some of the fields we provide are date-only and have no time component. Date only fields will not accept a time component in a request and will not include a time component in their response. You can see which fields these are by examining the model documentation and example responses provided by our [Interactive API Explorer](https://dev.marketplace.reapit.cloud/developer/swagger). 

```javascript
{
  "myDateAndTimeField": "2020-02-11T13:32:03.6759302Z",
  "myDateOnlyField": "2020-02-11"
}
```

### Retrieving data

Our APIs support retrieval of resources using the `GET` verb. When a GET request has been successfully fulfilled, you will receive a `200 OK` response with results included as a JSON encoded payload. 

For practical and performance reasons, our top level APIs enforce paging and require a standardised set of query strings in their requests. The `pageSize` and `pageNumber` parameters are used to cycle through the available results from a top level API. 

For example, `GET /contacts?pageSize=10&pageNumber=2` will return the second page of ten contact resources in the following structure:

| Response payload | Description |
| :--- | :--- |
| `pageSize` | The number of records that have been retrieved by this response. Default is 25 and maximum 100 unless specified |
| `pageNumber` | The page number that this response represents |
| `pageCount` | The number of available pages based on the current response `pageSize` |
| `totalCount` | The total number of resources available that fulfill the criteria of the current request |
| `_embedded` | The list of resources that have been returned in this paged response |

### Creating data

Our APIs support resource creation using the `POST` verb. When a creation request has been successfully fulfilled, you will receive a `201 Created` response. 

Since the creation of new resources is often asynchronous, we do not include the payload of the newly created resource in the `POST` response. Instead, we include the the location of where the new resource can be retrieved from in the `Location` header of the `POST` response.

### Updating data

Our APIs support resource updates using the `PATCH` verb. When an update request has been successfully fulfilled, you will receive a `204 No Content` response.

When you provide an update to use using the `PATCH` verb, you're able to only update the parts of a resource that you care about, rather than completely replacing the entire resource. Usage is simple and you just need to specifically send us the data you wish to update.

The below example will only update the notes field on a representation that may allow you update many other attributes:

```javascript
{
  "notes": "Returned Mr Johnsons Call",
}
```

As with resource creation, we do not include the updated resource in the `PATCH` response. Instead,  simply re-fetch the latest state of the resource by issuing a `GET` request.

### Request validation

To protect the integrity of our clients data, we enforce proper validation on all `POST` and `PATCH` requests

Should your request not pass the validation requirements of the endpoint, then you'll be issued a `422 Unprocessable Entity` code. The[ error response ](api-documentation.md#errors)will include a listing of validation problems and how you can solve them.

```javascript
{
  "errors": [
    {
      "field": "type",
      "message": "The enum value provided for AreaType is incorrect"
    }
  ],
  "statusCode": 422,
  "dateTime": "2020-02-11T13:32:03.6759302Z",
  "description": "One or more validation failures have occurred. Please refer to Errors list for details"
}
```

### Optimistic concurrency

Our APIs serve Platform functionality and data to various different applications and users at the same time, which needs to be managed carefully to avoid concurrency problems. 

In some systems, when multiple systems perform updates at the same time without knowledge of each others changes, you can be left with the problem of **lost updates** whereby the last update "wins" and previous updates are lost. Our APIs enforce o[ptimistic concurrency control](https://en.wikipedia.org/wiki/Optimistic_concurrency_control) to help avoid this problem.

We use [entity tags](https://tools.ietf.org/html/rfc7232#section-2.3) as an indicator of the current version of any resource returned from our APIs and whenever a singular representation is served by any of our `GET` endpoints, it will include `eTag` in the response header. For convenience, we also include this as an `_eTag` attribute in the response for each object.

This gives both client and server a means of understanding the version of a particular resource an application has received. Subsequently when a resource is updated, it's `eTag` value will also be updated.

To ensure that updates aren't lost, you must include an `If-Match` header in your `PATCH` request containing the `eTag` value exactly as you received it **including quotation marks.** The server will then compare its version of the resource with the `eTag` you provided.

* If they match, then the update is intended for the same version of the resource and the request will be processed 
* If they do not match, then the resource has been updated since it was fetched and the request will be rejected with a `412 Precondition Failed` error response

If rejected, you need to retrieve the latest version of the resource and replay your changes before attempting another update.

{% hint style="info" %}
**For more information** about entity tags and our implementation of conditional requests, please see [RFC 7232](https://tools.ietf.org/html/rfc7232)
{% endhint %}

## Versioning

As we evolve our platform, new features will be added and fixes will be made. We categorize changes in two ways: **breaking** and **non-breaking** changes. We make every effort to implement changes as non-breaking wherever possible, however, there are sometimes situations that require this. 

Whenever a breaking change is introduced into our platform we release a new, dated version. The current version is **2020-01-31.** 

All requests should indicate the version that should be used to fulfill them. You can do this by including the header `api-version` set to the dated version required.  

### Breaking changes

We consider the following to be examples of breaking changes:

* Renaming or removing an existing field or endpoint
* Changing the URL structure of an existing endpoint
* Changing the filters that an existing endpoint provides
* Changing error response codes or messages that an endpoint provides
* Modifying or adding a new validation to an existing resource
* Changing the data type of an existing field
* Requiring a parameter that wasn't previously required

### Depreciation

Whenever a new version is released, the previous version enters its sunset period. This is presently six months though will be reviewed as our platform continues to grow and evolve.

At the end of a versions sunset period it will become depreciated and you will be required to adopt more recent version. You will be notified if your application is using a version that is soon to be depreciated.

{% hint style="info" %}
**Stay up to date:** please see the [help section](https://dev.marketplace.reapit.cloud/developer/help) of our developer portal for information on recent and upcoming changes.
{% endhint %}

## Metadata

Most resources that can be updated support a `metadata` attribute in their request and response payload. This attribute can be used to attach additional key-value data against a specific resource that your application can later use. 

Our metadata system allows you to easily extend the data that our resources present. You can create a richer integration between your application and our Platform and the process is simplified by storing all relevant data in a single place. 

The `metadata` attribute is populated in `POST` and `PATCH` payloads as below:

```javascript
{
  ...
  "metadata": {
    "MyCustomField1": "MyCustomValue1",
    "MyCustomField2": true
  }
}
```

Once `metadata` has been set against a resource, it will be automatically returned in the same format for future `GET` requests. **Metadata is application specific** and any data that your application sets will not be presented to Reapit or other applications built on the Foundations platform.

Metadata storage should not be used for any sensitive information \(personally identifiable details, bank accounts, etc\).

{% hint style="info" %}
**Coming soon**: we will add the ability to search for resources that match specific metadata content. See our [project milestones](https://github.com/reapit/foundations/milestones) for further details.
{% endhint %}

## Hypermedia

Our APIs are ****REST level 3[ ](https://restfulapi.net/richardson-maturity-model/)and implement [hypermedia controls](https://restfulapi.net/richardson-maturity-model/) to improve the developer experience of using our platform. 

Hypermedia makes our APIs self documenting and aids discovery. Each `GET` response provides a uniform interface to present links to demonstrate **which** data is related and **how** that data can be retrieved. This is particularly useful for APIs that present complex systems of interrelated data, such as ours. 

We adopt the [HAL hypertext application language](http://stateless.co/hal_specification.html) to serve as our message format. Each resource, including [collection resources](api-documentation.md#pagination), include a `_links` collection to present related data. The responses `_links` dictionary will include a **key** to represent the type of relationship and a **value** to represent the location where the related resources can be obtained from. 

The **condensed** `GET` contact payload example below demonstrates how relationships are presented:

```text
{
  "id": "OXF18000001",
  "created": "2018-02-12T09:45:01.0000000Z",
  "modified": "2019-06-23T12:30:12.0000000Z",
  "title": "Mr",
  "forename": "John",
  "surname": "Smith",
  "dateOfBirth": "1992-08-12",
  "homePhone": "01234 567890",
  "mobilePhone": "07890 123456",
  "email": "example@email.com",
  "officeIds": [
    "OXF"
  ],
  "negotiatorIds": [
    "JAS"
  ],
  "_eTag": ""33a64df551425fcc55e4d42a148795d9f25f89d4"",
  "_links": {
    "self": {
      "href": "/contacts/OXF18000001"
    },
    "documents": {
      "href": "/documents/?ownerType=contact&ownerId=OXF18000001"
    },
    "identityChecks": {
      "href": "/identityChecks/?contactId=OXF18000001"
    },
    "offices": {
      "href": "/offices/?id=OXF"
    },
    "negotiators": {
      "href": "/negotiators/?id=JAS"
    }
  },
  "_embedded": null
}
```

In the example above, the presence of the `identityChecks` **key** indicates that there is a related resource available. The **value** contains the service location and query string parameters required to retrieve the related identity check resources.

{% hint style="info" %}
**Coming soon**: we will add the ability to embed related data in our API responses. See our [milestones](https://github.com/reapit/foundations/milestones) for more information.
{% endhint %}

## Webhooks

We will be adding webhook functionality in the coming months, please see our [milestone](https://github.com/reapit/foundations/milestones) for details.s  

