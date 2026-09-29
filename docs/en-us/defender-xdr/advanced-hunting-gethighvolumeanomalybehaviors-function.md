<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-gethighvolumeanomalybehaviors-function -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# GetHighVolumeAnomalyBehaviors\(\)

Use the `GetHighVolumeAnomalyBehaviors()` function in [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to return behaviors that contain at least one `HighVolumeAnomaly` insight in the `Insights` column.

A `HighVolumeAnomaly` insight indicates that an unusually high volume of activity was detected compared to the established behavioral baseline.

## Syntax

```kusto
invoke GetHighVolumeAnomalyBehaviors()
```

## Parameters

This function has no explicit parameters. Invoke it as part of a query on a tabular input that contains an `Insights` column of type `string`.

## Return value

Returns the rows from the input table that contain at least one `HighVolumeAnomaly` insight. All columns from the input table are preserved.

## Example

### Find recent behaviors with unusually high activity volume

```kusto
BehaviorInfo
| where ServiceSource == "Microsoft Sentinel"
| where TimeGenerated > ago(7d)
| invoke GetHighVolumeAnomalyBehaviors()
| project TimeGenerated, BehaviorId, Title, Insights
| order by TimeGenerated desc
```

## Related content

- [Investigate anomalies on UEBA behaviors in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/ueba-anomalies-on-behaviors)
- [BehaviorInfo table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorinfo-table)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
