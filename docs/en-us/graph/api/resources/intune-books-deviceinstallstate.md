<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceInstallState resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the installation state for a device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceInstallStates](https://learn.microsoft.com/en-us/graph/api/intune-books-deviceinstallstate-list?view=graph-rest-1.0) | [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) collection | List properties and relationships of the [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) objects. |
| [Get deviceInstallState](https://learn.microsoft.com/en-us/graph/api/intune-books-deviceinstallstate-get?view=graph-rest-1.0) | [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) | Read properties and relationships of the [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) object. |
| [Create deviceInstallState](https://learn.microsoft.com/en-us/graph/api/intune-books-deviceinstallstate-create?view=graph-rest-1.0) | [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) | Create a new [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) object. |
| [Delete deviceInstallState](https://learn.microsoft.com/en-us/graph/api/intune-books-deviceinstallstate-delete?view=graph-rest-1.0) | None | Deletes a [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0). |
| [Update deviceInstallState](https://learn.microsoft.com/en-us/graph/api/intune-books-deviceinstallstate-update?view=graph-rest-1.0) | [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) | Update the properties of a [deviceInstallState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-deviceinstallstate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| deviceName | String | Device name. |
| deviceId | String | Device Id. |
| lastSyncDateTime | DateTimeOffset | Last sync date and time. |
| installState | [installState](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-installstate?view=graph-rest-1.0) | The install state of the eBook. The possible values are: `notApplicable`, `installed`, `failed`, `notInstalled`, `uninstallFailed`, `unknown`. |
| errorCode | String | The error code for install failures. |
| osVersion | String | OS Version. |
| osDescription | String | OS Description. |
| userName | String | Device User Name. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceInstallState",
  "id": "String (identifier)",
  "deviceName": "String",
  "deviceId": "String",
  "lastSyncDateTime": "String (timestamp)",
  "installState": "String",
  "errorCode": "String",
  "osVersion": "String",
  "osDescription": "String",
  "userName": "String"
}
```
