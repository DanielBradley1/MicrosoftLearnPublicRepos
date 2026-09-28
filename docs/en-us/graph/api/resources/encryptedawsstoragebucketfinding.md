<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/encryptedawsstoragebucketfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# encryptedAwsStorageBucketFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the findings for AWS encrypted storage buckets.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/encryptedawsstoragebucketfinding-list?view=graph-rest-beta) | [encryptedAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedawsstoragebucketfinding?view=graph-rest-beta) collection | Get a list of the [encryptedAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedawsstoragebucketfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/encryptedawsstoragebucketfinding-get?view=graph-rest-beta) | [encryptedAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedawsstoragebucketfinding?view=graph-rest-beta) | Read the properties and relationships of an [encryptedAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedawsstoragebucketfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessibility | awsAccessType | Aws resources access type. The possible values are: `public`, `restricted`, `crossAccount`, `private`, `unknownFutureValue`. |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| storageBucket | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) | Represents a resource in an AWS authorization system. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.encryptedAwsStorageBucketFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "accessibility": "String"
}
```
