<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bucketaggregationdefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# bucketAggregationDefinition resource type

Namespace: microsoft.graph

Provides the details on how to generate the aggregations in the results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDescending | Boolean | `True` to specify the sort order as descending. The default is `false`, with the sort order as ascending. Optional. |
| minimumCount | Int32 | The minimum number of items that should be present in the aggregation to be returned in a bucket. Optional. |
| prefixFilter | String | A filter to define a matching criteria. The key should start with the specified prefix to be returned in the response. Optional. |
| ranges | [bucketAggregationRange](https://learn.microsoft.com/en-us/graph/api/resources/bucketaggregationrange?view=graph-rest-1.0) collection | Specifies the manual ranges to compute the aggregations. This is only valid for nonstring refiners of date or numeric type. Optional. |
| sortBy | bucketAggregationSortProperty | The possible values are `count` to sort by the number of matches in the aggregation, `keyAsString`to sort alphabetically based on the key in the aggregation, `keyAsNumber` for numerical sorting based on the key in the aggregation. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isDescending": true,
  "minimumCount": 1024,
  "prefixFilter": "String",
  "ranges": [{"@odata.type": "microsoft.graph.bucketAggregationRange"}],
  "sortBy": "String"
}
```
