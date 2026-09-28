<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentitystate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# importedWindowsAutopilotDeviceIdentityState resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceImportStatus | [importedWindowsAutopilotDeviceIdentityImportStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importedwindowsautopilotdeviceidentityimportstatus?view=graph-rest-1.0) | Device status reported by Device Directory Service\(DDS\). The possible values are: `unknown`, `pending`, `partial`, `complete`, `error`. |
| deviceRegistrationId | String | Device Registration ID for successfully added device reported by Device Directory Service\(DDS\). |
| deviceErrorCode | Int32 | Device error code reported by Device Directory Service\(DDS\). |
| deviceErrorName | String | Device error name reported by Device Directory Service\(DDS\). |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.importedWindowsAutopilotDeviceIdentityState",
  "deviceImportStatus": "String",
  "deviceRegistrationId": "String",
  "deviceErrorCode": 1024,
  "deviceErrorName": "String"
}
```
