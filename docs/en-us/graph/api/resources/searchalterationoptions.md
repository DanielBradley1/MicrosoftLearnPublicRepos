<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchalterationoptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# searchAlterationOptions resource type

Namespace: microsoft.graph

Provides the search alteration options for spelling correction.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableModification | Boolean | Indicates whether spelling modifications are enabled. If enabled, the user gets the search results for the corrected query *if there were no results* for the original query with typos. The [response](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse) will also include the spelling modification information in the **queryAlterationResponse** property. Optional. |
| enableSuggestion | Boolean | Indicates whether spelling suggestions are enabled. If enabled, the user gets the search results for the original search query and suggestions for spelling correction in the **queryAlterationResponse** property of the [response](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse) for the typos in the query. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "enableModification": "Boolean",
  "enableSuggestion": "Boolean"
}
```
