<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printmargin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-04 -->

# printMargin resource type

Namespace: microsoft.graph

Specifies the margin widths to use when printing.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bottom | Int32 | The margin in microns from the bottom edge. |
| left | Int32 | The margin in microns from the left edge. |
| right | Int32 | The margin in microns from the right edge. |
| top | Int32 | The margin in microns from the top edge. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printMargin",
  "top": "Integer",
  "bottom": "Integer",
  "right": "Integer",
  "left": "Integer"
}
```
