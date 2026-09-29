<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-getanomalousbehaviorsabout-function -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# GetAnomalousBehaviorsAbout\(\)

Use the `GetAnomalousBehaviorsAbout()` function in [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to return behaviors whose insights match multiple entity or contextual criteria.

The function searches the `About` array of each insight. All supplied filters must be satisfied within the same insight for the behavior to be returned.

The function supports up to three filter objects.

## Syntax

```kusto
invoke GetAnomalousBehaviorsAbout(filters)
```

## Parameters

- **filters**—Required. A `dynamic` JSON array containing one to three filter objects.

Each filter object supports the following properties:

| Property | Required | Description |
| --- | --- | --- |
| `Kind` | Yes | The exact entity or context type to match, such as `Account`, `Country`, `IP`, `Host`, or `ISP`. |
| `Value` | No | The exact value to match for the specified `Kind`. Omit `Value` or specify an empty string to match any value of that `Kind`. |

All filter objects use AND logic. A behavior is returned only when every filter is matched within the same insight's `About` array.

Invoke the function as part of a query on a tabular input that contains an `Insights` column of type `string`.

## Return value

Returns the rows from the input table containing at least one insight whose `About` array satisfies all specified filter criteria. All columns from the input table are preserved.

## Examples

### Find insights involving a specific account and any country

```kusto
BehaviorInfo
| where ServiceSource == "Microsoft Sentinel"
| invoke GetAnomalousBehaviorsAbout(
    dynamic([
        {
            "Kind": "Account",
            "Value": "jsmith@contoso.com"
        },
        {
            "Kind": "Country"
        }
    ])
)
| project TimeGenerated, BehaviorId, Title, Insights
| order by TimeGenerated desc
```

### Find insights involving an exact country, account, and IP address

```kusto
BehaviorInfo
| where ServiceSource == "Microsoft Sentinel"
| invoke GetAnomalousBehaviorsAbout(
    dynamic([
        {
            "Kind": "Country",
            "Value": "Brazil"
        },
        {
            "Kind": "Account",
            "Value": "jsmith@contoso.com"
        },
        {
            "Kind": "IP",
            "Value": "1.2.3.4"
        }
    ])
)
| project TimeGenerated, BehaviorId, Title, Insights
```

## Related content

- [Investigate anomalies on UEBA behaviors in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/ueba-anomalies-on-behaviors)
- [BehaviorInfo table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-behaviorinfo-table)
- [Advanced hunting overview](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview)
- [Learn the query language](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
