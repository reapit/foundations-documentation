# GETTING\_STARTED

## Getting started

### First

```text
brew install node

brew install yarn
```

### To build for dev

```text
yarn

yarn dev
```

HMR dev server available on [port 8080](http://localhost:8080)

### To build for prod

```text
yarn build

yarn start
```

Again, server available on [port 8080](http://localhost:8080)

### To run the linter \(Prettier & TSLint\)

```text
yarn lint
```

This also runs as a pre-commit hook

### To run the unit tests \(Jest & Enzyme\)

```text
yarn test
```

This also runs as a pre-push hook

### To run the unit tests in dev mode

```text
yarn test-dev
```

### To run the performance Tests \(Lighthouse & Jest\)

```text
yarn test-perf
```

### To run the E2E Dash board allowing you to choose specific test case \(Cypress\)

```text
yarn test-e2e:dev
```

### To run the E2E Tests in headless mode \(Cypress\)

```text
yarn test-e2e
```

### To run an analysis of bundles and packages

```text
yarn bundle-analyse
```

## Read on:

* [Home](https://github.com/reapit/foundations-documentation/tree/777f5a5c6d6e2d106c049a6fbf696ba3f4ddfd95/Open%20Source/README.md)
* [Api Platform](api_platform.md)
* [Code Style](code_style.md)
* [Version Control](version_control.md)
* [Definition of Done](definition_of_done.md)
* [Deployment](deployment.md)

