<!-- Source: https://learn.microsoft.com/en-us/graph/search-concept-acronym -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Use the Microsoft Search API to search acronyms

You can use the Microsoft Search API in Microsoft Graph to search acronyms in your organization. Administrators can create acronyms in the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home#/MicrosoftSearch/acronyms) or via the [Create acronym](https://learn.microsoft.com/en-us/graph/api/search-searchentity-post-acronyms) API.

Caution

The search API schema has changed in the beta version. Some properties in a search request and response have been renamed or removed. For details, see [Schema change deprecation warning](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-beta&preserve-view=true#schema-change-deprecation-warning). The examples in this topic show the up-to-date schema.

After acronyms are created, to search for them, in the [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest), in the **entityTypes** property, specify `acronym` as the value.

## Example 1: Search acronyms

### Request

```HTTP
POST https://graph.microsoft.com/v1.0/search/query
Content-Type: application/json

{
  "requests": [
    {
      "entityTypes": [
        "acronym"
      ],
      "query": {
        "queryString":"what is KQL"
      }
    }
  ]
}
```

### Response

```HTTP
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#search",
  "value": [
  {
   "@odata.type": "#microsoft.graph.searchResponse",
   "hitsContainers": [
    {
     "@odata.type": "#microsoft.graph.searchHitsContainer",
     "hits": [
      {
       "@odata.type": "#microsoft.graph.searchHit",
       "hitId": "a9f59c69-f4a1-42ac-820e-0f35114300f8",
       "rank": 1,
       "resource": {
          "@odata.type": "#microsoft.graph.search.acronym",
          "id": "a9f59c69-f4a1-42ac-820e-0f35114300f8",
          "displayName": "KQL",
          "description": "Kusto Query Language is a powerful tool to explore your data and discover patterns, identify anomalies and outliers, create statistical modeling, and more.",
          "webUrl": "https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query",
          "standsFor": "Kusto Query Language"
        }
       }
      }
     ],
     "total": 1,
     "moreResultsAvailable": false
    }
   ]
  }
 ]
}
```

## Known issues

- Sorting, aggregation, and pagination aren't supported for acronym searches.
- Combination searches with non-answer entity types \(for example, **driveItem** and **list**\) aren't supported.

## Next steps

- [Use the Microsoft Search API to query data](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview)
