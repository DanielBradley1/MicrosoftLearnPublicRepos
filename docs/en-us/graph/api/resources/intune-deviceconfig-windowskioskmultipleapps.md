<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskmultipleapps?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsKioskMultipleApps resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The class used to identify the MultiMode app configuration for the kiosk configuration

Inherits from [windowsKioskAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappconfiguration?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| apps | [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta) collection | These are the only Windows Store Apps that will be available to launch from the Start menu. This collection can contain a maximum of 128 elements. |
| showTaskBar | Boolean | This setting allows the admin to specify whether the Task Bar is shown or not. |
| allowAccessToDownloadsFolder | Boolean | This setting allows access to Downloads folder in file explorer. |
| disallowDesktopApps | Boolean | This setting indicates that desktop apps are allowed. Default to true. |
| startMenuLayoutXml | Binary | Allows admins to override the default Start layout and prevents the user from changing it. The layout is modified by specifying an XML file based on a layout modification schema. XML needs to be in Binary format. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskMultipleApps",
  "apps": [
    {
      "@odata.type": "microsoft.graph.windowsKioskUWPApp",
      "startLayoutTileSize": "String",
      "name": "String",
      "appType": "String",
      "autoLaunch": true,
      "appUserModelId": "String",
      "appId": "String",
      "containedAppId": "String"
    }
  ],
  "showTaskBar": true,
  "allowAccessToDownloadsFolder": true,
  "disallowDesktopApps": true,
  "startMenuLayoutXml": "binary"
}
```
