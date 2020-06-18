---
description: A guide to how to work with Reapit open source packages
---

# Contributing

## Intro

At Reapit, we have made a company wide commitment to open sourcing as much source code as possible. There a number of reasons for this decision but with regard to the Foundations project these are principally;

* Approach - we want our partners to see how we go about building things internally, to give you insight into how your own integrations may work.
* Transparency - we want our partners to see what we are building, our future roadmap and progress against project milestones.
* Tooling - we want to share the tools we use internally to build marketplace applications with our partners so they can get the benefits of quick-to-market efficient development.

All our code is in a [mono-repo on Github](https://github.com/reapit/foundations), along with our project [Kanban boards](https://github.com/reapit/foundations/projects) and an open [issues page.](https://github.com/reapit/foundations/issues) Most people will want to use this as a resource alongside their own project, as living code as documentation but if you do want to contribute to a project, fork and extend an app or fix a bug, we welcome pull requests from all.

efwefefwf

## Getting Started

### Pre-requisites

To get started working working with Foundations, you will first need to have [Git](https://git-scm.com/), [NodeJS](https://nodejs.org/en/) and [Yarn](https://yarnpkg.com/) installed globally on your local machine.

Then, you will need to clone the repo with this command `git clone git@github.com:reapit/foundations.git`

You then need to set up Yarn workspaces with `yarn config set workspaces-experimental true`

Then install dependencies with `yarn`

### Working with the Mono Repo

We have a CLI binary that exists at the root of the project called `wapp` that makes working with workspaces easier. Under the hood, as well as Yarn Workspaces we also leverage [LernaJS](https://lerna.js.org/) to manage package and dependencies.

This exports the following commands:

* To add dependencies to the project root  `./wapp add global <dependency_name>`
* To add dependencies to an individual project `./wapp add <package_name> <dependency_name>`
* To add dev dependencies to a particular project`/.wapp add-dev <package_name> <dependency_name>`
* To run a particular project `./wapp start <package_name>`
* To run the tests for a project  `./wapp test <package_name> --watch`
* To create a new package within the main repo`yarn workspace react-app-scaffolder scaffold`

### Environment & Config

Each of our applications load their configuration from a file called `config.json` at the root of the package folder, where they are either pulled and set on the server by the CI for Node projects, or for client side applications, injected at render time by `window.reapit.config` object. Any secrets we set in Github's secrets manager so we can reference in the CI only.

Internally we manage the non confidential config using our Config Manager [see here](../api/web.md#config-manager) for info on how to do this yourself. If you are working internally on the project, you should follow these steps.

An example of the base config file[ is here](https://github.com/reapit/foundations/blob/master/packages/marketplace/config.example.json) and by default one ships with our app scaffolder. If you are trying to build the apps yourself, you can rename this, place in the root director, add a value to the `cognitoClientId`\(this is the client id, you can see in the app detail modal when you have submitted your app\), `cognitoOAuthUrl` and `cognitoUserPoolId` , and you should have sufficient config to work in the local environment.

The reason why we choose to fetch the config and inject in the render time is we only build one time and the bundle can run on many environment by replacing the `config.json` file.

### Development

The codebase is almost exclusively written in [TypeScript](https://www.typescriptlang.org/), with the exception of some node scripts that handle deployment and tooling. This decision was taken because of the level of robustness and scalability of the language over vanilla JS.

For those who have not worked with TS before, it is "just JavaScript" with type notations - we would recommend doing a couple of tutorials before digging into the codebase but for experienced JavaScript devs, you can be productive extremely quickly in TypeScript too.

We use [Webpack](https://webpack.js.org/) for bundling our code the Webpack scripts are all found in the `./scripts/webpack` directory. We use the TypeScript compiler to transpile our builds to modern ESNext code in dev mode, and for production, we use [Babel](https://babeljs.io/) to target older browsers \(IE 11\). There is a base TS Config that all packages inherit from at the base of the project.

We have worked to normalise our development workflows so that the majority of packages export the same predictable commands for building and running in both development and production modes.

Given that you have already installed dependencies [\(see getting started\)](contributing.md#getting-started), you can `cd` into a `packages/<<package-name>>` directory and \(where relevant\);

`yarn start:dev` will get you up and running with a web-server at `localhost:8080`

`yarn test:dev` will run unit tests in watch mode for the project

`yarn test-e2e:dev` will run any end to end tests in watch mode

`yarn build:prod` will bundle the code for production

`yarn start:prod` will serve your production build with a Node web server at `localhost:8080`

`yarn test:ci` will perform a single run of your tests and produce a coverage report

`yarn test-e2e:ci` will run any end to end tests in headless mode

### Styling

We support two styling methods across our projects; [SASS with CSS Modules](https://sass-lang.com/) and [Styled Components](https://styled-components.com/). You are welcome to use either and both are supported by our [React App Scaffolder](../api/web.md#react-app-scaffolder), although only one by project.

By convention, we store any Styled Components that are specific to an individual component in a sub folder of that component called `__styles__` however, if a style is re-usable, generic or global to the project, please use the `src/styles` directory to reduce duplication.

For components that are genuinely generic across the estate, please take the time to add to the [Elements](../api/web.md#elements) project as a Storybook item so we can use it again. If you suspect you may be writing a common component from scratch, it is likely it will already exist in Elements so please take a look if there is anything that can be re-used or adapted with a modifier class.

Our overriding aim is to write as little CSS as possible and focus on re-usable components, both to save time and to develop a consistent look and feel across the estate.

### Testing

Our code has a lot of automated testing, mostly unit tests, although we have some E2E tests and this is something we will be expanding going forward. In the previous section you saw the commands exported from each of the projects to run the test suites so this section deals with some basic conventions for working with tests on the codebase.

We use [Jest](https://jestjs.io/) for our unit testing, with [Enzyme](https://airbnb.io/enzyme/) for rendering React components where relevant. If you are not familiar with these libraries, we would urge you to do some reading before getting started. Our goal is that each of our packages, where relevant, should have ~90% coverage of functions and lines. Whilst this target is an arbitrary value, the desired outcome is a high level of confidence in our CI / CD pipeline which means we can deploy straight to development and daily to production.

By convention, we keep our test scripts in a sub folder of the source code called `__tests__` with the same file name. Where we use mocks and stubs, as with tests, they live in the same folder of the source code with the same file name and sub folder convention `__stubs__` and `__mocks__` .

For React components as a bare minimum, we expect a snapshot of the shallow rendered component, with snapshots saving to the `__snapshots__` sub folder of the component.

End to end functional tests are all written using the excellent Cypress framework. Whilst it does not support cross browser testing for older browsers, we feel it is a decent tradeoff owing to the speed, developer experience and reliability of the tests over conventional Selenium / Webdriver tests.

Where relevant, files e2e test specs are placed in the `src/tests/cypress` folder of the package. We use the `Page Object Model` pattern, storing anything related to a specific page; selectors and actions, to make them more re-usable and modular.

When raising a pull request, please ensure that existing tests are passing locally and that where relevant, new tests are added to maintain our overall coverage levels.

### Monitor Web Application

We're using [https://sentry.io/](https://sentry.io/) for monitoring our web applications. When build the app, webpack will push all sourcecode including sourcemap file to sentry.io for easy to monitor and catch error with the log for human readable. For the new project init. 1. Go to [https://sentry.io/](https://sentry.io/) create the project 2. Create `.sentryclirc` in root folder.

```text
[defaults]
project=<your_sentry_project_name>
org=<your_organization>

[http]
keepalive=false
```

1. Add to webpack plugins

   ```text
   new SentryWebpackPlugin({
   include: './public/dist/',
   ignore: ['node_modules'],
   configFile: '.sentryclirc',
   setCommits: {
    repo: '<your_repo_name>',
    auto: true,
   },
   }),
   ```

   For more information please reference [https://github.com/getsentry/sentry-webpack-plugin](https://github.com/getsentry/sentry-webpack-plugin)

### Interacting with our APIs

We use [Insomnia](https://insomnia.rest/) for testing and interacting with our APIs. We created a configuration file called `api-doc-config.json` at `./scripts/api-documentation`, so you can just import it to your Insomnia app and use all the REST and GraphQL services we built out of the box.

When communicating with APIs, it's hard to manage common values like `protocol`, `serverDomain` in multiple environments \(local, development, production\) and we may end up repeating those identical values across multiple requests. We solve this problem by using \[Environment Variables\] \([https://support.insomnia.rest/article/18-environment-variables](https://support.insomnia.rest/article/18-environment-variables)\) to define common values in a single place and then referenced those values in multiple requests. Now we can use our APIs across multiple environments with ease and if we need to change the environment variables, we have the ability to modify them in a single place.

For more information please reference [https://support.insomnia.rest/](https://support.insomnia.rest/)

## Workflow

### Github Issues & Projects

The starting point for any development work is to raise or assign a [Github Issue](https://github.com/reapit/foundations/issues) to yourself. The issue should be a descriptive as necessary for a future developer to understand or for a tester to properly validate.

We use labels heavily to categorise issues. Each issue should have either `bug` `feature` or `chore` added based on the type of work required. It should also have either a `platform-team` label for API issues or `cloud-team` label for web application issue and where relevant, a label for services it will effect for example `marketplace` or `elements`.

{% hint style="info" %}
Raising an issue does not guarantee that we will work on it. In many cases we will ask for more information and in some cases we may close an issue if it does not fit with our roadmap. In all cases, we will update the ticket with an outcome so please keep an eye on it for updates.
{% endhint %}

When raising an issue, you should add a project to the ticket, either [`Feature Triage` ](https://github.com/reapit/foundations/projects/3)or [`Bug Triage`](https://github.com/reapit/foundations/projects/2) . This will alert one of our Product Owners that the issue requires investigation and they will move it into one of our development streams if it is accepted and ranked by priority. Ultimately accepted issues will make it onto the main [`Kanban`](https://github.com/reapit/foundations/projects/1) board where an engineer will pick it up for development.

{% hint style="warning" %}
Ensure a triage project is added to your issue to make sure we process it as quickly as possible
{% endhint %}

In all cases, the more information you can give us, the better. For features, please be descriptive about the expected / intended behaviour. For bugs, please give us detailed steps to replicate including device, environment and app / page / component / endpoint where relevant.

### Version Control

When working on the project, we ask that contributors follow a basic git flow, with `master` as the base branch;

* Branch names are in the convention of `feat/description-of-issue` `fix/description-of-issue` or `chore/description-of-issue` mapping to the common issue types we use in Github issues.
* Commits should also follow this pattern in the convention `fix: what I changed` `feat: what I changed` or `chore: what I changed` we enforce this in a pre-commit hook using [CommitLint.](https://commitlint.js.org/#/) It is helpful but not essential to include the issue number you are working on in your commit messages eg `fix: #123 what I changed`.
* To merge back into the base branch, raise a pull request against `master`. All checks should pass and at least two approvers are necessary to merge into base.
* Keep your branch up to date at all times with the base branch by `rebase` only, to keep the tree clean.
* On merging to base, use `squash and merge`, to keep the tree clean and to make rolling back changes easy.

### Github Actions, CI / CD & Releasing

We use [Github Actions](https://help.github.com/en/actions) for all our Continuous integration pipelines. You can see the various workflows being executed in [live time here](https://github.com/reapit/foundations/actions) and the [source files here](https://github.com/reapit/foundations/tree/master/.github).

The basic flow for all projects is that;

* **On Pull Request:** Test, build and lint tasks run to ensure the branch is sound.
* **On Pull Request Merge:** Test, build and lint tasks run as well as `release:dev` which will push the code to the relevant development environment for the project.
* **On Release Tag:** Again, test, build and lint tasks run and the \`release:prod\` task runs to deploy the relevant tagged project. The release [tag should be raised here](https://github.com/reapit/foundations/releases) and be in the format `<<package>>_v<<version-number>>` to trigger the production workflow. For parallel deployments, you should wait for the first deployment passed checkout repository step and at that time you can continue to trigger the next deployment.

Details of the development and production environments / deployments for each package [are listed here](packages.md).

### Definition of Done

As per the previous sections, all work on the project is performed against the spec as per a Github Issue ticket. A Github issue is considered ready to be moved to the `done` column only when the following checklist has been completed.

* The complete acceptance criteria or task list on the Issue ticket has been fulfilled. To be verified by a PO if appropriate.
* The feature has appropriate unit and end to end tests.
* The feature has been verified as working by a QA if appropriate.
* All tests and checks on Github are passing.
* The feature is up to date with the base branch.
* The feature has had at least two peer reviewers and that they have approved the feature for release.
* The feature has been merged and deployed into the master branch and it has successfully deployed to the development environment.

## Code Style

### Linting & Formatting

The vast majority of base code style is enforced by [ESLint](https://eslint.org/) with sensible community presets from [TSLint](https://palantir.github.io/tslint/) rules, and [Prettier](https://prettier.io/). The linter runs in a pre-commit hook on staged files with an auto-fix flag set to address any trivial issues.

If you want to run the lint command manually, you can do this from the root of the project by executing `yarn lint`

In addition to the lint rules, please also where possible, stick to the contribution guidelines below. These rules should be kept in mind when reviewing Pull Requests.

### Code Guidelines

* Code should be functional in style rather than Object Orientated or Imperative unless there are no clean alternatives.
  * Use pure functions where possible to make them testable and modular.
  * Avoid mutating variables and the `let` keyword.
  * React Components should be stateless functional components where possible.
  * Avoid classes and stateful modules where possible.
  * Avoid React lifecycle hooks.
  * Keep all state in Redux and business logic as pure functions of Redux State.
  * The above rules can be relaxed for test scripts.
* React components should be templates, free of logic. This is because we aim to re-use code in the future in React Native Applications so by keeping the React layer as purely presentational.
* Presentational logic helpers should live in a utils file in the same folder as your component so they can be re-used agnostic of the template.
* Use Redux connect for nested components for better performance and reduced re-rendering over `prop drilling`. Use `React.memo` for the same reason and selectors if appropriate.
* Type-safe everything! Use `any` and `unknown` types only when there is no alternative - try to avoid `implicit any` - types should be documentation as code for the project. We can relax this as a convenience in test scripts.
* Where possible use auto generated types from Swagger documentation or GraphQL definitions to ensure shared contracts with front and back end. These auto-generated types live in the main types folder.
* Styled Components or CSS / Sass Modules are used for styling in all cases where a third party library \(eg Bulma\) is not used.
* Styled Components & CSS / Sass Modules where they are generic should be kept out of the main components folder - they should live in the main styles folder to reduce duplication.
* The styles project should make extensive use of variables and mix-ins for things like colours, layouts, font sizes, line heights and so on. This ensures re-usablility and maintainability.
* Where possible, use `rems` over `px` as a unit for layout.
* Maintain the separation of concerns in the folder structure laid out in the initial scaffold seen in the [React App Boilerplate](https://github.com/reapit/react-app) eg, reducers should all be in the reducers folder, global types in the types folder and so on. There are many React projects in the company and they should all follow a broadly familiar structure and architecture.
* Make extensive use of the constants files for significant strings and other re-usable constant variables used in the app.
* When adding third party libraries to the project consider carefully the following;
  * Is this a trivial package we can easily write in house? If so, take the time to roll your own.
  * Is this library well supported, under active development and widely used in the community? If not, do not use.
  * Do we use a similar but different library for the same task elsewhere in the company? If so, use this library for developer familiarity and consistency.
  * Will this library impact significantly performance or bundle size eg Lodash or Moment? If so, consider carefully if it is necessary or if there is a better alternative.
* We have two kinds of tests; Unit tests with Jest and e2e tests with Cypress. For all new features an appropriate level of test coverage is an implicit part of the feature definition.
* For unit tests, the expectation is;
  * All functions / methods, especially utilities have i.o. tests, with internal conditional logic and edge cases tested.
  * All React templates have at least a snapshot, and any calls to action are tested to call their handlers with correct params.
  * Redux actions, reducers and sagas have test coverage for all cases.
  * Styled components do not require tests unless necessary, likewise constants and build scripts.
  * Tests should live in the same folder as their source in a `__tests__` folder. 
  * Mocks and stubs should also follow the same `__mocks__` & `__stubs__` pattern.
* For e2e tests, the expectation is;
  * Happy path user journeys are all tested through the app.
  * Calls to action are all tested, verifying an appropriate change in the state of the application is observed.
  * The page object model for selectors and methods is used to ensure re-usability.
  * The tests should not be excessive or flaky to ensure they do not block dev workflow.
* File naming should be `kebab-case` for `.js(x), .ts(x), .css` files, and indeed all files where possible. No use of capitals to avoid issues where Unix systems do not respect casing when a file name is changed.
* Exports from files can be either as variable or default exports, but please stick to naming the object before using `export default` to avoid anonymous module names in stack traces and React dev tools.

