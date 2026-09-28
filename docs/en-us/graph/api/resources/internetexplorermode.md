<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/internetexplorermode?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# internetExplorerMode resource type

Namespace: microsoft.graph

Represents a container for [Internet Explorer mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode) resources.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/internetexplorermode-list-sitelists?view=graph-rest-1.0) | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) collection | Get a list of the [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/internetexplorermode-post-sitelists?view=graph-rest-1.0) | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) | Create a new [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) object to support [Internet Explorer mode](https://learn.microsoft.com/en-us/deployedge/edge-ie-mode). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/internetexplorermode-delete-sitelists?view=graph-rest-1.0) | None | Delete a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) object. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| siteLists | [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) collection | A collection of site lists to support Internet Explorer mode. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.internetExplorerMode"
}
```
