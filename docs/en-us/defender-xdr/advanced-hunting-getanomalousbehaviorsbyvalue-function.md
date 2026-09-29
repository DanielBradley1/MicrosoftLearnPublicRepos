<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-getanomalousbehaviorsbyvalue-function -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# GetAnomalousBehaviorsByValue\(\)

Use the `GetAnomalousBehaviorsByValue()` function in [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to return behaviors containing an insight that involves a specific entity or contextual value.

The function searches the `Value` fields in each insight's `About` array. You can optionally limit the results to a specific insight type.

## Syntax

```kusto
invoke GetAnomalousBehaviorsByValue(entityValue, insightType)
```

## Parameters

- **entityValue**—Required. A `string` containing the exact `Value` to match in the insight's `About` array. The value can represent an account, country, IP address, ISP, device, resource, or other contextual value.
- **insightType**—Optional. A `string` containing the exact insight type to match, such as `FirstSeen`, `UncommonValue`, or `HighVolumeAnomaly`. If you omit this parameter or specify an empty string, the function matches all insight types.

Invoke the function as part of a query on a tabular input that contains an `Insights` column of type `string`.

## Return value

Returns the rows from the input table containing an insight whose `About` array includes an entry with the specified `Value`. When `insightType` is provided, only insights of that type are evaluated. All columns from the input table are preserved.

## Examples

### Find FirstSeen insights involving a specific account

```kusto
BehaviorInfo
| where ServiceSource == "Microsoft Sentinel"
| invoke GetAnomalousBehaviorsByValue(
    "jsmith@contoso.com",
    "FirstSeen"
)
| project TimeGenerated, BehaviorId, Title, Insights
| order by TimeGenerated desc
```

### Find all insights involving a specific country

Omit the `insightType` parameter to return matching insights of any type.

```kusto
BehaviorInfo
| where ServiceSource == "Microsoft Sentinel"
| invoke GetAnomalousBehaviorsByValue("Sweden")
| project TimeGenerated, BehaviorId, Title, Insights
```

## Related content

- [Investigate anomalies on UEBA behaviors in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/ueba-anomalies-on-behaviors)
- [BehaviorInfo table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorinfo-table)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
