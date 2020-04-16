---
description: How to manage authentication of Reapit users with our hosted identity solution
---

# Reapit Connect

## Overview

Reapit Connect is our hosted identity solution designed to allow applications to securely authenticate Reapit users against a single, trusted identity. Backed by our OpenID Connect compliant system, it is quick and easy to build applications that adhere to best security practices and extend an excellent experience to your users.

**Building your application with Reapit Connect is our recommended way to interact with our Platform.**

## Why use Reapit Connect

### Simplicity

Reapit Connect removes the overhead of having to build and maintain a user credential directory for your app. Instead, users can be securely authenticated against a single, trusted Reapit identity.

### **Security**

Our identity provision is an implementation of OpenId Connect, the defacto industry standard for authentication and authorisation for web and mobile applications. Simply put, you don't need to worry about securely capturing or storing user credentials - we do that part for you.

### Single sign on

Reapit Connect supports single sign on \(SSO\) to allow authenticated sessions to be shared between any application using Reapit Connect to manage its authentication. The experience of interacting with your application is streamlined as users aren't re-prompted for their credentials.

### Cross platform

You can use Reapit Connect to authenticate users regardless of your front or back end technologies. Reapit Connect is agnostic of technology and integration is as simple as a redirect to our hosted login screen and a subsequent REST API call.

### Trust

Your users will be presented with a unified login screen from a brand they already know and trust. They will receive the same user experience as they do from other Reapit applications and of those that exist in our marketplace.

## Marketplace integration

### Registering your application

Registering your app in our Marketplace is the first step for it to be able to interact with Reapit customer data.

