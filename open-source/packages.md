---
description: >-
  A brief description of each of our open source repos, what they do and how to
  work on them
---

# Packages

{% hint style="info" %}
Where possible, our applications follow in-house conventions, style guides and design patterns. As such, please read our contributing guide first as this document will only inform you of exceptions to our conventions beyond a brief description of the core package functionality and / or usage.
{% endhint %}

## Marketplace

The core frontend of the Reapit Foundations platform. Performs functionality for both the Marketplace and Developer Portal applications.

## AML Checklist

An anti-money laundering app, aimed at helping negotiators gather identity checking information from clients and applicants.

## Geo Diary

An app for negotiators on the go. It geo locates the user and assists them with their daily appointments by getting them from A to B.

## Elements

A UI toolkit for building web applications in the Reapit Marketplace

### Typescript modules

* All modules are added to the src folder.
* React components should live in their own folder within the components folder and be PascalCased.
* Utilities should live in their own folder within the utilities folder and be kebab-cased.
* All components and utils should export from an `index.ts(x)` at the root of their folder.
* All components should be properly tested and contain their tests within their folder, following the `__tests__` convention.
* All modules should export their own type definitions.
* `index.tsx` at the root of `src` is the entry point for the app. All modules should be exported from here eg `export * from './components/Input'`

### Styles

* All components should use vanilla \(S\)CSS classes \(no modules\) - refactor where necessary.
* Styles live in the styles folder in all cases.
* Styles export from `index.scss` at the root of the styles project, ensure any new files are `@import`ed here.

### Building and Publishing

* NOTED: THIS PROCESS WON'T BUMP THE PACKAGE VERSION AUTOMATICALLY FOR YOU
* When a PR is created, checks will run to make sure testcases have been passed, code have passes linter standard. If one of checks fail, the PR won't able to be merged, and require the sumbmitter to update his/her code again.
* Create a PR to merge develop. When the PR merged to develop, there will be a tag published that have a version based on version field on package.json file. If there were a tag that has the same tag name created, the old tag would be overridden by the new tag. Install them on other by edit package.json as `@reapit/elements:git+ssh:git@github.com:reapit/elements.git#{tag}`. eg `@reapit/elements: "git+ssh:git@github.com:reapit/elements.git#v0.5.4-beta"`, or commandline: `yarn add @reapit/elements@git+ssh:git@github.com:reapit/elements.git#v0.5.4-beta`
* To release a stable version of npm package, create a PR to merge master. When the PR was merged, npm package will be published to npm , a new release will be created automatically, and storybook assets will be deployed to GH-pages.

### To use the project

* You will need an NPM token to install the package - this should be added to the `.npmrc` file.
* `yarn add @reapit/elements`to your project - you can then import the modules with your chosen module system.
* You will need to globally install / add the CSS file from `@reapit/elements/dist/index.css`.

### Storybook

