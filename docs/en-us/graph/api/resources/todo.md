<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/todo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# todo resource type

Namespace: microsoft.graph

Represents the To Do services available to a user.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List task lists](https://learn.microsoft.com/en-us/graph/api/todo-list-lists?view=graph-rest-1.0) | [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) collection | Get all the task lists in the user's mailbox. |
| [Create task list](https://learn.microsoft.com/en-us/graph/api/todo-post-lists?view=graph-rest-1.0) | [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) | Create a To Do task list in the user's mailbox. |

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| lists | [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0) collection | The task lists in the users mailbox. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.todo",
  "id": "String"
}
```
