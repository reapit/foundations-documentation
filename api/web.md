---
description: Components and packages to help you build a Reapit Marketplace application
---

# Web

## Elements

Elements is a React UI Component and utility library we have developed internally and open sourced. The Developer Portal and Marketplace itself uses Elements extensively and if you are building a React app to be installed by clients, we recommend you do too.

The styles are based on the excellent [Bulma UI](https://bulma.io/) library to provide sensible base defaults for common patterns. Although the components themselves are based on React, the project exports a regular stylesheet you can import as normal and markup in your preferred templating language see "What if I don't use React" below. 

In the future, we plan to move away from Bulma to use entirely in-house styles, supporting both Styled Components \(React CSS in JS\) and vanilla CSS. You can keep a track of Elements v2 progress against [this milestone](https://github.com/reapit/foundations/milestone/8).

As well as React Components, we also export a number of useful utilities like form validators, date-time helpers and a HTTP fetch module. 

### Basic Usage

In your terminal, execute;

`yarn install @reapit/elements`

Then insert the stylesheet, either as an import into another stylesheet;

```css
@import '~@reapit/elements/dist/index.css';
```

Or into the head of your document in the normal way.

Then in your code you can either import a component with ES Modules;

```javascript
import { H1, Alert } from '@reapit/elements'
```

Or, using CommonJS

```javascript
const { H1, Alert } = require('@reapit/elements')
```

Then you can use the tags in your code as regular React Components;

```jsx
export const MyCoolComponent = () => {
    return (
        <>
            <H1>Heading!</H1>
            <Alert message="Success!" type="success"/>
        </>
    )
}
```

And that's about it...

### Storybook: Code as documentation

Well, not quite all!

All of the Elements modules are rendered out using [React Storybook](https://storybook.js.org/) and hosted inside the [Developer Portal](https://marketplace.reapit.cloud/developer/elements). If you are not familiar with Storybook as a tool, it allows the developer to interact in live time with the pre-rendered components and their variants. You can adjust the code and see how they behave in live time, as well as providing copy-paste snippets to insert into your project.

When using Storybook, you can toggle between code examples and rendered output of components by using the ‘Canvas’ and ‘Docs’ tabs. You should also toggle the "Show add ons" option from the menu to render the code below the components, and it's variants see below:

![](../.gitbook/assets/screenshot-2020-02-12-at-16.18.04.png)

In addition to Storybook, because we have used TypeScript throughout out estate, each of our modules ships with TS definitions for free. If you use TypeScript, this is clearly a big help but even if you don't modern IDEs like VSCode will give you intellisense hints about prop types and parameters as you code. 

### What if I don't use React?

Obviously, not everyone uses React and 



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

## Foundations TS Definitions

Develop in TypeScript against the Reapit Foundations Platform with confidence

If you are using TypeScript \(and we recommend you do!\), for your front end project, we provide full type definitions for the API documented in the [API explorer](https://github.com/reapit/foundations-documentation/tree/db0718c9be27b7760dfae34e69518806acf0e855/developer/swagger/README.md). We generate these types from the Swagger contracts direct so you can be sure that when the API changes, your types will be updated also. This allows for a much closer alignment between front and back end development and ultimately more robust applications.

{% hint style="warning" %}
The definitions are updated automatically when the API changes. As such, it is recommended strongly that 
{% endhint %}



This is a package containing both marketplace and platform defintion. They are fetched by a scheduled cronjob activity executed daily at 00:00AM UTC.

### Install:

Beacuse this is a private scoped package, Make sure you have .npmrc in your root project folder configured with proper NPM\_TOKEN env variable Install using npm `npm install --dev @reapit/foundations-ts-definitions` Install using yarn `npm install --dev @reapit/foundations-ts-definitions`

### Import types:

Import the required type from the package named `@reapit/foundations-ts-definitions`. Eg:

```javascript
import {AppClientSecretModel} from '@reapit/foundations-ts-definitions'
```

## React App Scaffolder

A CLI application to get you started in the Reapit Marketplace with sensible but opinionated tooling and authentication out the box.

* Clone the repo
* Create an empty repo on Github and copy the git:path
* `yarn install`
* `npm install -g yo`
* `npm link`
* `yarn scaffold`
* Select the options you want and wait... your app will build and export to the same directory as the generator, running on localhost:8080 and pushed to Github!

## Config Manager

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

## Web Components

In addition to the Elements React component toolkit, Reapit will soon be offering a number of other downloadable Front End Resources. 

These may be modular blocks of functionality that can be embedded within your site, toolsets or even CMS friendly bundles of scripts available elsewhere. The guiding principles of the project is that the components should be standalone, highly customisable and lightweight. 

These are under active development by our team with an Alpha release in the coming months. You can check on progress [here.](https://github.com/reapit/foundations/milestone/6)

### Search Component

Coming soon...

### Book a Valuation Component

Coming soon...

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



