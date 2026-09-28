<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseriesformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-11 -->

# workbookChartSeriesFormat resource type

Namespace: microsoft.graph

encapsulates the format properties for the chart series

## Methods

None

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| fill | [workbookChartFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfill?view=graph-rest-1.0) | Represents the fill format of a chart series, which includes background formatting information. Read-only. |
| line | [workbookChartLineFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlineformat?view=graph-rest-1.0) | Represents line formatting. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "fill": {"@odata.type": "microsoft.graph.workbookChartFill"},
  "line": {"@odata.type": "microsoft.graph.workbookChartLineFormat"}
}
```
