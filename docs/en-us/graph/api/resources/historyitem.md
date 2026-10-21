<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# historyItem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An audit or activity record for a change made to a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) or its child entities. `entityId`, `entityType`, `eventType`, and `occurredDateTime` \(the primary sort key\) are returned by default; the acting identity and before/after state are opt-in via $select.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plan-list-historyitems?view=graph-rest-beta) | [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) collection | Get a list of the historyItem objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/plan-post-historyitems?view=graph-rest-beta) | [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) | Create a new historyItem object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/historyitem-get?view=graph-rest-beta) | [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) | Read the properties and relationships of [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/historyitem-update?view=graph-rest-beta) | [historyItem](https://learn.microsoft.com/en-us/graph/api/resources/historyitem?view=graph-rest-beta) | Update the properties of a historyItem object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plan-delete-historyitems?view=graph-rest-beta) | None | Delete a historyItem object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actor | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) that performed the change. |
| entityId | String | ID of the entity the history item describes. |
| entityType | historyEntityType | Type of the entity the history item describes. The possible values are: `task`, `unknownFutureValue`. |
| eventType | historyEventType | Type of the change event that occurred. The possible values are: `created`, `updated`, `deleted`, `undeleted`, `moved`, `unknownFutureValue`. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| newData | String | Serialized representation of the entity state after the change. |
| occurredDateTime | DateTimeOffset | Date and time the change occurred. Read-only. |
| oldData | String | Serialized representation of the entity state before the change. |
| planId | String | ID of the plan the change occurred in. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.historyItem",
  "id": "String (identifier)",
  "planId": "String",
  "entityId": "String",
  "entityType": "String",
  "eventType": "String",
  "occurredDateTime": "String (timestamp)",
  "actor": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "oldData": "String",
  "newData": "String"
}
```
