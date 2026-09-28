<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureserverlessfunction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# azureServerlessFunction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a serverless function in an Azure authorization system.

Inherits from [azureIdentity](https://learn.microsoft.com/en-us/graph/api/resources/azureidentity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the object. Supports `$filter` \(`eq`,`contains`\). Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| externalId | String | The ID for the serverless function as defined by Microsoft Azure. Supports `$filter` \(`eq`\).Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| id | String | The ID for the serverless function in Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| source | [authorizationSystemIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentitysource?view=graph-rest-beta) | The source of the authorization system identity. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | Represents the authorization system. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) |
| resource | [azureAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemresource?view=graph-rest-beta) | Represents the resources in an authorization system. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureServerlessFunction",
  "id": "String (identifier)",
  "displayName": "String",
  "source": {
    "@odata.type": "microsoft.graph.authorizationSystemIdentitySource"
  },
  "externalId": "String"
}
```
