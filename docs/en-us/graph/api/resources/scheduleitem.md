<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/scheduleitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# scheduleItem resource type

Namespace: microsoft.graph

An item that describes the availability of a user corresponding to an actual event on the user's default calendar. This item applies to a resource \(room or equipment\) as well.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| end | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that the corresponding event ends. |
| isPrivate | Boolean | The sensitivity of the corresponding event. True if the event is marked `private`, false otherwise. Optional. |
| location | String | The location where the corresponding event is held or attended from. Optional. |
| start | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that the corresponding event starts. |
| status | freeBusyStatus | The availability status of the user or resource during the corresponding event. The possible values are: `free`, `tentative`, `busy`, `oof`, `workingElsewhere`, `unknown`. |
| subject | String | The corresponding event's subject line. Optional. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "end": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "isPrivate": true,
  "location": "String",
  "start": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "status": "String",
  "subject": "String"
}
```
