<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchbucket?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# searchBucket resource type

Namespace: microsoft.graph

Represents a container for one or more search results that share the same value for the entity field that aggregates them.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aggregationFilterToken | String | A token containing the encoded filter to aggregate search matches by the specific **key** value. To use the filter, pass the token as part of the **aggregationFilter** property in a **searchRequest** object, in the format **"{field}:\\"{aggregationFilterToken}\\""**. See an [example](https://learn.microsoft.com/en-us/graph/search-concept-aggregation#example-2-apply-an-aggregation-filter-based-on-a-previous-request). |
| count | Int32 | The approximate number of search matches that share the same value specified in the **key** property. Note that this number is not the exact number of matches. |
| key | String | The discrete value of the field that an aggregation was computed on. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "key": "String",
  "count": "10",  
  "aggregationFilterToken": "String"
}
```
