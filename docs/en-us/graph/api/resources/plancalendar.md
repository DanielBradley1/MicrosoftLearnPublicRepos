<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plancalendar?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# planCalendar resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **calendar** property of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) resource uses this type.

Working-time calendar settings for a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), including the plan's time zone and default working days.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| timeZone | String | Time zone the plan's calendar is expressed in. |
| workDayDefaults | [workDayDefaults](https://learn.microsoft.com/en-us/graph/api/resources/workdaydefaults?view=graph-rest-beta) | Default working-day start and end times for the plan. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.planCalendar",
  "timeZone": "String",
  "workDayDefaults": {
    "@odata.type": "microsoft.graph.workDayDefaults"
  }
}
```
