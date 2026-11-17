<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannergroup-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# plannerGroup resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerGroup** resource provides access to Planner resources for a [group](https://learn.microsoft.com/en-us/graph/api/group?view=graph-rest-beta). It doesn't contain any usable properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List group's plans](https://learn.microsoft.com/en-us/graph/plannergroup-list-plans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Get a **plannerPlan** object collection. |
| [List plans \(Planner Unified plans Graph API\)](https://learn.microsoft.com/en-us/graph/plannergroup-list-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) collection | Get a list of the [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) objects owned by the group. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. Identifier of the **plannerGroup** |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| plans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) collection | Read-only. Nullable. Returns the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/plannerplan?view=graph-rest-beta) owned by the group. |
| plans\_v2 | [plan](https://learn.microsoft.com/en-us/graph/api/plan?view=graph-rest-beta) collection | Read-only. Nullable. The collection of plans in the Planner Unified plans Graph API owned by the group. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)"
}
```
