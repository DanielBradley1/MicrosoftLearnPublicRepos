<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcforensicstorageaccount?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-23 -->

# cloudPcForensicStorageAccount resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the storage account information that can be used to store a snapshot or snapshots of a Cloud PC for forensic analysis.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessTier | [cloudPcStorageAccountAccessTier](#cloudpcstorageaccountaccesstier-values) | Indicates the access tier of the storage account. Possible values are `hot`, `cool`, `premium`, `cold`, and `unknownFutureValue`. Default value is `hot`. Read-only. |
| immutableStorage | Boolean | Indicates whether immutability policies are configured for the storage account. When `true`, the storage account only accepts `hot` as the snapshot access tier. When `false`, the storage account accepts all valid access tiers. Read-Only. |
| storageAccountId | String | Indicates the ID of the storage account. Read-only. |
| storageAccountName | String | Indicates the name of the storage account. Read-only. |

### cloudPcStorageAccountAccessTier values

| Member | Description |
| :--- | :--- |
| hot | The storage account access tier is "hot." This tier is optimized for storing data that is accessed or modified frequently. |
| cool | The storage account access tier is "cool." This tier is optimized for storing data that is infrequently accessed or modified. |
| premium | The storage account access tier is "premium." This tier is optimized with low and consistent latency. |
| cold | The storage account access tier is "cold." This tier is optimized for storing data that is rarely accessed or modified, but still requires fast retrieval. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcForensicStorageAccount",
  "storageAccountId": "String",
  "storageAccountName": "String",
  "immutableStorage": "Boolean",
  "accessTier": "String"
}
```
