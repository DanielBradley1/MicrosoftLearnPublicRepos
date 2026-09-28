<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/automaticrepliessetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# automaticRepliesSetting resource type

Namespace: microsoft.graph

Configuration settings to automatically notify the sender of an incoming email with a message from the signed-in user. For example, an automatic reply to notify that the signed-in user is unavailable to respond to emails.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| externalAudience | externalAudienceScope | The set of audience external to the signed-in user's organization who will receive the **ExternalReplyMessage**, if **Status** is `AlwaysEnabled` or `Scheduled`. The possible values are: `none`, `contactsOnly`, `all`. |
| externalReplyMessage | string | The automatic reply to send to the specified external audience, if **Status** is `AlwaysEnabled` or `Scheduled`. |
| internalReplyMessage | string | The automatic reply to send to the audience internal to the signed-in user's organization, if **Status** is `AlwaysEnabled` or `Scheduled`. |
| scheduledEndDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time that automatic replies are set to end, if **Status** is set to `Scheduled`. |
| scheduledStartDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time that automatic replies are set to begin, if **Status** is set to `Scheduled`. |
| status | automaticRepliesStatus | Configurations status for automatic replies. The possible values are: `disabled`, `alwaysEnabled`, `scheduled`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "externalAudience": "String",
  "externalReplyMessage": "string",
  "internalReplyMessage": "string",
  "scheduledEndDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "scheduledStartDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "status": "String"
}
```
