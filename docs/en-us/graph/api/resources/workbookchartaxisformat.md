<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookchartaxisformat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-11 -->

# workbookChartAxisFormat resource type

Namespace: microsoft.graph

Encapsulates the format properties for the chart axis.

## Methods

None

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| font | [workbookChartFont](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartfont?view=graph-rest-1.0) | Represents the font attributes \(font name, font size, color, etc.\) for a chart axis element. Read-only. |
| line | [workbookChartLineFormat](https://learn.microsoft.com/en-us/graph/api/resources/workbookchartlineformat?view=graph-rest-1.0) | Represents chart line formatting. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "font": {"@odata.type": "microsoft.graph.workbookChartFont"},
  "line": {"@odata.type": "microsoft.graph.workbookChartLineFormat"}
}
```
