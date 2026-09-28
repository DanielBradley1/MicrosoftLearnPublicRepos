<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# recycleBinItem resource type

Namespace: microsoft.graph

Represents information about a deleted item in a [recycleBin](https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0) of a SharePoint Embedded [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0).

Inherits from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/recyclebin-list-items?view=graph-rest-1.0) | [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) collection | Get a collection of [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) resources in the [recycleBin](https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0) of the specified SharePoint Embedded [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-delete-recyclebinitem?view=graph-rest-1.0) | None. | Permanently delete **recycleBinItem** objects from the [recycleBin](https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0) of a **fileStorageContainer**. |
| [Restore recycleBinItem by driveItemId](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-restore-recyclebinitem?view=graph-rest-1.0) Restore recycle bin items by driveItemId. |  |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Date and time when the item was deleted. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| deletedFromLocation | String | Relative URL of the list or folder that originally contained the item. |
| id | String | Unique identifier of the delete transaction. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| name | String | Name of the item. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| size | Int64 | Size of the item in bytes. |

## JSON Representation

The following JSON representation shows the resource type.

```json
{
  "deletedDateTime": "String (timestamp)",
  "deletedFromLocation": "String",
  "id": "String (identifier)",
  "name": "String",
  "size": "Int64"
}
```
