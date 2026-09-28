<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onedrive?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# Working with files in Microsoft Graph

You can use Microsoft Graph to create an app that connects with files across OneDrive, OneDrive for Business, and SharePoint document libraries. With Microsoft Graph, you can build a variety of experiences with files stored in Microsoft 365, from simply storing user documents to complex file-sharing scenarios.

Microsoft Graph exposes two resource types for working with files:

- [Drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) - Represents a logical container of files, like a document library or a user's OneDrive.
- [DriveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) - Represents an item within a drive, like a document, photo, video, or folder.

Most of the interaction with files occurs through interaction with **DriveItem** resources. The following is an example of a DriveItem resource:

```json
{
  "@content.downloadUrl":"https://public-sn3302.files.1drv.com/y2pcT7OaUEExF7EHOlpTjCE55mIUoiX7H3sx1ff6I-nP35XUTBqZlnkh9FJhWb_pf9sZ7LEpEchvDznIbQig0hWBeidpwFkOqSKCwQylisarN6T0ecAeMvantizBUzM2PA1",
  "createdDateTime": "2016-09-16T03:37:04.72Z",
  "cTag": "aYzpENDY0OEYwNkM5MUQ5RDNEITU0OTI3LjI1Ng",
  "eTag": "aRDQ2NDhGMDZDOTFEOUQzRCE1NDkyNy4w",
  "id":"D4648F06C91D9D3D!54927",
  "lastModifiedBy": {
    "user": {
      "displayName": "Daron Spektor",
      "id": "d4648f06c91d9d3d"
    }
  },
  "name":"BritishShorthair.jpg",
  "size":35212,
  "image":{
    "height":398,
    "width":273
  },
  "file": {
    "hashes":{
      "sha1Hash":"wmgPQ6jrSeMX7JP1XmstQEGM2fc="
    }
  }
}
```

**Drive** and **DriveItem** resources expose data in three different ways:

- *Properties* \(like **id** and **name**\) expose simple values \(strings, numbers, Booleans\).
- *Facets* \(like **file** and **image**\) expose complex values. The presence of **file** or **folder** facets indicates behaviors and properties of a **DriveItem**.
- *References* \(like **children** and **thumbnails**\) point to collections of other resources.

## Commonly accessed resources

Most API requests for file interactions will use one of these base resources to access a **Drive** or **DriveItem**.

| Path | Resource |
| --- | --- |
| `/me/drive` | User's OneDrive |
| `/me/drives` | Enumerate OneDrive resources available to the user. |
| `/drives/{drive-id}` | Access a specific **Drive** by the drive's ID. |
| `/drives/{drive-id}/root/children` | Enumerate the **DriveItem** resources in the root of a specific **Drive**. |
| `/me/drive/items/{item-id}` | Access a **DriveItem** in the user's OneDrive by its unique ID. |
| `/me/drive/special/{special-id}` | Access a special \(named\) folder in the user's OneDrive by its known name. |
| `/users/{user-id}/drive` | Access another user's OneDrive by using the user's unique ID. |
| `/groups/{group-id}/drive` | Access the default document library for a group by the group's unique ID. |
| `/shares/{share-id}` | Access a **DriveItem** by its **sharedId** or sharing URL. |
| `/sites/{site-id}/drive` | Access the default **Drive** \(document library\) for the given [SharePoint](https://learn.microsoft.com/en-us/graph/api/resources/sharepoint?view=graph-rest-1.0) [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) |
| `/sites/{site-id}/drives` | Enumerate the **Drives** \(document libraries\) under the given [SharePoint](https://learn.microsoft.com/en-us/graph/api/resources/sharepoint?view=graph-rest-1.0) [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) |

In addition to addressing a **DriveItem** within a **Drive** by unique ID, your app can also address a **DriveItem** by relative path from a known resource. To address using a path, the colon \(`:`\) character is used to escape the relative path. This table provides an example of different ways to use the colon character to address an item by path.

| Path | Resource |
| --- | --- |
| `/me/drive/root:/path/to/file` | Access a **DriveItem** by path relative to the user's OneDrive root folder. |
| `/me/drive/items/{item-id}:/path/to/file` | Access a **DriveItem** by path relative to another item \(a **DriveItem** with a **folder** facet\). |
| `/me/drive/root:/path/to/folder:/children` | List the children of a **DriveItem** by path relative to the root of the user's OneDrive. |
| `/me/drive/items/{item-id}:/path/to/folder:/children` | List the children of a **DriveItem** by path relative to another item. |

For more information, see [addressing driveItems](https://learn.microsoft.com/en-us/graph/onedrive-addressing-driveitems).

## Drive resource

The [Drive resource](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) is the top-level object within a user's OneDrive or a [SharePoint](https://learn.microsoft.com/en-us/graph/api/resources/sharepoint?view=graph-rest-1.0) document library. Nearly all files operations will start by addressing a specific drive resource.

A drive resource can be addressed either by the drive's unique ID or by the default drive for a [User](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), [Group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0), or organization.

## DriveItem resource

[DriveItems](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) are the objects inside a drive's file system. They can be accessed by their **id** by using `/items/{item-id}` syntax, or by their file system path using the `/root:/path/to/item/` syntax.

DriveItems have *facets* that provide data about the item's identity and capabilities.

DriveItems with a **folder** facet act as containers of items, and have a **children** reference, which points to a collection of items under the folder.

## Shared folders and remote items

OneDrive personal users can add one or more shared items from another drive to their own OneDrive. These shared items appear as a **DriveItem** in the **children** collection with a [remoteItem](https://learn.microsoft.com/en-us/graph/api/resources/remoteitem?view=graph-rest-1.0) facet.

For more information about working with shared folders and remote items, see [Remote items and shared folders](https://learn.microsoft.com/en-us/graph/api/resources/remoteitem?view=graph-rest-1.0).

## Sharing and permissions

One of the most common actions for OneDrive and SharePoint document libraries is sharing content with other people. Microsoft Graph allows your app to create [sharing links](https://learn.microsoft.com/en-us/graph/api/driveitem-createlink?view=graph-rest-1.0), [add permissions and send invitations](https://learn.microsoft.com/en-us/graph/api/driveitem-invite?view=graph-rest-1.0) to items in a drive.

Microsoft Graph also provides a way for your app to [access shared content](https://learn.microsoft.com/en-us/graph/api/shares-get?view=graph-rest-1.0) directly from a sharing link.
