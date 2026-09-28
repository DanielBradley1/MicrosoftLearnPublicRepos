<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/search?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# search resource type

Namespace: microsoft.graph

The search resource is the top level object representing the search endpoint. It serves as an anchor to the [query](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) action.

This resource isn't expected to be called as such. Any request on the resource incurs a Bad Request.

Important

Microsoft 365 Copilot connectors are currently in public preview status. To gain access to connectors functionality, you must turn on the Targeted release option in your tenant. For more information, see the [connectors preview program](https://learn.microsoft.com/en-us/microsoftsearch/connectors-preview).

## JSON representation

None

## Properties

None

## Relationships

None

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Query data](https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0) | [searchResponse](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse?view=graph-rest-1.0) Collection | Executes the query specified in the [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0) |
