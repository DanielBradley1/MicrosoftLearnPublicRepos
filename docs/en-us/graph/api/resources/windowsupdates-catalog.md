<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalog?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# catalog resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Entity representing the catalog of content that you can approve for deployment.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List catalog entries](https://learn.microsoft.com/en-us/graph/api/windowsupdates-catalog-list-entries?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) collection | Get the [catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) resources from the entries navigation property. Returns **catalogEntry** resources of the following derived types: [featureUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatecatalogentry?view=graph-rest-beta), [qualityUpdateCatalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatecatalogentry?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | An identifier for the catalog. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| entries | [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) collection | Lists the content that you can approve for deployment. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.catalog",
  "id": "String (identifier)"
}
```
