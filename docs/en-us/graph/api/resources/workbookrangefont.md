<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefont?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# workbookRangeFont resource type

Namespace: microsoft.graph

This object represents the font attributes \(font name, font size, color, etc.\) for an object.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/rangefont-get?view=graph-rest-1.0) | [workbookRangeFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefont?view=graph-rest-1.0) | Read the properties and relationships of a workbookRangeFont object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/rangefont-update?view=graph-rest-1.0) | [workbookRangeFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefont?view=graph-rest-1.0) | Update a workbookRangeFont object |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bold | Boolean | Inidicates whether the font is bold. |
| color | string | The HTML color code representation of the text color. For example, #FF0000 represents the color red. |
| italic | Boolean | Inidicates whether the font is italic. |
| name | string | The font name. For example, "Calibri". |
| size | double | The font size. |
| underline | string | The type of underlining applied to the font. The possible values are: `None`, `Single`, `Double`, `SingleAccountant`, `DoubleAccountant`. |

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
