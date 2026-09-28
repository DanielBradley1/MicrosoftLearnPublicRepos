<!-- Source: https://learn.microsoft.com/en-us/graph/api/browsersitelist-post-sharedcookies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create browserSharedCookie

Namespace: microsoft.graph

Create a new [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) object in a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0).

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
POST /admin/edge/internetExplorerMode/siteLists/{browserSiteListId}/sharedCookies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) object.

You can specify the following properties when you create a **browserSharedCookie**.

| Property | Type | Description |
| :--- | :--- | :--- |
| comment | String | The comment of the cookie. Required. |
| displayName | String | The name of the cookie. Required. |
| hostOnly | Boolean | Determines whether a cookie is a host-only or domain cookie. Required. |
| hostOrDomain | String | The URL of the cookie. Required. |
| path | String | The path of the cookie. Required. |
| sourceEnvironment | browserSharedCookieSourceEnvironment | Specifies how the cookies are shared between Microsoft Edge and Internet Explorer. The possible values are: `microsoftEdge`, `internetExplorer11`, `both`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [browserSharedCookie](https://learn.microsoft.com/en-us/graph/api/resources/browsersharedcookie?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/admin/edge/internetExplorerMode/siteLists/e370d818-f650-5ab1-499e-5915e83f4573/sharedCookies
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.browserSharedCookie",
    "hostOrDomain": "www.microsoft.com",
    "sourceEnvironment": "InternetExplorer11",
    "displayName": "Microsoft Cookie",
    "hostOnly": true,
    "comment": "A cookie for microsoft.com",
    "path": "/"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BrowserSharedCookie
{
	OdataType = "#microsoft.graph.browserSharedCookie",
	HostOrDomain = "www.microsoft.com",
	SourceEnvironment = BrowserSharedCookieSourceEnvironment.InternetExplorer11,
	DisplayName = "Microsoft Cookie",
	HostOnly = true,
	Comment = "A cookie for microsoft.com",
	Path = "/",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Edge.InternetExplorerMode.SiteLists["{browserSiteList-id}"].SharedCookies.PostAsync(requestBody);
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
sourceEnvironment := graphmodels.INTERNETEXPLORER11_BROWSERSHAREDCOOKIESOURCEENVIRONMENT 
requestBody.SetSourceEnvironment(&sourceEnvironment) 
displayName := "Microsoft Cookie"
requestBody.SetDisplayName(&displayName) 
hostOnly := true
requestBody.SetHostOnly(&hostOnly) 
comment := "A cookie for microsoft.com"
requestBody.SetComment(&comment) 
path := "/"
requestBody.SetPath(&path) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sharedCookies, err := graphClient.Admin().Edge().InternetExplorerMode().SiteLists().ByBrowserSiteListId("browserSiteList-id").SharedCookies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BrowserSharedCookie browserSharedCookie = new BrowserSharedCookie();
browserSharedCookie.setOdataType("#microsoft.graph.browserSharedCookie");
browserSharedCookie.setHostOrDomain("www.microsoft.com");
browserSharedCookie.setSourceEnvironment(BrowserSharedCookieSourceEnvironment.InternetExplorer11);
browserSharedCookie.setDisplayName("Microsoft Cookie");
browserSharedCookie.setHostOnly(true);
browserSharedCookie.setComment("A cookie for microsoft.com");
browserSharedCookie.setPath("/");
BrowserSharedCookie result = graphClient.admin().edge().internetExplorerMode().siteLists().byBrowserSiteListId("{browserSiteList-id}").sharedCookies().post(browserSharedCookie);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browserSharedCookie = {
    '@odata.type': '#microsoft.graph.browserSharedCookie',
    hostOrDomain: 'www.microsoft.com',
    sourceEnvironment: 'InternetExplorer11',
    displayName: 'Microsoft Cookie',
    hostOnly: true,
    comment: 'A cookie for microsoft.com',
    path: '/'
};

await client.api('/admin/edge/internetExplorerMode/siteLists/e370d818-f650-5ab1-499e-5915e83f4573/sharedCookies')
	.post(browserSharedCookie);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BrowserSharedCookie;
use Microsoft\Graph\Generated\Models\BrowserSharedCookieSourceEnvironment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BrowserSharedCookie();
$requestBody->setOdataType('#microsoft.graph.browserSharedCookie');
$requestBody->setHostOrDomain('www.microsoft.com');
$requestBody->setSourceEnvironment(new BrowserSharedCookieSourceEnvironment('internetExplorer11'));
$requestBody->setDisplayName('Microsoft Cookie');
$requestBody->setHostOnly(true);
$requestBody->setComment('A cookie for microsoft.com');
$requestBody->setPath('/');

$result = $graphServiceClient->admin()->edge()->internetExplorerMode()->siteLists()->byBrowserSiteListId('browserSiteList-id')->sharedCookies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement

$params = @{
	"@odata.type" = "#microsoft.graph.browserSharedCookie"
	hostOrDomain = "www.microsoft.com"
	sourceEnvironment = "InternetExplorer11"
	displayName = "Microsoft Cookie"
	hostOnly = $true
	comment = "A cookie for microsoft.com"
	path = "/"
}

New-MgAdminEdgeInternetExplorerModeSiteListSharedCookie -BrowserSiteListId $browserSiteListId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.browser_shared_cookie import BrowserSharedCookie
from msgraph.generated.models.browser_shared_cookie_source_environment import BrowserSharedCookieSourceEnvironment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BrowserSharedCookie(
	odata_type = "#microsoft.graph.browserSharedCookie",
	host_or_domain = "www.microsoft.com",
	source_environment = BrowserSharedCookieSourceEnvironment.InternetExplorer11,
	display_name = "Microsoft Cookie",
	host_only = True,
	comment = "A cookie for microsoft.com",
	path = "/",
)

result = await graph_client.admin.edge.internet_explorer_mode.site_lists.by_browser_site_list_id('browserSiteList-id').shared_cookies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "status": "pendingAdd",
    "id": "07f4030f-45ff-4ad1-9277-3b8f6ee74141",
    "hostOrDomain": "www.microsoft.com",
    "sourceEnvironment": "internetExplorer11",
    "displayName": "Microsoft Cookie",
    "path": "/",
    "hostOnly": true,
    "comment": "A cookie for microsoft.com",
    "lastModifiedDateTime": "2022-06-29T15:32:39.6732721Z",
    "createdDateTime": "2022-06-29T15:32:39.673272Z",
    "deletedDateTime": null,
    "lastModifiedBy": {
        "user": {
            "id": "f6ff107e-bc40-4918-a432-8d7b60030a7c",
            "displayName": "Joe Smith"
        },
        "application": null
    },
    "history": []
}
```
