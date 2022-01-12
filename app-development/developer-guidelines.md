---
description: >-
  This guide is intended to provide basic guidelines on the delivery of projects
  for the Reapit Foundations Platform as a Service (PAAS).
---

# Developer Guidelines

## General

* Production applications to be written in TypeScript. JavaScript only to be used for scripting, config files and throw-away rapid prototyping.
* TypeScript definitions for platform endpoints should be imported from [https://foundations-documentation.reapit.cloud/app-development/foundations-ts-defintions](https://foundations-documentation.reapit.cloud/app-development/foundations-ts-defintions)&#x20;
* Use of “any”, “unknown”, and inferred types should be avoided in the codebase.
* Code should be explicit in typing for future maintainers and be type-checked at compile time with the TSC.&#x20;
* Babel TypeScript should be avoided as it offers no type checking.
* Modern ES6+ standards to be used throughout, enforced with ESLint. ESLint config should extend the TypeScript ESLint recommended settings.
* Code should be formatted using Prettier, with a standard config.
* Automated testing essential on all production applications. Either unit tests written in Jest or functional end to end tests in Cypress. Other well supported test frameworks are also acceptable.&#x20;
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
* If there is an SEO requirement for a project, NextJS and Gatsby are acceptable choices for SSR.&#x20;
* React code should be primarily functional, only using OO paradigms like classes when entirely necessary.
* State management should use React Context / Hooks API for smaller projects and Redux if the project is large.&#x20;
* Consider using GraphQL / Apollo both state management and data fetching using our dedicated service [https://foundations-documentation.reapit.cloud/api/graphql](https://foundations-documentation.reapit.cloud/api/graphql)&#x20;
* Authentication in the front end must use the Reapit Connect OAuth flow and must validate id tokens on authentication.&#x20;
* No access or id tokens should be cached outside of memory (local storage, cookies) and the user session must not last longer than a browser session.&#x20;
* It is highly recommended to use [https://foundations-documentation.reapit.cloud/app-development/connect-session](https://foundations-documentation.reapit.cloud/app-development/connect-session) to manage
* Reapit Elements must be used as the primary UI library and styleguide for all Reapit AppMarket project.
* No other UI frameworks should be used (Material UI, Tailwind etc), to ensure visual consistency with Elements.&#x20;
* Vanilla CSS, SASS or a well-supported CSS in JS library are all acceptable for small visual tweaks not available in Elements
* All modern browsers should be supported (Chrome, Edge, Firefox, Safari). Minimum Chromium version is 69.

## Back End

* Node Services can use either functional or OO paradigms. This should be consistent on a project-by-project basis and not mixed in the same project.
* Express should be used for simple to medium complexity RESTful NodeJS services.
* Cloud functions are an acceptable alternative to Express for micro services. Can also be used with Express.
* For more complex services, other frameworks like NestJS can be considered, but musy be well supported and have a solid long term support.
* Low cost pay as you use, serverless solutions should be used for infra eg Lambda, Dynamo and Aroura over “always on” containers and DBs.&#x20;
* If using Node to serve client side applications, Reapit Connect must be used to authenticate as per Client Side React applications.

## Technical Test

_The below test is intended to assess suitability for candidates applying to work on the Reapit Foundations Platform_&#x20;

Task: To render a list of Properties from the Foundations API, using the Reapit Elements UI library Table. Following the steps below will give you the solution - if you spend plenty of time reading the documentation carefully, the code itself should take no more than an hour.

1. Register for the developer portal here: [https://developers.reapit.cloud/register](https://developers.reapit.cloud/register)
2. When you have followed the registration flow and have logged in, navigate to the docs page here and follow the steps here to register an app and obtain a client id: [https://developers.reapit.cloud/api-docs/developer-portal](https://developers.reapit.cloud/api-docs/developer-portal) When asked for permissions, you will need Read Properties only.
3. Next scaffold an application using our Create React App template here: [https://developers.reapit.cloud/api-docs/app-development/create-react-app-template](https://developers.reapit.cloud/api-docs/app-development/create-react-app-template)&#x20;
4. In your text editor, add your client id and user pool id to the reapit-config.json file as per the documentation in the previous step and start the Webpack dev server.
5. Log into your scaffolded app using your developer portal credentials - you will see a welcome screen and in the console, you will see logged out an example of data being fetched from the platform API.
6. Replace the fetched data with an API call to the GET /properties endpoint here [https://developers.reapit.cloud/swagger](https://developers.reapit.cloud/swagger) you should apply a marketingMode filter of “selling” to your query.
7. Render this data on the page in a Table using the React version of our Table component here: [https://elements.reapit.cloud/?path=/docs/table--react-shorthand-usage](https://elements.reapit.cloud/?path=/docs/table--react-shorthand-usage). Add a Title to the page “Properties for Sale”\


Bonus points - any of these you are able to complete will improve your application but are not essential.

1. Add a slide down container to the table that Renders a single button. The button should say “Edit Me” and should open a Modal window that contains Lorem Ipsum. Refer to the Elements storybook on how to do this.
2. Add unit or automated integration tests to your code.
3. Deploy your code to any cloud platform of your choosing via a CI / CD pipeline eg Circle CI / Github Actions.
