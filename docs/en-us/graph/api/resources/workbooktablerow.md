<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookTableRow resource type

Namespace: microsoft.graph

Represents a row in a table.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/tablerow-list?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) collection | Get a workbookTableRow object collection. |
| [Add](https://learn.microsoft.com/en-us/graph/api/tablerowcollection-add?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) | Add a new row to the table. |
| [Get](https://learn.microsoft.com/en-us/graph/api/tablerow-get?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) | Read the properties and relationships of a tableRow object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tablerow-update?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) | Update a workbookTableRow object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/tablerow-delete?view=graph-rest-1.0) | None | Delete the row from the table. |
| [Add rows](https://learn.microsoft.com/en-us/graph/api/table-post-rows?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) | Add rows to the table. |
| [Get item at](https://learn.microsoft.com/en-us/graph/api/tablerowcollection-itemat?view=graph-rest-1.0) | [workbookTableRow](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablerow?view=graph-rest-1.0) | Get a row based on its position in the collection. |
| [Get row range](https://learn.microsoft.com/en-us/graph/api/tablerow-range?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Return the range object associated with the entire row. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| index | Int32 | The index of the row within the rows collection of the table. Zero-based. Read-only. |
| values | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-1.0) | The raw values of the specified range. The data returned could be of type string, number, or a Boolean. Any cell that contain an error will return the error string. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workbookTableRow",
  "index": "Integer",
  "values": {
    "@odata.type": "microsoft.graph.Json"
  }
}
```
