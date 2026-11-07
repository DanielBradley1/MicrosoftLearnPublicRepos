<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ruleschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# ruleSchedule resource type

Namespace: microsoft.graph.security

Represents how often the [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) runs, and when it next runs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| frequency | Duration | The recurring time interval at which the rule runs \(ISO 8601 duration, for example P1D for daily, PT1H for hourly\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ruleSchedule",
  "frequency": "String (duration)"
}
```
