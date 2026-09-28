<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementScriptAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign a device management script to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementScriptAssignments](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptassignment-list?view=graph-rest-beta) | [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) objects. |
| [Get deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptassignment-get?view=graph-rest-beta) | [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) object. |
| [Create deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptassignment-create?view=graph-rest-beta) | [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) | Create a new [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) object. |
| [Delete deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta). |
| [Update deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptassignment-update?view=graph-rest-beta) | [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) | Update the properties of a [deviceManagementScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device management script group assignment entity. This property is read-only. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The Id of the Azure Active Directory group we are targeting the script to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementScriptAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
