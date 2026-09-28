<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchaggregation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# searchAggregation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides the details of the search aggregation in the search response.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The friendly name of the aggregation. This value was provided in the input. |
| field | String | Defines on which field the aggregation was computed on. |
| buckets | [searchBucket](https://learn.microsoft.com/en-us/graph/api/resources/searchbucket?view=graph-rest-beta) collection | Defines the actual buckets of the computed aggregation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "field": "String",  
  "buckets": [{"@odata.type": "microsoft.graph.searchBucket"}]
}
```
