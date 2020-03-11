---
description: >-
  An API to interact between the Reapit Agency Cloud CRM and a Marketplace Web
  Application
---

# Desktop

{% hint style="danger" %}
The Desktop API is not available during the Alpha period.
{% endhint %}

{% hint style="info" %}
To obtain a copy of Reapit's Agency Cloud CRM, you must be sponsored by a Reapit Client.
{% endhint %}

### Overview

Applications that are built on our Foundations Platform are able to communicate with Reapit's Agency Cloud CRM system. Using a well-defined API, you are able to trigger a wide variety of actions in our award-winning desktop application to augment your own applications and build a rich integration between systems.

### URL Scheme

When a Marketplace application is launched and hosted within Agency Cloud, that application can interact with Agency Cloud by using our custom URI scheme. When a user triggers a link with an agencycloud: prefix, Agency Cloud will interpret that action and perform the corresponding action.

### Format

Links are structured in a REST style to provide a well-defined and descriptive mechanism for interacting with the screens and functionality that Agency Cloud offers. The primary and secondary screens that exist in the Agency Cloud user interface broadly map to the REST notion of resources and sub-resources. Some actions also accept parameters which can be applied to the URI in the usual manner. Full documentation of the available interactions is listed below, grouped by primary screen.

## Property

### Load Property

Opens the property edit screen for the property with specified id

```text
agencycloud://properties/{id}
```

### Perform Matching

Performs a property to applicant match for the applicant with specified id

```text
agencycloud://properties/{id}/match
```

### Load Journal

Opens the journal screen for the specified property

```text
agencycloud://properties/{id}/journal
```

### Load Offers

Opens the offers screen for the specified property

```text
agencycloud://properties/{id}/offers
```

### Property Search

Opens advanced search screen in property mode and runs a search with provided parameters. At least one parameter is required.

```text
agencycloud://properties?address=MK43&mode=s
```

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| name | string | A full or partial name fragment to search for | No |
| address | string | An address fragment to search for \(eg. a postcode\) | No |
| communication | string | An email address or phone number to search for | No |
| mode | string | The marketing mode of the properties to search for | Yes |
| appId | string | The GUID of the app to return the code of the selected property to \(if not present then search will not return to an app\) | No |
| appParam | string | The key to use in the query string when returning the property primary key to an app \(required if appId is set\) | No? |

## Applicants

### Load Applicant

Opens the applicant edit screen for the applicant with specified id

```text
agencycloud://applicants/{id}
```

### Perform Matching

Performs a applicant to applicant match for the applicant with specified id

```text
agencycloud://applicants/{id}/match
```

### Load Journal

Opens the journal screen for the specified applicant

```text
agencycloud://applicants/{id}/journal
```

### Applicant Search

Opens advanced search screen in applicant mode and runs a search with provided parameters. At least one parameter is required.

```text
agencycloud://applicants?name=smith&mode=lettings
```

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| name | string | A full or partial name fragment to search for | No |
| address | string | An address fragment to search for \(eg. a postcode\) | No |
| communication | string | An email address or phone number to search for | No |
| mode | string | The marketing mode of the properties to search for | Yes |
| appId | string | The GUID of the app to return the code of the selected property to \(if not present then search will not return to an app\) | No |
| appParam | string | The key to use in the query string when returning the property primary key to an app \(required if appId is set\) | No? |

## Appointments

### Load Diary

Opens the diary screen to provide a calendar view of appointments for the given date range. The dates don’t need to be set, but if you set one, you need to set both. If you don’t set a date range then the current default dates for the negotiator will be used.

```text
agencycloud://appointments?dateFrom=2019/12/25&dateTo=2019/12/26
```

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| dateFrom | date | Only display appointments scheduled after and including this date | No |
| dateTo | date | Only display appointments scheduled before this date | No |

## Contacts

### Contact Search

Opens advanced search screen in contact mode and runs a search with provided parameters. At least one parameter is required.

