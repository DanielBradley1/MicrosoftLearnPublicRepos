<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/album?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# album resource type

Namespace: microsoft.graph

A photo album is a way to virtually group [driveItems](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) with [photo](https://learn.microsoft.com/en-us/graph/api/resources/photo?view=graph-rest-1.0) facets together in a [bundle](https://learn.microsoft.com/en-us/graph/api/resources/bundle?view=graph-rest-1.0). Bundles of this type have the **album** property set on the [bundle](https://learn.microsoft.com/en-us/graph/api/resources/bundle?view=graph-rest-1.0) resource.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| coverImageItemId | String | Unique identifier of the [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) that is the cover of the album. |

**Note:** If a **coverImageItemId** hasn't been set before, the thumbnails for an album are chosen automatically. After **coverImageItemId** has been set, the thumbnails for an album will always be the item associated with that ID. You can override the default cover by PATCHing the [bundle item](https://learn.microsoft.com/en-us/graph/api/resources/bundle?view=graph-rest-1.0) and setting the **coverImageItemId** property on the `album` to the ID of an image contained within the album. To remove a custom-set cover, you can set the **coverImageItemId** property to null, and a default one will be chosen automatically again.

## JSON representation

```json
{
  "coverImageItemId": "string"
}
```
