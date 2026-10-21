<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# task resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A Planner V4 task. `planId` routes the task back to its parent [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta). Unlike the V3 **plannerTask**/**plannerTaskDetails** split, a V4 task has no separate details object - description, notes, checklist, assignments, and links are properties and sub-collections directly on the task.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plan-list-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) collection | Get a list of the task objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/plan-post-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) | Create a new task object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/task-get?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) | Read the properties and relationships of [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/task-update?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) | Update the properties of a task object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plan-delete-tasks?view=graph-rest-beta) | None | Delete a task object. |
| [List checklist](https://learn.microsoft.com/en-us/graph/api/task-list-checklist?view=graph-rest-beta) | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) collection | Get a list of the checklistItemV4 objects and their properties. |
| [Create checklistItemV4](https://learn.microsoft.com/en-us/graph/api/task-post-checklist?view=graph-rest-beta) | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) | Create a new checklistItemV4 object. |
| [List customFieldValues](https://learn.microsoft.com/en-us/graph/api/task-list-customfieldvalues?view=graph-rest-beta) | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) collection | Get a list of the customFieldValue objects and their properties. |
| [Create customFieldValue](https://learn.microsoft.com/en-us/graph/api/task-post-customfieldvalues?view=graph-rest-beta) | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) | Create a new customFieldValue object. |
| [List links](https://learn.microsoft.com/en-us/graph/api/task-list-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) collection | Get a list of the contentLink objects and their properties. |
| [Create contentLink](https://learn.microsoft.com/en-us/graph/api/task-post-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) | Create a new contentLink object. |
| [List messages](https://learn.microsoft.com/en-us/graph/api/task-list-messages?view=graph-rest-beta) | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) collection | Get a list of the plannerChatMessage objects and their properties. |
| [Create plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/task-post-messages?view=graph-rest-beta) | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) | Create a new plannerChatMessage object. |
| [List userAssignments](https://learn.microsoft.com/en-us/graph/api/task-list-userassignments?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) collection | Get a list of the userAssignment objects and their properties. |
| [Create userAssignment](https://learn.microsoft.com/en-us/graph/api/task-post-userassignments?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) | Create a new userAssignment object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. |
| bucketId | String | ID of the bucket that the task belongs to. |
| capabilities | [taskCapability](https://learn.microsoft.com/en-us/graph/api/resources/taskcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| completedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who marked the task complete. |
| completedDateTime | DateTimeOffset | Date and time the task was completed. |
| creationInfo | [creationInfo](https://learn.microsoft.com/en-us/graph/api/resources/creationinfo?view=graph-rest-beta) | Read-only creation metadata for the entity. |
| displayName | String | Title of the task. |
| dueDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is due. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| finishDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task was finished. |
| goalIds | String collection | IDs of the goals that the task is associated with. |
| hasChat | Boolean | Indicates whether the task has an associated chat. |
| hasChildren | Boolean | Indicates whether the task has subtasks. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isCritical | Boolean | Indicates whether the task is on the critical path, as computed from its dependencies. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Additional details or notes about the task. |
| parentTaskId | String | ID of the parent task, if this task is a subtask. |
| percentComplete | Int32 | Percentage of the task's completion, ranging from 0 to 100. |
| personalView | [taskPersonalView](https://learn.microsoft.com/en-us/graph/api/resources/taskpersonalview?view=graph-rest-beta) | Per-user personal view settings for the task, such as My Day membership. |
| planId | String | ID of the plan that contains the task. Immutable after creation. |
| planView | [taskPlanView](https://learn.microsoft.com/en-us/graph/api/resources/taskplanview?view=graph-rest-beta) | Task view settings scoped to the plan, such as applied category IDs. |
| priority | Int32 | Priority of the task. Supported values range from 0 \(urgent\) to 10 \(low\). |
| recurrence | [plannerTaskRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskrecurrence?view=graph-rest-beta) | Recurrence pattern for the task, if it repeats. |
| startDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/resources/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is scheduled to start. |
| status | plannerTaskStatus | Indicates progress on the task. The possible values are: `notStarted`, `inProgress`, `completed`, `blocked`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| checklist | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/resources/checklistitemv4?view=graph-rest-beta) collection | The collection of checklist items on the task. Read-only. Nullable. |
| customFieldValues | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/resources/customfieldvalue?view=graph-rest-beta) collection | The collection of custom field values set on the task. Read-only. Nullable. |
| links | [contentLink](https://learn.microsoft.com/en-us/graph/api/resources/contentlink?view=graph-rest-beta) collection | The collection of content links attached to the task. Read-only. Nullable. |
| messages | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) collection | The collection of chat messages associated with the task. Read-only. Nullable. |
| userAssignments | [userAssignment](https://learn.microsoft.com/en-us/graph/api/resources/userassignment?view=graph-rest-beta) collection | The collection of user assignments on the task. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.task",
  "id": "String (identifier)",
  "displayName": "String",
  "planId": "String",
  "bucketId": "String",
  "goalIds": [
    "String"
  ],
  "status": "String",
  "priority": "Int32",
  "percentComplete": "Int32",
  "startDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime"
  },
  "dueDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime"
  },
  "finishDateTime": {
    "@odata.type": "microsoft.graph.dateWithOptionalTime"
  },
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "creationInfo": {
    "@odata.type": "microsoft.graph.creationInfo"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "completedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "completedDateTime": "String (timestamp)",
  "recurrence": {
    "@odata.type": "microsoft.graph.plannerTaskRecurrence"
  },
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "planView": {
    "@odata.type": "microsoft.graph.taskPlanView"
  },
  "personalView": {
    "@odata.type": "microsoft.graph.taskPersonalView"
  },
  "parentTaskId": "String",
  "hasChildren": "Boolean",
  "isCritical": "Boolean",
  "hasChat": "Boolean",
  "capabilities": {
    "@odata.type": "microsoft.graph.taskCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
