<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementScriptUserState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for user run state of the device management script.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementScriptUserStates](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptuserstate-list?view=graph-rest-beta) | [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) objects. |
| [Get deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptuserstate-get?view=graph-rest-beta) | [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) object. |
| [Create deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptuserstate-create?view=graph-rest-beta) | [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) | Create a new [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) object. |
| [Delete deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptuserstate-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta). |
| [Update deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptuserstate-update?view=graph-rest-beta) | [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) | Update the properties of a [deviceManagementScriptUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptuserstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device management script user state entity. This property is read-only. |
| successDeviceCount | Int32 | Success device count for specific user. |
| errorDeviceCount | Int32 | Error device count for specific user. |
| userPrincipalName | String | User principle name of specific user. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deviceRunStates | [deviceManagementScriptDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptdevicestate?view=graph-rest-beta) collection | List of run states for this script across all devices of specific user. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementScriptUserState",
  "id": "String (identifier)",
  "successDeviceCount": 1024,
  "errorDeviceCount": 1024,
  "userPrincipalName": "String"
}
```
