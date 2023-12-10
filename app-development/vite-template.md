---
description: A Vite Template to get you immediately started with Reapit Foundations
---

# Vite Template

{% hint style="info" %}
Even if you aren't going to build a React App, we still suggest scaffolding an application with the Vite template as an example of how to get the best out of Reapit Elements.
{% endhint %}

The fastest way to get started building a Reapit AppMarket App is with our [Foundations Vite Template](https://github.com/reapit/foundations-react-vite-template). Out of the box you will have an app that:

* Is authenticated against our Platform API using Reapit Connect and Connect Session
* Has the Elements UI library installed and out the box, it ships a fully working end-to-end Reapit contact look up and edit app, demonstrating how to get started with the platform as well as suggested UI layouts and patterns
* Has a login, log out, private protected routes, primary and secondary navigation.
* Includes TypeScript Platform Type Definitions, and Unit Tests.
* Includes Github Actions pipelines for pull request validation and production deployment.
* Comes bundled with AWS CDK scripts to enable you to deploy to your own AWS environment with virtually zero configuration.
* For a quick start development environment, you can deploy to our [Infra as a Service (IaaS)](iaas-coming-soon/) - contact us for beta access.

{% hint style="info" %}
For a demo deployed to our Infra as a Service (IaaS), [visit here.](https://handsome-zipper.iaas.paas.reapit.cloud/) You can use your developer credentials to log in with Reapit Connect.
{% endhint %}

### Getting Started

First, if you don't have a Reapit Connect client id yet, will need to obtain one [here](https://developers.reapit.cloud/apps/new).

If you are creating a fresh client id or already have one but want to see the full functionality of the template, you will need to add the following scopes to your app `read contacts`, `write contacts`, `read negotiators` & `read offices` - you can always remove these scopes later if you don't need them.

Ensure also you have set `http://localhost:8080` as a redirect uri and `http://localhost:8080/login` as a logout uri in your app settings in the [developer portal](https://developers.reapit.cloud/apps).

The output app will create a simple CRUD contacts app to demonstrate the features of the platform.

#### Prerequisites

* Node.js 18+
* Yarn 1+

First, run;

```
npx degit reapit/foundations-react-vite-template <<Your App Name>>
```

Then;

```
git init
```

And;

```
yarn
```

Add your `CONNECT_CLIENT_ID` to the `.env.example` file at the root of the project and rename it to `.env`.

Finally

```
yarn start
```

Each package has the following commands that can be run using yarn:

* `yarn start` will start a dev server at localhost:8080 with typechecking and linting enabled
* `yarn build` will build an app for production
* `yarn test` will run the Jest tests in watch mode
* `yarn test:ci` will run the Jest tests without watch and with coverage for use in CI environments
* `yarn lint` will run eslint and prettier accross the project
* `yarn check` will use tsc to type check the project
* `yarn upgrade:deps` will load a CLI to that allows you to update dependencies to their latest versions

### CI/CD and Releases

#### Development & PRs

When raising a PR, the dedicated Github action workflow will run tests, linting, typechecking and build tasks against all packages that changed since `main`.
