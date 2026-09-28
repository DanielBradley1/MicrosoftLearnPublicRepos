<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlines?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# workbookChartGridlines resource type

Namespace: microsoft.graph

Represents major or minor gridlines on a chart axis.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/chartgridlines-get?view=graph-rest-1.0) | [workbookChartGridlines](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlines?view=graph-rest-1.0) | Read the properties and relationships of a chartGridlines object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chartgridlines-update?view=graph-rest-1.0) | [workbookChartGridlines](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlines?view=graph-rest-1.0) | Update a chartGridlines object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| visible | Boolean | Indicates whether the axis gridlines are visible. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| format | [workbookChartGridlinesFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartgridlinesformat?view=graph-rest-1.0) | Represents the formatting of chart gridlines. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "visible": true
}
```
