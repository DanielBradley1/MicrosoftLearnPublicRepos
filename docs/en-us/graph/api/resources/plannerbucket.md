<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# plannerBucket resource type

Namespace: microsoft.graph

Represents a bucket \(or "custom column"\) for tasks in a plan in Microsoft 365. It is contained in a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) and can have a collection of [plannerTasks](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get bucket](https://learn.microsoft.com/en-us/graph/api/plannerbucket-get?view=graph-rest-1.0) | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) | Read properties and relationships of **plannerBucket** object. |
| [List bucket tasks](https://learn.microsoft.com/en-us/graph/api/plannerbucket-list-tasks?view=graph-rest-1.0) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) collection | Get a **plannerTask** object collection. |
| [Create bucket](https://learn.microsoft.com/en-us/graph/api/planner-post-buckets?view=graph-rest-1.0) | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) | Create a new **plannerBucket** object. |
| [Update bucket](https://learn.microsoft.com/en-us/graph/api/plannerbucket-update?view=graph-rest-1.0) | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) | Update **plannerBucket** object. |
| [Delete bucket](https://learn.microsoft.com/en-us/graph/api/plannerbucket-delete?view=graph-rest-1.0) | None | Delete **plannerBucket** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. ID of the bucket. It is 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| name | String | Name of the bucket. |
| orderHint | String | Hint used to order items of this type in a list view. For details about the supported format, see [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| planId | String | Plan ID to which the bucket belongs. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| tasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) collection | Read-only. Nullable. The collection of tasks in the bucket. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "name": "String",
  "orderHint": "String",
  "planId": "String"
}
```
