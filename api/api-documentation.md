---
description: Complete technical guidance on how to work with the Foundations REST APIs
---

# REST API

{% hint style="warning" %}
The Foundations REST API will in-time replace our existing REST and SOAP web services, however, **the existing REST and SOAP web services are not at this time being deprecated** and will continue to operate side-by-side until appropriate notice given.
{% endhint %}

## Introduction

The Foundations API is organised around [REST](http://en.wikipedia.org/wiki/Representational\_State\_Transfer). Our API has predictable resource-oriented URLs using standard HTTP response codes and verbs. All requests and responses, including errors, are [JSON-encoded](http://www.json.org/).

You can immediately start testing our APIs in [sandbox mode](api-documentation.md#sandbox-mode) by using our [Interactive API Explorer](https://developers.reapit.cloud/swagger). Please see our [help page](https://marketplace.reapit.cloud/developer/help) for support and information on preview / upcoming changes.

| Service base location                                                                    | Description                                                                                                                                                                                                 |
| ---------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><strong>Authentication service</strong></p><p>https://connect.reapit.cloud/</p>       | First, use our [authentication service](api-documentation.md#authentication) to receive an access token. Include this in the header of any request you issue to our other platform services.                |
| <p><strong>All other platform services</strong></p><p>https://platform.reapit.cloud/</p> | Once authenticated, you can issue requests to our other platform services. For details on the endpoint we provide, see our [Interactive API Explorer](https://marketplace.reapit.cloud/developer/swagger).  |

The current version of our APIs is **2020-01-31** - please include it in your `api-version` request header. For more information, see our [versioning](api-documentation.md#versioning) information

{% hint style="success" %}
**Our Platform is in** **beta** and we'll be continually building new features during this phase. Please see our [help section](https://marketplace.reapit.cloud/developer/help) to view our milestones or to submit a feature request or bug.
{% endhint %}

## REST

### Request methods

Our APIs present a uniform interface for performing CRUD (create, retrieve, update, delete) operations. Each endpoint adheres to REST guidelines to map the correct verb to the operation being performed.

Our APIs support the following HTTP request methods:

| Method   | Action                                                                                   |
| -------- | ---------------------------------------------------------------------------------------- |
| `GET`    | Retrieve a resource or collection of resources                                           |
| `POST`   | Create a new resource                                                                    |
| `PATCH`  | Partially update an existing resource by only including the fields to replace in payload |
| `DELETE` | Soft delete an existing resource                                                         |

### Response codes

We use standardized HTTP status codes to indicate the outcome of a request. Below is a listing of the codes our APIs may return and their meaning.

* Codes in the `2xx` range indicate that the request was fulfilled successfully.&#x20;
* Codes in the `4xx` range indicate an error caused by the information provided.
* Codes in the `5xx` range indicate an error with our APIs which will be logged and investigated.

| Code                       | Description                                                                                                                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `200 OK`                   | The request has been fulfilled.                                                                                                                                                                        |
| `201 Created`              | The request has been fulfilled and a new resource has been created.                                                                                                                                    |
| `204 No Content`           | The request has been fulfilled but there is no need to send any data back.                                                                                                                             |
| `400 Bad Request`          | The request was not understood by the server. This is generally due to bad request syntax.                                                                                                             |
| `401 Unauthorized`         | The provided authentication credentials are incorrect or not present. Generally, this is due to the lack of an "Authorization" header                                                                  |
| `403 Forbidden`            | The authentication credentials request do not provide sufficient scope to fulfill the request                                                                                                          |
| `404 Not Found`            | The requested resource was not found.                                                                                                                                                                  |
| `412 Precondition Failed`  | The was not fulfilled because preconditions provided by the client could not be met. Usually occurs [optimistic concurrency control ](api-documentation.md#optimistic-concurrency)rejects the request. |
| `422 Unprocessable Entity` | A validation error has occurred. The error response body will provide additional information on the failure(s).                                                                                        |
| `429 Too Many Requests`    | The request was not accepted because the application has exceeded the rate limit.                                                                                                                      |
| `500 Internal Error`       | The request triggered an unexpected error which will be logged and investigated.                                                                                                                       |

### Errors

In addition to the relevant response code, unsuccessful requests will return a JSON encoded error response as outlined below:

| Attribute     | Description                                                                                                           |
| ------------- | --------------------------------------------------------------------------------------------------------------------- |
| `statusCode`  | The integer response code issued by this response                                                                     |
| `dateTime`    | UTC formatted timestamp of when error response was issued                                                             |
| `description` | Human readable message providing details about the error.                                                             |
| `errors`      | A collection of validation issues with the provided payload. Only populated for `422 Unprocessable Entity` responses. |

{% hint style="info" %}
**All responses** are issued with a unique request id, regardless of whether they were successful or not. You can find this in the `x-amzn-RequestId` response header. If you [report a bug](https://marketplace.reapit.cloud/developer/help) be sure to include this id to allow us to examine your problem in greater depth.
{% endhint %}

### Rate limits

We apply rate limits on the API calls an application can make within a given time period. If this limit is exceeded the app will be throttled and API requests will fail.

* 20 requests can be sent per second
* 5 maximum concurrent requests at any time per customer&#x20;
* 250,000 maximum requests per day&#x20;

If your application exceeds these limits, your app will be presented with `429 Too Many Requests` responses.

## Authentication

The Foundations platform uses [OpenID Connect](https://openid.net/connect/faq/) for authenticating requests. OpenID Connect is a protocol for authenticating users, built on top of the OAuth 2.0 specification.

### Registering your app

Submitting your application to our AppMarket is the first step for it to be able to interact with our clients data. After you have [successfully submitted your app](https://marketplace.reapit.cloud/developer/submit-app), you will be issued with a **client id** and **secret.** You can obtain these by clicking your app in the [My Apps](https://marketplace.reapit.cloud/developer/apps) area of our developer portal.

{% hint style="info" %}
**For more information** on how to get started and register your application with our AppMarket, please see our[ developer portal guide](../developer-portal.md).
{% endhint %}

### Customer installation

You can immediately access our [sandbox environment](https://foundations-documentation.reapit.cloud/api/api-documentation#sandbox-mode) but in order to be authorized to access a customers data, they must choose to install it.

Customer administrators are able to control your applications access to their companies data by opted to install it once it has been listed in our AppMarket. As part of this process, they will grant your application with any permissions (scopes) it requires to interact with Foundations API endpoints.

### OAuth 2.0 Grants

We support the use of two different OAuth 2.0 grants for applications built on our Platform:

| Grant                   | Description                                                                                                                                                                                                                                                                              |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Authorization code flow | For use by client and server side applications that have a user in context. Allows the implementing application to be authenticated on the behalf of the user. **To use this grant, please see the documentation for our** [**Reapit Connect**](reapit-connect.md#overview) **service.** |
| Client credentials flow | For use by server side machine to machine applications that do not have a user in context. Allows the implementing application to be authenticated on behalf of itself.                                                                                                                  |

### Client credentials flow

To obtain tokens for your application to interact with our protected endpoints, you must send a `POST` request to our token endpoint, as below:

`https://connect.reapit.cloud/token`

| Request payload | Description                                                                 |
| --------------- | --------------------------------------------------------------------------- |
| `client_id`     | The unique client id that was issued to your application after registration |
| `grant_type`    | Must be set to `client_credentials`                                         |

Content-Type must be set to `application/x-www-form-urlencoded` and the `Authorization` header should be set to `Basic <base64 secret>`where `<base64 secret>` is the **base64 representation of the client id and secret concatenated with a colon**. You can obtain **client id** and **secret** by clicking your app in the [My Apps](https://marketplace.reapit.cloud/developer/apps) area of our developer portal.

If your request is properly formed and valid, you'll receive a response similar to below.

```
HTTP/1.1 200 OK
Content-Type: application/json

{ 
 "access_token" : "eyJz9sdfsdfsdfsd", 
 "token_type" : "Bearer", 
 "expires_in" : 3600
}
```

| Response payload | Description                                               |
| ---------------- | --------------------------------------------------------- |
| `access_token`   | Token to grant access to protected Foundations endpoints  |
| `expires_in`     | The number of seconds that the access token is valid for  |
| `token_type`     | The type of tokens issued. Will always be set to `bearer` |

{% hint style="danger" %}
**Client credentials flow** must not be used for applications that are client side only. A server side component is required to be able to safely store credentials.
{% endhint %}

### Using access tokens

Access tokens (also known as bearer tokens) are designed to provide your application with access to protected resources. Once you have been issued an access token from our token endpoint, your application can access Foundations APIs by including it in a`Authorization` header, prefixed with `Bearer`

`Authorization: Bearer <your access token>`

Our servers will validate this token and fulfill the request, subject to your application application requesting the relevant endpoint scope during registration.

### Accessing customer data

Requests issued with access codes gained from the client credentials flow must also indicate which customers/agents data they wish to interact with.

You must additionally include a `reapit-customer` header in your request so that it can be fulfilled appropriately. The header should be set to the customers unique id which becomes available to view after a customer has chosen to install your application. You find out out the unique ids and names of the clients that have installed your application in the [Analytics](https://marketplace.reapit.cloud/developer/analytics) area of the developer portal.

If a customer chooses to uninstall your application then your access to their data will be revoked.

{% hint style="info" %}
We recommend using our webhooks system to be instantly notified when a Reapit customer installs your application. See our [webhooks documentation](webhooks.md)  for more information.
{% endhint %}

## Sandbox mode

You can use the Foundations APIs in Sandbox mode which provides a set of demonstration data that can be interacted with without requiring a customer to install your application. Sandbox mode supports processing of all read and write requests so that you can build and test in confidence without impacting customer data.

To access the sandbox, you just need to be registered as a developer on our Portal.

* You can use **authorization code flow** by providing your developer portal credentials to our [Reapit Connect](reapit-connect.md#overview) service
* You can use **client credentials flow** by providing `SBOX` as your `reapit-customer` request header

{% hint style="info" %}
**For a quick start experience**, our [interactive API explorer](https://marketplace.reapit.cloud/developer/swagger) is connected to the sandbox automatically
{% endhint %}

## Issuing requests

### Timestamps

The Foundations platform exclusively works with UTC date times to allow us to present a uniform interface and ensure that behavior remains predictable, regardless of your application or user timezone.

Our APIs enforce that any date information that your application issues to us adheres to the [ISO-8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. If you provide a time component, then it must be accompanied by a [time zone designator](https://en.wikipedia.org/wiki/ISO\_8601#Time\_zone\_designators). If you provide a request body, query string or header that does not adhere to this standard, you will receive a validation error reporting the problem. Any date times issued from our endpoints will be returned to you in the same format.

Some of the fields we provide are date-only and have no time component. Date only fields will not accept a time component in a request and will not include a time component in their response. You can see which fields these are by examining the model documentation and example responses provided by our [Interactive API Explorer](https://marketplace.reapit.cloud/developer/swagger).

```javascript
{
  "myDateAndTimeField": "2020-02-11T13:32:03.6759302Z",
  "myDateOnlyField": "2020-02-11"
}
```

### Retrieving data

Our APIs support retrieval of resources using the `GET` verb.  When a `GET` request has been successfully fulfilled, you will receive a `200 OK` response with results included as a JSON payload. To ensure that parameters that `GET` resources accept work as you expect, please ensure you URL encode the parameters you provide.

For practical and performance reasons, our top level APIs enforce paging and require a standardised set of query strings in their requests. The `pageSize` and `pageNumber` parameters are used to cycle through the available results from a top level API.

For example, `GET /contacts?pageSize=10&pageNumber=2` will return the second page of ten contact resources in the following structure:

| Response payload | Description                                                                              |
| ---------------- | ---------------------------------------------------------------------------------------- |
| `pageSize`       | The requested number of records per page. Default is 25 and maximum 100 unless specified |
| `pageNumber`     | The page number that this response represents                                            |
| `pageCount`      | The actual number of records that the current page contains                              |
| `totalPageCount` | The total number of pages available in the response                                      |
| `totalCount`     | The total number of resources available that fulfil the criteria of the current request  |
| `_embedded`      | The list of resources that have been returned in this paged response                     |

{% hint style="info" %}
**Extras field**\
If you represent an AgencyCloud customer and require access to data held in the 'extras' semi structured field, please submit a GitHub developer request using the issue template provided.
{% endhint %}

### Creating data

Our APIs support resource creation using the `POST` verb. When a creation request has been successfully fulfilled, you will receive a `201 Created` response.

The body of a `POST` request should always be sent as a JSON object, with the `Content-Type` header set to `application/json`

Since the creation of new resources is often asynchronous, we do not include the payload of the newly created resource in the `POST` response. Instead, we include the the location of where the new resource can be retrieved from in the `Location` header of the `POST` response.

### Updating data

Our APIs support resource updates using the `PATCH` verb. When an update request has been successfully fulfilled, you will receive a `204 No Content` response.

The body of a `PATCH` request should always be sent as a JSON object, with the `Content-Type` header set to `application/json`

When you provide an update to use using the `PATCH` verb, you're able to only update the parts of a resource that you care about, rather than completely replacing the entire resource. Usage is simple and you just need to specifically send us the data you wish to update.

The below example will only update the notes field on a representation that may allow you update many other attributes:

```javascript
{
  "notes": "Returned Mr Johnsons Call",
}
```

As with resource creation, we do not include the updated resource in the `PATCH` response. Instead, simply re-fetch the latest state of the resource by issuing a `GET` request.

### Uploading files

The following APIs allow consumers to upload certain types of documents to the Reapit Platform:

* documents
* propertyImages
* identityChecks

Each respective APIs `POST` endpoint supports uploads of files up to 6Mb in size, however we understand that there may sometimes be a legitimate need to upload larger files. To support this requirement, it is possible to obtain a pre-signed URL from each of these APIs which you can then send your data to.&#x20;

#### Using pre-signed URLs

To upload files between 6Mb and 30Mb in size, a pre-signed URL should be obtained from the Platform and used to upload your data. Each of the APIs listed in the [Uploading files](api-documentation.md#uploading-files) section of this documentation has a `POST /signedUrl` endpoint which can be called to generate up to 10 pre-signed URLs. This can be useful where you need to upload more than one file.&#x20;

Use the following request body when calling the endpoint, setting amount to a value between 1 and 10 to have the respective number of URLs returned to you

```
POST /documents/signedUrl
{
    "amount": 2
}
```

The response will contain a collection of URLs which can then be used to upload your content to, along with an expiry date for the provided URLs, which will expire after 15 minutes

```
{
  "urls": [
    "https://reapit-file-uploads-prod.s3.eu-west-2.amazonaws.com/443e4a98-dfcb-4345-abb2-e52031928ed1?X-Amz-Expires=900&x-amz-security-token=IQoJb3JpZ2luX2VjEBcaCWV1LXdlc3QtMiJHMEUCIQC0Lx67%2F6JwNS9X7faUwm%2BwHYYpTLQ1UM42ge5WXDHKrgIgPh7r4O%2BLSlV0xhCQ5qoifZmIHajay2%2BMSddWghyj1Acq6wMIEBABGgw1MDM2MTQ4Mjg1MTciDO3pV3zkZcZVtWhWxyrIA6%2Bt4yRlh3g4B%2FCgt7T7YJ7yX3VUcOg%2F2fOKATN2qSqAjshXNMQ2ZKkqDDiHbAgvbzuZBkQDbKirksRmhqVGVv1A8VBcJ7JYP5jqpiwUuwgKjjQtsHWocKsfPVYsiBReiP%2Fw%2FJD9d0hWLPAvl%2FGwUoQr4bFveQxTTbh59G%2FUJx%2B%2BJO1vX3iAPLaLGSbEk7vWsyEDHlnCZKt3FftJ6rLlPlldzTLSl0dxjXUuYHXtwfHr2xT%2FMEkznvCxfYvhkRq2JqMrRFDs9HhYmgNKGSq22RTXpG6H6bvPj2CB1%2F2wKOAXbeZxnrtcWdnHlgE3xqOYwr1QaoL0w4llwGwGKIv5bQndF8MOiqDYIKZmWoH%2Bd3oQRfX2lFsBx3Ou1VDc4T28PkN8nPUnAx5OZ%2Fqu4A%2FWAbNnxM6L9%2B0kwDU0ijXro%2FjKNaTynYmqzNHVei6MTeEv7l2IaBV4eYZcU76jNIa8qPntGZjfCNm3nHHoTalPj6jYVYQJLGGe5OAa5U5YLm%2FczFhjPNQdBW5QsUaFEdccAV5QDYoQdaQba%2FnuTXvPS2147LYNdNMiQsi1M5peEhe89kaIitGONn9GOBXdeh2OBIrfRDYVICmQKjDjlbqHBjqlAUlaHQsfcgpG0NXSVM4q0XaxTWUQs117DKno2d5kJpur35M%2Bmk1ywaOg%2BQQs1elOD5lWUW7iQU8OKP6OFFe4pEMQlM02lz%2BtdNCy7aUQ%2FBVl43buUyDgciDI5DTbhEJe0LZuv1Yf0bGhuhtS%2FZhesqgbAlMVTwy8TiKPd7hE3%2FfsrThEtrgvrAMVSr4hbrZSDItfdsFb976epf%2BZt%2Fb5aTsz%2BxHzgA%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAXKQOIN7STXK57JEK/20210714/eu-west-2/s3/aws4_request&X-Amz-Date=20210714T082753Z&X-Amz-SignedHeaders=host;x-amz-security-token&X-Amz-Signature=f8f5fb8919dc1a4aff335be64bd0746e6c523480f27a47d17106ed9d98181799",
    "https://reapit-file-uploads-prod.s3.eu-west-2.amazonaws.com/f6ea00ba-1b70-49ed-9a4a-d480d438d443?X-Amz-Expires=900&x-amz-security-token=IQoJb3JpZ2luX2VjEBcaCWV1LXdlc3QtMiJHMEUCIQC0Lx67%2F6JwNS9X7faUwm%2BwHYYpTLQ1UM42ge5WXDHKrgIgPh7r4O%2BLSlV0xhCQ5qoifZmIHajay2%2BMSddWghyj1Acq6wMIEBABGgw1MDM2MTQ4Mjg1MTciDO3pV3zkZcZVtWhWxyrIA6%2Bt4yRlh3g4B%2FCgt7T7YJ7yX3VUcOg%2F2fOKATN2qSqAjshXNMQ2ZKkqDDiHbAgvbzuZBkQDbKirksRmhqVGVv1A8VBcJ7JYP5jqpiwUuwgKjjQtsHWocKsfPVYsiBReiP%2Fw%2FJD9d0hWLPAvl%2FGwUoQr4bFveQxTTbh59G%2FUJx%2B%2BJO1vX3iAPLaLGSbEk7vWsyEDHlnCZKt3FftJ6rLlPlldzTLSl0dxjXUuYHXtwfHr2xT%2FMEkznvCxfYvhkRq2JqMrRFDs9HhYmgNKGSq22RTXpG6H6bvPj2CB1%2F2wKOAXbeZxnrtcWdnHlgE3xqOYwr1QaoL0w4llwGwGKIv5bQndF8MOiqDYIKZmWoH%2Bd3oQRfX2lFsBx3Ou1VDc4T28PkN8nPUnAx5OZ%2Fqu4A%2FWAbNnxM6L9%2B0kwDU0ijXro%2FjKNaTynYmqzNHVei6MTeEv7l2IaBV4eYZcU76jNIa8qPntGZjfCNm3nHHoTalPj6jYVYQJLGGe5OAa5U5YLm%2FczFhjPNQdBW5QsUaFEdccAV5QDYoQdaQba%2FnuTXvPS2147LYNdNMiQsi1M5peEhe89kaIitGONn9GOBXdeh2OBIrfRDYVICmQKjDjlbqHBjqlAUlaHQsfcgpG0NXSVM4q0XaxTWUQs117DKno2d5kJpur35M%2Bmk1ywaOg%2BQQs1elOD5lWUW7iQU8OKP6OFFe4pEMQlM02lz%2BtdNCy7aUQ%2FBVl43buUyDgciDI5DTbhEJe0LZuv1Yf0bGhuhtS%2FZhesqgbAlMVTwy8TiKPd7hE3%2FfsrThEtrgvrAMVSr4hbrZSDItfdsFb976epf%2BZt%2Fb5aTsz%2BxHzgA%3D%3D&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAXKQOIN7STXK57JEK/20210714/eu-west-2/s3/aws4_request&X-Amz-Date=20210714T082753Z&X-Amz-SignedHeaders=host;x-amz-security-token&X-Amz-Signature=bc30d0325591bbb5a315440fcf3dc815b4339678282e737f7422fd926aba0d51"
  ],
  "expiration": "2021-07-14T08:42:53.6452618Z"
}
```

When the file has been uploaded, you will still need to use the main `POST` endpoint of the relevant API to store your file to a customer's file system. Rather than sending the base64 encoded file content in the `fileData` property, you should use the `fileUrl` property and send the pre-signed URL that the file was sent to. The platform will then transfer the file from the holding area to the relevant customer's file system. It is not necessary to include all the query string parameters from the pre-signed URL in the subsequent `POST`, as per the example below

```
POST /documents
{
  "associatedType": "property",
  "associatedId": "OXF190347",
  "typeId": "DET",
  "name": "24 Smithson Road Details.pdf",
  "fileUrl": "https://reapit-file-uploads-prod.s3.eu-west-2.amazonaws.com/443e4a98-dfcb-4345-abb2-e52031928ed1",
}
```

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

In some systems, when multiple systems perform updates at the same time without knowledge of each others changes, you can be left with the problem of **lost updates** whereby the last update "wins" and previous updates are lost. Our APIs enforce o[ptimistic concurrency control](https://en.wikipedia.org/wiki/Optimistic\_concurrency\_control) to help avoid this problem.

We use [entity tags](https://tools.ietf.org/html/rfc7232#section-2.3) as an indicator of the current version of any resource returned from our APIs and whenever a singular representation is served by any of our `GET` endpoints, it will include `eTag` in the response header. For convenience, we also include this as an `_eTag` attribute in the response for each object.

This gives both client and server a means of understanding the version of a particular resource an application has received. Subsequently when a resource is updated, it's `eTag` value will also be updated.

To ensure that updates aren't lost, you must include an `If-Match` header in your `PATCH` request containing the `eTag` value exactly as you received it **including quotation marks.** The server will then compare its version of the resource with the `eTag` you provided.

* If they match, then the update is intended for the same version of the resource and the request will be processed&#x20;
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

### Deprecation

Whenever a new version is released, the previous version enters its sunset period. This is presently six months though will be reviewed as our platform continues to grow and evolve.

At the end of a versions sunset period it will become deprecated and you will be required to adopt more recent version. You will be notified if your application is using a version that is soon to be deprecated.

{% hint style="info" %}
**Stay up to date:** please see the [help section](https://marketplace.reapit.cloud/developer/help) of our developer portal for information on recent and upcoming changes.
{% endhint %}

## Metadata

Our metadata system allows you to easily extend the data that our platform supports. Most of our POST and PATCH endpoints provide the ability to attach a JSON document to our entities which will be automatically included in future fetches of that entity.&#x20;

We also provide specific metadata endpoints for more direct, granular control on the data you provide. You can use these same endpoints to build new, standalone entities that are specific to your application without needing to hosting your own datastore.&#x20;

Metadata is specific to a customer and any data that your application sets will not be made available to users of your application who represent a different customer. We do not recommend using metadata storage for any sensitive information (personally identifiable details, bank accounts, etc).

### Attaching metadata to our entities

The easiest way to work with metadata is to populate the `metadata` attribute on our existing endpoints. You can provide a JSON document in the `PATCH` or `POST` payload as below:&#x20;

```javascript
{
  <rest_of_payload>
  ...
  "metadata": {
    "MyCustomField1": "MyCustomValue1",
    "MyCustomField2": true
  }
}
```

Once metadata has been set against an entity, it will be automatically returned in the same format for future `GET` requests originating from your app.&#x20;

For more granular control, you can use our dedicated metadata endpoints to create, update and retrieve outside of the context of one of our Foundations endpoints.

### Creating custom entities

You can use these metadata endpoints to use Foundations as a simple datastore. You can create a standalone entity by providing a custom `entityType` with your JSON payload. You can then fetch, filter and update your entity using the `/metadata` REST endpoints we provide.

```javascript
{
  "entityType": "myCustomEntityType",
  "entityId": "75c46440-5cb9-4db1-801d-f57eab8999e2",
  "metadata": {
    "CustomStringField": "my string",
    "CustomBoolField": false,
    "CustomNumericField": 100.5,
    "CustomDateField": "2019-06-15T13:45:30Z"
  }
}
```

If you'd like to associate your custom entity with an entity your hold outside of Foundations, you may pass in an `entityId` which you can later use for searching/filtering. If you do not, an `entityId` will be generated and returned to you automatically.&#x20;

### Validating custom entities

Our `metadataSchema` endpoints allow you to provide a [JSON Schema](https://json-schema.org/) to validate the metadata JSON document that you provide the platform. Once you associate a schema with a custom entity type, you it will be used to validate future metadata submissions for entities of that type. If this content does not conform with the JSON schema you've provided for that entity type, the request with fail with a `422 Unprocessable Entity` response and a[ listing of the reasons why validation](api-documentation.md#request-validation) failed. For more information, see our Swagger documentation.

### Searching for metadata

Once metadata has been set against an entity, its content can then be used to re-locate that entity by using your metadata as a search term. The `metadata` query string parameter accepts a filter expression to identity the record(s) required in the following prescribed format:

`GET /<endpoint>?metadata=metadata.<fieldName> <operation> <criteria>`

Failure to adhere to the format required will provide a `400 Bad Request` response detailing the problem. If you are having trouble, consult our example [usage guide](api-documentation.md#example-usage) below.

### Search operations

We support querying using up to eight different filter operations, depending on the data type of the metadata field you’re searching upon.

| **Operation**            | **Keyword** | **Information**                                                                                                                     |
| ------------------------ | ----------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Equals                   | **$eq**     | Works for all data types                                                                                                            |
| Not equals               | **$ne**     | Works for all data types                                                                                                            |
| Greater than             | **$gt**     | Works for datetime and numeric data types                                                                                           |
| Less than                | **$lt**     | Works for datetime and numeric data types                                                                                           |
| Greater than or equal to | **$gte**    | Works for datetime and numeric data types                                                                                           |
| Less than or equal to    | **$lte**    | Works for datetime and numeric data types                                                                                           |
| In list                  | **$in**     | Provide a comma separated list of values to check for the value provided within. Works for string, datetime and numeric data types. |
| Not in list              | **$nin**    | Provide a comma separated list of values to check for the value provided within. Works for string, datetime and numeric data types. |

### Example usage

| Criteria Type | Example filters                                                                                    | Information                                                            |
| ------------- | -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Boolean**   | metadata.myBooleanField $eq true                                                                   | Only works for `$eq` and `$neq`. Criteria must be either true or false |
| **Numeric**   | <p>metadata.myNumericField $gte 100</p><p>metadata.myNumericField $nin 30,50,60,100</p>            | Criteria decimal places                                                |
| **String**    | <p>metadata.myStringField $neq ‘London’</p><p>metadata.myStringField $in ‘red’,’brown’,’green’</p> | Criteria must be contained within apostrophes                          |
| **DateTime**  | <p>metadata.myDateField $lt 2020-11-05T13:15:30Z</p><p>metadata.myDateField $eq 2020-11-05</p>     | Time component is optional. Must be provided in ISO 8601 format.       |

### Additional information

* Metadata filtering is not case sensitive
* Metadata filter expressions are additive and can be used any number of times by providing the `metadata` query string more than once
* Metadata filter expressions can be used in conjunction with any other query string parameter that an endpoint makes available. &#x20;
* Metadata filtering can use the dot notation format to search for data stored in a nested structure.

## Hypermedia

Our APIs are **REST level 3**[ ](https://restfulapi.net/richardson-maturity-model/)and implement [hypermedia controls](https://restfulapi.net/richardson-maturity-model/) to improve the developer experience of using our platform. Hypermedia makes our APIs self documenting, easier to use and aids discovery. We adopt the [HAL hypertext application language](http://stateless.co/hal\_specification.html) to serve as our message format.

### Links

Each `GET` response provides a uniform interface to present links to demonstrate **which** data is related and **how** that data can be retrieved. This is particularly useful for APIs that present complex systems of interrelated data, such as ours.

&#x20;Each resource, including [collection resources](api-documentation.md#pagination), include a `_links` collection to present related data. The responses `_links` dictionary will include a **key** to represent the type of relationship and a **value** to represent the location where the related resources can be obtained from.

The **condensed** `GET /contact/{id}` payload example below demonstrates how relationships are presented:

```
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

### Embedding data

Many of our GET APIs provide the ability to compose requests that automatically **embed related data** in their responses. This is a convenient tool that reduces the number of round trips your application needs to make to our Platform. Using this mechanism can result in improved application performance with less API interaction code required.

If your application requires data from one or more related resource(s) (indicated by a link), you can simply specify the name of the related resource in the `embed` parameter and our APIs will do the rest. So long as the related data exists, it is returned to your app in the correct resource(s) `_embedded` data collection.

{% hint style="info" %}
This mechanism allows your application to make fewer round trips to the server by allowing our APIs to make requests on your applications behalf. Any request triggered by the embed mechanism will still contribute to your usage statistics in the same way as if they were directly issued from your application.
{% endhint %}

You can embed as many related data sources in a request as your application requires. Our [interactive API explorer](https://marketplace.reapit.cloud/developer/swagger) provides a user interface which demonstrates the available `embed` parameter options for each API.

#### Example

`GET /contacts/OXF18000001/?embed=offices&embed=negotiators`

The request above illustrates the means of requesting that related office and negotiator resources are included with the response from the contacts API. The condensed response below demonstrates how these related resources are returned within the contacts payload in the `_embedded` attribute.

```
{
  "id": "OXF18000001",
  "title": "Mr",
  "forename": "John",
  "surname": "Smith",
  "officeIds": [
    "OXF"
  ],
  "negotiatorIds": [
    "JAS"
  ],
  
  <rest of contacts payload>
  
  "_links": {
    "self": {
      "href": "/contacts/OXF18000001"
    },
    "offices": {
      "href": "/offices/?id=OXF"
    },
    "negotiators": {
      "href": "/negotiators/?id=JAS"
    }
  },
  "_embedded": {
    "offices" : [
      {
        "id": "OXF",
        "name": "Oxford",
        "manager": "David Brown",
        "address": {
          "buildingName": "",
          "buildingNumber": "1a",
          "line1": "Wellington Square",
          "line2": "Brownhaven",
          "line3": "Oxford",
          "line4": "",
          "postcode": "OX1 2JD"
        },
        
        <rest of offices payload>
      }
    ],
    "negotiators" : [
      {
        "id": "JAS",
        "name": "John Smith",
        "jobTitle": "Senior Negotiator",
        "active": true,
        "officeId": "OXF",
        "email": "drew.mcculloch@reapitestates.net",
        
        <rest of negotiators payload>
      }
    ],
  }
}
```

##

