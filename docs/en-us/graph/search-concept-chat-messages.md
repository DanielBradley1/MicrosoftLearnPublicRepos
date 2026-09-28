<!-- Source: https://learn.microsoft.com/en-us/graph/search-concept-chat-messages -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Use the Microsoft Search API to search Teams messages

Use the Microsoft Search API in Microsoft Graph to search for information in Teams messages, return messages ranked by relevance, and render a dedicated search experience. The search applies to the body and attachments of messages in the signed-in user's Teams messages.

Caution

The search API schema has changed in the beta version. Some properties in a search request and response have been renamed or removed. For details, see [Schema change deprecation warning](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-beta&preserve-view=true#schema-change-deprecation-warning). The examples in this topic show the up-to-date schema.

Teams message search also looks for attachments. The [supported file types](https://learn.microsoft.com/en-us/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types) for message attachment search are the same as those for SharePoint Online search.

## Examples

### Example 1: Search Teams chat message

#### Request

The following example queries Teams chat messages in the signed-in user's Teams chat storage that contains the string "test" in any part of the chat message \(the sender name, message body, or any attachments\). The query returns the first 25 results. The search results are ordered by descending **dateTime**.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```HTTP
POST https://graph.microsoft.com/beta/search/query
Content-Type: application/json

{
  "requests": [
    {
      "entityTypes": [
        "chatMessage"
      ],
      "query": {
        "queryString": "test"
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
using Microsoft.Graph.Beta.Search.Query;
using Microsoft.Graph.Beta.Models;

var requestBody = new QueryPostRequestBody
{
	Requests = new List<SearchRequest>
	{
		new SearchRequest
		{
			EntityTypes = new List<EntityType?>
			{
				EntityType.ChatMessage,
			},
			Query = new SearchQuery
			{
				QueryString = "test",
			},
			From = 0,
			Size = 25,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Query.PostAsQueryPostResponseAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphsearch "github.com/microsoftgraph/msgraph-beta-sdk-go/search"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphsearch.NewQueryPostRequestBody()


searchRequest := graphmodels.NewSearchRequest()
entityTypes := []graphmodels.EntityTypeable {
	entityType := graphmodels.CHATMESSAGE_ENTITYTYPE 
	searchRequest.SetEntityType(&entityType)
}
searchRequest.SetEntityTypes(entityTypes)
query := graphmodels.NewSearchQuery()
queryString := "test"
query.SetQueryString(&queryString) 
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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.search.query.QueryPostRequestBody queryPostRequestBody = new com.microsoft.graph.beta.search.query.QueryPostRequestBody();
LinkedList<SearchRequest> requests = new LinkedList<SearchRequest>();
SearchRequest searchRequest = new SearchRequest();
LinkedList<EntityType> entityTypes = new LinkedList<EntityType>();
entityTypes.add(EntityType.ChatMessage);
searchRequest.setEntityTypes(entityTypes);
SearchQuery query = new SearchQuery();
query.setQueryString("test");
searchRequest.setQuery(query);
searchRequest.setFrom(0);
searchRequest.setSize(25);
requests.add(searchRequest);
queryPostRequestBody.setRequests(requests);
var result = graphClient.search().query().post(queryPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const searchResponse = {
  requests: [
    {
      entityTypes: [
        'chatMessage'
      ],
      query: {
        queryString: 'test'
      },
      from: 0,
      size: 25
    }
  ]
};

await client.api('/search/query')
	.version('beta')
	.post(searchResponse);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Search\Query\QueryPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\SearchRequest;
use Microsoft\Graph\Beta\Generated\Models\EntityType;
use Microsoft\Graph\Beta\Generated\Models\SearchQuery;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new QueryPostRequestBody();
$requestsSearchRequest1 = new SearchRequest();
$requestsSearchRequest1->setEntityTypes([new EntityType('chatMessage'),	]);
$requestsSearchRequest1Query = new SearchQuery();
$requestsSearchRequest1Query->setQueryString('test');
$requestsSearchRequest1->setQuery($requestsSearchRequest1Query);
$requestsSearchRequest1->setFrom(0);
$requestsSearchRequest1->setSize(25);
$requestsArray []= $requestsSearchRequest1;
$requestBody->setRequests($requestsArray);


$result = $graphServiceClient->search()->query()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Search

$params = @{
	requests = @(
		@{
			entityTypes = @(
			"chatMessage"
		)
		query = @{
			queryString = "test"
		}
		from = 0
		size = 25
	}
)
}

Invoke-MgBetaQuerySearch -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.search.query.query_post_request_body import QueryPostRequestBody
from msgraph_beta.generated.models.search_request import SearchRequest
from msgraph_beta.generated.models.entity_type import EntityType
from msgraph_beta.generated.models.search_query import SearchQuery
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = QueryPostRequestBody(
	requests = [
		SearchRequest(
			entity_types = [
				EntityType.ChatMessage,
			],
			query = SearchQuery(
				query_string = "test",
			),
			from = 0,
			size = 25,
		),
	],
)

result = await graph_client.search.query.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

The following is an example of the response, which contains one message that matches the search criterion.

```HTTP
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "searchTerms": [
                "test"
            ],
            "hitsContainers": [
                {
                    "hits": [
                        {
                            "hitId": "AAMkAGIwMDA5MmY0LWY5ZTgtNGY5YS04NzczLWNhNjc0ZGIyZDBjYgBGAAAAAADm35sgHbzESapJ8+BjBlhEBwDAYtphe7dsRbDrOT/HAHoKAAAAAAEpAADAYtphe7dsRbDrOT/HAHoKAAFwxQGaAAA=",
                            "rank": 1,
                            "summary": "...Test with the TDF account",
                            "resource": {
                                "@odata.type": "microsoft.graph.chatMessage",
                                "id": "1657782060227",
                                "createdDateTime": "2022-07-14T07:01:01Z",
                                "lastModifiedDateTime": "2022-07-14T07:01:03Z",
                                "subject": "",
                                "importance": "normal",
                                "webLink": "https://outlook.office365.com/owa/?ItemID=AAMkAGIwMDA5MmY0LWY5ZTgtNGY5YS04NzczLWNhNjc0ZGIyZDBjYgBGAAAAAADm35sgHbzESapJ8%2BBjBlhEBwDAYtphe7dsRbDrOT%2FHAHoKAAAAAAEpAADAYtphe7dsRbDrOT%2FHAHoKAAFwxQGaAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
                                "from": {
                                    "emailAddress": {
                                        "name": "Goncalo Torres",
                                        "address": "gtorres@contoso.com"
                                    }
                                },
                                "channelIdentity": {},
                                "etag": "1657782060227",
                                "chatId": "19:bdeff6bfed7f4b159cdf7fdd61aeacaa@thread.v2"
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

### Example 2: Search top results messages

#### Request

The following example uses the search query shown in Example 1, and sorts the results by relevance.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```HTTP
POST https://graph.microsoft.com/v1.0/search/query
Content-Type: application/json

{
  "requests": [
    {
      "entityTypes": [
        "chatMessage"
      ],
      "query": {
        "queryString": "test"
      },
      "from": 0,
      "size": 15,
      "enableTopResults": true
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
				EntityType.ChatMessage,
			},
			Query = new SearchQuery
			{
				QueryString = "test",
			},
			From = 0,
			Size = 15,
			EnableTopResults = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Query.PostAsQueryPostResponseAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
	entityType := graphmodels.CHATMESSAGE_ENTITYTYPE 
	searchRequest.SetEntityType(&entityType)
}
searchRequest.SetEntityTypes(entityTypes)
query := graphmodels.NewSearchQuery()
queryString := "test"
query.SetQueryString(&queryString) 
searchRequest.SetQuery(query)
from := int32(0)
searchRequest.SetFrom(&from) 
size := int32(15)
searchRequest.SetSize(&size) 
enableTopResults := true
searchRequest.SetEnableTopResults(&enableTopResults) 

requests := []graphmodels.SearchRequestable {
	searchRequest,
}
requestBody.SetRequests(requests)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
query, err := graphClient.Search().Query().PostAsQueryPostResponse(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.search.query.QueryPostRequestBody queryPostRequestBody = new com.microsoft.graph.search.query.QueryPostRequestBody();
LinkedList<SearchRequest> requests = new LinkedList<SearchRequest>();
SearchRequest searchRequest = new SearchRequest();
LinkedList<EntityType> entityTypes = new LinkedList<EntityType>();
entityTypes.add(EntityType.ChatMessage);
searchRequest.setEntityTypes(entityTypes);
SearchQuery query = new SearchQuery();
query.setQueryString("test");
searchRequest.setQuery(query);
searchRequest.setFrom(0);
searchRequest.setSize(15);
searchRequest.setEnableTopResults(true);
requests.add(searchRequest);
queryPostRequestBody.setRequests(requests);
var result = graphClient.search().query().post(queryPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const searchResponse = {
  requests: [
    {
      entityTypes: [
        'chatMessage'
      ],
      query: {
        queryString: 'test'
      },
      from: 0,
      size: 15,
      enableTopResults: true
    }
  ]
};

await client.api('/search/query')
	.post(searchResponse);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
$requestsSearchRequest1->setEntityTypes([new EntityType('chatMessage'),	]);
$requestsSearchRequest1Query = new SearchQuery();
$requestsSearchRequest1Query->setQueryString('test');
$requestsSearchRequest1->setQuery($requestsSearchRequest1Query);
$requestsSearchRequest1->setFrom(0);
$requestsSearchRequest1->setSize(15);
$requestsSearchRequest1->setEnableTopResults(true);
$requestsArray []= $requestsSearchRequest1;
$requestBody->setRequests($requestsArray);


$result = $graphServiceClient->search()->query()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	requests = @(
		@{
			entityTypes = @(
			"chatMessage"
		)
		query = @{
			queryString = "test"
		}
		from = 0
		size = 15
		enableTopResults = $true
	}
)
}

Invoke-MgQuerySearch -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
				EntityType.ChatMessage,
			],
			query = SearchQuery(
				query_string = "test",
			),
			from = 0,
			size = 15,
			enable_top_results = True,
		),
	],
)

result = await graph_client.search.query.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```HTTP
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "searchTerms": [
                "test"
            ],
            "hitsContainers": [
                {
                    "hits": [
                        {
                            "hitId": "AAMkAGIwMDA5MmY0LWY5ZTgtNGY5YS04NzczLWNhNjc0ZGIyZDBjYgBGAAAAAADm35sgHbzESapJ8+BjBlhEBwDAYtphe7dsRbDrOT/HAHoKAAAAAAEpAADAYtphe7dsRbDrOT/HAHoKAAFwxQGaAAA=",
                            "rank": 1,
                            "summary": "...Test with the TDF account",
                            "resource": {
                                "@odata.type": "microsoft.graph.chatMessage",
                                "id": "1657782060227",
                                "createdDateTime": "2022-07-14T07:01:01Z",
                                "lastModifiedDateTime": "2022-07-14T07:01:03Z",
                                "subject": "",
                                "importance": "normal",
                                "webLink": "https://outlook.office365.com/owa/?ItemID=AAMkAGIwMDA5MmY0LWY5ZTgtNGY5YS04NzczLWNhNjc0ZGIyZDBjYgBGAAAAAADm35sgHbzESapJ8%2BBjBlhEBwDAYtphe7dsRbDrOT%2FHAHoKAAAAAAEpAADAYtphe7dsRbDrOT%2FHAHoKAAFwxQGaAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
                                "from": {
                                    "emailAddress": {
                                        "name": "Goncalo Torres",
                                        "address": "gtorres@contoso.com"
                                    }
                                },
                                "channelIdentity": {},
                                "etag": "1657782060227",
                                "chatId": "19:bdeff6bfed7f4b159cdf7fdd61aeacaa@thread.v2"
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

### Example 3: Search Teams Message with KQL

#### Supported scope terms

You can use the following scope terms in your [Keyword Query Language \(KQL\)](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) query.

| Scope Terms | Description | Example |
| :--- | :--- | :--- |
| from | Search only for messages sent by scoped person. | from:bob |
| hasAttachment | Search only for messages that contain or don't contain attachments. | hasAttachment:true |
| IsRead | Search only for messages that were or weren't read. | IsRead:true |
| IsMentioned | Search only for messages that did or didn't mention you. | IsMentioned:true |
| mentions | Search only for messages that mentioned somebody. | mentions:497b7a2a9e1a48d780e82965d2fc3a81 \(This is user ID without '-'\) |
| sent | Search only for messages sent to the scoped date range. | sent > 2022-07-14 |
| to | Search only for messages sent to the scoped person, partially supported for the one-on-one message. | to:bob |

#### Request

The following example shows how to search a message that contains Contoso that Bob sent to Alice after 2022-07-14.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```HTTP
POST https://graph.microsoft.com/v1.0/search/query
Content-Type: application/json

{
  "requests": [
    {
      "entityTypes": [
        "chatMessage"
      ],
      "query": {
        "queryString": "contoso from:bob to:alice sent>2022-07-14"
      },
      "from": 0,
      "size": 15,
      "enableTopResults": true
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
				EntityType.ChatMessage,
			},
			Query = new SearchQuery
			{
				QueryString = "contoso from:bob to:alice sent>2022-07-14",
			},
			From = 0,
			Size = 15,
			EnableTopResults = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Search.Query.PostAsQueryPostResponseAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
	entityType := graphmodels.CHATMESSAGE_ENTITYTYPE 
	searchRequest.SetEntityType(&entityType)
}
searchRequest.SetEntityTypes(entityTypes)
query := graphmodels.NewSearchQuery()
queryString := "contoso from:bob to:alice sent>2022-07-14"
query.SetQueryString(&queryString) 
searchRequest.SetQuery(query)
from := int32(0)
searchRequest.SetFrom(&from) 
size := int32(15)
searchRequest.SetSize(&size) 
enableTopResults := true
searchRequest.SetEnableTopResults(&enableTopResults) 

requests := []graphmodels.SearchRequestable {
	searchRequest,
}
requestBody.SetRequests(requests)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
query, err := graphClient.Search().Query().PostAsQueryPostResponse(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.search.query.QueryPostRequestBody queryPostRequestBody = new com.microsoft.graph.search.query.QueryPostRequestBody();
LinkedList<SearchRequest> requests = new LinkedList<SearchRequest>();
SearchRequest searchRequest = new SearchRequest();
LinkedList<EntityType> entityTypes = new LinkedList<EntityType>();
entityTypes.add(EntityType.ChatMessage);
searchRequest.setEntityTypes(entityTypes);
SearchQuery query = new SearchQuery();
query.setQueryString("contoso from:bob to:alice sent>2022-07-14");
searchRequest.setQuery(query);
searchRequest.setFrom(0);
searchRequest.setSize(15);
searchRequest.setEnableTopResults(true);
requests.add(searchRequest);
queryPostRequestBody.setRequests(requests);
var result = graphClient.search().query().post(queryPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const searchResponse = {
  requests: [
    {
      entityTypes: [
        'chatMessage'
      ],
      query: {
        queryString: 'contoso from:bob to:alice sent>2022-07-14'
      },
      from: 0,
      size: 15,
      enableTopResults: true
    }
  ]
};

await client.api('/search/query')
	.post(searchResponse);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
$requestsSearchRequest1->setEntityTypes([new EntityType('chatMessage'),	]);
$requestsSearchRequest1Query = new SearchQuery();
$requestsSearchRequest1Query->setQueryString('contoso from:bob to:alice sent>2022-07-14');
$requestsSearchRequest1->setQuery($requestsSearchRequest1Query);
$requestsSearchRequest1->setFrom(0);
$requestsSearchRequest1->setSize(15);
$requestsSearchRequest1->setEnableTopResults(true);
$requestsArray []= $requestsSearchRequest1;
$requestBody->setRequests($requestsArray);


$result = $graphServiceClient->search()->query()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Search

$params = @{
	requests = @(
		@{
			entityTypes = @(
			"chatMessage"
		)
		query = @{
			queryString = "contoso from:bob to:alice sent>2022-07-14"
		}
		from = 0
		size = 15
		enableTopResults = $true
	}
)
}

Invoke-MgQuerySearch -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
				EntityType.ChatMessage,
			],
			query = SearchQuery(
				query_string = "contoso from:bob to:alice sent>2022-07-14",
			),
			from = 0,
			size = 15,
			enable_top_results = True,
		),
	],
)

result = await graph_client.search.query.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```HTTP
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "searchTerms": [
                "test"
            ],
            "hitsContainers": [
                {
                    "hits": [
                        {
                            "hitId": "AAMkAGIwMDA5MmY0LWY5ZTgtNGY5YS04NzczLWNhNjc0ZGIyZDBjYgBGAAAAAADm35sgHbzESapJ8+BjBlhEBwDAYtphe7dsRbDrOT/HAHoKAAAAAAEpAADAYtphe7dsRbDrOT/HAHoKAAFwxQGaAAA=",
                            "rank": 1,
                            "summary": "...Contoso Test with the TDF account",
                            "resource": {
                                "@odata.type": "microsoft.graph.chatMessage",
                                "id": "1657782060227",
                                "createdDateTime": "2022-07-15T07:01:01Z",
                                "lastModifiedDateTime": "2022-07-15T07:01:03Z",
                                "subject": "",
                                "importance": "normal",
                                "webLink": "https://outlook.office365.com/owa/?ItemID=AAMkAGIwMDA5MmY0LWY5ZTgtNGY5YS04NzczLWNhNjc0ZGIyZDBjYgBGAAAAAADm35sgHbzESapJ8%2BBjBlhEBwDAYtphe7dsRbDrOT%2FHAHoKAAAAAAEpAADAYtphe7dsRbDrOT%2FHAHoKAAFwxQGaAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
                                "from": {
                                    "emailAddress": {
                                        "name": "bob",
                                        "address": "bob@contoso.com"
                                    }
                                },
                                "channelIdentity": {},
                                "etag": "1657782060228",
                                "chatId": "19:bdeff6bee3df4b159bad3fdd61aeacaa@thread.v2"
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

## Known limitations

- You can access only the signed-in user's Teams message or the message the user is included in.
- The search Teams API doesn't return all properties defined in [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage). You can use the [Teams API](https://learn.microsoft.com/en-us/graph/api/chatmessage-get) to retrieve more details about any single message.
- For Teams messages, the **total** property of the [searchHitsContainer](https://learn.microsoft.com/en-us/graph/api/resources/searchhitscontainer) type contains the number of results on the page, not the total number of matching results.
- Sorting results isn't supported for messages.
- You can't use this API with other entity types at this time.

## JSON representation

Here's a JSON representation of all retrievable properties currently available for [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage) search.

```json
{
  "channelIdentity": {"@odata.type": "microsoft.graph.channelIdentity"},
  "chatId": "string",
  "createdDateTime": "string (timestamp)",
  "etag": "string",
  "from": {"@odata.type": "microsoft.graph.chatMessageFromIdentitySet"},
  "id": "string (identifier)",
  "importance": "string",
  "lastModifiedDateTime": "string (timestamp)",
  "subject": "string",
  "webUrl": "string"
}
```

## Next steps

- [Use the Microsoft Search API to query data](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview)
