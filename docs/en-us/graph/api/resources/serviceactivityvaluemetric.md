<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceactivityvaluemetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# serviceActivityValueMetric resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the aggregated value of a service activity metric over a given interval from the start time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| intervalStartDateTime | DateTimeOffset | The starting date and time \(UTC\) of the interval. |
| value | Int64 | The aggregated value over the given aggregation interval starting from the `intervalStartDateTime`. The value is caculated at the minute level. The value at the starting minute of the `intervalStartDateTime` is included. The value at the last minute of the given interval is excluded. For example, if `intervalStartDateTime` is `2023-09-20T18:00:00Z` and aggregation interval is `5` minutes, then the value is aggregated from `2023-09-20T18:00:00Z`\(inclusive\) to `2023-09-20T18:05:00Z`\(exclusive\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceActivityValueMetric",
  "intervalStartDateTime": "String (timestamp)",
  "value": "Integer"
}
```
