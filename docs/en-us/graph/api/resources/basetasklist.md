<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# baseTaskList resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The to-do API set built on [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta&preserve-view=true) was deprecated on May 31, 2022, and stopped returning data on August 31, 2022. Use the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-beta&preserve-view=true) API instead.

Contains one or more [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) resources.

This is the base resource for the following derived types of task lists.

- Built-in task list \([wellKnownTaskList](https://learn.microsoft.com/en-us/graph/api/resources/wellknowntasklist?view=graph-rest-beta) resource\)
- User created task list \([taskList](https://learn.microsoft.com/en-us/graph/api/resources/tasklist?view=graph-rest-beta) resource\)

This is an abstract type.

## Methods

The following methods apply to any of the derived types of **baseTaskList** \(**wellKnownTaskList**,**taskList**\)

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List base task lists](https://learn.microsoft.com/en-us/graph/api/tasks-list-lists?view=graph-rest-beta) | [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) collection | Get a list of the [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) objects and their properties. |
| [Get base task list](https://learn.microsoft.com/en-us/graph/api/basetasklist-get?view=graph-rest-beta) | [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) | Read the properties and relationships of a [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) object. |
| [List base tasks](https://learn.microsoft.com/en-us/graph/api/basetasklist-list-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | Get the baseTask resources from the tasks navigation property. |
| [Create base task](https://learn.microsoft.com/en-us/graph/api/basetasklist-post-tasks?view=graph-rest-beta) | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) | Create a new baseTask object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the task list. |
| id | String | The identifier of the task list, unique in the user's mailbox. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-beta) collection | The collection of open extensions defined for the task list. Nullable. |
| tasks | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | The tasks in this task list. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.baseTaskList",
  "displayName": "String",
  "id": "String (identifier)"
}
```
