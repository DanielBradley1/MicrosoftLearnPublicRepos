<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# workbookRangeFormat resource type

Namespace: microsoft.graph

A format object encapsulating the range's font, fill, borders, alignment, and other properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/rangeformat-get?view=graph-rest-1.0) | [workbookRangeFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeformat?view=graph-rest-1.0) | Read properties and relationships of rangeFormat object. |
| [Update range format](https://learn.microsoft.com/en-us/graph/api/rangeformat-update?view=graph-rest-1.0) | [workbookRangeFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeformat?view=graph-rest-1.0) | Update RangeFormat object. |
| [List range borders](https://learn.microsoft.com/en-us/graph/api/rangeformat-list-borders?view=graph-rest-1.0) | [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0) collection | Get the list of workbookRangeBorder objects. |
| [Create range borders](https://learn.microsoft.com/en-us/graph/api/rangeformat-post-borders?view=graph-rest-1.0) | [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0) | Create a new workbookRangeBorder object by posting to the borders collection. |
| [Autofit columns](https://learn.microsoft.com/en-us/graph/api/rangeformat-autofitcolumns?view=graph-rest-1.0) | None | Changes the width of the columns of the current range to achieve the best fit for the current data in the columns. |
| [Autofit rows](https://learn.microsoft.com/en-us/graph/api/rangeformat-autofitrows?view=graph-rest-1.0) | None | Changes the height of the rows of the current range to achieve the best fit for the current data in the columns. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| columnWidth | double | The width of all columns within the range. If the column widths aren't uniform, null will be returned. |
| horizontalAlignment | string | The horizontal alignment for the specified object. The possible values are: `General`, `Left`, `Center`, `Right`, `Fill`, `Justify`, `CenterAcrossSelection`, `Distributed`. |
| rowHeight | double | The height of all rows in the range. If the row heights aren't uniform null will be returned. |
| verticalAlignment | string | The vertical alignment for the specified object. The possible values are: `Top`, `Center`, `Bottom`, `Justify`, `Distributed`. |
| wrapText | Boolean | Indicates whether Excel wraps the text in the object. A null value indicates that the entire range doesn't have a uniform wrap setting. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| borders | [workbookRangeBorder](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeborder?view=graph-rest-1.0) collection | Collection of border objects that apply to the overall range selected Read-only. |
| fill | [workbookRangeFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefill?view=graph-rest-1.0) | Returns the fill object defined on the overall range. Read-only. |
| font | [workbookRangeFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangefont?view=graph-rest-1.0) | Returns the font object defined on the overall range selected Read-only. |
| protection | [workbookFormatProtection](https://learn.microsoft.com/en-us/graph/api/resources/workbookformatprotection?view=graph-rest-1.0) | Returns the format protection object for a range. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "columnWidth": 1024,
  "horizontalAlignment": "string",
  "rowHeight": 1024,
  "verticalAlignment": "string",
  "wrapText": true
}
```
