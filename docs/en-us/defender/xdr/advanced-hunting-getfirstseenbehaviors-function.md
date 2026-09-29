<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-getfirstseenbehaviors-function -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# GetFirstSeenBehaviors\(\)

Use the `GetFirstSeenBehaviors()` function in [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to return behaviors that contain at least one `FirstSeen` insight in the `Insights` column.

A `FirstSeen` insight indicates that a behavior, entity, value, or combination of values was observed for the first time.

## Syntax

```kusto
invoke GetFirstSeenBehaviors()
```

## Parameters

This function has no explicit parameters. Invoke it as part of a query on a tabular input that contains an `Insights` column of type `string`.

## Return value

Returns the rows from the input table that contain at least one `FirstSeen` insight. All columns from the input table are preserved.

## Example

### Find recent Microsoft Sentinel behaviors with FirstSeen insights

```kusto
BehaviorInfo
| where ServiceSource == "Microsoft Sentinel"
| where TimeGenerated > ago(1d)
| invoke GetFirstSeenBehaviors()
| project TimeGenerated, BehaviorId, Title, Insights
```

## Related content

- [Investigate anomalies on UEBA behaviors in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/ueba-anomalies-on-behaviors)
- [BehaviorInfo table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorinfo-table)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
