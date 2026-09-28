<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftappsfilestoragecontainerusage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# microsoftAppsFileStorageContainerUsage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents tenant-level storage usage data for SharePoint Embedded file storage containers.

This resource provides aggregated metrics including total storage used and container count across the tenant, with the ability to expand to geo-level and app-level details.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get SharePoint Embedded file storage container usage summary](https://learn.microsoft.com/en-us/graph/api/reportroot-getmicrosoftappsfilestoragecontainerusagesummary?view=graph-rest-beta) | [microsoftAppsFileStorageContainerUsage](https://learn.microsoft.com/en-us/graph/api/resources/microsoftappsfilestoragecontainerusage?view=graph-rest-beta) | Get storage usage data for SharePoint Embedded file storage containers in a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the usage summary. The value is always `microsoftAppsFileStorageContainerUsageSummary`. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| totalActiveContainerCount | Int64 | The total number of active file storage containers across the tenant. |
| totalActiveStorageUsedInBytes | Int64 | The total storage used in bytes across all active file storage containers in the tenant. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| usageByDataLocation | [microsoftAppsFileStorageContainerGeoUsage](https://learn.microsoft.com/en-us/graph/api/resources/microsoftappsfilestoragecontainergeousage?view=graph-rest-beta) collection | Storage usage data broken down by geographic location. Expandable using `$expand=usageByDataLocation`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerUsage",
  "id": "String (identifier)",
  "totalActiveStorageUsedInBytes": "Int64",
  "totalActiveContainerCount": "Int64",
  "usageByDataLocation": [{"@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerGeoUsage"}]
}
```
