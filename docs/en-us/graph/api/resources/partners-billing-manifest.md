<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-manifest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# manifest resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents metadata for the exported data. Use the metadata to get details of the file you want to download from an Azure Blob Storage.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/partners-billing-manifest-get?view=graph-rest-1.0) | [microsoft.graph.partners.billing.manifest](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-manifest?view=graph-rest-1.0) | Read the properties and relationships of a [manifest](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-manifest?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blobCount | Int32 | The total file count for this partner tenant ID. |
| blobs | [microsoft.graph.partners.billing.blob](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-blob?view=graph-rest-1.0) collection | A collection of blob objects that contain details of all the files for the partner tenant ID. |
| createdDateTime | DateTimeOffset | The date and time when a manifest resource was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| dataFormat | String | The billing data file format. The possible value is: `compressedJSONLines`. Each blob is a compressed file and data in the file is in [JSON lines](https://jsonlines.org/) format. Decompress the file to access the data. |
| eTag | String | Version of data represented by the manifest. Any change in **eTag** indicates a new data version. |
| id | String | The unique identifier for the **manifest**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| partitionType | String | Indicates the division of data. If a given partition has more than the supported number, the data is split into multiple files, each file representing a specific **partitionValue**. By default, the data in the file is partitioned by the number of line items. |
| partnerTenantId | String | The Microsoft Entra tenant ID of the partner. |
| rootDirectory | String | The root directory that contains all the files. |
| sasToken | String | The SAS token for accessing the directory or an individual file in the directory. |
| schemaVersion | String | The version of the manifest schema. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "blobCount": "Int32",
  "blobs": [{"@odata.type": "microsoft.graph.partners.billing.blob"}],
  "createdDateTime": "String (timestamp)",
  "dataFormat": "String",
  "eTag": "String",
  "id": "String (identifier)",
  "partitionType": "String",
  "partnerTenantId": "String",
  "rootDirectory": "String",
  "sasToken": "String",
  "schemaVersion": "String"
}
```
