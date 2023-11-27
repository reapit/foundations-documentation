---
description: Real time event delivery to Reapit products from your applications
---

# Notifications

{% hint style="info" %}
This feature is in beta release and requires you to be invited to the Notifications beta programme
{% endhint %}

The Notifications API allows developers running apps with the `notifications.*.write` scopes to push certain events back through our Platform for delivery to users of Reapit products in real-time. For the beta programme, the only supported scope is`notifications.telephony.write` - the purpose of this mechanism is primarily to replace legacy TAPI support in the AgencyCloud CRM, but there are plans to expand it's use cases in the future.

### How it works

When a developer pushes an event through the Notifications API, it flows through a pipeline that understands where that event should be delivered. When a user logs into a Reapit product, a real-time connection is opened to the Notifications backend which allows bi-directional real-time communication. The events are pushed through these channels and handled by each of the Reapit products independently.

The API itself that is consumed by developers uses an envelope and message (payload) approach to allow the JSON contract to remain fluid so that different event types can be supported. It's important that anybody utilising the endpoint understands the different notification types and how that affects the payload that the API will expect. If the payload is not as expected, API validation routines will reject the event.

### What is supported

The beta programme allows third party telephony providers to push telephony events through to end users of Reapit products. This enables invocation of certain pieces of product specific functionality, such as screen popping when a new call comes in directly inside AgencyCloud.

### Notification payload

{% hint style="warning" %}
Always refer to the Swagger documentation published in the Reapit DeveloperPortal for the most up to date JSON contracts
{% endhint %}

The payload pushed to `POST /notifications` can be thought of as a letter. It has an envelope - which has some basic information about the type of content and where it should be delivered - and a payload, the actual message.

```json
{
  "type": "telephony",
  "subType": "missedCall",
  "products": [
    "AgencyCloud"
  ],
  "targets": {
    "negotiatorId": [
      "ADV"
    ]
  },
  "payload": {}
}
```

The combination of `type` and `subType` tells the system what kind of `payload` to expect.  The incoming data will be validated to ensure the expected payload has been provided, otherwise a validation error will be returned to the caller.

The `targets` object allows the caller to specify where the event should be sent to. Currently this supports one or more `negotiatorId` values. When multiple targets are provided, the system uses a fan-out mechanism to distribute the same event to each recipient. To be able to deliver notifications correctly, the app will need to understand and contain mappings back to users in Reapit products. To do this, request the `negotiators.read` scope, and use the `GET /negotiators` endpoint to fetch user information.

### Notification Types

The following notification types are currently supported. Please note that examples will eventually be available on our Swagger documentation which will supersede this page, however an update to Open API 3 is required before this can be supported

In all payloads, the `id` property can optionally be used to correlate chained events from the source system. For example, the `id` for an `incomingCall` and `answeredCall` event could be the same value to notify our system that the two events are related.

<table><thead><tr><th width="131">Type</th><th width="147">SubType</th><th>Payload Example</th><th>Usage Notes</th></tr></thead><tbody><tr><td>telephony</td><td>incomingCall</td><td>{ <br>    "id": "ax2uyio8p",<br>    "created": "2023-11-01T10:28:00",<br>    "callerId": "07123 456789", <br>    "destinationId": "01234 567890", <br>    "huntGroup": false <br>}</td><td>Providing the <code>huntGroup</code> flag allows some Reapit products to alter how the incoming notification is displayed, however the field is optional</td></tr><tr><td>telephony</td><td>answeredCall</td><td>{ <br>   "id": "ax2uyio8p", <br>   "created": "2023-11-01T10:28:00",<br>    "callerId": "07123 456789", <br>    "destinationId": "01234 567890", <br>    "huntGroup": false, <br>    "answeredById": "TST" <br>}</td><td>Providing the <code>answeredById</code> property is optional, however when a call is delivered to a hunt group, it allows some Reapit products to adjust how notifications are display when one user from the group answers the call. The <code>answeredById</code> should be a valid negotiator id</td></tr><tr><td>telephony</td><td>endedCall</td><td>{ <br>    "id": "ax2uyio8p", <br>    "created": "2023-11-01T10:28:00", <br>    "callerId": "07123 456789", <br>    "destinationId": "01234 567890", <br>    "huntGroup": false, <br>    "answeredById": "TST" <br>}</td><td></td></tr><tr><td>telephony</td><td>missedCall</td><td>{ <br>    "id": "ax2uyio8p", <br>    "created": "2023-11-01T10:28:00", <br>    "callerId": "07123 456789", <br>    "destinationId": "01234 567890", <br>    "huntGroup": false <br>}</td><td>Missed calls are not delivered in real-time and are instead polled by our products</td></tr></tbody></table>



