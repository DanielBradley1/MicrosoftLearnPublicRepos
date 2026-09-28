<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsAuthorizationSystemResource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an AWS resource in an AWS authorization system.

Inherits from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-resources?view=graph-rest-beta) | [awsAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemresource?view=graph-rest-beta) collection | Get a list of the [awsAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemresource?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystemresource-get?view=graph-rest-beta) | [awsAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemresource?view=graph-rest-beta) | Read the properties and relationships of an [awsAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/awsauthorizationsystemresource?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the resource. Read-only. Supports `$filter` \(`eq`,`contains`\). Inherited from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta). |
| externalId | String | The ID of the resource as defined by AWS. Read-only. Supports `$filter` \(`eq`\). Inherited from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta). |
| id | String | The ID of the resource as defined by Permissions Management. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| resourceType | String | The type of the resource. Read-only. Supports `$filter` \(`eq`\). Inherited from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | The authorization system that the resource is in. Inherited from [microsoft.graph.authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) |
| service | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) | The service associated with the resource in an AWS authorization system. This is autoexpanded. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsAuthorizationSystemResource",
  "id": "String (identifier)",
  "externalId": "String",
  "displayName": "String",
  "resourceType": "String"
}
```
