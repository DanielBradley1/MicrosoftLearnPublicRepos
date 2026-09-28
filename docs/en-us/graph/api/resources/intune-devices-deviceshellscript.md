<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceShellScript resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Intune will provide customer the ability to run their Shell scripts on the enrolled Mac OS devices. The script can be run once or periodically.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceShellScripts](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceshellscript-list?view=graph-rest-beta) | [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) collection | List properties and relationships of the [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) objects. |
| [Get deviceShellScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceshellscript-get?view=graph-rest-beta) | [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) | Read properties and relationships of the [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) object. |
| [Create deviceShellScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceshellscript-create?view=graph-rest-beta) | [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) | Create a new [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) object. |
| [Delete deviceShellScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceshellscript-delete?view=graph-rest-beta) | None | Deletes a [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta). |
| [Update deviceShellScript](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceshellscript-update?view=graph-rest-beta) | [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) | Update the properties of a [deviceShellScript](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceshellscript?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-devices-deviceshellscript-assign?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| executionFrequency | Duration | The interval for script to run. If not defined the script will run once |
| retryCount | Int32 | Number of times for the script to be retried if it fails |
| blockExecutionNotifications | Boolean | Does not notify the user a script is being executed |
| id | String | Unique Identifier for the device management script. |
| displayName | String | Name of the device management script. |
| description | String | Optional description for the device management script. |
| scriptContent | Binary | The script content. |
| createdDateTime | DateTimeOffset | The date and time the device management script was created. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time the device management script was last modified. This property is read-only. |
| runAsAccount | [runAsAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runasaccounttype?view=graph-rest-beta) | Indicates the type of execution context. Possible values are: `system`, `user`. |
| fileName | String | Script file name. |
| roleScopeTagIds | String collection | List of Scope Tag IDs for this PowerShellScript instance. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groupAssignments | [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) collection | The list of group assignments for the device management script. |
| assignments | [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) collection | The list of group assignments for the device management script. |
| runSummary | [deviceManagementScriptRunSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptrunsummary?view=graph-rest-beta) | Run summary for device management script. |
| deviceRunStates | [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) collection | List of run states for this script across all devices. |
| userRunStates | [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) collection | List of run states for this script across all users. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceShellScript",
  "executionFrequency": "String (duration)",
  "retryCount": 1024,
  "blockExecutionNotifications": true,
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "scriptContent": "binary",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "runAsAccount": "String",
  "fileName": "String",
  "roleScopeTagIds": [
    "String"
  ]
}
```
