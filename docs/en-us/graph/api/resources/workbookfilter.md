<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookfilter?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-12 -->

# workbookFilter resource type

Namespace: microsoft.graph

Manages the filtering of a table's column.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Apply](https://learn.microsoft.com/en-us/graph/api/filter-apply?view=graph-rest-1.0) | None | Apply the given filter criteria on the given column. |
| [Clear](https://learn.microsoft.com/en-us/graph/api/filter-clear?view=graph-rest-1.0) | None | Clear the filter on the given column. |

## Properties

| Name | Type | Description |
| :--- | :--- | :--- |
| criteria | [workbookFilterCriteria](https://learn.microsoft.com/en-us/graph/api/resources/filtercriteria?view=graph-rest-1.0) | The currently applied filter on the given column. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "criteria": {"@odata.type": "microsoft.graph.workbookFilterCriteria" }
}
```
