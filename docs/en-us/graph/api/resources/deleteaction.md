<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/deleteaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# deleteAction resource type

Namespace: microsoft.graph

The presence of the **deleteAction** resource on an [**itemActivity**](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) indicates that the activity deleted an item.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| name | string | The name of the item that was deleted. |
| objectType | string | `File` or `Folder`, depending on the type of the deleted item. |

## JSON representation

```json
{
  "name": "string",
  "objectType": "File | Folder"
}
```
