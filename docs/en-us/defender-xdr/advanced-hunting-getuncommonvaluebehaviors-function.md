<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-getuncommonvaluebehaviors-function -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# GetUncommonValueBehaviors\(\)

Use the `GetUncommonValueBehaviors()` function in [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to return behaviors that contain at least one `UncommonValue` insight in the `Insights` column.

An `UncommonValue` insight indicates that a value associated with the behavior, such as a country or internet service provider \(ISP\), is rarely observed across the organization.

## Syntax

```kusto
invoke GetUncommonValueBehaviors()
```

## Parameters

This function has no explicit parameters. Invoke it as part of a query on a tabular input that contains an `Insights` column of type `string`.

## Return value

Returns the rows from the input table that contain at least one `UncommonValue` insight. All columns from the input table are preserved.

## Example

### Find Microsoft Sentinel behaviors with uncommon values

```kusto
BehaviorInfo
| where ServiceSource == "Microsoft Sentinel"
| invoke GetUncommonValueBehaviors()
| project TimeGenerated, BehaviorId, Title, Insights
| order by TimeGenerated desc
```

## Related content

- [Investigate anomalies on UEBA behaviors in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/ueba-anomalies-on-behaviors)
- [BehaviorInfo table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorinfo-table)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
