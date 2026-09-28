<!-- Source: https://learn.microsoft.com/en-us/graph/api/browsersitelist-publish?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# browserSiteList: publish

Namespace: microsoft.graph

Publish the specified [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) for devices to download.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BrowserSiteLists.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BrowserSiteLists.ReadWrite.All | Not available. |

## HTTP request

```http
POST /admin/edge/internetExplorerMode/siteLists/{browserSiteListId}/publish
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, omit both sites and shared cookies to publish the entire site list. Optionally, you can publish specific sites and shared cookies by specifying a collection of IDs.

| Property | Type | Description |
| :--- | :--- | :--- |
| revision | String | The revision of the site list to publish. Required. |
| sharedCookies | [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) collection | The collection of shared cookies to publish. Optional. Only requires the shared cookie ID. All other fields are ignored. |
| sites | [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) collection | The collection of sites to publish. Optional. Only requires the site ID. All other fields are ignored. |

## Response

If successful, this action returns a `200 OK` response code and a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0) in the response body.

## Examples

### Example 1: Publish all sites and shared cookies

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

```http
POST https://graph.microsoft.com/v1.0/admin/edge/internetExplorerMode/siteLists/36ba61eb-c492-4283-a38b-963a1dbb2f69/publish
Content-Type: application/json

{
    "revision": "1.0"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Edge.InternetExplorerMode.SiteLists.Item.Publish;

var requestBody = new PublishPostRequestBody
{
	Revision = "1.0",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Edge.InternetExplorerMode.SiteLists["{browserSiteList-id}"].Publish.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)

requestBody := graphadmin.NewPublishPostRequestBody()
revision := "1.0"
requestBody.SetRevision(&revision) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
publish, err := graphClient.Admin().Edge().InternetExplorerMode().SiteLists().ByBrowserSiteListId("browserSiteList-id").Publish().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.edge.internetexplorermode.sitelists.item.publish.PublishPostRequestBody publishPostRequestBody = new com.microsoft.graph.admin.edge.internetexplorermode.sitelists.item.publish.PublishPostRequestBody();
publishPostRequestBody.setRevision("1.0");
var result = graphClient.admin().edge().internetExplorerMode().siteLists().byBrowserSiteListId("{browserSiteList-id}").publish().post(publishPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browserSiteList = {
    revision: '1.0'
};

await client.api('/admin/edge/internetExplorerMode/siteLists/36ba61eb-c492-4283-a38b-963a1dbb2f69/publish')
	.post(browserSiteList);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Edge\InternetExplorerMode\SiteLists\Item\Publish\PublishPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PublishPostRequestBody();
$requestBody->setRevision('1.0');

$result = $graphServiceClient->admin()->edge()->internetExplorerMode()->siteLists()->byBrowserSiteListId('browserSiteList-id')->publish()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement

$params = @{
	revision = "1.0"
}

Publish-MgAdminEdgeInternetExplorerModeSiteList -BrowserSiteListId $browserSiteListId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.edge.internetexplorermode.sitelists.item.publish.publish_post_request_body import PublishPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PublishPostRequestBody(
	revision = "1.0",
)

result = await graph_client.admin.edge.internet_explorer_mode.site_lists.by_browser_site_list_id('browserSiteList-id').publish.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.browserSiteList",
    "id": "36ba61eb-c492-4283-a38b-963a1dbb2f69",
    "revision": "1.0",
    "displayName": "Product Site List A",
    "description": "A production site list for team A",
    "lastModifiedDateTime": "2022-06-28T19:29:52.8752365Z",
    "publishedDateTime": "2022-06-28T19:29:52.8752365Z",
    "status": "published",
    "lastModifiedBy": {
        "user": {
            "id": "f6ff107e-bc40-4918-a432-8d7b60030a7c",
            "displayName": "Joe Smith"
        },
        "application": null
    },
    "publishedBy": {
        "user": {
            "id": "f6ff107e-bc40-4918-a432-8d7b60030a7c",
            "displayName": "Joe Smith"
        },
        "application": null
    }
}
```

### Example 2: Publish specific sites and shared cookies

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
POST https://graph.microsoft.com/v1.0/admin/edge/internetExplorerMode/siteLists/36ba61eb-c492-4283-a38b-963a1dbb2f69/publish
Content-Type: application/json

{
    "revision": "1.0",
    "sites": [
        {
            "id": "53e5f971-fc7b-4cd3-a1bf-34d7c0416882"
        },
        {
            "id": "2e27cc86-3662-447e-b751-274fb9f869ea"
        }
    ],
    "sharedCookies": [
        {
            "id": "7f639835-23ab-4793-b1e6-1a06fad127a2"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Edge.InternetExplorerMode.SiteLists.Item.Publish;
using Microsoft.Graph.Models;

var requestBody = new PublishPostRequestBody
{
	Revision = "1.0",
	Sites = new List<BrowserSite>
	{
		new BrowserSite
		{
			Id = "53e5f971-fc7b-4cd3-a1bf-34d7c0416882",
		},
		new BrowserSite
		{
			Id = "2e27cc86-3662-447e-b751-274fb9f869ea",
		},
	},
	SharedCookies = new List<BrowserSharedCookie>
	{
		new BrowserSharedCookie
		{
			Id = "7f639835-23ab-4793-b1e6-1a06fad127a2",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Edge.InternetExplorerMode.SiteLists["{browserSiteList-id}"].Publish.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphadmin.NewPublishPostRequestBody()
revision := "1.0"
requestBody.SetRevision(&revision) 


browserSite := graphmodels.NewBrowserSite()
id := "53e5f971-fc7b-4cd3-a1bf-34d7c0416882"
browserSite.SetId(&id) 
browserSite1 := graphmodels.NewBrowserSite()
id := "2e27cc86-3662-447e-b751-274fb9f869ea"
browserSite1.SetId(&id) 

sites := []graphmodels.BrowserSiteable {
	browserSite,
	browserSite1,
}
requestBody.SetSites(sites)


browserSharedCookie := graphmodels.NewBrowserSharedCookie()
id := "7f639835-23ab-4793-b1e6-1a06fad127a2"
browserSharedCookie.SetId(&id) 

sharedCookies := []graphmodels.BrowserSharedCookieable {
	browserSharedCookie,
}
requestBody.SetSharedCookies(sharedCookies)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
publish, err := graphClient.Admin().Edge().InternetExplorerMode().SiteLists().ByBrowserSiteListId("browserSiteList-id").Publish().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.edge.internetexplorermode.sitelists.item.publish.PublishPostRequestBody publishPostRequestBody = new com.microsoft.graph.admin.edge.internetexplorermode.sitelists.item.publish.PublishPostRequestBody();
publishPostRequestBody.setRevision("1.0");
LinkedList<BrowserSite> sites = new LinkedList<BrowserSite>();
BrowserSite browserSite = new BrowserSite();
browserSite.setId("53e5f971-fc7b-4cd3-a1bf-34d7c0416882");
sites.add(browserSite);
BrowserSite browserSite1 = new BrowserSite();
browserSite1.setId("2e27cc86-3662-447e-b751-274fb9f869ea");
sites.add(browserSite1);
publishPostRequestBody.setSites(sites);
LinkedList<BrowserSharedCookie> sharedCookies = new LinkedList<BrowserSharedCookie>();
BrowserSharedCookie browserSharedCookie = new BrowserSharedCookie();
browserSharedCookie.setId("7f639835-23ab-4793-b1e6-1a06fad127a2");
sharedCookies.add(browserSharedCookie);
publishPostRequestBody.setSharedCookies(sharedCookies);
var result = graphClient.admin().edge().internetExplorerMode().siteLists().byBrowserSiteListId("{browserSiteList-id}").publish().post(publishPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browserSiteList = {
    revision: '1.0',
    sites: [
        {
            id: '53e5f971-fc7b-4cd3-a1bf-34d7c0416882'
        },
        {
            id: '2e27cc86-3662-447e-b751-274fb9f869ea'
        }
    ],
    sharedCookies: [
        {
            id: '7f639835-23ab-4793-b1e6-1a06fad127a2'
        }
    ]
};

await client.api('/admin/edge/internetExplorerMode/siteLists/36ba61eb-c492-4283-a38b-963a1dbb2f69/publish')
	.post(browserSiteList);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Edge\InternetExplorerMode\SiteLists\Item\Publish\PublishPostRequestBody;
use Microsoft\Graph\Generated\Models\BrowserSite;
use Microsoft\Graph\Generated\Models\BrowserSharedCookie;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PublishPostRequestBody();
$requestBody->setRevision('1.0');
$sitesBrowserSite1 = new BrowserSite();
$sitesBrowserSite1->setId('53e5f971-fc7b-4cd3-a1bf-34d7c0416882');
$sitesArray []= $sitesBrowserSite1;
$sitesBrowserSite2 = new BrowserSite();
$sitesBrowserSite2->setId('2e27cc86-3662-447e-b751-274fb9f869ea');
$sitesArray []= $sitesBrowserSite2;
$requestBody->setSites($sitesArray);

$sharedCookiesBrowserSharedCookie1 = new BrowserSharedCookie();
$sharedCookiesBrowserSharedCookie1->setId('7f639835-23ab-4793-b1e6-1a06fad127a2');
$sharedCookiesArray []= $sharedCookiesBrowserSharedCookie1;
$requestBody->setSharedCookies($sharedCookiesArray);


$result = $graphServiceClient->admin()->edge()->internetExplorerMode()->siteLists()->byBrowserSiteListId('browserSiteList-id')->publish()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement

$params = @{
	revision = "1.0"
	sites = @(
		@{
			id = "53e5f971-fc7b-4cd3-a1bf-34d7c0416882"
		}
		@{
			id = "2e27cc86-3662-447e-b751-274fb9f869ea"
		}
	)
	sharedCookies = @(
		@{
			id = "7f639835-23ab-4793-b1e6-1a06fad127a2"
		}
	)
}

Publish-MgAdminEdgeInternetExplorerModeSiteList -BrowserSiteListId $browserSiteListId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.edge.internetexplorermode.sitelists.item.publish.publish_post_request_body import PublishPostRequestBody
from msgraph.generated.models.browser_site import BrowserSite
from msgraph.generated.models.browser_shared_cookie import BrowserSharedCookie
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PublishPostRequestBody(
	revision = "1.0",
	sites = [
		BrowserSite(
			id = "53e5f971-fc7b-4cd3-a1bf-34d7c0416882",
		),
		BrowserSite(
			id = "2e27cc86-3662-447e-b751-274fb9f869ea",
		),
	],
	shared_cookies = [
		BrowserSharedCookie(
			id = "7f639835-23ab-4793-b1e6-1a06fad127a2",
		),
	],
)

result = await graph_client.admin.edge.internet_explorer_mode.site_lists.by_browser_site_list_id('browserSiteList-id').publish.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **status** will show `pending` if the request contains sites or shared cookies that you have not published yet.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.browserSiteList",
    "id": "36ba61eb-c492-4283-a38b-963a1dbb2f69",
    "revision": "1.0",
    "displayName": "Product Site List A",
    "description": "A production site list for team A",
    "lastModifiedDateTime": "2022-06-28T19:29:52.8752365Z",
    "publishedDateTime": "2022-06-28T19:29:52.8752365Z",
    "status": "pending",
    "lastModifiedBy": {
        "user": {
            "id": "f6ff107e-bc40-4918-a432-8d7b60030a7c",
            "displayName": "Joe Smith"
        },
        "application": null
    },
    "publishedBy": {
        "user": {
            "id": "f6ff107e-bc40-4918-a432-8d7b60030a7c",
            "displayName": "Joe Smith"
        },
        "application": null
    }
}
```
