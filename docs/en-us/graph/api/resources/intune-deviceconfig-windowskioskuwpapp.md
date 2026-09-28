<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskuwpapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# windowsKioskUWPApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The base class for a type of apps

Inherits from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| startLayoutTileSize | [windowsAppStartLayoutTileSize](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsappstartlayouttilesize?view=graph-rest-beta) | The app tile size for the start layout Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta). Possible values are: `hidden`, `small`, `medium`, `wide`, `large`. |
| name | String | Represents the friendly name of an app Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta) |
| appType | [windowsKioskAppType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskapptype?view=graph-rest-beta) | The app type Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta). Possible values are: `unknown`, `store`, `desktop`, `aumId`. |
| autoLaunch | Boolean | Allow the app to be auto-launched in multi-app kiosk mode Inherited from [windowsKioskAppBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappbase?view=graph-rest-beta) |
| appUserModelId | String | This is the only Application User Model ID \(AUMID\) that will be available to launch use while in Kiosk Mode |
| appId | String | This references an Intune App that will be target to the same assignments as Kiosk configuration |
| containedAppId | String | This references an contained App from an Intune App |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskUWPApp",
  "startLayoutTileSize": "String",
  "name": "String",
  "appType": "String",
  "autoLaunch": true,
  "appUserModelId": "String",
  "appId": "String",
  "containedAppId": "String"
}
```
