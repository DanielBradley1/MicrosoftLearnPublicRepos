<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleazureblobcontainerfinding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# externallyAccessibleAzureBlobContainerFinding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Get insights into Azure blob containers that are accessible externally

Inherits from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List externallyAccessibleAzureBlobContainerFinding objects](https://learn.microsoft.com/en-us/graph/api/externallyaccessibleazureblobcontainerfinding-list?view=graph-rest-beta) | [externallyAccessibleAzureBlobContainerFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleazureblobcontainerfinding?view=graph-rest-beta) collection | Get a list of the [externallyAccessibleAzureBlobContainerFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleazureblobcontainerfinding?view=graph-rest-beta) objects and their properties. |
| [Get externallyAccessibleAzureBlobContainerFinding](https://learn.microsoft.com/en-us/graph/api/externallyaccessibleazureblobcontainerfinding-get?view=graph-rest-beta) | [externallyAccessibleAzureBlobContainerFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleazureblobcontainerfinding?view=graph-rest-beta) | Read the properties and relationships of an [externallyAccessibleAzureBlobContainerFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleazureblobcontainerfinding?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessibility | azureAccessType | resources access type.The possible values are: `public`, `private`, `unknownFutureValue`. |
| createdDateTime | DateTimeOffset | Defines when the finding was created. Inherited from [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta). |
| encryptionManagedBy | azureEncryption | Specifies who manages encryption of Azure storage accounts.The possible values are: `microsoftStorage`, `microsoftKeyVault`, `customer`, `unknownFutureValue`. |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| storageAccount | [authorizationSystemResource](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystemresource?view=graph-rest-beta) | Represents a resource in an authorization system |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externallyAccessibleAzureBlobContainerFinding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "accessibility": "String",
  "encryptionManagedBy": "String"
}
```
