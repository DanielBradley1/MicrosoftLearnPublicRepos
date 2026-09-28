<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/file?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# File resource type

Namespace: microsoft.graph

The **File** resource groups file-related data items into a single structure.

If a [**DriveItem**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) has a non-null **file** facet, the item represents a file. In addition to other properties, files have a **content** relationship that contains the byte stream of the file.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hashes": {"@odata.type": "microsoft.graph.hashes"},
  "mimeType": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hashes | [Hashes](https://learn.microsoft.com/en-us/graph/api/resources/hashes?view=graph-rest-1.0) | Hashes of the file's binary content, if available. Read-only. |
| mimeType | string | The MIME type for the file. This is determined by logic on the server and might not be the value provided when the file was uploaded. Read-only. |

## Remarks

For more information about the facets on a DriveItem, see [DriveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
