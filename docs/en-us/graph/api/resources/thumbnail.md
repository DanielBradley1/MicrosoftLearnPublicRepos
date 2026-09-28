<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/thumbnail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# Thumbnail resource type

Namespace: microsoft.graph

The **thumbnail** resource type represents a thumbnail for an image, video, document, or any item that has a bitmap representation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The content stream for the thumbnail. |
| height | Int32 | The height of the thumbnail, in pixels. |
| sourceItemId | String | The unique identifier of the item that provided the thumbnail. This is only available when a folder thumbnail is requested. |
| url | String | The URL used to fetch the thumbnail content. |
| width | Int32 | The width of the thumbnail, in pixels. |

## JSON representation

Here is a JSON representation of the **thumbnail** resource.

```json
{
  "height": "Int32",
  "sourceItemId": "String",
  "url": "String",
  "width": "Int32",
  "content": "Stream"
}
```
