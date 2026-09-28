<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deletedwindowsautopilotdevicestate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# deletedWindowsAutopilotDeviceState resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| serialNumber | String | Autopilot Device Serial Number |
| deviceRegistrationId | String | ZTD Device Registration ID . |
| deletionState | [windowsAutopilotDeviceDeletionState](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdevicedeletionstate?view=graph-rest-1.0) | Device deletion state. The possible values are: `unknown`, `failed`, `accepted`, `error`. |
| errorMessage | String | Device deletion error message. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deletedWindowsAutopilotDeviceState",
  "serialNumber": "String",
  "deviceRegistrationId": "String",
  "deletionState": "String",
  "errorMessage": "String"
}
```
