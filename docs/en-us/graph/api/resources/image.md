<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/image?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# image resource type

Namespace: microsoft.graph

The **image** resource groups image-related properties into a single structure. If a [**driveItem**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) has a non-null **image** facet, the item represents a bitmap image.

> **Note:** If the service is unable to determine the width and height of the image, the **image** resource may be empty.

## JSON representation

```json
{
  "width": 100,
  "height": 200
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **height** | Int32 | Optional. Height of the image, in pixels. Read-only. |
| **width** | Int32 | Optional. Width of the image, in pixels. Read-only. |

## Remarks

In OneDrive for Business, this resource is returned on items that are expected to be images based on file extension.

For more information about the facets on a DriveItem, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
