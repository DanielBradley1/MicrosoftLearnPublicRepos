<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-applicationanalyticsusagepoint?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# applicationAnalyticsUsagePoint resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a single data point for application usage analytics, providing daily aggregated counts for cloud and enterprise applications in Global Secure Access. This information is returned by the [getApplicationUsageAnalytics](https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-getapplicationusageanalytics?view=graph-rest-beta) API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudAppsCount | Int64 | The count attributed to cloud applications for the specified aggregation type. |
| enterpriseAppsCount | Int64 | The count attributed to enterprise applications for the specified aggregation type. |
| timeStampDateTime | DateTimeOffset | The date for which the aggregated data point represents. |
| totalCount | Int64 | The total count for the specified aggregation type \(users, devices, or transactions\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.applicationAnalyticsUsagePoint",
  "timeStampDateTime": "String (timestamp)",
  "totalCount": "Integer",
  "enterpriseAppsCount": "Integer",
  "cloudAppsCount": "Integer"
}
```
