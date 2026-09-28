<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannergroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# plannerGroup resource type

Namespace: microsoft.graph

The **plannerGroup** resource provides access to Planner resources for a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). It doesn't contain any usable properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List plans for group](https://learn.microsoft.com/en-us/graph/api/plannergroup-list-plans?view=graph-rest-1.0) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) collection | Get a **plannerPlan** object collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. Identifier of the **plannerGroup** |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| plans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) collection | Read-only. Nullable. Returns the [plannerPlans](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-1.0) owned by the group. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)"
}
```
