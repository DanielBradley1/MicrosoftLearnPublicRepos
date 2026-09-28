<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookRange resource type

Namespace: microsoft.graph

Represents a set of one or more contiguous cells in a workbook, such as a cell, a row, a column, or a block of cells.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/range-get?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Read the properties and relationships of a range object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/range-update?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Update a range object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/range-delete?view=graph-rest-1.0) | None | Delete the cells associated with the range. |
| [Clear](https://learn.microsoft.com/en-us/graph/api/range-clear?view=graph-rest-1.0) | None | Clear range values, format, fill, or border. |
| [Get boundingrect](https://learn.microsoft.com/en-us/graph/api/range-boundingrect?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the smallest range object that encompasses the given ranges. For example, the GetBoundingRect of "B2:C5" and "D10:E15" is "B2:E16". |
| [Get cell](https://learn.microsoft.com/en-us/graph/api/range-cell?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the range object containing the single cell based on row and column numbers. The cell can be outside the bounds of its parent range, as long as it stays within the worksheet grid. The returned cell is located relative to the top left cell of the range. |
| [Get column](https://learn.microsoft.com/en-us/graph/api/range-column?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get a column contained in the range. |
| [Get columns after](https://learn.microsoft.com/en-us/graph/api/workbookrange-columnsafter?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) | Get some columns to the right of the given range. |
| [Get columns before](https://learn.microsoft.com/en-us/graph/api/workbookrange-columnsbefore?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) | Get some columns to the left of the given range. |
| [Get entire column](https://learn.microsoft.com/en-us/graph/api/range-entirecolumn?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get an object that represents the entire column of the range. |
| [Get entire row](https://learn.microsoft.com/en-us/graph/api/range-entirerow?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get an object that represents the entire row of the range. |
| [Get intersection](https://learn.microsoft.com/en-us/graph/api/range-intersection?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the range object that represents the rectangular intersection of the given ranges. |
| [Get last cell](https://learn.microsoft.com/en-us/graph/api/range-lastcell?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the last cell within the range. For example, the last cell of "B2:D5" is "D5". |
| [Get last column](https://learn.microsoft.com/en-us/graph/api/range-lastcolumn?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the last column within the range. For example, the last column of "B2:D5" is "D2:D5". |
| [Get last row](https://learn.microsoft.com/en-us/graph/api/range-lastrow?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Getsthe last row within the range. For example, the last row of "B2:D5" is "B5:D5". |
| [Get offset range](https://learn.microsoft.com/en-us/graph/api/range-offsetrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get an object that represents a range that's offset from the specified range. The dimension of the returned range matches this range. If the resulting range is forced outside the bounds of the worksheet grid, an exception is thrown. |
| [Get resized range](https://learn.microsoft.com/en-us/graph/api/workbookrange-resizedrange?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) | Get a range object similar to the current range object, but with its bottom-right corner expanded \(or contracted\) by some number of rows and columns. |
| [Get row](https://learn.microsoft.com/en-us/graph/api/range-row?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get a row contained in the range. |
| [Get rows above](https://learn.microsoft.com/en-us/graph/api/workbookrange-rowsabove?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) | Get some rows above a given range. |
| [Get rows below](https://learn.microsoft.com/en-us/graph/api/workbookrange-rowsbelow?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) | Get some rows below a given range. |
| [Get used range](https://learn.microsoft.com/en-us/graph/api/range-usedrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Return the used range of the given range object. |
| [Get visible view](https://learn.microsoft.com/en-us/graph/api/workbookrange-visibleview?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) | Get the range visible from a filtered range. |
| [Insert range](https://learn.microsoft.com/en-us/graph/api/range-insert?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Insert a cell or a range of cells into the worksheet in place of this range, and shifts the other cells to make space. Returns a new Range object at the now blank space. |
| [Merge](https://learn.microsoft.com/en-us/graph/api/range-merge?view=graph-rest-1.0) | None | Merge the range cells into one region in the worksheet. |
| [Unmerge](https://learn.microsoft.com/en-us/graph/api/range-unmerge?view=graph-rest-1.0) | None | Unmerge the range cells into separate cells. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | string | Represents the range reference in A1-style. Address value contains the Sheet reference \(for example, Sheet1!A1:B4\). Read-only. |
| addressLocal | string | Represents range reference for the specified range in the language of the user. Read-only. |
| cellCount | int | Number of cells in the range. Read-only. |
| columnCount | int | Represents the total number of columns in the range. Read-only. |
| columnHidden | Boolean | Indicates whether all columns of the current range are hidden. |
| columnIndex | int | Represents the column number of the first cell in the range. Zero-indexed. Read-only. |
| formulas | Json | Represents the formula in A1-style notation. |
| formulasLocal | Json | Represents the formula in A1-style notation, in the user's language and number-formatting locale. For example, the English "=SUM\(A1, 1.5\)" formula would become "=SUMME\(A1; 1,5\)" in German. |
| formulasR1C1 | Json | Represents the formula in R1C1-style notation. |
| hidden | Boolean | Represents if all cells of the current range are hidden. Read-only. |
| numberFormat | Json | Represents Excel's number format code for the given cell. |
| rowCount | int | Returns the total number of rows in the range. Read-only. |
| rowHidden | Boolean | Indicates whether all rows of the current range are hidden. |
| rowIndex | int | Returns the row number of the first cell in the range. Zero-indexed. Read-only. |
| text | Json | Text values of the specified range. The Text value doesn't depend on the cell width. The # sign substitution that happens in Excel UI doesn't affect the text value returned by the API. Read-only. |
| valueTypes | Json | Represents the type of data of each cell. The possible values are: `Unknown`, `Empty`, `String`, `Integer`, `Double`, `Boolean`, `Error`. Read-only. |
| values | Json | Represents the raw values of the specified range. The data returned can be of type string, number, or a Boolean. Cell that contains an error returns the error string. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookRangeFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeformat?view=graph-rest-1.0) | Returns a format object, encapsulating the range's font, fill, borders, alignment, and other properties. Read-only. |
| sort | [workbookRangeSort](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangesort?view=graph-rest-1.0) | The worksheet containing the current range. Read-only. |
| worksheet | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | The worksheet containing the current range. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "address": "string",
  "addressLocal": "string",
  "cellCount": 1024,
  "columnCount": 1024,
  "columnHidden": true,
  "columnIndex": 1024,
  "formulas": "json",
  "formulasLocal": "json",
  "formulasR1C1": "json",
  "hidden": true,
  "numberFormat": "json",
  "rowCount": 1024,
  "rowHidden": true,
  "rowIndex": 1024,
  "text": "json",
  "valueTypes": "string",
  "values": "json"
}
```
