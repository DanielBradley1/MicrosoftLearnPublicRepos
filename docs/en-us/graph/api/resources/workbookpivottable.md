<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookpivottable?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookPivotTable resource type

Namespace: microsoft.graph

Represents an Excel PivotTable.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/workbookpivottable-get?view=graph-rest-1.0) | [workbookPivotTable](https://learn.microsoft.com/en-us/graph/api/resources/workbookpivottable?view=graph-rest-1.0) | Read the properties and relationships of a workbookPivotTable object. |
| [Refresh a pivot table](https://learn.microsoft.com/en-us/graph/api/workbookpivottable-refresh?view=graph-rest-1.0) | None | Refresh the pivot table. |
| [Refresh all pivot tables](https://learn.microsoft.com/en-us/graph/api/workbookpivottable-refreshall?view=graph-rest-1.0) | None | Refresh all pivot tables within a specified worksheet. This action is available only on the pivot table collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ID | String | The identifier for the pivot table. Read-only. |
| name | String | The name of the pivot table. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| worksheet | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | The worksheet that contains the current pivot table. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "name": "String"
}
```
