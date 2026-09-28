<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sortproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# sortProperty resource type

Namespace: microsoft.graph

Indicates the order to sort search results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDescending | Boolean | `True` if the sort order is descending. Default is `false`, with the sort order as ascending. Optional. |
| name | String | The name of the property to sort on. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "String",
  "isDescending": "true"
}
```
