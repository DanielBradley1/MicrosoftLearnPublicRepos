<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementScriptGroupAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign a device management script to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementScriptGroupAssignments](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptgroupassignment-list?view=graph-rest-beta) | [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) objects. |
| [Get deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptgroupassignment-get?view=graph-rest-beta) | [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) object. |
| [Create deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptgroupassignment-create?view=graph-rest-beta) | [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) | Create a new [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) object. |
| [Delete deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptgroupassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta). |
| [Update deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicemanagementscriptgroupassignment-update?view=graph-rest-beta) | [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) | Update the properties of a [deviceManagementScriptGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicemanagementscriptgroupassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device management script group assignment entity. This property is read-only. |
| targetGroupId | String | The Id of the Azure Active Directory group we are targeting the script to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementScriptGroupAssignment",
  "id": "String (identifier)",
  "targetGroupId": "String"
}
```
