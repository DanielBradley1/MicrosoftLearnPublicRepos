<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceAppManagementTask resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A device app management task.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAppManagementTasks](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-deviceappmanagementtask-list?view=graph-rest-beta) | [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) collection | List properties and relationships of the [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) objects. |
| [Get deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-deviceappmanagementtask-get?view=graph-rest-beta) | [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) | Read properties and relationships of the [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) object. |
| [Create deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-deviceappmanagementtask-create?view=graph-rest-beta) | [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) | Create a new [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) object. |
| [Delete deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-deviceappmanagementtask-delete?view=graph-rest-beta) | None | Deletes a [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). |
| [Update deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-deviceappmanagementtask-update?view=graph-rest-beta) | [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) | Update the properties of a [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) object. |
| [updateStatus action](https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-deviceappmanagementtask-updatestatus?view=graph-rest-beta) | None | Set the task's status and attach a note. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The entity key. |
| displayName | String | The name. |
| description | String | The description. |
| createdDateTime | DateTimeOffset | The created date. |
| dueDateTime | DateTimeOffset | The due date. |
| category | [deviceAppManagementTaskCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskcategory?view=graph-rest-beta) | The category. Possible values are: `unknown`, `advancedThreatProtection`. |
| priority | [deviceAppManagementTaskPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskpriority?view=graph-rest-beta) | The priority. Possible values are: `none`, `high`, `low`. |
| creator | String | The email address of the creator. |
| creatorNotes | String | Notes from the creator. |
| assignedTo | String | The name or email of the admin this task is assigned to. |
| status | [deviceAppManagementTaskStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskstatus?view=graph-rest-beta) | The status. Possible values are: `unknown`, `pending`, `active`, `completed`, `rejected`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAppManagementTask",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "dueDateTime": "String (timestamp)",
  "category": "String",
  "priority": "String",
  "creator": "String",
  "creatorNotes": "String",
  "assignedTo": "String",
  "status": "String"
}
```
