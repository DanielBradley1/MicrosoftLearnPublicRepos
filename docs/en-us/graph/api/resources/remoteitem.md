<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/remoteitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# remoteItem resource type

Namespace: microsoft.graph

The **remoteItem** resource indicates that a [**driveItem**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) references an item that exists in another drive. This resource provides the unique IDs of the source drive and target item.

[**driveItems**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) with a non-null **remoteItem** facet are resources that are shared, added to the user's OneDrive, or on items returned from heterogeneous collections of items \(like search results\).

> **Note:** Unlike with folders in the same drive, a **driveItem** moved into a remote item may have its `id` value changed.

## JSON representation

```json
{
  "id": "string",
  "createdBy": { "@odata.type": "microsoft.graph.identitySet" },
  "createdDateTime": "timestamp",
  "file": { "@odata.type": "microsoft.graph.file" },
  "fileSystemInfo": { "@odata.type": "microsoft.graph.fileSystemInfo" },
  "folder": { "@odata.type": "microsoft.graph.folder" },
  "image" : { "@odata.type": "microsoft.graph.image" },
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "timestamp",
  "name": "string",
  "package": { "@odata.type": "microsoft.graph.package" },
  "parentReference": { "@odata.type": "microsoft.graph.itemReference" },
  "shared": { "@odata.type": "microsoft.graph.shared" },
  "sharepointIds": { "@odata.type": "microsoft.graph.sharepointIds" },
  "specialFolder": { "@odata.type": "microsoft.graph.specialFolder" },
  "size": 1024,
  "video": { "@odata.type": "microsoft.graph.video" },
  "webDavUrl": "url",
  "webUrl": "url"
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| createdBy | [IdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which created the item. Read-only. |
| createdDateTime | Timestamp | Date and time of item creation. Read-only. |
| file | [File](https://learn.microsoft.com/en-us/graph/api/resources/file?view=graph-rest-1.0) | Indicates that the remote item is a file. Read-only. |
| fileSystemInfo | [FileSystemInfo](https://learn.microsoft.com/en-us/graph/api/resources/filesysteminfo?view=graph-rest-1.0) | Information about the remote item from the local file system. Read-only. |
| folder | [Folder](https://learn.microsoft.com/en-us/graph/api/resources/folder?view=graph-rest-1.0) | Indicates that the remote item is a folder. Read-only. |
| id | String | Unique identifier for the remote item in its drive. Read-only. |
| image | [Image](https://learn.microsoft.com/en-us/graph/api/resources/image?view=graph-rest-1.0) | Image metadata, if the item is an image. Read-only. |
| lastModifiedBy | [IdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which last modified the item. Read-only. |
| lastModifiedDateTime | Timestamp | Date and time the item was last modified. Read-only. |
| name | String | Optional. Filename of the remote item. Read-only. |
| package | [Package](https://learn.microsoft.com/en-us/graph/api/resources/package?view=graph-rest-1.0) | If present, indicates that this item is a package instead of a folder or file. Packages are treated like files in some contexts and folders in others. Read-only. |
| parentReference | [ItemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | Properties of the parent of the remote item. Read-only. |
| shared | [shared](https://learn.microsoft.com/en-us/graph/api/resources/shared?view=graph-rest-1.0) | Indicates that the item has been shared with others and provides information about the shared state of the item. Read-only. |
| sharepointIds | [SharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-1.0) | Provides interop between items in OneDrive for Business and SharePoint with the full set of item identifiers. Read-only. |
| size | Int64 | Size of the remote item. Read-only. |
| specialFolder | [specialFolder](https://learn.microsoft.com/en-us/graph/api/resources/specialfolder?view=graph-rest-1.0) | If the current item is also available as a special folder, this facet is returned. Read-only. |
| video | [Video](https://learn.microsoft.com/en-us/graph/api/resources/video?view=graph-rest-1.0) | Video metadata, if the item is a video. Read-only. |
| webDavUrl | Url | DAV compatible URL for the item. |
| webUrl | Url | URL that displays the resource in the browser. Read-only. |

## Remarks

For more information about the facets on a **driveItem**, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
