# Reapit Connect

## Overview

**Reapit Connect** is our hosted identity solution designed to allow applications to securely authenticate Reapit users against a single, trusted identity. 

Backed by our OpenID Connect compliant system, it is quick and easy to build applications that adhere to best security practices and extend an excellent experience to your users.

Building your application with Reapit Connect is our **recommended way** to interact with our Platform. Here's why:

### Simplicity

Reapit Connect removes the overhead of having to build and maintain a user credential directory for your app. Instead, users can be securely authenticated against a single, trusted Reapit identity and directed back to your application

We present information about the user on successful authentication that you can optionally use to register them in your own system, if you require. 

### Single sign on

Reapit Connect supports single sign on \(SSO\) to allow authenticated sessions to be shared between any application using Reapit Connect to manage it's authentication requirement. This means that if a user has already authenticated with Reapit Connect, that session is remembered and the experience of interacting with your application is streamlined as users aren't re-prompted for their credentials.    

### **Security**

Our identity provision is an implementation of OpenId Connect, the defacto industry standard for authentication and authorisation for web and mobile applications. 

OpenId Connect provides an authentication layer over the widely adopted OAuth 2.0 standard which allows your application to be authorised on behalf of a user. Simply put, you don't need to worry about securely capturing or storing user credentials - we do that part for you. 

### Cross platform

You can use Reapit Connect to authenticate users regardless of the front or back end technologies you have chosen for your application. Reapit Connect is agnostic of technology and integration is as simple as a redirect to our hosted login screen and a subsequent REST API call.

### Trust

Your users will be presented with a unified login screen from a brand they already know and trust. They will receive the same user experience as they do from other Reapit applications and of those that exist in our marketplace. 

## OAuth 2.0

OAuth 2.0 is an authorization framework that we use to allow a user to grant limited access to resources in our Foundations platform without having to expose their credentials.

We use the [Authorisation Code Grant](https://developer.okta.com/blog/2018/04/10/oauth-authorization-code-grant-type) ****flow to authenticate, which is broken down into the following steps.

* Your application redirects the user to our Reapit Connect in the browser
* Reapit Connect presents the user with a login screen to capture their credentials
* Reapit Connect will direct the browser back to your application with an authorization code in the query string
* Your application exchanges the authorisation code for tokens with a REST API call  

## Integrating with Reapit Connect 

### Register your application

Registering your app in our Marketplace is the first step for it to be able to interact with our clients data.

Our [application submission page](https://dev.marketplace.reapit.cloud/developer/submit-app) will capture information about your application, including the details required for integration with Reapit Connect. 

* Select **Authenticate with Reapit Connect** as your required authentication flow ****
* Provide one or more **redirect URLs** and a **logout URL** to define the acceptable URLs that Reapit Connect is permitted to redirect back to after a successful authentication or logout

Once you have successfully registered, you will be issued with a client id. You can obtain this by clicking your app in the [My Apps](https://dev.marketplace.reapit.cloud/developer/apps) area of our developer portal.

{% hint style="info" %}
**For more information** on how to register your application with our Marketplace, please see our [welcome guide](https://dev.marketplace.reapit.cloud/developer/welcome).
{% endhint %}

### Direct user to Reapit Connect

Once you have successfully registered your app, it will be provided with a unique client id. You can obtain your applications client id by clicking it's entry in [My Apps](https://dev.marketplace.reapit.cloud/developer/apps).

To initiate a login, you application should redirect users to our authorize endpoint:

`https://dev.connect.reapit.cloud/login?response_type=code&client_id=<client id>&redirect_uri=<redirect url>&state=<state>`

| Parameter | Description |
| :--- | :--- |
| `response_type` | The type of authentication flow that Reapit Connect should initiate. At present, this must be set to **code** |
| `client_id` | The unique client id that was issued to your application after registration |
| `redirect_uri` | The URL to redirect back to once the user has been authenticated. This must **exactly match** one of the URL's you provide during app registration |
| `state` | Optional parameter to pass state to our hosted login screen. Upon successful login, it will be returned back to you. |

### Capture user credentials

The user will be presented with a Reapit branded login screen where they are required to input their credentials and submit. They can also initiate password recovery for their Reapit identity from this form. 

This step will be automatically skipped if the user has an authenticated session with Reapit Connect. The user will immediately directed back to your app. 

![](../.gitbook/assets/image%20%281%29.png)

### Redirect back to your app

If the user provides valid credentials, Reapit Connect will redirect back to your application using the `redirect_uri` that was provided when [directing the user to Reapit Connect](reapit-connect.md#direct-user-to-reapit-connect).

A `code` parameter will be appended to the redirected URL, as well as any `state` you passed through to the authorize endpoint.

{% hint style="warning" %}
**Reapit Connect** will only redirect to URLs that were added during app registration. This is a security measure to prevent malicious users to impersonate your integration.
{% endhint %}



