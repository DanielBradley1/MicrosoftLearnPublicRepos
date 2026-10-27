<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# mdmAppSetting resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings for an MDM application within the current tenant.

Access these resources through the **mdmAppSettings** relationship of [tenantSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-tenantsetting?view=graph-rest-beta). The **mdmAppId** property is the resource key and must be a nonempty GUID-formatted string. This resource supports list, create, get, and update operations.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List mdmAppSettings](https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-list-mdmappsettings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) collection | Get a list of the mdmAppSetting objects and their properties. |
| [Create MDM app setting](https://learn.microsoft.com/en-us/graph/api/windowsupdates-tenantsetting-post-mdmappsettings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) | Create a new mdmAppSetting object. |
| [Get MDM app setting](https://learn.microsoft.com/en-us/graph/api/windowsupdates-mdmappsetting-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) | Read the properties and relationships of [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) object. |
| [Update MDM app setting](https://learn.microsoft.com/en-us/graph/api/windowsupdates-mdmappsetting-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.mdmAppSetting](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-mdmappsetting?view=graph-rest-beta) | Update the properties of a mdmAppSetting object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isHotpatchEnabled | Boolean | Whether hotpatch is enabled for this MDM application. The default is `true`. |
| mdmAppId | String | The unique identifier of the MDM application as a GUID-formatted string. This property is the resource key and can't be updated. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.mdmAppSetting",
  "mdmAppId": "String (identifier)",
  "isHotpatchEnabled": "Boolean"
}
```
