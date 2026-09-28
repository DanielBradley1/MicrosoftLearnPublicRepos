<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptdevicestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceHealthScriptDeviceState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for device run state of the device health script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceHealthScriptDeviceStates](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptdevicestate-list?view=graph-rest-beta) | [deviceHealthScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptdevicestate?view=graph-rest-beta) collection | List properties and relationships of the [deviceHealthScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptdevicestate?view=graph-rest-beta) objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device health script device state entity. This property is read-only. |
| detectionState | [runState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runstate?view=graph-rest-beta) | Detection state from the lastest device health script execution. The possible values are: `unknown`, `success`, `fail`, `scriptError`, `pending`, `notApplicable`. |
| lastStateUpdateDateTime | DateTimeOffset | The last timestamp of when the device health script executed |
| expectedStateUpdateDateTime | DateTimeOffset | The next timestamp of when the device health script is expected to execute |
| lastSyncDateTime | DateTimeOffset | The last time that Intune Managment Extension synced with Intune |
| preRemediationDetectionScriptOutput | String | Output of the detection script before remediation |
| preRemediationDetectionScriptError | String | Error from the detection script before remediation |
| remediationScriptError | String | Error output of the remediation script |
| postRemediationDetectionScriptOutput | String | Detection script output after remediation |
| postRemediationDetectionScriptError | String | Error from the detection script after remediation |
| remediationState | [remediationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remediationstate?view=graph-rest-beta) | Remediation state from the lastest device health script execution. The possible values are: `unknown`, `skipped`, `success`, `remediationFailed`, `scriptError`, `unknownFutureValue`. |
| assignmentFilterIds | String collection | A list of the assignment filter ids used for health script applicability evaluation |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedDevice | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) | The managed device on which the device health script executed |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceHealthScriptDeviceState",
  "id": "String (identifier)",
  "detectionState": "String",
  "lastStateUpdateDateTime": "String (timestamp)",
  "expectedStateUpdateDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "preRemediationDetectionScriptOutput": "String",
  "preRemediationDetectionScriptError": "String",
  "remediationScriptError": "String",
  "postRemediationDetectionScriptOutput": "String",
  "postRemediationDetectionScriptError": "String",
  "remediationState": "String",
  "assignmentFilterIds": [
    "String"
  ]
}
```
