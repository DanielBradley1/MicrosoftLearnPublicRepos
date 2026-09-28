<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookChartSeries resource type

Namespace: microsoft.graph

Represents a series in a chart.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/chartseries-list?view=graph-rest-1.0) | [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0) collection | Get the list of chart series. |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartseries-get?view=graph-rest-1.0) | [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0) | Read the properties and relationships of a chart series. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chartseries-update?view=graph-rest-1.0) | [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0) | Update a chart series. |
| [Create chart points](https://learn.microsoft.com/en-us/graph/api/chartseries-post-points?view=graph-rest-1.0) | [workbookChartPoint](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint?view=graph-rest-1.0) | Create a new chart point by posting to the points collection. |
| [List chart points](https://learn.microsoft.com/en-us/graph/api/chartseries-list-points?view=graph-rest-1.0) | [workbookChartPoint](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint?view=graph-rest-1.0) collection | Get a list of chart points. |
| [Get series at](https://learn.microsoft.com/en-us/graph/api/chartseriescollection-itemat?view=graph-rest-1.0) | [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0) | Get a chart series based on its position in the collection. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | string | The name of a series in a chart. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartSeriesFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseriesformat?view=graph-rest-1.0) | The formatting of a chart series, which includes fill and line formatting. Read-only. |
| points | [workbookChartPoint](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint?view=graph-rest-1.0) collection | A collection of all points in the series. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "string"
}
```
