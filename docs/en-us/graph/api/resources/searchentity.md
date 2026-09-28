<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# searchEntity resource type

Namespace: microsoft.graph

A top level object that represents the Microsoft Search API endpoint.

The **searchEntity** resource serves as an anchor to the [query](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) action and search answer relationships with the following resources: [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0), [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0), and [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0).

Important

Microsoft 365 Copilot connectors are currently in public preview status. To gain access to connectors functionality, you must turn on the Targeted release option in your tenant. For more information, see the [connectors preview program](https://learn.microsoft.com/en-us/microsoftsearch/connectors-preview).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Query data](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) | [searchResponse](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse?view=graph-rest-1.0) collection | Run the query specified in the request body. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| acronyms | [microsoft.graph.search.acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) collection | Administrative answer in Microsoft Search results to define common acronyms in an organization. |
| bookmarks | [microsoft.graph.search.bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) collection | Administrative answer in Microsoft Search results for common search queries in an organization. |
| qnas | [microsoft.graph.search.qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) collection | Administrative answer in Microsoft Search results that provide answers for specific search keywords in an organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.searchEntity"
}
```

## See also

Explore the [query](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) action.
