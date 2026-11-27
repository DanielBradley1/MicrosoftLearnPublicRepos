<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# plannerDelta resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents the base type for planner entities such as a plan or a task.

Base type of [plannerBucket](https://learn.microsoft.com/en-us/graph/api/resources/plannerbucket?view=graph-rest-beta), [plannerGoal](https://learn.microsoft.com/en-us/graph/api/resources/plannergoal?view=graph-rest-beta), [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta), [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta), and [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerDelta",
  "id": "String (identifier)"
}
```
