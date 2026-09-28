<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationcontainerinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationContainerInfo resource type

Namespace: microsoft.graph

Contains the Azure blob container URLs and the key for content encryption. The Azure containers are used as temporary storage for migration content and metadata.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataContainerUri | String | A valid URL with a SAS token for accessing the Azure blob storage container that contains the file content. Read-only. |
| encryptionKey | String | Provides the AES-256-CBC encryption key if files stored in Azure blob containers are encrypted. The key is Base64-encoded. Read-only. |
| metadataContainerUri | String | A valid URL with a SAS token for accessing the Azure blob storage container that contains the file metadata. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationContainerInfo",
  "dataContainerUri": "String",
  "encryptionKey": "String",
  "metadataContainerUri": "String"
}
```
