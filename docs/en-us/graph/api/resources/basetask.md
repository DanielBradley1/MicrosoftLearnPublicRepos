<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# baseTask resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The to-do API set built on [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta&preserve-view=true) was deprecated on May 31, 2022, and stopped returning data on August 31, 2022. Use the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-beta&preserve-view=true) API instead.

An abstract type that represents a task, such as a piece of work or personal item, that can be tracked and completed.

This is a base type inherited by the [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) resource.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List baseTasks](https://learn.microsoft.com/en-us/graph/api/basetasklist-list-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | Get a list of the [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) objects and their properties. |
| [Create baseTask](https://learn.microsoft.com/en-us/graph/api/basetasklist-post-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) | Create a new [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) object. |
| [Get baseTask](https://learn.microsoft.com/en-us/graph/api/basetask-get?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) | Read the properties and relationships of a [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) object. |
| [Update baseTask](https://learn.microsoft.com/en-us/graph/api/basetask-update?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) | Update the properties of a [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) object. |
| [Delete baseTask](https://learn.microsoft.com/en-us/graph/api/basetask-delete?view=graph-rest-beta) | None | Deletes a [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) object. |
| [move](https://learn.microsoft.com/en-us/graph/api/basetask-move?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) | Move the message to a different list. |
| [delta](https://learn.microsoft.com/en-us/graph/api/basetask-delta?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | Get a set of **baseTask** objects that have been added, deleted, or updated in a specified list. |
| [List checklistItems](https://learn.microsoft.com/en-us/graph/api/todotask-list-checklistitems?view=graph-rest-beta) | [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-beta) collection | Get the **checklistItem** resources from the checklistItems navigation property. |
| [Create checklistItem](https://learn.microsoft.com/en-us/graph/api/todotask-post-checklistitems?view=graph-rest-beta) | [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-beta) | Create a new **checklistItem** object. |
| [List linkedResources](https://learn.microsoft.com/en-us/graph/api/basetask-list-linkedresources?view=graph-rest-beta) | [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) collection | Get the **linkedResource\_v2** resources from the linkedResources navigation property. |
| [Create linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/basetask-post-linkedresources?view=graph-rest-beta) | [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) | Create a new **linkedResource\_v2** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| textBody | String | The task body in text format that typically contains information about the task. |
| bodyLastModifiedDateTime | DateTimeOffset | The date and time when the task was last modified. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| completedDateTime | DateTimeOffset | The date when the task was finished. |
| createdDateTime | DateTimeOffset | The date and time when the task was created. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| displayName | String | The name of the task. |
| dueDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-beta) | The date in the specified time zone that the task is to be finished. |
| id | String | Unique identifier for the task. By default, this value will not change if a task is moved from one list to another. |
| importance | importance | The importance of the task. The possible values are: `low`, `normal`, `high`. The possible values are: `low`, `normal`, `high`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the task was last modified. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| viewpoint | [taskViewpoint](https://learn.microsoft.com/en-us/graph/api/resources/taskviewpoint?view=graph-rest-beta) | Properties that are personal to a user such as **reminderDateTime** and **categories**. |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-beta) | The recurrence pattern for the task. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-beta) | The date in the specified time zone when the task is to begin. |
| status | taskStatus\_v2 | Indicates the state or progress of the task. The possible values are: `notStarted`, `inProgress`, `completed`,`unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| checklistItems | [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/checklistitem?view=graph-rest-beta) collection | A collection of smaller subtasks linked to the more complex parent task. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-beta) collection | The collection of open extensions defined for the task . |
| linkedResources | [linkedResource\_v2](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource_v2?view=graph-rest-beta) collection | A collection of resources linked to the task. |
| parentList | [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) | The list which contains the task. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.baseTask",
  "textBody": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "bodyLastModifiedDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "dueDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "startDateTime": {
    "@odata.type": "microsoft.graph.dateTimeTimeZone"
  },
  "importance": "String",
  "recurrence": {
    "@odata.type": "microsoft.graph.patternedRecurrence"
  },
  "displayName": "String",
  "status": "String",
  "viewpoint": {
    "@odata.type": "microsoft.graph.taskViewpoint"
  },
  "id": "String (identifier)"
}
```
