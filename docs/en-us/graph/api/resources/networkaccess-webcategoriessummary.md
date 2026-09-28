<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategoriessummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# webCategoriesSummary resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A summary of the users, devices, and transactions that recently accessed a web category.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceCount | Int32 | The number of unique devices that were seen. |
| transactionCount | Int32 | The number of transactions that were seen. |
| userCount | Int32 | The number of unique Microsoft Entra ID users that were seen. |
| webCategory | [microsoft.graph.networkaccess.webCategory](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webcategory?view=graph-rest-beta) | The website category. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.webCategoriesSummary",
  "webCategory": {
    "@odata.type": "microsoft.graph.networkaccess.webCategory"
  },
  "userCount": "Integer",
  "deviceCount": "Integer",
  "transactionCount": "Integer"
}
```
