<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsRole resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an AWS role. An AWS role is an AWS identity with permission policies that determine what the identity can and can't do in AWS. However, unlike an AWS user, an AWS role isn't uniquely associated with one person but is assumable by any identity that needs it.

Inherits from [awsIdentity](https://learn.microsoft.com/en-us/graph/api/resources/awsidentity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsassociatedidentities-list-roles?view=graph-rest-beta) | [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) | Get a list of the [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awsrole-get?view=graph-rest-beta) | [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) | Read the properties and relationships of an [awsRole](https://learn.microsoft.com/en-us/graph/api/resources/awsrole?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the object. Supports `$filter` \(`eq`,`contains`\). Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| externalId | String | The ID for the role as defined by AWS. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| id | String | The ID for the role in Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| source | [authorizationSystemIdentitySource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentitysource?view=graph-rest-beta) | The source of the authorization system identity. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta). |
| trustEntityType | awsRoleTrustEntityType | Types of role trusts. The possible values are: `none`, `service`, `sso`, `crossAccount`, `webIdentity`, `unknownFutureValue`. |
| roleType | awsRoleType | Indicates whether role is a `system` or `custom` role. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | Represents the authorization system. Inherited from [authorizationSystemIdentity](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemidentity?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsRole",
  "id": "String (identifier)",
  "displayName": "String",
  "source": {
    "@odata.type": "microsoft.graph.authorizationSystemIdentitySource"
  },
  "externalId": "String",
  "trustEntityType": "String",
  "roleType": "String"
}
```
