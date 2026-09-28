<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementScriptDeviceState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for device run state of the device management script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementScriptDeviceStates](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptdevicestate-list?view=graph-rest-beta) | [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) objects. |
| [Get deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptdevicestate-get?view=graph-rest-beta) | [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) object. |
| [Create deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptdevicestate-create?view=graph-rest-beta) | [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) | Create a new [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) object. |
| [Delete deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptdevicestate-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta). |
| [Update deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptdevicestate-update?view=graph-rest-beta) | [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) | Update the properties of a [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device management script device state entity. This property is read-only. |
| runState | [runState](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runstate?view=graph-rest-beta) | State of latest run of the device management script. Possible values are: `unknown`, `success`, `fail`, `scriptError`, `pending`, `notApplicable`. |
| resultMessage | String | Details of execution output. |
| lastStateUpdateDateTime | DateTimeOffset | Latest time the device management script executes. |
| errorCode | Int32 | Error code corresponding to erroneous execution of the device management script. |
| errorDescription | String | Error description corresponding to erroneous execution of the device management script. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| managedDevice | [managedDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-manageddevice?view=graph-rest-beta) | The managed devices that executes the device management script. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementScriptDeviceState",
  "id": "String (identifier)",
  "runState": "String",
  "resultMessage": "String",
  "lastStateUpdateDateTime": "String (timestamp)",
  "errorCode": 1024,
  "errorDescription": "String"
}
```
