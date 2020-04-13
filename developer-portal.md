---
description: A step-by-step guide to getting started in the developer portal
---

# Developer Portal

We want getting started with the Developer Portal to be as frictionless as possible. There is a lot of detail in the documentation for advanced concepts but to get started in as little as 5 mins with an authenticated marketplace app, you just need to follow these steps:

### 1. Login to the Portal

You will receive an email with a link to the developer portal and temporary login credentials. The app will redirect you to the [Reapit Connect](api/reapit-connect.md) login screen and then back to the authenticated portal. 

The first screen you will see is the apps page which initially will be empty:

![](.gitbook/assets/screenshot-2020-02-16-at-13.33.56.png)

When you are in the portal, navigate to the API tab on the left hand side menu. 

### 2. Choose an API

Assuming you have an idea of the data types / entities you are interested in, ensure that the endpoints you need are available in the platform by "trying out" the API explorer. 

![](.gitbook/assets/screenshot-2020-02-16-at-13.42.53.png)

For the purposes of this example my app will need Applicant data. Don't worry if you find you need other endpoints later, you can add them at any time.

![](.gitbook/assets/screenshot-2020-02-16-at-13.43.21.png)

### 3. Register an app

The next step is to register an app. We understand you won't have any code yet, this is all about setting up a client to work with the API.

The first step is to upload the listing details of your app. Eventually they will be the client facing details of your application in the marketplace.

![](.gitbook/assets/screenshot-2020-02-16-at-13.40.23.png)

You then need to select an OAuth Authentication flow:

If your application is **user facing**, you should select "Authorization Code". This will allow you to use our hosted authentication service, [Reapit Connect](api/reapit-connect.md#overview). As part of this flow, you need will need to register one or more call back URLs and a log out URL to allow Reapit Connect to direct traffic back to your application in a secure way.

If you are developing a **server-side machine to machine** application such as a feed to another system, you should select "Client Credentials". You can find details on how this flow works in our [platform documentation](api/api-documentation.md#authentication).

For the purposes of this example, because we are building a client side app, we will select "Authorization Code".

![](.gitbook/assets/screenshot-2020-02-16-at-13.40.37.png)

The next section is applicable only if you want to restrict the marketplace listing to a single or limited sub-set of clients, for example if you are building some private in-house tooling. For the public beta we don't support surfacing the client ids you wish to restrict to since the marketplace is not live however, if you want your app to be private, you can select "yes" and ignore the customer code list. For most users, you will select "no".

![](.gitbook/assets/screenshot-2020-04-10-at-14.41.09.png)

Then select an icon and some screengrabs for your app listing...

![](.gitbook/assets/screenshot-2020-02-16-at-13.40.48%20%281%29.png)

...this step is for server side apps only and should be skipped if you are building a web-based marketplace listed app; if however you are building an integration that you don't want to appear in the marketplace, you can select this option. You app will still be listed for permission only purposes however, it will not be possible to launch from within the Agency Cloud desktop app. For the purposes of this example, we will leave unchecked...

![](.gitbook/assets/screenshot-2020-02-16-at-13.41.05.png)

...then select the permissions \(OAuth scopes\) you need for your app to work. They must map to the endpoints you selected at point two above.

![](.gitbook/assets/screenshot-2020-02-16-at-13.41.15.png)

Finally, submit the form and you will return via a success message to the Apps page where you will see your registered application.

![](.gitbook/assets/screenshot-2020-02-16-at-13.44.57.png)

It is important to note, the app is not live yet, both because as we in developer beta only and because to set the live status, you need to edit your app and set the 'listed' status for approval. This behaviour is out of scope for this document.

### 4. Get your Client Id

From the Apps screen above, you will need to obtain your application's client id to authenticate your new app. To do this, click on the app to bring up the App Detail modal as above.

![](.gitbook/assets/screenshot-2020-02-16-at-13.45.15.png)

The Client Id should now be visible. Keep this page open so you can copy the Client Id at the next step.

### 5. **Write some code!**

The first step with your application will be to authenticate it against our Platform APIs. To do this you will need to use our authentication service [Reapit Connec](api/reapit-connect.md)t which supports the OAuth protocol. To make this easier on the client side, we have some JavaScript helpers you might find useful in our [Cognito Auth ](api/web.md#cognito-auth)module, however, if you are familiar with OAuth, you can just roll your own.

If you intend to use React for your Web Application, or are just interested in how we handle client side authentication at Reapit, you may want to read on as this article continues with our [React App Scaffolder.](api/web.md#react-app-scaffolder) 

### 6. Scaffolding an app \(optional\)

Even if you intend to write your own React app from scratch, it is worth scaffolding an app as an initial playground until you feel comfortable working with the platform. There are more docs explaining the flavours of React App [here](api/web.md#react-app-scaffolder) but the basic steps are;

First install globally both Yeoman and React App Scaffolder itself.

`npm install yo @reapit/generator-react-app-scaffolder@latest -g`

You may need to run this with the `sudo` prefix depending on your OS.

Then;

`yo @reapit/react-app-scaffolder`

This will launch the scaffolder with the following options:

![](.gitbook/assets/screenshot-2020-04-13-at-16.03.07.png)

Having entered the basic meta data for your app, ensure you enter the Client Id from step four before selecting the styling and state management solutions you want to work with. Hit return and the app will start building.

![](.gitbook/assets/screenshot-2020-02-16-at-13.49.21.png)

This will launch an app at localhost:8080. You will be redirected again to Reapit Connect and then back to the app as an authenticated user.

![](.gitbook/assets/screenshot-2020-02-16-at-13.56.24.png)

You should now be good to go. The basic app structure and authentication are all set up to start building components and working with the platform API. 

