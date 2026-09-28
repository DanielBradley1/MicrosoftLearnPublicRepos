<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceHealthScript resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Intune will provide customer the ability to run their Powershell Health scripts \(remediation + detection\) on the enrolled windows 10 Azure Active Directory joined devices.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceHealthScripts](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-list?view=graph-rest-beta) | [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) collection | List properties and relationships of the [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) objects. |
| [Get deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-get?view=graph-rest-beta) | [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) | Read properties and relationships of the [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) object. |
| [Create deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-create?view=graph-rest-beta) | [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) | Create a new [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) object. |
| [Delete deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-delete?view=graph-rest-beta) | None | Deletes a [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta). |
| [Update deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-update?view=graph-rest-beta) | [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) | Update the properties of a [deviceHealthScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscript?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-assign?view=graph-rest-beta) | None |  |
| [updateGlobalScript action](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-updateglobalscript?view=graph-rest-beta) | String | Update the Proprietary Device Health Script |
| [getGlobalScriptHighestAvailableVersion action](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-getglobalscripthighestavailableversion?view=graph-rest-beta) | String | Update the Proprietary Device Health Script |
| [enableGlobalScripts action](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-enableglobalscripts?view=graph-rest-beta) | None |  |
| [areGlobalScriptsAvailable function](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-areglobalscriptsavailable?view=graph-rest-beta) | [globalDeviceHealthScriptState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-globaldevicehealthscriptstate?view=graph-rest-beta) |  |
| [getRemediationSummary function](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-getremediationsummary?view=graph-rest-beta) | [deviceHealthScriptRemediationSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptremediationsummary?view=graph-rest-beta) |  |
| [getRemediationHistory function](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscript-getremediationhistory?view=graph-rest-beta) | [deviceHealthScriptRemediationHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptremediationhistory?view=graph-rest-beta) | Function to get the number of remediations by a device health scripts |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the device health script |
| publisher | String | Name of the device health script publisher |
| version | String | Version of the device health script |
| displayName | String | Name of the device health script |
| description | String | Description of the device health script |
| detectionScriptContent | Binary | The entire content of the detection powershell script |
| remediationScriptContent | Binary | The entire content of the remediation powershell script |
| createdDateTime | DateTimeOffset | The timestamp of when the device health script was created. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | The timestamp of when the device health script was modified. This property is read-only. |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runasaccounttype?view=graph-rest-beta) | Indicates the type of execution context. Possible values are: `system`, `user`. |
| enforceSignatureCheck | Boolean | Indicate whether the script signature needs be checked |
| runAs32Bit | Boolean | Indicate whether PowerShell script\(s\) should run as 32-bit |
| roleScopeTagIds | String collection | List of Scope Tag IDs for the device health script |
| isGlobalScript | Boolean | Determines if this is Microsoft Proprietary Script. Proprietary scripts are read-only |
| highestAvailableVersion | String | Highest available version for a Microsoft Proprietary script |
| deviceHealthScriptType | [deviceHealthScriptType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscripttype?view=graph-rest-beta) | DeviceHealthScriptType for the script policy. Possible values are: `deviceHealthScript`, `managedInstallerScript`. |
| detectionScriptParameters | [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) collection | List of ComplexType DetectionScriptParameters objects. |
| remediationScriptParameters | [deviceHealthScriptParameter](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptparameter?view=graph-rest-beta) collection | List of ComplexType RemediationScriptParameters objects. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) collection | The list of group assignments for the device health script |
| runSummary | [deviceHealthScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptrunsummary?view=graph-rest-beta) | High level run summary for device health script. |
| deviceRunStates | [deviceHealthScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptdevicestate?view=graph-rest-beta) collection | List of run states for the device health script across all devices |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceHealthScript",
  "id": "String (identifier)",
  "publisher": "String",
  "version": "String",
  "displayName": "String",
  "description": "String",
  "detectionScriptContent": "binary",
  "remediationScriptContent": "binary",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "runAsAccount": "String",
  "enforceSignatureCheck": true,
  "runAs32Bit": true,
  "roleScopeTagIds": [
    "String"
  ],
  "isGlobalScript": true,
  "highestAvailableVersion": "String",
  "deviceHealthScriptType": "String",
  "detectionScriptParameters": [
    {
      "@odata.type": "microsoft.graph.deviceHealthScriptStringParameter",
      "name": "String",
      "description": "String",
      "isRequired": true,
      "applyDefaultValueWhenNotAssigned": true,
      "defaultValue": "String"
    }
  ],
  "remediationScriptParameters": [
    {
      "@odata.type": "microsoft.graph.deviceHealthScriptStringParameter",
      "name": "String",
      "description": "String",
      "isRequired": true,
      "applyDefaultValueWhenNotAssigned": true,
      "defaultValue": "String"
    }
  ]
}
```
