<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/folder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# Folder resource type

Namespace: microsoft.graph

The **Folder** resource groups folder-related data on an item into a single structure. [**DriveItems**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) with a non-null **folder** facet are containers for other DriveItems.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "childCount": 1024,
  "view": { "@odata.type": "microsoft.graph.folderView" }
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **childCount** | Int32 | Number of children contained immediately within this container. |
| **view** | [folderView](https://learn.microsoft.com/en-us/graph/api/resources/folderview?view=graph-rest-1.0) | A collection of properties defining the recommended view for the folder. |

## Remarks

For more information about the facets on a DriveItem, see [DriveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
