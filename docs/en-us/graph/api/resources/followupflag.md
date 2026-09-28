<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/followupflag?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# followupFlag resource type

Namespace: microsoft.graph

Allows setting a flag in an item for the user to follow up on later.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time that the follow-up was finished. |
| dueDateTime | **dateTimeTimeZone** | The date and time that the follow-up is to be finished. **Note**: To set the due date, you must also specify the `startDateTime`; otherwise, you get a `400 Bad Request` response. |
| flagStatus | followupFlagStatus | The status for follow-up for an item. Possible values are `notFlagged`, `complete`, and `flagged`. |
| startDateTime | **dateTimeTimeZone** | The date and time that the follow-up is to begin. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "completedDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "dueDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "flagStatus": "String",
  "startDateTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"}
}
```
