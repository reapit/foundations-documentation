---
description: >-
  A service catalogue of our open source packages, what they do, where they
  deploy, the services they leverage and any additional steps how to work on
  them
---

# Packages

{% hint style="info" %}
Where possible, our applications follow in-house conventions, style guides and design patterns. As such, please read our contributing guide first, along with our Web API section for the majority of usage information. This guide is solely concerned with package-specific information.
{% endhint %}

## Marketplace

The core frontend of the Reapit Foundations platform. Contains all functionality in both the Marketplace and Developer Portal applications.

* **Tech Stack:** React, Redux, React Router, Elements, Cognito Auth, Jest, Cypress, Sass / CSS Modules.
* **Cloud Services:** S3, CloudFront, AWS Cognito, SecretsManager, Sentry
* **Production:** [https://marketplace.reapit.cloud](https://marketplace.reapit.cloud)
* **Development:** [https://dev.marketplace.reapit.cloud](https://dev.marketplace.reapit.cloud) ****

## Elements

A UI toolkit for building web applications in the Reapit Marketplace. Exports a library of React Components, JavaScript and TypeScript utilities and a CSS Stylesheet. For usage visit [here.](../api/web.md#elements)

* **Tech Stack:** React, Bulma, StoryBook, Sass / CSS Modules.
* **Cloud Services:** Github Pages
* **Production:** [https://reapit.github.io/elements/](https://reapit.github.io/elements/)

## Cognito Auth 

A thin wrapper around the AWS SDK and OAuth flow to take the pain out of authenticating your App with Reapit Connect. For usage visit[ here.](../api/web.md#cognito-auth)

* **Tech Stack:** AWS JavaScript SDK
* **Cloud Services:** NPM, AWS Cognito
* **Production:** [https://www.npmjs.com/package/@reapit/elements](https://www.npmjs.com/package/@reapit/elements)

## React App Scaffolder

A CLI for generating React Apps, optimised for the marketplace, including Reapit Connect authentication and Elements. For usage visit[ here.](../api/web.md#react-app-scaffolder)

* **Tech Stack:** Yeoman, React, Redux, Jest, React, Router, Styled-Components, Sass, CSS Modules
* **Cloud Services:** NPM
* **Production:** [https://www.npmjs.com/package/@reapit/generator-react-redux-app](https://www.npmjs.com/package/@reapit/generator-react-redux-app)

## Foundations TS Definitions

Automated TypeScript definitions for the Foundations API Platform. Automatically generates up to date TypeScript type definitions from Platform API swagger documentation. For usage visit [here.](../api/web.md#foundations-ts-definitions)

* **Tech Stack:** NodeJS
* **Cloud Services:** NPM
* **Production:** [https://www.npmjs.com/package/@reapit/foundations-ts-definitions](https://www.npmjs.com/package/@reapit/foundations-ts-definitions)

## AML Checklist

An anti-money laundering app, aimed at helping negotiators gather identity checking information from clients and applicants.

* **Tech Stack:** React, Redux, React Router, Elements, Cognito Auth, Jest, Sass / CSS Modules.
* **Cloud Services:** S3, CloudFront, AWS Cognito, SecretsManager, Sentry
* **Development:** [https://dev.aml-app.reapit.cloud](https://dev.aml-app.reapit.cloud)
* **Production:** [https://aml-app.reapit.cloud](https://aml-app.reapit.cloud)

## Geo Diary

An app for negotiators on the go. It geo locates the user and assists them with their daily appointments by getting them from A to B.

* **Tech Stack:** React, Redux, React Router, Elements, Cognito Auth, Jest, Sass / CSS Modules.
* **Cloud Services:** S3, CloudFront, AWS Cognito, SecretsManager, Sentry
* **Development:** [https://dev.geo-diary-app.reapit.cloud](https://dev.geo-diary-app.reapit.cloud)
* **Production:** [https://geo-diary-app.reapit.cloud](https://geo-diary-app.reapit.cloud)

## Config Manager

A thin wrapper around AWS Secrets Manager for keeping remote config secure. For usage visit [here.](../api/web.md#config-manager)

* **Tech Stack:** AWS SDK
* **Cloud Services:** NPM, AWS Secrets Manager
* **Production:** [https://www.npmjs.com/package/@reapit/config-manager](https://www.npmjs.com/package/@reapit/config-manager)

## Lifetime Legal

Fork of AML App, to extend functionality for Lifetime Legal client.

* **Tech Stack:** React, Redux, React Router, Elements, Cognito Auth, Jest, Sass / CSS Modules.
* **Cloud Services:** S3, CloudFront, AWS Cognito, SecretsManager, Sentry
* **Development:** [https://dev.lifetime-legal-app.reapit.cloud](https://dev.lifetime-legal-app.reapit.cloud)
* **Production:** [https://lifetime-legal-app.reapit.cloud](https://lifetime-legal-app.reapit.cloud)

## Cognito Custom Mail Lambda

Lambda that intercepts Cognito Emails and applies custom Reapit response.

* **Tech Stack:** Serverless, EJS, NodeJS
* **Cloud Services:** CloudForm, AWS Lambda

## Web Components

Embeddable TypeScript widgets to enhance static sites. For usage visit [here.](../api/web.md#search-component)

Under active development pre-alpha.

## Demo Site

A simple HTML app for deploying Reapit Web Components.

Under active development pre-alpha.

## GraphQL Server

A GraphQL implementation of the Foundations API. 

Under active development pre-alpha.

## SMB Small Businesses App

An application to onboard new businesses to the Reapit Agency Cloud CRM.

Under active development pre-alpha.





