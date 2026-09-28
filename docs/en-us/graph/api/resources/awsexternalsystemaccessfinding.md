<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# awsExternalSystemAccessFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents findings related to external accounts that are able to access a given AWS account.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/awsexternalsystemaccessfinding-list?view=graph-rest-beta) | [awsExternalSystemAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessfinding?view=graph-rest-beta) collection | Get a list of the [awsExternalSystemAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/awsexternalsystemaccessfinding-get?view=graph-rest-beta) | [awsExternalSystemAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessfinding?view=graph-rest-beta) | Read the properties and relationships of an [awsExternalSystemAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessMethods | externalSystemAccessMethods | Specifies if the system can be accessed directly, via role chaining, or both. The possible values are: `direct`, `roleChaining`, `unknownFutureValue`. Supports `$filter` \(`eq`\). |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| systemWithAccessId | string | The account ID for the external system that is able to access the given system. |
| systemWithAccess | [authorizationSystemInfo](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsysteminfo?view=graph-rest-beta) | The external system that is able to access the given system. |
| trustedIdentityCount | Int32 | The number of identities in the external system that are trusted, if not all. Supports `$orderby`. |
| trustsAllIdentities | Boolean | Flag that determines if all identities in the external system are trusted, or only a subset. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| affectedSystem | [authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) | The system that can be accessed from an external system. Supports `$orderby` \(`affectedSystem/authorizationSystemName`\) and `$filter` as follows: `$filter=affectedSystem/authorizationSystemId IN ['authorizationSystemIds']` |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.awsExternalSystemAccessFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "trustsAllIdentities": "Boolean",
  "accessMethods": "String",
  "trustedIdentityCount": "Integer",
  "systemWithAccess": {
    "@odata.type": "microsoft.graph.authorizationSystemInfo"
  }
}
```
