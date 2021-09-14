---
description: Getting the most out of our Platform
---

# Usage Guidelines

To ensure your application is a good tenant and provides the best experience to our customers, please adhere to the following usage and architectural guidelines when interacting with our platform

## Rate limits

We apply rate limits on the API calls an application can make within a given time period. If this limit is exceeded, your app will be throttled, and API requests will fail with a 429 Too Many Requests response. 

* 20 requests can be sent per second
* 5 maximum concurrent requests at any time per customer 
* 250,000 maximum requests per day 

To best adhere to these limits, we recommend that your application maintains no more than 5 API interaction threads and awaits completion of previous requests before submitting new ones.

## Appropriate usage

### Our REST APIs are intended for:

* Retrieval of data in real-time as and when your application requires it
* Storage of data as a transactional, operational data store for your application 

### Our REST APIs should NOT be used for:

* Bulk extraction of data into third party applications, databases, or data warehouses to support business intelligence \(BI\), data mining, and other decision support applications 
* Automated or scheduled routines to acquire data without a requirement to immediately process it for your applications use case \(this does not include webhooks\) 
* Load or volume testing of your application using sandbox or customer data 

Applications that do not use our APIs appropriately will be removed from the AppMarket.

## Being a responsible tenant

### Creating entities 

You should perform a uniqueness check before adding a contact or contact centric entity \(applicant, landlord, etc\) to avoid data duplication. 

Where possible, email address is usually the best way of finding a pre-existing entity. We understand that results may vary depending on data input, but our customers would appreciate your app taking this step.

### Updating entities

Our customers data is accessed by multiple different applications concurrently. We have built mechanisms to protect data integrity during update operations

To minimise the footprint of your application, where update operations use the `PATCH` verb, only include the fields that your application wishes to change in the payload. 

From time to time, you may receive a `412` status code implying that an update has been attempted using a stale version of the entity. Your application should handle this situation replaying your change set over the top of a refreshed version of the entity and re-submitting your `PATCH` request.

