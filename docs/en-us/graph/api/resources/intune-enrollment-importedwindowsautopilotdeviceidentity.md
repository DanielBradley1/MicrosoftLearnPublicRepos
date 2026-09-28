<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# importedWindowsAutopilotDeviceIdentity resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Imported windows autopilot devices.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List importedWindowsAutopilotDeviceIdentities](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedwindowsautopilotdeviceidentity-list?view=graph-rest-1.0) | [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0) collection | List properties and relationships of the [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0) objects. |
| [Get importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedwindowsautopilotdeviceidentity-get?view=graph-rest-1.0) | [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0) | Read properties and relationships of the [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0) object. |
| [Create importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedwindowsautopilotdeviceidentity-create?view=graph-rest-1.0) | [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0) | Create a new [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0) object. |
| [Delete importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedwindowsautopilotdeviceidentity-delete?view=graph-rest-1.0) | None | Deletes a [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0). |
| [import action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-importedwindowsautopilotdeviceidentity-import?view=graph-rest-1.0) | [importedWindowsAutopilotDeviceIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentity?view=graph-rest-1.0) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |
| groupTag | String | Group Tag of the Windows autopilot device. |
| serialNumber | String | Serial number of the Windows autopilot device. |
| productKey | String | Product Key of the Windows autopilot device. |
| importId | String | The Import Id of the Windows autopilot device. |
| hardwareIdentifier | Binary | Hardware Blob of the Windows autopilot device. |
| state | [importedWindowsAutopilotDeviceIdentityState](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentitystate?view=graph-rest-1.0) | Current state of the imported device. |
| assignedUserPrincipalName | String | UPN of the user the device will be assigned |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.importedWindowsAutopilotDeviceIdentity",
  "id": "String (identifier)",
  "groupTag": "String",
  "serialNumber": "String",
  "productKey": "String",
  "importId": "String",
  "hardwareIdentifier": "binary",
  "state": {
    "@odata.type": "microsoft.graph.importedWindowsAutopilotDeviceIdentityState",
    "deviceImportStatus": "String",
    "deviceRegistrationId": "String",
    "deviceErrorCode": 1024,
    "deviceErrorName": "String"
  },
  "assignedUserPrincipalName": "String"
}
```
