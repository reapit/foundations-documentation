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

### Development



### Environment & Config



All ENVs are loaded in reapit-config.json. No .env file required to setup e2e test. Key with value type is an object won't be loaded. E.g. {load: 'load', notLoad: {key: 'value}} -&gt; key notLoad will not be loaded to Cypress as an ENV

Required ENVs are:

* DEVELOPER\_ACCOUNT\_EMAIL - email of the developer account that will be used to testing
* DEVELOPER\_ACCOUNT\_PASSWORD - password of the developer account that will be used to testing
* CLIENT\_ACCOUNT\_EMAIL - email of the client account that will be used to testing
* CLIENT\_ACCOUNT\_PASSWORD - password of the client account that will be used to testing
* ADMIN\_ACCOUNT\_EMAIL - email of the admin account that will be used to testing
* ADMIN\_ACCOUNT\_PASSWORD - password of the admin account that will be used to testing
* APPLICATION\_URL - URL of the web application to test against

### Testing



* Files involved e2e testing will be placed in `src/tests/cypress`.
* Pages: Use `Page Object Model` pattern: store anything related to a specific page: selectors, reusable actions.
* Commands: Any utility actions that not involve specific page
*  * yarn test-e2e:dev - open cypress dashboard allowed you to choose specific test file to testing
  * yarn test-e2e - execute cypress tests in headless mode

## Code Style

### Linting & Formatting

The vast majority of base code style is enforced by [TSLint](https://palantir.github.io/tslint/), with sensible community presets from [StandardJS](https://standardjs.com/) and [Prettier](https://prettier.io/). The linter runs in a pre-commit hook on staged files with an auto-fix flag set to address any trivial issues. TS Lint also runs in a parallel process with the TS Compiler so you will get constant feedback in the terminal on linting issues.

In addition to the lint rules, please also where possible, stick to the contribution guidelines below. These rules should be kept in mind when reviewing Pull Requests.

### Code Guidelines

* Code should be functional in style rather than Object Orientated or Imperative unless there are no clean alternatives.
  * Use pure functions where possible to make them testable and modular.
  * Avoid mutating varibles and the `let` keyword.
  * React Components should be stateless functional components where possible.
  * Avoid classes and stateful modules where possible.
  * Avoid React lifecyle hooks.
  * Keep all state in Redux and business logic as pure functions of Redux State.
  * The above rules can be relaxed for test scripts.
* React components should be templates, free of logic. This is because we aim to re-use code in the future in React Native Applications so by keeping the React layer as purely presentational.
  * Presentational logic helpers should live in a utils file in the same folder as your component so they can be re-used agnostic of the template.
* Use Redux connect for nested components for better performance and reduced re-rendering over `prop drilling`. Use `React.memo` for the same reason and selectors if appropriate.
* Typesafe everything! Use `any` and `unknown` types only when there is no alternative - try to avoid `implicit any` - types should be documentation as code for the project. We can relax this as a convenience in test scripts.
  * Where possible use auto generated types from Swagger documentation or GraphQL defintions to ensure shared contracts with front and back end. These auto-generated types live in the main types folder.
* Syled Components are used for styling in all cases where a third party library \(eg Bootstrap\) is not used.
  * Styled Components should be kept out of the main components folder - they should live in the main styles folder. This is so we can easily abstract the styles into a styleguide the future, using a tool like Storybook or Bit. It also helps with reducing duplication.
  * The styles project should make extensive use of variables and mixins for things like colors, layouts, font sizes, line heights and so on. This ensures re-usablility and maintainability.
  * Where possible, use `rems` over `px` as a unit for layout.
* Maintain the separation of concerns in the folder structure laid out in the initial scaffold seen in the [React App Boilerplate](https://github.com/reapit/react-app) eg, reducers should all be in the reducers folder, global types in the types folder and so on. There are many React projects in the company and they should all follow a broadly familiar structure and architecture.
* Make extensive use of the constants files for significant strings and other re-usable constant variables used in the app.
* When adding third party libraries to the project consider carefully the following;
  * Is this a trivial package we can easily write in house? If so, take the time to roll your own.
  * Is this library well supported, under active development and widely used in the community? If not, do not use.
  * Do we use a similar but different library for the same task elsewhere in the company? If so, use this library for developer familiarity and consistency.
  * Will this library impact significantly performance or bundle size eg Lodash or Moment? If so, consider carefully if it is necessary or if there is a better alternative.
* We have two kinds of tests; Unit tests with Jest and e2e tests with Webdriver. For all new features an approprate level of test coverage is an implicit part of the feature definition.
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
* Exports from files can be either as variable or default exports, but please stick to naming the object before using `export default` to avoid anonomous module names in stack traces and React dev tools.

## Workflow

### Github Issues & Projects



### Version Control



When working on the project, please observe the following workflow:

* Branches are of three types `feature/...`, `hotfix/...` or `task/...` mapping to the JIRA ticket types of `story`, `bug` and `task`.
* Branch names should follow the pattern of `<issue type>/<JIRA-REF>-<brief-description>` for example `feature/LABS-1-some-cool-feature`.
* Typically, `develop` is the base branch for all branches, the exception being a hotfix on production code. In this case, `master` is the base and the hotfix should be back merged when deployed.
* Commits should be prefaced with the JIRA ref eg `"[LABS-1] My commit message"` so progress can be tracked on JIRA.
* To merge back into the base branch, raise a pull request aginst this branch. All checks should pass and at least one approver is necessary to merge into base.
* Keep your branch up to date at all times with the base branch by `rebase` only, to keep the tree clean.
* On merging to base, use `squash and merge`, to keep the tree clean and to make rolling back changes easy.

### Github Actions & CI / CD



We currently deploy static assets to S3 buckets.

* [Develop environment](https://d3ps8i1lmu75tx.cloudfront.net) is triggered by pushs to `develop` branch
* [Production environment](https://dvyjx6qs1jinm.cloudfront.net) is triggered by tag

  pushs with `AS-` prefix, eg. pushing `AS-0.0.1` tag will trigger a build pipeline

  and deploy it's output assets to Production S3 bucket

### Definition of Done

A JIRA issue is considered ready to be moved to the `done` column only when the follwing checklist has been completed.

* The complete acceptance criteria or task list on the JIRA ticket has been fulfilled. To be verified by a PO if appropriate.
* The feature has appropriate unit and end to end tests.
* The feature has been verified as working by a QA if appropriate.
* All tests and checks on Github are passing.
* The feature is up to date with the base branch.
* The feature has had at least one peer reviewer and that they have approved the feature for release.
* The feature has been merged and deployed into the base branch.

















