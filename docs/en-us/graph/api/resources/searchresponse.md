<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# searchResponse resource type

Namespace: microsoft.graph

Represents results from a search query, and the terms used for the query.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hitsContainers | [searchHitsContainer](https://learn.microsoft.com/en-us/graph/api/resources/searchhitscontainer?view=graph-rest-1.0) collection | A collection of search results. |
| queryAlterationResponse | [alterationResponse](https://learn.microsoft.com/en-us/graph/api/resources/alterationresponse?view=graph-rest-1.0) | Provides information related to spelling corrections in the alteration response. |
| resultTemplates | [resultTemplate](https://learn.microsoft.com/en-us/graph/api/resources/resulttemplate?view=graph-rest-1.0) collection | A dictionary of **resultTemplateIds** and associated values, which include the name and JSON schema of the result templates. |
| searchTerms | String collection | Contains the search terms sent in the initial search query. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hitsContainers": [{"@odata.type": "microsoft.graph.searchHitsContainer"}],
  "queryAlterationResponse": {"@odata.type": "microsoft.graph.alterationResponse"},
  "resultTemplates": [{"@odata.type":"microsoft.graph.resultTemplateDictionary"}],
  "searchTerms": ["String"]
}
```
