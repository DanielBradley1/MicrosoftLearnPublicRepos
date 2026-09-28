<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannergoal?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# plannerGoal resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a goal associated with a set of tasks in a [Planner plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta).

Third-party applications can read goals but can't create, update, or delete them.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get goal](https://learn.microsoft.com/en-us/graph/api/plannergoal-get?view=graph-rest-beta) | [plannerGoal](https://learn.microsoft.com/en-us/graph/api/resources/plannergoal?view=graph-rest-beta) | Read the properties and relationships of a **plannerGoal** object. |
| [List goals](https://learn.microsoft.com/en-us/graph/api/plannerplan-list-goals?view=graph-rest-beta) | [plannerGoal](https://learn.microsoft.com/en-us/graph/api/resources/plannergoal?view=graph-rest-beta) collection | Get the goals associated with a **plannerPlan** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Required. The display name of the goal. |
| finishDate | Date | Nullable. The date on which the goal is scheduled to finish. |
| id | String | Read-only. The unique identifier of the goal. Inherited from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta). |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Nullable. The notes associated with the goal. |
| planId | String | Required. The ID of the plan that contains the goal. |
| priority | Int32 | Optional. The relative priority of the goal. Valid values range from `0` to `10`, inclusive. The default value is `5`. |
| startDate | Date | Nullable. The date on which the goal is scheduled to start. |
| status | [plannerGoalStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#plannergoalstatus-values) | Required. The current status of the goal. The default value is `notStarted`. The possible values are: `notStarted`, `onTrack`, `behind`, `atRisk`, `closed`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| tasks | [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) collection | Read-only. Nullable. The tasks associated with the goal. This relationship doesn't support direct retrieval or `$expand`. To identify the goals associated with a task, read the **goalIds** property of the [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta) resource. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerGoal",
  "displayName": "String",
  "finishDate": "Date",
  "id": "String (identifier)",
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "planId": "String",
  "priority": "Int32",
  "startDate": "Date",
  "status": "String"
}
```
