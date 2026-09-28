<!-- Source: https://learn.microsoft.com/en-us/graph/api/basesitepage-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get baseSitePage

Namespace: microsoft.graph

Get the metadata for a [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) in the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0).

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
GET /sites/{site-id}/pages/{page-id}
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

If successful, this method returns a `200` and a [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) object in the response body.

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
GET /sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages["{baseSitePage-id}"].GetAsync();
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
pages, err := graphClient.Sites().BySiteId("site-id").Pages().ByBaseSitePageId("baseSitePage-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BaseSitePage result = graphClient.sites().bySiteId("{site-id}").pages().byBaseSitePageId("{baseSitePage-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let baseSitePage = await client.api('/sites/7f50f45e-714a-4264-9c59-3bf43ea4db8f/pages/df69e386-6c58-4df2-afc0-ab6327d5b202')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->byBaseSitePageId('baseSitePage-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

Get-MgSitePage -SiteId $siteId -BaseSitePageId $baseSitePageId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.sites.by_site_id('site-id').pages.by_base_site_page_id('baseSitePage-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.sitePage",
    "@odata.etag": "\"{F45354CB-D634-45DF-8B88-2B4E96A1DC45},8\"",
    "description": "Reiciendis placeat dolores.Mollitia veniam tempora tempora quidem voluptatum.Quos animi maiores facilis.Dolores officiis consequatur provident beatae deleniti accusamus magni quam tenetur.",
    "eTag": "\"{F45354CB-D634-45DF-8B88-2B4E96A1DC45},8\"",
    "id": "f45354cb-d634-45df-8b88-2b4e96a1dc45",
    "lastModifiedDateTime": "2023-04-16T10:01:41Z",
    "name": "Electronic Convertible.aspx",
    "webUrl": "https://contoso.sharepoint.com/SitePages/Electronic Convertible.aspx",
    "title": "Electronic Convertible",
    "pageLayout": "article",
    "thumbnailWebUrl": "https://media.akamai.odsp.cdn.office.net/_layouts/15/images/sitepagethumbnail.png",
    "promotionKind": "page",
    "showComments": false,
    "showRecommendedPages": true,
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
}
```
