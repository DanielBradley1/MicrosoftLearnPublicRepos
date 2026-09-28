<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemtypeaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# gcpAuthorizationSystemTypeAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an action in a GCP authorization system.

Inherits from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list-actions?view=graph-rest-beta) | [gcpAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemtypeaction?view=graph-rest-beta) collection | Get a list of the [gcpAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemtypeaction?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystemtypeaction-get?view=graph-rest-beta) | [gcpAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemtypeaction?view=graph-rest-beta) | Read the properties and relationships of a [gcpAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemtypeaction?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionType | authorizationSystemActionType | The type of action. Supports `$filter` and \(`eq`\). Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). The possible values are: `delete`, `read`, `unknownFutureValue`. |
| externalId | String | The ID of the action as defined by GCP. Read-only. Supports `$filter` and `eq`. Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). |
| id | String | The ID for the action as defined by Permissions Management. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resourceTypes | String collection | The resource types the action can be performed on. Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). |
| severity | authorizationSystemActionSeverity | The severity of the action. Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). The possible values are: `normal`, `high`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| service | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) | The service associated with the action in a GCP authorization system. This object is autoexpanded. Supports `$filter` \(`eq`\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.gcpAuthorizationSystemTypeAction",
  "id": "String (identifier)",
  "externalId": "String",
  "resourceTypes": [
    "String"
  ],
  "severity": "String",
  "actionType": "String"
}
```
