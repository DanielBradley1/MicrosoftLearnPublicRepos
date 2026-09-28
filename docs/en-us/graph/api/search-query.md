<!-- Source: https://learn.microsoft.com/en-us/graph/api/search-query?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-09 -->

# searchEntity: query

Namespace: microsoft.graph

Runs the query specified in the request body. Search results are provided in the response.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.Read | Acronym.Read.All, Bookmark.Read.All, Calendars.Read, Chat.Read, ExternalItem.Read.All, Files.Read.All, QnA.Read.All, Sites.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.Read.All | Sites.Read.All |

## HTTP request

```HTTP
POST /search/query
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| requests | [searchRequest](https://learn.microsoft.com/en-us/graph/api/resources/searchrequest?view=graph-rest-1.0) collection | A collection of one or more search requests each formatted in a JSON blob. Each JSON blob contains the types of resources expected in the response, the underlying sources, paging parameters, requested fields, and actual search query. Be aware of [known limitations](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-1.0#known-limitations) on searching specific combinations of entity types, and sorting or aggregating search results. |

## Response

If successful, this method returns `HTTP 200 OK` response code and a [searchResponse](https://learn.microsoft.com/en-us/graph/api/resources/searchresponse?view=graph-rest-1.0) collection object in the response body.

## Examples

### Example 1: Basic call to perform a search request

The following example shows how to search for expected connector items.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/search/query
Content-type: application/json

{
  "requests": [
    {
      "entityTypes": [
        "externalItem"
      ],
      "contentSources": [
        "/external/connections/connectionfriendlyname"
      ],
       "region": "US",
       "query": {
        "queryString": "contoso product"
      },
      "from": 0,
      "size": 25,
      "fields": [
        "title",
        "description"
      ]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Search.Query;
using Microsoft.Graph.Models;

var requestBody = new QueryPostRequestBody
{
	Requests = new List<SearchRequest>
	{
		new SearchRequest
		{
			EntityTypes = new List<EntityType?>
			{
				EntityType.ExternalItem,
			},
			ContentSources = new List<string>
			{
				"/external/connections/connectionfriendlyname",
			},
			Region = "US",
			Query = new SearchQuery
			{
				QueryString = "contoso product",
			},
			From = 0,
			Size = 25,
			Fields = new List<string>
			{
				"title",
				"description",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Query.PostAsQueryPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsearch "github.com/microsoftgraph/msgraph-sdk-go/search"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphsearch.NewQueryPostRequestBody()


searchRequest := graphmodels.NewSearchRequest()
entityTypes := []graphmodels.EntityTypeable {
	entityType := graphmodels.EXTERNALITEM_ENTITYTYPE 
	searchRequest.SetEntityType(&entityType)
}
searchRequest.SetEntityTypes(entityTypes)
contentSources := []string {
	"/external/connections/connectionfriendlyname",
}
searchRequest.SetContentSources(contentSources)
region := "US"
searchRequest.SetRegion(&region) 
query := graphmodels.NewSearchQuery()
queryString := "contoso product"
query.SetQueryString(&queryString) 
searchRequest.SetQuery(query)
from := int32(0)
searchRequest.SetFrom(&from) 
size := int32(25)
searchRequest.SetSize(&size) 
fields := []string {
	"title",
	"description",
}
searchRequest.SetFields(fields)

requests := []graphmodels.SearchRequestable {
	searchRequest,
}
requestBody.SetRequests(requests)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
query, err := graphClient.Search().Query().PostAsQueryPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.search.query.QueryPostRequestBody queryPostRequestBody = new com.microsoft.graph.search.query.QueryPostRequestBody();
LinkedList<SearchRequest> requests = new LinkedList<SearchRequest>();
SearchRequest searchRequest = new SearchRequest();
LinkedList<EntityType> entityTypes = new LinkedList<EntityType>();
entityTypes.add(EntityType.ExternalItem);
searchRequest.setEntityTypes(entityTypes);
LinkedList<String> contentSources = new LinkedList<String>();
contentSources.add("/external/connections/connectionfriendlyname");
searchRequest.setContentSources(contentSources);
searchRequest.setRegion("US");
SearchQuery query = new SearchQuery();
query.setQueryString("contoso product");
searchRequest.setQuery(query);
searchRequest.setFrom(0);
searchRequest.setSize(25);
LinkedList<String> fields = new LinkedList<String>();
fields.add("title");
fields.add("description");
searchRequest.setFields(fields);
requests.add(searchRequest);
queryPostRequestBody.setRequests(requests);
var result = graphClient.search().query().post(queryPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const searchResponse = {
  requests: [
    {
      entityTypes: [
        'externalItem'
      ],
      contentSources: [
        '/external/connections/connectionfriendlyname'
      ],
       region: 'US',
       query: {
        queryString: 'contoso product'
      },
      from: 0,
      size: 25,
      fields: [
        'title',
        'description'
      ]
    }
  ]
};

await client.api('/search/query')
	.post(searchResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Search\Query\QueryPostRequestBody;
use Microsoft\Graph\Generated\Models\SearchRequest;
use Microsoft\Graph\Generated\Models\EntityType;
use Microsoft\Graph\Generated\Models\SearchQuery;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new QueryPostRequestBody();
$requestsSearchRequest1 = new SearchRequest();
$requestsSearchRequest1->setEntityTypes([new EntityType('externalItem'),	]);
$requestsSearchRequest1->setContentSources(['/external/connections/connectionfriendlyname', 	]);
$requestsSearchRequest1->setRegion('US');
$requestsSearchRequest1Query = new SearchQuery();
$requestsSearchRequest1Query->setQueryString('contoso product');
$requestsSearchRequest1->setQuery($requestsSearchRequest1Query);
$requestsSearchRequest1->setFrom(0);
$requestsSearchRequest1->setSize(25);
$requestsSearchRequest1->setFields(['title', 'description', 	]);
$requestsArray []= $requestsSearchRequest1;
$requestBody->setRequests($requestsArray);


$result = $graphServiceClient->search()->query()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	requests = @(
		@{
			entityTypes = @(
			"externalItem"
		)
		contentSources = @(
		"/external/connections/connectionfriendlyname"
	)
	region = "US"
	query = @{
		queryString = "contoso product"
	}
	from = 0
	size = 25
	fields = @(
	"title"
"description"
)
}
)
}

Invoke-MgQuerySearch -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.search.query.query_post_request_body import QueryPostRequestBody
from msgraph.generated.models.search_request import SearchRequest
from msgraph.generated.models.entity_type import EntityType
from msgraph.generated.models.search_query import SearchQuery
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = QueryPostRequestBody(
	requests = [
		SearchRequest(
			entity_types = [
				EntityType.ExternalItem,
			],
			content_sources = [
				"/external/connections/connectionfriendlyname",
			],
			region = "US",
			query = SearchQuery(
				query_string = "contoso product",
			),
			from = 0,
			size = 25,
			fields = [
				"title",
				"description",
			],
		),
	],
)

result = await graph_client.search.query.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "searchTerms": [
        "searchTerms-value"
      ],
      "hitsContainers": [
        {
          "hits": [
            {
              "hitId": "1",
              "rank": 1,
              "summary": "_summary-value",
              "resource": "The source field will contain the underlying graph entity part of the response"
            }
          ],
          "total": 47,
          "moreResultsAvailable": true
        }
      ]
    }
  ]
}
```

