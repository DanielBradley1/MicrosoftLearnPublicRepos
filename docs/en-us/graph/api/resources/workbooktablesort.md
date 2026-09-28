<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbooktablesort?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookTableSort resource type

Namespace: microsoft.graph

Manages sorting operations on Table objects.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/tablesort-get?view=graph-rest-1.0) | [workbookTableSort](https://learn.microsoft.com/en-us/graph/api/resources/workbooktablesort?view=graph-rest-1.0) | Read the properties and relationships of the workbookTableSort object. |
| [Apply sort](https://learn.microsoft.com/en-us/graph/api/tablesort-apply?view=graph-rest-1.0) | None | Perform a sort operation. |
| [Clear sort](https://learn.microsoft.com/en-us/graph/api/tablesort-clear?view=graph-rest-1.0) | None | Clears the sorting that is currently on the table. While this doesn't modify the table's ordering, it clears the state of the header buttons. |
| [Reapply sort](https://learn.microsoft.com/en-us/graph/api/tablesort-reapply?view=graph-rest-1.0) | None | Reapplies the current sorting parameters to the table. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fields | [workbookSortField](https://learn.microsoft.com/en-us/graph/api/resources/sortfield?view=graph-rest-1.0) collection | The list of the current conditions last used to sort the table. Read-only. |
| matchCase | Boolean | Indicates whether the casing impacted the last sort of the table. Read-only. |
| method | string | The Chinese character ordering method last used to sort the table. The possible values are: `PinYin`, `StrokeCount`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "matchCase": true,
  "method": "string",
  "fields": [{ "@odata.type": "microsoft.graph.workbookSortField" }]
}
```
