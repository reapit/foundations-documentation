---
description: >-
  Below you will find a listing of the recent changes we have made to our
  Platform API. This includes details of both breaking and non-breaking changes.
  The current version of our APIs is 2020-01-31.
---

# Platform change log

## March 2020

#### 2020-03-10

* [\#562](https://github.com/reapit/foundations/issues/562) - Fixed issue that meant the negotiator and office ids associated to applicant resources were sometimes populating incorrectly in the responses returned from `GET /applicants` and `GET /applicants/{id}`

#### 2020-03-09

* [\#563 ](https://github.com/reapit/foundations/issues/563)- Fixed issue that prevented contact source of enquiry from being populated in the payload returned from `GET /contacts` and `GET /contacts/{id}`
* [\#482](https://github.com/reapit/foundations/issues/482) - The response from `GET /applicants` and `GET /applicants/{id}` will now include a link to the offers that the applicant has made
* [\#501](https://github.com/reapit/foundations/issues/501) - It is now possible to request that related information is included with `GET /identityChecks` and `GET /identityChecks/{id}` responses by using the `embed` parameter
* [\#497 ](https://github.com/reapit/foundations/issues/497)-  It is now possible to request that related information is included with `GET /appointments` and `GET /appointments/{id}` responses by using the `embed` parameter
* [\#506](https://github.com/reapit/foundations/issues/506) - It is now possible to request that related information is included with `GET /vendors` and `GET /vendors/{id}` responses by using the `embed` parameter
* [\#551](https://github.com/reapit/foundations/issues/551) - Created additional endpoint to request the details of a specific contacts relationships on the system.
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



