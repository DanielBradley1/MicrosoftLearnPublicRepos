<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/encryptedazurestorageaccountfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# encryptedAzureStorageAccountFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Represents the findings for Azure encrypted storage buckets.

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/encryptedazurestorageaccountfinding-list?view=graph-rest-beta) | [encryptedAzureStorageAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedazurestorageaccountfinding?view=graph-rest-beta) collection | Get a list of the [encryptedAzureStorageAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedazurestorageaccountfinding?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/encryptedazurestorageaccountfinding-get?view=graph-rest-beta) | [encryptedAzureStorageAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedazurestorageaccountfinding?view=graph-rest-beta) | Read the properties and relationships of an [encryptedAzureStorageAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedazurestorageaccountfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| encryptionManagedBy | azureEncryption | Specifies who manages encryption of Azure storage accounts. The possible values are: `microsoftStorage`, `microsoftKeyVault`, `customer`, `unknownFutureValue`. |
| id | String | Unique identifier for the Finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| storageAccount | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) | Represents a resource in an Azure authorization system. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.encryptedAzureStorageAccountFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "encryptionManagedBy": "String"
}
```
