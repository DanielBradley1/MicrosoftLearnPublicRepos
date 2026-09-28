<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tasks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# tasks resource type

Namespace: microsoft.graph

Represents the To Do tasks services available to a user.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List base task lists](https://learn.microsoft.com/en-us/graph/api/tasks-list-lists?view=graph-rest-beta) | [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) collection | Get the baseTaskList resources from the lists navigation property. |
| [Create base task list](https://learn.microsoft.com/en-us/graph/api/tasks-post-lists?view=graph-rest-beta) | [taskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) | Create a new baseTaskList object. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alltasks | [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/basetask?view=graph-rest-beta) collection | All tasks in the users mailbox. |
| lists | [baseTaskList](https://learn.microsoft.com/en-us/graph/api/resources/basetasklist?view=graph-rest-beta) collection | The task lists in the users mailbox. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tasks",
  "id": "String (identifier)"
}
```
