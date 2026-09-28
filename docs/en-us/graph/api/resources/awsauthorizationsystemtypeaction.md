<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemtypeaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsAuthorizationSystemTypeAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an action in an AWS authorization system.

Inherits from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-actions?view=graph-rest-beta) | [awsAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemtypeaction?view=graph-rest-beta) collection | Get a list of the [awsAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemtypeaction?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystemtypeaction-get?view=graph-rest-beta) | [awsAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemtypeaction?view=graph-rest-beta) | Read the properties and relationships of an [awsAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemtypeaction?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionType | authorizationSystemActionType | The type of action. Supports `$filter` \(`eq`\). Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). The possible values are: `delete`, `read`, `unknownFutureValue`. |
| externalId | String | The ID of the action as defined by AWS. Read-only. Supports `$filter` \(`eq`\). Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). |
| id | String | The ID for the action as defined by Permissions Management. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resourceTypes | String collection | The resource types the action can be performed on. Supports `$filter` and \(`eq`, `contains`\). Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). |
| severity | authorizationSystemActionSeverity | The severity of the action. Inherited from [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta). The possible values are: `normal`, `high`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| service | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) | The service associated with the action in an AWS authorization system. This object autoexpanded. Supports `$filter` \(`eq`\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsAuthorizationSystemTypeAction",
  "id": "String (identifier)",
  "externalId": "String",
  "resourceTypes": [
    "String"
  ],
  "severity": "String",
  "actionType": "String"
}
```
