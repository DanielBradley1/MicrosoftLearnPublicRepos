<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamschannelplanner?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# teamsChannelPlanner resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides access to Planner resources for a Teams shared [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-beta). This resource doesn't contain any usable properties.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List plans](https://learn.microsoft.com/en-us/graph/api/teamschannelplanner-list-plans?view=graph-rest-beta) | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) collection | Get a list of [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) objects owned by a shared [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-beta) in Teams. |
| [List plans\_v2](https://learn.microsoft.com/en-us/graph/api/teamschannelplanner-list-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) collection | Get a list of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) objects owned by the Teams channel. |
| [Create plan\_v2](https://learn.microsoft.com/en-us/graph/api/teamschannelplanner-post-plans_v2?view=graph-rest-beta) | [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) | Create a new [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the **teamsChannelPlanner** object. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| plans | [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) collection | A collection of [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) objects owned by the Teams channel. Currently, only shared channels are supported. Read-only. Nullable. |
| plans\_v2 | [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) collection | Read-only. Nullable. The collection of Planner Graph V4 plans owned by the Teams channel. Currently, only shared channels are supported. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)"
}
```
