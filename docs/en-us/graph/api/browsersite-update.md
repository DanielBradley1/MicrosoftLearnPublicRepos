<!-- Source: https://learn.microsoft.com/en-us/graph/api/browsersite-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update browserSite

Namespace: microsoft.graph

Update the properties of a [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) object.

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
PATCH /admin/edge/internetExplorerMode/siteLists/{browserSiteListId}/sites/{browserSiteId}
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
| allowRedirect | Boolean | Controls the behavior of redirected sites. If `true`, indicates that the site will open in Internet Explorer 11 or Microsoft Edge even if the site is navigated to as part of a HTTP or meta refresh redirection chain. |
| comment | String | The comment for the site. |
| compatibilityMode | browserSiteCompatibilityMode | Controls what compatibility setting is used for specific sites or domains. The possible values are: `default`, `internetExplorer8Enterprise`, `internetExplorer7Enterprise`, `internetExplorer11`, `internetExplorer10`, `internetExplorer9`, `internetExplorer8`, `internetExplorer7`, `internetExplorer5`, `unknownFutureValue`. |
| mergeType | browserSiteMergeType | The merge type of the site. The possible values are: `noMerge`, `default`, `unknownFutureValue`. |
| targetEnvironment | browserSiteTargetEnvironment | The target environment that the site should open in. The possible values are: `internetExplorerMode`, `internetExplorer11`, `microsoftEdge`, `configurable`, `none`, `unknownFutureValue`.  <br>  <br>Prior to June 15, 2022, the `internetExplorer11` option would allow opening a site in the Internet Explorer 11 \(IE11\) desktop application. Following the retirement of IE11 on June 15, 2022, the `internetExplorer11` option will no longer open an IE11 window and will instead behave the same as the `internetExplorerMode` option. |
| webUrl | String | The URL of the site. |

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
PATCH https://graph.microsoft.com/v1.0/admin/edge/internetExplorerMode/siteLists/972a5778-df43-45fd-9c2a-5dd944c7a1ce/sites/7cf831d2-8a9b-4826-b120-911566f6fd6a
Content-Type: application/json
Content-length: 387

{
    "webUrl": "www.microsoft.com",
    "targetEnvironment": "microsoftEdge",
    "mergeType": "default",
    "compatibilityMode": "default",
    "allowRedirect": false,
    "comment": "Updating to Edge."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BrowserSite
{
	WebUrl = "www.microsoft.com",
	TargetEnvironment = BrowserSiteTargetEnvironment.MicrosoftEdge,
	MergeType = BrowserSiteMergeType.Default,
	CompatibilityMode = BrowserSiteCompatibilityMode.Default,
	AllowRedirect = false,
	Comment = "Updating to Edge.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Edge.InternetExplorerMode.SiteLists["{browserSiteList-id}"].Sites["{browserSite-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewBrowserSite()
webUrl := "www.microsoft.com"
requestBody.SetWebUrl(&webUrl) 
targetEnvironment := graphmodels.MICROSOFTEDGE_BROWSERSITETARGETENVIRONMENT 
requestBody.SetTargetEnvironment(&targetEnvironment) 
mergeType := graphmodels.DEFAULT_BROWSERSITEMERGETYPE 
requestBody.SetMergeType(&mergeType) 
compatibilityMode := graphmodels.DEFAULT_BROWSERSITECOMPATIBILITYMODE 
requestBody.SetCompatibilityMode(&compatibilityMode) 
allowRedirect := false
requestBody.SetAllowRedirect(&allowRedirect) 
comment := "Updating to Edge."
requestBody.SetComment(&comment) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sites, err := graphClient.Admin().Edge().InternetExplorerMode().SiteLists().ByBrowserSiteListId("browserSiteList-id").Sites().ByBrowserSiteId("browserSite-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BrowserSite browserSite = new BrowserSite();
browserSite.setWebUrl("www.microsoft.com");
browserSite.setTargetEnvironment(BrowserSiteTargetEnvironment.MicrosoftEdge);
browserSite.setMergeType(BrowserSiteMergeType.Default);
browserSite.setCompatibilityMode(BrowserSiteCompatibilityMode.Default);
browserSite.setAllowRedirect(false);
browserSite.setComment("Updating to Edge.");
BrowserSite result = graphClient.admin().edge().internetExplorerMode().siteLists().byBrowserSiteListId("{browserSiteList-id}").sites().byBrowserSiteId("{browserSite-id}").patch(browserSite);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browserSite = {
    webUrl: 'www.microsoft.com',
    targetEnvironment: 'microsoftEdge',
    mergeType: 'default',
    compatibilityMode: 'default',
    allowRedirect: false,
    comment: 'Updating to Edge.'
};

await client.api('/admin/edge/internetExplorerMode/siteLists/972a5778-df43-45fd-9c2a-5dd944c7a1ce/sites/7cf831d2-8a9b-4826-b120-911566f6fd6a')
	.update(browserSite);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BrowserSite;
use Microsoft\Graph\Generated\Models\BrowserSiteTargetEnvironment;
use Microsoft\Graph\Generated\Models\BrowserSiteMergeType;
use Microsoft\Graph\Generated\Models\BrowserSiteCompatibilityMode;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BrowserSite();
$requestBody->setWebUrl('www.microsoft.com');
$requestBody->setTargetEnvironment(new BrowserSiteTargetEnvironment('microsoftEdge'));
$requestBody->setMergeType(new BrowserSiteMergeType('default'));
$requestBody->setCompatibilityMode(new BrowserSiteCompatibilityMode('default'));
$requestBody->setAllowRedirect(false);
$requestBody->setComment('Updating to Edge.');

$result = $graphServiceClient->admin()->edge()->internetExplorerMode()->siteLists()->byBrowserSiteListId('browserSiteList-id')->sites()->byBrowserSiteId('browserSite-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement

$params = @{
	webUrl = "www.microsoft.com"
	targetEnvironment = "microsoftEdge"
	mergeType = "default"
	compatibilityMode = "default"
	allowRedirect = $false
	comment = "Updating to Edge."
}

Update-MgAdminEdgeInternetExplorerModeSiteListSite -BrowserSiteListId $browserSiteListId -BrowserSiteId $browserSiteId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.browser_site import BrowserSite
from msgraph.generated.models.browser_site_target_environment import BrowserSiteTargetEnvironment
from msgraph.generated.models.browser_site_merge_type import BrowserSiteMergeType
from msgraph.generated.models.browser_site_compatibility_mode import BrowserSiteCompatibilityMode
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BrowserSite(
	web_url = "www.microsoft.com",
	target_environment = BrowserSiteTargetEnvironment.MicrosoftEdge,
	merge_type = BrowserSiteMergeType.Default,
	compatibility_mode = BrowserSiteCompatibilityMode.Default,
	allow_redirect = False,
	comment = "Updating to Edge.",
)

result = await graph_client.admin.edge.internet_explorer_mode.site_lists.by_browser_site_list_id('browserSiteList-id').sites.by_browser_site_id('browserSite-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