* All React components should have their own Storybook stories in their own folder using the `component.stories.tsx` convention.
* You should add as many variants of your component as is helpful for future devs - these are our live docs.
* All future component work for generic components should be "Storybook" first if possible.
* To run a local Storybook instance with a dev server run `yarn storybook`.
* To build and publish to Github Pages at [https://reapit.github.io/elements/](https://reapit.github.io/elements/) run `yarn deploy-storybook` - this happens by default in a postpublish hook when you deploy to NPM.

## Cognito Auth 

A thin wrapper around the AWS SDK and OAuth flow to take the pain out of authenticating your App with Reapit Connect

* First create a `env.yml` file at the root of the project. You will see the keys you will need in the `env.example.yml` file - you should obtain the values from the AWS Console.
* Assuming you have NodeJS@10.x installed, run `npm install -g serverless yarn`
* Run `yarn` to install dependant node modules.
* Add your personal AWS IAM credentials to your $PATH using `serverless config credentials --provider aws --key <<KEY>> --secret <<SECRET_KEY>>`, full docs [here](https://github.com/serverless/serverless/blob/master/docs/providers/aws/guide/credentials.md)
* You are now good to start developing. To run a local server in watch mode, run `yarn dev`.
* To run tests in watch mode run `yarn test-dev`.
* To deploy the app to AWS, just run `yarn deploy`. This will run the following steps;
  * `yarn lint` To check for code and formatting errors.
  * `yarn build` To compile the TypeScript to JavaScript.
  * `yarn test` To run the tests, both unit and integration.
  * `yarn serverless` To bundle the app and push to AWS Lambda - **this will deploy to production immediately so proceed carefully!**.
* To view details of your deployment, configure the Lambda or view the logs [visit](https://eu-west-2.console.aws.amazon.com/lambda/home?region=eu-west-2#/functions/cognito-auth-api-dev-dev-server?tab=graph).

## React App Scaffolder

A CLI application to get you started in the Reapit Marketplace with sensible but opinionated tooling and authentication out the box.

* Clone the repo
* Create an empty repo on Github and copy the git:path
* `yarn install`
* `npm install -g yo`
* `npm link`
* `yarn scaffold`
* Select the options you want and wait... your app will build and export to the same directory as the generator, running on localhost:8080 and pushed to Github!

## Foundations TS Definitions

Automated TypeScript definitions for the Foundations API Platform

This is a package containing both marketplace and platform defintion. They are fetched by a scheduled cronjob activity executed daily at 00:00AM UTC.

## Usage:

### Install:

Beacuse this is a private scoped package, Make sure you have .npmrc in your root project folder configured with proper NPM\_TOKEN env variable Install using npm `npm install --dev @reapit/foundations-ts-definitions` Install using yarn `npm install --dev @reapit/foundations-ts-definitions`

### Import types:

Import the required type from the package named `@reapit/foundations-ts-definitions`. Eg:

```javascript
import {AppClientSecretModel} from '@reapit/foundations-ts-definitions'
```

## Web Components

Embeddable TypeScript widgets to enhance static sites. The library will be built into two different types: as npm package to use with npm project,  as UMD scripts to embed into other static sites.

### Build and publish NPM package

This action should be done by CI after a PR merged into master Execute npm script: `build:npm` to build package into a folder named dist-npm, then `npm publish` to publish the package \(make sure you have a required env set: NPM\_TOKEN\)

### Build and publish CDN static files

This action should be done by CI after a PR merged into master Execute npm script: `build:cdn` to build package into a folder named dist-cdn, then `npm publish:cdn` to publish static files into AWS s3 \(make sure you have configurated valid s3 credential: [https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)\)

### Usage

#### NPM package

* Install the package `yarn add @reapit/web-components` or `npm install @reapit/web-components` \(make sure you have a correct .npmrc in your root folder\)
* Import the widgets that you want to use

  ```text
  import { SearchWidget } from '@reapit/web-components'
  ```

#### CDN package

* Add a script tag at the end of your static

  ```markup
  <script src="http://reapit-web-components.s3.amazonaws.com/search-widget.js"></script>
  ```

* Use the desired component follow the instruction of that component

  ```markup
  <div id="reapit-search-widget-container">
  <div id="result"></div>
  ```

#### Development

Create a storybook for your component, and execute `yarn storybook` to start to develop your component at `localhost:8080`undations platform.

## Lifetime Legal

Fork of AML App, to extend functionality for Lifetime Legal client.

## GraphQL Server

A GraphQL implementation of the Foundations API. 



## Config Manager

A thin wrapper around AWS Secrets Manager for keeping remote config secure.

Simple wrapper around AWS SDK for managing config objects in AWS Secrets Manager. Exports both CLI and Node versions and is distributed via an NPM Package.

#### Pre-Requisits

You must have valid AWS IAM credentials in your current bash / zsh profile specifically, variables in the following format:

`export AWS_ACCESS_KEY_ID="<<SOME_ID_HERE>>"`

`export AWS_SECRET_ACCESS_KEY="<<SOME_KEY_HERE>>"`

#### Installation

* `yarn install @reapit/config-manager --dev` if you are working in a JS project.
* `git clone git@github.com:reapit/config-manager.git && cd config-manager && yarn` If you want to modify / upload / delete / view secrets locally

#### Methods

The project exports 5 methods; 4 to perfom CRUD operations and a 5th to set the specified secret to the local environment. All 5 methods accept a single string parameter `<<secretName>>` which maps to the named secret in AWS secrets manager.

The name of the secret for Cloud app project config is `reapit-marketplace-app-config`

* `getSecret` Fetches a secret by name and outputs to a local JSON file called `reapit.config.json` at the root of your project. **BE SURE TO ADD THIS TO YOUR LOCAL .gitignore**. You can see an example of the output file at  `reapit.config.example.json`
* `createSecret` Stores a new secret by name, with the value of the secret string set to whatever is in the `reapit.config.json` at the root of your project.
* `updateSecret` Updates a secret by name, with the value of the secret string set to whatever is in the `reapit.config.json` at the root of your project. Suggest very strongly that you should use `getSecret` first then only update the values you need to change.
* `deleteSecret` Deletes a secret by name - it is stored for a default of 7 days should you ever need to recover it before being hard deleted.
* `setEnv` Works like `getSecret` but rather than storing to JSON, writes the values of to your `proces.env` object.

#### Usage with Node / JS

Assuming you have installed the package, you can simply require and call the methods in the normal way eg

```javascript
const getSecret = require('@reapit/config-manager').getSecret

//

const mySecret = getSecret('my-cool-secret-name')

// >> reapit.config.json
```

The async requests are intentionally blocking to make it easier to work on the command line with them so if you are using them in your code, consider wrapping in a promise.

#### Usage on the CLI

The script `config-manager` is available in the bin dir if you have used yarn to install. You can call this with the name of the method as your first arg and secret name as the second eg:

`yarn config-manager getSecret reapit-marketplace-app-config`

If you are working locally, you can just call the CLI script in the same way eg

`./cli.js getSecret reapit-marketplace-app-config`

## SMB Small Businesses App

An application to onboard new businesses to the Reapit Agency Cloud CRM.

## Demo Site

A simple HTML app for deploying Reapit Web Components.

## Cognito Custom Mail Lambda

Lambda that intercepts Cognito Emails and applies custom Reapit response



```
$ give me super-powers
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours
{% endhint %}

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



