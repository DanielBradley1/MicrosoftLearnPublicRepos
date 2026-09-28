<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsuser?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsUser resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents AWS users.

Inherits from [awsIdentity](https://learn.microsoft.com/en-us/graph/api/resources/awsidentity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsassociatedidentities-list-users?view=graph-rest-beta) | [awsUser](https://learn.microsoft.com/en-us/graph/api/resources/awsuser?view=graph-rest-beta) | Read the properties and relationships of an [awsUser](https://learn.microsoft.com/en-us/graph/api/resources/awsuser?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awsuser-get?view=graph-rest-beta) | [awsUser](https://learn.microsoft.com/en-us/graph/api/resources/awsuser?view=graph-rest-beta) | Read the properties and relationships of an [awsUser](https://learn.microsoft.com/en-us/graph/api/resources/awsuser?view=graph-rest-beta) object. |
| [List assumable roles](https://learn.microsoft.com/en-us/graph/api/awsuser-list-assumableroles?view=graph-rest-beta) | [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) | Read the properties and relationships of an [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the object. Supports `$filter` \(`eq`,`contains`\). Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| externalId | String | The ID for the user as defined by AWS. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| id | String | The ID for the identity in Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| source | [authorizationSystemIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentitysource?view=graph-rest-beta) | The source of the authorization system identity. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assumableRoles | [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) collection | Roles assumed by the user. |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | Represents the authorization system. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsUser",
  "id": "String (identifier)",
  "displayName": "String",
  "source": {
    "@odata.type": "microsoft.graph.authorizationSystemIdentitySource"
  },
  "externalId": "String"
}
```
