<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-29 -->

# todoTask resource type

Namespace: microsoft.graph

A **todoTask** represents a task, such as a piece of work or personal item, that can be tracked and completed.

A **todoTask** is always contained in a [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0). It includes a relationship to a collection of [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) objects, tracking one or more sources of the task.

This resource supports the following:

- Adding your data as custom properties in [open extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).
- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions and updates.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/todotasklist-list-tasks?view=graph-rest-1.0) | [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) collection | Get all the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) resources in the specified list. |
| [Create task](https://learn.microsoft.com/en-us/graph/api/todotasklist-post-tasks?view=graph-rest-1.0) | [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Create a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) in the specified task list |
| [Get task](https://learn.microsoft.com/en-us/graph/api/todotask-get?view=graph-rest-1.0) | [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Read the properties and relationships of a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) object. |
| [Update task](https://learn.microsoft.com/en-us/graph/api/todotask-update?view=graph-rest-1.0) | [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Update the properties of a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) object. |
| [Delete task](https://learn.microsoft.com/en-us/graph/api/todotask-delete?view=graph-rest-1.0) | None | Deletes a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) object. |
| [List checklistItems](https://learn.microsoft.com/en-us/graph/api/todotask-list-checklistitems?view=graph-rest-1.0) | [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-1.0) collection | Get the **checklistItem** resources from the checklistItems navigation property. |
| [Create checklistItem](https://learn.microsoft.com/en-us/graph/api/todotask-post-checklistitems?view=graph-rest-1.0) | [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-1.0) | Create a new **checklistItem** object. |
| [List linkedResources](https://learn.microsoft.com/en-us/graph/api/todotask-list-linkedresources?view=graph-rest-1.0) | [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) collection | Get the linkedResources from the linkedResources navigation property. |
| [Create linkedResources](https://learn.microsoft.com/en-us/graph/api/todotask-post-linkedresources?view=graph-rest-1.0) | [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) | Create a new linkedResources object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The task body that typically contains information about the task. |
| bodyLastModifiedDateTime | DateTimeOffset | The date and time when the task body was last modified. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| categories | String collection | The categories associated with the task. Each category corresponds to the **displayName** property of an [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) that the user has defined. |
| completedDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time in the specified time zone that the task was finished. |
| createdDateTime | DateTimeOffset | The date and time when the task was created. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| dueDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time in the specified time zone that the task is to be finished. |
| hasAttachments | Boolean | Indicates whether the task has attachments. |
| id | String | Unique identifier for the task. By default, this value changes when the item is moved from one list to another. |
| importance | importance | The importance of the task. The possible values are: `low`, `normal`, `high`. |
| isReminderOn | Boolean | Set to true if an alert is set to remind the user of the task. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the task was last modified. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The recurrence pattern for the task. |
| reminderDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time in the specified time zone for a reminder alert of the task to occur. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time in the specified time zone at which the task is scheduled to start. |
| status | taskStatus | Indicates the state or progress of the task. The possible values are: `notStarted`, `inProgress`, `completed`, `waitingOnOthers`, `deferred`. |
| title | String | A brief description of the task. |

Tasks can be exported using the PST download described in [Export content search results from the Microsoft Purview portal](https://learn.microsoft.com/en-us/purview/ediscovery-export-search-results). You can reference the mapping between `todoTask` properties and the properties in the exported PST file in [To Do API overview](https://learn.microsoft.com/en-us/graph/todo-concept-overview).

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attachments | [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) collection | A collection of file attachments for the task. |
| checklistItems | [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-1.0) collection | A collection of checklistItems linked to a task. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the task. Nullable. |
| linkedResources | [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) collection | A collection of resources linked to the task. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.todoTask",
  "id": "String (identifier)",
  "body": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "categories": ["string"],
  "completedDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "dueDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "importance": "String",
  "isReminderOn": "Boolean",
  "recurrence": {
    "@odata.type": "microsoft.graph.patternedRecurrence"
  },
  "reminderDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "status": "String",
  "title": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "bodyLastModifiedDateTime": "String (timestamp)"
}
```
