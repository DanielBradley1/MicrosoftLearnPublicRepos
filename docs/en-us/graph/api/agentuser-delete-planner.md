<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentuser-delete-planner?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# plannerUser resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides access to Planner resources for a [user](https://learn.microsoft.com/en-us/graph/api/user?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List user's assigned tasks](https://learn.microsoft.com/en-us/graph/planneruser-list-tasks?view=graph-rest-beta) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) collection | Get the [plannerTasks](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) assigned to the user. |
| [List user's My Day tasks](https://learn.microsoft.com/en-us/graph/planneruser-list-mydaytasks?view=graph-rest-beta) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) collection | Get the [plannerTasks](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) to be shown in the user's MyDay view. |
| [List user's favorite plans](https://learn.microsoft.com/en-us/graph/planneruser-list-favoriteplans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Get the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) marked as favorite by the user. |
| [List user's recent plans](https://learn.microsoft.com/en-us/graph/planneruser-list-recentplans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Get the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) recently viewed by the user. |
| [List user's plans in rosters](https://learn.microsoft.com/en-us/graph/planneruser-list-rosterplans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Get the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) contained by the [plannerRosters](https://learn.microsoft.com/en-us/graph/api/plannerroster?view=graph-rest-beta) that the user is a member. |
| [Update user's settings](https://learn.microsoft.com/en-us/graph/planneruser-update?view=graph-rest-beta) | [plannerUser](https://learn.microsoft.com/en-us/graph/api/planneruser?view=graph-rest-beta) | Update a **plannerUser** object. |
| [List plans \(Planner Unified plans Graph API\)](https://learn.microsoft.com/en-us/graph/planneruser-list-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) collection | Get a list of the [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) objects associated with the user. |
| [List tasks \(Planner Unified plans Graph API\)](https://learn.microsoft.com/en-us/graph/planneruser-list-tasks_v2?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) collection | Get a list of the [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) objects assigned to the user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| favoritePlanReferences | [plannerFavoritePlanReferenceCollection](https://learn.microsoft.com/en-us/graph/api/plannerfavoriteplanreferencecollection?view=graph-rest-beta) | A collection that contains the references to the plans that the user marked as favorites. |
| id | String | Read-only. Unique identifier for the **plannerUser** object. |
| recentPlanReferences | [plannerRecentPlanReferenceCollection](https://learn.microsoft.com/en-us/graph/api/plannerrecentplanreferencecollection?view=graph-rest-beta) | A collection that contains references to the plans that the user recently viewed in apps that support recent plans. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| favoritePlans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Read-only. Nullable. Returns the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) that the user marked as favorites. |
| myDayTasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) collection | Read-only. Nullable. Returns the [plannerTasks](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) to be shown in the My Day view of the user. |
| plans\_v2 | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) collection | Read-only. Nullable. The collection of plans in the Planner Unified plans Graph API associated with the user. |
| recentPlans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Read-only. Nullable. Returns the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) that the user recently viewed in apps that support recent plans. |
| rosterPlans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Read-only. Nullable. Returns the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) contained by the [plannerRosters](https://learn.microsoft.com/en-us/graph/api/plannerroster?view=graph-rest-beta) the user is a member. |
| tasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) collection | Read-only. Nullable. Returns the [plannerTasks](https://learn.microsoft.com/en-us/graph/api/plannertask?view=graph-rest-beta) assigned to the user. |
| tasks\_v2 | [task](https://learn.microsoft.com/en-us/graph/api/task?view=graph-rest-beta) collection | Read-only. Nullable. The collection of tasks in the Planner Unified plans Graph API assigned to the user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "favoritePlanReferences": {"@odata.type": "microsoft.graph.plannerFavoritePlanReferenceCollection"},
  "recentPlanReferences": {"@odata.type": "microsoft.graph.plannerRecentPlanReferenceCollection"}
}
```
