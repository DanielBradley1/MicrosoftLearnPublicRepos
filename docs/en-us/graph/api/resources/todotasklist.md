<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# todoTaskList resource type

Namespace: microsoft.graph

A list in Microsoft To Do that contains one or more [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) resources.

In To Do, there are built-in task lists such as **Flagged emails** and **Tasks** which cannot be renamed or deleted. You can, however, create additional task lists.

This resource supports

- Adding your data to custom properties as [open extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions and updates.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List task lists](https://learn.microsoft.com/en-us/graph/api/todo-list-lists?view=graph-rest-1.0) | [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) collection | Get all the [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) in the user's mailbox. |
| [Create task list](https://learn.microsoft.com/en-us/graph/api/todo-post-lists?view=graph-rest-1.0) | [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) | Create a [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) in the user's mailbox. |
| [Get task list](https://learn.microsoft.com/en-us/graph/api/todotasklist-get?view=graph-rest-1.0) | [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) | Read the properties and relationships of the specified [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0). |
| [Update task list](https://learn.microsoft.com/en-us/graph/api/todotasklist-update?view=graph-rest-1.0) | [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) | Update the writable properties of the specified [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0). |
| [Delete task list](https://learn.microsoft.com/en-us/graph/api/todotasklist-delete?view=graph-rest-1.0) | None | Delete the specified [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) . |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/todotasklist-list-tasks?view=graph-rest-1.0) | [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) collection | Get all the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) resources in the specified list. |
| [Create task](https://learn.microsoft.com/en-us/graph/api/todotasklist-post-tasks?view=graph-rest-1.0) | [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Create a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) in the specified task list. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the task list. |
| id | String | The identifier of the task list, unique in the user's mailbox. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| isOwner | Boolean | True if the user is owner of the given task list. |
| isShared | Boolean | True if the task list is shared with other users |
| wellknownListName | wellknownListName | Property indicating the list name if the given list is a well-known list. The possible values are: `none`, `defaultList`, `flaggedEmails`, `unknownFutureValue`. |

### wellknownListName values

| Member | Description |
| :--- | :--- |
| none | User created list. |
| defaultList | Built-in **Tasks** list. |
| flaggedEmails | Built-in **Flagged email** list. Tasks from flagged emails are present in this list. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the task list. Nullable. |
| tasks | [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) collection | The tasks in this task list. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.todoTaskList",
  "id": "String (identifier)",
  "displayName": "String",
  "isOwner": "Boolean",
  "isShared": "Boolean",
  "wellknownListName": "String"
}
```
