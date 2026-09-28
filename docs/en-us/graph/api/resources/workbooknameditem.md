<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# workbookNamedItem resource type

Namespace: microsoft.graph

Represents a defined name for a range of cells or value. Names can be primitive named objects \(as seen in the type below\), range object, reference to a range. This object can be used to obtain range object associated with names.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/nameditem-list?view=graph-rest-1.0) | [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0) collection | Get the list of workbookNamedItem objects. |
| [Add](https://learn.microsoft.com/en-us/graph/api/nameditem-add?view=graph-rest-1.0) | [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0) | Add a new workbookNamedItem object to the collection of the given scope. |
| [Get](https://learn.microsoft.com/en-us/graph/api/nameditem-get?view=graph-rest-1.0) | [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0) | Read the properties and relationships of a workbookNamedItem object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/nameditem-update?view=graph-rest-1.0) | [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0) | Update a workbookNamedItem object. |
| [Add named item to collection](https://learn.microsoft.com/en-us/graph/api/nameditem-addformulalocal?view=graph-rest-1.0) | [workbookNamedItem](https://learn.microsoft.com/en-us/graph/api/resources/workbooknameditem?view=graph-rest-1.0) | Add a new workbookNamedItem object to the collection of the given scope. Uses the user's locale for the formula. |
| [List range](https://learn.microsoft.com/en-us/graph/api/nameditem-range?view=graph-rest-1.0) | [workbookRange](https://learn.microsoft.com/en-us/graph/api/resources/workbookrange?view=graph-rest-1.0) | Return the range object that is associated with the workbookNamedItem object. Throw an exception if the workbookNamedItem object's **type** is not a range. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| comment | String | The comment associated with this name. |
| name | String | The name of the object. Read-only. |
| scope | String | Indicates whether the name is scoped to the workbook or to a specific worksheet. Read-only. |
| type | String | The type of reference is associated with the name. The possible values are: `String`, `Integer`, `Double`, `Boolean`, `Range`. Read-only. |
| value | String | The formula that the name is defined to refer to. For example, `=Sheet14!$B$2:$H$12` and `=4.75`. Read-only. |
| visible | Boolean | Indicates whether the object is visible. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| worksheet | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | Returns the worksheet to which the named item is scoped. Available only if the item is scoped to the worksheet. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "string",
  "comment": "string",
  "scope": "string",
  "type": "string",
  "value": {"@odata.type": "microsoft.graph.Json"},
  "visible": true

}
```
