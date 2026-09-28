<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfont?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# workbookChartFont resource type

Namespace: microsoft.graph

This object represents the font attributes \(font name, font size, color, etc.\) for a chart object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartfont-get?view=graph-rest-1.0) | [workbookChartFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfont?view=graph-rest-1.0) | Read the properties and relationships of a chartFont object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chartfont-update?view=graph-rest-1.0) | [workbookChartFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfont?view=graph-rest-1.0) | Update a chartFont object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bold | Boolean | Indicates whether the fond is bold. |
| color | string | The HTML color code representation of the text color. For example #FF0000 represents Red. |
| italic | Boolean | Indicates whether the fond is italic. |
| name | string | The font name. For example "Calibri". |
| size | double | The size of the font. For example, 11. |
| underline | string | The type of underlining applied to the font. The possible values are: `None`, `Single`. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "bold": true,
  "color": "string",
  "italic": true,
  "name": "string",
  "size": 1024,
  "underline": "string"
}
```
