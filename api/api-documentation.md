# Platform

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
| GET | Retrieve a resource or collection of resources |
| POST | Create a new resource |
| PUT | Update an existing resource by replacing it with the content of the payload |
| PATCH | Partially update an existing resource by only including the fields to replace in payload |
| DELETE | Soft delete an existing resource |

### Response codes

We use standardised HTTP status codes to indicate the outcome of a request. Below is a listing of the codes our APIs may return and their meaning.

* Codes in the `2xx` range indicate that the request was fulfilled successfully. 
* Codes in the `4xx` range indicate an error caused by the information provided.
* Codes in the `5xx` range indicate an error with our APIs.

| Code | Title | Description |
| :--- | :--- | :--- |
| `200` | `OK` | The request has been fulfilled. |
| `201` | `Created` | The request has been fulfilled and a new resource has been created.  |
| `204` | `No content` | The request has been fulfilled but there is no need to send any data back.  |
| `400` | `Bad request` | The request was not understood by the server. This is generally due to bad request syntax. |
| `401` | `Unauthorized` | The provided authentication credentials are incorrect or not present. Generally, this is due to the lack of an "Authorization" header |
| `403` | `Forbidden` | The authentication credentials request do not provide sufficient scope to fulfill the request |
| `404` | `Not found` | The requested resource was not found. |
| `412` | `Precondition failed` | The was not fulfilled because preconditions provided bu the client could not be met. Usually occurs during PATCH operations when the eTag provided in the 'If-Match' header is out of date. |
| `422` | `Unprocessable entity` | A validation error has occurred. The error response body will provide additional information on the failure\(s\). |
| `429` | `Too many requests` | The request was not accepted because the application has exceeded the rate limit.  |
| `500` | `Internal error` | The request triggered an unexpected error which will be logged and investigated. |

### Errors

In addition to the relevant response code, unsuccessful requests will return a JSON encoded error response:

| Attribute | Description |
| :--- | :--- |
| `statusCode` | An integer response code that issued by this error |
| `dateTime` | UTC formatted timestamp of when error response was issued |
| `description` | Human readable message providing more details about the error. |
| `errors` | A collection of validation issues with the provided payload. Only populated for `422 Unprocessable entity` errors. |

## Developer Sandbox

You can use the Foundation API in Sandbox mode which provides a set of demonstration data that can be interacted with without affecting any client environment.

Upon registering with our developer portal, you can immediately get familiar with the functionality our APIs offer and enjoy a hurdle free route to start developing your application

Sandbox mode supports processing of all read and write requests so that you can build and test in confidence before submitting your application to our Marketplace.

To access the sandbox, you'll need to register for a developer account at our Portal. You're then able to simply use those credentials provide them to our Authorization services in the normal way. The access token generated for your developer credentials will point our APIs at your sandbox data.

Alternatively, our Interactive API Explorer will automatically grant access to sandbox data when you're logged into the Developer Portal.

## Rate limits

You can make 1000 requests per minute to our APIs. Each response will include HTTP headers to provide information on the current rate limit statistics.

| Header | Attribute |
| :--- | :--- |
| X-RateLimit-Limit | The number of requests that a client is allowed to issue per minute |
| X-RateLimit-Remaining | The number of requests that a client is allowed to issue in the current rate limit window before hitting the limit |
| X-RateLimit-Reset | The unix timestamp at which the current rate limit window resets |
| Retry-After | When the rate limit is hit, this header presents the number of seconds to wait before attempting another request |

If the rate limit is hit, a response similar to below will be issued:

```javascript
HTTP/1.1 429 Too Many Requests X-RateLimit-Limit: 1000 X-RateLimit-Remaining: 0 X-RateLimit-Reset: 1402010983 Retry-After: 30Content-Type: application/json
{
  "statusCode": 429,
  "dateTime": "2019-04-23T18:25:43.511Z",
  "description": "Rate limit for API requests has been hit.
                  Your limit is 1000 requests per minute.
                  This limit will be reset in 30 seconds."
}
```

## Pagination

Top level API resources provide functionality to return a list of resources in bulk. For example, `GET /contacts` will return a list of contact resources in a single response.

For reasons of performance and practicality, these APIs enforce paging and require a standardised set of query strings in their requests. The `pageSize` and `pageNumber` parameters are used to cycle through the available results from a top level API. 

Paged responses are issued in the following structure:

| Attribute | Description |
| :--- | :--- |
| `pageSize` | The number of records that have been retrieved by this response |
| `pageNumber` | The page number that this response represents |
| `pageCount` | The number of available pages worth of data, based on the current responses `pageSize` |
| `totalCount` | The total number of resources available that fulfill the criteria of the current request |
| `_embedded` | The list of resources that have been returned in this paged response |

### Request

Unless documented, the default page size is 25 and the maximum is 50.

```text
http://foundations.reapit.com/contacts?pageSize=10&pageNumber=2
```

### Response

```javascript
Content-Type: application/json
{
  "pageNumber": 2,
  "pageSize": 10,
  "pageCount": 10,
  "totalCount" : 142,
  "data" : [
    ...
  ]
}
```

## Metadata

Our resources that can be updated support a `metadata` attribute in their request and response payload. This attribute can be used to attach key-value data against resources specific resource 



a JSON data fragment against a specific resource by including the metadata attribute in POST and PATCH requests. This will subsequently be included in future fetches of that resource.

Metadata should be used to store additional, structured information against an object. This allows our clients to build upon the resource returned by the API and create a point of integration between our platform and third party applications. A common use case would be to store a unique identifier from an external system.

Once metadata has been submitted to a representation, a JSON schema is built and used to validate future metadata submissions to the same endpoint to keep ensure that data is valid and consistent.

Information stored in metadata is specific to your application and is not available to other Reapit or third party applications. Do not store any sensitive information \(personally identifiable information, bank details, etc.\) as metadata.

{% hint style="info" %}
**Coming soon**: we will add the ability to search for resources that match specific metadata content. See our [project milestone](https://github.com/reapit/foundations/milestone/10) for further details.
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

