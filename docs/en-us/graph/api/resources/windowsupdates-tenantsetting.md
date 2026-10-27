<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-tenantsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# tenantSetting resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents tenant-level settings for Windows Autopatch updates.

Access this singleton at `/admin/windows/updates/tenantSettings`; don't append a tenant ID. Use GET to read the settings and PATCH to update them. When no settings have been saved, the GET operation returns the default settings.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get tenant settings](https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.tenantSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-tenantsetting?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.windowsUpdates.tenantSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-tenantsetting?view=graph-rest-beta) object. |
| [Update tenant settings](https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.tenantSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-tenantsetting?view=graph-rest-beta) | Update the properties of a tenantSetting object. |
| [List mdmAppSettings](https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-list-mdmappsettings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) collection | Get the MDM application settings for the current tenant. |
| [Create MDM app setting](https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-post-mdmappsettings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) | Create a new mdmAppSetting object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| areDataProcessorServiceForWindowsFeaturesEnabled | Boolean | Whether Data Processor Service for Windows \(DPSW\) features are enabled for this tenant. The default is `false`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| mdmAppSettings | [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) collection | The per-MDM-application settings for the current tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.tenantSetting",
  "areDataProcessorServiceForWindowsFeaturesEnabled": "Boolean"
}
```
