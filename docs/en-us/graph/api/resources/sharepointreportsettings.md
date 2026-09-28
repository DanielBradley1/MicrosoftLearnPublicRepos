<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointreportsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# sharePointReportSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the tenant-level settings for SharePoint API usage reports. This resource allows you to enable, disable, or view the status of API usage report metrics.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/sharepointreportsettings-list-apiusagereportmetrics?view=graph-rest-beta) | [apiUsageReportEnablementStatus](https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta) collection | Get the list of [SharePoint API usage report metrics and their enablement status](https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta) for the tenant. |
| [Enable API usage report](https://learn.microsoft.com/en-us/graph/api/sharepointreportsettings-enableapiusagereport?view=graph-rest-beta) | [apiUsageReportEnablementStatus](https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta) | Enable a [SharePoint API usage report metric](https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta) for the tenant. |
| [Disable API usage report](https://learn.microsoft.com/en-us/graph/api/sharepointreportsettings-disableapiusagereport?view=graph-rest-beta) | [apiUsageReportEnablementStatus](https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta) | Disable a [SharePoint API usage report metric](https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta) for the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the SharePoint report settings object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| apiUsageReportMetrics | [apiUsageReportEnablementStatus](https://learn.microsoft.com/en-us/graph/api/resources/apiusagereportenablementstatus?view=graph-rest-beta) collection | The collection of API usage report metrics and the status of their enablement. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointReportSettings",
  "id": "String (identifier)"
}
```
