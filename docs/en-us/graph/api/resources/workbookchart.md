<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookChart resource type

Namespace: microsoft.graph

Represents a chart object in a workbook.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/chart-list?view=graph-rest-1.0) | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) collection | Get the list of chart objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/chart-get?view=graph-rest-1.0) | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) | Read the properties and relationships of chart object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chart-update?view=graph-rest-1.0) | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) | Update a chart object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/chart-delete?view=graph-rest-1.0) | None | Delete the chart object. |
| [List chart series](https://learn.microsoft.com/en-us/graph/api/chart-list-series?view=graph-rest-1.0) | [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0) collection | Get the list of chart series. |
| [Create chart series](https://learn.microsoft.com/en-us/graph/api/chart-post-series?view=graph-rest-1.0) | [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0) | Create a new chart series in the chart series. |
| [Add chart](https://learn.microsoft.com/en-us/graph/api/chartcollection-add?view=graph-rest-1.0) | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) | Creates a new chart. |
| [Get chart at](https://learn.microsoft.com/en-us/graph/api/chartcollection-itemat?view=graph-rest-1.0) | [workbookChart](https://learn.microsoft.com/en-us/graph/api/resources/workbookchart?view=graph-rest-1.0) | Gets a chart based on its position in the collection. |
| [Get chart image](https://learn.microsoft.com/en-us/graph/api/chart-image?view=graph-rest-1.0) | Image base64 encoded string | Get a base64-encoded image of the chart that is scaled to fit the specified dimensions. |
| [Reset data](https://learn.microsoft.com/en-us/graph/api/chart-setdata?view=graph-rest-1.0) | None | Resets the source data for the chart. |
| [Set position data](https://learn.microsoft.com/en-us/graph/api/chart-setposition?view=graph-rest-1.0) | None | Positions the chart relative to cells on the worksheet. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| height | double | Represents the height, in points, of the chart object. |
| id | string | Gets a chart based on its position in the collection. Read-only. |
| left | double | The distance, in points, from the left side of the chart to the worksheet origin. |
| name | string | Represents the name of a chart object. |
| top | double | Represents the distance, in points, from the top edge of the object to the top of row 1 \(on a worksheet\) or the top of the chart area \(on a chart\). |
| width | double | Represents the width, in points, of the chart object. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| axes | [workbookChartAxes](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxes?view=graph-rest-1.0) | Represents chart axes. Read-only. |
| dataLabels | [workbookChartDataLabels](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartdatalabels?view=graph-rest-1.0) | Represents the data labels on the chart. Read-only. |
| format | [workbookChartAreaFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartareaformat?view=graph-rest-1.0) | Encapsulates the format properties for the chart area. Read-only. |
| legend | [workbookChartLegend](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegend?view=graph-rest-1.0) | Represents the legend for the chart. Read-only. |
| series | [workbookChartSeries](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartseries?view=graph-rest-1.0) collection | Represents either a single series or collection of series in the chart. Read-only. |
| title | [workbookChartTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitle?view=graph-rest-1.0) | Represents the title of the specified chart, including the text, visibility, position and formatting of the title. Read-only. |
| worksheet | [workbookWorksheet](https://learn.microsoft.com/en-us/graph/api/resources/workbookworksheet?view=graph-rest-1.0) | The worksheet containing the current chart. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "height": 1024,
  "id": "string",
  "left": 1024,
  "name": "string",
  "top": 1024,
  "width": 1024
}
```
