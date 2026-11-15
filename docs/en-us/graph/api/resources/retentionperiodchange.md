<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/retentionperiodchange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# retentionPeriodChange resource type

Namespace: microsoft.graph

Describes the retention period changes to be applied to a protection unit.

The **pendingRetentionPeriodChange** property of [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) returns this resource when a protection unit moves between policies with different retention periods. The property is read-only and is `null` when no change is pending.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| effectiveFromDateTime | DateTimeOffset | The date and time from which the retention period change takes effect. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2026, is `2026-01-01T00:00:00Z`. Nullable. |
| status | retentionPeriodChangeStatus | Indicates the progress of the application of the retention period change. The possible values are: `none`, `inProgress`, `failed`, `completed`, `unknownFutureValue`. Not nullable. |
| targetRetentionPeriodInDays | Int32 | Specifies the retention period, in days, that applies after the change is completed. Nullable. |

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
