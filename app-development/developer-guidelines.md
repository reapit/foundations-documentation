---
description: >-
  This guide is intended to provide basic guidelines on the delivery of projects
  for the Reapit Foundations Platform as a Service (PAAS).
---

# Developer Guidelines

## General

* Production applications to be written in TypeScript. JavaScript only to be used for scripting, config files and throw-away rapid prototyping.
* TypeScript definitions for platform endpoints should be imported from [https://foundations-documentation.reapit.cloud/app-development/foundations-ts-defintions](https://foundations-documentation.reapit.cloud/app-development/foundations-ts-defintions) 
* Use of “any”, “unknown”, and inferred types should be avoided in the codebase.
* Code should be explicit in typing for future maintainers and be type-checked at compile time with the TSC. 
* Babel TypeScript should be avoided as it offers no type checking.
* Modern ES6+ standards to be used throughout, enforced with ESLint. ESLint config should extend the TypeScript ESLint recommended settings.
* Code should be formatted using Prettier, with a standard config.
* Automated testing essential on all production applications. Either unit tests written in Jest or functional end to end tests in Cypress. Other well supported test frameworks are also acceptable. 
* Unit test coverage basic metric is at least 80% coverage lines, statements, and functions.
* Functional tests where used, should cover all core user journeys as defined in the client supplied product definition.
* Code should be deployed using CI/CD pipelines that run tests, lint and compile the code prior to merging and deployment.
* Github Actions, Circle CI, Azure Devops, or any other well supported CI/CD provider are acceptable.
* Code should be deployed to a cloud provider offering industry standard security and reliability e.g. AWS, GCP, Azure or Heroku.
* Infrastructure must be shipped “as code”, using solutions like CloudFormation, Serverless Framework and Terraform.
* It must be possible for all infra to be programmatically destroyed and rebuilt without manual configuration steps.
* Env files, API keys and other semi-confidential application specific config like client ids must be stored in a secure remote location e.g. AWS SSM Parameter Store.

## Front End

* Front end applications to be bult in React primarily.
* If there is an SEO requirement for a project, NextJS and Gatsby are acceptable choices for SSR. 
* React code should be primarily functional, only using OO paradigms like classes when entirely necessary.
* State management should use React Context / Hooks API for smaller projects and Redux if the project is large. 
* Consider using GraphQL / Apollo both state management and data fetching using our dedicated service [https://foundations-documentation.reapit.cloud/api/graphql](https://foundations-documentation.reapit.cloud/api/graphql) 
* Authentication in the front end must use the Reapit Connect OAuth flow and must validate id tokens on authentication. 
* No access or id tokens should be cached outside of memory \(local storage, cookies\) and the user session must not last longer than a browser session. 
* It is highly recommended to use [https://foundations-documentation.reapit.cloud/app-development/connect-session](https://foundations-documentation.reapit.cloud/app-development/connect-session) to manage
* Reapit Elements must be used as the primary UI library and styleguide for all Reapit AppMarket project.
* No other UI frameworks should be used \(Material UI, Tailwind etc\), to ensure visual consistency with Elements. 
* Vanilla CSS, SASS or a well-supported CSS in JS library are all acceptable for small visual tweaks not available in Elements
* All modern browsers should be supported \(Chrome, Edge, Firefox, Safari\). Minimum Chromium version is 69.

## Back End

* Node Services can use either functional or OO paradigms. This should be consistent on a project-by-project basis and not mixed in the same project.
* Express should be used for simple to medium complexity RESTful NodeJS services.
* Cloud functions are an acceptable alternative to Express for micro services. Can also be used with Express.
* For more complex services, other frameworks like NestJS can be considered, but musy be well supported and have a solid long term support.
* Low cost pay as you use, serverless solutions should be used for infra eg Lambda, Dynamo and Aroura over “always on” containers and DBs. 
* If using Node to serve client side applications, Reapit Connect must be used to authenticate as per Client Side React applications.

