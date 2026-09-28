<!-- Source: https://learn.microsoft.com/en-us/graph/api/browsersharedcookie-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update browserSharedCookie

Namespace: microsoft.graph

Update the properties of a [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) object.

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
PATCH /admin/edge/internetExplorerMode/siteLists/{browserSiteListId}/sharedCookies/{browserSharedCookieId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| comment | String | The comment of the cookie. |
| displayName | String | The name of the cookie. |
| hostOnly | Boolean | Determines whether a cookie is a host-only or domain cookie. |
| hostOrDomain | String | The URL of the cookie. |
| path | String | The path of the cookie. |
| sourceEnvironment | browserSharedCookieSourceEnvironment | Specifies how the cookies are shared between Microsoft Edge and Internet Explorer. The possible values are: `microsoftEdge`, `internetExplorer11`, `both`, `unknownFutureValue`. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

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

```http
PATCH https://graph.microsoft.com/v1.0/admin/edge/internetExplorerMode/siteLists/20579923-e6c8-425a-b728-47f43c10bc05/sharedCookies/972a5778-df43-45fd-9c2a-5dd944c7a1ce
Content-Type: application/json
Content-length: 349

{
  "hostOrDomain": "www.microsoft.com",
  "sourceEnvironment": "microsoftEdge",
  "displayName": "Microsoft Cookie",
  "path": "/",
  "hostOnly": true,
  "comment": "Updating source environment."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BrowserSharedCookie
{
	HostOrDomain = "www.microsoft.com",
	SourceEnvironment = BrowserSharedCookieSourceEnvironment.MicrosoftEdge,
	DisplayName = "Microsoft Cookie",
	Path = "/",
	HostOnly = true,
	Comment = "Updating source environment.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Edge.InternetExplorerMode.SiteLists["{browserSiteList-id}"].SharedCookies["{browserSharedCookie-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewBrowserSharedCookie()
hostOrDomain := "www.microsoft.com"
requestBody.SetHostOrDomain(&hostOrDomain) 
sourceEnvironment := graphmodels.MICROSOFTEDGE_BROWSERSHAREDCOOKIESOURCEENVIRONMENT 
requestBody.SetSourceEnvironment(&sourceEnvironment) 
displayName := "Microsoft Cookie"
requestBody.SetDisplayName(&displayName) 
path := "/"
requestBody.SetPath(&path) 
hostOnly := true
requestBody.SetHostOnly(&hostOnly) 
comment := "Updating source environment."
requestBody.SetComment(&comment) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sharedCookies, err := graphClient.Admin().Edge().InternetExplorerMode().SiteLists().ByBrowserSiteListId("browserSiteList-id").SharedCookies().ByBrowserSharedCookieId("browserSharedCookie-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BrowserSharedCookie browserSharedCookie = new BrowserSharedCookie();
browserSharedCookie.setHostOrDomain("www.microsoft.com");
browserSharedCookie.setSourceEnvironment(BrowserSharedCookieSourceEnvironment.MicrosoftEdge);
browserSharedCookie.setDisplayName("Microsoft Cookie");
browserSharedCookie.setPath("/");
browserSharedCookie.setHostOnly(true);
browserSharedCookie.setComment("Updating source environment.");
BrowserSharedCookie result = graphClient.admin().edge().internetExplorerMode().siteLists().byBrowserSiteListId("{browserSiteList-id}").sharedCookies().byBrowserSharedCookieId("{browserSharedCookie-id}").patch(browserSharedCookie);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browserSharedCookie = {
  hostOrDomain: 'www.microsoft.com',
  sourceEnvironment: 'microsoftEdge',
  displayName: 'Microsoft Cookie',
  path: '/',
  hostOnly: true,
  comment: 'Updating source environment.'
};

await client.api('/admin/edge/internetExplorerMode/siteLists/20579923-e6c8-425a-b728-47f43c10bc05/sharedCookies/972a5778-df43-45fd-9c2a-5dd944c7a1ce')
	.update(browserSharedCookie);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BrowserSharedCookie;
use Microsoft\Graph\Generated\Models\BrowserSharedCookieSourceEnvironment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BrowserSharedCookie();
$requestBody->setHostOrDomain('www.microsoft.com');
$requestBody->setSourceEnvironment(new BrowserSharedCookieSourceEnvironment('microsoftEdge'));
$requestBody->setDisplayName('Microsoft Cookie');
$requestBody->setPath('/');
$requestBody->setHostOnly(true);
$requestBody->setComment('Updating source environment.');

$result = $graphServiceClient->admin()->edge()->internetExplorerMode()->siteLists()->byBrowserSiteListId('browserSiteList-id')->sharedCookies()->byBrowserSharedCookieId('browserSharedCookie-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement

$params = @{
	hostOrDomain = "www.microsoft.com"
	sourceEnvironment = "microsoftEdge"
	displayName = "Microsoft Cookie"
	path = "/"
	hostOnly = $true
	comment = "Updating source environment."
}

Update-MgAdminEdgeInternetExplorerModeSiteListSharedCookie -BrowserSiteListId $browserSiteListId -BrowserSharedCookieId $browserSharedCookieId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.browser_shared_cookie import BrowserSharedCookie
from msgraph.generated.models.browser_shared_cookie_source_environment import BrowserSharedCookieSourceEnvironment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BrowserSharedCookie(
	host_or_domain = "www.microsoft.com",
	source_environment = BrowserSharedCookieSourceEnvironment.MicrosoftEdge,
	display_name = "Microsoft Cookie",
	path = "/",
	host_only = True,
	comment = "Updating source environment.",
)

result = await graph_client.admin.edge.internet_explorer_mode.site_lists.by_browser_site_list_id('browserSiteList-id').shared_cookies.by_browser_shared_cookie_id('browserSharedCookie-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
