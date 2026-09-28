<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxistitle?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookChartAxisTitle resource type

Namespace: microsoft.graph

Represents the title of a chart axis.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartaxistitle-get?view=graph-rest-1.0) | [workbookChartAxisTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxistitle?view=graph-rest-1.0) | Readthe properties and relationships of a chart axis title. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chartaxistitle-update?view=graph-rest-1.0) | [workbookChartAxisTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxistitle?view=graph-rest-1.0) | Update a chart axis title. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| text | string | Represents the axis title. |
| visible | Boolean | A Boolean that specifies the visibility of an axis title. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartAxisTitleFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxistitleformat?view=graph-rest-1.0) | Represents the formatting of chart axis title. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "format": {"@odata.type":"microsoft.graph.workbookChartAxisTitleFormat"},
  "text": "string",
  "visible": true
}
```
