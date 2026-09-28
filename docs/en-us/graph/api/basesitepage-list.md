<!-- Source: https://learn.microsoft.com/en-us/graph/api/basesitepage-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List baseSitePages

Namespace: microsoft.graph

Get the collection of [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) objects from the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). All pages in the site are returned \(with pagination\). Sort alphabetically by **name** in ascending order.

> **Note:** The [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) specified is a parent type and doesn't have any instance. As a result, the returned data only consists of available subtypes that are provided as a list.

**The following table lists the available subtypes.**

| Entity name | Description |
| :--- | :--- |
| [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) | Represents a regular page. |

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

```msgraph
GET /sites/{site-id}/pages
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

If successful, this method returns a `200 OK` response code and a collection of [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) objects in the response body.

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
GET /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages.GetAsync();
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
pages, err := graphClient.Sites().BySiteId("site-id").Pages().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BaseSitePageCollectionResponse result = graphClient.sites().bySiteId("{site-id}").pages().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let pages = await client.api('/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

Get-MgSitePage -SiteId $siteId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.sites.by_site_id('site-id').pages.get()
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
      "@odata.type": "#microsoft.graph.sitePage",
      "@odata.etag": "\"{5FA48F95-2FDF-40E8-A28C-6D0D8345BCD2},8\"",
      "description": "Placeat porro perspiciatis maxime esse nobis illo.Voluptate vitae maxime totam consectetur fugit sit quos.Saepe ea veniam voluptate tempore quod deleniti necessitatibus repellat.",
      "eTag": "\"{5FA48F95-2FDF-40E8-A28C-6D0D8345BCD2},8\"",
      "id": "5fa48f95-2fdf-40e8-a28c-6d0d8345bcd2",
      "lastModifiedDateTime": "2023-04-16T08:37:51Z",
      "name": "Account holistic.aspx",
      "webUrl": "https://contoso.sharepoint.com/SitePages/Account holistic.aspx",
      "title": "CSS Global Lithuanian meter",
      "pageLayout": "article",
      "thumbnailWebUrl": "https://media.akamai.odsp.cdn.office.net/a830edad9050849vanaukyisx52.spgrid.com/_layouts/15/images/sitepagethumbnail.png",
      "promotionKind": "page",
      "showComments": false,
      "showRecommendedPages": false,
      "contentType": {
        "id": "0x0101009D1CB255DA76424F860D91F20E6C4118009E6554A5E299E84FB2E07731DD6C6D4A",
        "name": "Site Page"
      },
      "createdBy": {
        "user": {
          "displayName": "admin_contoso",
          "email": "admin@contoso.onmicrosoft.com"
        }
      },
      "lastModifiedBy": {
        "user": {
          "displayName": "admin_contoso",
          "email": "admin@contoso.onmicrosoft.com"
        }
      },
      "parentReference": {
        "siteId": "45bb2a3b-0a4e-46f4-8c68-749c3fea75d3"
      },
      "publishingState": {
        "level": "draft",
        "versionId": "0.4"
      },
      "reactions": {}
    },
    {
      "@odata.type": "#microsoft.graph.sitePage",
      "@odata.etag": "\"{DA0F67BE-977E-4D09-88AC-506A1002E678},5\"",
      "eTag": "\"{DA0F67BE-977E-4D09-88AC-506A1002E678},5\"",
      "id": "da0f67be-977e-4d09-88ac-506a1002e678",
      "lastModifiedDateTime": "2023-04-16T06:39:30Z",
      "name": "Analyst Fresh.aspx",
      "webUrl": "https://contoso.sharepoint.com/SitePages/Analyst Fresh.aspx",
      "title": "Lesotho Account Metal Analyst du",
      "pageLayout": "article",
      "thumbnailWebUrl": "https://media.akamai.odsp.cdn.office.net/a830edad9050849vanaukyisx52.spgrid.com/_layouts/15/images/sitepagethumbnail.png",
      "promotionKind": "page",
      "showComments": false,
      "showRecommendedPages": false,
      "contentType": {
        "id": "0x0101009D1CB255DA76424F860D91F20E6C4118009E6554A5E299E84FB2E07731DD6C6D4A",
        "name": "Site Page"
      },
      "createdBy": {
        "user": {
          "displayName": "admin_contoso",
          "email": "admin@contoso.onmicrosoft.com"
        }
      },
      "lastModifiedBy": {
        "user": {
          "displayName": "admin_contoso",
          "email": "admin@contoso.onmicrosoft.com"
        }
      },
      "parentReference": {
        "siteId": "45bb2a3b-0a4e-46f4-8c68-749c3fea75d3"
      },
      "publishingState": {
        "level": "draft",
        "versionId": "0.1"
      },
      "reactions": {},
      "titleArea": {
        "enableGradientEffect": false,
        "imageWebUrl": "https://loremflickr.com/640/480",
        "layout": "plain",
        "showAuthor": false,
        "showPublishedDate": false,
        "showTextBlockAboveTitle": false,
        "textAboveTitle": "generating ADP",
        "textAlignment": "center",
        "title": "strategic underneath protocol Buckinghamshire forecast",
        "authors@odata.type": "#Collection(String)",
        "authors": [],
        "authorByline@odata.type": "#Collection(String)",
        "authorByline": [],
        "imageSourceType": 4,
        "serverProcessedContent": {
          "htmlStrings": [],
          "searchablePlainTexts": [],
          "links": [],
          "imageSources": []
        }
      }
    }
  ]
}
```
