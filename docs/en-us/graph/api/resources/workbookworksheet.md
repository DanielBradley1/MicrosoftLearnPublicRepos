<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookWorksheet resource type

Namespace: microsoft.graph

Represnts an Excel worksheet, which contains a grid of cells. It can contain data, tables, charts, and so on.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/worksheet-list?view=graph-rest-1.0) | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) collection | Get the list of worksheets in the workbook. |
| [Add](https://learn.microsoft.com/en-us/graph/api/worksheetcollection-add?view=graph-rest-1.0) | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | Adds a new worksheet to the workbook. The worksheet will be added at the end of existing worksheets. |
| [Get](https://learn.microsoft.com/en-us/graph/api/worksheet-get?view=graph-rest-1.0) | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | Read the properties and relationships of the workbookWorksheet object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/worksheet-update?view=graph-rest-1.0) | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | Update a workbookWorksheet object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/worksheet-delete?view=graph-rest-1.0) | None | Delete the worksheet from the workbook. |
| [List charts](https://learn.microsoft.com/en-us/graph/api/worksheet-list-charts?view=graph-rest-1.0) | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) collection | Get a list of the charts in the worksheet. |
| [Add chart](https://learn.microsoft.com/en-us/graph/api/worksheet-post-charts?view=graph-rest-1.0) | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) | Create a new chart by posting to the charts collection. |
| [List names](https://learn.microsoft.com/en-us/graph/api/worksheet-list-names?view=graph-rest-1.0) | [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0) collection | Get the list of workbookNamedItem objects for the worksheet. |
| [List pivot tables](https://learn.microsoft.com/en-us/graph/api/workbookworksheet-list-pivottables?view=graph-rest-1.0) | [workbookPivotTable](https://learn.microsoft.com/en-us/graph/api/resources/workbookpivottable?view=graph-rest-1.0) collection | Get a list of the pivot tables in the worksheet. |
| [List tables](https://learn.microsoft.com/en-us/graph/api/worksheet-list-tables?view=graph-rest-1.0) | [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) collection | Get the list of tables in the worksheet. |
| [Add table](https://learn.microsoft.com/en-us/graph/api/worksheet-post-tables?view=graph-rest-1.0) | [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) | Create a new table by posting to the tables collection. |
| [Get cell](https://learn.microsoft.com/en-us/graph/api/worksheet-cell?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the range object that contains the single cell, specified by row and column numbers. The cell can be outside the bounds of its parent range, so long as it is within the worksheet grid. |
| [Get range](https://learn.microsoft.com/en-us/graph/api/worksheet-range?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the range object specified by the address or name. |
| [Get used range](https://learn.microsoft.com/en-us/graph/api/worksheet-usedrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the smallest range that encompasses any cells that have a value or formatting assigned to them. If the worksheet is blank, this function will return the top left cell. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The unique identifier for the worksheet in the workbook. The value of the identifier remains the same even when the worksheet is renamed or moved. Read-only. |
| name | string | The display name of the worksheet. |
| position | int | The zero-based position of the worksheet within the workbook. |
| visibility | string | The visibility of the worksheet. The possible values are: `Visible`, `Hidden`, `VeryHidden`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| charts | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) collection | The list of charts that are part of the worksheet. Read-only. |
| names | [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0) collection | The list of names that are associated with the worksheet. Read-only. |
| pivotTables | [workbookPivotTable](https://learn.microsoft.com/en-us/graph/api/resources/workbookpivottable?view=graph-rest-1.0) collection | The list of piot tables that are part of the worksheet. |
| protection | [workbookWorksheetProtection](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheetprotection?view=graph-rest-1.0) | The sheet protection object for a worksheet. Read-only. |
| tables | [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) collection | The list of tables that are part of the worksheet. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "name": "string",
  "position": 1024,
  "visibility": "string"
}
```
