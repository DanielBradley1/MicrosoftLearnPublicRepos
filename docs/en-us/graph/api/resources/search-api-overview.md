<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-13 -->

# Use the Microsoft Search API to query data

You can use the Microsoft Search API to query Microsoft 365 data in your apps.

Search requests run in the context of the signed-in user, identified using an [access token with delegated permissions](https://learn.microsoft.com/en-us/graph/auth-v2-user).

## Common use cases

The Microsoft Search API provides a [query](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) method to search across your data in Microsoft Search, where you pass a [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0) in the request body, defining the specifics of your search.

This section lists the common use cases of the **query** method, based on the properties and parameters you set in the **query** [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0) body.

Search requests run on behalf of the user. Search results are scoped to enforce any access control applied to the items. For example, in the context of files, permissions on the files are evaluated as part of the search request. Users cannot access more items in a search than they can otherwise obtain from a corresponding GET operation with the same permissions and access control.

| Use cases | Properties to define in the query request body |
| :--- | :--- |
| [Scope search results based on entity types](#scope-search-based-on-entity-types) | **entityTypes** |
| [Page results](#page-search-results) | **from** and **size** |
| [Get the most relevant emails](#get-the-most-relevant-emails) | **enableTopResults** |
| [Get selected properties](#get-selected-properties) | **fields** |
| [Use KQL in query terms](#keyword-query-language-kql-support) | **query** |
| [Collapse search results](#collapse-search-results) | **collapseProperties** |
| [Sort search results](#sort-search-results) | **sortProperties** |
| [Refine results using aggregations](#refine-results-using-aggregations) | **aggregations** |
| [Request spelling correction](#request-spelling-correction) | **queryAlterationOptions** |
| [Search display layout](#search-display-layout) \(preview\) | **resultTemplateOptions** |

## Scope search based on entity types

Define the scope of the search request using the **entityTypes** property in the **query** request payload. The following table describes the types available to query and the supported permissions to access the data.

| EntityType | Permission scope required to access the items | Source | Comment |
| :--- | :--- | :--- | :--- |
| [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym?view=graph-rest-1.0) | Acronym.Read.All | Microsoft Search | Acronyms in Microsoft Search in your organization. |
| [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark?view=graph-rest-1.0) | Bookmark.Read.All | Microsoft Search | Bookmarks in Microsoft Search in your organization. |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Chat.Read, Chat.ReadWrite, ChannelMessage.Read.All | Teams | Teams messages. |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.Read, Mail.ReadWrite | Exchange Online | Email messages. |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.Read, Calendars.ReadWrite | Exchange Online | Calendar events. |
| [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) | Files.Read.All, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All | SharePoint | Document libraries. |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Files.Read.All, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All | SharePoint and OneDrive | Files, folders, pages, and news. |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Sites.Read.All, Sites.ReadWrite.All | SharePoint and OneDrive | Lists. Note that document libraries are also returned as lists. |
| [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) | Sites.Read.All, Sites.ReadWrite.All | SharePoint and OneDrive | List items. Note that files and folders are also returned as list items; **listItem** is the super class of **driveItem**. |
| [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna?view=graph-rest-1.0) | QnA.Read.All | Microsoft Search | Questions and answers in Microsoft Search in your organization. |
| [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) | Sites.Read.All, Sites.ReadWrite.All | SharePoint | Sites in SharePoint. |

## Page search results

Control pagination of the search results by specifying the following two properties in the **query** request body:

- **from** - An integer that indicates the 0-based starting point to list search results on the page. The default value is 0.
- **size** - An integer that indicates the number of results to be returned for a page. The default is 25 results. The maximum is 1000 results.

Note the following limits if you're searching the **event** or **message** entity:

- **from** must start at zero in the first page request; otherwise, the request results in an HTTP 400 `Bad request`.
- The maximum number of results per page \(**size**\) is 25 for **message** and **event**.

The upper limit for SharePoint or OneDrive items is 1000. A reasonable page size is 200. A larger page size generally incurs higher latency.

Best practices:

- Specify a smaller first page in the initial request. For example, specify **from** as 0, **size** as 25.
- Paginate subsequent pages by updating the **from** and **size** properties. You can increase the page size in each subsequent request. The following table shows an example.
  | Page | from | size |
  | :--- | :--- | :--- |
  | 1 | 0 | 25 |
  | 2 | 25 | 50 |
  | 3 | 75 | 75 |
  | 4 | 150 | 100 |

## Get the most relevant emails

When searching the **message** entity, specifying **enableTopResults** as `true` returns a hybrid list of messages: the first three messages in the response are sorted by relevance; the remaining messages are sorted by date/time.

## Get selected properties

When searching an entity type, such as **message**, **event**, **drive**, **driveItem**, **list**, **listItem**, **site**, **externalItem**, you can include in the **fields** property specific entity properties to return in the search results. This is similar to using the [OData system query option, $select](https://learn.microsoft.com/en-us/graph/query-parameters#select-parameter) in REST requests. The search API does not technically support these query options because the behavior is expressed in the POST body.

For all these entity types, specifying the **fields** property reduces the number of properties returned in the response, optimizing the payload over the wire.

The **listItem** and **externalItem** entities are the only supported entities that allow getting extended retrievable fields configured in the schema. You cannot retrieve extended properties from all the other entities by using the search API. For example, if you created a retrievable field for **externalItem** in the search schema, or if you have a retrievable custom column on a **listItem**, you can retrieve these properties from search. To retrieve an extended property on a file, specify the **listItem** type in the request.

If the **fields** specified in the request are either not present in the schema, or not marked as retrievable, they will not be returned in the response. Invalid fields in the request are silently ignored.

If you do not specify any **fields** in the request, you will get the default set of properties for all types. For extended properties, **listItem** and **externalItem** behave differently when no **fields** are passed in the request:

- **listItem** will not return any custom field.
- **externalItem** will return all the fields marked with the **retrievable** attribute in the Microsoft 365 Copilot connector \(formerly Microsoft Graph connectors\) schema for that particular connection.

## Keyword Query Language \(KQL\) support

Specify free text keywords, operators \(such as `AND`, `OR`\), and property restrictions in KQL syntax in the actual search query string \(**query** property of the **query** request body\). The [XRANK](https://learn.microsoft.com/en-us/graph/search-concept-xrank) operator boosts the dynamic rank of items based on certain term occurrences within the match expression, without changing which items match the query. The syntax and command depend on the entity types \(in the **entityTypes** property\) you target in the same **query** request body.

Depending on the entity type, the searchable properties vary. For details, see:

- [Email properties](https://learn.microsoft.com/en-us/microsoft-365/compliance/keyword-queries-and-search-conditions#searchable-email-properties)
- [Site properties](https://learn.microsoft.com/en-us/microsoft-365/compliance/keyword-queries-and-search-conditions#searchable-site-properties)

## Collapse search results

The **collapseProperties** property contains a set of criteria, fields, and limit size used to collapse results in a response body. Using **collapseProperties** only impacts the recall but not ranking/sorting actions.

The [query](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) method lets you customize the collapse property by specifying **collapseProperties** on the `requests` parameter, which is a collection of [collapseProperty](https://learn.microsoft.com/en-us/graph/api/resources/collapseproperty?view=graph-rest-1.0) objects. This allows you to specify a set of one or more collapse properties.

Note that collapsing results is currently supported for the following entity types: [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0), [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0), [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0), [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0).

To use the collapse clause effectively, the properties you apply it to must be queryable, and either sortable or refinable. When using multi-level collapse, it's important to note that each subsequent property's limit size specified in a multi-level request should be equal to or smaller than the previous one. If a subsequent property's limit size exceeds the previous one, the server will respond with an `HTTP 400 Bad Request` error.

See [collapse search results](https://learn.microsoft.com/en-us/graph/search-concept-collapse) for more collapse results examples.

## Sort search results

Search results in the response are sorted in the following default sort order:

- **message** and **event** are sorted by date.
- All SharePoint, OneDrive, person and connector types are sorted by relevance.

The [query](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) method lets you customize the search order by specifying the **sortProperties** on the `requests` parameter, which is a collection of [sortProperty](https://learn.microsoft.com/en-us/graph/api/resources/sortproperty?view=graph-rest-1.0) objects. This allows you to specify a list of one or more sortable properties and the sort order.

Note that sorting results is currently only supported on the following SharePoint and OneDrive types: [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0), [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0).

The properties on which the sort clause are applied need to be sortable in the SharePoint [search schema](https://learn.microsoft.com/en-us/sharepoint/manage-search-schema). If the property specified in the request is not sortable or does not exist, the response will return an error, `HTTP 400 Bad Request`. Note that you cannot specify to sort documents by relevance using [sortProperty](https://learn.microsoft.com/en-us/graph/api/resources/sortproperty?view=graph-rest-1.0).

When specifying the **name** of a [sortProperty](https://learn.microsoft.com/en-us/graph/api/resources/sortproperty?view=graph-rest-1.0) object, you can either use the property name from the Microsoft Graph type \(for example, in [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0)\), or the name of the managed property in the search index.

See [sort search results](https://learn.microsoft.com/en-us/graph/search-concept-sort) for examples that show how to sort results.

## Refine results using aggregations

Aggregations \(also known as refiners in SharePoint\) are a very popular way to enhance a search experience. In addition to the results, they provide some level of aggregate information on the matching set of search results. For example, you can provide information on the most represented authors of the documents matching the query, or the most represented file types, etc.

In the [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0), specify the aggregations that should be returned in addition to the search results. The description of each aggregation is defined in the [aggregationOption](https://learn.microsoft.com/en-us/graph/api/resources/aggregationoption?view=graph-rest-1.0), which specifies the property on which the aggregation should be computed, and the number of [searchBucket](https://learn.microsoft.com/en-us/graph/api/resources/searchbucket?view=graph-rest-1.0) to be returned in the response.

The properties on which the aggregation is requested need to be refinable in the SharePoint [search schema](https://learn.microsoft.com/en-us/sharepoint/manage-search-schema). If the property specified is not refinable or does not exist, the response returns `HTTP 400 Bad Request`.

Once the response is returned containing the collection of [searchBucket](https://learn.microsoft.com/en-us/graph/api/resources/searchbucket?view=graph-rest-1.0) objects, it is possible to refine the search request to only the matching elements contained in one [searchBucket](https://learn.microsoft.com/en-us/graph/api/resources/searchbucket?view=graph-rest-1.0). This is achieved by passing back the **aggregationsFilterToken** value in the **aggregationFilters** property of the subsequent [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0).

Aggregations are currently supported for any refinable property on the following SharePoint and OneDrive types: [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0), [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0), and on Copilot connectors [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem?view=graph-rest-1.0).

For examples that show how to use aggregation to enhance and narrow down search results, see [Refine search results](https://learn.microsoft.com/en-us/graph/search-concept-aggregation).

## Request spelling correction

Spelling correction is a popular way to handle mismatches between typos in a user query and the correct words in matched contents. When typos are detected in the original user query, you can get the search result either for the original user query or the corrected alternate query. You can also get the spelling correction information for typos in the **queryAlterationResponse** property of the [searchResponse](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse?view=graph-rest-1.0).

In the request body of the [query](https://learn.microsoft.com/en-us/graph/api/search-query) method, specify the **queryAlterationOptions** that should be applied to the query for the spelling corrections. The description of **queryAlterationOptions** is defined in the [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0).

For examples that show how to use spelling corrections, see [Request spelling correction](https://learn.microsoft.com/en-us/graph/search-concept-speller).

## Search display layout

The search API allows you to render search results from [connectors](https://learn.microsoft.com/en-us/microsoftsearch/connectors-overview) by using the display layout or the result template configured by the IT admin for each connector. The result templates are [Adaptive Cards](https://adaptivecards.io/), which are a semantically meaningful combination of layout and data.

To get the result template in the [searchResponse](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse?view=graph-rest-1.0) you have to set the **enableResultTemplate** property to **true**, which is defined in the [resultTemplateOptions](https://learn.microsoft.com/en-us/graph/api/resources/resulttemplateoption?view=graph-rest-1.0) in the [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0). The response includes a **resultTemplateId** for every [searchHit](https://learn.microsoft.com/en-us/graph/api/resources/searchhit?view=graph-rest-1.0), which maps to one of the display layouts included in the **resultTemplates** dictionary that is part of the response.

For examples that show how to render search results, see [Use search display layout](https://learn.microsoft.com/en-us/graph/search-concept-display-layout).

## Error handling

The search API returns error responses as defined by [OData error object definition](http://docs.oasis-open.org/odata/odata-json-format/v4.01/cs01/odata-json-format-v4.01-cs01.html#sec_ErrorResponse), each of which is a JSON object containing a code and a message.

## Known limitations

The search API has the following limitations:

- The **query** method is defined to allow passing a collection of one or more **searchRequest** instances at once. However, the service currently supports only a single [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0) at a time.
- The [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0) resource supports passing multiple types of entities at a time. The following table lists the combinations that are supported.
  | Entity Type | acronym | bookmark | message | chatMessage | drive | driveItem | event | externalItem | list | listItem | person | qna | site |
  | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
  | acronym | True | True | - | - | - | - | - | - | - | - | - | True | - |
  | bookmark | True | True | - | - | - | - | - | - | - | - | - | True | - |
  | chatMessage | - | - | - | True | - | - | - | - | - | - | - | - | - |
  | drive | - | - | - | - | True | True | - | True | True | True | - | - | True |
  | driveItem | - | - | - | - | True | True | - | True | True | True | - | - | True |
  | event | - | - | - | - | - | - | True | - | - | - | - | - | - |
  | externalItem | - | - | - | - | True | True | - | True | True | True | - | - | True |
  | list | - | - | - | - | True | True | - | True | True | True | - | - | True |
  | listItem | - | - | - | - | True | True | - | True | True | True | - | - | True |
  | message | - | - | True | - | - | - | - | - | - | - | - | - | - |
  | person | - | - | - | - | - | - | - | - | - | - | True | - | - |
  | qna | True | True | - | - | - | - | - | - | - | - | - | True | - |
  | site | - | - | - | - | True | True | - | True | True | True | - | - | True |
- The **contentSource** property, which defines the connection to use, is only applicable when **entityType** is specified as `externalItem`.
- The search API doesn't support custom sort for **acronym**, **bookmark**, **message**, **chatMessage**, **event**, **person**, **qna**, or **externalItem**.
- The search API doesn't support aggregations for **acronym**, **bookmark**, **message**, **event**, **site**, **person**, **qna**, or **drive**.
- The search API doesn't support xrank for **acronym**, **bookmark**, **message**, **chatMessage**, **event**, **person**, **qna**, or **externalItem**.
- Guest search doesn't support searches for **acronym**, **bookmark**, **message**, **chatMessage**, **event**, **person**, **qna**, or **externalItem**.
- Customizations in SharePoint search, such as a custom search schema or result sources, can interfere with Microsoft Search API operations.
- The search API doesn't support the site-level [search schema](https://learn.microsoft.com/en-us/sharepoint/manage-search-schema). Use the tenant-level or default [search schema](https://learn.microsoft.com/en-us/sharepoint/manage-search-schema).

## Related content

- Learn more about a few key use cases:

  - [Search Teams messages](https://learn.microsoft.com/en-us/graph/search-concept-chat-messages)
  - [Search Outlook messages](https://learn.microsoft.com/en-us/graph/search-concept-messages)
  - [Search calendar events](https://learn.microsoft.com/en-us/graph/search-concept-events)
  - [Search content in SharePoint and OneDrive](https://learn.microsoft.com/en-us/graph/search-concept-files)
  - [Collapse search results](https://learn.microsoft.com/en-us/graph/search-concept-collapse)
  - [Sort search results](https://learn.microsoft.com/en-us/graph/search-concept-sort)
  - [Refine search results](https://learn.microsoft.com/en-us/graph/search-concept-aggregation)
  - [Request spelling correction](https://learn.microsoft.com/en-us/graph/search-concept-speller)
  - [Use search display layout](https://learn.microsoft.com/en-us/graph/search-concept-display-layout)
  - [Search content with application permission](https://learn.microsoft.com/en-us/graph/search-concept-searchall)
  - [XRANK search results](https://learn.microsoft.com/en-us/graph/search-concept-xrank)

- Explore the search APIs in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
- Find out about the [latest new features and updates](https://learn.microsoft.com/en-us/graph/whats-new-overview) for this API set.
