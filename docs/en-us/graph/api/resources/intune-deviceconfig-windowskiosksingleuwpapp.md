<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskiosksingleuwpapp?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsKioskSingleUWPApp resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The class used to identify the UWP app info for the kiosk configuration

Inherits from [windowsKioskAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskappconfiguration?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| uwpApp | [windowsKioskUWPApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowskioskuwpapp?view=graph-rest-beta) | This is the only Application User Model ID \(AUMID\) that will be available to launch use while in Kiosk Mode |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsKioskSingleUWPApp",
  "uwpApp": {
    "@odata.type": "microsoft.graph.windowsKioskUWPApp",
    "startLayoutTileSize": "String",
    "name": "String",
    "appType": "String",
    "autoLaunch": true,
    "appUserModelId": "String",
    "appId": "String",
    "containedAppId": "String"
  }
}
```
