<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookTable resource type

Namespace: microsoft.graph

Represents an Excel table.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/table-list?view=graph-rest-1.0) | [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) collection | Get table object collection. |
| [Add](https://learn.microsoft.com/en-us/graph/api/tablecollection-add?view=graph-rest-1.0) | [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) | Create a new table. The range source address determines the worksheet under which the table will be added. If the table can't be added \(for example, because the address is invalid, or the table would overlap with another table\), an error is thrown. |
| [Get](https://learn.microsoft.com/en-us/graph/api/table-get?view=graph-rest-1.0) | [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) | Read the properties and relationships of the workbookTable object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/table-update?view=graph-rest-1.0) | [workbookTable](https://learn.microsoft.com/en-us/graph/api/resources/workbooktable?view=graph-rest-1.0) | Update the workbookTable object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/table-delete?view=graph-rest-1.0) | None | Deletes the table. |
| [List columns](https://learn.microsoft.com/en-us/graph/api/table-list-columns?view=graph-rest-1.0) | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) collection | Get a list of workbookTableColumn objects. |
| [Create column](https://learn.microsoft.com/en-us/graph/api/table-post-columns?view=graph-rest-1.0) | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) | Create a new workbookTableColumn by posting to the columns collection. |
| [List rows](https://learn.microsoft.com/en-us/graph/api/table-list-rows?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) collection | Get a workbookTableRow object collection. |
| [Create row](https://learn.microsoft.com/en-us/graph/api/table-post-rows?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) | Create a new workbookTableRow by posting to the rows collection. |
| [Get data body range](https://learn.microsoft.com/en-us/graph/api/table-databodyrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the workbookRange object associated with the data body of the table. |
| [Get header row range](https://learn.microsoft.com/en-us/graph/api/table-headerrowrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the workbookRange object associated with header row of the table. |
| [Get table range](https://learn.microsoft.com/en-us/graph/api/table-range?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the workbookRange object associated with the entire table. |
| [Get total row range](https://learn.microsoft.com/en-us/graph/api/table-totalrowrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the workbookRange object associated with totals row of the table. |
| [Clear filters](https://learn.microsoft.com/en-us/graph/api/table-clearfilters?view=graph-rest-1.0) | None | Clears all the filters currently applied on the table. |
| [Convert to range](https://learn.microsoft.com/en-us/graph/api/table-converttorange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Converts the table into a normal range of cells. All data is preserved. |
| [Reapply filters](https://learn.microsoft.com/en-us/graph/api/table-reapplyfilters?view=graph-rest-1.0) | None | Reapplies all the filters currently on the table. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The unique identifier for the table in the workbook. The value of the identifier remains the same even when the table is renamed. This property should be interpreted as an opaque string value and shouldn't be parsed to any other type. Read-only. |
| name | string | The name of the table. |
| showHeaders | Boolean | Indicates whether the header row is visible or not. This value can be set to show or remove the header row. |
| showTotals | Boolean | Indicates whether the total row is visible or not. This value can be set to show or remove the total row. |
| style | string | A constant value that represents the Table style. The possible values are: `TableStyleLight1` through `TableStyleLight21`, `TableStyleMedium1` through `TableStyleMedium28`, `TableStyleStyleDark1` through `TableStyleStyleDark11`. A custom user-defined style present in the workbook can also be specified. |
| highlightFirstColumn | Boolean | Indicates whether the first column contains special formatting. |
| highlightLastColumn | Boolean | Indicates whether the last column contains special formatting. |
| showBandedColumns | Boolean | Indicates whether the columns show banded formatting in which odd columns are highlighted differently from even ones to make reading the table easier. |
| showBandedRows | Boolean | Indicates whether the rows show banded formatting in which odd rows are highlighted differently from even ones to make reading the table easier. |
| showFilterButton | Boolean | Indicates whether the filter buttons are visible at the top of each column header. Setting this is only allowed if the table contains a header row. |
| legacyId | String | A legacy identifier used in older Excel clients. The value of the identifier remains the same even when the table is renamed. This property should be interpreted as an opaque string value and shouldn't be parsed to any other type. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| columns | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) collection | The list of all the columns in the table. Read-only. |
| rows | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) collection | The list of all the rows in the table. Read-only. |
| sort | [workbookTableSort](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablesort?view=graph-rest-1.0) | The sorting for the table. Read-only. |
| worksheet | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | The worksheet containing the current table. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "highlightFirstColumn": true,
  "highlightLastColumn": true,
  "id": "String (identifier)",
  "name": "String",
  "showBandedColumns": true,
  "showBandedRows": true,
  "showFilterButton": true,
  "showHeaders": true,
  "showTotals": true,
  "style": "String",
  "legacyId": "String"
}
```
