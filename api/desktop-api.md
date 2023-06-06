---
description: >-
  An API to interact between the Reapit AgencyCloud CRM and a AppMarket Web
  Application
---

# Desktop API

{% hint style="info" %}
To obtain a copy of Reapit's AgencyCloud CRM (Developer Edition), please visit the '[Desktop](https://marketplace.reapit.cloud/developer/desktop)' page within the Developers Portal. NOTE Reapit does not provide technical support for Developer Edition.
{% endhint %}

{% hint style="warning" %}
During the Beta period certain elements of AgencyCloud may not function end-to-end with a web application.  For example, pictures or documents added to Agency Cloud via the desktop will not be available via the platform.&#x20;
{% endhint %}

### Overview

Applications that are built on our Foundations Platform are able to communicate with Reapit's AgencyCloud CRM system. Using a well-defined API, you are able to trigger a wide variety of actions in our award-winning desktop application to augment your own applications and build a rich integration between systems.

_Note_ - apps cannot rely on cookies/local storage being available between separate instances of AgencyCloud.  Therefore any data which will need to be shared between separate sessions will need to be handled outside of these methods.

### Debugging your App

When you are testing your app inside of AgencyCloud Developer Edition then there is a button top left of the app window which will allow launching of the Chromium Developer Tools in a separate window. &#x20;

![Remote debugging button on the app ribbon bar](<../.gitbook/assets/image (51).png>)

Clicking this button will launch a separate window which hosts the developer tools:

![Remote debugging via the developer tools window](<../.gitbook/assets/image (52).png>)

### URL Scheme

When a AppMarket application is launched and hosted within AgencyCloud, that application can interact with AgencyCloud by using our custom URI scheme. When a user triggers a link with an agencycloud: prefix, AgencyCloud will interpret that action and perform the corresponding action.

### Format

Links are structured in a REST style to provide a well-defined and descriptive mechanism for interacting with the screens and functionality that AgencyCloud offers. The primary and secondary screens that exist in the AgencyCloud user interface broadly map to the REST notion of resources and sub-resources. Some actions also accept parameters which can be applied to the URI in the usual manner. Full documentation of the available interactions is listed below, grouped by primary screen.

## Property

### Load Property

Opens the property edit screen for the property with specified id

```
agencycloud://properties/{id}
```

### Perform Matching

Performs a property to applicant match for the applicant with specified id

```
agencycloud://properties/{id}/match
```

### Load Journal

Opens the journal screen for the specified property

```
agencycloud://properties/{id}/journal
```

### Load Offers

Opens the offers screen for the specified property

```
agencycloud://properties/{id}/offers
```

### Property Search

Opens advanced search screen in property mode and runs a search with provided parameters. At least one parameter is required.

```
agencycloud://properties?address=MK43&mode=s
```

| Parameter     | Type   | Description                                                                                                               | Required |
| ------------- | ------ | ------------------------------------------------------------------------------------------------------------------------- | -------- |
| name          | string | A full or partial name fragment to search for                                                                             | No       |
| address       | string | An address fragment to search for (eg. a postcode)                                                                        | No       |
| communication | string | An email address or phone number to search for                                                                            | No       |
| mode          | string | <p>The marketing mode of the properties to search for:</p><ul><li>s or sales</li><li>l or lettings</li></ul>              | Yes      |
| appId         | string | The GUID of the app to return the code of the selected property to (if not present then search will not return to an app) | No       |
| appParam      | string | The key to use in the query string when returning the property primary key to an app (required if appId is set)           | No       |

## Applicants

### Load Applicant

Opens the applicant edit screen for the applicant with specified id

```
agencycloud://applicants/{id}
```

### Perform Matching

Performs a applicant to applicant match for the applicant with specified id

```
agencycloud://applicants/{id}/match
```

### Load Journal

Opens the journal screen for the specified applicant

```
agencycloud://applicants/{id}/journal
```

### Applicant Search

Opens advanced search screen in applicant mode and runs a search with provided parameters. At least one parameter is required.

```
agencycloud://applicants?name=smith&mode=lettings
```

| Parameter     | Type   | Description                                                                                                               | Required |
| ------------- | ------ | ------------------------------------------------------------------------------------------------------------------------- | -------- |
| name          | string | A full or partial name fragment to search for                                                                             | No       |
| address       | string | An address fragment to search for (eg. a postcode)                                                                        | No       |
| communication | string | An email address or phone number to search for                                                                            | No       |
| mode          | string | <p>The marketing mode of the properties to search for:</p><ul><li>s or sales</li><li>l or lettings</li></ul>              | Yes      |
| appId         | string | The GUID of the app to return the code of the selected property to (if not present then search will not return to an app) | No       |
| appParam      | string | The key to use in the query string when returning the property primary key to an app (required if appId is set)           | No       |

## Appointments

### Load Diary

Opens the diary screen to provide a calendar view of appointments for the given date range. The dates don’t need to be set, but if you set one, you need to set both. If you don’t set a date range then the current default dates for the negotiator will be used.

Note: the dates must be in the format _yyyy-MM-dd_ to be parsed correctly.

```
agencycloud://appointments?dateFrom=2019-12-25&dateTo=2019-12-26
```

| Parameter | Type | Description                                                                        | Required |
| --------- | ---- | ---------------------------------------------------------------------------------- | -------- |
| dateFrom  | date | Only display appointments scheduled after and including this date (i.e. inclusive) | No       |
| dateTo    | date | Only display appointments scheduled before this date (i.e. exclusive)              | No       |

## Contacts

### Contact Search

Opens advanced search screen in contact mode and runs a search with provided parameters. At least one parameter is required.

```
agencycloud://contacts?name=smith
```

| Parameter     | Type   | Description                                                                                                              | Required |
| ------------- | ------ | ------------------------------------------------------------------------------------------------------------------------ | -------- |
| name          | string | A full or partial name fragment to search for                                                                            | No       |
| address       | string | An address fragment to search for (eg. a postcode)                                                                       | No       |
| communication | string | An email address or phone number to search for                                                                           | No       |
| appId         | string | The GUID of the app to return the code of the selected contact to (if not present then search will not return to an app) | No       |
| appParam      | string | The key to use in the query string when returning the contact primary key to an app (required if appId is set)           | No       |

### Load Contact

Opens the contact edit screen for the contact with specified id

```
agencycloud://contacts/{id}
```

### Load Journal

Opens the journal screen for the specified contact

```
agencycloud://contacts/{id}/journal
```



## Works Orders

### Load Works Orders

Opens the specific works order screen

```
agencycloud://worksorders/{id} 
```

### Search Works Order

Opens the works order search screen and prepopulate any search criteria as specified. As with other search urls it should also support the appId and appParam which will allow the selected item in the search to be sent back to an app.

```
agencycloud://worksorders?address={abc}&supplier={def}&status={ghi}&desc={jkl}
```

## Process

From version 12.122.0 there will also be a resource called **process** which will have two sub processes:

* webpage
* email

### Webpage

This will allow you to launch a webpage in the local default browser.  An example would be:

```
agencycloud://process/webpage?url=https://www.reapit.com
```

This will launch the https://www.reapit.com site in the default browser.  Note: the url parameter _must_ start with http for this to work.

### E-mail

This will allow you to launch the users default e-mail client and send to an address.  An example would be:

```
agencycloud://process/email?address=help@reapit.com
```

This will create a new e-mail in the users default mail client.  It will do this by taking the value of the address parameter, prefixing it with _mailto:_ and then starting a process with that argument.

## AgencyCloud Interaction API

### Overview

Not only can Applications built on the Foundations Platform trigger events in the AgencyCloud CRM system, but installed apps can also be associated with common actions in AgencyCloud to replace the default behaviour.

The most common way that this will manifest itself is by replacing a screen in AgencyCloud with an application. For example if you want to use an App to manage all of your AML and ID checking then you can associate the app with this action in AgencyCloud and every time you click to launch the ID check screen, the associated App will be presented instead.

All apps should be able to be launched from the Installed Apps screen and be ran standalone without the need to be linked to an action. They will just be hosted in the AppMarket and launched in AgencyCloud – for example the Geo Diary application.

### Desktop Types

To be able to associate an application with an action in AgencyCloud the application will need to be given a desktop type. This will be required so that AgencyCloud can be confident of the way the application will behave and that the application is agreeing to accept certain parameters when launched.  These parameters will be available inside the **`window.__REAPIT_MARKETPLACE_GLOBALS__`** javascript object which is used to identify that a page is in _Desktop_ mode.

For example – an AML or ID checking app will need to be able to accept a parameter in the dictionary with a key of **cntCode** which tells the application which contact to show the ID checks for.

There are currently seven supported application desktop types which are based on the most commonly customised parts of AgencyCloud.  This list will be extended as we learn what apps developers are building;

* Property
* Applicant
* ID Check
* Property Marketing Information
* Vendor Marketing Report
* Property Detail Generation (print wizard)
* Applicant Export

From version 12.118.0 the following will also be available:

* Landlord
* Contact
* Company
* Tenancy
* Offer
* Sales Progression
* Chain Management

From version 12.130.1 the following will also be available:

* Outbound - Email&#x20;
* Outbound - Landline
* Outbound - Mobile&#x20;

From version 12.142.0 the following will also be available:

* Match Output&#x20;

From version 12.152.3 the following will also be available:

* Diary

From version 12.153+ the following will also be available:&#x20;

* Pre Tenancy Checks&#x20;
* Works Order

From version 12.156+ the following with also be available:

* Referrals

From version 12.160+ the following with also be available:

* Renewal Negotiation Checks

From version 12.161+ the following with also be available:

* Property Images

From version 12.163+ the following with also be available:

* Property Licensing



## Types

### Property

The type of _Property_ will be given to an application that can be launched for a specific property from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "prpCode": "ABC200123" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                | Required |
| --------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| prpCode   | string | The primary key of the property to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Property is installed then an Apps menu will appear on the Property screen.  Clicking on an app will launch it with the property code.

![Property apps launch point](<../.gitbook/assets/image (12) (1).png>)

### Applicant

The type of _Applicant_ will be given to an application that can be launched for a specific applicant from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "appCode": "ABC200123" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                 | Required |
| --------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| appCode   | string | The primary key of the applicant to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Applicant is installed then an Apps menu will appear on the Applicant screen.  Clicking on an app will launch it with the applicant code.

![Applicant apps launch point](<../.gitbook/assets/image (6).png>)

### Id Check

The type of _ID Check_ will be given to an application that can be used to replace the ID Check screen in AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific contact:

```
{ "cntCode": "ABC20012345" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                             | Required |
| --------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| cntCode   | string | The primary key of the contact to load the ID checks for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

This desktop type will take affect in AgencyCloud when the following button is clicked (this will be seen on various screens, for example contact and applicant).

![Id Check button in AgencyCloud](<../.gitbook/assets/image (5).png>)

### Property Marketing Information

The type of _Property Marketing Information_ can be given to an application that can replace the standard property marketing screen in AgencyCloud. This is the most commonly customised screen in AgencyCloud as it allows clients the opportunity to store bespoke information for their business.  The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "prpCode": "ABC201023" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                                 | Required |
| --------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| prpCode   | string | The primary key of the property to load the marketing information app for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |

An application of this type can be launched from the Marketing button on the property screen in AgencyCloud:

![Property Marketing app launch point ](<../.gitbook/assets/image (3).png>)

### Vendor Marketing Report

The type of _Vendor Marketing Report_ can be given to an application that can produce a customised Vendor Marketing Report. This is also one of the most commonly customised areas of AgencyCloud as different agents have different requirements for how their vendor marketing reports should look.  The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "prpCode": "ABC201023" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                  | Required |
| --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| prpCode   | string | The primary key of the property to generate the report for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |

An application of this type can be launched from the Applicant Interest and Reports screen in AgencyCloud (launched from the Property Journal window):

![Vendor Marketing App launch point](<../.gitbook/assets/image (17).png>)

### Property Detail Generation

The type of _Property Detail Generation_ can be given to an application that can replace the standard details template generation and brochure ordering process. This application could allow selection of a template as defined in the application – selection of pictures to include, what paper size to print the brochures on etc.  The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "prpCode": "ABC201023" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                          | Required |
| --------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| prpCode   | string | The primary key of the property to load generate the brochures for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |

An application of this type can be launched from the Property Details screen in AgencyCloud:

![Details generator app launch point ](<../.gitbook/assets/image (14) (1).png>)

### Applicant Export

The category of _Applicant Export_ would enable an application to be used to export the details of an applicant to a separate system.  The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "appCode": "ABC201023" }
```

<table data-header-hidden><thead><tr><th>Parameter</th><th width="403">Type</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>Parameter</td><td>Type</td><td>Description</td><td>Required</td></tr><tr><td>appCode</td><td>string</td><td>The primary key of the applicant to export (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route).</td><td>Yes</td></tr></tbody></table>

An application of this type would be triggered in two ways from AgencyCloud:

1. Upon first save of the applicant
2. As an option when clicking Print on the applicant screen:

![Applicant Export launch point](<../.gitbook/assets/image (26).png>)

### Landlord

The type of _Landlord_ will be given to an application that can be launched for a specific landlord from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific landlord:

```
{ "lldCode": "ABC200123" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                | Required |
| --------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| lldCode   | string | The primary key of the landlord to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Landlord is installed then an Apps menu will appear on the Landlord screen.  Clicking on an app will launch it with the landlord code.

![Apps button on landlord screen (when lettings accounts is turned off)](<../.gitbook/assets/image (42).png>)

![Apps button on landlord screen (when lettings accounts is turned on) ](<../.gitbook/assets/image (41).png>)

### Contact

The type of _Contact_ will be given to an application that can be launched for a specific contact from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific contact:

```
{ "cntCode": "ABC20012345" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                               | Required |
| --------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| cntCode   | string | The primary key of the contact to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Contact is installed then an Apps menu will appear on the Contact screen.  Clicking on an app will launch it with the contact code.

![Apps button on the contact screen](<../.gitbook/assets/image (29).png>)

### Company

The type of _Company_ will be given to an application that can be launched for a specific company from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific company:

```
{ "cmpCode": "ABC20012345" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                               | Required |
| --------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| cmpCode   | string | The primary key of the company to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Company is installed then an Apps menu will appear on the Company screen.  Clicking on an app will launch it with the company code.

![Apps button on the company screen](<../.gitbook/assets/image (45).png>)

### Tenancy

The type of _Tenancy_ will be given to an application that can be launched for a specific tenancy from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific tenancy:

```
{ "tenCode": "ABC200123" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                               | Required |
| --------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| tenCode   | string | The primary key of the tenancy to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Tenancy is installed then an Apps menu will appear on the Tenancy screen.  Clicking on an app will launch it with the tenancy code.

![Apps button on tenancy screen](<../.gitbook/assets/image (31).png>)

### Offer

The type of _Offer_ will be given to an application that can be launched for a specific offer from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific offer:

```
{ "offerCode": "ABC200123" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                             | Required |
| --------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| offerCode | string | The primary key of the offer to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Offer is installed then an Apps menu will appear on the Offer screen.  Clicking on an app will launch it with the code of the **selected** offer.

![Apps button on the offer screen](<../.gitbook/assets/image (46).png>)

### Sales Progression

The type of _Sales Progression_ will be given to an application that can be launched in place of the standard Sales Progression screen in AgencyCloud.  The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "prpCode": "ABC201023" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                                         | Required |
| --------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| prpCode   | string | The primary key of the property to load the sales progression information app for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |

An application of this type can be launched from the _Sales Progression_ button on the offers screen in AgencyCloud:

![Sales progression button on the offers screen](<../.gitbook/assets/image (44).png>)

### Chain Management

The type of _Chain Management_ will be given to an application that can be launched in place of the standard Chain screen in AgencyCloud.  The globals dictionary will contain the below key when launched by AgencyCloud for a specific property:

```
{ "prpCode": "ABC201023" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                                                        | Required |
| --------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------- |
| prpCode   | string | The primary key of the property to load the chain management information app for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |

An application of this type can be launched from the _Chain_ button on the offers screen in AgencyCloud:

![Chain button on the offers screen](<../.gitbook/assets/image (30).png>)



### Match Output

The category of _Match Output_ would enable an application to be used to export the details of a match either from an applicant to a property or a property to an applicant. The globals dictionary will contain the below key when launched by AgencyCloud for a specific match:

```
'{"NegCode":"RTR","Matches":[{"OutputType":"PrpToAppMatch","SourceCode":"BCK160024","Results":["RPT210019"]}]}'
```

| Match type (PrpToappMatch/AppToPrpMatch)  | Property to applicant or applicant to property |
| ----------------------------------------- | ---------------------------------------------- |
| Property ID(s)                            | Single/Array of property IDs                   |
| Applicant ID(s)                           | Single/Array of applicant IDs                  |
| Negotiator ID - User (NegCode)            | Neg ID of the logged in Negotiator             |
|                                           |                                                |

An app with the integration type 'Match Output' will be visible by selecting 'Print' after running a match:&#x20;

![](../.gitbook/assets/MatchOutput.jpg)



### Diary

The desktop type of _Diary_ can be given to an application that can be launched on an existing appointment in AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific appointment:

{diaryCode: 'OXF2202628'}



```
{ "diaryCode": 'OXF2202628'}
```

| Parameter | Type   | Description                                                                                                                                                                                                          | Required |
| --------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| diaryCode | string | The primary key of the appointment (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |



<figure><img src="../.gitbook/assets/DiaryAPI.png" alt=""><figcaption></figcaption></figure>

### Pre Tenancy Checks

The type of _Pre Tenancy Checks_ will be given to an application that replaces the Pre Tenancy screen from AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a specific tenancy:

```
{ "tenCode": "ABC200123" }
```

| Parameter | Type   | Description                                                                                                                                                                                                                               | Required |
| --------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| tenCode   | string | The primary key of the tenancy to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |

When an app with a type of Pre Tenancy Check is installed, it will be launched when accessing the Pre Tenancy screen (if multiple apps with the same integration type are installed, an option to select will be presented).  Clicking on an app will launch it with the tenancy code.

<figure><img src="../.gitbook/assets/PTenancyCheck.jpg" alt=""><figcaption></figcaption></figure>

### **Works Orders**

The desktop type of _Works Order_ can be given to an application that can be launched from a Works Orders screen in AgencyCloud. When an application has this desktop type, it will replace the native behaviour and will launch when selecting ‘Create’. The globals dictionary will contain the below key when launched by AgencyCloud:&#x20;

```
{ "prpCode": "ABC201023" }
```



<table data-header-hidden><thead><tr><th>Parameter</th><th width="280">Type</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>Parameter</td><td>Type</td><td>Description</td><td>Required</td></tr><tr><td>prpCode</td><td>string</td><td>The primary key of the property to load the Works Order information app for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route).</td><td>Yes</td></tr></tbody></table>





<figure><img src="../.gitbook/assets/WO1.png" alt=""><figcaption></figcaption></figure>

You can also launch the app from an existing works order and the globals dictionary will contain the below key when launched by AgencyCloud:

```
{woCode: 'MKT22000195'}
```



| Parameter | Type   | Description                                                                                                                                                                                                                                                      | Required |
| --------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| woCode    | string | The primary key of the works order to load the Works Order information app for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |



<figure><img src="../.gitbook/assets/WO2.png" alt=""><figcaption></figcaption></figure>

### Referral

The desktop type of _Referral_ can be given to an application that can be launched after a user creates a referral in AgencyCloud. The globals dictionary will contain the below key when launched by AgencyCloud for a referral:

`{refCode: 'MKT220075'}`

&#x20;

| Parameter | Type   | Description                                                                                                                                                                                                                                                       | Required |
| --------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| `refCode` | string | The primary key of the referral to load the referral information within the app (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route). | Yes      |

&#x20;

&#x20;

#### Setup

Referrals/Leads are part of the AgencyCloud configuration and will need to be setup before you can launch your app from the panel (this cannot be setup via Platform).

Configuration can only be accessed by an Admin with the correct permissions or by the agent making a request to our service desk.

#### Step 1 - Installation:

The agent should first install your app from the AppMarket and after installation, restart AgencyCloud

#### Step 2 – Setting up the Referral in AgencyCloud:

Open the ‘Setup Referrals/Leads’ section under configuration:

<figure><img src="../.gitbook/assets/RT01.png" alt=""><figcaption></figcaption></figure>

Either click 'Add' or edit an existing referral and enter the required information and select ‘Marketplace App’, the menu should open to display any apps that have been installed with the desktop type of ‘Referral’:

<figure><img src="../.gitbook/assets/RT02.png" alt=""><figcaption></figcaption></figure>

Once the setup is saved, the new referral option should appear on the chosen screen. For example, on the Applicant screen 'Referral Example':

<figure><img src="../.gitbook/assets/RT03.png" alt=""><figcaption></figcaption></figure>

#### Process

When a user clicks on the  referral, it will prompt them to ‘Create New Referral’:

<figure><img src="../.gitbook/assets/RT04.png" alt=""><figcaption></figcaption></figure>

&#x20;

Once created, the app setup for that referral will automatically launch.

If a user closes the app or wishes to make amendments/relaunch the app, they can simply right click on the referral and select ‘Launch App…’:

<figure><img src="../.gitbook/assets/RT05.png" alt=""><figcaption></figcaption></figure>

### Renewal Negotiation Check

The desktop type of _Renewal Negotiation Check_ can be given to an application that will replace the checks section on a Renewal Negotiation screen in AgencyCloud. The global dictionary will contain the below key when launched by AgencyCloud for a renewal:

```
{ "renewalCode": "ABC200123" }
```

| Parameter   | Type   | Description                                                                                                                                                                                                                               | Required |
| ----------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| renewalCode | string | The primary key of the renewal to load the application for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the desktop type route). | Yes      |



<figure><img src="../.gitbook/assets/RenewalChecks.jpg" alt=""><figcaption><p>'Checks' section on a Renewal Negotiation in AgencyCloud</p></figcaption></figure>

When an app with a type of _Renewal Negotiation Check_ is installed, it will replace the 'checks' on the Renewal Negotiation screen (when heavy weight renewals are enabled). If multiple apps with the same integration type are installed, an option to select will be presented).  Clicking on an app will launch it with the renewal code.



### Property Images

The desktop type of _Property Image_ can be given to an application that can be launched from the 'Apps' menu on the property images screen. The globals dictionary will contain the below key when launched by AgencyCloud:&#x20;

The below key when launched by AgencyCloud:&#x20;

```
{ "prpCode": "ABC201023" }
```



<table data-header-hidden><thead><tr><th>Parameter</th><th width="280">Type</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>Parameter</td><td>Type</td><td>Description</td><td>Required</td></tr><tr><td>prpCode</td><td>string</td><td>The primary key of the property to load the property images app (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route).</td><td>Yes</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/Property Image.jpg" alt=""><figcaption><p>'Apps' option on the Property Images screen in Agency Cloud</p></figcaption></figure>

### **Property Licensing**

The desktop type of _Property Licensing_ can be given to an application that replaces the 'Licensing' button on the property attributes screen. When an application has this desktop type, it will replace the native behaviour and will launch when selecting ‘Licensing’. The globals dictionary will contain the below key when launched by AgencyCloud:&#x20;

```
{ "prpCode": "ABC201023" }
```



<table data-header-hidden><thead><tr><th>Parameter</th><th width="280">Type</th><th>Description</th><th>Required</th></tr></thead><tbody><tr><td>Parameter</td><td>Type</td><td>Description</td><td>Required</td></tr><tr><td>prpCode</td><td>string</td><td>The primary key of the property to load the property licensing app for (note that this won’t be present when the app loads from the AppMarket, but the app needs to be able to accept this parameter when it is launched via the app association route).</td><td>Yes</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/Licensing.jpg" alt=""><figcaption><p>Licensing optin in AgencyCloud</p></figcaption></figure>

