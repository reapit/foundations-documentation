---
description: >-
  A Create React App Template to get you immediately started with Reapit
  Foundations
---

# Create React App Template

The fastest way to get started building a Reapit AppMarket App is with our [Create-React-App](https://create-react-app.dev/) template. This package extends the functionality offered by the Facebook CLI and React Scripts whilst adding Reapit Specific packages for AppMarket development. Out of the box you will have an app that;

* Is authenticated against our Platform API using Reapit Connect and Connect Session
* Has the Elements UI library installed with detailed examples of suggested layouts for lists, tables and forms.
* Has a login, log out, private protected routes, primary and secondary navigation.
* Has an example API call fetching data from the Platform using a generic endpoint
* Includes TypeScript, Platform Type Definitions, and Unit Tests

{% hint style="info" %}
Even if you aren't going to build a React App, we still suggest scaffolding an application with the CRA template as an example of how to get the best out of Reapit Elements.
{% endhint %}

The newly scaffolded application will initially redirect you to a landing page, with navigation options to each of the example views.

![](<../.gitbook/assets/Screenshot 2022-01-18 at 10.34.01.png>) ![](<../.gitbook/assets/Screenshot 2022-01-18 at 10.34.15.png>) ![](<../.gitbook/assets/Screenshot 2022-01-18 at 10.34.35.png>) ![](<../.gitbook/assets/Screenshot 2022-01-18 at 10.34.51.png>) ![](<../.gitbook/assets/Screenshot 2022-01-18 at 10.35.02.png>)

### Usage

First execute&#x20;

`npx create-react-app@latest <<your-app-name-here>> --template @reapit/cra-template-foundations`

Open the project in your text editor and insert your Reapit Connect ClientId from the Developer Portal along with the  production `connectUserPoolId,` `eu-west-2_eQ7dreNzJ` into the config file located at:

`src/reapit.config.json`

CD into your project directory and run `yarn start` or any of the CRA standard commands eg `yarn build` `yarn test`

On running `yarn start` your app will load at `http://localhost:8080,` you will first be re-directed to log in to Reapit Connect if you don't already have a session, then will return back authenticated to a landing page.&#x20;

You should have everything there to get off the ground and immediately be productive on the platform!
