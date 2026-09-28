<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-product?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# product resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Windows product.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get known issues by time range](https://learn.microsoft.com/en-us/graph/api/windowsupdates-product-getknownissuesbytimerange?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.knownIssue](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-knownissue?view=graph-rest-beta) collection | Get known issues related to a particular product based on a specified timeframe in the past. |
| [Find by catalog ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-product-findbycatalogid?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.product](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-product?view=graph-rest-beta) collection | Find the product revisions associated with a catalog ID and the known issues directly or indirectly related to the catalog ID. |
| [Find by knowledge base number](https://learn.microsoft.com/en-us/graph/api/windowsupdates-product-findbykbnumber?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.product](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-product?view=graph-rest-beta) collection | Find the product revisions associated with a knowledge base number and the known issues directly or indirectly related to the knowledge base number. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| friendlyNames | String collection | The friendly names of the product. For example, `Version 22H2 (OS build 22621)`. Read-only. |
| groupName | String | The name of the product group. For example, `Windows 11`. Read-only. |
| id | String | The unique identifier for the product. Read-only. |
| name | String | The name of the product. For example, `Windows 11, version 22H2`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| editions | [microsoft.graph.windowsUpdates.edition](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-edition?view=graph-rest-beta) collection | Represents an edition of a particular Windows product. |
| knownIssues | [microsoft.graph.windowsUpdates.knownIssue](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-knownissue?view=graph-rest-beta) collection | Represents a known issue related to a Windows product. |
| revisions | [microsoft.graph.windowsUpdates.productRevision](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-productrevision?view=graph-rest-beta) collection | Represents a product revision. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.product",
  "friendlyNames": ["String"],
  "groupName": "String",
  "id": "String (identifier)",
  "name": "String",
  "releaseDateTime": "String (timestamp)"
}
```
