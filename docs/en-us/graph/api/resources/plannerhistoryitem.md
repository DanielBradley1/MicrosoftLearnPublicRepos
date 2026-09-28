<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-21 -->

# plannerHistoryItem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a record of a change made to an entity within a [planner plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta). This resource serves as the base for specific history item types.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plannerplan-list-historyitems?view=graph-rest-beta) | [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta) collection | Get the [history](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta) of changes made to tasks within a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actor | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user or application that performed the change. |
| entityId | String | The ID of the entity that was changed. |
| entityType | historyEntityType | The type of entity that was changed. The possible values are: `task`, `unknownFutureValue`. |
| eventType | historyEventType | The type of change event that occurred. The possible values are: `created`, `updated`, `deleted`, `undeleted`, `moved`, `unknownFutureValue`. |
| id | String | The unique identifier for the history item. Inherited from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta). |
| occurredDateTime | DateTimeOffset | The date and time when the change occurred. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| planId | String | The ID of the plan that contains the changed entity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerHistoryItem",
  "id": "String (identifier)",
  "planId": "String",
  "entityId": "String",
  "entityType": "String",
  "eventType": "String",
  "occurredDateTime": "String (timestamp)",
  "actor": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```
