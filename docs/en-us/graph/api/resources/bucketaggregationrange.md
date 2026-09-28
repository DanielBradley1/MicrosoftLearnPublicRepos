<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bucketaggregationrange?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# bucketAggregationRange resource type

Namespace: microsoft.graph

Specifies the lower and upper limit to a range for aggregating search results. Applies only to refiners of the date or numeric type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| from | String | Defines the lower bound from which to compute the aggregation. This can be a numeric value or a string representation of a date using the `YYYY-MM-DDTHH:mm:ss.sssZ` format. Required. |
| to | String | Defines the upper bound up to which to compute the aggregation. This can be a numeric value or a string representation of a date using the `YYYY-MM-DDTHH:mm:ss.sssZ` format. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "from": "String",
  "to": "String"
}
```
