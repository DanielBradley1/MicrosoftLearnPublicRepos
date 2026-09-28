<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingworktimeslot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# bookingWorkTimeSlot resource type

Namespace: microsoft.graph

Defines the start and end times for work.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endTime | TimeOfDay | The time of the day when work stops. For example, 17:00:00.0000000. |
| startTime | TimeOfDay | The time of the day when work starts. For example, 08:00:00.0000000. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "endTime": "String (timestamp)",
  "startTime": "String (timestamp)"
}
```
