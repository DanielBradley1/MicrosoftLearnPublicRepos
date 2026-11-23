<!-- Source: https://learn.microsoft.com/en-us/graph/api/planneruser-delete-tasks_v2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# task resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A task in the Planner Unified plans Graph API. `planId` routes the task back to its parent [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta). Unlike the **plannerTask**/**plannerTaskDetails** split in the Planner Basic plans Graph API, a task in the Planner Unified plans Graph API has no separate details object - description, notes, checklist, assignments, and links are properties and sub-collections directly on the task.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/plannerdelta?view=graph-rest-beta).

Use the listed methods to create, read, update, and delete tasks. You can create supported related objects in the same request as a task by using a [deep insert](https://learn.microsoft.com/en-us/graph/planner-post-tasks_v2?view=graph-rest-beta). This doesn't imply standalone CRUD support for every related type, or that sending an array in a PATCH request replaces the collection.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/plan-list-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) collection | Get a list of the task objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/planner-post-tasks_v2?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) | Create a new task object. |
| [Get](https://learn.microsoft.com/en-us/graph/task-get?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) | Read the properties and relationships of [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/task-update?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) | Update the properties of a task object. |
| [Delete](https://learn.microsoft.com/en-us/graph/plan-delete-tasks?view=graph-rest-beta) | None | Delete a task object. |
| [List checklist](https://learn.microsoft.com/en-us/graph/task-list-checklist?view=graph-rest-beta) | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/checklistitemv4?view=graph-rest-beta) collection | Get a list of the checklistItemV4 objects and their properties. |
| [List customFieldValues](https://learn.microsoft.com/en-us/graph/task-list-customfieldvalues?view=graph-rest-beta) | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/customfieldvalue?view=graph-rest-beta) collection | Get a list of the customFieldValue objects and their properties. |
| [List links](https://learn.microsoft.com/en-us/graph/task-list-links?view=graph-rest-beta) | [contentLink](https://learn.microsoft.com/en-us/graph/api/contentlink?view=graph-rest-beta) collection | Get a list of the contentLink objects and their properties. |
| [List messages](https://learn.microsoft.com/en-us/graph/task-list-messages?view=graph-rest-beta) | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/plannerchatmessage?view=graph-rest-beta) collection | Get a list of the plannerChatMessage objects and their properties. |
| [List userAssignments](https://learn.microsoft.com/en-us/graph/task-list-userassignments?view=graph-rest-beta) | [userAssignment](https://learn.microsoft.com/en-us/graph/api/userassignment?view=graph-rest-beta) collection | Get a list of the userAssignment objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/plannerarchivalinfo?view=graph-rest-beta) | Service-populated information about whether the entity is archived, and when it was archived. Read-only. |
| bucketId | String | ID of the bucket that the task belongs to. |
| capabilities | [taskCapability](https://learn.microsoft.com/en-us/graph/api/taskcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| completedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/identityset?view=graph-rest-beta) | Identity of the user who marked the task complete. Read-only. |
| completedDateTime | DateTimeOffset | Date and time the task was completed. Read-only. |
| creationInfo | [creationInfo](https://learn.microsoft.com/en-us/graph/api/creationinfo?view=graph-rest-beta) | Read-only creation metadata for the entity. |
| displayName | String | Title of the task. |
| dueDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is due. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| finishDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task was finished. |
| goalIds | String collection | IDs of the goals that the task is associated with. |
| hasChat | Boolean | Indicates whether the task has an associated chat. Read-only. |
| hasChildren | Boolean | Indicates whether the task has subtasks. Read-only. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/entity?view=graph-rest-beta) |
| isCritical | Boolean | Indicates whether the task is on the critical path, as computed from its dependencies. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/itembody?view=graph-rest-beta) | Additional details or notes about the task. |
| parentTaskId | String | ID of the parent task, if this task is a subtask. |
| percentComplete | Int32 | Percentage of the task's completion, ranging from 0 to 100. |
| personalView | [taskPersonalView](https://learn.microsoft.com/en-us/graph/api/taskpersonalview?view=graph-rest-beta) | Per-user personal view settings for the task, such as My Day membership. |
| planId | String | ID of the plan that contains the task. Immutable after creation. |
| planView | [taskPlanView](https://learn.microsoft.com/en-us/graph/api/taskplanview?view=graph-rest-beta) | Task view settings scoped to the plan, such as applied category IDs. |
| priority | Int32 | Priority of the task. Supported values range from 0 \(urgent\) to 10 \(low\). |
| recurrence | [plannerTaskRecurrence](https://learn.microsoft.com/en-us/graph/api/plannertaskrecurrence?view=graph-rest-beta) | Recurrence pattern for the task, if it repeats. |
| startDateTime | [dateWithOptionalTime](https://learn.microsoft.com/en-us/graph/api/datewithoptionaltime?view=graph-rest-beta) | Date and, optionally, time the task is scheduled to start. |
| status | plannerTaskStatus | Indicates progress on the task. The possible values are: `notStarted`, `inProgress`, `completed`, `blocked`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| checklist | [checklistItemV4](https://learn.microsoft.com/en-us/graph/api/checklistitemv4?view=graph-rest-beta) collection | Checklist items on the task. Can be supplied when creating a task by using a deep insert. Nullable. |
| customFieldValues | [customFieldValue](https://learn.microsoft.com/en-us/graph/api/customfieldvalue?view=graph-rest-beta) collection | The collection of custom field values set on the task. Read-only. Nullable. |
| links | [contentLink](https://learn.microsoft.com/en-us/graph/api/contentlink?view=graph-rest-beta) collection | Content links attached to the task. Can be supplied when creating a task by using a deep insert. Nullable. |
| messages | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/plannerchatmessage?view=graph-rest-beta) collection | The collection of chat messages associated with the task. Read-only. Nullable. |
| userAssignments | [userAssignment](https://learn.microsoft.com/en-us/graph/api/userassignment?view=graph-rest-beta) collection | User assignments on the task. Can be supplied when creating a task by using a deep insert. Nullable. |

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
