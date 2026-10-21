<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# goal resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A Planner V4 goal associated with a set of [tasks](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) in a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta). `status` \(for example, on-track, at-risk, off-track\) is returned by default; description, metrics, and narrative updates require $select.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plan-list-goals?view=graph-rest-beta) | [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) collection | Get a list of the goal objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/plan-post-goals?view=graph-rest-beta) | [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) | Create a new goal object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/goal-get?view=graph-rest-beta) | [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) | Read the properties and relationships of [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/goal-update?view=graph-rest-beta) | [goal](https://learn.microsoft.com/en-us/graph/api/resources/goal?view=graph-rest-beta) | Update the properties of a goal object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plan-delete-goals?view=graph-rest-beta) | None | Delete a goal object. |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/goal-list-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) collection | Get a list of the task objects and their properties. |
| [Add task](https://learn.microsoft.com/en-us/graph/api/goal-post-tasks?view=graph-rest-beta) | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) | Add tasks by posting to the tasks collection. |
| [Remove tasks](https://learn.microsoft.com/en-us/graph/api/goal-delete-tasks?view=graph-rest-beta) | None | Remove a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| archivalInfo | [plannerArchivalInfo](https://learn.microsoft.com/en-us/graph/api/resources/plannerarchivalinfo?view=graph-rest-beta) | Information about whether the entity is archived, and when it was archived. |
| capabilities | [goalCapability](https://learn.microsoft.com/en-us/graph/api/resources/goalcapability?view=graph-rest-beta) | Server-computed, read-only capability flags indicating which optional features are enabled for the entity. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who created the entity. Read-only. |
| createdDateTime | DateTimeOffset | Date and time the entity was created. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| displayName | String | Title of the goal. |
| extensions | [extensionFieldCollection](https://learn.microsoft.com/en-us/graph/api/resources/extensionfieldcollection?view=graph-rest-beta) | Custom extension field values set on the entity. Supports $select. |
| finishDate | Date | Date the goal is targeted to finish. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who last modified the entity. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the entity was last modified. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-beta) | Additional details or notes about the goal. |
| planId | String | ID of the plan that contains the goal. Required, and immutable after creation. |
| priority | Int32 | Priority of the goal. |
| startDate | Date | Date the goal starts. |
| status | plannerGoalStatus | Progress status of the goal. The possible values are: `notStarted`, `onTrack`, `behind`, `atRisk`, `closed`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| tasks | [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) collection | The collection of tasks associated with the goal. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.goal",
  "id": "String (identifier)",
  "displayName": "String",
  "planId": "String",
  "status": "String",
  "priority": "Int32",
  "startDate": "Date",
  "finishDate": "Date",
  "notes": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "archivalInfo": {
    "@odata.type": "microsoft.graph.plannerArchivalInfo"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "capabilities": {
    "@odata.type": "microsoft.graph.goalCapability"
  },
  "extensions": {
    "@odata.type": "microsoft.graph.extensionFieldCollection"
  }
}
```
