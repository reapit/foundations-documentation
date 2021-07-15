---
description: A guide to how to work with Reapit open source packages
---

# Contributing

## Intro

At Reapit, we have made a company wide commitment to open sourcing as much source code as possible. There a number of reasons for this decision but with regard to the Foundations project these are principally;

* Approach - we want our partners to see how we go about building things internally, to give you insight into how your own integrations may work.
* Transparency - we want our partners to see what we are building, our future roadmap and progress against project milestones.
* Tooling - we want to share the tools we use internally to build marketplace applications with our partners so they can get the benefits of quick-to-market efficient development.

All our code is in a [mono-repo on Github](https://github.com/reapit/foundations), along with our project [Kanban board](https://github.com/reapit/foundations/projects) and an open [issues page.](https://github.com/reapit/foundations/issues) Most people will want to use this as a resource alongside their own project, as living code as documentation but if you do want to contribute to a project, fork and extend an app or fix a bug, we welcome pull requests from all.

If you do want to work with the project, it is important to note there are certain configurations that are not committed to Github for security and environment reasons. Should you need to get access to a local configuration file, please contact us on the developer live chat in the Developer Portal &gt; Help section.

## Getting Started

### Pre-requisites

To get started working with Foundations, you will first need to have [Git](https://git-scm.com/), [NodeJS](https://nodejs.org/en/) and [Yarn](https://yarnpkg.com/) installed globally on your local machine. Currently, we use `yarn@2.4.x` and `node@14.x.x` internally however, other versions may well work for you.

For a clean build, then follow the steps below;

1. Clone the repo: `git clone git@github.com:reapit/foundations.git`
2. CD into the root of the project: `cd foundations`
3. Install dependencies `yarn`
4. Either: Obtain developer AWS Access Keys from a Reapit Admin and add to your bash profile as per instructions [here](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/loading-node-credentials-shared.html) then run `yarn conf-all` to pull in remote configs from AWS Parameter Store
5. Or: rename `config.example.json` file \(where relevant\) for the package you are working on - see Environment and Config below for more details on this.
6. Add an NPM token scoped to at least private read to your bash / zsh profile in the format of `export NPMTOKEN="<<your_token>>"`. You can obtain one of these from any of the Reapit Platform Applications team.

### Environment & Config

Each of our applications that has environment specific or non secret configuration \(API Endpoints, API keys, OAuth client ids, environment variables etc\), has a `config.json` at the root of the package folder. These files are stored in AWS Parameter Store and are are either pulled at compile time and set on the server by the CI for Node projects, or for client side applications, injected at runtime into a `window.reapit.config` object.

Any secret config \(that cannot be leaked publicly\), we set in Github's secrets manager so we can reference in the CI only.

Internally we manage the non confidential config using our Config Manager [see here](https://github.com/reapit/foundations/tree/master/packages/config-manager) for info on how to do this yourself. If you are working internally on the project, you should follow these steps.

An example of the base config file is at the root of each relevant project \(not all packages have a config\), and named as `config.example.json`. If you are trying to build the apps yourself, you can rename this, place in the root directory, and add a values as required.

Typically you will need a `connectClientId`\(this is the client id, you can see in the app detail modal when you have submitted your app\), `connectOAuthUrl` and `connectUserPoolId` , as a minimum to make the app functional for development. These variables are used to populate the [Connect Session Module](connect-session.md) that we use to manage the OAuth Flow in [Reapit Connect](../api/reapit-connect.md).

### Working with the Mono Repo & Yarn Workspaces

We use [Yarn 2.x \(Yarn Berry\), Workspaces](https://yarnpkg.com/cli/workspace) functionality to manage package and dependencies. If you are used to working with Yarn 1.x there are a number of fundamental differences to the API in v2. The main practical change is the way Yarn now moves all dependencies to the root node\_modules directory and loads them from a `.yarn/cache` directory at the root of the project.

This caching ensures much faster local and CI builds as well as more deterministic behaviour and some useful new features like [Interactive Upgrading ](https://yarnpkg.com/cli/upgrade-interactive)and [Workspace Management tools](https://yarnpkg.com/cli/workspaces/foreach).

Workspace packages are defined in the packages array in the root package.json of the project. When adding a new package to the repo you will need to it to this array for yarn to treat it as a workspace. Similarly, if you want to remove it from the project or disable it from the workspaces workflow, you should remove from this array.

From the root of the project, you can run Workspace commands on individual packages in the following format:

`yarn workspace <<packagename>> run <<command_name>>`

eg 

`yarn workspace developer-portal run start`

To run yarn specific commands you can use the following syntax:

`yarn workspace <<packagename>> <<yarn_command>> <<options>>`

eg

`yarn workspace developer-portal add react --dev`

You can of course just CD into a package directory and work in there as per any other JS/TS project.

We have worked to normalise our development workflows so that the majority of packages export the same predictable commands for building and running in both development and production modes.

Given that you are in a package directory you can run the following commands:

`yarn start` will get you up and running in dev mode - for web apps this will be a Webpack dev server at `localhost:8080`and for Node apps Serverless Offline at `localhost:3000`

`yarn test` will run unit tests in watch mode for the project - you can add add additional flags as per the Jest CLI API eg `--watch=false --ci --coverage` for running in a CI environment.

`yarn build` will bundle the code for production

`yarn lint` will lint the project, typically using ESLint

`yarn release` will release your app to a deployed environment in AWS, typically using [Serverless framework](https://www.serverless.com/) and by default to dev. If you want to deploy to production, add the `--stage prod` flag to this command.

`yarn publish` will publish the package to NPM, by default to the private registry unless the `--access public` flag is added.

All commands are always provided but where not relevant to the package they will just print to console `...skipping...`

If you want to run the same command on each package you can do this at the root of the project using the `yarn test-all / build-all / lint-all / conf-all commands.` These use the `yarn workspaces forEach` command to perform the same command on each package in the repo.

### Shared Scripts & Types

You will notice there are no dependencies at the root of the workspace and that many of the packages depend on each other. This is by design - packages should know about their own dependencies to allow maximum flexibility to upgrade packages independently. Packages that depend on other packages within the repo can reference each other using the `"@reapit/config-manager": "workspace:packages/config-manager"` syntax in your package.json.

Yarn will do the heavy lifting of resolving dependencies by package and we can use commands like `yarn dedupe` and `yarn upgrade-interactive` to keep things sane on a project wide basis.

Furthermore because yarn 2 has no `node_modules/.bin` directory, any executable from the yarn cli MUST be in scope in the individual package eg `webpack` and `jest`. 

To keep some centralised configuration for our scripts we have a package `@reapit/ts-scripts` that exports our global WebPack and Jest configs. Each package then imports them individually and can add any "special sauce" as required. The same applies to `ts-config` files which again inherit from the base at the root of the project.

Similarly, we have centralised our `@types/**` modules in a single `@reapit/ts-types` module to avoid type duplications eg 2 version of the React types that can cause compile time issues. We also have an internally generated types package `@reapit/foundations-ts-definitions` that contains the definitions for the API platform itself. These are auto generated from the Swagger definitions via a nightly cron job. [See here.](foundations-ts-defintions.md)

## Workflow

### Github Issues & Projects

The starting point for any development work is to raise or assign a [Github Issue](https://github.com/reapit/foundations/issues) to yourself. The issue should be a descriptive as necessary for a future developer to understand or for a tester to properly validate.

We use labels heavily to categorise issues. Each issue should have either `bug` `feature` or `chore` added based on the type of work required. It should also have either a `back-end` label for API issues or `front-end` label for web / node application issue and where relevant, a label for services it will effect for example `marketplace` or `elements`.

{% hint style="info" %}
Raising an issue does not guarantee that we will work on it. In many cases we will ask for more information and in some cases we may close an issue if it does not fit with our roadmap. In all cases, we will update the ticket with an outcome so please keep an eye on it for updates.
{% endhint %}

When raising an issue, you should add a project to the ticket, either[ Back End Backlog](https://github.com/reapit/foundations/projects/6) or [Front End Kanban](https://github.com/reapit/foundations/projects/1). This will alert one of our Product Owners that the issue requires investigation and they will move it into one of our development streams if it is accepted and ranked by priority.

See the dedicated [Development Requests ](../dev-requests.md)in these docs for more information on our product processes. 

{% hint style="warning" %}
Ensure a triage project is added to your issue to make sure we process it as quickly as possible
{% endhint %}

In all cases, the more information you can give us, the better. For features, please be descriptive about the expected / intended behaviour. For bugs, please give us detailed steps to replicate including device, environment and app / page / component / endpoint where relevant.

### Version Control

When working on the project, we ask that contributors follow a basic git flow, with `master` as the base branch;

* Branch names are in the convention of `feat/description-of-issue` `fix/description-of-issue` or `chore/description-of-issue` mapping to the common issue types we use in Github issues.
* Commits should also follow this pattern in the convention `fix: what I changed` `feat: what I changed` or `chore: what I changed` . It is helpful but not essential to include the issue number you are working on in your commit messages eg `fix: #123 what I changed`.
* To merge back into the base branch, raise a pull request against `master`. All checks should pass and at least two approvers are necessary to merge into base.
* Keep your branch up to date at all times with the base branch by `rebase` only, to keep the tree clean.
* On merging to base, use `squash and merge`, to keep the tree clean and to make rolling back changes easy.

### Github Actions, Serverless, AWS & Releases

All of our cloud infrastructure is in AWS. For releasing our code, we leverage [Serverless Framework](https://www.serverless.com/) where possible for it's convenience and clean, declarative code as infra approach. Under the hood it uses CloudFormation to spin up and tear down the infrastructure we need in AWS.

Anyone not familiar with Serverless and AWS Services should do some reading at this stage but the infra we use is declared for each project in a `serverless.yml` file at the root of each package. This is where you will add and remove required resources as required. 

For web applications, this typically means an S3 bucket with Cloudfront CDN on the front end and a DNS record in Route53. For Node services, typically we use Lambda, S3, DynamoDB, Cloudwatch and API Gateway. A basic template for deploying the various flavours of application is included in the apps generated by our app scaffolder.

When you are happy with your infra, you can either run `serverless deploy` locally to push to a development environment. On the CI this is mapped to the `yarn release` command. If you need to tear down your infra, you can do this using the `serverless remove` command. In all cases you will need to have the relevant [AWS credentials in your bash / zsh profile. ](https://docs.aws.amazon.com/sdk-for-javascript/v3/developer-guide/loading-node-credentials-shared.html)

We use [Github Actions](https://help.github.com/en/actions) for all our Continuous integration pipelines. You can see the various workflows being executed in [live time here](https://github.com/reapit/foundations/actions) and the [source files here](https://github.com/reapit/foundations/tree/master/.github).

The basic flow for all projects is that;

* **Build PR:** Build task runs to ensure the branch is sound.
* **Test PR:** Test, and lint tasks run to verify a PR. Runs in parallel with Build PR.
* **Release Dev:** Triggered on the successful merge of a PR, builds the project and releases to the relevant dev environment.
* **Release Prod:** Triggered by tagging a release in Github, ****again, test, build and lint tasks run and the `release-prod` task runs to deploy the relevant tagged project. The release tag should be raised [here](https://github.com/reapit/foundations/releases) and be in the format `<<package>>_v<<version-number>>` to trigger the production workflow.  Will release a single package to production and if relevant, publish to NPM&gt;

### Definition of Done

As per the previous sections, all work on the project is performed against the spec as per a Github Issue ticket. A Github issue is considered ready to be moved to the `done` column only when the following checklist has been completed.

* The complete acceptance criteria or task list on the Issue ticket has been fulfilled. To be verified by a PO if appropriate.
* The feature has appropriate unit and end to end tests.
* The feature has been verified as working by a QA if appropriate.
* All tests and checks on Github are passing.
* The feature is up to date with the base branch.
* The feature has had at least one peer reviewer and that they have approved the feature for release.
* The feature has been merged and deployed into the master branch and it has successfully deployed to the development environment.

## Code Style & Conventions

### Linting & Formatting

The vast majority of base code style is enforced by [ESLint](https://eslint.org/) with sensible community presets from [TSLint](https://palantir.github.io/tslint/) rules, and [Prettier](https://prettier.io/). The linter runs in a pre-commit hook on staged files with an auto-fix flag set to address any trivial issues.

If you want to run the lint command manually, you can do this from the root of the project by executing `yarn lint-all.`

In addition to the lint rules, please also where possible, stick to the contribution guidelines below. These rules should be kept in mind when reviewing Pull Requests.

### Code Guidelines

* The codebase is almost exclusively written in [TypeScript](https://www.typescriptlang.org/), with the exception of some node scripts that handle deployment and tooling. This decision was taken because of the level of robustness and scalability of the language over vanilla JS and we ask that contributors favour TypeScript where possible for future development.
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
* Where possible, use `rems or ems`  over `px` as a unit for layout.
* Maintain where it makes sense to do so the separation of concerns laid out in the initial scaffold seen in the [React App Boilerplate](https://github.com/reapit/react-app) here. There are many TS projects in the company and they should all follow a broadly familiar structure and architecture.
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

### Styling

We support two styling methods across our projects; [SASS with CSS Modules](https://sass-lang.com/) and [Linaria](https://github.com/callstack/linaria) \(CSS in JS\). For new projects we favour Linaria and are aiming to eventually deprecate / refactor our SASS from our projects.

By convention, we store any Linaria components that are specific to an individual component in a sub folder of that component called `__styles__` however, if a style is re-usable, generic or global to the project, please use the `src/styles` directory to reduce duplication.

For components that are genuinely generic across the estate, please take the time to add to the [Elements](web.md#elements) project as a Storybook item so we can use it again. If you suspect you may be writing a common component from scratch, it is likely it will already exist in Elements so please take a look if there is anything that can be re-used or adapted with a modifier class.

Our overriding aim is to write as little CSS as possible and focus on re-usable components, both to save time and to develop a consistent look and feel across the estate.

### Testing

Our code has a lot of automated testing, mostly unit tests, although we have some E2E tests and this is something we will be expanding going forward. In the previous section you saw the commands exported from each of the projects to run the test suites so this section deals with some basic conventions for working with tests on the codebase.

We use [Jest](https://jestjs.io/) for our unit testing, with [Enzyme](https://airbnb.io/enzyme/) for rendering React components where relevant. If you are not familiar with these libraries, we would urge you to do some reading before getting started. Our goal is that each of our packages, where relevant, should have ~90% coverage of functions and lines. Whilst this target is an arbitrary value, the desired outcome is a high level of confidence in our CI / CD pipeline which means we can deploy straight to development and daily to production.

By convention, we keep our test scripts in a sub folder of the source code called `__tests__` with the same file name. Where we use mocks and stubs, as with tests, they live in the same folder of the source code with the same file name and sub folder convention `__stubs__` and `__mocks__` .

For React components as a bare minimum, we expect a snapshot of the shallow rendered component, with snapshots saving to the `__snapshots__` sub folder of the component.

End to end functional tests are all written using the excellent Cypress framework. Whilst it does not support cross browser testing for older browsers, we feel it is a decent tradeoff owing to the speed, developer experience and reliability of the tests over conventional Selenium / Webdriver tests.

Where relevant, files e2e test specs are placed in the `src/tests/cypress` folder of the package. We use the `Page Object Model` pattern, storing anything related to a specific page; selectors and actions, to make them more re-usable and modular.

When raising a pull request, please ensure that existing tests are passing locally and that where relevant, new tests are added to maintain our overall coverage levels.

