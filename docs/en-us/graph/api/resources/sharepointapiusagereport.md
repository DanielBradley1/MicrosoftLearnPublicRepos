<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointapiusagereport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# sharePointApiUsageReport resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents aggregated OneDrive and SharePoint API usage data for a tenant. The report contains a summary aggregating usage across all applications and details showing per-application usage.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| details | [sharePointApiUsageDataPoint](https://learn.microsoft.com/en-us/graph/api/resources/sharepointapiusagedatapoint?view=graph-rest-beta) collection | The collection of per-application, per-date usage data points. Each item represents usage for a specific application on a specific date. |
| summary | [sharePointApiUsageDataPoint](https://learn.microsoft.com/en-us/graph/api/resources/sharepointapiusagedatapoint?view=graph-rest-beta) | The aggregated summary of usage across all applications for the specified period or date. The **appId** is `null` and **activeApps** contains the count of distinct applications. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointApiUsageReport",
  "summary": {
    "@odata.type": "microsoft.graph.sharePointApiUsageDataPoint"
  },
  "details": [
    {
      "@odata.type": "microsoft.graph.sharePointApiUsageDataPoint"
    }
  ]
}
```
