<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerkioskmodeweblink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidDeviceOwnerKioskModeWeblink resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A weblink on the Android Device Owner Managed Home Screen

Inherits from [androidDeviceOwnerKioskModeFolderItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerkioskmodefolderitem?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | Display name for weblink |
| link | String | Link for weblink |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidDeviceOwnerKioskModeWeblink",
  "label": "String",
  "link": "String"
}
```
