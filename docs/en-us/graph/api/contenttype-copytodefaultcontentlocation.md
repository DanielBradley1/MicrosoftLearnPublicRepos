<!-- Source: https://learn.microsoft.com/en-us/graph/api/contenttype-copytodefaultcontentlocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# contentType: copyToDefaultContentLocation

Namespace: microsoft.graph

Copy a file to a default content location in a [content type](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0). The file can then be added as a default file or template via a POST operation.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Sites.FullControl.All, Sites.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Sites.FullControl.All, Sites.Manage.All |

## HTTP request

```http
POST /sites/{siteId}/contentTypes/{contentTypeId}/copyToDefaultContentLocation 
```

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
| sourceFile | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | Metadata about the source file that needs to be copied to the default content location. Required. |
| destinationFileName | string | Destination filename. |

## Response

If successful, this call returns a `204 No Content` response.

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
POST https://graph.microsoft.com/v1.0/sites/{siteId}/contentTypes/{contentTypeId}/copyToDefaultContentLocation 
Content-Type: application/json

{
   "sourceFile":{
      "sharepointIds":{
         "listId":"e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0",
         "listItemId":"2"
      }
   },
   "destinationFileName":"newname.txt"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Sites.Item.ContentTypes.Item.CopyToDefaultContentLocation;
using Microsoft.Graph.Models;

var requestBody = new CopyToDefaultContentLocationPostRequestBody
{
	SourceFile = new ItemReference
	{
		SharepointIds = new SharepointIds
		{
			ListId = "e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0",
			ListItemId = "2",
		},
	},
	DestinationFileName = "newname.txt",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Sites["{site-id}"].ContentTypes["{contentType-id}"].CopyToDefaultContentLocation.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsites "github.com/microsoftgraph/msgraph-sdk-go/sites"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphsites.NewCopyToDefaultContentLocationPostRequestBody()
sourceFile := graphmodels.NewItemReference()
sharepointIds := graphmodels.NewSharepointIds()
listId := "e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0"
sharepointIds.SetListId(&listId) 
listItemId := "2"
sharepointIds.SetListItemId(&listItemId) 
sourceFile.SetSharepointIds(sharepointIds)
requestBody.SetSourceFile(sourceFile)
destinationFileName := "newname.txt"
requestBody.SetDestinationFileName(&destinationFileName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Sites().BySiteId("site-id").ContentTypes().ByContentTypeId("contentType-id").CopyToDefaultContentLocation().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.sites.item.contenttypes.item.copytodefaultcontentlocation.CopyToDefaultContentLocationPostRequestBody copyToDefaultContentLocationPostRequestBody = new com.microsoft.graph.sites.item.contenttypes.item.copytodefaultcontentlocation.CopyToDefaultContentLocationPostRequestBody();
ItemReference sourceFile = new ItemReference();
SharepointIds sharepointIds = new SharepointIds();
sharepointIds.setListId("e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0");
sharepointIds.setListItemId("2");
sourceFile.setSharepointIds(sharepointIds);
copyToDefaultContentLocationPostRequestBody.setSourceFile(sourceFile);
copyToDefaultContentLocationPostRequestBody.setDestinationFileName("newname.txt");
graphClient.sites().bySiteId("{site-id}").contentTypes().byContentTypeId("{contentType-id}").copyToDefaultContentLocation().post(copyToDefaultContentLocationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const copyToDefaultContentLocation = {
   sourceFile: {
      sharepointIds: {
         listId: 'e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0',
         listItemId: '2'
      }
   },
   destinationFileName: 'newname.txt'
};

await client.api('/sites/{siteId}/contentTypes/{contentTypeId}/copyToDefaultContentLocation')
	.post(copyToDefaultContentLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Sites\Item\ContentTypes\Item\CopyToDefaultContentLocation\CopyToDefaultContentLocationPostRequestBody;
use Microsoft\Graph\Generated\Models\ItemReference;
use Microsoft\Graph\Generated\Models\SharepointIds;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CopyToDefaultContentLocationPostRequestBody();
$sourceFile = new ItemReference();
$sourceFileSharepointIds = new SharepointIds();
$sourceFileSharepointIds->setListId('e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0');
$sourceFileSharepointIds->setListItemId('2');
$sourceFile->setSharepointIds($sourceFileSharepointIds);
$requestBody->setSourceFile($sourceFile);
$requestBody->setDestinationFileName('newname.txt');

$graphServiceClient->sites()->bySiteId('site-id')->contentTypes()->byContentTypeId('contentType-id')->copyToDefaultContentLocation()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	sourceFile = @{
		sharepointIds = @{
			listId = "e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0"
			listItemId = "2"
		}
	}
	destinationFileName = "newname.txt"
}

Copy-MgSiteContentTypeToDefaultContentLocation -SiteId $siteId -ContentTypeId $contentTypeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.sites.item.contenttypes.item.copy_to_default_content_location.copy_to_default_content_location_post_request_body import CopyToDefaultContentLocationPostRequestBody
from msgraph.generated.models.item_reference import ItemReference
from msgraph.generated.models.sharepoint_ids import SharepointIds
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CopyToDefaultContentLocationPostRequestBody(
	source_file = ItemReference(
		sharepoint_ids = SharepointIds(
			list_id = "e2ecf63b-b0fd-48f7-a54a-d8c15479e3b0",
			list_item_id = "2",
		),
	),
	destination_file_name = "newname.txt",
)

await graph_client.sites.by_site_id('site-id').content_types.by_content_type_id('contentType-id').copy_to_default_content_location.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
