<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceactivityperformancemetric?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-03 -->

# serviceActivityPerformanceMetric resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the aggregated percentage of performance for a service over a given interval from the start time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| intervalStartDateTime | DateTimeOffset | The start date and time \(UTC\) of the interval. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| percentage | Double | The aggregated performance over the given aggregation interval that starts from the **intervalStartDateTime**. The performance is calculated at the minute level. The performance at the starting minute of the **intervalStartDateTime** is included. The performance at the last minute of the given interval is excluded. For example, if **intervalStartDateTime** is `2023-09-20T18:00:00Z` and the aggregation interval is `5` minutes, then performance is aggregated from `2023-09-20T18:00:00Z` \(inclusive\) to `2023-09-20T18:05:00Z` \(exclusive\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceActivityPerformanceMetric",
  "intervalStartDateTime": "String (timestamp)",
  "percentage": "Double"
}
```
