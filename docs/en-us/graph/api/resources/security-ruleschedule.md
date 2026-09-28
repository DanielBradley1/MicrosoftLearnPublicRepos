<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ruleschedule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# ruleSchedule resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents how often the [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) runs, and when it next runs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| frequency | Duration | The recurring time interval at which the rule runs \(ISO 8601 duration, for example P1D for daily, PT1H for hourly\). |
| nextRunDateTime \(deprecated\) | DateTimeOffset | Timestamp of the custom detection rule's next scheduled run. **Deprecated.** This property will be removed from this resource on 2026-10-01. |
| period \(deprecated\) | String | How often the detection rule is set to run. The allowed values are: `0`, `1H`, `3H`, `12H`, or `24H`. `0` signifies the rule is run continuously. **Deprecated.** Use **frequency** instead. This property will be removed from this resource on 2026-10-01. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ruleSchedule",
  "frequency": "String (duration)",
  "nextRunDateTime": "String (timestamp)",
  "period": "String"
}
```
