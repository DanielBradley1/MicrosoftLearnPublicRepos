<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filtercriteria?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-16 -->

# workbookFilterCriteria resource type

Namespace: microsoft.graph

Represents the filtering criteria applied to a column.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | String | The color applied to the cell. |
| criterion1 | String | A custom criterion. |
| criterion2 | String | A custom criterion. |
| dynamicCriteria | String | A dynamic formula specified in a custom filter. |
| filterOn | String | Indicates whether a filter is applied to a column. |
| icon | [workbookIcon](https://learn.microsoft.com/en-us/graph/api/resources/workbookicon?view=graph-rest-1.0) | An icon applied to a cell via conditional formatting. |
| operator | String | An operator in a cell; for example, `=`, `>`, `<`, `<=`, or `<>`. |
| values | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-1.0) | The values that appear in the cell. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "color": "String",
  "criterion1": "String",
  "criterion2": "String",
  "dynamicCriteria": "String",
  "filterOn": "String",
  "icon": {"@odata.type": "microsoft.graph.workbookIcon"},
  "values": {"@odata.type": "microsoft.graph.Json"}
}
```
