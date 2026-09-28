<!-- Source: https://learn.microsoft.com/en-us/graph/api/sitepage-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-19 -->

# Get SitePage

Namespace: microsoft.graph

Returns the metadata for a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) in the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Read.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Read.All | Sites.ReadWrite.All |

## HTTP request

```http
GET /sites/{site-id}/pages/{page-id}/microsoft.graph.sitePage
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

You can use the `$expand=canvasLayout` query string parameter to include the content of an item when retrieving the metadata of an item if the item has a **=canvasLayout** relationship.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| Accept | application/json;odata.metadata=none. Optional. Removes all OData metadata from the response. We recommend including this header when the response will be used in another request. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200` and a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get a page in the site pages list of a site

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages["{baseSitePage-id}"].GraphSitePage.GetAsync();
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
graphSitePage, err := graphClient.Sites().BySiteId("site-id").Pages().ByBaseSitePageId("baseSitePage-id").GraphSitePage().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SitePage result = graphClient.sites().bySiteId("{site-id}").pages().byBaseSitePageId("{baseSitePage-id}").graphSitePage().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sitePage = await client.api('/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->byBaseSitePageId('baseSitePage-id')->graphSitePage()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

Get-MgSitePageAsSitePage -SiteId $siteId -BaseSitePageId $baseSitePageId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.sites.by_site_id('site-id').pages.by_base_site_page_id('baseSitePage-id').graph_site_page.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.type": "microsoft.graph.sitePage",
  "description": "Here's the page description",
  "id": "65e59907-59d5-44ff-a038-7c0bf3098c01",
  "name": "Home.aspx",
  "webUrl": "https://contoso.sharepoint.com/SitePages/Home.aspx",
  "title": "Organization Home",
  "thumbnailWebUrl": "https://cdn.hubblecontent.osi.office.net/m365content/publish/00210d24-bba0-42e6-9a31-1d452a95dd75/thumbnails/large.jpg?file=163352059.jpg",
  "promotionKind": "page",
  "pageLayout": "home",
  "showComments": true,
  "showRecommendedPages": false,
  "createdBy": {
    "user": {
        "displayName": "Rahul Mittal",
        "email": "rahmit@contoso.com"
    }
  },
  "lastModifiedBy": {
    "user": {
        "displayName": "Rahul Mittal",
        "email": "rahmit@contoso.com"
    }
  },
  "publishingState": {
    "level": "published",
    "versionId": "1.0"
  },
  "reactions": {
    "commentCount": 1
  }
}
```

### Example 2: Get a page using select and expand

#### Request

With `$select` and `$expand` statements, you can retrieve sitePage metadata and page content in a single request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage?$select=id,name
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages["{baseSitePage-id}"].GraphSitePage.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","name" };
});
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

requestParameters := &graphsites.ItemPagesItemGraph.sitePageRequestBuilderGetQueryParameters{
	Select: [] string {"id","name"},
}
configuration := &graphsites.ItemPagesItemGraph.sitePageRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphSitePage, err := graphClient.Sites().BySiteId("site-id").Pages().ByBaseSitePageId("baseSitePage-id").GraphSitePage().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SitePage result = graphClient.sites().bySiteId("{site-id}").pages().byBaseSitePageId("{baseSitePage-id}").graphSitePage().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "name"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sitePage = await client.api('/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage')
	.select('id,name')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Sites\Item\Pages\Item\Graph\SitePage\SitePageRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GraphSitePageRequestBuilderGetRequestConfiguration();
$queryParameters = GraphSitePageRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","name"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->byBaseSitePageId('baseSitePage-id')->graphSitePage()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

Get-MgSitePageAsSitePage -SiteId $siteId -BaseSitePageId $baseSitePageId -Property "id,name" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.sites.item.pages.item.graph.site_page.site_page_request_builder import SitePageRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = SitePageRequestBuilder.SitePageRequestBuilderGetQueryParameters(
		select = ["id","name"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.sites.by_site_id('site-id').pages.by_base_site_page_id('baseSitePage-id').graph_site_page.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.etag": "\"{F45354CB-D634-45DF-8B88-2B4E96A1DC45},8\"",
    "id": "f45354cb-d634-45df-8b88-2b4e96a1dc45",
    "name": "Electronic Convertible.aspx"
}
```

### Example 3: Get a page with page content

#### Request

You can expand references in your URL with the *$expand* query parameter. To access the page with page content, append the `?$expand=canvasLayout` query string.

```http
GET /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202/microsoft.graph.sitePage?$expand=canvasLayout
```

#### Response

The following example shows the response.

```json
{
  "description": "Reiciendis placeat dolores.",
  "eTag": "\"{F45354CB-D634-45DF-8B88-2B4E96A1DC45},8\"",
  "id": "f45354cb-d634-45df-8b88-2b4e96a1dc45",
  "lastModifiedDateTime": "2023-04-16T10:01:41Z",
  "name": "autotest Electronic Convertible.aspx",
  "webUrl": "https://contoso.sharepoint.com/SitePages/autotest Electronic Convertible.aspx",
  "title": "autotest Electronic Convertible",
  "pageLayout": "article",
  "thumbnailWebUrl": "https://media.akamai.odsp.cdn.office.net/sitepagethumbnail.png",
  "promotionKind": "page",
  "showComments": false,
  "showRecommendedPages": true,
  "createdBy": {
    "user": {
        "displayName": "Rahul Mittal",
        "email": "rahmit@contoso.com"
    }
  },
  "lastModifiedBy": {
    "user": {
        "displayName": "Rahul Mittal",
        "email": "rahmit@contoso.com"
    }
  },
  "parentReference": {
    "listId": "468fc883-e278-4773-ba09-91351a1e42ed",
    "siteId": "45bb2a3b-0a4e-46f4-8c68-749c3fea75d3"
  },
  "contentType": {
    "id": "0x0101009D1CB255DA76424F860D91F20E6C4118009E6554A5E299E84FB2E07731DD6C6D4A",
    "name": "Site Page"
  },
  "publishingState": {
    "level": "draft",
    "versionId": "0.4"
  },
  "reactions": {},
  "canvasLayout": {
    "horizontalSections": [
      {
        "layout": "threeColumns",
        "id": "1",
        "emphasis": "neutral",
        "columns": [
          {
            "id": "1",
            "width": 4,
            "webparts": [
              {
                "@odata.type": "#oneDrive.textWebPart",
                "id": "f6d0ef70-c977-45e4-ae4b-4676a30d5aab",
                "innerHtml": "<h1>sample content</h1>"
              }
            ]
          },
          {
            "id": "2",
            "width": 4,
            "webparts": [
              {
                "@odata.type": "#oneDrive.textWebPart",
                "id": "99f59f91-c853-433e-9e75-ad7a32e46106",
                "innerHtml": "<h1>sample content</h1>"
              }
            ]
          },
          {
            "id": "3",
            "width": 4,
            "webparts": [
              {
                "@odata.type": "#oneDrive.textWebPart",
                "id": "48998492-9633-48b8-a7e9-d293533b4fa6",
                "innerHtml": "<h1>sample content</h1>"
              }
            ]
          }
        ]
      }
    ]
  }
}
```
