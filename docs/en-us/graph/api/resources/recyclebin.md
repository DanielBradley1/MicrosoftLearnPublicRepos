<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# recycleBin resource type

Namespace: microsoft.graph

Represents a container for a collection of [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) resources in a SharePoint Embedded [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0).

Inherits from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List items](https://learn.microsoft.com/en-us/graph/api/recyclebin-list-items?view=graph-rest-1.0) | [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) collection | Get a collection of [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) resources in the [recycleBin](https://learn.microsoft.com/en-us/graph/api/resources/recyclebin?view=graph-rest-1.0) of the specified SharePoint Embedded [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the **recycleBin** object. Requires `$select` to retrieve. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| items | [recycleBinItem](https://learn.microsoft.com/en-us/graph/api/resources/recyclebinitem?view=graph-rest-1.0) collection | List of the **recycleBinItems** deleted by a user. |

## JSON Representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
}
```
