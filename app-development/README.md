---
description: A guide to building web applications for the Reapit AppMarket
---

# App Development

At Reapit we want to make it as easy as possible to get started building apps against our platform APIs. For this reason we have open sourced a lot of the tooling we use internally for App Development for our App Partners to use.

As you will have read in the [developer portal guide](../developer-portal.md), for developers familiar with React a great place to get started is the Create React App Template, which extends Facebook's CRA scripts with Reapit tooling.

If you are planning to build a AppMarket App that is launched from the AgencyCloud CRM, we ask that you adhere to our interactive Style Guide [Elements](elements.md). This is distributed as an NPM package with components for React users and a stylesheet for Non React users.

We understand that authenticating your app using [Reapit Connect](../api/reapit-connect.md) single sign on can be a pain point and to smooth this process over, we have built a low dependency, framework agnostic auth package on NPM, [Connect Session](connect-session.md). This exports Vanilla JS, NodeJS and React versions and handles all redirecting, caching and refreshing of your session. 

In addition, we export up to date [TypeScript definitions](foundations-ts-defintions.md) of the Platform API, with [Web Component](web.md) widgets to extend any site with Reapit functionality coming very soon.

