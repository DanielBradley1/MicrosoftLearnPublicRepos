<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatereport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# driverUpdateReport resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a driver update available in a tenant, aggregated across Windows Autopatch driver update policies. Use the **deviceStatuses** relationship to inspect the latest rollout status for affected devices.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List drivers](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatedata-list-drivers?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.driverUpdateReport](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatereport?view=graph-rest-beta) collection | List driver updates available in the tenant. |
| [Get driver update report](https://learn.microsoft.com/en-us/graph/api/windowsupdates-driverupdatereport-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.driverUpdateReport](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatereport?view=graph-rest-beta) | Read a driver update report. |
| [List deviceStatuses](https://learn.microsoft.com/en-us/graph/api/windowsupdates-driverupdatereport-list-devicestatuses?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.driverUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatedevicestatus?view=graph-rest-beta) collection | List per-device rollout statuses for the driver update. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| class | String | The device class targeted by the driver update. Read-only. |
| displayName | String | The display name of the driver update. Read-only. |
| id | String | The catalog entry identifier of the driver update. Read-only. |
| manufacturer | String | The manufacturer of the driver update. Read-only. |
| releaseDateTime | DateTimeOffset | The date and time when the driver update was released. Read-only. |
| version | String | The driver version. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceStatuses | [microsoft.graph.windowsUpdates.driverUpdateDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatedevicestatus?view=graph-rest-beta) collection | The latest rollout statuses for devices associated with the driver update. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateReport",
  "class": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "manufacturer": "String",
  "releaseDateTime": "String (timestamp)",
  "version": "String"
}
```
