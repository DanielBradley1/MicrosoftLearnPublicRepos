<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceHealthScriptAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties used to assign a device management script to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceHealthScriptAssignments](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptassignment-list?view=graph-rest-beta) | [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) objects. |
| [Get deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptassignment-get?view=graph-rest-beta) | [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) object. |
| [Create deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptassignment-create?view=graph-rest-beta) | [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) | Create a new [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) object. |
| [Delete deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta). |
| [Update deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/intune-devices-devicehealthscriptassignment-update?view=graph-rest-beta) | [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) | Update the properties of a [deviceHealthScriptAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the device health script assignment entity. This property is read-only. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The Azure Active Directory group we are targeting the script to |
| runRemediationScript | Boolean | Determine whether we want to run detection script only or run both detection script and remediation script |
| runSchedule | [deviceHealthScriptRunSchedule](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicehealthscriptrunschedule?view=graph-rest-beta) | Script run schedule for the target group |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceHealthScriptAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.configurationManagerCollectionAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "collectionId": "String"
  },
  "runRemediationScript": true,
  "runSchedule": {
    "@odata.type": "microsoft.graph.deviceHealthScriptDailySchedule",
    "interval": 1024,
    "useUtc": true,
    "time": "String (time of day)"
  }
}
```
