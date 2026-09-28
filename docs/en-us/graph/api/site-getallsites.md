<!-- Source: https://learn.microsoft.com/en-us/graph/api/site-getallsites?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-15 -->

# sites: getAllSites

List [sites](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) across geographies in an organization. This API can also be used to enumerate all sites in a non-multi-geo tenant.

For more information, see [Best practices for discovering files and detecting changes at scale](https://learn.microsoft.com/en-us/onedrive/developer/rest-api/concepts/scan-guidance?view=odsp-graph-online&preserve-view=true).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Read.All | Sites.ReadWrite.All |

## HTTP request

```http
GET /sites/getAllSites
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Examples

### Example 1: Initial request

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/sites/getAllSites
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites.GetAllSites.GetAsGetAllSitesGetResponseAsync();
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
getAllSites, err := graphClient.Sites().GetAllSites().GetAsGetAllSitesGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.sites().getAllSites().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllSites = await client.api('/sites/getAllSites')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->sites()->getAllSites()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

Get-MgAllSite
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.sites.get_all_sites.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "id": "contoso-apc.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c",
      "name": "Root Site",
      "isPersonalSite": false,
      "root": { },
      "siteCollection": {
        "hostName": "contoso-apc.sharepoint.com",
        "dataLocationCode": "APC",
        "root": { }
      },
      "webUrl": "https://contoso-apc.sharepoint.com"
    },
    {
      "id": "contoso-apc.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f",
      "name": "Site A",
      "isPersonalSite": false,
      "root": { },
      "siteCollection": {
        "hostName": "contoso-apc.sharepoint.com"
      },
      "webUrl": "https://contoso-apc.sharepoint.com/sites/siteA"
    },
    {
      "id": "contoso-apc.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022",
      "name": "Site B",
      "isPersonalSite": false,
      "root": { },
      "siteCollection": {
        "hostName": "contoso-apc.sharepoint.com"
      },
      "webUrl": "https://contoso-apc.sharepoint.com/sites/siteB"
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/sites/oneDrive.getAllSites?$skiptoken=U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ"
}
```

This response includes the first page of enumerated sites, and the @odata.nextLink property indicates that there are more items available in the current set of items. Your app should continue to request the URL value of @odata.nextLink until all pages of items are retrieved.

### Example 2: Subsequent request

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET /sites/getAllSites?$skiptoken=U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
// Note: The URI string parameter used with WithUrl() can be retrieved using the OdataNextLink or OdataDeltaLink property from a response object
var result = await graphClient.Sites.GetAllSites.WithUrl("https://graph.microsoft.com/v1.0/sites/getAllSites?$skiptoken=U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ").GetAsGetAllSitesGetResponseAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsites "github.com/microsoftgraph/msgraph-sdk-go/sites"
	  //other-imports
)


requestSkiptoken := "U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ"

requestParameters := &graphsites.SitesGetAllSitesRequestBuilderGetQueryParameters{
	Skiptoken: &requestSkiptoken,
}
configuration := &graphsites.SitesGetAllSitesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getAllSites, err := graphClient.Sites().GetAllSites().GetAsGetAllSitesGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.sites().getAllSites().get(requestConfiguration -> {
	requestConfiguration.queryParameters.skiptoken = "U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllSites = await client.api('/sites/getAllSites')
	.skiptoken('U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Sites\GetAllSites\GetAllSitesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetAllSitesRequestBuilderGetRequestConfiguration();
$queryParameters = GetAllSitesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->skiptoken = "U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->sites()->getAllSites()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

Get-MgAllSite -Skiptoken "U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.sites.get_all_sites.get_all_sites_request_builder import GetAllSitesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetAllSitesRequestBuilder.GetAllSitesRequestBuilderGetQueryParameters(
		skiptoken = "U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.sites.get_all_sites.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "id": "contoso-nam.sharepoint.com,bf6fb551-d508-4946-a439-b2a6154fc1d9,65a04b8b-1f44-442b-a1fc-9e5852fb946c",
      "name": "Root Site",
      "isPersonalSite": false,
      "root": { },
      "siteCollection": {
        "hostName": "contoso-nam.sharepoint.com",
        "dataLocationCode": "NAM",
        "root": { }
      },
      "webUrl": "https://contoso-nam.sharepoint.com"
    },
    {
      "id": "contoso-nam.sharepoint.com,d9ecf079-9b13-4376-ac5d-f242dda55626,746dbcc1-fa2b-4120-b657-2670bae5bb6f",
      "name": "Site A",
      "isPersonalSite": false,
      "root": { },
      "siteCollection": {
        "hostName": "contoso-nam.sharepoint.com"
      },
      "webUrl": "https://contoso-nam.sharepoint.com/sites/siteA"
    },
    {
      "id": "contoso-nam.sharepoint.com,fd1a778f-263e-4c43-acdf-d5c2519d80eb,c06016db-dfec-4f79-83a1-09c6dbfd7022",
      "name": "Site B",
      "isPersonalSite": false,
      "root": { },
      "siteCollection": {
        "hostName": "contoso-nam.sharepoint.com"
      },
      "webUrl": "https://contoso-nam.sharepoint.com/sites/siteB"
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/sites/oneDrive.getAllSites?$skiptoken=U1BHZW9EYXRhTG9jYXRpb25Db2RlYU5BTQ"
}
```
