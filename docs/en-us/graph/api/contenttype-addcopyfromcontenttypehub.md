<!-- Source: https://learn.microsoft.com/en-us/graph/api/contenttype-addcopyfromcontenttypehub?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# contentType: addCopyFromContentTypeHub

Namespace: microsoft.graph

Add or sync a copy of a published content type from the content type hub to a target [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) or a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0).

This method is part of the content type publishing changes to optimize the syncing of published content types to sites and lists, effectively switching from a "push everywhere" to "pull as needed" approach. The method allows users to pull content types directly from the content type hub to a site or list. For more information, see [contentType: getCompatibleHubContentTypes](https://learn.microsoft.com/en-us/graph/api/contenttype-getcompatiblehubcontenttypes?view=graph-rest-1.0) and the blog post [Syntex Product Updates – August 2021](https://techcommunity.microsoft.com/t5/sharepoint-syntex-blog/syntex-product-updates-august-2021/ba-p/2606438).

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
POST /sites/{siteId}/lists/{listId}/contentTypes/addCopyFromContentTypeHub
POST /sites/{siteId}/contentTypes/addCopyFromContentTypeHub
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameter that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentTypeId | String | The ID of the content type in the content type hub that will be added to a target site or a list. |

## Response

If successful, this action returns a `200 OK` response code and a [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) object in the response body if the content type is added synchronously or a `202 Accepted` response code if the content type will be synced asynchronously. The response will also contain a `Location` header, which contains the location of the [richLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) that was created to handle the copy/sync operation. In case of an asynchronous operation, it can take up to 70 minutes to sync or add a content type.

## Examples

### Example 1: Synchronous pull

The following example adds or syncs a content type synchronously based on certain backend conditions.

#### Request

The following is an example of a synchronous operation.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/sites/root/lists/Documents/contentTypes/addCopyFromContentTypeHub
Content-Type: application/json
Content-length: 33

{
  "contentTypeId": "0x0101"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Sites.Item.Lists.Item.ContentTypes.AddCopyFromContentTypeHub;

var requestBody = new AddCopyFromContentTypeHubPostRequestBody
{
	ContentTypeId = "0x0101",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Lists["{list-id}"].ContentTypes.AddCopyFromContentTypeHub.PostAsync(requestBody);
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

requestBody := graphsites.NewAddCopyFromContentTypeHubPostRequestBody()
contentTypeId := "0x0101"
requestBody.SetContentTypeId(&contentTypeId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
addCopyFromContentTypeHub, err := graphClient.Sites().BySiteId("site-id").Lists().ByListId("list-id").ContentTypes().AddCopyFromContentTypeHub().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.sites.item.lists.item.contenttypes.addcopyfromcontenttypehub.AddCopyFromContentTypeHubPostRequestBody addCopyFromContentTypeHubPostRequestBody = new com.microsoft.graph.sites.item.lists.item.contenttypes.addcopyfromcontenttypehub.AddCopyFromContentTypeHubPostRequestBody();
addCopyFromContentTypeHubPostRequestBody.setContentTypeId("0x0101");
var result = graphClient.sites().bySiteId("{site-id}").lists().byListId("{list-id}").contentTypes().addCopyFromContentTypeHub().post(addCopyFromContentTypeHubPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const contentType = {
  contentTypeId: '0x0101'
};

await client.api('/sites/root/lists/Documents/contentTypes/addCopyFromContentTypeHub')
	.post(contentType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Sites\Item\Lists\Item\ContentTypes\AddCopyFromContentTypeHub\AddCopyFromContentTypeHubPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AddCopyFromContentTypeHubPostRequestBody();
$requestBody->setContentTypeId('0x0101');

$result = $graphServiceClient->sites()->bySiteId('site-id')->lists()->byListId('list-id')->contentTypes()->addCopyFromContentTypeHub()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	contentTypeId = "0x0101"
}

Add-MgSiteListContentTypeCopyFromContentTypeHub -SiteId $siteId -ListId $listId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.sites.item.lists.item.contenttypes.add_copy_from_content_type_hub.add_copy_from_content_type_hub_post_request_body import AddCopyFromContentTypeHubPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AddCopyFromContentTypeHubPostRequestBody(
	content_type_id = "0x0101",
)

result = await graph_client.sites.by_site_id('site-id').lists.by_list_id('list-id').content_types.add_copy_from_content_type_hub.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.contentType",
    "id": "0x0101",
    "description": "Document content type",
    "group": "Document Content Types",
    "hidden": false,
    "isBuiltIn": true,
    "name": "Document"
}
```

### Example 2: Asynchronous pull

The following example adds or syncs a content type asynchronously because the backend conditions for a synchronous operation are not fulfilled.

#### Request

The following is an example of an asynchronous operation.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/sites/root/lists/Documents/contentTypes/addCopyFromContentTypeHub
Content-Type: application/json
Content-length: 33

{
  "contentTypeId": "0x0101"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Sites.Item.Lists.Item.ContentTypes.AddCopyFromContentTypeHub;

var requestBody = new AddCopyFromContentTypeHubPostRequestBody
{
	ContentTypeId = "0x0101",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Lists["{list-id}"].ContentTypes.AddCopyFromContentTypeHub.PostAsync(requestBody);
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

requestBody := graphsites.NewAddCopyFromContentTypeHubPostRequestBody()
contentTypeId := "0x0101"
requestBody.SetContentTypeId(&contentTypeId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
addCopyFromContentTypeHub, err := graphClient.Sites().BySiteId("site-id").Lists().ByListId("list-id").ContentTypes().AddCopyFromContentTypeHub().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.sites.item.lists.item.contenttypes.addcopyfromcontenttypehub.AddCopyFromContentTypeHubPostRequestBody addCopyFromContentTypeHubPostRequestBody = new com.microsoft.graph.sites.item.lists.item.contenttypes.addcopyfromcontenttypehub.AddCopyFromContentTypeHubPostRequestBody();
addCopyFromContentTypeHubPostRequestBody.setContentTypeId("0x0101");
var result = graphClient.sites().bySiteId("{site-id}").lists().byListId("{list-id}").contentTypes().addCopyFromContentTypeHub().post(addCopyFromContentTypeHubPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const contentType = {
  contentTypeId: '0x0101'
};

await client.api('/sites/root/lists/Documents/contentTypes/addCopyFromContentTypeHub')
	.post(contentType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Sites\Item\Lists\Item\ContentTypes\AddCopyFromContentTypeHub\AddCopyFromContentTypeHubPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AddCopyFromContentTypeHubPostRequestBody();
$requestBody->setContentTypeId('0x0101');

$result = $graphServiceClient->sites()->bySiteId('site-id')->lists()->byListId('list-id')->contentTypes()->addCopyFromContentTypeHub()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	contentTypeId = "0x0101"
}

Add-MgSiteListContentTypeCopyFromContentTypeHub -SiteId $siteId -ListId $listId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.sites.item.lists.item.contenttypes.add_copy_from_content_type_hub.add_copy_from_content_type_hub_post_request_body import AddCopyFromContentTypeHubPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AddCopyFromContentTypeHubPostRequestBody(
	content_type_id = "0x0101",
)

result = await graph_client.sites.by_site_id('site-id').lists.by_list_id('list-id').content_types.add_copy_from_content_type_hub.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
location: https://graph.microsoft.com/v1.0/sites/root/lists/Documents/operations/contentTypeCopy,0x0101
```
