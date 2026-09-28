<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# driveItemVersion resource type

Namespace: microsoft.graph

Represents a specific version of a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/driveitem-list-versions?view=graph-rest-1.0) | [driveItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) collection | Retrieve the [versions](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) of a [file](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/driveitemversion-get?view=graph-rest-1.0) | [driveItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) | Retrieve the metadata for a specific [version](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) of a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0). |
| [Download version](https://learn.microsoft.com/en-us/graph/api/driveitemversion-get-contents?view=graph-rest-1.0) | download URL | Retrieve the contents of a specific [version](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) of a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0). |
| [Restore version](https://learn.microsoft.com/en-us/graph/api/driveitemversion-restoreversion?view=graph-rest-1.0) | None | Restore a previous [version](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) of a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) to be the current **version**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The content stream for this version of the item. |
| id | String | The ID of the version. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user who last modified the version. Read-only. |
| lastModifiedDateTime | [DateTimeOffset](https://learn.microsoft.com/en-us/graph/api/resources/timestamp?view=graph-rest-1.0) | Date and time when the version was last modified. Read-only. |
| publication | [publicationFacet](https://learn.microsoft.com/en-us/graph/api/resources/publicationfacet?view=graph-rest-1.0) | Indicates the publication status of this particular version. Read-only. |
| size | Int64 | Indicates the size of the content stream for this version of the item. |

## Instance attributes

| Property name | Type | Description |
| :--- | :--- | :--- |
| @microsoft.graph.downloadUrl | string | A URL that can be used to download this version of the file's content. Authentication is not required with this URL. Read-only. |

> **Notes:** The `@microsoft.graph.downloadUrl` value is a short-lived URL and can't be cached. The URL is only available for a short period of time \(1 hour\) before it is invalidated. Removing file permissions for a user might not immediately invalidate the URL.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "content": { "@odata.type": "Edm.Stream" },
  "id": "String",
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "String (timestamp)",
  "publication": { "@odata.type": "microsoft.graph.publicationFacet" },
  "size": "Int64",

  /* instance annotations */
  "@microsoft.graph.downloadUrl": "url",
}
```
