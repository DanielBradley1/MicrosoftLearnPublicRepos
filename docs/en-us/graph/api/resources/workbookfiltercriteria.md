<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookfiltercriteria?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# workbookFilterCriteria resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the filtering criteria applied to a column.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| color | String | The color applied to the cell. |
| criterion1 | String | A custom criterion. |
| criterion2 | String | A custom criterion. |
| dynamicCriteria | String | A dynamic formula specified in a custom filter. |
| filterOn | String | Indicates whether a filter is applied to a column. |
| icon | [workbookIcon](https://learn.microsoft.com/en-us/graph/api/resources/workbookicon?view=graph-rest-beta) | An icon applied via conditional formatting. |
| operator | String | An operator in a cell; for example, `=`, `>`, `<`, `<=`, or `<>`. |
| values | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json?view=graph-rest-beta) | The values that appear in the cell. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "color": "string",
  "criterion1": "string",
  "criterion2": "string",
  "dynamicCriteria": "string",
  "filterOn": "string",
  "values": {"@odata.type":"microsoft.graph.Json"},
  "icon":{"@odata.type": "microsoft.graph.workbookIcon"},
  "operator":"string"
}
```
