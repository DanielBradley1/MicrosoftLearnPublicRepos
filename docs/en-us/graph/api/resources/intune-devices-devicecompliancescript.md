<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceScript resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Intune will provide customer the ability to run their Powershell Compliance scripts \(detection\) on the enrolled windows 10 Azure Active Directory joined devices.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceComplianceScripts](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescript-list?view=graph-rest-beta) | [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) collection | List properties and relationships of the [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) objects. |
| [Get deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescript-get?view=graph-rest-beta) | [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) | Read properties and relationships of the [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) object. |
| [Create deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescript-create?view=graph-rest-beta) | [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) | Create a new [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) object. |
| [Delete deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescript-delete?view=graph-rest-beta) | None | Deletes a [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta). |
| [Update deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescript-update?view=graph-rest-beta) | [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) | Update the properties of a [deviceComplianceScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescript?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescript-assign?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique Identifier for the device compliance script |
| publisher | String | Name of the device compliance script publisher |
| version | String | Version of the device compliance script |
| displayName | String | Name of the device compliance script |
| description | String | Description of the device compliance script |
| detectionScriptContent | Binary | The entire content of the detection powershell script |
| createdDateTime | DateTimeOffset | The timestamp of when the device compliance script was created. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | The timestamp of when the device compliance script was modified. This property is read-only. |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runasaccounttype?view=graph-rest-beta) | Indicates the type of execution context. Possible values are: `system`, `user`. |
| enforceSignatureCheck | Boolean | Indicate whether the script signature needs be checked |
| runAs32Bit | Boolean | Indicate whether PowerShell script\(s\) should run as 32-bit |
| roleScopeTagIds | String collection | List of Scope Tag IDs for the device compliance script |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) collection | The list of group assignments for the device compliance script |
| runSummary | [deviceComplianceScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptrunsummary?view=graph-rest-beta) | High level run summary for device compliance script. |
| deviceRunStates | [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) collection | List of run states for the device compliance script across all devices |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceScript",
  "id": "String (identifier)",
  "publisher": "String",
  "version": "String",
  "displayName": "String",
  "description": "String",
  "detectionScriptContent": "binary",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "runAsAccount": "String",
  "enforceSignatureCheck": true,
  "runAs32Bit": true,
  "roleScopeTagIds": [
    "String"
  ]
}
```
