---
description: >-
  This section provides further information on the concepts and terminology
  referenced by the Reapit Foundations Platform and the endpoints we provide
---

# Platform Glossary

### Applicant

Applicants represent the [property](./#property) buying or renting interests of one or more [contacts](./#contact) or [companies](./#company). This includes requirements such as the number of rooms, maximum budget and the geographical areas that the applicant is interested in.&#x20;

### Area

Areas represent a specific geographical location that an [applicant ](./#applicant)is interested in buying/renting within. Areas are comprised of either polygon coordinates or a listing of postcodes. Areas are hierarchical and a single area can alternatively include a list of other areas.

### Appointment

Appointments represent calendar engagements used by [negotiators](./#negotiator) to schedule meetings or arrange events, such as [property](./#property) viewings and valuations. Appointments can be set to recur by including recurrence information and can be scheduled to appear in multiple [negotiators](./#negotiator)’ calendars.

### Company

Companies represent a business organisation that the agent ([customer](./#customer)) has a relationship with. Companies can be assigned a type which relates to the various roles they are able to fulfill such as solicitor or supplier, as well as being able to be involved in their own [property](./#property) transactions.

### Configuration

Configuration represents the customisation options relevant for a customers data set, as some data can differ depending on the configuration of the customer. For example, an agent may want to add to their list of [vendor](./#vendor) selling reasons so that it can be set against a particular [vendors ](./#vendor)`sellingReasonId`

We present lists like this as RESTful endpoints and document where a field references a configurable lists id. We also include links/embed options where appropriate to simplify consumption.

### Contact

Contacts represent the details of a person that the agent has a relationship with. Contact details are captured and managed centrally so that a single contact can fulfill multiple [vendor](./#vendor), [landlord](./#landlord), [applicant ](./#applicant)and [tenancy](./#tenancy) roles at the same time.

### Conveyancing

Conveyancing represents the process of progressing an accepted [offer ](./#offer)to the completion of the sale of a property.&#x20;

Submitting new offers and transitioning them to an accepted status is done using the Offers API. The Conveyancing API is responsible for transitioning that existing, accepted offer into a completed property sale.&#x20;

Our Conveyancing APIs also allow a chain to be managed, providing a means of linking dependant offers together. It's possible to link to offers added to other properties that the customer has instructed, as well as those that are external and instructed to another agent.

### Customer

Customers represent estate agents who use Reapit software. We do not provide an API to obtain details of our customers, instead, their details will be known to you at the point that they install your AppMarket application.&#x20;

### Department

Departments represent a set of descriptive attributes used to describe a [property](./#property). Departments are assigned to both [properties](./#property) and [applicants ](./#applicant)and are used to define which attributes can be used to describe a [property ](./#property)or an [applicant](./#applicant) property requirement.

A Department is most commonly used to ring fence groups of [properties](./#property) and [applicants](./#applicant), particularly when it comes to matching (the process of finding properties that meet specific applicant requirements and vice versa). Typically, customers dealing with only residential sales and lettings will have a single department as there is no real need to separate any of the data, however an example of where multiple departments might be configured would be a customer who deals with both residential and commercial property transactions. In this scenario, a separate Department would normally be setup to separate the two disparate sets of data, as it would be undesirable for residential applicants to be sent details of commercial properties.

#### Interpreting Department Data <a href="#interpreting-department-data" id="interpreting-department-data"></a>

Departments are completely customisable for each agent and subsequently it can be difficult to understand how to interpret this data as it comes out of the various APIs that expose it. As the APIs are standardised across all our customers, Department data has also been standardised where possible using a mapping mechanism to map the customisable values from our CRM into standard values in the API. Any options that do not have a corresponding mapping and are selected on a [Property ](./#property)or [Applicant ](./#applicant)entity will be included in the `unmappedAttributes` and `unmappedRequirements` collections in their respective APIs. Additionally, the _Special_ attributes column in the CRM is mapped explicitly.&#x20;

The tabbed content below provides the latest version of the mappings

{% tabs %}
{% tab title="Type" %}
The following table shows the values exposed in the `type` collection returned by the [Applicant](./#applicant), [Property ](./#property)and [Department ](./#department)APIs and their corresponding mappings back to the AgencyCloud CRM.



| Platform Value         | AgencyCloud Mapping                                                      |
| ---------------------- | ------------------------------------------------------------------------ |
| bungalow               | Bungalow                                                                 |
| commercial             | Commercial                                                               |
| cottage                | Cottage                                                                  |
| developmentOpportunity | Development Opportunity                                                  |
| developmentPlot        | Development Plot, Single Plot, Plot, Building Plot                       |
| estate                 | Estate, Farm/Estate, Residential Farm/Estate, Country Estate             |
| farm                   | Farm                                                                     |
| flatApartment          | Flat/Apartment, Flat / Apartment, Flat, Apartment, Unit/Apartment, Flats |
| garage                 | Garage, Garage Lockup, Lockup, Garage Only                               |
| hotel                  | Hotel, Hotels                                                            |
| house                  | House, House/Villa                                                       |
| industrial             | Industrial, Industrial/Storage                                           |
| land                   | Land                                                                     |
| leisure                | Leisure, Leisure Facility                                                |
| maisonette             | Maisonette                                                               |
| mixedUse               | Mixed Use, Mixed                                                         |
| office                 | Office, Offices                                                          |
| publicHouse            | Public House, Pub                                                        |
| retail                 | Retail                                                                   |
| shop                   | Shop                                                                     |
| smallHolding           | Small Holding                                                            |
| studio                 | Studio, Studio Flat                                                      |
| townhouse              | Townhouse, Town House                                                    |
| villa                  | Villa                                                                    |
| warehouse              | Warehouse, Warehouse/Distribution                                        |
{% endtab %}

{% tab title="Style" %}
The following table shows the values exposed in the `style` collection returned by the [Applicant](./#applicant), [Property ](./#property)and [Department ](./#department)APIs and their corresponding mappings back to the AgencyCloud CRM.



| Platform Value     | AgencyCloud Mapping                                            |
| ------------------ | -------------------------------------------------------------- |
| basement           | Basement                                                       |
| bungalow           | Bungalow                                                       |
| detached           | Detached                                                       |
| duplex             | Duplex                                                         |
| endTerrace         | End of Terrace                                                 |
| firstFloor         | First Floor                                                    |
| groundFloor        | Ground Floor                                                   |
| linkDetached       | Link Detached, Link-Detached                                   |
| lowerGroundFloor   | Lower Ground Floor, Lower Ground                               |
| mews               | Mews                                                           |
| penthouse          | Penthouse                                                      |
| semiDetached       | Semi Detached, Semi-Detached                                   |
| steading           | Steading                                                       |
| studio             | Studio, Studio Flat                                            |
| terraced           | Terraced, Terrace                                              |
| upperFloor         | Upper Floor, Upper Floor without Lift, Upper Floor w/out Lift  |
| upperFloorWithLift | Upper Floor with Lift, Upper Floor w/Lift, Upper Flr with Lift |
{% endtab %}

{% tab title="Situation" %}
The following table shows the values exposed in the `situation` collection returned by the [Applicant](./#applicant), [Property ](./#property)and [Department ](./#department)APIs and their corresponding mappings back to the AgencyCloud CRM.



| Platform Value | AgencyCloud Mapping                         |
| -------------- | ------------------------------------------- |
| balcony        | Balcony                                     |
| communalGarden | Communal Garden                             |
| conservatory   | Conservatory                                |
| garden         | Garden                                      |
| julietBalcony  | Juliette Balcony                            |
| land           | Land/Paddock, Land / Paddock, Paddock Land  |
| outsideSpace   | Outside Space                               |
| patio          | Patio                                       |
| roofTerrace    | Roof Terrace, Terrace, Roof Terrace/Terrace |
{% endtab %}

{% tab title="Locality" %}
The following table shows the values exposed in the `locality` collection returned by the [Applicant](./#applicant), [Property ](./#property)and [Department ](./#department)APIs and their corresponding mappings back to the AgencyCloud CRM.



| Platform Value | AgencyCloud Mapping                                         |
| -------------- | ----------------------------------------------------------- |
| rural          | Rural                                                       |
| townCity       | Town/City, Town / City, Town, Town Centre, Town/City Centre |
| village        | Village                                                     |
{% endtab %}

{% tab title="Parking" %}
The following table shows the values exposed in the `parking` collection returned by the [Applicant](./#applicant), [Property ](./#property)and [Department ](./#department)APIs and their corresponding mappings back to the AgencyCloud CRM.



| Platform Value | AgencyCloud Mapping                                                                                                                                       |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| carport        | Carport, Car Port                                                                                                                                         |
| doubleGarage   | Double Garage                                                                                                                                             |
| garage         | Garage                                                                                                                                                    |
| offStreet      | Off Street Parking, Off Road Parking, Driveway, Off Street                                                                                                |
| residents      | Residents Parking, Resident Parking, Parking, Allocated Parking, Permit Parking, Garage/Parking Space, Allocated Parking Space, Allocated/Private Parking |
| secure         | Secure Parking, Gated Parking                                                                                                                             |
| tripleGarage   | Triple Garage                                                                                                                                             |
| underground    | Underground, Underground Parking, Secure Underground Parking                                                                                              |
{% endtab %}

{% tab title="Age" %}
The following table shows the values exposed in the `age` collection returned by the [Applicant](./#applicant), [Property ](./#property)and [Department ](./#department)APIs and their corresponding mappings back to the AgencyCloud CRM.



| Platform Value | AgencyCloud Mapping                                                                                           |
| -------------- | ------------------------------------------------------------------------------------------------------------- |
| modern         | Modern, Post War, Post-war, Modern (Post 1945), Modern (1920+)                                                |
| new            | New, New Build, New Homes, New Home, New (Off Plan), Newly Built, New Property, New Development, New Property |
| period         | Period, Pre-war, Period (to 1714), Period (Pre 1945), Period (Pre-1920)                                       |
{% endtab %}
{% endtabs %}

### Document

Documents represent the details of a file asset that has been added to our platform. Documents can be assigned a type to indicate its purpose (eg. a brochure) and associated to an associated entity (eg. a [property](./#property)).

When using the `GET /documents/{id}/download` endpoint to download the physical file asset, you must pass an `Accept` header with the value `application/octet-stream`

### Enquiry

Enquiries (Internet Registrations) represent a potential sales or lettings lead for the agent. An enquiry can either contain information about a valuation request from a [vendor](./#vendor)/[landlord](./#landlord) or can represent interest from a potential [applicant](./#applicant) such as a viewing request. Enquiries are vetted by the agent before they are promoted into [property](./#property) or [applicant ](./#applicant)entities. Enquiries will appear in AgencyCloud under the 'Internet Registrations' section.&#x20;

### Identity check

Identity checks represent the information captured to verify the identity of a [contact](./#contact) or [company](./#company). Agents must adhere to anti-money laundering regulations and are required to capture proof of identity and address for their customers. Identity checks can store textual information such as passport number as well as file assets associated as [documents](./#document) (such as scanned copies).

### Journal entry

Journal entries indicate that an event has occurred for an associated entity. For example, if a [property](./#property) asking price was changed, this event would be recorded as a timestamped journal entry. Journal entries are used to drive the various activity feeds in our CRM systems.

### Landlord

Landlords represent the details of one or more [contacts](./#contact) or [companies](./#company) that wish to rent out a [property](./#property). Landlords can have a portfolio of any number of [properties](./#property)[ ](https://foundations-documentation.reapit.cloud/platform-glossary#properties)on the system.

### Negotiator

Negotiators represent a member of staff working for an agent. Details about the individual negotiator are captured such as name, job title and email address – as well as the singular [office](./#office) to which they are assigned.

### Notification

A notification is an event that can be passed through to Reapit products in real-time to notify users that something has happened (or is happening). You can read more about the Notifications API and it's associated functionality [here](../api/notifications.md). Please note that this feature is currently in beta.

### Metadata

Our [metadata ](../api/api-documentation.md#metadata)system allows you to easily extend the data that our platform supports. Most of our POST and PATCH endpoints provide the ability to attach a JSON document to our entities which will be automatically included in future fetches of that entity.&#x20;

When using our specific metadata endpoints for more direct, granular control on the data you provide, you can also build new, standalone entities that are specific to your application without needing to hosting your own datastore.&#x20;

Metadata is specific to a developer and any data that your application sets will not be presented to other developers who build on the Foundations platform. We do not recommend using metadata storage for any sensitive information (personally identifiable details, bank accounts, etc).

### Offer

Offers represent the submission of an offer from an [applicant ](./#applicant)to purchase a [property](./#property). Offers are for property sales only and represent information such as monetary amount, date of submission and a status to indicate whether the offer can proceed or not.

### Office

Offices represent the details of a branch within an agency. Offices contain information about the office such as manager, contact details and address, though some offices may be virtual and not have a physical address. Each office can contain multiple [negotiators](./#negotiator).

### Property

Properties represent the details of a building that the agent has had an interaction with. Properties include specifics such as the number of rooms, asking price and descriptive marketing details. Properties can be flagged for both sales and lettings marketing concurrently and are associated to a single [vendor](./#vendor) and/or [landlord](./#landlord) entity.

### Property image

Property images represent a picture that has been taken of a [property](./#property) to be used for marketing purposes. Property images are most frequently used for display on portals, agent web sites and for generation of printed materials.

### Referral

A referral is the action of directing a [contact ](./#contact)or [vendor ](./#vendor)to a third party where there may be interest in the services on offer. This could be anything from a solicitor to a removals company. Users of the AgencyCloud CRM will typically be the ones to initiate a referral.

### Rest hook

Rest hooks are a [loose standard](https://resthooks.org/) for providing a set of APIs to create a [web hook](../api/webhooks.md) programmatically. If your application uses web hooks, this functionality can help you automate onboarding of customers and remove any manual steps needed in the portal.

### Source

Sources represent the origin of enquiry for a potential customer. Many entities such as [applicant](./#applicant), [landlord](./#landlord) and [contact](./#contact) can capture source information which allows the agent to understand where their business is coming from (for example, a portal or google search).

### Task

Tasks represent details on an action that should be performed by a given date. Tasks are categorised by type and can optionally be related to another entity (for example, a task to remind a [negotiator](./#negotiator) to call a [landlord](./#landlord)). If no activation date is specified, tasks can be used to send messages to and from [negotiators](./#negotiator)/[offices](./#office).

### Tenancy

Tenancies represent a [property](./#property) lease agreement between a [landlord](./#landlord) and one or more tenants. The role of the agent during the life-cycle of the tenancy will differ, depending on the agreement with the [landlord](./#landlord). The tenancy can be managed from offer submission/arranging stage right through until the tenancy is finished.

### Transaction

Transactions represent a financial transaction that can be associated to a [property](./#property), [landlord](./#landlord), [tenancy](./#tenancy), or [company](./#company). Examples of transactions are rent payments and supplier invoices. A transaction can be associated with one or more of the aforementioned related entities.

### Vendor

Vendors represents one or more [contact](./#contact) or [companies](./#company) who are interested in selling a [property](./#property). A vendor is always associated to a single [property](./#property) record and is automatically created when a [property](./#property) with sales marketing is added to the platform.

### Works order

Works orders represent one or more maintenance jobs that have been requested for a lettings [property](./#property). Works orders are usually reported by the [landlord](./#landlord) or [tenant ](./#tenancy)and can be tracked from approval until the work has been completed. Approved works orders are assigned to a [company](./#company) supplier who can then provide estimates and costings for the work.
