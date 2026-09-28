<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/planneruser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# plannerUser resource type

Namespace: microsoft.graph

Provides access to Planner resources for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). It doesn't contain any usable properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List plans](https://learn.microsoft.com/en-us/graph/api/planneruser-list-plans?view=graph-rest-1.0) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) collection | Get a **plannerPlan** object collection. |
| [Get tasks for user](https://learn.microsoft.com/en-us/graph/api/planneruser-list-tasks?view=graph-rest-1.0) | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) collection | Get a **plannerTask** object collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. The unique identifier for the **plannerUser** object. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| plans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) collection | Read-only. Nullable. Returns the [plannerTasks](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) assigned to the user. |
| tasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) collection | Read-only. Nullable. Returns the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) shared with the user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)"
}
```
