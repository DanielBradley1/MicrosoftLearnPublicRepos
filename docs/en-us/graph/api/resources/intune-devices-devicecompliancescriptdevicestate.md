<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceComplianceScriptDeviceState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for device run state of the device compliance script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceComplianceScriptDeviceStates](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescriptdevicestate-list?view=graph-rest-beta) | [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) collection | List properties and relationships of the [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) objects. |
| [Get deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescriptdevicestate-get?view=graph-rest-beta) | [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) | Read properties and relationships of the [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) object. |
| [Create deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescriptdevicestate-create?view=graph-rest-beta) | [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) | Create a new [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) object. |
| [Delete deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescriptdevicestate-delete?view=graph-rest-beta) | None | Deletes a [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta). |
| [Update deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicecompliancescriptdevicestate-update?view=graph-rest-beta) | [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) | Update the properties of a [deviceComplianceScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicecompliancescriptdevicestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device compliance script device state entity. This property is read-only. |
| detectionState | [runState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runstate?view=graph-rest-beta) | Detection state from the lastest device compliance script execution. Possible values are: `unknown`, `success`, `fail`, `scriptError`, `pending`, `notApplicable`. |
| lastStateUpdateDateTime | DateTimeOffset | The last timestamp of when the device compliance script executed |
| expectedStateUpdateDateTime | DateTimeOffset | The next timestamp of when the device compliance script is expected to execute |
| lastSyncDateTime | DateTimeOffset | The last time that Intune Managment Extension synced with Intune |
| scriptOutput | String | Output of the detection script |
| scriptError | String | Error from the detection script |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedDevice | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) | The managed device on which the device compliance script executed |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceComplianceScriptDeviceState",
  "id": "String (identifier)",
  "detectionState": "String",
  "lastStateUpdateDateTime": "String (timestamp)",
  "expectedStateUpdateDateTime": "String (timestamp)",
  "lastSyncDateTime": "String (timestamp)",
  "scriptOutput": "String",
  "scriptError": "String"
}
```
