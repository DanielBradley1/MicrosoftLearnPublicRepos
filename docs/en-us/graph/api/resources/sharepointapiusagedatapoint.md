<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointapiusagedatapoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# sharePointApiUsageDataPoint resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a single data point in a OneDrive and SharePoint API usage report. Each data point can be either a summary row or a detail row:

- **Summary row**: Aggregated usage across all applications for a date or period. The **appId** is `null` and **activeApps** is populated.
- **Detail row**: Usage for a specific application on a specific date. The **appId** is populated and **activeApps** is `null`.

Data points in detail rows are ordered by **usageDateTime** descending \(most recent first\).

The properties present in each data point depend on the report type requested through the `reportType` parameter of the [getSharePointApiUsage](https://learn.microsoft.com/en-us/graph/api/reportroot-getsharepointapiusage?view=graph-rest-beta) function. The `egressReport` includes **usageMB** but not **throttledRequests**, while the `throttlingReport` includes **throttledRequests** but not **usageMB**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeApps | Int32 | The number of distinct applications with usage during the reporting period. Summary rows: populated with the count of active applications. Detail rows: null. Read-only. |
| appId | String | The unique identifier \(GUID\) for the application. Summary rows: null. Detail rows: the application GUID. Read-only. |
| serviceArea | String | The service area name. Always `OneDrive and SharePoint` for SharePoint API usage reports. Read-only. |
| tenantId | String | The unique identifier \(GUID\) for the tenant. Read-only. |
| throttledRequests | Int64 | The number of API requests that were throttled. Only present in the throttlingReport; this property isn't returned for the egressReport. Summary rows: total throttled requests across all applications. Detail rows: throttled requests for the specific application on the specific date. Read-only. |
| usageDateTime | DateTimeOffset | The date and time for this data point in ISO 8601 format. For summary rows, this is the most recent date in the reporting period. For detail rows, this is the specific date for the usage data. Read-only. |
| usageMB | Int64 | Total usage in megabytes \(MB\) for this data point. Only present in the egressReport; this property isn't returned for the throttlingReport. Summary rows: total aggregated usage across all applications for the reporting period. Detail rows: usage for the specific application on the specific date. Read-only. |
| usageRequests | Int64 | The number of API requests. Summary rows: total requests across all applications. Detail rows: requests for the specific application on the specific date. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointApiUsageDataPoint",
  "activeApps": "Int32",
  "appId": "String",
  "serviceArea": "String",
  "tenantId": "String",
  "throttledRequests": "Int64",
  "usageDateTime": "String (timestamp)",
  "usageMB": "Int64",
  "usageRequests": "Int64"
}
```
