<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-transactionsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# transactionSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains information about network transactions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| blockedCount | Int32 | The number of transactions that were blocked. |
| totalCount | Int32 | The total number of transactions. |
| trafficType | microsoft.graph.networkaccess.trafficType | The trraffic classification. The possible values are `internet`, `private`, `microsoft365`, and `all`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.transactionSummary",
  "trafficType": "String",
  "totalCount": "Integer",
  "blockedCount": "Integer"
}
```
