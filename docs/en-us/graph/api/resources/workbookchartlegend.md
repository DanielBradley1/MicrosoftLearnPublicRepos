<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegend?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# workbookChartLegend resource type

Namespace: microsoft.graph

Represents the legend in a chart.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartlegend-get?view=graph-rest-1.0) | [workbookChartLegend](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegend?view=graph-rest-1.0) | Read the properties and relationships of chartLegend object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chartlegend-update?view=graph-rest-1.0) | [workbookChartLegend](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegend?view=graph-rest-1.0) | Update a chartLegend object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| overlay | Boolean | Indicates whether the chart legend should overlap with the main body of the chart. |
| position | string | Represents the position of the legend on the chart. The possible values are: `Top`, `Bottom`, `Left`, `Right`, `Corner`, `Custom`. |
| visible | Boolean | Indicates whether the chart legend is visible. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartLegendFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegendformat?view=graph-rest-1.0) | Represents the formatting of a chart legend, which includes fill and font formatting. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "format": {"@odata.type":"microsoft.graph.workbookChartLegendFormat"},
  "overlay": true,
  "position": "string",
  "visible": true
}
```
