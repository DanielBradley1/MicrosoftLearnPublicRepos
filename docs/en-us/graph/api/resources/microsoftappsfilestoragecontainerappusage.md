<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftappsfilestoragecontainerappusage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# microsoftAppsFileStorageContainerAppUsage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents app-level storage usage data for SharePoint Embedded file storage containers.

This resource provides metrics for a specific application within a geographic location, including the app identifier, display name, storage used, and container count.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeContainerCount | Int64 | The number of active file storage containers for this application. |
| activeStorageUsedInBytes | Int64 | The storage used in bytes for active file storage containers for this application. |
| appId | String | The unique identifier \(GUID\) of the Microsoft application. |
| displayName | String | The display name of the Microsoft application \(for example, `Loop`, `Designer`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.microsoftAppsFileStorageContainerAppUsage",
  "appId": "String (identifier)",
  "displayName": "String",
  "activeStorageUsedInBytes": "Int64",
  "activeContainerCount": "Int64"
}
```
