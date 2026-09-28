<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# searchRequest resource type

Namespace: microsoft.graph

A search request formatted in a JSON blob.

The JSON blob contains the types of resources expected in the response, the underlying sources, paging parameters, sort options, requested aggregations and fields, and actual search query. See [examples](#related-content) of search requests on various resources.

Note

Be aware of [known limitations](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-1.0#known-limitations) on searching specific combinations of entity types, and sorting or aggregating search results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aggregationFilters | String collection | Contains one or more filters to obtain search results aggregated and filtered to a specific value of a field. Optional.  <br>Build this filter based on a prior search that aggregates by the same field. From the response of the prior search, identify the [searchBucket](https://learn.microsoft.com/en-us/graph/api/resources/searchbucket?view=graph-rest-1.0) that filters results to the specific value of the field, use the string in its **aggregationFilterToken** property, and build an aggregation filter string in the format **"{field}:\\"{aggregationFilterToken}\\""**.  <br>If multiple values for the same field need to be provided, use the strings in its **aggregationFilterToken** property and build an aggregation filter string in the format **"{field}:or\(\\"{aggregationFilterToken1}\\",\\"{aggregationFilterToken2}\\"\)"**.  <br>For example, searching and aggregating drive items by file type returns a **searchBucket** for the file type `docx` in the response. You can conveniently use the **aggregationFilterToken** returned for this **searchBucket** in a subsequent search query and filter matches down to drive items of the `docx` file type. [Example 1](https://learn.microsoft.com/en-us/graph/search-concept-aggregation#example-1-request-aggregations-by-string-fields) and [example 2](https://learn.microsoft.com/en-us/graph/search-concept-aggregation#example-2-apply-an-aggregation-filter-based-on-a-previous-request) show the actual requests and responses. |
| aggregations | [aggregationOption](https://learn.microsoft.com/en-us/graph/api/resources/aggregationoption?view=graph-rest-1.0) collection | Specifies aggregations \(also known as refiners\) to be returned alongside search results. Optional. |
| collapseProperties | [collapseProperty](https://learn.microsoft.com/en-us/graph/api/resources/collapseproperty?view=graph-rest-1.0) collection | Contains the ordered collection of fields and limit to collapse results. Optional. |
| contentSources | String collection | Contains the connection to be targeted. |
| enableTopResults | Boolean | This triggers hybrid sort for messages : the first 3 messages are the most relevant. This property is only applicable to entityType=`message`. Optional. |
| entityTypes | entityType collection | One or more types of resources expected in the response. The possible values are: `event`, `message`, `driveItem`, `externalItem`, `site`, `list`, `listItem`, `drive`, `chatMessage`, `person`, `acronym`, `bookmark`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `chatMessage`, `person`, `acronym`, `bookmark`. See [known limitations](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-1.0#known-limitations) for those combinations of two or more entity types that are supported in the same search request. Required. |
| fields | String collection | Contains the fields to be returned for each resource object specified in **entityTypes**, allowing customization of the fields returned by default; otherwise, including additional fields such as custom managed properties from SharePoint and OneDrive, or custom fields in **externalItem** from the content that Microsoft 365 Copilot connectors bring in. The **fields** property can use the [semantic labels](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector#step-6-assign-property-labels) applied to properties. For example, if a property is labeled as title, you can retrieve it using the following syntax: `label_title`. Optional. |
| from | Int32 | Specifies the offset for the search results. Offset 0 returns the very first result. Optional. |
| query | [searchQuery](https://learn.microsoft.com/en-us/graph/api/resources/searchquery?view=graph-rest-1.0) | Contains the query terms. Required. |
| queryAlterationOptions | [searchAlterationOptions](https://learn.microsoft.com/en-us/graph/api/resources/searchalterationoptions?view=graph-rest-1.0) | Query alteration options formatted in a JSON blob that contains two optional flags related to spelling correction. Optional. |
| region | String | The geographic location for the search. Required for searches that use application permissions. For details, see [Get the region value](https://learn.microsoft.com/en-us/graph/search-concept-searchall). |
| resultTemplateOptions | [resultTemplateOption](https://learn.microsoft.com/en-us/graph/api/resources/resulttemplateoption?view=graph-rest-1.0) collection | Provides the search result template options to render search results from connectors. |
| sharePointOneDriveOptions | [sharePointOneDriveOptions](https://learn.microsoft.com/en-us/graph/api/resources/sharepointonedriveoptions?view=graph-rest-1.0) | Indicates the kind of contents to be searched when a search is performed using application permissions. Optional. |
| size | Int32 | The size of the page to be retrieved. The maximum value is 500. Optional. |
| sortProperties | [sortProperty](https://learn.microsoft.com/en-us/graph/api/resources/sortproperty?view=graph-rest-1.0) collection | Contains the ordered collection of fields and direction to sort results. There can be at most 5 sort properties in the collection. Optional. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "aggregationFilters": ["String"],
  "aggregations": [{"@odata.type": "microsoft.graph.aggregationOption"}],
  "collapseProperties": [{"@odata.type": "microsoft.graph.collapseProperty"}],
  "enableTopResults": "Boolean",
  "entityTypes": ["String"],
  "contentSources": ["String"],
  "fields": ["String"],
  "from": "Int32",
  "query": {"@odata.type": "microsoft.graph.searchQuery"},
  "queryAlterationOptions": {"@odata.type": "microsoft.graph.searchAlterationOptions"},
  "region": "String",
  "resultTemplateOptions": [{"@odata.type": "microsoft.graph.resultTemplateOption"}],
  "sharePointOneDriveOptions": {"@odata.type": "microsoft.graph.sharePointOneDriveOptions"},
  "size": "Int32"
}
```

## Related content

- [Use query templates](https://learn.microsoft.com/en-us/graph/search-concept-query-template)
- Search [mail messages](https://learn.microsoft.com/en-us/graph/search-concept-messages)
- Search [calendar events](https://learn.microsoft.com/en-us/graph/search-concept-events)
- Search content in SharePoint and OneDrive \([files, lists and sites](https://learn.microsoft.com/en-us/graph/search-concept-files)\)
- [Sort](https://learn.microsoft.com/en-us/graph/search-concept-sort) search results
- Use [aggregations](https://learn.microsoft.com/en-us/graph/search-concept-aggregation) to refine search results
- Use [display layout](https://learn.microsoft.com/en-us/graph/search-concept-display-layout)
- Enable [spell corrections](https://learn.microsoft.com/en-us/graph/search-concept-speller) in search results
- [Search SharePoint content with application permissions](https://learn.microsoft.com/en-us/graph/search-concept-searchall)
- [Collapse search results](https://learn.microsoft.com/en-us/graph/search-concept-collapse)