```text
agencycloud://contacts?name=smith
```

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| name | string | A full or partial name fragment to search for | No |
| address | string | An address fragment to search for \(eg. a postcode\) | No |
| communication | string | An email address or phone number to search for | No |
| appId | string | The GUID of the app to return the code of the selected contact to \(if not present then search will not return to an app\) | No |
| appParam | string | The key to use in the query string when returning the contact primary key to an app \(required if appId is set\) | No? |

### Load Contact

Opens the contact edit screen for the contact with specified id

```text
agencycloud://contacts/{id}
```

### Load Journal

Opens the journal screen for the specified contact

```text
agencycloud://contacts/{id}/journal
```

## Agency Cloud Interaction API

### Overview

Not only can Applications built on the Foundations Platform trigger events in the Agency Cloud CRM system, but installed apps can also be associated with common actions in Agency Cloud to replace the default behaviour.

The most common way that this will manifest itself is by replacing a screen in Agency Cloud with an application. For example if you want to use an App to manage all of your AML and ID checking then you can associate the app with this action in Agency Cloud and every time you click to launch the ID check screen, the associated App will be presented instead.

Another area which is possible to replace here is default functionality such as sending an SMS which currently is sometimes done now by hooking up to a 3rd party API, but instead purpose built app could provide a richer user experience to be able to edit the message before it is sent, and possibly choose the recipients of the message.

All apps should be able to be launched from the Installed Apps screen and be ran standalone without the need to be linked to an action. They will just be hosted in the marketplace and launched in Agency Cloud – for example the Geo Diary application.

### Categorisation

To be able to associate an application with an action in Agency Cloud the application will need to be given a category. This will be required so that Agency Cloud can be confident of the way the application will behave and that the application is agreeing to accept certain parameters when launched.

For example – an AML or ID checking app will need to be able to accept a query parameter in the launch url of cntCode which tells the application which contact to show the ID checks for.

Possible associations;

* ID Check
* Property Detail Generation \(print wizard\)
* Applicant Preview

## Categories

### Id Check

The category of ID Check will be given to an application that can be used to replace the ID Check screen in Agency Cloud. The url that an application with this category would look like would be:

```text
https://{AppLaunchUrl}?Username={loggedInUserEmail}&Desktop=true&CntCode={PrimaryKey}
```

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| username | string | The username of the user logged into Agency Cloud | Yes |
| desktop | boolean | This will always be passed as True to indicate app should run in desktop mode \(if it has/needs one\) | Yes |
| cntCode | string | The primary key of the contact to load the ID checks for \(note that this won’t be present when the app loads from the marketplace, but the app needs to be able to accept this parameter when it is launched via the app association route\). | Yes |

### Property Detail Generation

The category of Property Detail Generation can be given to an application that can replace the standard details template generation and brochure ordering process. This application could allow selection of a template as defined in the application – selection of pictures to include, what paper size to print the brochures on etc The url that this application would use would be like:

```text
https://{AppLaunchUrl}?Username={loggedInUserEmail}&Desktop=true&PrpCode={PrimaryKey}
```

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| username | string | The username of the user logged into Agency Cloud | Yes |
| desktop | boolean | This will always be passed as True to indicate app should run in desktop mode \(if it has/needs one\) | Yes |
| prpCode | string | The primary key of the property to load generate the brochures for \(note that this won’t be present when the app loads from the marketplace, but the app needs to be able to accept this parameter when it is launched via the app association route\). | Yes |

### Applicant Preview

The category of Applicant Preview would enable an application to be used to display a list of properties to a user. The application would need to be able to take a comma separated list of property codes which to display. The url that this application would use would be like:

```text
https://{AppLaunchUrl}?Username={loggedInUserEmail}&Desktop=true &PrpCodes={List of PrimaryKeys}
```

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| username | string | The username of the user logged into Agency Cloud | Yes |
| desktop | boolean | This will always be passed as True to indicate app should run in desktop mode \(if it has/needs one\) | Yes |
| prpCodes | string | The primary key of the property to load generate the brochures for \(note that this won’t be present when the app loads from the marketplace, but the app needs to be able to accept this parameter when it is launched via the app association route\). | Yes |

