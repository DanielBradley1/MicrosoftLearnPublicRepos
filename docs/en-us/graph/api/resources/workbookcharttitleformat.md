<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookcharttitleformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-11 -->

# workbookChartTitleFormat resource type

Namespace: microsoft.graph

Encapsulates the format properties for the chart title.

## Methods

None

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| fill | [workbookChartFill](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfill?view=graph-rest-1.0) | Represents the fill format of an object, which includes background formatting information. Read-only. |
| font | [workbookChartFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfont?view=graph-rest-1.0) | Represents the font attributes \(font name, font size, color, etc.\) for the current object. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "fill": {"@odata.type": "microsoft.graph.workbookChartFill"},
  "font": {"@odata.type": "microsoft.graph.workbookChartFont"}
}
```
