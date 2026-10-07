<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/retentionperiodchange?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# retentionPeriodChange resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the retention period changes to be applied to a protection unit.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| effectiveFromDateTime | DateTimeOffset | The date and time from which the retention period change takes effect. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026, is `2026-01-01T00:00:00Z`. |
| status | retentionPeriodChangeStatus | Indicates the progress of the application of the retention period change. The possible values are: `none`, `inProgress`, `failed`, `completed`, `unknownFutureValue`. |
| targetRetentionPeriodInDays | Int32 | Specifies the retention period, in days, that applies after the change is completed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.retentionPeriodChange",
  "status": "String",
  "targetRetentionPeriodInDays": "Int32",
  "effectiveFromDateTime": "String (timestamp)"
}
```
