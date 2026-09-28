<!-- Source: https://learn.microsoft.com/en-us/graph/api/contenttype-associatewithhubsites?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# contentType: associateWithHubSites

Namespace: microsoft.graph

Associate a published [content type](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) present in a content type hub with a list of hub sites.

> **Note:** This feature is limited to tenants that have a SharePoint Syntex license.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Manage.All | Sites.FullControl.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Manage.All | Sites.FullControl.All |

## HTTP request

```http
POST /sites/{siteId}/contentTypes/{contentTypeId}/associateWithHubSites
```

> **Note:** The *siteId* represents a content type hub site.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| --- | --- | --- |
| hubSiteUrls | String collection | List of canonical URLs to the hub sites where the content type needs to be enforced. Required. |
| propagateToExistingLists | Boolean | If `true`, content types are enforced on existing lists in the hub sites; otherwise, they're applied only to newly created lists. |

## Response

If successful, this action returns a `204 No Content` response code.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/sites/{site-id}/contentTypes/{contentTypeId}/associateWithHubSites
Content-Type: application/json

{
   "hubSiteUrls":[
      "https://graph.microsoft.com/v1.0/sites/{site-id}"
   ],
   "propagateToExistingLists":false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Sites.Item.ContentTypes.Item.AssociateWithHubSites;

var requestBody = new AssociateWithHubSitesPostRequestBody
{
	HubSiteUrls = new List<string>
	{
		"https://graph.microsoft.com/v1.0/sites/{site-id}",
	},
	PropagateToExistingLists = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Sites["{site-id}"].ContentTypes["{contentType-id}"].AssociateWithHubSites.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsites "github.com/microsoftgraph/msgraph-sdk-go/sites"
	  //other-imports
)

requestBody := graphsites.NewAssociateWithHubSitesPostRequestBody()
hubSiteUrls := []string {
	"https://graph.microsoft.com/v1.0/sites/{site-id}",
}
requestBody.SetHubSiteUrls(hubSiteUrls)
propagateToExistingLists := false
requestBody.SetPropagateToExistingLists(&propagateToExistingLists) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Sites().BySiteId("site-id").ContentTypes().ByContentTypeId("contentType-id").AssociateWithHubSites().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.sites.item.contenttypes.item.associatewithhubsites.AssociateWithHubSitesPostRequestBody associateWithHubSitesPostRequestBody = new com.microsoft.graph.sites.item.contenttypes.item.associatewithhubsites.AssociateWithHubSitesPostRequestBody();
LinkedList<String> hubSiteUrls = new LinkedList<String>();
hubSiteUrls.add("https://graph.microsoft.com/v1.0/sites/{site-id}");
associateWithHubSitesPostRequestBody.setHubSiteUrls(hubSiteUrls);
associateWithHubSitesPostRequestBody.setPropagateToExistingLists(false);
graphClient.sites().bySiteId("{site-id}").contentTypes().byContentTypeId("{contentType-id}").associateWithHubSites().post(associateWithHubSitesPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const associateWithHubSites = {
   hubSiteUrls: [
      'https://graph.microsoft.com/v1.0/sites/{site-id}'
   ],
   propagateToExistingLists: false
};

await client.api('/sites/{site-id}/contentTypes/{contentTypeId}/associateWithHubSites')
	.post(associateWithHubSites);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Sites\Item\ContentTypes\Item\AssociateWithHubSites\AssociateWithHubSitesPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssociateWithHubSitesPostRequestBody();
$requestBody->setHubSiteUrls(['https://graph.microsoft.com/v1.0/sites/{site-id}', 	]);
$requestBody->setPropagateToExistingLists(false);

$graphServiceClient->sites()->bySiteId('site-id')->contentTypes()->byContentTypeId('contentType-id')->associateWithHubSites()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	hubSiteUrls = @(
	"https://graph.microsoft.com/v1.0/sites/{site-id}"
)
propagateToExistingLists = $false
}

Join-MgSiteContentTypeWithHubSite -SiteId $siteId -ContentTypeId $contentTypeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.sites.item.contenttypes.item.associate_with_hub_sites.associate_with_hub_sites_post_request_body import AssociateWithHubSitesPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssociateWithHubSitesPostRequestBody(
	hub_site_urls = [
		"https://graph.microsoft.com/v1.0/sites/{site-id}",
	],
	propagate_to_existing_lists = False,
)

await graph_client.sites.by_site_id('site-id').content_types.by_content_type_id('contentType-id').associate_with_hub_sites.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
