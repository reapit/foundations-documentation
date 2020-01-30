# E2E\_TESTING

## Notes

## ENV

All ENVs are loaded in reapit-config.json. No .env file required to setup e2e test. Key with value type is an object won't be loaded. E.g. {load: 'load', notLoad: {key: 'value}} -&gt; key notLoad will not be loaded to Cypress as an ENV

Required ENVs are:

* DEVELOPER\_ACCOUNT\_EMAIL - email of the developer account that will be used to testing
* DEVELOPER\_ACCOUNT\_PASSWORD - password of the developer account that will be used to testing
* CLIENT\_ACCOUNT\_EMAIL - email of the client account that will be used to testing
* CLIENT\_ACCOUNT\_PASSWORD - password of the client account that will be used to testing
* ADMIN\_ACCOUNT\_EMAIL - email of the admin account that will be used to testing
* ADMIN\_ACCOUNT\_PASSWORD - password of the admin account that will be used to testing
* APPLICATION\_URL - URL of the web application to test against

## Structure

* Files involved e2e testing will be placed in `src/tests/cypress`.
* Pages: Use `Page Object Model` pattern: store anything related to a specific page: selectors, reusable actions.
* Commands: Any utility actions that not involve specific page

## Commands

* yarn test-e2e:dev - open cypress dashboard allowed you to choose specific test file to testing
* yarn test-e2e - execute cypress tests in headless mode

