<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerprogresstaskboardtaskformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# plannerProgressTaskBoardTaskFormat resource type

Namespace: microsoft.graph

Represents the information used to render a task correctly in the progress view of the task board \(a view organized by the state of the PercentComplete field on the task object, with columns for Not Started, In Progress, and Complete\). Each [task](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) has one **plannerProgressTaskBoardTaskFormat** object associated with it.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get progress task board format](https://learn.microsoft.com/en-us/graph/api/plannerprogresstaskboardtaskformat-get?view=graph-rest-1.0) | [plannerProgressTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerprogresstaskboardtaskformat?view=graph-rest-1.0) | Read properties and relationships of **plannerProgressTaskBoardTaskFormat** object. |
| [Update progress task board format](https://learn.microsoft.com/en-us/graph/api/plannerprogresstaskboardtaskformat-update?view=graph-rest-1.0) | [plannerProgressTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerprogresstaskboardtaskformat?view=graph-rest-1.0) | Update **plannerProgressTaskBoardTaskFormat** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. ID of the resource. It's 28 characters long and case-sensitive. The [format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| orderHint | String | Hint value used to order the task on the progress view of the task board. For details about the supported format, see [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "orderHint": "String"
}
```
