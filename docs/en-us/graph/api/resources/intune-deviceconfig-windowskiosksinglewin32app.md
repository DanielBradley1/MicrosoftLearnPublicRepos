<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskiosksinglewin32app?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsKioskSingleWin32App resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The class used to identify the single app configuration for the kiosk win32 configuration

Inherits from [windowsKioskAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappconfiguration?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| win32App | [windowsKioskWin32App](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskwin32app?view=graph-rest-beta) | This is the win32 app that will be available to launch use while in Kiosk Mode |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskSingleWin32App",
  "win32App": {
    "@odata.type": "microsoft.graph.windowsKioskWin32App",
    "startLayoutTileSize": "String",
    "name": "String",
    "appType": "String",
    "autoLaunch": true,
    "classicAppPath": "String",
    "edgeNoFirstRun": true,
    "edgeKioskIdleTimeoutMinutes": 1024,
    "edgeKioskType": "String",
    "edgeKiosk": "String"
  }
}
```
