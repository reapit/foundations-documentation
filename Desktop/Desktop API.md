<div class="container-flex is-column   has-padding  ">

<div class="content desktop-api-docs-desktop-api-docs-3aGz1">

<div class="container is-column  has-background has-padding  ">

### Desktop Documentation

#### Contents

*   [API Introduction](#api)
*   [Property](#property)
*   [Applicants](#applicants)
*   [Appointments](#appointments)
*   [Contacts](#contacts)
*   [Agency Cloud Interaction API](#agency-cloud)

#### API Introduction

##### Overview

Applications that are built on our Foundations Platform are able to communicate with Reapit's Agency Cloud CRM system. Using a well-defined API, you are able to trigger a wide variety of actions in our award-winning desktop application to augment your own applications and build a rich integration between systems.

##### URL Scheme

When a Marketplace application is launched and hosted within Agency Cloud, that application can interact with Agency Cloud by using our custom URI scheme. When a user triggers a link with an agencycloud: prefix, Agency Cloud will interpret that action and perform the corresponding action.

##### Format

Links are structured in a REST style to provide a well-defined and descriptive mechanism for interacting with the screens and functionality that Agency Cloud offers. The primary and secondary screens that exist in the Agency Cloud user interface broadly map to the REST notion of resources and sub-resources. Some actions also accept parameters which can be applied to the URI in the usual manner. Full documentation of the available interactions is listed below, grouped by primary screen.

#### Property

##### Load Property

Opens the property edit screen for the property with specified id

    agencycloud://properties/{id}

##### Perform Matching

Performs a property to applicant match for the applicant with specified id

    agencycloud://properties/{id}/match

##### Load Journal

Opens the journal screen for the specified property

    agencycloud://properties/{id}/journal

##### Load Offers

Opens the offers screen for the specified property

    agencycloud://properties/{id}/offers

##### Property Search

Opens advanced search screen in property mode and runs a search with provided parameters. At least one parameter is required.

    agencycloud://properties?address=MK43&mode=s

<div class="table-responsive">

<table class="table is-striped is-fullwidth ">

<thead>

<tr class="">

<th colspan="1" class="">Parameter</th>

<th colspan="1" class="">Type</th>

<th colspan="1" class="">Description</th>

<th colspan="1" class="">Required</th>

</tr>

</thead>

<tbody>

<tr class="">

<td class="">name</td>

<td class="">string</td>

<td class="">A full or partial name fragment to search for</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">address</td>

<td class="">string</td>

<td class="">An address fragment to search for (eg. a postcode)</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">communication</td>

<td class="">string</td>

<td class="">An email address or phone number to search for</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">mode</td>

<td class="">string</td>

<td class="">The marketing mode of the properties to search for</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">appId</td>

<td class="">string</td>

<td class="">The GUID of the app to return the code of the selected property to (if not present then search will not return to an app)</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">appParam</td>

<td class="">string</td>

<td class="">The key to use in the query string when returning the property primary key to an app (required if appId is set)</td>

<td class="">No?</td>

</tr>

</tbody>

</table>

</div>

#### Applicants

##### Load Applicant

Opens the applicant edit screen for the applicant with specified id

    agencycloud://applicants/{id}

##### Perform Matching

Performs a applicant to applicant match for the applicant with specified id

    agencycloud://applicants/{id}/match

##### Load Journal

Opens the journal screen for the specified applicant

    agencycloud://applicants/{id}/journal

##### Applicant Search

Opens advanced search screen in applicant mode and runs a search with provided parameters. At least one parameter is required.

    agencycloud://applicants?name=smith&mode=lettings

<div class="table-responsive">

<table class="table is-striped is-fullwidth ">

<thead>

<tr class="">

<th colspan="1" class="">Parameter</th>

<th colspan="1" class="">Type</th>

<th colspan="1" class="">Description</th>

<th colspan="1" class="">Required</th>

</tr>

</thead>

<tbody>

<tr class="">

<td class="">name</td>

<td class="">string</td>

<td class="">A full or partial name fragment to search for</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">address</td>

<td class="">string</td>

<td class="">An address fragment to search for (eg. a postcode)</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">communication</td>

<td class="">string</td>

<td class="">An email address or phone number to search for</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">mode</td>

<td class="">string</td>

<td class="">The marketing mode of the properties to search for</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">appId</td>

<td class="">string</td>

<td class="">The GUID of the app to return the code of the selected property to (if not present then search will not return to an app)</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">appParam</td>

<td class="">string</td>

<td class="">The key to use in the query string when returning the property primary key to an app (required if appId is set)</td>

<td class="">No?</td>

</tr>

</tbody>

</table>

</div>

#### Appointments

##### Load Diary

Opens the diary screen to provide a calendar view of appointments for the given date range. The dates don’t need to be set, but if you set one, you need to set both. If you don’t set a date range then the current default dates for the negotiator will be used.

    agencycloud://appointments?dateFrom=2019/12/25&dateTo=2019/12/26

<div class="table-responsive">

<table class="table is-striped is-fullwidth ">

<thead>

<tr class="">

<th colspan="1" class="">Parameter</th>

<th colspan="1" class="">Type</th>

<th colspan="1" class="">Description</th>

<th colspan="1" class="">Required</th>

</tr>

</thead>

<tbody>

<tr class="">

<td class="">dateFrom</td>

<td class="">date</td>

<td class="">Only display appointments scheduled after and including this date</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">dateTo</td>

<td class="">date</td>

<td class="">Only display appointments scheduled before this date</td>

<td class="">No</td>

</tr>

</tbody>

</table>

</div>

#### Contacts

##### Contact Search

Opens advanced search screen in contact mode and runs a search with provided parameters. At least one parameter is required.

    agencycloud://contacts?name=smith

<div class="table-responsive">

<table class="table is-striped is-fullwidth ">

<thead>

<tr class="">

<th colspan="1" class="">Parameter</th>

<th colspan="1" class="">Type</th>

<th colspan="1" class="">Description</th>

<th colspan="1" class="">Required</th>

</tr>

</thead>

<tbody>

<tr class="">

<td class="">name</td>

<td class="">string</td>

<td class="">A full or partial name fragment to search for</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">address</td>

<td class="">string</td>

<td class="">An address fragment to search for (eg. a postcode)</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">communication</td>

<td class="">string</td>

<td class="">An email address or phone number to search for</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">appId</td>

<td class="">string</td>

<td class="">The GUID of the app to return the code of the selected contact to (if not present then search will not return to an app)</td>

<td class="">No</td>

</tr>

<tr class="">

<td class="">appParam</td>

<td class="">string</td>

<td class="">The key to use in the query string when returning the contact primary key to an app (required if appId is set)</td>

<td class="">No?</td>

</tr>

</tbody>

</table>

</div>

##### Load Contact

Opens the contact edit screen for the contact with specified id

    agencycloud://contacts/{id}

##### Load Journal

Opens the journal screen for the specified contact

    agencycloud://contacts/{id}/journal

#### Agency Cloud Interaction API

##### Overview

Not only can Applications built on the Foundations Platform trigger events in the Agency Cloud CRM system, but installed apps can also be associated with common actions in Agency Cloud to replace the default behaviour.

The most common way that this will manifest itself is by replacing a screen in Agency Cloud with an application. For example if you want to use an App to manage all of your AML and ID checking then you can associate the app with this action in Agency Cloud and every time you click to launch the ID check screen, the associated App will be presented instead.

Another area which is possible to replace here is default functionality such as sending an SMS which currently is sometimes done now by hooking up to a 3rd party API, but instead purpose built app could provide a richer user experience to be able to edit the message before it is sent, and possibly choose the recipients of the message.

All apps should be able to be launched from the Installed Apps screen and be ran standalone without the need to be linked to an action. They will just be hosted in the marketplace and launched in Agency Cloud – for example the Geo Diary application.

##### Categorisation

To be able to associate an application with an action in Agency Cloud the application will need to be given a category. This will be required so that Agency Cloud can be confident of the way the application will behave and that the application is agreeing to accept certain parameters when launched.

For example – an AML or ID checking app will need to be able to accept a query parameter in the launch url of cntCode which tells the application which contact to show the ID checks for.

Possible associations;

*   ID Check
*   Property Detail Generation (print wizard)
*   Applicant Preview

#### Categories

##### Id Check

The category of ID Check will be given to an application that can be used to replace the ID Check screen in Agency Cloud. The url that an application with this category would look like would be:

    https://{AppLaunchUrl}?Username={loggedInUserEmail}&Desktop=true&CntCode={PrimaryKey}

<div class="table-responsive">

<table class="table is-striped is-fullwidth ">

<thead>

<tr class="">

<th colspan="1" class="">Parameter</th>

<th colspan="1" class="">Type</th>

<th colspan="1" class="">Description</th>

<th colspan="1" class="">Required</th>

</tr>

</thead>

<tbody>

<tr class="">

<td class="">username</td>

<td class="">string</td>

<td class="">The username of the user logged into Agency Cloud</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">desktop</td>

<td class="">boolean</td>

<td class="">This will always be passed as True to indicate app should run in desktop mode (if it has/needs one)</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">cntCode</td>

<td class="">string</td>

<td class="">The primary key of the contact to load the ID checks for (note that this won’t be present when the app loads from the marketplace, but the app needs to be able to accept this parameter when it is launched via the app association route).</td>

<td class="">Yes</td>

</tr>

</tbody>

</table>

</div>

##### Property Detail Generation

The category of Property Detail Generation can be given to an application that can replace the standard details template generation and brochure ordering process. This application could allow selection of a template as defined in the application – selection of pictures to include, what paper size to print the brochures on etc The url that this application would use would be like:

    https://{AppLaunchUrl}?Username={loggedInUserEmail}&Desktop=true&PrpCode={PrimaryKey}

<div class="table-responsive">

<table class="table is-striped is-fullwidth ">

<thead>

<tr class="">

<th colspan="1" class="">Parameter</th>

<th colspan="1" class="">Type</th>

<th colspan="1" class="">Description</th>

<th colspan="1" class="">Required</th>

</tr>

</thead>

<tbody>

<tr class="">

<td class="">username</td>

<td class="">string</td>

<td class="">The username of the user logged into Agency Cloud</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">desktop</td>

<td class="">boolean</td>

<td class="">This will always be passed as True to indicate app should run in desktop mode (if it has/needs one)</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">prpCode</td>

<td class="">string</td>

<td class="">The primary key of the property to load generate the brochures for (note that this won’t be present when the app loads from the marketplace, but the app needs to be able to accept this parameter when it is launched via the app association route).</td>

<td class="">Yes</td>

</tr>

</tbody>

</table>

</div>

##### Applicant Preview

The category of Applicant Preview would enable an application to be used to display a list of properties to a user. The application would need to be able to take a comma separated list of property codes which to display. The url that this application would use would be like:

    https://{AppLaunchUrl}?Username={loggedInUserEmail}&Desktop=true &PrpCodes={List of PrimaryKeys}

<div class="table-responsive">

<table class="table is-striped is-fullwidth ">

<thead>

<tr class="">

<th colspan="1" class="">Parameter</th>

<th colspan="1" class="">Type</th>

<th colspan="1" class="">Description</th>

<th colspan="1" class="">Required</th>

</tr>

</thead>

<tbody>

<tr class="">

<td class="">username</td>

<td class="">string</td>

<td class="">The username of the user logged into Agency Cloud</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">desktop</td>

<td class="">boolean</td>

<td class="">This will always be passed as True to indicate app should run in desktop mode (if it has/needs one)</td>

<td class="">Yes</td>

</tr>

<tr class="">

<td class="">prpCodes</td>

<td class="">string</td>

<td class="">The primary key of the property to load generate the brochures for (note that this won’t be present when the app loads from the marketplace, but the app needs to be able to accept this parameter when it is launched via the app association route).</td>

<td class="">Yes</td>

</tr>

</tbody>

</table>

</div>

</div>

</div>

</div>