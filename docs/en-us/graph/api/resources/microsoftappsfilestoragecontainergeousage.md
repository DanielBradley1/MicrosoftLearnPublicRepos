<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftappsfilestoragecontainergeousage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# microsoftAppsFileStorageContainerGeoUsage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents geo-level storage usage data for SharePoint Embedded file storage containers.

This resource provides aggregated metrics for a specific geographic location, including storage used and container count, with the ability to expand to app-level details.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeContainerCount | Int64 | The number of active file storage containers in this geographic location. |
| activeStorageUsedInBytes | Int64 | The storage used in bytes for active file storage containers in this geographic location. |
| dataLocationCode | String | The geographic location code \(for example, `NAM` for North America, `EUR` for Europe\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| usageByApp | [microsoftAppsFileStorageContainerAppUsage](https://learn.microsoft.com/en-us/graph/api/resources/microsoftappsfilestoragecontainerappusage?view=graph-rest-beta) collection | Storage usage data broken down by application within this geographic location. Expandable using `$expand=usageByApp`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerGeoUsage",
  "dataLocationCode": "String (identifier)",
  "activeStorageUsedInBytes": "Int64",
  "activeContainerCount": "Int64",
  "usageByApp": [{"@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerAppUsage"}]
}
```
