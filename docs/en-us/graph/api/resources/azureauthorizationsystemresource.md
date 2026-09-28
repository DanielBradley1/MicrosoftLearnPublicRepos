<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemresource?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# azureAuthorizationSystemResource resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents an Azure resource in an Azure authorization system onboarded to Permissions Management.

Inherits from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-resources?view=graph-rest-beta) | [azureAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemresource?view=graph-rest-beta) collection | Get a list of the [azureAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemresource?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystemresource-get?view=graph-rest-beta) | [azureAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemresource?view=graph-rest-beta) | Read the properties and relationships of an [azureAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/azureauthorizationsystemresource?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the resource. Supports `$filter` \(`eq`,`contains`\). Read-only. Inherited from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta). |
| externalId | String | The ID of the resource as defined by Microsoft Azure. Read-only. Alternate key. Inherited from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta). |
| id | String | The ID of the resource as defined by Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Read-only. |
| resourceType | String | The type of the resource. Read-only. Inherited from [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | The authorization system that the resource is in. Inherited from [microsoft.graph.authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) |
| service | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) | The service associated with the resource in an Azure authorization system. This object is auto-expanded. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureAuthorizationSystemResource",
  "id": "String (identifier)",
  "externalId": "String",
  "displayName": "String",
  "resourceType": "String"
}
```
