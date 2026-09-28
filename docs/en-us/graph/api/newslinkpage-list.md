<!-- Source: https://learn.microsoft.com/en-us/graph/api/newslinkpage-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List newsLinkPage

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) objects and their properties.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Read.All | Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Read.All | Sites.ReadWrite.All |

## HTTP request

```http
GET /sites/{site-id}/pages/microsoft.graph.newsLinkPage
```

## Optional query parameters

This method supports the `$count`, `$expand`, `$filter`, `$orderBy`, `$select`, and `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer | include-unknown-enum-members. Use the `Prefer: include-unknown-enum-members` request header to get the following values in [pageLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta#pagelayouttype-values), which is a [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `newsLink`. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/sites/056d8292-ef8a-44fe-bd22-97abf08659b1/pages/microsoft.graph.newsLinkPage
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages["{baseSitePage-id}"].GetAsync();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
pages, err := graphClient.Sites().BySiteId("site-id").Pages().ByBaseSitePageId("baseSitePage-id").Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BaseSitePage result = graphClient.sites().bySiteId("{site-id}").pages().byBaseSitePageId("{baseSitePage-id}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->byBaseSitePageId('baseSitePage-id')->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Sites

Get-MgBetaSitePage -SiteId $siteId -BaseSitePageId $baseSitePageId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.sites.by_site_id('site-id').pages.by_base_site_page_id('baseSitePage-id').get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#sites('056d8292-ef8a-44fe-bd22-97abf08659b1')/pages/microsoft.graph.newsLinkPage",
  "value": [
    {
      "@odata.type": "#microsoft.graph.newsLinkPage",
      "createdDateTime": "2024-06-11T17:31:20Z",
      "description": " In a groundbreaking study, a team of scientists has reportedly discovered the secret to eternal youth. The research, conducted in a top-secret laboratory, claims to have identified a unique combination of natural ingredients that can halt the aging process.",
      "eTag": "\"{179210C2-637E-4C61-8491-331D0D4A0C05},2\"",
      "id": "179210c2-637e-4c61-8491-331d0d4a0c05",
      "lastModifiedDateTime": "2024-06-11T17:31:21Z",
      "name": "Scientists-Discover-Secret-to-Eternal-Youth.aspx",
      "webUrl": "https://contoso.sharepoint.com/SitePages/Scientists-Discover-Secret-to-Eternal-Youth.aspx",
      "title": "Scientists Discover Secret to Eternal Youth",
      "pageLayout": "newsLink",
      "bannerImageWebUrl": "https://contoso.sharepoint.com/_layouts/15/getpreview.ashx?path=/SiteAssets/SitePages/Scientists-Discover-Secret-to-Eternal-Youth/BannerImage.png",
      "newsWebUrl": "https://someexternalnewssite.com/2024/06/11/scientists-discover-secret-to-eternal-youth",
      "createdBy": {
        "user": {
          "displayName": "John Doe",
          "email": "jdoe@contoso.com"
        }
      },
      "lastModifiedBy": {
        "user": {
          "displayName": "John Doe",
          "email": "jdoe@contoso.com"
        }
      },
      "publishingState": {
        "level": "published",
        "versionId": "1.0"
      }
    },
    {
      "@odata.type": "#microsoft.graph.newsLinkPage",
      "createdDateTime": "2024-06-11T17:31:20Z",
      "description": "You only need two simple letters to accurately convey the major shift in the technology space this year: A and I. Beyond those letters, however, is a complex, evolving and exciting way in which we work, communicate and collaborate.",
      "eTag": "\"{179210C2-637E-4C61-8491-331D0D4A0C05},2\"",
      "id": "179210c2-637e-4c61-8491-331d0d4a0c05",
      "lastModifiedDateTime": "2024-06-11T17:31:21Z",
      "name": "microsoft-build-ai-tools-developers.aspx",
      "webUrl": "https://contoso.sharepoint.com/SitePages/Microsoft-Build-brings-AI-tools-to-the-forefront-for-developers.aspx",
      "title": "Microsoft Build brings AI tools to the forefront for developers",
      "pageLayout": "newsLink",
      "bannerImageWebUrl": "https://contoso.sharepoint.com/_layouts/15/getpreview.ashx?path=/SiteAssets/SitePages/microsoft-build-ai-tools-developers/BannerImage.png",
      "newsWebUrl": "https://someexternalnewssite.com/2024/05/23/microsoft-build-ai-tools-developers",
      "createdBy": {
        "user": {
          "displayName": "John Doe",
          "email": "jdoe@contoso.com"
        }
      },
      "lastModifiedBy": {
        "user": {
          "displayName": "John Doe",
          "email": "jdoe@contoso.com"
        }
      },
      "publishingState": {
        "level": "published",
        "versionId": "1.0"
      }
    }
  ]
}
```
