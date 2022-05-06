---
description: >-
  This section provides further information on the concepts and terminology
  referenced by the Reapit Foundations Platform and the endpoints we provide
---

# Platform Glossary

### Applicant

Applicants represent the [property](platform-glossary.md#property) buying or renting interests of one or more [contacts](platform-glossary.md#contact) or [companies](platform-glossary.md#company). This includes requirements such as the number of rooms, maximum budget and the geographical areas that the applicant is interested in.&#x20;

### Area

Areas represent a specific geographical location that an [applicant ](platform-glossary.md#applicant)is interested in buying/renting within. Areas are comprised of either polygon coordinates or a listing of postcodes. Areas are hierarchical and a single area can alternatively include a list of other areas.

### Appointment

Appointments represent calendar engagements used by [negotiators](platform-glossary.md#negotiator) to schedule meetings or arrange events, such as [property](platform-glossary.md#property) viewings and valuations. Appointments can be set to recur by including recurrence information and can be scheduled to appear in multiple [negotiators](platform-glossary.md#negotiator)’ calendars.

### Company

Companies represent a business organisation that the agent ([customer](platform-glossary.md#customer)) has a relationship with. Companies can be assigned a type which relates to the various roles they are able to fulfill such as solicitor or supplier, as well as being able to be involved in their own [property](platform-glossary.md#property) transactions.

### Configuration

Configuration represents the customisation options relevant for a customers data set, as some data can differ depending on the configuration of the customer. For example, an agent may want to add to their list of [vendor](platform-glossary.md#vendor) selling reasons so that it can be set against a particular [vendors ](platform-glossary.md#vendor)`sellingReasonId`

We present lists like this as RESTful endpoints and document where a field references a configurable lists id. We also include links/embed options where appropriate to simplify consumption.

### Contact

Contacts represent the details of a person that the agent has a relationship with. Contact details are captured and managed centrally so that a single contact can fulfill multiple [vendor](platform-glossary.md#vendor), [landlord](platform-glossary.md#landlord), [applicant ](platform-glossary.md#applicant)and [tenancy](platform-glossary.md#tenancy) roles at the same time.

### Conveyancing

Conveyancing represents the process of progressing an accepted [offer ](platform-glossary.md#offer)to the completion of the sale of a property.&#x20;

Submitting new offers and transitioning them to an accepted status is done using the Offers API. The Conveyancing API is responsible for transitioning that existing, accepted offer into a completed property sale.&#x20;

Our Conveyancing APIs also allow a chain to be managed, providing a means of linking dependant offers together. It's possible to link to offers added to other properties that the customer has instructed, as well as those that are external and instructed to another agent.

### Customer

Customers represent estate agents who use Reapit software. We do not provide an API to obtain details of our customers, instead, their details will be known to you at the point that they install your AppMarket application.&#x20;

### Department

Departments represent a set of descriptive attributes used to describe a [property](platform-glossary.md#property). Departments are assigned to both [properties](platform-glossary.md#property) and [applicants ](platform-glossary.md#applicant)and are used to define which attributes can be used to describe a [property ](platform-glossary.md#property)or an [applicant](platform-glossary.md#applicant) property requirement.

A Department is most commonly used to ring fence groups of [properties](platform-glossary.md#property) and [applicants](platform-glossary.md#applicant), particularly when it comes to matching (the process of finding properties that meet specific applicant requirements and vice versa). Typically, customers dealing with only residential sales and lettings will have a single department as there is no real need to separate any of the data, however an example of where multiple departments might be configured would be a customer who deals with both residential and commercial property transactions. In this scenario, a separate Department would normally be setup to separate the two disparate sets of data, as it would be undesirable for residential applicants to be sent details of commercial properties.

### Document

Documents represent the details of a file asset that has added to our platform. Documents can be assigned a type to indicate its purpose (eg. a brochure) and associated to an associated entity (eg. a [property](platform-glossary.md#property)).

### Enquiry

Enquiries (Internet Registrations) represent a potential sales or lettings lead for the agent. An enquiry can either contain information about a valuation request from a [vendor](platform-glossary.md#vendor)/[landlord](platform-glossary.md#landlord) or can represent interest from a potential [applicant](platform-glossary.md#applicant) such as a viewing request. Enquiries are vetted by the agent before they are promoted into [property](platform-glossary.md#property) or [applicant ](platform-glossary.md#applicant)entities. Enquiries will appear in AgencyCloud under the 'Internet Registrations' section.&#x20;

### Identity check

Identity checks represent the information captured to verify the identity of a [contact](platform-glossary.md#contact) or [company](platform-glossary.md#company). Agents must adhere to anti-money laundering regulations and are required to capture proof of identity and address for their customers. Identity checks can store textual information such as passport number as well as file assets associated as [documents](platform-glossary.md#document) (such as scanned copies).

### Journal entry

Journal entries indicate that an event has occurred for an associated entity. For example, if a [property](platform-glossary.md#property) asking price was changed, this event would be recorded as a timestamped journal entry. Journal entries are used to drive the various activity feeds in our CRM systems.

### Landlord

Landlords represent the details of one or more [contacts](platform-glossary.md#contact) or [companies](platform-glossary.md#company) that wish to rent out a [property](platform-glossary.md#property). Landlords can have a portfolio of any number of [properties](platform-glossary.md#property)[ ](https://foundations-documentation.reapit.cloud/platform-glossary#properties)on the system.

### Negotiator

Negotiators represent a member of staff working for an agent. Details about the individual negotiator are captured such as name, job title and email address – as well as the singular [office](platform-glossary.md#office) to which they are assigned.

### Metadata

Our [metadata ](api/api-documentation.md#metadata)system allows you to easily extend the data that our platform supports. Most of our POST and PATCH endpoints provide the ability to attach a JSON document to our entities which will be automatically included in future fetches of that entity.&#x20;

When using our specific metadata endpoints for more direct, granular control on the data you provide, you can also build new, standalone entities that are specific to your application without needing to hosting your own datastore.&#x20;

Metadata is specific to a developer and any data that your application sets will not be presented to other developers who build on the Foundations platform. We do not recommend using metadata storage for any sensitive information (personally identifiable details, bank accounts, etc).

### Offer

Offers represent the submission of an offer from an [applicant ](platform-glossary.md#applicant)to purchase a [property](platform-glossary.md#property). Offers are for property sales only and represent information such as monetary amount, date of submission and a status to indicate whether the offer can proceed or not.

### Office

Offices represent the details of a branch within an agency. Offices contain information about the office such as manager, contact details and address, though some offices may be virtual and not have a physical address. Each office can contain multiple [negotiators](platform-glossary.md#negotiator).

### Property

Properties represent the details of a building that the agent has had an interaction with. Properties include specifics such as the number of rooms, asking price and descriptive marketing details. Properties can be flagged for both sales and lettings marketing concurrently and are associated to a single [vendor](platform-glossary.md#vendor) and/or [landlord](platform-glossary.md#landlord) entity.

### Property image

Property images represent a picture that has been taken of a [property](platform-glossary.md#property) to be used for marketing purposes. Property images are most frequently used for display on portals, agent web sites and for generation of printed materials.

### Rest hook

Rest hooks are a [loose standard](https://resthooks.org) for providing a set of APIs to create a [web hook](api/webhooks.md) programmatically. If your application uses web hooks, this functionality can help you automate onboarding of customers and remove any manual steps needed in the portal.

### Source

Sources represent the origin of enquiry for a potential customer. Many entities such as [applicant](platform-glossary.md#applicant), [landlord](platform-glossary.md#landlord) and [contact](platform-glossary.md#contact) can capture source information which allows the agent to understand where their business is coming from (for example, a portal or google search).

### Task

Tasks represent details on an action that should be performed by a given date. Tasks are categorised by type and can optionally be related to another entity (for example, a task to remind a [negotiator](platform-glossary.md#negotiator) to call a [landlord](platform-glossary.md#landlord)). If no activation date is specified, tasks can be used to send messages to and from [negotiators](platform-glossary.md#negotiator)/[offices](platform-glossary.md#office).

### Tenancy

Tenancies represent a [property](platform-glossary.md#property) lease agreement between a [landlord](platform-glossary.md#landlord) and one or more tenants. The role of the agent during the life-cycle of the tenancy will differ, depending on the agreement with the [landlord](platform-glossary.md#landlord). The tenancy can be managed from offer submission/arranging stage right through until the tenancy is finished.

### Transaction

Transactions represent a financial transaction that can be associated to a [property](platform-glossary.md#property), [landlord](platform-glossary.md#landlord), [tenancy](platform-glossary.md#tenancy), or [company](platform-glossary.md#company). Examples of transactions are rent payments and supplier invoices. A transaction can be associated with one or more of the aforementioned related entities.

### Vendor

Vendors represents one or more [contact](platform-glossary.md#contact) or [companies](platform-glossary.md#company) who are interested in selling a [property](platform-glossary.md#property). A vendor is always associated to a single [property](platform-glossary.md#property) record and is automatically created when a [property](platform-glossary.md#property) with sales marketing is added to the platform.

### Works order

Works orders represent one or more maintenance jobs that have been requested for a lettings [property](platform-glossary.md#property). Works orders are usually reported by the [landlord](platform-glossary.md#landlord) or [tenant ](platform-glossary.md#tenancy)and can be tracked from approval until the work has been completed. Approved works orders are assigned to a [company](platform-glossary.md#company) supplier who can then provide estimates and costings for the work.
