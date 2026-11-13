<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/retentionsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# retentionSetting resource type

Namespace: microsoft.graph

Contains the backup frequency and retention period for the **retentionSettings** property of [protectionPolicyBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) and its derived types.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| interval | String | The backup frequency, expressed as an ISO 8601 repeating interval. The service defines the backup intervals: `R/PT10M` for 10-minute copies and `R/P1W` for weekly copies. Use `R/P1W` when specifying the policy retention period in a create or update request. |
| period | Duration | The period of time to retain the protected data for a single Microsoft 365 service, expressed as an ISO 8601 duration. The supported policy retention periods in create and update requests are: `P90D`, `P180D`, `P365D`, `P730D`, `P1095D`, `P1460D`, `P1825D`, `P2190D`, `P2555D`, `P2920D`, `P3285D`, and `P3650D`. Other policy retention periods aren't supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.retentionSetting",
  "interval": "String",
  "period": "String (duration)"
}
```
