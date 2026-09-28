<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchquerystring?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# searchQueryString resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

Resources used in a Microsoft Search API request and response have had properties renamed or removed, or are being deprecated. Find [more details](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-beta&preserve-view=true#schema-change-deprecation-warning) about the deprecation. Update search API queries in any earlier apps accordingly.

The search terms for the query.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| query | String | Contains the actual search terms of the request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "query": "String"
}
```
