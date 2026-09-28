<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlegendformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-11 -->

# workbookChartLegendFormat resource type

Namespace: microsoft.graph

Encapsulates the format properties of a chart legend.

## Methods

None

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| fill | [workbookChartFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfill?view=graph-rest-1.0) | Represents the fill format of an object, which includes background formating information. Read-only. |
| font | [workbookChartFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfont?view=graph-rest-1.0) | Represents the font attributes such as font name, font size, color, etc. of a chart legend. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "fill": {"@odata.type": "microsoft.graph.workbookChartFill"},
  "font": {"@odata.type": "microsoft.graph.workbookChartFont"}
}
```
