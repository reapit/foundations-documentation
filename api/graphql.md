---
description: GraphQL Implementation of the Foundations API
---

# GraphQL

The Reapit GraphQL service is a GraphQL implementation of the Foundations API. It is a proxy service that sits on top of the Reapit Foundations Platform API which means both share the same domain model. The service exists as a convenience for developers to build web applications quickly and with minimal boilerplate, rather than an alternative standalone platform.

{% hint style="success" %}
Whilst the service is beta, because the aim of the project is to be schema compliant with the REST platform API, you can rely on no breaking changes to the schema itself
{% endhint %}

We have been using the service internally in production at Reapit - it powers the Geo Diary App, which is currently the most installed Reapit AppMarket application. Having completed this initial internal Beta, we are now excited to release it publicly for the first time.

### Basic Usage & Authentication

The GraphQL production  endpoint is `https://graphql.reapit.cloud/graphql`

Visiting this Url in your browser will load the GraphQL [playground](https://www.apollographql.com/docs/apollo-server/testing/graphql-playground/) where you can experiment with the service. If you are not familiar with Playground, it is an API explorer, like Swagger, but for GraphQL.

{% hint style="info" %}
You will need to authenticate any request made to the GraphQL service using Reapit Connect. The scopes for the clientId that generates your tokens must map 1:1 to the downstream platform endpoints queries by GraphQL.
{% endhint %}

There are two required headers in the service as per below, you will need to obtain your `accessToken` and `idToken` from your Reapit Connect session as normal. See the [developer portal](../developer-portal.md#5-get-your-client-id), [Reapit Connect](reapit-connect.md) and [Connect Session](../app-development/connect-session.md) sections of these docs for details on how to obtain these tokens.

```javascript
{
  "authorization": "<<idToken>>",
  "reapit-connect-token": "<<accessToken>>"
}
```

These headers need to be added to the http headers section of the playground for you to interact with the service, or to your GraphQL client of choice's fetcher. Internally we use Apollo Client to interact with the service - [see documentation on this here](https://www.apollographql.com/docs/tutorial/client/).

{% hint style="warning" %}
Because an idToken is required for authentication, the GraphQL service is not suitable for developers using the Client Credentials OAuth flow.
{% endhint %}

### Errors

Because the service is a platform proxy, it is very likely that errors from the GraphQL service are downstream platform issues rather than errors thrown by the service itself. For downstream errors, the service will return a 200 with an errors object in the payload. You should inspect this errors list for details of any failures downstream, even if the GraphQL service itself was able to respond correctly.

If the service itself throws an exception, it will be in the 4xx and 5xx scopes as normal. 401 errors are the most common - these are thrown by our API gateway owing to an invalid or missing `idToken`. See the basic usage section on how to set up your headers above. 

### Billing

No additional charges are applied for using the GraphQL service over the Foundations REST API. Since the service is a proxy, your consumption charges will be on the basis of the downstream API calls made by GraphQL service to the corresponding REST services. The normal fair usage and consumption rules apply.

### Known Limitations

* The service is already working in production with live customers, powering the Reapit Geo Diary app however, naturally with beta services there may be some issues. If you find a problem with the GraphQL service, please [open an issue here](https://github.com/reapit/foundations/issues/new?assignees=&labels=bug%2C+needs-triage%2C+graphql-server&template=bug_report.md&title=) and we will look at it as soon as possible.
* The objective of the project is to offer the an identical schema to the Foundations API, with no extension, modification or deviation. Objects returned from the service should map 1:1 to those seen in the [developer portal swagger document](https://developers.reapit.cloud/swagger).  There may however be some delay between when a property is updated in the main platform. If you find any inconsistencies between the platform API and the service, again please report as an issue - it is likely that the platform has updated and the service is yet to follow.
* The service is lacking two services that exist in the Platform Schema - Meta Data and Meta Data Schema. Owing to the strongly typed nature of GraphQL it is not possible to query arbitrary JSON structures that vary from developer to developer. This is likely to remain a limitation of the service going forward.

