<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcereference?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# resourceReference resource type

Namespace: microsoft.graph

Complex type containing properties of [officeGraphInsights](https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | The item's unique identifier. |
| type | String | A string value that can be used to classify the item, such as "microsoft.graph.driveItem" |
| webUrl | String | A URL leading to the referenced item. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "webUrl": "string",
  "id": "string",
  "type": "string"
}
```
