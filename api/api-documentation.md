# Foundations Platform

## Overview

The Foundations API is organised around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). Our API has predictable resource-oriented URLs using standard HTTP response codes, authentication, and verbs. All requests and responses, including errors, are [JSON-encoded](http://www.json.org/).

You are able to use the Foundations API in sandbox mode to allow you to quickly test and develop your application without worrying about affecting the live data of our clients. The credentials you use to authenticate determine whether your request is issued to the sandbox environment or not. 

You can immediately start testing our APIs in sandbox mode by using our Interactive API Explorer. Alternatively, if you prefer to test using Postman, you can import our collection of example requests directly by simply clicking the button below.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/c69a1ca2deb44b40b393)

## Authentication

The Foundation platform uses [OpenID Connect](https://openid.net/connect/faq/) for authenticating requests. OpenID Connect is a protocol for authenticating users, built on top of the OAuth 2.0 specification.

HTTP requests to our protected endpoints must be issued with a secure JSON Web Token \(JWT\) access token. Requests are fulfilled if the token is valid, unexpired and fulfills the required scopes \(permissions\) that the endpoint requires.

Our OpenID Connect service can issue JWT tokens using two different authentication flows:

| Flow | Description |
| :--- | :--- |
| Authorisation code flow | For use by client and server side applications that have a user in context. Allows the implementing application to be authenticated on the behalf of the user.  |
| Client credentials flow | For use by server side applications that do not have a user in context \(machine to machine apps\). Allows the implementing application to be authenticated on behalf of itself. |

{% hint style="danger" %}
**Client credentials flow** should not be used for applications that are client side only. A server side component is required to be able to safely store credentials. 
{% endhint %}

### Registering your application

Your application must be registered with our Marketplace before it can interact with data, functionality and assets provided by the Foundations APIs. For more information on how to register your application, see our Marketplace documentation.

As part of the application registration process, you'll be required to choose the [scopes](https://oauth.net/2/scope/) that your application requires to function. After successfully authenticating, any JWT access token your application is issued will include the scopes you require, granting your application permission to the corresponding endpoints. 

Once your application has been successfully registered, you will be provided with a unique **client id** which is required to interact with our authentication services.

### Authorisation code flow



### Client installation

Once your application submission has been approved by Reapit, it will appear as a listing in our Marketplace. Reapit clients will then be able to interact with your application's details and potentially choose to install it.

As part of the installation process, clients are required to agree to the scopes that your application requires before your application becomes accessible to end users. Applications cannot interact with client data or assets without prior approval from the client.

Once installed, an application can access Foundation services on an end users behalf. The recommended way to achieve this is to use one of our Client Libraries, however you can interact directly with our APIs as detailed below.

### Create an authorization code

To create an OAuth [authorization code](https://oauth.net/2/grant-types/authorization-code/), direct users to the URL documented below where they'll be prompted to enter their credentials. The clientId parameter is required and provided during the Marketplace app registration process.

```http
GET https://foundations.reapit.com/oauth/authorize?clientId=xxxxxxxxxxxxxxxx
```

Upon success, the service will direct back to your application with an authorization code provided as a query string.

```text
https://application.company.com/?code=xxxxxxxxxxxxxxxx
```

### Exchange code for tokens

If your application has successfully guided the end user through the OAuth flow and obtained an authorization code, you need to send it along with the client id issued to your application during Marketplace registration to the following endpoint:

```text
POST https://foundations.reapit.com/oauth/access_token
  {
    "clientId" : "xxxxxxxxxxxxxxxx",
    "code" : "xxxxxxxxxxxxxxx"
  }
```

Issuing a request with a valid authorization code and client id will provide a response in the following format:

```javascript
Content-Type: application/json
{
  "id_token" : "xxxxxxxxxxxxxx"
  "refresh_token" : "xxxxxxxxxxxxxx",
  "access_token" : "xxxxxxxxxxxxxx",
  "expires_in" : 3600,
}
```

| Attribute | Description |
| :--- | :--- |
| id\_token | A JWT containing claims about the users identity. |
| refresh\_token | A refresh token that can be issued to get a new id and access token. |
| access\_token | A JWT to grant access to secured API resources for given set of scopes |
| expires\_in | A JWT to grant access to secured API resources for given set of scopes |

### Create a request

The access token must then be sent in the Authorization header to be able to access protected Foundation APIs.

```text
Authorization : Bearer <access token>
```

Upon recieving an access token, the Foundation will validate the token to ensure:

* The access token is valid, issued from the correct source and not tampered with&gt;
* The access token contains the required scopes to perform the action that the endpoint requires
* The applications access to the end users data has not been revoked.

## API Reference

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

We use standardised HTTP status codes to indicate the outcome of a request. Below is a listing of the codes our APIs may return and their meaning.

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
| `412 Precondition Failed` | The was not fulfilled because preconditions provided bu the client could not be met. Usually occurs during PATCH operations when the eTag provided in the 'If-Match' header is out of date. |
| `422 Unprocessable Entity` | A validation error has occurred. The error response body will provide additional information on the failure\(s\). |
| `429 Too Many Requests` | The request was not accepted because the application has exceeded the rate limit.  |
| `500 Internal Error` | The request triggered an unexpected error which will be logged and investigated. |

### Errors

In addition to the relevant response code, unsuccessful requests will return a JSON encoded error response as outlined below:

| Attribute | Description |
| :--- | :--- |
| `statusCode` | An integer response code that issued by this error |
| `dateTime` | UTC formatted timestamp of when error response was issued |
| `description` | Human readable message providing more details about the error. |
| `errors` | A collection of validation issues with the provided payload. Only populated for `422 Unprocessable Entity` errors. |

{% hint style="info" %}
**All responses** are issued with a unique request id, regardless of whether they were successful or not. You can find this in the `x-amzn-RequestId` response header. If you [report a bug](https://dev.marketplace.reapit.cloud/developer/help), be sure to include this id to allow us to examine your problem in greater depth.
{% endhint %}

## Sandbox Mode

You can use the Foundation API in Sandbox mode which provides a set of demonstration data that can be interacted with without affecting any client environment.

Upon registering with our developer portal, you can immediately get familiar with the functionality our APIs offer and enjoy a hurdle free route to start developing your application

Sandbox mode supports processing of all read and write requests so that you can build and test in confidence before submitting your application to our Marketplace.

To access the sandbox, you just need to be registered as a developer on our Portal. You're then able to simply provide those credentials to our Authorization services in the normal way. The access token generated for your developer credentials will point our APIs at your sandbox data.

Alternatively, our Interactive API Explorer will automatically grant access to sandbox data when you're logged into the Developer Portal.

## Validation

Our APIs allow you to extensively write data into the Platform as well as reading it back. To protect the integrity of our clients data, we enforce proper validation on all `POST` and `PATCH` requests

Should your request not pass the validation requirements of the endpoint, then you'll be issued a `422 Unprocessable Entity` error response. This will include a listing of validation problems and how you can solve. 

## Creation APIs

Our APIs support resource creation using the `POST` verb. When a creation request has been successfully fulfilled, you will receive a `201 Created` response. 

Since the creation of new resources is often asynchronous, we do not include the payload of the newly created resource in the `POST` response. Instead, we include the the location of where the new resource can be retrieved from in the `Location` header of the `POST` response.

## Update APIs

Our APIs support resource updates using the `PATCH` verb. When an update request has been successfully fulfilled, you will receive a `204 No Content` response.

As with resource creation, we do not include the update resource in the `PATCH` response. Instead, to receive the latest version of a resource after updating it, simply re-fetch the resource from using a `GET` request.

## Optimistic concurrency

Our APIs serve Platform functionality and data to various different applications and users at the same time, which needs to be managed carefully to avoid concurrency problems. 

In some systems, when multiple systems perform updates at the same time without knowledge of each others changes, you can be left with the problem of **lost updates** whereby the last update "wins" and previous updates are lost. Our APIs enforce o[ptimistic concurrency control](https://en.wikipedia.org/wiki/Optimistic_concurrency_control) to help avoid this problem.

We use [entity tags](https://tools.ietf.org/html/rfc7232#section-2.3) as an indicator of the current version of any resource returned from our APIs and whenever a singular representation is served by any of our `GET` endpoints, it will include `eTag` in the response header. For convenience, we also this as an `_eTag` attribute in the response for each object for both singular and collection based resources. 

This gives both client and server a means of understanding the version of a particular resource an application has received. When a resource is updated, it's `eTag` value will also be updated.

To ensure that updates aren't lost, you must include an `If-Match` header in your `PATCH` request containing the `eTag` value exactly as you received it **including quotation marks.** The server will then compare its version of the resource with the `eTag` you provided.

* If they match, then the update is intended for the same version of the resource and the request will be processed 
* If they do not match, then the resource has been updated since it was fetched. The request will be rejected with a `412 Precondition Failed` error response. You need to retrieve the latest version of the resource and replay your changes before attempting another update.

{% hint style="info" %}
**For more information** about entity tags and the implementation of conditional requests, please see [RFC 7232](https://tools.ietf.org/html/rfc7232)
{% endhint %}

## Pagination

Top level API resources provide functionality to return a list of resources in bulk. For example, `GET /contacts` will return a list of contact resources in a single response.

For practical and performance reasons, these APIs enforce paging and require a standardised set of query strings in their requests. The `pageSize` and `pageNumber` parameters are used to cycle through the available results from a top level API. 

Paged responses are issued in the following structure:

| Attribute | Description |
| :--- | :--- |
| `pageSize` | The number of records that have been retrieved by this response. Default is usually 25 and the maximum is usually 100. |
| `pageNumber` | The page number that this response represents |
| `pageCount` | The number of available pages based on the current response `pageSize` |
| `totalCount` | The total number of resources available that fulfill the criteria of the current request |
| `_embedded` | The list of resources that have been returned in this paged response |

## Metadata

Most resources that can be updated support a `metadata` attribute in their request and response payload. This attribute can be used to attach additional key-value data against a specific resource that your application can later use. 

The `metadata` attribute is populated in POST/PATCH payloads as below:

```javascript
{
  ...
  "metadata": {
    "MyCustomField1": "MyCustomValue1",
    "MyCustomField2": true
  }
}
```

Once `metadata` has been set against a resource, it will automatically be included as part of that resource for future fetches originating from the same application. Metadata is application specific and will not be presented to other applications. 

Our metadata system allows you to easily extend the data that our resources present. You can create a richer point of integration between your application and our platform and integrations are simplified the process by storing all relevant data in a single place. 

Please do not store any sensitive information \(personally identifiable information, bank details, etc.\) as metadata.

{% hint style="info" %}
**Coming soon**: we will add the ability to search for resources that match specific metadata content. See our [project milestones](https://github.com/reapit/foundations/milestones) for further details.
{% endhint %}

## Versioning

As we evolve our platform, new features will be added and fixes will be made. We categorise changes in two ways: **breaking** and **non-breaking** changes. We make every effort to implement changes as non-breaking wherever possible, however, there are sometimes situations that require this. 

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

