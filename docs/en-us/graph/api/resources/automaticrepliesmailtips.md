<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/automaticrepliesmailtips?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# automaticRepliesMailTips resource type

Namespace: microsoft.graph

[MailTips](https://learn.microsoft.com/en-us/graph/api/resources/mailtips?view=graph-rest-1.0) about any automatic replies that have been set up on a mailbox.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| message | String | The automatic reply message. |
| messageLanguage | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-1.0) | The language that the automatic reply message is in. |
| scheduledEndTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time that automatic replies are set to end. |
| scheduledStartTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time that automatic replies are set to begin. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "message": "string",
  "messageLanguage": {"@odata.type": "microsoft.graph.localeInfo"},
  "scheduledEndTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "scheduledStartTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"}
}
```
