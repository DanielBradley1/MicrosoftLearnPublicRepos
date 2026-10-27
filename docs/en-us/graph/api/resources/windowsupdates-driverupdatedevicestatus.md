<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatedevicestatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# driverUpdateDeviceStatus resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the latest rollout status of a driver update for a device in a Windows Autopatch ring.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List deviceStatuses](https://learn.microsoft.com/en-us/graph/api/windowsupdates-driverupdatereport-list-devicestatuses?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.driverUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatedevicestatus?view=graph-rest-beta) collection | List per-device rollout statuses for a driver update. |
| [Get driver update device status](https://learn.microsoft.com/en-us/graph/api/windowsupdates-driverupdatedevicestatus-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.driverUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatedevicestatus?view=graph-rest-beta) | Read a per-device driver update rollout status. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aadDeviceId | String | The Microsoft Entra identifier of the device. Read-only. |
| clientState | [windowsUpdates.deviceClientState](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#deviceclientstate-values) | The rollout state reported by the device. The possible values are: `offering`, `onHold`, `installing`, `installed`, `cancelled`, `uninstalling`, `uninstalled`, `notOffering`, `unknownFutureValue`. Read-only. |
| clientSubstate | [windowsUpdates.deviceClientSubstate](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#deviceclientsubstate-values) | The detailed rollout substate reported by the device. The possible values are: `deferred`, `offerReady`, `paused`, `offerReceived`, `downloadStart`, `downloadComplete`, `installStart`, `installComplete`, `restartRequired`, `restartInitiated`, `restartComplete`, `updateInstalled`, `rollbackComplete`, `userCancelled`, `deviceCancelled`, `uninstall`, `rollback`, `updateUninstalled`, `notSupported`, `previousUpdateInProgress`, `unknownFutureValue`. Read-only. |
| deviceName | String | The device name. Read-only. |
| id | String | The composite identifier for the driver update status. Read-only. |
| lastEventDateTime | DateTimeOffset | The date and time of the latest status event. Read-only. |
| policyId | String | The identifier of the driver update policy. Read-only. |
| policyName | String | The display name of the driver update policy. Read-only. |
| ringId | String | The identifier of the Windows Autopatch ring. Read-only. |
| ringName | String | The display name of the Windows Autopatch ring. Read-only. |
| serviceState | [windowsUpdates.deviceServiceState](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#deviceservicestate-values) | The rollout state maintained by the service. The possible values are: `unknown`, `pending`, `offering`, `onHold`, `cancelled`, `notOffering`, `unknownFutureValue`. Read-only. |
| serviceSubstate | [windowsUpdates.deviceServiceSubstate](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#deviceservicesubstate-values) | The detailed rollout substate maintained by the service. The possible values are: `unknown`, `scheduled`, `offerReady`, `adminPaused`, `adminCancelled`, `removedFromDeployment`, `notOffering`, `unknownFutureValue`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateDeviceStatus",
  "aadDeviceId": "String",
  "clientState": "String",
  "clientSubstate": "String",
  "deviceName": "String",
  "id": "String (identifier)",
  "lastEventDateTime": "String (timestamp)",
  "policyId": "String",
  "policyName": "String",
  "ringId": "String",
  "ringName": "String",
  "serviceState": "String",
  "serviceSubstate": "String"
}
```
