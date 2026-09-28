<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/deleted?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# Deleted facet

Namespace: microsoft.graph

The **Deleted** resource indicates that the item has been deleted. In this version of the API, the presence \(non-null\) of the resource value indicates that the file was deleted. A null \(or missing\) value indicates that the file is not deleted.

See [view changes for an item](https://learn.microsoft.com/en-us/graph/api/driveitem-delta?view=graph-rest-1.0) for more information on tracking changes and finding deleted items.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "state": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| state | String | Represents the state of the deleted item. |

## Remarks

For more information about the facets on a DriveItem, see [DriveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
