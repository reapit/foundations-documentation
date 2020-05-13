---
description: >-
  Below you will find a listing of the recent changes we have made to our
  Platform API. This includes details of both breaking and non-breaking changes.
  The current version of our APIs is 2020-01-31.
---

# Platform Change Log

## May 2020

#### 2020-05-13

* [\#734](https://github.com/reapit/foundations/issues/734) - Added a new `modified` query string to `GET /properties` to filter properties based on the date they were last modified or created

#### 2020-05-11

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



