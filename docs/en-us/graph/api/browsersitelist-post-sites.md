<!-- Source: https://learn.microsoft.com/en-us/graph/api/browsersitelist-post-sites?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create browserSite

Namespace: microsoft.graph

Create a new [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) object in a [browserSiteList](https://learn.microsoft.com/en-us/graph/api/resources/browsersitelist?view=graph-rest-1.0).

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
POST /admin/edge/internetExplorerMode/siteLists/{browserSiteListId}/sites
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) object.

You can specify the following properties when you create a **browserSite**.

| Property | Type | Description |
| :--- | :--- | :--- |
| allowRedirect | Boolean | Controls the behavior of redirected sites. If `true`, indicates that the site will open in Internet Explorer 11 or Microsoft Edge even if the site is navigated to as part of a HTTP or meta refresh redirection chain. Required. |
| comment | String | The comment for the site. Required |
| compatibilityMode | browserSiteCompatibilityMode | Controls what compatibility setting is used for specific sites or domains. The possible values are: `default`, `internetExplorer8Enterprise`, `internetExplorer7Enterprise`, `internetExplorer11`, `internetExplorer10`, `internetExplorer9`, `internetExplorer8`, `internetExplorer7`, `internetExplorer5`, `unknownFutureValue`. Required. |
| mergeType | browserSiteMergeType | The merge type of the site. The possible values are: `noMerge`, `default`, `unknownFutureValue`. Required. |
| targetEnvironment | browserSiteTargetEnvironment | The target environment that the site should open in. The possible values are: `internetExplorerMode`, `internetExplorer11`, `microsoftEdge`, `configurable`, `none`, `unknownFutureValue`. Required.  <br>  <br>Prior to June 15, 2022, the `internetExplorer11` option would allow opening a site in the Internet Explorer 11 \(IE11\) desktop application. Following the retirement of IE11 on June 15, 2022, the `internetExplorer11` option will no longer open an IE11 window and will instead behave the same as the `internetExplorerMode` option. |
| webUrl | String | The URL of the site. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [browserSite](https://learn.microsoft.com/en-us/graph/api/resources/browsersite?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/admin/edge/internetExplorerMode/siteLists/e370d818-f650-5ab1-499e-5915e83f4573/sites
Content-Type: application/json
Content-length: 387

{
    "@odata.type": "#microsoft.graph.browserSite",
    "webUrl": "www.microsoft.com",
    "targetEnvironment": "InternetExplorer11",
    "comment": "A site that opens in InternetExplorer11",
    "mergeType": "default",
    "compatibilityMode": "default",
    "allowRedirect": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BrowserSite
{
	OdataType = "#microsoft.graph.browserSite",
	WebUrl = "www.microsoft.com",
	TargetEnvironment = BrowserSiteTargetEnvironment.InternetExplorer11,
	Comment = "A site that opens in InternetExplorer11",
	MergeType = BrowserSiteMergeType.Default,
	CompatibilityMode = BrowserSiteCompatibilityMode.Default,
	AllowRedirect = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Edge.InternetExplorerMode.SiteLists["{browserSiteList-id}"].Sites.PostAsync(requestBody);
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
targetEnvironment := graphmodels.INTERNETEXPLORER11_BROWSERSITETARGETENVIRONMENT 
requestBody.SetTargetEnvironment(&targetEnvironment) 
comment := "A site that opens in InternetExplorer11"
requestBody.SetComment(&comment) 
mergeType := graphmodels.DEFAULT_BROWSERSITEMERGETYPE 
requestBody.SetMergeType(&mergeType) 
compatibilityMode := graphmodels.DEFAULT_BROWSERSITECOMPATIBILITYMODE 
requestBody.SetCompatibilityMode(&compatibilityMode) 
allowRedirect := true
requestBody.SetAllowRedirect(&allowRedirect) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sites, err := graphClient.Admin().Edge().InternetExplorerMode().SiteLists().ByBrowserSiteListId("browserSiteList-id").Sites().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BrowserSite browserSite = new BrowserSite();
browserSite.setOdataType("#microsoft.graph.browserSite");
browserSite.setWebUrl("www.microsoft.com");
browserSite.setTargetEnvironment(BrowserSiteTargetEnvironment.InternetExplorer11);
browserSite.setComment("A site that opens in InternetExplorer11");
browserSite.setMergeType(BrowserSiteMergeType.Default);
browserSite.setCompatibilityMode(BrowserSiteCompatibilityMode.Default);
browserSite.setAllowRedirect(true);
BrowserSite result = graphClient.admin().edge().internetExplorerMode().siteLists().byBrowserSiteListId("{browserSiteList-id}").sites().post(browserSite);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const browserSite = {
    '@odata.type': '#microsoft.graph.browserSite',
    webUrl: 'www.microsoft.com',
    targetEnvironment: 'InternetExplorer11',
    comment: 'A site that opens in InternetExplorer11',
    mergeType: 'default',
    compatibilityMode: 'default',
    allowRedirect: true
};

await client.api('/admin/edge/internetExplorerMode/siteLists/e370d818-f650-5ab1-499e-5915e83f4573/sites')
	.post(browserSite);
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
$requestBody->setOdataType('#microsoft.graph.browserSite');
$requestBody->setWebUrl('www.microsoft.com');
$requestBody->setTargetEnvironment(new BrowserSiteTargetEnvironment('internetExplorer11'));
$requestBody->setComment('A site that opens in InternetExplorer11');
$requestBody->setMergeType(new BrowserSiteMergeType('default'));
$requestBody->setCompatibilityMode(new BrowserSiteCompatibilityMode('default'));
$requestBody->setAllowRedirect(true);

$result = $graphServiceClient->admin()->edge()->internetExplorerMode()->siteLists()->byBrowserSiteListId('browserSiteList-id')->sites()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement

$params = @{
	"@odata.type" = "#microsoft.graph.browserSite"
	webUrl = "www.microsoft.com"
	targetEnvironment = "InternetExplorer11"
	comment = "A site that opens in InternetExplorer11"
	mergeType = "default"
	compatibilityMode = "default"
	allowRedirect = $true
}

New-MgAdminEdgeInternetExplorerModeSiteListSite -BrowserSiteListId $browserSiteListId -BodyParameter $params
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
	odata_type = "#microsoft.graph.browserSite",
	web_url = "www.microsoft.com",
	target_environment = BrowserSiteTargetEnvironment.InternetExplorer11,
	comment = "A site that opens in InternetExplorer11",
	merge_type = BrowserSiteMergeType.Default,
	compatibility_mode = BrowserSiteCompatibilityMode.Default,
	allow_redirect = True,
)

result = await graph_client.admin.edge.internet_explorer_mode.site_lists.by_browser_site_list_id('browserSiteList-id').sites.post(request_body)
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
    "id": "a22cbc85-d5d2-4e61-8414-42e6704c36f7",
    "webUrl": "www.microsoft.com",
    "targetEnvironment": "internetExplorer11",
    "mergeType": "default",
    "compatibilityMode": "default",
    "allowRedirect": true,
    "comment": "A site that opens in InternetExplorer11",
    "lastModifiedDateTime": "2022-06-29T14:51:23.8662592Z",
    "createdDateTime": "2022-06-29T14:51:23.8662595Z",
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
