<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/taskhistoryitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-21 -->

# taskHistoryItem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a record of a change made to a task within a [planner plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta). Use this resource to track the history of task modifications, including creation, updates, deletions, and moves.

Inherits from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta).

## Methods

For the list of supported methods, see [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actor | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user or application that performed the change. Inherited from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta). |
| entityId | String | The ID of the task that was changed. Inherited from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta). |
| entityType | historyEntityType | The type of entity that was changed. The possible values are: `task`, `unknownFutureValue`. Inherited from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta). |
| eventType | historyEventType | The type of change event that occurred. The possible values are: `created`, `updated`, `deleted`, `undeleted`, `moved`, `unknownFutureValue`. Inherited from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta). |
| id | String | The unique identifier for the history item. Inherited from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta). |
| newData | [plannerTaskData](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdata?view=graph-rest-beta) | A snapshot of the task state after the change. This property is `null` for deletion events. |
| occurredDateTime | DateTimeOffset | The date and time when the change occurred. The date and time information uses ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2021 is `2021-01-01T00:00:00Z`. Inherited from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta). |
| oldData | [plannerTaskData](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdata?view=graph-rest-beta) | A snapshot of the task state before the change. This property is `null` for creation and undeletion events. |
| planId | String | The ID of the plan that contains the task. Inherited from [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.taskHistoryItem",
  "id": "String (identifier)",
  "planId": "String",
  "entityId": "String",
  "entityType": "String",
  "eventType": "String",
  "occurredDateTime": "String (timestamp)",
  "actor": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "oldData": {
    "@odata.type": "microsoft.graph.plannerTaskData"
  },
  "newData": {
    "@odata.type": "microsoft.graph.plannerTaskData"
  }
}
```
