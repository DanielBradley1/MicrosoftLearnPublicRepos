<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# workbookRangeView resource type

Namespace: microsoft.graph Represents a set of visible cells of the parent range.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List rows](https://learn.microsoft.com/en-us/graph/api/workbookrangeview-list-rows?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) collection | Get a workbookRangeView object collection. |
| [Get item at](https://learn.microsoft.com/en-us/graph/api/workbookrangeview-itemat?view=graph-rest-1.0) | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) | Get a range view item based in index. |
| [Get range](https://learn.microsoft.com/en-us/graph/api/workbookrangeview-range?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Get the range object associated with the range view |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cellAddresses | Json | The cell addresses. |
| columnCount | Int32 | The number of visible columns. Read-only. |
| formulas | Json | The formula in A1-style notation. |
| formulasLocal | Json | The formula in A1-style notation, in the user's language and number-formatting locale. For example, the English "=SUM\(A1, 1.5\)" formula would become "=SUMME\(A1; 1,5\)" in German. |
| formulasR1C1 | Json | Represents the formula in R1C1-style notation. |
| index | Int32 | The index of the range. |
| numberFormat | Json | Excel's number format code for the given cell. Read-only. |
| rowCount | Int32 | The number of visible rows. Read-only. |
| text | Json | The text values of the specified range. The Text value won't depend on the cell width. The # sign substitution that happens in Excel UI won't affect the text value returned by the API. Read-only. |
| valueTypes | Json | The type of data of each cell. Read-only. The possible values are: Unknown, Empty, String, Integer, Double, Boolean, Error. |
| values | Json | The raw values of the specified range view. The data returned could be of type string, number, or a Boolean. Cell that contains an error returns the error string. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| rows | [workbookRangeView](https://learn.microsoft.com/en-us/graph/api/resources/workbookrangeview?view=graph-rest-1.0) collection | The collection of range views associated with the range. Read-only. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "cellAddresses": "Json",
  "columnCount": 1024,
  "formulas": "Json",
  "formulasLocal": "Json",
  "formulasR1C1": "Json",
  "index": 1024,
  "numberFormat": "Json",
  "rowCount": 1024,
  "text": "Json",
  "valueTypes": "Json",
  "values": "Json"
}
```
