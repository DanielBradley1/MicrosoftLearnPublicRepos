<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# plannerPlan resource type

Namespace: microsoft.graph

Represents a plan in Microsoft 365. A plan can be owned by a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) and contains a collection of [plannerTasks](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0). It can also have a collection of [plannerBuckets](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0). Each plan object has a [details](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) object that can contain more information about the plan. For more information about the relationships between groups, plans, and tasks, see [Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/planner-post-plans?view=graph-rest-1.0) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) | Create a **plannerPlan** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/plannerplan-get?view=graph-rest-1.0) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) | Read properties and relationships of **plannerPlan** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plannerplan-update?view=graph-rest-1.0) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) | Update **plannerPlan** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plannerplan-delete?view=graph-rest-1.0) | None | Delete **plannerPlan** object. |
| [List plan buckets](https://learn.microsoft.com/en-us/graph/api/plannerplan-list-buckets?view=graph-rest-1.0) | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) collection | Get a **plannerBucket** object collection. |
| [List plan tasks](https://learn.microsoft.com/en-us/graph/api/plannerplan-list-tasks?view=graph-rest-1.0) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) collection | Get a **plannerTask** object collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| container | [plannerPlanContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontainer?view=graph-rest-1.0) | Identifies the container of the plan. Specify only the **url**, the **containerId** and **type**, or all properties. After it's set, this property can’t be updated. Required. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Read-only. The user who created the plan. |
| createdDateTime | DateTimeOffset | Read-only. Date and time at which the plan is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| id | String | Read-only. ID of the plan. It's 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| owner \(deprecated\) | String | Use the **container** property instead. ID of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) that owns the plan. After it's set, this property can’t be updated. This property won't return a valid group ID if the container of the plan isn't a group. |
| title | String | Required. Title of the plan. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| buckets | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-1.0) collection | Read-only. Nullable. Collection of buckets in the plan. |
| details | [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) | Read-only. Nullable. Extra details about the plan. |
| tasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) collection | Read-only. Nullable. Collection of tasks in the plan. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "container": {
    "@odata.type": "microsoft.graph.plannerPlanContainer",
    "containerId": "String",
    "type": "String",
    "url": "String"
  },
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "title": "String"
}
```
