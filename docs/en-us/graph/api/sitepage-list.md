<!-- Source: https://learn.microsoft.com/en-us/graph/api/sitepage-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List SitePage

Namespace: microsoft.graph

Get the collection of [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) objects from the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a site [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). All pages in the site are returned \(with pagination\). Sort alphabetically by `name` in ascending order.

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
GET /sites/{site-id}/pages/microsoft.graph.sitePage
```

## Optional query parameters

This method supports the `$count`, `$expand`, `$filter`, `$orderBy`, `$select`, and `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200` and a list of [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) object in the response body.

## Example

### Request

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
GET /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/microsoft.graph.sitePage
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages.GraphSitePage.GetAsync();
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
graphSitePage, err := graphClient.Sites().BySiteId("site-id").Pages().GraphSitePage().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SitePageCollectionResponse result = graphClient.sites().bySiteId("{site-id}").pages().graphSitePage().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sitePage = await client.api('/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/microsoft.graph.sitePage')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->graphSitePage()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

Get-MgSitePageAsSitePage -SiteId $siteId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.sites.by_site_id('site-id').pages.graph_site_page.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "value": [
        {
            "id": "08f48aa6-02e3-407c-bbcb-ff61cec653fa",
            "name": "sample.aspx",
            "webUrl": "https://contoso.sharepoint.com/SitePages/sample.aspx",
            "title": "sample",
            "pageLayout": "article",
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
                "level": "checkout",
                "versionId": "1.1",
                "checkedOutBy": {
                    "user": {
                        "displayName": "Rahul Mittal",
                        "email": "rahmit@contoso.com"
                    }
                }
            },
            "reactions": {
                "commentCount": 4,
                "likeCount": 2
            },
            "titleArea": {
                "enableGradientEffect": true,
                "imageWebUrl": "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
                "layout": "imageAndTitle",
                "showAuthor": false,
                "showPublishedDate": false,
                "showTextBlockAboveTitle": false,
                "textAboveTitle": "",
                "textAlignment": "left",
                "imageSourceType": 2,
                "title": "sample"
            }
        },
        {
            "id": "7d87eee1-7c77-46b5-b2c4-ad6e4e432a8e",
            "name": "Home.aspx",
            "webUrl": "https://contoso.sharepoint.com/SitePages/Home.aspx",
            "title": "Home",
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
                "level": "checkout",
                "versionId": "1.1",
                "checkedOutBy": {
                    "user": {
                        "displayName": "Rahul Mittal",
                        "email": "rahmit@contoso.com"
                    }
                }
            },
            "reactions": {
                "commentCount": 1
            },
            "titleArea": {
                "enableGradientEffect": true,
                "imageWebUrl": "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
                "layout": "imageAndTitle",
                "showAuthor": true,
                "showPublishedDate": false,
                "showTextBlockAboveTitle": false,
                "textAboveTitle": "Text Above Title",
                "textAlignment": "left",
                "imageSourceType": 2,
                "title": "Home",
                "hasTitleBeenCommitted": true
            }
        }
    ]
}
```
