<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookTableColumn resource type

Namespace: microsoft.graph

Represents a column in a table.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tablecolumn-list?view=graph-rest-1.0) | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) collection | Get tableColumn object collection. |
| [Add](https://learn.microsoft.com/en-us/graph/api/tablecolumncollection-add?view=graph-rest-1.0) | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) | Add a new column to the table. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tablecolumn-get?view=graph-rest-1.0) | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) | Read properties and relationships of tableColumn object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tablecolumn-update?view=graph-rest-1.0) | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) | Update TableColumn object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/tablecolumn-delete?view=graph-rest-1.0) | None | Deletes the column from the table. |
| [Get column range](https://learn.microsoft.com/en-us/graph/api/tablecolumn-range?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the range object associated with the entire column. |
| [Get data body range](https://learn.microsoft.com/en-us/graph/api/tablecolumn-databodyrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the range object associated with the data body of the column. |
| [Get header row range](https://learn.microsoft.com/en-us/graph/api/tablecolumn-headerrowrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the range object associated with the header row of the column. |
| [Get item at](https://learn.microsoft.com/en-us/graph/api/tablecolumncollection-itemat?view=graph-rest-1.0) | [workbookTableColumn](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablecolumn?view=graph-rest-1.0) | Gets a column based on its position in the collection. |
| [Get total row range](https://learn.microsoft.com/en-us/graph/api/tablecolumn-totalrowrange?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Gets the range object associated with the totals row of the column. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The unique identifier for the column within the table. This property should be interpreted as an opaque string value and shouldn't be parsed to any other type. Read-only. |
| index | int | The index of the column within the columns collection of the table. Zero-indexed. Read-only. |
| name | string | The name of the table column. |
| values | Json | TRepresents the raw values of the specified range. The data returned could be of type string, number, or a Boolean. Cell that contain an error will return the error string. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| filter | [workbookFilter](https://learn.microsoft.com/en-us/graph/api/resources/workbookfilter?view=graph-rest-1.0) | The filter applied to the column. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "1024",
  "index": 1024,
  "name": "string",
  "values": "json"
}
```
