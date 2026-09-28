<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitle?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# workbookChartTitle resource type

Namespace: microsoft.graph

Represents a chart title object of a chart.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/charttitle-get?view=graph-rest-1.0) | [workbookChartTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitle?view=graph-rest-1.0) | Read the properties and relationships of a chart title. |
| [Update](https://learn.microsoft.com/en-us/graph/api/charttitle-update?view=graph-rest-1.0) | [workbookChartTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitle?view=graph-rest-1.0) | Update a chart title. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| overlay | Boolean | Indicates whether the chart title will overlay the chart or not. |
| text | string | The title text of the chart. |
| visible | Boolean | Indicates whether the chart title is visible. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartTitleFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitleformat?view=graph-rest-1.0) | The formatting of a chart title, which includes fill and font formatting. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "overlay": true,
  "text": "string",
  "visible": true
}
```
