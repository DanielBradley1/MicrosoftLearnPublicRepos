<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# taskList resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The to-do API set built on [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta&preserve-view=true) was deprecated on May 31, 2022, and stopped returning data on August 31, 2022. Use the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-beta&preserve-view=true) API instead.

Represents a list created by a user in Microsoft To Do that contains one or more [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) resources.

This resource supports the following:

- Adding your data to custom properties as [open extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions and updates.

The **taskList** resource inherits from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta). Its contents, of the **task** resource type, inherit from [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List base task lists](https://learn.microsoft.com/en-us/graph/api/tasks-list-lists?view=graph-rest-beta) | [taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) collection | Get a list of the [taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) objects and their properties. |
| [Get base task list](https://learn.microsoft.com/en-us/graph/api/basetasklist-get?view=graph-rest-beta) | [taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) | Read the properties and relationships of a [taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) object. |
| [Update base task list](https://learn.microsoft.com/en-us/graph/api/tasklist-update?view=graph-rest-beta) | [taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) | Update the properties of a [taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) object. |
| [Delete base task list](https://learn.microsoft.com/en-us/graph/api/tasklist-delete?view=graph-rest-beta) | None | Deletes a [taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) object. |
| [List base tasks](https://learn.microsoft.com/en-us/graph/api/basetasklist-list-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | Get the baseTask resources from the tasks navigation property. |
| [Create base task](https://learn.microsoft.com/en-us/graph/api/basetasklist-post-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) | Create a new baseTask object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the task list. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta). |
| id | String | The identifier of the task list, unique in the user's mailbox. Read-only. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-beta) collection | The collection of open extensions defined for the task list. Nullable. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) |
| tasks | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | The tasks in this task list. Read-only. Nullable. Inherited from [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.taskList",
  "displayName": "String",
  "id": "String (identifier)"
}
```