Our [application submission page](https://marketplace.reapit.cloud/developer/submit-app) will capture information about your application, including the details required for integration with Reapit Connect.

* Select **Authenticate with Reapit Connect** as your required authentication flow _\*\*_
* Provide one or more **redirect URLs** and a **logout URL** to define the acceptable URLs that Reapit Connect is permitted to redirect back to after a successful authentication or logout

Once you have successfully registered, you will be issued with a client id. You can obtain this by clicking your app in the [My Apps](https://marketplace.reapit.cloud/developer/apps) area of our developer portal.

### Customer installation

In order for Reapit Connect to authenticate your application on a users behalf, the user must belong to a Reapit customer that has opted to allow your application access to their data.

Customer administrators are able to control your applications access by choosing to install from our Marketplace. As part of this process, they will grant your application with any permissions \(scopes\) it requires to interact with Foundations API endpoints.

{% hint style="info" %}
**You can test Reapit Connect** with our [sandbox environment](api-documentation.md#sandbox-mode) which does not require the customer installation step. Simply provide your developer portal credentials when Reapit Connect prompts for a username and password.
{% endhint %}

## Authentication flow

OAuth 2.0 is an authorization framework that we use to allow a user to grant limited access to resources in our Foundations platform without having to expose their credentials.

We use the [Authorization Code Grant](https://developer.okta.com/blog/2018/04/10/oauth-authorization-code-grant-type) _\*\*_flow to authenticate, which is broken down into the following steps.

* Your application redirects the user to our Reapit Connect in the browser
* Reapit Connect presents the user with a login screen to capture their credentials
* Reapit Connect will direct the browser back to your application with an authorization code in the query string
* Your application exchanges the authorization code for tokens with a REST API call  

### Direct user to Reapit Connect

To initiate a login, your application should redirect users to our authorize endpoint:

`https://dev.connect.reapit.cloud/authorize?response_type=code&client_id=<client id>&redirect_uri=<redirect url>&state=<state>`

| Parameter | Description |
| :--- | :--- |
| `response_type` | The type of authentication flow that Reapit Connect should initiate. At present, this must be set to **code** |
| `client_id` | The unique client id that was issued to your application after registration |
| `redirect_uri` | The URL to redirect back to once the user has been authenticated. This must **exactly match** one of the URL's you provide during app registration |
| `state` | Optional parameter to pass state to our hosted login screen. Upon successful login, it will be returned back to you. |

### Present login form

The user will be presented with a Reapit branded login screen where they are required to input their credentials and submit. They can also initiate password recovery for their Reapit identity from this form.

This step will be automatically skipped if the user has an authenticated session with Reapit Connect. The user will immediately be redirected back to your app.

![](../.gitbook/assets/image%20%2817%29.png)

### Redirect back to your app

If the user provides valid credentials, Reapit Connect will redirect back to your application using the `redirect_uri` that was provided when [directing the user to Reapit Connect](reapit-connect.md#direct-user-to-reapit-connect).

A `code` parameter will be appended to the redirected URL, as well as any `state` you passed through to the authorize endpoint.

`https://your_redirect_url?code=<code>&state=<state>`

{% hint style="success" %}
**Reapit Connect** will only redirect to URLs that were added during app registration. This is a security measure to prevent malicious users attempting to impersonate your application.
{% endhint %}

### Exchange code for tokens

Once your application has successfully guided the user through the OAuth flow, you can extract the authorization code from the redirected URL. You are then able to use this code to exchange for JWT tokens for proof of authentication and access for Foundations resources. You can only attempt to exchange authorization codes once and they will expire 10 minutes after they have been issued.

To make the exchange, send a `POST` request to the endpoint below with Content-type set to `application/x-www-form-urlencoded`:

`https://dev.connect.reapit.cloud/token`

| Request payload | Description |
| :--- | :--- |
| `client_id` | The unique client id that was issued to your application after registration |
| `code` | The authorization code returned to you in URL |
| `grant_type` | Must be set to `authorization_code` |
| `redirect_uri` | The redirect URL that was submitted when [directing user to Reapit Connect ](reapit-connect.md#direct-user-to-reapit-connect) |

If your request is properly formed and valid, you'll receive a response similar to below.

```text
HTTP/1.1 200 OK
Content-Type: application/json

{ 
 "access_token" : "eyJz9sdfsdfsdfsd", 
 "refresh_token" : "dn43ud8uj32nk2je", 
 "id_token" : "dmcxd329ujdmkemkd349r",
 "token_type" : "Bearer", 
 "expires_in" : 3600
}
```

## Making authenticated requests

If the user successfully logged in and your application performed the code exchange, you will receive a JSON payload containing a series of tamper proof [JWT tokens](https://tools.ietf.org/html/rfc7519):

| Response payload | Description |
| :--- | :--- |
| `access_token` | Token to grant access to protected Foundations resources |
| `id_token` | Token containing claims about the users identity. |
| `refresh_token` | Token that can be issued to get a new id and access token. |
| `expires_in` | The number of seconds that the access token is valid for |
| `token_type` | The type of tokens issued. Will always be set to `bearer` |

### Using access tokens

Access tokens \(also known as bearer tokens\) are designed to provide your application with access to protected resources on the users behalf.

You can access Foundations API endpoints by including the access token as an `Authorization` header in all requests your application issues, subject to the scopes that your application requested during registration.

### Using identity tokens

Identity tokens are intended to provide proof of authentication with Reapit Connect. Your application should decode and [validate ](https://connect2id.com/blog/how-to-validate-an-openid-connect-id-token)the id token that it has been issued. There are a variety of [third party libraries](https://jwt.io/#libraries-io) to help accomplish this and **the token should not be trusted until validated**.

Once decoded, your application can inspect the claims that the id token includes. Claims provide information about the users identity such as the customer they work for, their email address and name which your application can make use of.

You can also issue a `GET` request to the following endpoint to get information on the user. Be sure to include your access token:

`https://dev.connect.reapit.cloud/oauth2/userInfo`

### Using refresh tokens

Access tokens issued from Reapit Connect will expire after 60 minutes. Refresh tokens provide your application with a means of retrieving a new set of tokens without requiring an interaction from the user. They are long lived and will continue to function until they are revoked.

To use a refresh token, issue a `POST` request to the endpoint below with Content-type set to `application/x-www-form-urlencoded`:

`https://dev.connect.reapit.cloud/token`

| Request payload | Description |
| :--- | :--- |
| `client_id` | The unique client id that was issued to your application after registration |
| `refresh_token` | The refresh token |
| `grant_type` | Must be set to `refresh_token` |

{% hint style="warning" %}
For recommendations on how to safely store and interact with tokens, please see our web integration module[ Cognito Auth](web.md#cognito-auth)
{% endhint %}