### Example 2: Basic call to use queryTemplate

The following example shows how to use the queryable property **createdBy** to retrieve all files created by a user.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/search/query
Content-type: application/json

{
  "requests": [
    {
      "entityTypes": [
        "listItem"
      ],
        "region": "US",
        "query": {
        "queryString": "contoso",
        "queryTemplate":"{searchTerms} CreatedBy:Bob"
      },
      "from": 0,
      "size": 25
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Search.Query;
using Microsoft.Graph.Models;

var requestBody = new QueryPostRequestBody
{
	Requests = new List<SearchRequest>
	{
		new SearchRequest
		{
			EntityTypes = new List<EntityType?>
			{
				EntityType.ListItem,
			},
			Region = "US",
			Query = new SearchQuery
			{
				QueryString = "contoso",
				QueryTemplate = "{searchTerms} CreatedBy:Bob",
			},
			From = 0,
			Size = 25,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Query.PostAsQueryPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsearch "github.com/microsoftgraph/msgraph-sdk-go/search"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphsearch.NewQueryPostRequestBody()


searchRequest := graphmodels.NewSearchRequest()
entityTypes := []graphmodels.EntityTypeable {
	entityType := graphmodels.LISTITEM_ENTITYTYPE 
	searchRequest.SetEntityType(&entityType)
}
searchRequest.SetEntityTypes(entityTypes)
region := "US"
searchRequest.SetRegion(&region) 
query := graphmodels.NewSearchQuery()
queryString := "contoso"
query.SetQueryString(&queryString) 
queryTemplate := "{searchTerms} CreatedBy:Bob"
query.SetQueryTemplate(&queryTemplate) 
searchRequest.SetQuery(query)
from := int32(0)
searchRequest.SetFrom(&from) 
size := int32(25)
searchRequest.SetSize(&size) 

requests := []graphmodels.SearchRequestable {
	searchRequest,
}
requestBody.SetRequests(requests)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
query, err := graphClient.Search().Query().PostAsQueryPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.search.query.QueryPostRequestBody queryPostRequestBody = new com.microsoft.graph.search.query.QueryPostRequestBody();
LinkedList<SearchRequest> requests = new LinkedList<SearchRequest>();
SearchRequest searchRequest = new SearchRequest();
LinkedList<EntityType> entityTypes = new LinkedList<EntityType>();
entityTypes.add(EntityType.ListItem);
searchRequest.setEntityTypes(entityTypes);
searchRequest.setRegion("US");
SearchQuery query = new SearchQuery();
query.setQueryString("contoso");
query.setQueryTemplate("{searchTerms} CreatedBy:Bob");
searchRequest.setQuery(query);
searchRequest.setFrom(0);
searchRequest.setSize(25);
requests.add(searchRequest);
queryPostRequestBody.setRequests(requests);
var result = graphClient.search().query().post(queryPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const searchResponse = {
  requests: [
    {
      entityTypes: [
        'listItem'
      ],
        region: 'US',
        query: {
        queryString: 'contoso',
        queryTemplate: '{searchTerms} CreatedBy:Bob'
      },
      from: 0,
      size: 25
    }
  ]
};

await client.api('/search/query')
	.post(searchResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Search\Query\QueryPostRequestBody;
use Microsoft\Graph\Generated\Models\SearchRequest;
use Microsoft\Graph\Generated\Models\EntityType;
use Microsoft\Graph\Generated\Models\SearchQuery;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new QueryPostRequestBody();
$requestsSearchRequest1 = new SearchRequest();
$requestsSearchRequest1->setEntityTypes([new EntityType('listItem'),	]);
$requestsSearchRequest1->setRegion('US');
$requestsSearchRequest1Query = new SearchQuery();
$requestsSearchRequest1Query->setQueryString('contoso');
$requestsSearchRequest1Query->setQueryTemplate('{searchTerms} CreatedBy:Bob');
$requestsSearchRequest1->setQuery($requestsSearchRequest1Query);
$requestsSearchRequest1->setFrom(0);
$requestsSearchRequest1->setSize(25);
$requestsArray []= $requestsSearchRequest1;
$requestBody->setRequests($requestsArray);


$result = $graphServiceClient->search()->query()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	requests = @(
		@{
			entityTypes = @(
			"listItem"
		)
		region = "US"
		query = @{
			queryString = "contoso"
			queryTemplate = '{searchTerms} CreatedBy:Bob"
		}
		from = 0
		size = 25
	}
)
}

Invoke-MgQuerySearch -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.search.query.query_post_request_body import QueryPostRequestBody
from msgraph.generated.models.search_request import SearchRequest
from msgraph.generated.models.entity_type import EntityType
from msgraph.generated.models.search_query import SearchQuery
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = QueryPostRequestBody(
	requests = [
		SearchRequest(
			entity_types = [
				EntityType.ListItem,
			],
			region = "US",
			query = SearchQuery(
				query_string = "contoso",
				query_template = "{searchTerms} CreatedBy:Bob",
			),
			from = 0,
			size = 25,
		),
	],
)

result = await graph_client.search.query.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "searchTerms": [
                "contoso"
            ],
            "hitsContainers": [
                {
                    "hits": [
                        {
                            "hitId": "1",
                            "rank": 1,
                            "summary": "_summary-value",
                            "resource": {
                                "@odata.type": "#microsoft.graph.listItem",
                                "id": "c23c7035-73d6-4bad-8901-9e2930d4be8e",
                                "createdBy": {
                                    "user": {
                                        "displayName": "Bob",
                                        "email": "Bob@contoso.com"
                                    }
                                },
                                "createdDateTime": "2021-11-19T17:04:18Z",
                                "lastModifiedDateTime": "2023-03-09T18:52:26Z"
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

## Related content

- Search [mail messages](https://learn.microsoft.com/en-us/graph/search-concept-messages)
- Search [calendar events](https://learn.microsoft.com/en-us/graph/search-concept-events)
- Search content in SharePoint and OneDrive \([files, lists and sites](https://learn.microsoft.com/en-us/graph/search-concept-files)\)
- Search [custom types \(Graph Connectors\)](https://learn.microsoft.com/en-us/graph/search-concept-custom-types) data
- Search with [queryTemplate](https://learn.microsoft.com/en-us/graph/search-concept-query-template)
- [Sort](https://learn.microsoft.com/en-us/graph/search-concept-sort) search results
- Use [aggregations](https://learn.microsoft.com/en-us/graph/search-concept-aggregation) to refine search results
