<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# windowsKioskAppBase resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The base class for a type of apps

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| startLayoutTileSize | [windowsAppStartLayoutTileSize](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsappstartlayouttilesize?view=graph-rest-beta) | The app tile size for the start layout. Possible values are: `hidden`, `small`, `medium`, `wide`, `large`. |
| name | String | Represents the friendly name of an app |
| appType | [windowsKioskAppType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskapptype?view=graph-rest-beta) | The app type. Possible values are: `unknown`, `store`, `desktop`, `aumId`. |
| autoLaunch | Boolean | Allow the app to be auto-launched in multi-app kiosk mode |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskAppBase",
  "startLayoutTileSize": "String",
  "name": "String",
  "appType": "String",
  "autoLaunch": true
}
```
