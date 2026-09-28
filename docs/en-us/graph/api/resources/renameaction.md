<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/renameaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# renameAction resource type

Namespace: microsoft.graph

The presence of the **renameAction** resource on an [**itemActivity**](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) indicates that the activity renamed an item.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| newName | string | The new name of the item. |
| oldName | string | The previous name of the item. |

## JSON representation

```json
{
  "oldName": "string",
  "newName": "string"
}
```
