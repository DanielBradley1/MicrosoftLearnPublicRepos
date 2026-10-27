<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deviceprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# deviceProfile resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents read-only profile and Windows servicing information for a device managed by Windows Autopatch.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List deviceProfiles](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-deviceprofiles?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deviceProfile](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deviceprofile?view=graph-rest-beta) collection | List device profiles and their Windows servicing information. |
| [Get device profile](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deviceprofile-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deviceProfile](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deviceprofile?view=graph-rest-beta) | Read the properties of a device profile. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureAdDeviceId | String | The Microsoft Entra device identifier. Read-only. |
| deviceModel | String | The hardware model of the device. Read-only. |
| deviceName | String | The device name. Read-only. |
| hotpatchReadiness | [windowsUpdates.hotpatchReadiness](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#hotpatchreadiness-values) | The device's readiness for hotpatch updates. The possible values are: `ready`, `notReady`, `unknownFutureValue`. Read-only. |
| id | String | The unique identifier for the device profile. Read-only. |
| osBuild | String | The Windows build installed on the device. Read-only. |
| osStatus | [windowsUpdates.osStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#osstatus-values) | The servicing status of the device's Windows version. The possible values are: `endOfServicing`, `inServicing`, `nearEndOfServicing`, `unknownFutureValue`. Read-only. |
| osVersion | String | The Windows version installed on the device. Read-only. |
| serialNumber | String | The device serial number. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.deviceProfile",
  "azureAdDeviceId": "String",
  "deviceModel": "String",
  "deviceName": "String",
  "hotpatchReadiness": "String",
  "id": "String (identifier)",
  "osBuild": "String",
  "osStatus": "String",
  "osVersion": "String",
  "serialNumber": "String"
}
```
