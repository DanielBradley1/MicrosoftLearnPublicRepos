<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookChartPoint resource type

Namespace: microsoft.graph

Represents a point of a series in a chart.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/chartpoint-list?view=graph-rest-1.0) | [workbookChartPoint](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint?view=graph-rest-1.0) collection | Get a list of chartPoint objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartpoint-get?view=graph-rest-1.0) | [workbookChartPoint](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint?view=graph-rest-1.0) | Read the properties and relationships of chartPoint object. |
| [Get chart point at](https://learn.microsoft.com/en-us/graph/api/chartpointscollection-itemat?view=graph-rest-1.0) | [workbookChartPoint](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpoint?view=graph-rest-1.0) | Get a point based on its position within the series. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ID | string | unique identifier |
| value | Json | The value of a chart point. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartPointFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartpointformat?view=graph-rest-1.0) | The format properties of the chart point. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "value": "string"
}
```
