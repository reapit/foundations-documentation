# Platform

To work with the Reapit Platform API you will need to follow these steps;

* Register with the developer portal [here](https://reapit.cloud.tyk.io/portal/)
* When you receive the confirmation email, login and request an API key. This is a manual process so it may take a while \(although it shouldn't!\).
* When you have the key navigate to `./src/constants` and rename the `.env.example` file to `.env`. 
* Copy your API key to the file next to the `REAPIT_API_KEY` variable.

You are good to go!

The API key should be included as an Authorisation header when fetching from the API. It is made available by webpack in the app by Webpack so you can reference it with `process.env.REAPIT_API_KEY`.

The schema defintion is fetched from a Swagger endpoint by running the command `yarn fetch-definitions`. This then parses the Swagger defs into TypeScript definitions, complete with comments and writes to the `./src/types/tyke-api-schema.ts` file. This file should be the only reference point for API data definitions **do not write your own interfaces for data!**

If you get an API runtime error because of an incorrect definition, firstly fetch the defintions again so they are up-to-date and if you still have a problem, raise an issue with the Platform Team to update the Swagger defintion.

## Authentication

Because the app has three distinct permissioned areas, you need different dev credentials to access each area of the site.

For a client, you can login at `/login` with `cbryan@reapit.com` and `T00lb0x53` For a developer, you can login at `/login` with `wmcvay@reapit.com` and `T00lb0x53` For an admin, you can login at `/admin/login` with `rwilcox@reapit.com` and `T00lb0x53`

## Foundations

## API Overview

The Foundations API is organised around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer) with all resources accessible using standard [HTTP methods](api-documentation.md#httpmethods) and returning predictable [response codes](api-documentation.md#statuscodes). All request and response bodies, including errors, are encoded in [JSON](https://en.wikipedia.org/wiki/JSON) and served over [HTTPS TLS v1.1+](https://en.wikipedia.org/wiki/Transport_Layer_Security) to ensure data privacy and security.

Our API resources are secured and require an [authorization JWT bearer token](https://en.wikipedia.org/wiki/JSON_Web_Token) to be submitted as part of requests sent to protected endpoints. For more information how our APIs are secured, please see [Authorization](api-documentation.md#authorization).

Alternatively, our [Developer Sandbox](api-documentation.md#developersandbox) provides a quick start experience to quickly get to grips with the platform and start developing.

## REST

### HTTP Methods

Foundation APIs present a uniform interface for performing CRUD \(create, retrieve, update, delete\) operations. Each endpoint adheres to REST guidelines to map the correct verb to the operation being performed. Our APIs support the following HTTP methods:

| Method | Action |
| :--- | :--- |
| GET | Retrieve a resource or collection of resources |
| POST | Create a new resource |
| PATCH | Partially update an existing resource by only including the fields to replace in payload |
| DELETE | Soft delete an existing resource |

### Response status codes

Foundation APIs use standardised HTTP status codes to indicate whether a request has been successful or has resulted in an error. Below is a listing of the codes our APIs may return and their meaning:

| Code | Title | Description |
| :--- | :--- | :--- |
| 200 | OK | The request has been fulfilled. |
| 201 | Created | The request has been fulfilled and a new resource has been created. |
| 202 | Async created | The request has been accepted will be fulfilled asynchronously |
| 400 | Bad request | The request was not understood by the server, generally due to bad syntax or because the "Content-Type" header was not correctly set to `application/json`. |
| 401 | Unauthorized | The provided authentication credentials are incorrect or not present. Generally, this is due to the lack of an "Authorization" header |
| 403 | Forbidden | The provided authentication credentials do not provide the request with sufficient scope to fulfil the request. |
| 404 | Not found | The requested resource was not found |
| 422 | Unprocessable entity | A validation error has occurred. The error response body will provide additional information on the failure\(s\). |
| 429 | Too many requests | The request was not accepted because the application has exceeded the rate limit. See Rate Limit for an overview of this mechanism |
| 500 | Too many requests | The request was not accepted because the application has exceeded the rate limit. See Rate Limit for an overview of this mechanism |



## Authorization

The Foundation platform uses [OpenID Connect](https://openid.net/connect/faq/) \(OIDC\) as it's Authentication protocol, based on the OAuth 2.0 specification.

Our authentication mechanisms allow you to quickly build apps on top of our platform and provide a seamless authentication experience for your end users.

### Registering your application

Your application must be registered with our Marketplace before it can interact with data, functionality and assets provided by the Foundations API. For more information on how to register your application, see our Marketplace documentation.

As part of creating your application, you'll be required to choose the [scopes](https://oauth.net/2/scope/) that you application requires. Scopes govern the actions that your application can perform against our services. Each endpoint will detail the scopes that an application must be granted in order to interact with it.

Once your application has been successfully registered, you will be provided with a unique application id which is required to interact with our authorization services.

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

```

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

## Developer Sandbox

You can use the Foundation API in Sandbox mode which provides a set of demonstration data that can be interacted with without affecting any client environment.

Upon registering with our developer portal, you can immediately get familiar with the functionality our APIs offer and enjoy a hurdle free route to start developing your application

Sandbox mode supports processing of all read and write requests so that you can build and test in confidence before submitting your application to our Marketplace.

To access the sandbox, you'll need to register for a developer account at our Portal. You're then able to simply use those credentials provide them to our Authorization services in the normal way. The access token generated for your developer credentials will point our APIs at your sandbox data.

Alternatively, our Interactive API Explorer will automatically grant access to sandbox data when you're logged into the Developer Portal.

## Errors

Unsuccessful requests return an error response in JSON format. This includes a status code, a time stamp and textual description of the error:

```text
Content-Type: application/json
{
  "statusCode": 404,
  "dateTime": "2019-04-23T18:25:43.511Z",
  "description": "Contact RPT19000001 was not found."
}
```

Validation errors will also include a breakdown of the problems with the submitted payload:

```text
Content-Type: application/json
{
  "statusCode": 422,
  "dateTime": "2019-04-23T18:25:43.511Z",
  "description": "The submitted payload has failed validation.
                  See the errors list for more information.",
  "errors": [
    {
      "field" : "caption",
      "message" : "Must be less than 50 characters in length."
    }
  ]
}
```

## Rate limits

You can make 1000 requests per minute to our APIs. Each response will include HTTP headers to provide information on the current rate limit statistics.

| Header | Attribute |
| :--- | :--- |
| X-RateLimit-Limit | The number of requests that a client is allowed to issue per minute |
| X-RateLimit-Remaining | The number of requests that a client is allowed to issue in the current rate limit window before hitting the limit |
| X-RateLimit-Reset | The unix timestamp at which the current rate limit window resets |
| Retry-After | When the rate limit is hit, this header presents the number of seconds to wait before attempting another request |

If the rate limit is hit, a response similar to below will be issued:

```text
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

All collection API resources can be paged and share a common structure in their responses. Page size and offset is controlled by use of standardised query strings.

### Request

Unless documented, the default page size is 25 and the maximum is 50.

```text
http://foundations.reapit.com/contacts?pageSize=10&pageNumber=2
```

### Response

```text
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

## Resource expansion

Some of the top level resources made available by the platform include resource expansion functionality. When fetching data from a resource expansion enabled endpoint, clients can optionally request that a response includes data from one or more related resources.

This ability is to designed to reduce the number of required client-server roundtrips to obtain the data that a client needs for a specific use-case.

Query parameters are used to govern this functionality, please see the specific documention of each end point for details.

### Request

The example request below will fetch a list of contacts with resource expansion enabled for the identity checks nested collection:

```text
http://foundations.reapit.com/contacts?embed=identityChecks
```

### Response

A paged response from the`/contacts`request example above:

```text
Content-Type: application/json
{
  "data" :
  [
    {
      "id" : "RPT1900001",
      "title" : "Mr",
      "forename" : "David",
      "surname" : "Smith",
      ...
      "embedded": {
          "identityChecks" :
          [
            {
              "id" : "RPT1900050",
              "contactId" : "RPT1900001",
              "status" : "pending",
              ...
              }
            ]
        }
      }
  ],
  "pageNumber": 1,
  "pageSize": 25,
  "pageCount": 25,
  "totalCount" : 142,
}
```

## Metadata

Resources that support editing have a`metadata`attribute available in their payload. This attribute can be used to set a JSON data fragment against a specific resource by including the metadata attribute in POST and PATCH requests. This will subsequently be included in future fetches of that resource.

Metadata should be used to store additional, structured information against an object. This allows our clients to build upon the resource returned by the API and create a point of integration between our platform and third party applications. A common use case would be to store a unique identifier from an external system.

Once metadata has been submitted to a representation, a JSON schema is built and used to validate future metadata submissions to the same endpoint to keep ensure that data is valid and consistent.

Information stored in metadata is specific to your application and is not available to other Reapit or third party applications. Do not store any sensitive information \(personally identifiable information, bank details, etc.\) as metadata.

## Versioning

## Elements

The Elements UI toolkit you can browse [here](https://github.com/reapit/foundations-documentation/tree/db0718c9be27b7760dfae34e69518806acf0e855/developer/elements/README.md) is available as an NPM package. We also support an AMD \(require.js\), version that may suit your needs better, especially when serving content from a CDN or CMS.

## React App Scaffolder

Content

## Cognito Auth

Content

## Foundations TS Definitions

If you are using TypeScript \(and we recommend you do!\), for your front end project, we provide full type definitions for the API documented in the [API explorer](https://github.com/reapit/foundations-documentation/tree/db0718c9be27b7760dfae34e69518806acf0e855/developer/swagger/README.md). We generate these types from the Swagger contracts direct so you can be sure that when the API changes, your types will be updated also. This allows for a much closer alignment between front and back end development and ultimately more robust applications.

