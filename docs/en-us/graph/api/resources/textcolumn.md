<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/textcolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# TextColumn resource type

Namespace: microsoft.graph

The **textColumn** on a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) resource indicates that the column's values are text.

## JSON representation

Here is a JSON representation of a **textColumn** resource.

```json
{
  "allowMultipleLines": true,
  "appendChangesToExistingText": false,
  "linesForEditing": 6,
  "maxLength": 300,
  "textType": "plain | richText"
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **allowMultipleLines** | Boolean | Whether to allow multiple lines of text. |
| **appendChangesToExistingText** | Boolean | Whether updates to this column should replace existing text, or append to it. |
| **linesForEditing** | int32 | The size of the text box. |
| **maxLength** | int32 | The maximum number of characters for the value. |
| **textType** | string | The type of text being stored. Must be one of `plain` or `richText` |
