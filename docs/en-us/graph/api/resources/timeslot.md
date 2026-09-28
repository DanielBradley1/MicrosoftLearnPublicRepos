<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/timeslot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# timeSlot resource type

Namespace: microsoft.graph

Represents a time slot for a meeting.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| end | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that a period ends. |
| start | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that a period begins. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "end": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "start": {"@odata.type": "microsoft.graph.dateTimeTimeZone"}
}
```
