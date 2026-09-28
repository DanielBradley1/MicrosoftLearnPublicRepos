<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# windowsAutopilotDeviceIdentity resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The windowsAutopilotDeviceIdentity resource represents a Windows Autopilot Device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsAutopilotDeviceIdentities](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-list?view=graph-rest-1.0) | [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0) collection | List properties and relationships of the [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0) objects. |
| [Get windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-get?view=graph-rest-1.0) | [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0) | Read properties and relationships of the [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0) object. |
| [Create windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-create?view=graph-rest-1.0) | [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0) | Create a new [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0) object. |
| [Delete windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-delete?view=graph-rest-1.0) | None | Deletes a [windowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeviceidentity?view=graph-rest-1.0). |
| [assignUserToDevice action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-assignusertodevice?view=graph-rest-1.0) | None | Assigns user to Autopilot devices. |
| [unassignUserFromDevice action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-unassignuserfromdevice?view=graph-rest-1.0) | None | Unassigns the user from an Autopilot device. |
| [updateDeviceProperties action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-updatedeviceproperties?view=graph-rest-1.0) | None | Updates properties on Autopilot devices. |
| [deleteDevices action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeviceidentity-deletedevices?view=graph-rest-1.0) | [deletedWindowsAutopilotDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deletedwindowsautopilotdevicestate?view=graph-rest-1.0) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |
| groupTag | String | Group Tag of the Windows autopilot device. |
| purchaseOrderIdentifier | String | Purchase Order Identifier of the Windows autopilot device. |
| serialNumber | String | Serial number of the Windows autopilot device. |
| productKey | String | Product Key of the Windows autopilot device. |
| manufacturer | String | Oem manufacturer of the Windows autopilot device. |
| model | String | Model name of the Windows autopilot device. |
| enrollmentState | [enrollmentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentstate?view=graph-rest-1.0) | Intune enrollment state of the Windows autopilot device. The possible values are: `unknown`, `enrolled`, `pendingReset`, `failed`, `notContacted`. |
| lastContactedDateTime | DateTimeOffset | Intune Last Contacted Date Time of the Windows autopilot device. |
| addressableUserName | String | Addressable user name. |
| userPrincipalName | String | User Principal Name. |
| resourceName | String | Resource Name. |
| skuNumber | String | SKU Number |
| systemFamily | String | System Family |
| azureActiveDirectoryDeviceId | String | AAD Device ID - to be deprecated |
| managedDeviceId | String | Managed Device ID |
| displayName | String | Display Name |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsAutopilotDeviceIdentity",
  "id": "String (identifier)",
  "groupTag": "String",
  "purchaseOrderIdentifier": "String",
  "serialNumber": "String",
  "productKey": "String",
  "manufacturer": "String",
  "model": "String",
  "enrollmentState": "String",
  "lastContactedDateTime": "String (timestamp)",
  "addressableUserName": "String",
  "userPrincipalName": "String",
  "resourceName": "String",
  "skuNumber": "String",
  "systemFamily": "String",
  "azureActiveDirectoryDeviceId": "String",
  "managedDeviceId": "String",
  "displayName": "String"
}
```
