<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# authorizationSystemTypeAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an action in an authorization system onboarded to Permissions Management. The following resource types are derived from this base type:

- [awsAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemtypeaction?view=graph-rest-beta) resource type
- [azureAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemtypeaction?view=graph-rest-beta) resource type
- [gcpAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemtypeaction?view=graph-rest-beta) resource type

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionType | authorizationSystemActionType | The type of action allowed in the authorization system's service. The possible values are: `delete`, `read`, `unknownFutureValue`. Supports `$filter` and \(`eq`\). |
| externalId | String | The display name of an action. Read-only. Supports `$filter` and \(`eq`\). |
| id | String | The base64 encoded identifier of externalId for an action as defined by Permissions Management. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resourceTypes | String collection | The resource types in the authorization system's service where the action can be performed. Supports `$filter` and \(`eq`\). |
| severity | authorizationSystemActionSeverity | The severity of the action in the authorization systems' service. The possible values are: `normal`, `high`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authorizationSystemTypeAction",
  "id": "String (identifier)",
  "externalId": "String",
  "resourceTypes": [
    "String"
  ],
  "severity": "String",
  "actionType": "String"
}
```
