<!-- Source: https://learn.microsoft.com/en-us/graph/api/newslinkpage-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-11 -->

# Create newsLinkPage

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) in the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-beta) of a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
POST /sites/{site-id}/pages
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json for JSON content, including the required **title** property in multipart requests. Multipart requests use the multipart/form-data; boundary=your-boundary content type. Required. |
| Prefer | include-unknown-enum-members. Use the `Prefer: include-unknown-enum-members` request header to get the following value in [pageLayoutType](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta#pagelayouttype-values), which is a [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `newsLink`. |

## Request body

In the request body, supply a JSON representation of the [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) object. The body must contain required properties placed directly in the request body; however, to set a banner image by uploading an image, it must be in a multipart message format as shown in the example. For the banner image upload, you must send a multipart request because it involves binary data.

> **Notes:**
> 
> - To ensure successful parsing of the request body, the `@odata.type=#microsoft.graph.newsLinkPage` must be included in the request body.
> - Currently, to set the **bannerImageWebUrl**, the capability exists to upload the image bytes directly. These bytes get auto-saved in the site assets library, and the **bannerImageWebUrl** is then generated based on the persisted file. To achieve this, make a multipart request and set the `@microsoft.graph.bannerImageWebUrlContent` annotation to send the image content. For more details, see [Example 2](https://learn.microsoft.com/en-us/graph/api/newslinkpage-create?view=graph-rest-beta#example-2-create-a-news-link-page-and-upload-the-banner-image-file-content).

You can specify the following properties when you create a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The descriptive text for the item. The maximum length limit is 250 characters. Optional. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |
| newsWebUrl | String | The URL of the news article referenced by the **newsLinkPage**. It can be an external link. Required. |
| title | String | Title of the **newsLinkPage**. The maximum length limit is 110 characters. Required. Inherited from [baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-beta). |

## Response

If successful, this method returns a `201 Created` response code and a [newsLinkPage](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create a news link page with only the required properties

The following example shows how to create a [news link page](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) using only the required properties.

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

```
POST /sites/c1370818-f5e0-4a40-a99b-be4520640642/pages
prefer: include-unknown-enum-members
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.newsLinkPage",
  "newsWebUrl":"https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car",
  "title": "Contoso Unveils First Self-Driving Car"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new NewsLinkPage
{
	OdataType = "#microsoft.graph.newsLinkPage",
	NewsWebUrl = "https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car",
	Title = "Contoso Unveils First Self-Driving Car",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("prefer", "include-unknown-enum-members");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  graphsites "github.com/microsoftgraph/msgraph-beta-sdk-go/sites"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("prefer", "include-unknown-enum-members")

configuration := &graphsites.ItemPagesRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewBaseSitePage()
newsWebUrl := "https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car"
requestBody.SetNewsWebUrl(&newsWebUrl) 
title := "Contoso Unveils First Self-Driving Car"
requestBody.SetTitle(&title) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
pages, err := graphClient.Sites().BySiteId("site-id").Pages().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

NewsLinkPage baseSitePage = new NewsLinkPage();
baseSitePage.setOdataType("#microsoft.graph.newsLinkPage");
baseSitePage.setNewsWebUrl("https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car");
baseSitePage.setTitle("Contoso Unveils First Self-Driving Car");
BaseSitePage result = graphClient.sites().bySiteId("{site-id}").pages().post(baseSitePage, requestConfiguration -> {
	requestConfiguration.headers.add("prefer", "include-unknown-enum-members");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const baseSitePage = {
  '@odata.type': '#microsoft.graph.newsLinkPage',
  newsWebUrl: 'https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car',
  title: 'Contoso Unveils First Self-Driving Car'
};

await client.api('/sites/c1370818-f5e0-4a40-a99b-be4520640642/pages')
	.version('beta')
	.post(baseSitePage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Sites\Item\Pages\PagesRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\NewsLinkPage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new NewsLinkPage();
$requestBody->setOdataType('#microsoft.graph.newsLinkPage');
$requestBody->setNewsWebUrl('https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car');
$requestBody->setTitle('Contoso Unveils First Self-Driving Car');
$requestConfiguration = new PagesRequestBuilderPostRequestConfiguration();
$headers = [
		'prefer' => 'include-unknown-enum-members',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Sites

$params = @{
	"@odata.type" = "#microsoft.graph.newsLinkPage"
	newsWebUrl = "https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car"
	title = "Contoso Unveils First Self-Driving Car"
}

New-MgBetaSitePage -SiteId $siteId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.sites.item.pages.pages_request_builder import PagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.news_link_page import NewsLinkPage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = NewsLinkPage(
	odata_type = "#microsoft.graph.newsLinkPage",
	news_web_url = "https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car",
	title = "Contoso Unveils First Self-Driving Car",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("prefer", "include-unknown-enum-members")


result = await graph_client.sites.by_site_id('site-id').pages.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "eTag": "\"{6A34958A-6F84-4571-A26E-B2CEB20261EB},3\"",
  "id": "6a34958a-6f84-4571-a26e-b2ceb20261eb",
  "lastModifiedDateTime": "2023-09-10T18:46:23Z",
  "name": "contoso-unveils-first-self-driving-car.aspx",
  "webUrl": "https://contoso.sharepoint.com/SitePages/contoso-unveils-first-self-driving-car.aspx",
  "title": "Contoso Unveils First Self-Driving Car",
  "pageLayout": "newsLink",
  "newsWebUrl": "https://someexternalnewssite.com/2024/11/11/contoso-unveils-first-self-driving-car",
  "createdBy": {
    "user": {
      "displayName": "Jane Doe"
    }
  },
  "lastModifiedBy": {
    "user": {
      "displayName": "Jane Doe"
    }
  },
  "contentType": {
    "id": "0x0101009D1CB255DA76424F860D91F20E6C4118002A50BFCFB7614729B56886FADA02339B000B27C676C81DC54289A1417148759BF3",
    "name": "Repost Page"
  },
  "publishingState": {
    "level":"checkout",
    "versionId":"0.1",
    "checkedOutBy": {
      "user": {
        "displayName":"Jane Doe",
        "email":"JaneDoe@contoso.sharepoint.com"
      }
    }
  }
}
```

### Example 2: Create a news link page and upload the banner image file content

The following example shows how to create a [news link page](https://learn.microsoft.com/en-us/graph/api/resources/newslinkpage?view=graph-rest-beta) with a banner image. This process requires a multipart request.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/sites/c1370818-f5e0-4a40-a99b-be4520640642/pages
Prefer: include-unknown-enum-members
Content-type: multipart/form-data; boundary=MyPartBoundary198374

--MyPartBoundary198374
Content-Disposition: form-data; name="request"
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.newsLinkPage",
  "title": "Microsoft Build brings AI tools to the forefront for developers",
  "newsWebUrl": "https://someexternalnewssite.com/2024/05/23/microsoft-build-ai-tools-developers",
  "description": "You only need two simple letters to accurately convey the major shift in the technology space this year: A and I. Beyond those letters, however, is a complex, evolving and exciting way in which we work, communicate and collaborate.",
  "@microsoft.graph.bannerImageWebUrlContent": "name:content"
}

--MyPartBoundary198374
Content-Disposition: form-data; name="content"; filename="b3.jpg"
Content-Type: image/jpeg

... binary image data ...

--MyPartBoundary198374
```

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const baseSitePage = --MyPartBoundary198374
Content-Disposition: form-data; name='request'
Content-Type: application/json

{
  '@odata.type': '#microsoft.graph.newsLinkPage',
  title: 'Microsoft Build brings AI tools to the forefront for developers',
  newsWebUrl: 'https://someexternalnewssite.com/2024/05/23/microsoft-build-ai-tools-developers',
  description: 'You only need two simple letters to accurately convey the major shift in the technology space this year: A and I. Beyond those letters, however, is a complex, evolving and exciting way in which we work, communicate and collaborate.',
  '@microsoft.graph.bannerImageWebUrlContent': 'name:content'
}

--MyPartBoundary198374
Content-Disposition: form-data; name='content'; filename='b3.jpg'
Content-Type: image/jpeg

... binary image data ...

--MyPartBoundary198374;

await client.api('/sites/c1370818-f5e0-4a40-a99b-be4520640642/pages')
	.version('beta')
	.post(baseSitePage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. If a failure occurs when you upload or persist the banner image, the response contains `@microsoft.graph.bannerImageWebUrlContentError` and a descriptive error message.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

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
    "level": "checkout",
    "versionId": "0.1",
    "checkedOutBy": {
      "user": {
        "displayName": "John Doe",
        "email": "jdoe@contoso.com"
      }
    }
  }
}
```
