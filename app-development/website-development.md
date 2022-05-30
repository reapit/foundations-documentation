---
description: A guide to assist website developers when working with the Foundation API
---

# Website Development

#### Quick Start

To get a property feed up and running within a couple of minutes, we suggest you first watch [this short video](https://www.youtube.com/watch?v=EJWB5u1ja\_U) and visit our [code examples repo](https://github.com/reapit/foundations-code-examples) with boilerplate examples in Node, PHP and .NET.&#x20;

It is important to note though, these guides are intended to get you up and running as quickly as possible. You should optimise your implementation to minimise API consumption charges and to give the best UX for your customers.

{% hint style="info" %}
Fetching Properties from the API for each page render is not an efficient way of building a website on Foundations and can result in unnecessary API consumption charges
{% endhint %}

#### Suggested Architecture

In the code example, we fetch a list of properties on the fly. This is fine if you need the data to be the latest in our DB at the exact moment of execution however, practically for serving a website, it is expensive in terms of processing on the server, http round trips and financial cost by API calls.

So how do I build on the website feed example?

The simplest reasonable design pattern is as follows;

**1. Seed your application**

Fetch all properties and embedded property images in a paged response, and commit to a database of your choosing. The query will be paginated at a maximum of 100 so you will need to do this step in a few requests, depending on your client.

The following query will fetch all properties where;

* The selling status is `forSale` - you can specify other statuses as you wish eg `underOffer`
* The letting status is `toLet` and `tenancyCurrent` - as above, you can specify additional statuses
* The customer has specified `internetAdvertising` is true
* The page size is 100, and the page number is 1 - you will need to increment the page number until no more properties match your query
* Embed property images. This will return all property images associated to each property. You should store these in a separate location in your database.

```ts
'https://platform.reapit.cloud/properties?sellingStatus=forSale&lettingStatus=toLet&lettingStatus=tenancyCurrent&internetAdvertising=true&embed=images&pageSize=100&pageNumber=1'
```

When you have seeded your DB, you can use this data to serve your website, removing the need to make a round trip for the properties from our APIs each time, thus keeping your costs to a minimum.

**2. On a schedule, fetch the properties that change**

When you have your initial seed, you will need to update your data with any new or changed properties. This should be done with a scheduled job that queries both the properties and property images that change or are created, matching your filters.

The following query will fetch the properties where;

* The selling status, letting status, internet advertising and paging are as per the seed at stage 1
* Images **are not** embedded in the property as it would fetch all images regardless of whether they change or not
* The modified from date covers the last hour. This assumes that you will run your scheduled job every hour - you can adjust the timeframe based on how up to date you need your data to be however, more frequent fetching will result in greater cost.

```ts
'https://platform.reapit.cloud/properties?sellingStatus=forSale&lettingStatus=toLett&lettingStatus=tenancyCurrent&internetAdvertising=true&pageSize=100&pageNumber=1&modifiedFrom=2022-05-26T10:38:06.581Z'
```

The following query will fetch the property images where;

* The paging is as per the seed at stage 1
* The modified date from matches the last hour as per properties
* The `propertyId` values (represented as foo, bar & baz), are the ids of the properties in your DB. You should break the query into batches of 100 propertyIds at a time to avoid timeouts and use paging to return all images changed.

```ts
'https://platform.reapit.cloud/propertyImages?propertyId=foo&propertyId=bar&propertyId=baz&pageSize=100&pageNumber=1&modifiedFrom=2022-05-26T10:38:06.581Z'
```

In both cases, when you have received your updated properties, you should update the corresponding records in your database.

**3. Housekeeping**

Each day (or on a schedule of your choosing), we would recommend checking that your property data has not gone stale. This can be done by fetching each property by id in batches of 100 using the below query where the ids of the properties in your database are represented by foo, bar and baz.

```ts
'https://platform.reapit.cloud/properties?id=foo&id=bar&id=baz'
```

On fetching of this request, you should validate that the returned data is still valid i.e. it matches your `forSale`, `toLet` filters and so on. Records that are no longer valid should be remove from your database.

#### Estimating Charges

You will be billed monthly for using the foundations API on a consumption model, per API call. The cost per call is on a sliding scale, getting cheaper the more calls you make. [see here](https://foundations-documentation.reapit.cloud/developer-terms-and-conditions#schedule-2-fees) for details of these changes.

Consumption may vary significantly from customer to customer, depending on how they use Reapit Software however, we have attempted to give you an illustrative example, based on real world numbers from an SME Agent, with 8 offices.

{% hint style="warning" %}
**Actual costs will vary from customer to customer based on your product and implementation decisions**
{% endhint %}

Assuming you implement the architecture model above, the cost calculation will approximate as below;

**Month 1 seed calls**

```
p = initial seed of live properties for agent = 700
i = average number of images per property = 15
n = number of paged items per API call = 100

Calculation: ((p / n) + (p * i)) / n

Initial seed calls: (700 / 100) + ((700 * 15) / 100 = 112 API Calls
```

**Rolling monthly calls**

```
p = average number of properties in database = 700
i = average number of images changed per hour = 100 (30 actual, but anything up to 100 will be charged as 1 call if paging set to 100)
c = average number of properties changed per hour = 100 (30 actual, but anything up to 100 will be charged as 1 call if paging set to 100)
n = number of paged items per API call = 100
d = number of days in a month running scheduled job = 31
h = hours in day running scheduled job = 24


Calculation Scheduled Calls Per Month: ((c / n) + ((p / n) * (i / n)) * h ) * d
Calculation Monthly Housekeeping Calls: (p / n) * d

Scheduled Calls Per Month: ((100 / 100) + ((700 / 100) * (100 / 100)) * 24) * 31 = 5952 API Calls
Monthly Housekeeping Calls: (700 / 100) * 31 = 217 API Calls

Total Rolling Monthly Calls: 6169 API Calls
```

**Costs**

As per above, API calls are charged on a sliding scale and get cheaper the more calls you make.

Based on this example, basis 2 endpoints (properties and property images), you would be charged as follows:

```
1000 calls @ £0.01 = £10
1500 calls @ £0.008 = £12
2500 calls @ £0.006 = £15
1169 calls @ £0.005 = £5.85

Ongoing Total Calls: £42.85

Initial Seed Month 1: 112 calls @ 0.005 = £0.56
```

**Managing Costs**

As previously stated, we based these numbers on a real world example of an SME agent with 8 offices and around 700 properties on their website. Your use case may differ significantly and adjusting the variables will effect your calls and therefore costs significantly.

Before starting work on a website project, we urge developers to consider the ongoing costs incurred and how you can optimise your code to minimise these costs.

For example, we have assumed updating the website every hour, 24 hours a day, 7 days a week. You can halve you API calls by only updating 7am - 7pm during working hours, and further reduce them by not updating on a Sunday.

Perhaps you don't need the site to update every hour and every two hours is adequate. In this case, simply adjust your scheduled job and the date time range of the modifiedFrom filter.

Maybe you don't need 700 properties on your site, in this case, you can combine API filters or limit the number set for internet marketing inside AgencyCloud, with a corresponding impact on calls and cost.

Conversely, perhaps you need updates every 10 minutes, 24-7. In this case, we would urge you to consider if the overhead is represents value for money given the increase in incurred charges.
