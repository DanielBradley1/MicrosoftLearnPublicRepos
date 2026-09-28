<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# plannerAssignedToTaskBoardTaskFormat resource type

Namespace: microsoft.graph

Represents the information used to render a task correctly in the **AssignedTo** view of the task board \(a view organized by users to whom tasks are assigned\). Each [task](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) has one **plannerAssignedToTaskBoardTaskFormat** object associated with it.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get assigned to task board format](https://learn.microsoft.com/en-us/graph/api/plannerassignedtotaskboardtaskformat-get?view=graph-rest-1.0) | [plannerAssignedToTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat?view=graph-rest-1.0) | Read properties and relationships of **plannerAssignedToTaskBoardTaskFormat** object. |
| [Update assigned to task board format](https://learn.microsoft.com/en-us/graph/api/plannerassignedtotaskboardtaskformat-update?view=graph-rest-1.0) | [plannerAssignedToTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat?view=graph-rest-1.0) | Update **plannerAssignedToTaskBoardTaskFormat** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the resource. It's 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. Read-only. |
| orderHintsByAssignee | [plannerOrderHintsByAssignee](https://learn.microsoft.com/en-us/graph/api/resources/plannerorderhintsbyassignee?view=graph-rest-1.0) | Dictionary of hints used to order tasks on the AssignedTo view of the Task Board. The key of each entry is one of the users the task is assigned to and the value is the order hint. The format of each value is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| unassignedOrderHint | String | Hint value used to order the task on the AssignedTo view of the Task Board when the task isn't assigned to anyone, or if the orderHintsByAssignee dictionary doesn't provide an order hint for the user the task is assigned to. The format is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "orderHintsByAssignee": {"@odata.type": "microsoft.graph.plannerOrderHintsByAssignee"},
  "unassignedOrderHint": "String"
}
```
