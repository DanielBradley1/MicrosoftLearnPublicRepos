<!-- Source: https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-communities?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-22 -->

# List communities

Namespace: microsoft.graph

Get a list of the Viva Engage [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Community.Read.All | Community.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Community.Read.All | Community.ReadWrite.All |

## HTTP request

```http
GET /employeeExperience/communities
```

## Optional query parameters

This method supports the `$top`, `$select`, and `$expand` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. It also supports the `$orderby` parameter for the **displayName** property.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [community](https://learn.microsoft.com/en-us/graph/api/resources/community?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get a list of communities

The following example shows how to get a list of Viva Engage communities.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/employeeExperience/communities
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Communities.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
communities, err := graphClient.EmployeeExperience().Communities().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CommunityCollectionResponse result = graphClient.employeeExperience().communities().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let communities = await client.api('/employeeExperience/communities')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->employeeExperience()->communities()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.employee_experience.communities.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#employeeExperience/communities",
    "value": [
        {
            "id": "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ",
            "displayName": "All Company",
            "description": "This is the default group for everyone in the network",
            "privacy": "public",
            "groupId": "195d9ecd-f80e-4bab-af95-176eba253dff"
        },
        {
            "id": "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzNDY2Mzc2OTYifQ",
            "displayName": "TestCommunity5",
            "description": "Test community created via API",
            "privacy": "public",
            "groupId": "0bed8b86-5026-4a93-ac7d-56750cc099aa"
        }
    ]
}
```

### Example 2: Get a list of communities with pagination

The following example shows how to get a list of Viva Engage communities using the `$top` query parameter to set the page size of results.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/employeeExperience/communities?$top=2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Communities.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Top = 2;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphemployeeexperience "github.com/microsoftgraph/msgraph-sdk-go/employeeexperience"
	  //other-imports
)


requestTop := int32(2)

requestParameters := &graphemployeeexperience.EmployeeExperienceCommunitiesRequestBuilderGetQueryParameters{
	Top: &requestTop,
}
configuration := &graphemployeeexperience.EmployeeExperienceCommunitiesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
communities, err := graphClient.EmployeeExperience().Communities().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CommunityCollectionResponse result = graphClient.employeeExperience().communities().get(requestConfiguration -> {
	requestConfiguration.queryParameters.top = 2;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let communities = await client.api('/employeeExperience/communities')
	.top(2)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\EmployeeExperience\Communities\CommunitiesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new CommunitiesRequestBuilderGetRequestConfiguration();
$queryParameters = CommunitiesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->top = 2;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->employeeExperience()->communities()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.employee_experience.communities.communities_request_builder import CommunitiesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = CommunitiesRequestBuilder.CommunitiesRequestBuilderGetQueryParameters(
		top = 2,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.employee_experience.communities.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

If the number of communities exceeds 20 or you use the `$top` query parameter to set the page size of results, multiple query requests might be necessary to retrieve all results. In this scenario, the API continues to return a reference to the next page of results in the **@odata.nextLink** property with each response until no more pages remain to be retrieved.

The following example shows the response that includes the **@odata.nextLink** property.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#employeeExperience/communities",
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/employeeExperience/communities?$skiptoken=UVWlYzI7VjE7MTE2NDUzNDU3OTIwOzIwO0RlbW8tdGVzdC01OztEaXNwbGF5TmFtZTtmYWXYYTs",
    "value": [
        {
            "id": "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ",
            "displayName": "All Company",
            "description": "This is the default group for everyone in the network",
            "privacy": "public",
            "groupId": "195d9ecd-f80e-4bab-af95-176eba253dff"
        },
        {
            "id": "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzNDY2Mzc2OTYifQ",
            "displayName": "TestCommunity5",
            "description": "Test community created via API",
            "privacy": "public",
            "groupId": "0bed8b86-5026-4a93-ac7d-56750cc099aa"
        }
    ]
}
```
