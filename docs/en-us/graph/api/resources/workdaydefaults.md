<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workdaydefaults?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# workDayDefaults resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **workDayDefaults** property of the [planCalendar](https://learn.microsoft.com/en-us/graph/api/resources/plancalendar?view=graph-rest-beta) resource uses this type.

Default working-day start and end times for a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), used by [planCalendar](https://learn.microsoft.com/en-us/graph/api/resources/plancalendar?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endTime | TimeOfDay | Default end time of the working day. |
| startTime | TimeOfDay | Default start time of the working day. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workDayDefaults",
  "startTime": "String (time of day)",
  "endTime": "String (time of day)"
}
```
