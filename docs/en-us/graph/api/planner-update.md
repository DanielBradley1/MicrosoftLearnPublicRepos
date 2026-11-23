<!-- Source: https://learn.microsoft.com/en-us/graph/api/planner-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# planner resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **planner** resource is the entry point for the Planner object model. It returns a singleton **planner** resource. It doesn't contain any usable properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create bucket](https://learn.microsoft.com/en-us/graph/planner-post-buckets?view=graph-rest-beta) | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/plannerbucket?view=graph-rest-beta) | Create a new **plannerBucket** by posting to the buckets collection. |
| [Create plan](https://learn.microsoft.com/en-us/graph/planner-post-plans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) | Create a new **plannerPlan** by posting to the plans collection. |
| [Create roster](https://learn.microsoft.com/en-us/graph/planner-post-rosters?view=graph-rest-beta) | [plannerRoster](https://learn.microsoft.com/en-us/graph/api/plannerroster?view=graph-rest-beta) | Create a new **plannerRoster** by posting to rosters collection. |
| [Create task](https://learn.microsoft.com/en-us/graph/planner-post-tasks?view=graph-rest-beta) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) | Create a new **plannerTask** by posting to the tasks collection. |
| [List plans \(Planner Unified plans Graph API\)](https://learn.microsoft.com/en-us/graph/planner-list-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) collection | Get a list of the [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) objects and their properties. |
| [Create plan \(Planner Unified plans Graph API\)](https://learn.microsoft.com/en-us/graph/planner-post-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) | Create a new [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) object. |
| [List tasks \(Planner Unified plans Graph API\)](https://learn.microsoft.com/en-us/graph/planner-list-tasks_v2?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) collection | Get a list of the [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) objects and their properties. |
| [Create task \(Planner Unified plans Graph API\)](https://learn.microsoft.com/en-us/graph/planner-post-tasks_v2?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) | Create a new [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. Identifier of the **planner** resource. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| buckets | [plannerBucket](https://learn.microsoft.com/en-us/graph/api/plannerbucket?view=graph-rest-beta) collection | Read-only. Nullable. Returns a collection of the specified buckets |
| goals | [plannerGoal](https://learn.microsoft.com/en-us/graph/api/plannergoal?view=graph-rest-beta) collection | Read-only. Nullable. Returns a collection of the specified goals |
| plans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Read-only. Nullable. Returns a collection of the specified plans |
| plans\_v2 | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) collection | Read-only. Nullable. The collection of plans in the Planner Unified plans Graph API. |
| rosters | [plannerRoster](https://learn.microsoft.com/en-us/graph/api/plannerroster?view=graph-rest-beta) collection | Read-only. Nullable. Returns a collection of the specified rosters |
| tasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) collection | Read-only. Nullable. Returns a collection of the specified tasks |
| tasks\_v2 | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) collection | Read-only. Nullable. The collection of tasks in the Planner Unified plans Graph API. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)"
}
```
