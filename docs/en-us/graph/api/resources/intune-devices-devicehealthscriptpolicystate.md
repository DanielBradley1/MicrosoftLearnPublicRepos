<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceHealthScriptPolicyState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for policy run state of the device health script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceHealthScriptPolicyStates](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptpolicystate-list?view=graph-rest-beta) | [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) collection | List properties and relationships of the [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) objects. |
| [Get deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptpolicystate-get?view=graph-rest-beta) | [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) | Read properties and relationships of the [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) object. |
| [Create deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptpolicystate-create?view=graph-rest-beta) | [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) | Create a new [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) object. |
| [Delete deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptpolicystate-delete?view=graph-rest-beta) | None | Deletes a [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta). |
| [Update deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptpolicystate-update?view=graph-rest-beta) | [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) | Update the properties of a [deviceHealthScriptPolicyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptpolicystate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device health script policy state is a concatenation of the MT sideCar policy Id and Intune device Id |
| deviceId | String | The Intune device Id |
| policyId | String | The MT sideCar policy Id |
| deviceName | String | Display name of the device |
| policyName | String | Display name of the device health script |
| userName | String | Name of the user whom ran the device health script |
| osVersion | String | Value of the OS Version in string |
| detectionState | [runState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runstate?view=graph-rest-beta) | Detection state from the lastest device health script execution. Possible values are: `unknown`, `success`, `fail`, `scriptError`, `pending`, `notApplicable`. |
| lastStateUpdateDateTime | DateTimeOffset | The last timestamp of when the device health script executed |
| expectedStateUpdateDateTime | DateTimeOffset | The next timestamp of when the device health script is expected to execute |
| lastSyncDateTime | DateTimeOffset | The last time that Intune Managment Extension synced with Intune |
| preRemediationDetectionScriptOutput | String | Output of the detection script before remediation |
| preRemediationDetectionScriptError | String | Error from the detection script before remediation |
| remediationScriptError | String | Error output of the remediation script |
| postRemediationDetectionScriptOutput | String | Detection script output after remediation |
| postRemediationDetectionScriptError | String | Error from the detection script after remediation |
| remediationState | [remediationState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-remediationstate?view=graph-rest-beta) | Remediation state from the lastest device health script execution. Possible values are: `unknown`, `skipped`, `success`, `remediationFailed`, `scriptError`, `unknownFutureValue`. |
| assignmentFilterIds | String collection | A list of the assignment filter ids used for health script applicability evaluation |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceHealthScriptPolicyState",
  "id": "String (identifier)",
  "deviceId": "String",
  "policyId": "String",
  "deviceName": "String",
  "policyName": "String",
  "userName": "String",
  "osVersion": "String",
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
