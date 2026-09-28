<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstorageblobdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# cloudPcStorageBlobDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the detailed hierarchical resource information of the Azure storage blob, including the storage account and container as the parent resources of the blob, and the blob file name.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| containerName | String | Indicates the name of the container. For example, `mycontainer`. |
| fileName | String | The name of the file stored in the container. For example, `myexportedvm.vhd`. |
| storageAccountId | String | Indicates the unique identifier for the Azure storage account. For example, `/subscriptions/0231ef39-1113-4772-bffe-26e7d8a15c9e/resourceGroups/myresourcegroup/providers/Microsoft.Storage/storageAccounts/mystorageaccount.` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcStorageBlobDetail",
  "containerName": "String",
  "fileName": "String",
  "storageAccountId": "String"
}
```
