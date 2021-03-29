---
description: >-
  Below you will find a listing of the recent changes we have made to our
  Platform API. This includes details of both breaking and non-breaking changes.
  The current version of our APIs is 2020-01-31.
---

# Platform Change Log

## March 2021

**2021-03-29**

* [\#3495](https://github.com/reapit/foundations/issues/3495) - Added support for the uploading of files over 6MB \(Up to 30MB\) to Property Images and Documents via the use of pre-signed URL's

**2021-03-26**

* [\#986](https://github.com/reapit/foundations/issues/986) / [\#987](https://github.com/reapit/foundations/issues/987) - It is now possible to view mailing and event subscriptions for a specific contact

**2021-03-12**

* [\#3658](https://github.com/reapit/foundations/issues/3658) - Fixed bug where using the `modifiedFrom` and/or `modifiedTo` query string filters was not always returning correct results from `GET /properties`
* [\#3474](https://github.com/reapit/foundations/issues/3474) - Added support for retrieval of archived tenancies using new `fromArchive` query string parameter
* [\#3602](https://github.com/reapit/foundations/issues/3602) - Added new `PATCH /tenancies/{id}` to support the updating of certain tenancy properties
* [\#3559](https://github.com/reapit/foundations/issues/3559) - It is now possible to retrieve and set the profile image for an individual negotiator
* [\#3473](https://github.com/reapit/foundations/issues/3473) - Added support for retrieval of archived appointments using new `fromArchive` query string parameter

**2021-03-10**

* [\#3701](https://github.com/reapit/foundations/issues/3701) - Fixed incorrect link to journal entry documentation in Swagger documentation
* [\#3612](https://github.com/reapit/foundations/issues/3612) - Added `video2Url` and `video2Caption` properties to the property APIs
* [\#3469](https://github.com/reapit/foundations/issues/3469) - Added support for retrieval of archived applicants using new `fromArchive` query string parameter

**2021-03-08**

* [\#3588](https://github.com/reapit/foundations/issues/3588) - `application.install` and `application.uninstall` webhooks will now include the email address of the person who has carried out the action

**2021-03-03**

* [\#3571](https://github.com/reapit/foundations/issues/3571) - Implemented caching to improve load time of Swagger documentation in the Developer Portal

**2021-03-02**

* [\#3468](https://github.com/reapit/foundations/issues/3468) - Added support for retrieval of archived vendors using new `fromArchive` query string parameter
* [\#3566](https://github.com/reapit/foundations/issues/3566) - Resolved issue with trailing spaces in some enumeration options listed in the OpenAPI documentation
* [\#3472](https://github.com/reapit/foundations/issues/3472) - Added support for retrieval of archived properties using new `fromArchive` query string parameter

## February 2021

**2021-02-26**

* [\#3496](https://github.com/reapit/foundations/issues/3496) - Added new `alternateId` property to the model returned from `GET /properties`
* [\#3314](https://github.com/reapit/foundations/issues/3314) - Added new properties to the model returned from `GET /properties` to expose lost instruction information

**2021-02-24**

* [\#2903](https://github.com/reapit/foundations/issues/2903) - Fixed bug where there was a minor risk of a duplicate property image being generated when issuing a request to `POST /propertyImages`

**2021-02-23**

* [\#3466](https://github.com/reapit/foundations/issues/3466) - Added support for the retrieval of archived contacts using new `fromArchive` query string parameter
* [\#3467](https://github.com/reapit/foundations/issues/3467) - Added support for the retrieval of archived companies using new `fromArchive` query string parameter

**2021-02-22**

* [\#3270](https://github.com/reapit/foundations/issues/3270) - Added  `DELETE /metadata/{id}`endpoint to support the deletion of metadata documents
* [\#3346](https://github.com/reapit/foundations/issues/3346) - Updated validation messages to match the outward facing property names

**2021-02-21**

* [\#3401](https://github.com/reapit/foundations/issues/3401) - Fixed issue where some custom configuration items would not be displayed by the `GET /configuration/identityDocumentTypes` endpoint

**2021-02-17**

* [\#3400](https://github.com/reapit/foundations/issues/3400) - Added support for retrieval and updating of property general notes field in the properties API
* [\#3492](https://github.com/reapit/foundations/issues/3492) - Fixed bug where 500 Internal Server Error would be returned if the physical file asset for an entity returned from `GET /documents` was no longer available. `GET /documents/{id}/download` will now return a 404 in this scenario

**2021-02-12**

* [\#3417](https://github.com/reapit/foundations/issues/3417) - It is now possible to filter by the `active` flag when calling `GET /applicants`

**2021-02-11**

* [\#3481](https://github.com/reapit/foundations/issues/3481) - Fixed issue where certain data states would cause a 500 error when calling `GET /tenancies`

**2021-02-08**

* [\#3435](https://github.com/reapit/foundations/issues/3435) - It is now possible to filter by email address when using `GET /negotiators` using the `email` query string parameter

**2021-02-05**

* [\#3433](https://github.com/reapit/foundations/issues/3433) - Fixed issue where `negotiatorId` of 2 characters in length would be rejected by a number of `POST` endpoints

**2021-02-02**

* Fixed issue where image thumbnails were not being generated correctly when calling `POST /propertyImages`

## January 2021

**202**1**-01-22**

* [\#3178](https://github.com/reapit/foundations/issues/3178) - Fixed issue where `PATCH /conveyancing/{id}` would fail with a 400 BadRequest error
* [\#3334](https://github.com/reapit/foundations/issues/3334) - Fixed issue with eTag validation on some requests to `PATCH /documents/{id}`

**2021-01-21**

* [\#3291](https://github.com/reapit/foundations/issues/3291) - Properties API `externalArea` models will now expose the `max` property as 0 instead of null so the representation of what is available in the Agency Cloud UI is more accurate
* [\#3278](https://github.com/reapit/foundations/issues/3278) - Unlisted apps limit increased from 5 to 10 in the Developer Portal
* [\#3287](https://github.com/reapit/foundations/issues/3287) - Appointment APIs now support the new Agency Cloud `virtual` appointment flag

**2021-01-20**

* [\#3318](https://github.com/reapit/foundations/issues/3318) - Fixed bug where `surname` field was not being validated correct when sending payload to `POST /enquiries`
* [\#3189](https://github.com/reapit/foundations/issues/3189) - `GET /enquiries` can now be filtered and sorted by created/modified

**2021-01-06**

* [\#3189](https://github.com/reapit/foundations/issues/3189) - `GET /offices` can now be filtered and sorted by created/modified

**2021-01-05**

* [\#3211](https://github.com/reapit/foundations/issues/3211) - It is now possible to filter by `propertyId` when calling `GET /journalEntries`
* [\#3216](https://github.com/reapit/foundations/issues/3216) - The `officeIds` array return in the `AppointmentModel` will now include the id of the office the primary negotiator associated with the appointment is attached to

## December 2020

**2020-12-16**

* [\#2198](https://github.com/reapit/foundations/issues/2918) - `/documents` APIs will now advertise support for metadata in documentation

**2020-12-15**

* [\#3138 ](https://github.com/reapit/foundations/issues/3138)- Fixed issue where duplicate contacts could be displayed as part of an appointment attendee's contacts collection in certain situations when calling `GET /appointments`

## November 2020

#### 2020-11-06

* [\#52](https://github.com/reapit/foundations/milestone/52) - New endpoints have been created to allow for metadata to be granularly managed outside the context of other endpoints and to allow standalone, custom metadata powered entities to be created. For more information, please [see our documentation](api/api-documentation.md#metadata)

## October 2020

**2020-10-28**

* [\#2902](https://github.com/reapit/foundations/issues/2902) - It is now possible to request that related property, negotiator and/or type information is included with `GET /journalEntries`responses by using the `embed` parameter

**2020-10-08**

* Fixed bug where the `active` query string parameter was not respected when filtering results returned from `GET /landlords`

**2020-10-07**

* [\#2823](https://github.com/reapit/foundations/issues/2823) - The negotiator related to a new journal entry can now be set in the request body to `POST /journalEntries`

**2020-10-06**

* [\#2783](https://github.com/reapit/foundations/issues/2783) - Fixed bug where the `status` query parameter was not respected when filtering results returned from `GET /worksOrders`

**2020-10-01**

* [\#2768](https://github.com/reapit/foundations/issues/2768) - Fixed issue where `properties.created` webhook events would be fired twice if the property was registered via `POST /properties` and the request body contained room information

## September 2020

**2020-09-25**

* [\#2755 ](https://github.com/reapit/foundations/issues/2755)- Fixed issue with `Reapit-Webhook-Signature` header in webhook payloads

## July 2020

**2020-07-29**

* [\#2178](https://github.com/reapit/foundations/issues/2178) - Added support to filter by `officeId` for properties on `GET /properties`

**2020-07-27**

* [\#2175](https://github.com/reapit/foundations/issues/2175) It is now possible to request that related tenancy information is included with `GET /properties` and `GET /properties/{id}` responses by using the `embed` parameter

**2020-07-24**

* [\#1124](https://github.com/reapit/foundations/issues/1124) Added new webhook topics `application.install` and `application.uninstall` to provide notifications when a customer installs/uninstalls an app in the Marketplace. For more information see the [Webhooks documentation](api/webhooks.md#available-topics)

#### 2020-07-21

* Added new `totalPageCount` property to paged responses to indicate the total number of pages available in the response

#### 2020-07-10

* [\#1998](https://github.com/reapit/foundations/issues/1998) - The properties API will now allow for read and write of `selling.disposal` attribute, used to describe the method to be used to sell a property

## June 2020

#### 2020-06-23

* [\#1819](https://github.com/reapit/foundations/issues/1819) - Fixed issue with the way the `marketingMode` parameter was evaluated for `GET /properties` that could cause problems with address searching

#### 2020-06-19

* [\#1780](https://github.com/reapit/foundations/issues/1780) - The response from `GET /offers` and `GET /offers/{id}` will now include granular name information for any contacts that have been associated in the `related` collection
* [\#177](https://github.com/reapit/foundations/issues/1779)9 - The response from `GET /tenancies` and `GET /tenancies/{id}` will now include granular name information for any contacts that have been associated in the `related` collection
* [\#1778](https://github.com/reapit/foundations/issues/1778) - The response from `GET /landlords` and `GET /landlords/{id}` will now include granular name information for any contacts that have been associated in the `related` collection
* [\#177](https://github.com/reapit/foundations/issues/1777)7 - The response from `GET /vendors` and `GET /vendors/{id}` will now include granular name information for any contacts that have been associated in the `related` collection

#### 2020-06-18

* [\#1766](https://github.com/reapit/foundations/issues/1766) - The response from `GET /applicants` and `GET /applicants/{id}` will now include granular name information for any contacts that have been associated in the `related` collection

#### 2020-06-03

* [\#1502](https://github.com/reapit/foundations/issues/1502) - Fixed issue that meant the wrong identifier could be presented in the GET /conveyancing model

## May 2020

#### 2020-05-29

* [\#1205](https://github.com/reapit/foundations/issues/1205) - The response from `GET /offers` and `GET /offers/{id}` will now include a link to the offers associated conveyancing information
* [\#918](https://github.com/reapit/foundations/issues/918) - Tenancy endpoints now support setting and retrieval of [additional metadata fields](https://marketplace.reapit.cloud/developer/api-docs/api/api-documentation#metadata)

#### 2020-05-22

* It is now possible to set up webhooks to emit event information directly to your application. [See our documentation](api/webhooks.md) for more information.

#### 2020-05-13

* [\#734](https://github.com/reapit/foundations/issues/734) - Added a new `modified` query string to `GET /properties` to filter properties based on the date they were last modified or created

#### 2020-05-12

* [\#1209](https://github.com/reapit/foundations/issues/1209) - Ensured that the error response issued from `GET /documents/{id}/download` when `Accept` header is invalid is returned in the standard format
* [\#1208 ](https://github.com/reapit/foundations/issues/1208)- The response from `GET /companies` and `GET /companies/{id}` will now include a link to the companies associated relationships
* [\#1207](https://github.com/reapit/foundations/issues/1207) - The response from `GET /contacts` and `GET /contacts/{id}` will now include a link to the contacts associated relationships

#### 2020-05-11

* [\#1144](https://github.com/reapit/foundations/issues/1144) - Updated interactive API explorer to indicate that `GET /documents/{id}/download` provides content using the `Content-Type` of `application/octet-stream`
* [\#1088](https://github.com/reapit/foundations/issues/1088) - Created new API to request the details of a specific companies relationships on the system at `GET /companies/{id}/relationships`

#### 2020-05-07

* [\#1164](https://github.com/reapit/foundations/issues/1164) - The listing of contact roles at `GET /contacts/{id}/relationships` will now include offer roles

## April 2020

#### 2020-04-15

* [\#835 ](https://github.com/reapit/foundations/issues/835)- Ensured that `GET /appointments` handles an unexpected data condition more gracefully

#### 2020-04-08

* [\#846](https://github.com/reapit/foundations/issues/846) - Updated the documentation for the appointments `recurrence.type` attribute to include its acceptable values listing
* [\#804](https://github.com/reapit/foundations/issues/804) - It is now possible to request that related appointment information is included with `GET /properties` and `GET /properties/{id}` responses by using the `embed` parameter
* [\#843](https://github.com/reapit/foundations/issues/843) - It is now possible to request that related appointment information is included with `GET /tenancies` and `GET /tenancies/{id}` responses by using the `embed` parameter
* [\#805](https://github.com/reapit/foundations/issues/805) - It is now possible to request that related appointment information is included with `GET /applicants` and `GET /applicants/{id}` responses by using the `embed` parameter
* [\#806](https://github.com/reapit/foundations/issues/806) - It is now possible to request that related appointment information is included with `GET /landlords` and `GET /landlords/{id}` responses by using the `embed` parameter
* [\#801](https://github.com/reapit/foundations/issues/801) - The response from `GET /properties` and `GET /properties/{id}` will now include a link to the properties associated appointments
* [\#803](https://github.com/reapit/foundations/issues/803) - The response from `GET /landlords` and `GET /landlords/{id}` will now include a link to the landlords associated appointments
* [\#802](https://github.com/reapit/foundations/issues/802) - The response from `GET /applicants` and `GET /applicants/{id}` will now include a link to the applicants associated appointments
* [\#722](https://github.com/reapit/foundations/issues/722) - The response from `GET /tenancies` and `GET /tenancies/{id}` will now include a link to the tenancies associated appointments
* [\#735 ](https://github.com/reapit/foundations/issues/735)- Ensured that the appropriate error message and status code is returned when an incorrectly formatted date only attribute is provided in a `POST` or `PATCH` payload
* [\#799](https://github.com/reapit/foundations/issues/799) - The `marketingConsent` and `identityCheck` parameters for `GET /contacts` are now presented as enumerations

#### 2020-04-07

* [\#787](https://github.com/reapit/foundations/issues/787) - The response from `GET /appointments` and `GET /appointments/{id}` will now optionally include information about the appointments recurrence pattern
* [\#786](https://github.com/reapit/foundations/issues/786) - The `start` and `end` parameters are no longer required when interacting with `GET /appointments`

#### 2020-04-03

* [\#760](https://github.com/reapit/foundations/issues/760) - It is now possible to request that related property information is included with `GET /vendors` and `GET /vendors/{id}` responses by using the `embed` parameter

#### 2020-04-01

* [\#765](https://github.com/reapit/foundations/issues/765) - Added support to filter by agent role for lettings properties on `GET /properties` 
* [\#760](https://github.com/reapit/foundations/issues/760) - The payload from `GET /vendors` and `GET /vendors/{id}` will now include the `propertyId` of the property the vendor is associated with as well as an entry to that property in the `_links` collection

## March 2020

#### 2020-03-31

* [\#774](https://github.com/reapit/foundations/issues/774) - Fixed issue with the `id` field in the example property data being presented from the interactive API explorer
* [\#767](https://github.com/reapit/foundations/issues/767) - Corrected data condition that meant that related contact information could sometimes be incorrectly presented as a company type from the vendors API
* [\#770](https://github.com/reapit/foundations/issues/770) - Corrected data condition that meant that related contact information could sometimes be incorrectly presented as a company type from the applicants API
* [\#771](https://github.com/reapit/foundations/issues/771) - Corrected data condition that meant that related contact information could sometimes be incorrectly presented as a company type from the landlords API
* [\#772](https://github.com/reapit/foundations/issues/772) - Corrected data condition that meant that related contact information could sometimes be incorrectly presented as a company type from the offers API
* [\#77](https://github.com/reapit/foundations/issues/773)3 - Corrected data condition that meant that related contact information could sometimes be incorrectly presented as a company type from the tenancies API

#### 2020-03-27

* [\#733](https://github.com/reapit/foundations/issues/733) - It is now possible to search for appointments associated to related entities by using the `attendeeId` and `attendeeType` parameters at `GET /appointments` 

#### 2020-03-26

* [\#721](https://github.com/reapit/foundations/issues/721) - Corrected issue that meant that dates passed in an incorrect format as a payload to `POST` and `PATCH` operations would result in a `500` status code rather than a `422`
* [\#692](https://github.com/reapit/foundations/issues/692) - Created new API to allow an existing tenancy check to be soft deleted at `DELETE /tenancies/{id}/checks/{checkId}`
* [\#304](https://github.com/reapit/foundations/issues/304) - Created new API to allow an existing tenancy check to be updated at `PATCH /tenancies/{id}/checks/{checkId}`
* [\#303](https://github.com/reapit/foundations/issues/303) - Created new API to allow a new tenancy check to be created for a specific tenancy `POST /tenancies/{id}/checks`
* [\#302](https://github.com/reapit/foundations/issues/302) - Created new API to retrieve information about a specific tenancy check associated to a tenancy at `GET /tenancies/{id}/checks/{checkId}`
* [\#301](https://github.com/reapit/foundations/issues/301) - Created new API to provide a paged listing of pre and post tenancy checks associated to a tenancy at `GET /tenancies/{id}/checks`
* [\#299](https://github.com/reapit/foundations/issues/299) - Created new API to allow a new tenancy to be created in an arranging status at `POST /tenancies`

#### 2020-03-24

* [\#689](https://github.com/reapit/foundations/issues/689) -  Added `selling.exchanged` and `selling.completed` attributes to the payloads for `GET`, `POST`, and `PATCH` of property information

#### 2020-03-23

* [\#665](https://github.com/reapit/foundations/issues/665) - Added `letting.furnishing` attribute to the payloads for `GET`, `POST`, and `PATCH` of property information

#### 2020-03-20

* [\#668](https://github.com/reapit/foundations/issues/668) - The response from `GET /landlords` and `GET /landlords/{id}` will now include a link to the landlords associated properties
* [\#666](https://github.com/reapit/foundations/issues/666) - Added `videoUrl` and `videoCaption` attributes to the payloads for `GET`, `POST`, and `PATCH` of property information.
* [\#669](https://github.com/reapit/foundations/issues/669) - It is now possible to request that related property information is included with `GET /landlords` and `GET /landlords/{id}` responses by using the `embed` parameter

#### 2020-03-19

* [\#305](https://github.com/reapit/foundations/issues/305) - Created new API to provide a paged, filterable listing of journal entries at `GET /journalEntries`. Journal entries are timestamped events that are associated to other entities to indicate that an event has happened, such as a property price change.
* [\#306](https://github.com/reapit/foundations/issues/306) - Created new API to allow a new journal entry to be created at `POST /journalEntries`
* [\#463](https://github.com/reapit/foundations/issues/463) - Created new API to provide a paged, filterable listing of enquiries at `GET /enquiries`. Enquiriy details are usually captured directly in a website and represents interest from a prospective applicant about one or more properties, or interest from a prospective landlord/vendor about having a property valuation.
* [\#464](https://github.com/reapit/foundations/issues/464) - Created new API to retrieve information about a specific enquiry at `GET /enquiries/{id}`
* [\#465](https://github.com/reapit/foundations/issues/465) - Created new API to allow creation of a new enquiry at `POST /enquiries`
* [\#610 ](https://github.com/reapit/foundations/issues/610)-  It is now possible to filter contacts presented by `GET /contacts` by using the `email` parameter
* [\#661](https://github.com/reapit/foundations/issues/661) - Fixed issue that meant a successful `POST /worksOrder/{id}/items` request would present an incorrect URL in it's location response header
* [\#540](https://github.com/reapit/foundations/issues/540) - It is now possible to query the `GET /applicants` resource with a specific rent collection frequency
* [\#539](https://github.com/reapit/foundations/issues/539) - It is now possible to query the `GET /properties` resource with a specific rent collection frequency

#### 2020-03-17

* [\#542](https://github.com/reapit/foundations/issues/542) - Improved the documentation of the parameters required for `GET /propertyPictures/{id}`

#### 2020-03-16

* [\#395](https://github.com/reapit/foundations/issues/395) - The interactive API explorer will now allow the `If-Match` header to issued from within the user interface. This provides the ability to test `PATCH` endpoints using this tool. Please note that you will still need to retrieve and provide the `If-Match` header from the resource you want to update.

#### 2020-03-12

* [\#517](https://github.com/reapit/foundations/issues/517) - The `GET /properties` and `GET /applicants` APIs no longer requires the `departmentId` query string to be provided when using the `type`, `style`, `situation`, `age`, `parking` and `locality` parameters

#### 2020-03-11

* [\#576](https://github.com/reapit/foundations/issues/576) - Corrected the format of the documents link provided by the applicants, contacts, landlords, properties, tenancies and works orders read APIs
* [\#595](https://github.com/reapit/foundations/issues/595) - Fixed issue when using embed functionality fetch a sales properties associated vendor
* [\#593](https://github.com/reapit/foundations/issues/593) - It is now possible to additionally request that related landlord information is included with `GET /properties` and `GET /properties/{id}` responses by using the `embed` parameter
* [\#505](https://github.com/reapit/foundations/issues/505) - It is now possible to request that related information is included with `GET /tasks` and `GET /tasks/{id}` responses by using the `embed` parameter

#### 2020-03-10

* [\#584](https://github.com/reapit/foundations/issues/584) - Created new API to allow an existing item / job associated to a works order to be soft deleted at `DELETE /worksOrders/{id}/items/{itemId}`
* [\#410](https://github.com/reapit/foundations/issues/410) - Created new API to allow an existing item / job associated to a works order to be updated at `PATCH /worksOrders/{id}/items/{itemId}`
* [\#409](https://github.com/reapit/foundations/issues/409) - Created new API to allow a new item / job to be associated to be created against a works order at `POST /worksOrders/{id}/items`
* [\#408](https://github.com/reapit/foundations/issues/408) - Created new API to retrieve information about a specific item / job associated to a works order at `GET /worksOrders/{id}/items/{itemId}`
* [\#407](https://github.com/reapit/foundations/issues/407) - Created new API to retrieve information about the item / jobs associated to a specific works order at `GET /worksOrders/{id}/items`
* \#[406](https://github.com/reapit/foundations/issues/406) - Created new API to allow an existing works order to be updated at `PATCH /worksOrders`
* [\#405](https://github.com/reapit/foundations/issues/405) - Created new API to allow creation of a new works order at `POST /worksOrders`
* [\#404](https://github.com/reapit/foundations/issues/404) - Created new API to retrieve information about a specific works order at `GET /worksOrders/{id}`
* [\#403](https://github.com/reapit/foundations/issues/403) - Created new API to retrieve a paged, filterable listing of works orders at `GET /worksOrders`
* [\#583](https://github.com/reapit/foundations/issues/583) - Created new API to retrieve information about the contact / company tenant relationships associated with a specific tenancy at `GET /tenancies/{id}/relationships`
* [\#298](https://github.com/reapit/foundations/issues/298) - Created new API to retrieve information about a specific tenancy at `GET /tenancies/{id}`
* [\#297](https://github.com/reapit/foundations/issues/297) - Created new API to retrieve a paged, filterable listing of tenancies at `GET /tenancies` 
* [\#503](https://github.com/reapit/foundations/issues/503) -  It is now possible to request that related information is included with `GET /properties` and `GET /properties/{id}` responses by using the `embed` parameter
* [\#530](https://github.com/reapit/foundations/issues/530) - Created new API for retrieval of the available tenancy types that have been configured in a clients environment from `GET /configuration/tenancyTypes` and `GET /configuration/tenancyTypes/{id}`
* [\#496](https://github.com/reapit/foundations/issues/496) - It is now possible to request that related information is included with `GET /applicants` and `GET /applicants/{id}` responses by using the `embed` parameter
* [\#498](https://github.com/reapit/foundations/issues/498) - It is now possible to request that related information is included with `GET /companies` and `GET /companies/{id}` responses by using the `embed` parameter
* [\#562](https://github.com/reapit/foundations/issues/562) - Fixed issue that meant the negotiator and office ids associated to applicant resources were sometimes populating incorrectly in the responses returned from `GET /applicants` and `GET /applicants/{id}`

#### 2020-03-09

* [\#563 ](https://github.com/reapit/foundations/issues/563)- Fixed issue that prevented contact source of enquiry from being populated in the payload returned from `GET /contacts` and `GET /contacts/{id}`
* [\#482](https://github.com/reapit/foundations/issues/482) - The response from `GET /applicants` and `GET /applicants/{id}` will now include a link to the offers that the applicant has made
* [\#501](https://github.com/reapit/foundations/issues/501) - It is now possible to request that related information is included with `GET /identityChecks` and `GET /identityChecks/{id}` responses by using the `embed` parameter
* [\#497 ](https://github.com/reapit/foundations/issues/497)-  It is now possible to request that related information is included with `GET /appointments` and `GET /appointments/{id}` responses by using the `embed` parameter
* [\#506](https://github.com/reapit/foundations/issues/506) - It is now possible to request that related information is included with `GET /vendors` and `GET /vendors/{id}` responses by using the `embed` parameter
* [\#551](https://github.com/reapit/foundations/issues/551) - Created new API to request the details of a specific contacts relationships on the system at `GET /contacts/{id}/relationships`
* [\#556](https://github.com/reapit/foundations/issues/556) - Fixed issue that prevented vendor source of enquiry from being populated in the payload returned from `GET /vendors` and `GET /vendors/{id}`

#### 2020-03-06

* [\#507](https://github.com/reapit/foundations/issues/507) - It is now possible to request that related document, source,  office and solicitor information is included with `GET /landlords` and `GET /landlords/{id}` responses by using the `embed` parameter
* [\#502](https://github.com/reapit/foundations/issues/502) - It is now possible to request that related property, applicant and negotiator information is included with `GET /offers` and `GET /offers/{id}` responses by using the `embed` parameter

#### 2020-03-05

* [\#500](https://github.com/reapit/foundations/issues/500) - It is now possible to request that related document type information is included with `GET /documents` and `GET /documents/{id}` responses by using the `embed` parameter

#### 2020-03-03

* [\#504](https://github.com/reapit/foundations/issues/504) - It is now possible to request that related property information is included with `GET /propertyImages` and `GET /propertyImages/{id}` responses by using the `embed` parameter 

#### 2020-03-02

* [\#495](https://github.com/reapit/foundations/issues/495) - It is now possible to request that related negotiator information is included with `GET /offices` and `GET /offices/{id}` responses by using the `embed` parameter 
* [\#483](https://github.com/reapit/foundations/issues/483) - It is now possible to request that related office information is included with `GET /negotiators` and `GET /negotiators/{id}` responses by using the `embed` parameter

## February 2020

#### 2020-02-24

* [\#327](https://github.com/reapit/foundations/issues/327) - Added endpoints to present the available types of journal entry that have been configured a customer environment

#### 2020-02-20

* [\#383](https://github.com/reapit/foundations/issues/383) - Fixed issue where requests missing the required authorization header would return malformed error response



