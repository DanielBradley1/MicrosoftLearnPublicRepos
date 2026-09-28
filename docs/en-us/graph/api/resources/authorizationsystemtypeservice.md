<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# authorizationSystemTypeService resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a service in an authorization system that is onboarded to Permissions Management. Services are defined by the auth system type \(AWS, Azure, GCP\).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List AWS authorization system services](https://learn.microsoft.com/en-us/graph/api/awsauthorizationsystem-list-services?view=graph-rest-beta) | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) collection | Get a list of the [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) objects and their properties. |
| [List Azure authorization system type services](https://learn.microsoft.com/en-us/graph/api/azureauthorizationsystem-list-services?view=graph-rest-beta) | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) collection | Get a list of the [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) objects and their properties. |
| [List GCP authorization system type services](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list-services?view=graph-rest-beta) | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) collection | Get a list of the [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) objects and their properties. |
| [Get authorization system services](https://learn.microsoft.com/en-us/graph/api/authorizationsystemtypeservice-get?view=graph-rest-beta) | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) collection | Get the [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the service. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| actions | [authorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeaction?view=graph-rest-beta) collection | List of actions for the service in an authorization system that is onboarded to Permissions Management. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authorizationSystemTypeService",
  "id": "String (identifier)"
}
```
