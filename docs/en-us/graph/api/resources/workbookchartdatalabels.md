<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartdatalabels?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# workbookChartDataLabels resource type

Namespace: microsoft.graph

Represents a collection of all the data labels on a chart point.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartdatalabels-get?view=graph-rest-1.0) | [workbookChartDataLabels](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartdatalabels?view=graph-rest-1.0) | Read the properties and relationships of a chartDataLabels object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chartdatalabels-update?view=graph-rest-1.0) | [workbookChartDataLabels](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartdatalabels?view=graph-rest-1.0) | Update a ChartDataLabels object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| position | string | DataLabelPosition value that represents the position of the data label. The possible values are: `None`, `Center`, `InsideEnd`, `InsideBase`, `OutsideEnd`, `Left`, `Right`, `Top`, `Bottom`, `BestFit`, `Callout`. |
| separator | string | String that represents the separator used for the data labels on a chart. |
| showBubbleSize | Boolean | Boolean value that represents whether the data label bubble size is visible. |
| showCategoryName | Boolean | Boolean value that represents whether the data label category name is visible. |
| showLegendKey | Boolean | Boolean value that represents whether the data label legend key is visible. |
| showPercentage | Boolean | Boolean value that represents whether the data label percentage is visible. |
| showSeriesName | Boolean | Boolean value that represents whether the data label series name is visible. |
| showValue | Boolean | Boolean value that represents whether the data label value is visible. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartDataLabelFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartdatalabelformat?view=graph-rest-1.0) | Represents the format of chart data labels, which includes fill and font formatting. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "position": "string",
  "separator": "string",
  "showBubbleSize": true,
  "showCategoryName": true,
  "showLegendKey": true,
  "showPercentage": true,
  "showSeriesName": true,
  "showValue": true
}
```
