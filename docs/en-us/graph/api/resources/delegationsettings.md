<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# delegationSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings for a [delegator or delegate](https://learn.microsoft.com/en-us/graph/api/resources/calldelegation-api-overview?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

This resource is an open type that allows additional properties beyond those documented here.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/delegationsettings-get?view=graph-rest-beta) | [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) | Read the properties and relationships of a [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) object. |
| [List delegates](https://learn.microsoft.com/en-us/graph/api/callsettings-list-delegates?view=graph-rest-beta) | [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) collection | Get a list of all delegates for a user. |
| [List delegators](https://learn.microsoft.com/en-us/graph/api/callsettings-list-delegators?view=graph-rest-beta) | [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) collection | Get a list of all delegators for a user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedActions | [delegateAllowedActions](https://learn.microsoft.com/en-us/graph/api/resources/delegateallowedactions?view=graph-rest-beta) | The allowed actions for the delegator or delegate. |
| createdDateTime | DateTimeOffset | Date and time when the delegator or delegate entry was created. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | Unique identifier of the delegator or delegate. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| isActive | Boolean | Indicates whether the delegator or delegate relationship is currently active. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegationSettings",
  "allowedActions": {"@odata.type": "microsoft.graph.delegateAllowedActions"},
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isActive": "Boolean"
}
```
