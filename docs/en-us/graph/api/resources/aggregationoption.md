<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/aggregationoption?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# aggregationOption resource type

Namespace: microsoft.graph

Specifies which aggregations should be returned alongside the search results. The maximum returned value is 100 buckets.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bucketDefinition | [bucketAggregationDefinition](https://learn.microsoft.com/en-us/graph/api/resources/bucketaggregationdefinition?view=graph-rest-1.0) | Specifies the criteria to compute an aggregation. Optional. |
| field | String | Computes aggregation on the field while the field exists in the current entity type. Required. |
| size | Int32 | The number of [searchBucket](https://learn.microsoft.com/en-us/graph/api/resources/searchbucket?view=graph-rest-1.0) resources to be returned. This isn't required when the range is provided manually in the search request. The minimum accepted size is 1, and the maximum is 65535. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "bucketDefinition": {"@odata.type": "microsoft.graph.bucketAggregationDefinition"},
  "field": "String",
  "size": 1024
}
```
