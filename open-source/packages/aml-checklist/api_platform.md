# API Platform

To work with the Reapit Platform API you will need to follow these steps;

* Register with the developer portal [here](https://reapit.cloud.tyk.io/portal/)
* When you receive the confirmation email, login and request an API key. This is a manual process so it may take a while \(although it shouldn't!\).
* When you have the key navigate to `./src/constants` and rename the `.env.example` file to `.env`. 
* Copy your API key to the file next to the `REAPIT_API_KEY` variable.

You are good to go!

The API key should be included as an Authorisation header when fetching from the API. It is made available by webpack in the app by Webpack so you can reference it with `process.env.REAPIT_API_KEY`.

The schema definition is fetched from a Swagger endpoint by running the command `yarn fetch-definitions`. This then parses the Swagger defs into TypeScript definitions, complete with comments and writes to the `./src/types/tyke-api-schema.ts` file. This file should be the only reference point for API data definitions **do not write your own interfaces for data!**

If you get an API runtime error because of an incorrect definition, firstly fetch the defintions again so they are up-to-date and if you still have a problem, raise an issue with the Platform Team to update the Swagger defintion.

## Authentication

Because the app has three distinct permissioned areas, you need different dev credentials to access each area of the site.

For a client, you can login at `/login` with `plittlewood@reapit.com` and `T00lb0x53` For a developer, you can login at `/login` with `wmcvay@reapit.com` and `T00lb0x53` For an admin, you can login at `/admin/login` with `rwilcox@reapit.com` and `T00lb0x53`

## Read on:

* [Home](https://github.com/reapit/foundations-documentation/tree/777f5a5c6d6e2d106c049a6fbf696ba3f4ddfd95/Open%20Source/README.md)
* [Getting Started](getting_started.md)
* [Code Style](code_style.md)
* [Version Control](version_control.md)
* [Definition of Done](definition_of_done.md)
* [Deployment](deployment.md)

