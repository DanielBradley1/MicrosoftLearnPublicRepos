<!-- Source: https://learn.microsoft.com/en-us/graph/paging -->
<!-- Sitemap-Last-Modified: 2025-04-03 -->

# Paging Microsoft Graph data in your app

Paging involves requesting or receiving data in batches. It's a performance technique that's crucial for efficiently handling large datasets and that helps improve the performance of your app and the response time of Microsoft Graph.

Some GET queries against Microsoft Graph return multiple pages of data either due to server-side paging or client-side paging. In this article, we explore how paging works for Microsoft Graph and how you can use it to optimize your applications.

Note

If you're looking for information about paging in Microsoft Graph SDKs, see [Page through a collection using the Microsoft Graph SDKs](https://learn.microsoft.com/en-us/graph/sdks/paging).

Learn more about pagination through the following video.

<iframe src="https://www.youtube-nocookie.com/embed/DB_NoC9a1JI" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## How paging works

### Server-side paging

In server-side paging, the Microsoft Graph service returns a default number of results in a single page without the client specifying the number of results to return using `$top`. For example, the `GET /users` endpoint returns a default of 100 results in a single page.

When there's at least one more page of data available, Microsoft Graph returns an `@odata.nextLink` property in the response that contains a URL to the next page of results. You use this URL to query for the next page of results. Microsoft Graph will continue to return a reference to the next page of results in the `@odata.nextLink` property with each response until there are no more pages of results to retrieve. To read all results, you must continue to call Microsoft Graph with the `@odata.nextLink` property returned in each response until the `@odata.nextLink` property is no longer returned.

### Client-side paging

In client-side paging, a client app specifies the number of results it wants Microsoft Graph to return in a single page by using the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top), [$skip](https://learn.microsoft.com/en-us/graph/query-parameters#skip), or [$skipToken](https://learn.microsoft.com/en-us/graph/query-parameters#skiptoken) query parameters. Support for client-side paging, including the number of results that the client can request for in a single page depends on the API and the query being performed. For example, the `/users` endpoint supports `$top` but not `$skip`.

The rest of this article describes how to implement client-side paging.

## Implementing client-side paging

The following example shows client-side paging where the client uses the `$top` query parameter to request up to five users in the tenant.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users?$top=5
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Top = 5;
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestTop := int32(5)

requestParameters := &graphusers.UsersRequestBuilderGetQueryParameters{
	Top: &requestTop,
}
configuration := &graphusers.UsersRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
users, err := graphClient.Users().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserCollectionResponse result = graphClient.users().get(requestConfiguration -> {
	requestConfiguration.queryParameters.top = 5;
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let users = await client.api('/users')
	.top(5)
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\UsersRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new UsersRequestBuilderGetRequestConfiguration();
$queryParameters = UsersRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->top = 5;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUser -Top 5 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.users_request_builder import UsersRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = UsersRequestBuilder.UsersRequestBuilderGetQueryParameters(
		top = 5,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

If the result contains more results, Microsoft Graph returns an `@odata.nextLink` property similar to the following along with the first page of results:

```json
"@odata.nextLink": "https://graph.microsoft.com/v1.0/users?$top=5&$skiptoken=RFNwdAIAAQAAAD8...AAAAAAAA"
```

Use the entire URL in the `@odata.nextLink` property in a GET request to retrieve the next page of results. Depending on the API that the query is being performed against, the `@odata.nextLink` URL value contains either a `$skiptoken` or a `$skip` query parameter. Any other query parameters that were present in the original request are also encoded in this URL. Don't try to extract the `$skiptoken` or `$skip` value and use it in a different request.

Paging behavior varies across different Microsoft Graph APIs. Consider the following points when working with paged data:

- A page of results might contain zero or more results.
- Different APIs might have different default and maximum page sizes.
- Different APIs might behave differently if you specify a page size \(via the `$top` query parameter\) that exceeds the maximum page size for that API. The requested page size might be ignored, it might default to the maximum page size for that API, or Microsoft Graph might return an error.
- Not all resources or relationships support paging. For example, queries against [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole) don't support paging. This includes reading role objects themselves and role members.
- When paging against [directory resources](https://learn.microsoft.com/en-us/graph/api/resources/directoryObject), any custom request headers \(headers that aren't Authorization or Content-Type headers\) such as the **ConsistencyLevel** header aren't included by default in subsequent page requests. If those headers need to be sent on subsequent requests, you must set them explicitly.
- When using the `$count=true` query string when querying against [directory resources](https://learn.microsoft.com/en-us/graph/api/resources/directoryObject), the `@odata.count` property is returned only in the first page of the paged result set.

## Error handling

### Avoiding DirectoryPageTokenNotFoundException errors

When paging through large sets of data, you might encounter the `DirectoryPageTokenNotFoundException` error, which prevents the client app from successfully retrieving subsequent pages. This error occurs when the client app uses a token from a retry operation to request the next page of results.

To avoid this error, don't use tokens from retry operations for subsequent page requests as these tokens aren't guaranteed to be valid for future requests. Instead, persist the token from the last successful response and use it for the next page request. Therefore, the `@odata.nextLink` value used for the retry should be used for the subsequent page request.

#### Example scenario

1. Retrieve Page 1 and receive a token "Token1".
2. Use "Token1" to request Page 2.
3. If you encounter a network error, retry the request.
4. During the retry, you receive a new token "RetryToken".
5. Do not use "RetryToken" to request Page 3, as it might cause the `DirectoryPageTokenNotFoundException` error.
6. Instead, use "Token1" \(the token from the last successful non-retry response\) to request Page 3.

## Related content

- Microsoft Graph SDKs provide classes and methods to help with paging. For details, see [Page through a collection using the Microsoft Graph SDKs](https://learn.microsoft.com/en-us/graph/sdks/paging).
