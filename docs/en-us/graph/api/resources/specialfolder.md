<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/specialfolder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# SpecialFolder resource type

Namespace: microsoft.graph

The **SpecialFolder** resource groups special folder-related data items into a single structure.

If a **DriveItem** has a non-null **specialFolder** facet, the item represents a special \(named\) folder. Special folders can be accessed directly via the [special folders collection](https://learn.microsoft.com/en-us/graph/api/drive-get-specialfolder?view=graph-rest-1.0).

Special folders provide simple aliases to access well-known folders without the need to look up the folder by path \(which would require localization\), or reference the folder with an ID. If a special folder is renamed or moved to another location within the drive, this syntax will continue to return that folder.

Special folders are automatically created the first time an application attempts to write to one, if it doesn't already exist. If a user deletes one, it is recreated when written to again.

**Note:** If your app has only requested **Files.Read** scope and requests a special folder that doesn't exist, the response will be a `403 Forbidden` error.

## JSON representation

```json
{
  "name": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | string | The unique identifier for this item in the `/drive/special` collection |

## Special folders

Here are the special folders available in OneDrive Personal and OneDrive for Business.

| Name | Folder id | Description |
| :--- | :--- | :--- |
| App Root | `approot` | The application's personal folder. Usually in `/Apps/{Application Name}` |
| Camera Roll | `cameraroll` | The Camera Roll Backup folder. Not available in OneDrive for Business. |
| Documents | `documents` | The Documents folder. |
| Music | `music` | The Music folder. Not available in OneDrive for Business. |
| Photos | `photos` | The Photos folder. |

## Remarks

For more information about the facets on a DriveItem, see [DriveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
