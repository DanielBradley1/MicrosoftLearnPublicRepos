<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/thumbnailset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# ThumbnailSet resource type

Namespace: microsoft.graph

The **ThumbnailSet** resource is a keyed collection of [thumbnail](https://learn.microsoft.com/en-us/graph/api/resources/thumbnail?view=graph-rest-1.0) resources. It's used to represent a set of thumbnails associated with a DriveItem.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)",
  "large": { "@odata.type": "microsoft.graph.thumbnail" },
  "medium": { "@odata.type": "microsoft.graph.thumbnail" },
  "small": { "@odata.type": "microsoft.graph.thumbnail" },
  "source": { "@odata.type": "microsoft.graph.thumbnail" }
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID within the item. Read-only. |
| large | [Thumbnail](https://learn.microsoft.com/en-us/graph/api/resources/thumbnail?view=graph-rest-1.0) | A 1920x1920 scaled thumbnail. |
| medium | [Thumbnail](https://learn.microsoft.com/en-us/graph/api/resources/thumbnail?view=graph-rest-1.0) | A 176x176 scaled thumbnail. |
| small | [Thumbnail](https://learn.microsoft.com/en-us/graph/api/resources/thumbnail?view=graph-rest-1.0) | A 48x48 cropped thumbnail. |
| source | [Thumbnail](https://learn.microsoft.com/en-us/graph/api/resources/thumbnail?view=graph-rest-1.0) | A custom thumbnail image or the original image used to generate other thumbnails. |
