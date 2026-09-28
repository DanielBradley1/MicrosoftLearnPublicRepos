<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerbuckettaskboardtaskformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# plannerBucketTaskBoardTaskFormat resource type

Namespace: microsoft.graph

Represents the information used to render a task correctly in the buckets view of a task board \(a view organized by tasks within the buckets they're assigned to\). Each [task](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) has one **plannerBucketTaskBoardTaskFormat** object associated with it.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get bucket task board format](https://learn.microsoft.com/en-us/graph/api/plannerbuckettaskboardtaskformat-get?view=graph-rest-1.0) | [plannerBucketTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerbuckettaskboardtaskformat?view=graph-rest-1.0) | Read properties and relationships of **plannerBucketTaskBoardTaskFormat** object. |
| [Update bucket task board format](https://learn.microsoft.com/en-us/graph/api/plannerbuckettaskboardtaskformat-update?view=graph-rest-1.0) | [plannerBucketTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerbuckettaskboardtaskformat?view=graph-rest-1.0) | Update **plannerBucketTaskBoardTaskFormat** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. ID of the resource. It's 28 characters long and case-sensitive. The [format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| orderHint | String | Hint used to order tasks in the bucket view of the task board. For details about the supported format, see [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |

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
