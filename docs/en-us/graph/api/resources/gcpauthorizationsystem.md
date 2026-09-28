<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# gcpAuthorizationSystem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents a GCP authorization system onboarded to Permissions Management.

Inherits from [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/gcpauthorizationsystem-list?view=graph-rest-beta) | [gcpAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystem?view=graph-rest-beta) collection | Get a list of the [gcpAuthorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystem?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| associatedIdentities | [gcpAssociatedIdentities](https://learn.microsoft.com/en-us/graph/api/resources/gcpassociatedidentities?view=graph-rest-beta) | Identities in the authorization system.\* |
| authorizationSystemId | String | ID of the authorization system retrieved from the customer cloud environment.Supports `$filter`\(`eq`, `contains`\) and `$orderBy`. Inherited from [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta). |
| authorizationSystemName | String | Name of the authorization system detected after onboarding. Supports `$filter`\(`eq`,`contains`\) and `$orderBy`. Inherited from [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta). |
| authorizationSystemType | String | The type of this authorization system. Supports `$filter`\(`eq`\). Inherited from [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta). |
| id | String | Unique ID for the authorization system in Permissions Management. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| actions | [gcpAuthorizationSystemTypeAction](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemtypeaction?view=graph-rest-beta) collection | List of actions for service in authorization system. |
| dataCollectionInfo | [dataCollectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/datacollectioninfo?view=graph-rest-beta) | Used to expose data collection status of this authorizationSystem. Inherited from [microsoft.graph.authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) |
| resources | [gcpAuthorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/gcpauthorizationsystemresource?view=graph-rest-beta) collection | Resources associated with the authorization system type. |
| roles | [gcpRole](https://learn.microsoft.com/en-us/graph/api/resources/gcprole?view=graph-rest-beta) collection | Roles associated with the authorization system type. |
| services | [authorizationSystemTypeService](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemtypeservice?view=graph-rest-beta) collection | Services associated with the authorization system type. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.gcpAuthorizationSystem",
  "id": "String (identifier)",
  "authorizationSystemId": "String",
  "authorizationSystemName": "String",
  "authorizationSystemType": "String"
}
```
