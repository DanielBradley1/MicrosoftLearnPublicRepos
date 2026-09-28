<!-- Source: https://learn.microsoft.com/en-us/graph/search-concept-overview -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Overview of the Microsoft Search API in Microsoft Graph

Microsoft Search is an enterprise search engine that delivers productivity gains and relevant search results for your organization. It harnesses the collective knowledge and productivity of an organization, and surfaces relevant content to keep end users up to date. Microsoft Search is available in various experiences including Office, SharePoint, Delve, Windows, and Bing. You can use the Microsoft Search API in Microsoft Graph to extend Microsoft Search to your apps.

## Why use the Microsoft Search API?

### One unified search endpoint for Microsoft cloud data

The Microsoft Search API provides one unified search endpoint that you can use to [query](https://learn.microsoft.com/en-us/graph/api/search-query) data in the Microsoft cloud—messages and events in Outlook mailboxes and files on OneDrive and SharePoint—that Microsoft Search already indexes.

### Include custom external data in search experience

Use [Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoftsearch/connectors-overview) \(formerly Microsoft Graph connectors\) to include data outside of the Microsoft cloud in your search experience. For instance, connect to an organization's human resources database or product catalog. Then use the Microsoft Search API to seamlessly [query](https://learn.microsoft.com/en-us/graph/api/search-query) the external data source.

Browse the [Copilot connectors gallery](https://learn.microsoft.com/en-us/microsoftsearch/connectors-gallery) to find ready-to-use connectors. Alternatively, you can [build your own connectors](https://learn.microsoft.com/en-us/graph/api/resources/connectors-api-overview#common-use-cases) to index external custom items and query specific external data sources.

### Consistent, up-to-date search experience

When you use the Microsoft Search API, your customers benefit from more personalized, relevant search results powered by Microsoft Graph. The search experience in your apps will return results that are consistent with search in Office applications.

## What data can I add or access by using the Microsoft Search API?

The Microsoft Search API supports searching the following content in the Microsoft cloud:

- Outlook email [message](https://learn.microsoft.com/en-us/graph/api/resources/message) and calendar [event](https://learn.microsoft.com/en-us/graph/api/resources/event) resources.
- SharePoint and OneDrive files and folders \([driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) resources\), [list](https://learn.microsoft.com/en-us/graph/api/resources/list), [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem), [site](https://learn.microsoft.com/en-us/graph/api/resources/site), and [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive) resources.
- [Person](https://learn.microsoft.com/en-us/graph/api/resources/person) resources in an organization who are most relevant to a user.
- Content ingested through the Copilot connectors platform: [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem) resources.
- Administrative search answer resources: [acronym](https://learn.microsoft.com/en-us/graph/api/resources/search-acronym), [bookmark](https://learn.microsoft.com/en-us/graph/api/resources/search-bookmark), and [qna](https://learn.microsoft.com/en-us/graph/api/resources/search-qna) resources.

## API reference

Looking for the API reference for this service?

- [Use the Microsoft Search API to query data v1.0](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-1.0&preserve-view=true)
- [Use the Microsoft Search API to query data beta](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-beta&preserve-view=true)
- [Use the Microsoft Search API to index data](https://learn.microsoft.com/en-us/graph/api/resources/connectors-api-overview)
- [Use the Microsoft Search API to manage administrative search answers v1.0](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview?view=graph-rest-1.0&preserve-view=true)
- [Use the Microsoft Search API to manage administrative search answers beta](https://learn.microsoft.com/en-us/graph/api/resources/search-api-answers-overview?view=graph-rest-beta&preserve-view=true)

## Next steps

- Learn more about [Microsoft Search](https://learn.microsoft.com/en-us/microsoftsearch/).
- Learn more about a few key use cases:

  - [Manage connections to index external content](https://learn.microsoft.com/en-us/graph/connecting-external-content-manage-connections)
  - [Index external content](https://learn.microsoft.com/en-us/graph/connecting-external-content-manage-items)
  - [Search Outlook messages](https://learn.microsoft.com/en-us/graph/search-concept-messages)
  - [Search calendar events](https://learn.microsoft.com/en-us/graph/search-concept-events)
  - [Search content in SharePoint and OneDrive](https://learn.microsoft.com/en-us/graph/search-concept-files)
  - [Search external content](https://learn.microsoft.com/en-us/graph/search-concept-custom-types)
  - [Search with application permissions](https://learn.microsoft.com/en-us/graph/search-concept-searchall)
  - [Search person](https://learn.microsoft.com/en-us/graph/search-concept-person) \(preview\)
  - [Manage administrative search answers](https://learn.microsoft.com/en-us/graph/search-concept-answers) \(preview\)
  - [Manage search results layout](https://learn.microsoft.com/en-us/graph/search-concept-display-layout) \(preview\)
  - [Refine search results](https://learn.microsoft.com/en-us/graph/search-concept-aggregation)
  - [Request spelling correction](https://learn.microsoft.com/en-us/graph/search-concept-speller) \(preview\)
  - [Sort search results](https://learn.microsoft.com/en-us/graph/search-concept-sort)
  - [Use query templates](https://learn.microsoft.com/en-us/graph/search-concept-query-template) \(preview\)
  - [Trim duplicate search results](https://learn.microsoft.com/en-us/graph/search-concept-trim-duplicate) \(preview\)

- Explore the search APIs in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
- Download the [sample search connector](https://github.com/microsoftgraph/msgraph-search-connector-sample) from GitHub.
- Engage with the community on [Microsoft Q&A](https://learn.microsoft.com/en-us/answers/products/m365#microsoft-graph) or on GitHub.
