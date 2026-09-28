<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskwin32app?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# windowsKioskWin32App resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

KioskModeApp v4 for Win32 app support

Inherits from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| startLayoutTileSize | [windowsAppStartLayoutTileSize](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsappstartlayouttilesize?view=graph-rest-beta) | The app tile size for the start layout Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta). Possible values are: `hidden`, `small`, `medium`, `wide`, `large`. |
| name | String | Represents the friendly name of an app Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta) |
| appType | [windowsKioskAppType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskapptype?view=graph-rest-beta) | The app type Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta). Possible values are: `unknown`, `store`, `desktop`, `aumId`. |
| autoLaunch | Boolean | Allow the app to be auto-launched in multi-app kiosk mode Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta) |
| classicAppPath | String | This is the classicapppath to be used by v4 Win32 app while in Kiosk Mode |
| edgeNoFirstRun | Boolean | Edge first run flag for Edge kiosk mode |
| edgeKioskIdleTimeoutMinutes | Int32 | Edge kiosk idle timeout in minutes for Edge kiosk mode. Valid values 0 to 1440 |
| edgeKioskType | [windowsEdgeKioskType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsedgekiosktype?view=graph-rest-beta) | Edge kiosk type for Edge kiosk mode. Possible values are: `publicBrowsing`, `fullScreen`. |
| edgeKiosk | String | Edge kiosk \(url\) for Edge kiosk mode |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskWin32App",
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
```
