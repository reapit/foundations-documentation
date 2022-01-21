---
description: TypeScript definition files for the Reapit Foundations API
---

# Foundations TS Defintions

Develop in TypeScript against the Reapit Foundations Platform with confidence

If you are using TypeScript \(and we recommend you do!\), for your front end or NodeJS project, we provide full type definitions for the API documented in the [API explorer](https://github.com/reapit/foundations-documentation/tree/db0718c9be27b7760dfae34e69518806acf0e855/developer/swagger/README.md).

We generate these types from the Swagger contracts direct with a daily CRON job, so you can be sure that when the API changes, your types will be updated too. This allows for a much closer alignment between front and back end development, with compile time feedback on definition changes. Ultimately this should lead to more robust applications.

{% hint style="warning" %}
The definitions are updated automatically when the API changes. As such, it is recommended strongly that you match by date stamp the correct version of the definitions to the API version you are using in your headers.
{% endhint %}

### Usage:

For the latest version;

`yarn add @reapit/foundations-ts-definitions`


Then import the required type into your code with ES6 Modules or CommonJS. The naming maps directly to the model names in the API Explorer in the developer portal.

```javascript
import { AppModel } from '@reapit/foundations-ts-definitions'

// Or

const { AppModel } = require('@reapit/foundations-ts-definitions')
```

### Webhook types

Webhook event payloads are generic, however the types can be infered by the topicId. Here are some examples of how to use the webhook types

```ts
import {
  ReapitWebhookPayloadType,
  ReapitWebhookTopicEnum,
  ReapitWebhookApplicantCreatedEvent,
} from '@reapit/foundations-ts-definitions'

export const webhookEventHandler = (event: ReapitWebookPayloadType) => {
  switch (event.topicId) {
    case ReapitWebhookTopicEnum.APPLICANTS_CREATED:
      handleApplicantCreated(event) // event is of infered type ReapitWebhookApplicantCreatedEvent
      break
    default:
      console.log(event.new) // event.new is of infered type any
  }
}

const handleApplicantCreated = (event: ReapitWebhookApplicantCreatedEvent) => {
  console.log(event.new) // new is of inferred type ApplicantModel
}
```
