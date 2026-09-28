<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxis?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookChartAxis resource type

Namespace: microsoft.graph

Represents a single axis in a chart.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartaxis-get?view=graph-rest-1.0) | [workbookChartAxis](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxis?view=graph-rest-1.0) | Read the properties and relationships of a chart axis. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chartaxis-update?view=graph-rest-1.0) | [workbookChartAxis](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxis?view=graph-rest-1.0) | Update a chart axis. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | Unique identifier. Read-only. |
| majorUnit | Json | Represents the interval between two major tick marks. Can be set to a numeric value or an empty string. The returned value is always a number. |
| maximum | Json | Represents the maximum value on the value axis. Can be set to a numeric value or an empty string \(for automatic axis values\). The returned value is always a number. |
| minimum | Json | Represents the minimum value on the value axis. Can be set to a numeric value or an empty string \(for automatic axis values\). The returned value is always a number. |
| minorUnit | Json | Represents the interval between two minor tick marks. "Can be set to a numeric value or an empty string \(for automatic axis values\). The returned value is always a number. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartAxisFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxisformat?view=graph-rest-1.0) | Represents the formatting of a chart object, which includes line and font formatting. Read-only. |
| majorGridlines | [workbookChartGridlines](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlines?view=graph-rest-1.0) | Returns a gridlines object that represents the major gridlines for the specified axis. Read-only. |
| minorGridlines | [workbookChartGridlines](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlines?view=graph-rest-1.0) | Returns a Gridlines object that represents the minor gridlines for the specified axis. Read-only. |
| title | [workbookChartAxisTitle](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxistitle?view=graph-rest-1.0) | Represents the axis title. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "format": {"@odata.type": "microsoft.graph.workbookChartAxisFormat"},
  "id": "string",
  "majorGridlines": {"@odata.type": "microsoft.graph.workbookChartGridlines"},
  "majorUnit": "string",
  "maximum": "string",
  "minimum": "string",
  "minorGridlines": {"@odata.type": "microsoft.graph.workbookChartGridlines"},
  "minorUnit": "string",
  "title": {"@odata.type": "microsoft.graph.workbookChartAxisTitle"}
}
```
