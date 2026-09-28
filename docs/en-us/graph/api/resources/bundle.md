<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bundle?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# bundle resource type

Namespace: microsoft.graph

A bundle is a logical grouping of files used to share multiple files at once. It is represented by a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) entity containing a `bundle` facet and can be shared in the same way as any other driveItem.

The `bundle` facet on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) identifies an item as a bundle and groups bundle-specific information into a single structure. It is only included on [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resources returned from the **bundles** endpoint.

Note that the `bundle` resource type itself is not an entity of its own, and is only a facet on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0). The `bundles` collection on a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) is of type [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0), not `bundle`.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List bundles](https://learn.microsoft.com/en-us/graph/api/bundle-list?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | List all bundles in a drive |
| [Get bundle](https://learn.microsoft.com/en-us/graph/api/bundle-get?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Get bundle metadata |
| [Create bundle](https://learn.microsoft.com/en-us/graph/api/drive-post-bundles?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Create a new bundle |
| [Add item](https://learn.microsoft.com/en-us/graph/api/bundle-additem?view=graph-rest-1.0) | None | Add a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) to an existing bundle |
| [Remove item](https://learn.microsoft.com/en-us/graph/api/bundle-removeitem?view=graph-rest-1.0) | None | Remove a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) from an existing bundle |
| [Update bundle](https://learn.microsoft.com/en-us/graph/api/bundle-update?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Update bundle metadata |
| [Delete bundle](https://learn.microsoft.com/en-us/graph/api/bundle-delete?view=graph-rest-1.0) | None | Delete bundle |

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| album | [album](https://learn.microsoft.com/en-us/graph/api/resources/album?view=graph-rest-1.0) | If the bundle is an [album](https://learn.microsoft.com/en-us/graph/api/resources/album?view=graph-rest-1.0), then the `album` property is included |
| childCount | Int32 | Number of children contained immediately within this container. |

## JSON representation

```json
{
  "album": { "@odata.type": "microsoft.graph.album" },
  "childCount": 3
}
```
