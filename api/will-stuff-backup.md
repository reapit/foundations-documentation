# Will stuff backup

To work with the Reapit Platform API you will need to follow these steps;

* Register with the developer portal [here](https://reapit.cloud.tyk.io/portal/)
* When you receive the confirmation email, login and request an API key. This is a manual process so it may take a while \(although it shouldn't!\).
* When you have the key navigate to `./src/constants` and rename the `.env.example` file to `.env`. 
* Copy your API key to the file next to the `REAPIT_API_KEY` variable.

You are good to go!

The API key should be included as an Authorisation header when fetching from the API. It is made available by webpack in the app by Webpack so you can reference it with `process.env.REAPIT_API_KEY`.

The schema defintion is fetched from a Swagger endpoint by running the command `yarn fetch-definitions`. This then parses the Swagger defs into TypeScript definitions, complete with comments and writes to the `./src/types/tyke-api-schema.ts` file. This file should be the only reference point for API data definitions **do not write your own interfaces for data!**

If you get an API runtime error because of an incorrect definition, firstly fetch the defintions again so they are up-to-date and if you still have a problem, raise an issue with the Platform Team to update the Swagger defintion.

## Authentication

Because the app has three distinct permissioned areas, you need different dev credentials to access each area of the site.

For a client, you can login at `/login` with `cbryan@reapit.com` and `T00lb0x53` For a developer, you can login at `/login` with `wmcvay@reapit.com` and `T00lb0x53` For an admin, you can login at `/admin/login` with `rwilcox@reapit.com` and `T00lb0x53`

\`\`

## Elements

The Elements UI toolkit you can browse [here](https://github.com/reapit/foundations-documentation/tree/db0718c9be27b7760dfae34e69518806acf0e855/developer/elements/README.md) is available as an NPM package. We also support an AMD \(require.js\), version that may suit your needs better, especially when serving content from a CDN or CMS.

## React App Scaffolder

Content

## Cognito Auth

Content

## Foundations TS Definitions

If you are using TypeScript \(and we recommend you do!\), for your front end project, we provide full type definitions for the API documented in the [API explorer](https://github.com/reapit/foundations-documentation/tree/db0718c9be27b7760dfae34e69518806acf0e855/developer/swagger/README.md). We generate these types from the Swagger contracts direct so you can be sure that when the API changes, your types will be updated also. This allows for a much closer alignment between front and back end development and ultimately more robust applications.

