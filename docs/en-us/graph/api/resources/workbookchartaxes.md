<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-11 -->

# workbookChartAxes resource type

Namespace: microsoft.graph

Represents the chart axes.

## Methods

None

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| categoryAxis | [workbookChartAxis](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxis?view=graph-rest-1.0) | Represents the category axis in a chart. Read-only. |
| seriesAxis | [workbookChartAxis](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxis?view=graph-rest-1.0) | Represents the series axis of a 3-dimensional chart. Read-only. |
| valueAxis | [workbookChartAxis](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxis?view=graph-rest-1.0) | Represents the value axis in an axis. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "categoryAxis": {"@odata.type": "microsoft.graph.workbookChartAxis"},
  "seriesAxis": {"@odata.type": "microsoft.graph.workbookChartAxis"},
  "valueAxis": {"@odata.type": "microsoft.graph.workbookChartAxis"}
}
```
