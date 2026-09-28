<!-- Source: https://learn.microsoft.com/en-us/graph/long-running-actions-overview -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Working with long-running actions

This article describes how to work with long-running actions when you use Microsoft Graph APIs. Some API responses require an indeterminate amount of time to complete. Instead of waiting until the action is complete before returning a response, Microsoft Graph might use a long-running actions pattern. This pattern provides your app a way to poll for status updates on a long-running action, without any request waiting for the action to complete.

The general pattern involves the following steps:

1. Your app requests a long-running action via the API. The API accepts the action and returns a `202 Accepted` response along with a `Location` header for the API URL to retrieve action status reports.
2. Your app requests the action status report URL and receives an [asyncJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/asyncjobstatus) response with the progress of the long-running action.
3. The long-running action completes.
4. Your app requests the action status report URL again and receives an [asyncJobStatus](https://learn.microsoft.com/en-us/graph/api/resources/asyncjobstatus) response that shows the completion of the action.

## Prerequisites

The same [permissions](https://learn.microsoft.com/en-us/graph/permissions-reference) that are required to perform a long-running action are also required to query the status of a long-running action.

## Initial action request

The following example uses the [driveitem: copy](https://learn.microsoft.com/en-us/graph/api/driveitem-copy) method. In this scenario, your app makes a request to copy a folder that contains a large amount of data. This request is likely to take several seconds to complete because the amount of data is large.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/me/drive/items/{folder-item-id}/copy
Content-Type: application/json

{
  "parentReference": {
    "path": "/drive/root:/Documents"
  },
  "name": "Copy of LargeFolder1"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Drives.Item.Items.Item.Copy;
using Microsoft.Graph.Beta.Models;

var requestBody = new CopyPostRequestBody
{
	ParentReference = new ItemReference
	{
		Path = "/drive/root:/Documents",
	},
	Name = "Copy of LargeFolder1",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Copy.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-beta-sdk-go/drives"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphdrives.NewCopyPostRequestBody()
parentReference := graphmodels.NewItemReference()
path := "/drive/root:/Documents"
parentReference.SetPath(&path) 
requestBody.SetParentReference(parentReference)
name := "Copy of LargeFolder1"
requestBody.SetName(&name) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
copy, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Copy().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.drives.item.items.item.copy.CopyPostRequestBody copyPostRequestBody = new com.microsoft.graph.beta.drives.item.items.item.copy.CopyPostRequestBody();
ItemReference parentReference = new ItemReference();
parentReference.setPath("/drive/root:/Documents");
copyPostRequestBody.setParentReference(parentReference);
copyPostRequestBody.setName("Copy of LargeFolder1");
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").copy().post(copyPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const driveItem = {
  parentReference: {
    path: '/drive/root:/Documents'
  },
  name: 'Copy of LargeFolder1'
};

await client.api('/me/drive/items/{folder-item-id}/copy')
	.version('beta')
	.post(driveItem);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Drives\Item\Items\Item\Copy\CopyPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\ItemReference;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CopyPostRequestBody();
$parentReference = new ItemReference();
$parentReference->setPath('/drive/root:/Documents');
$requestBody->setParentReference($parentReference);
$requestBody->setName('Copy of LargeFolder1');

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->copy()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Files

$params = @{
	parentReference = @{
		path = "/drive/root:/Documents"
	}
	name = "Copy of LargeFolder1"
}

Copy-MgBetaDriveItem -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.drives.item.items.item.copy.copy_post_request_body import CopyPostRequestBody
from msgraph_beta.generated.models.item_reference import ItemReference
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CopyPostRequestBody(
	parent_reference = ItemReference(
		path = "/drive/root:/Documents",
	),
	name = "Copy of LargeFolder1",
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').copy.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The API responds that the action was accepted and provides the URL to retrieve the status of the long-running action.

```http
HTTP/1.1 202 Accepted
Location: https://api.onedrive.com/monitor/4A3407B5-88FC-4504-8B21-0AABD3412717
```

> **Note:** The location URL returned might not be on the Microsoft Graph API endpoint.

In many cases, this step is the end of the request, because the copy action completes without any other work from the app. However, if your app needs to show the status of the copy action or ensure that it completes without error, it can do so by using the monitor URL.

## Retrieve a status report from the monitor URL

To check on the status of the copy action, the app makes a request to the URL provided in the previous response.

> **Note:** This request doesn't require authentication, because the URL is short-lived and unique to the original caller.

```http
GET https://api.onedrive.com/monitor/4A3407B5-88FC-4504-8B21-0AABD3412717
```

The service responds with information that the long-running action is still in progress.

```http
HTTP/1.1 202 Accepted
Content-type: application/json

{
  "operation": "ItemCopy",
  "percentageComplete": 27.8,
  "status": "inProgress"
}
```

This information can be used to provide an update to the user about the progress of the copy action. The app can continue to poll the monitor URL to request status updates and keep track of the progress of the action.

## Retrieve a completed status report from the monitor URL

After a few seconds, the copy operation completes. This time, when the app makes a request to the monitor URL, the response is a redirection to the finished result of the action.

```http
GET https://api.onedrive.com/monitor/4A3407B5-88FC-4504-8B21-0AABD3412717
```

When the action completes, the response from the monitor service returns the resource ID for the results.

```http
HTTP/1.1 202 Accepted
Content-type: application/json

{
    "percentageComplete": 100.0,
    "resourceId": "01MOWKYVJML57KN2ANMBA3JZJS2MBGC7KM",
    "status": "completed"
}
```

## Retrieve the results of the completed operation

When the job is completed, the monitor URL returns the resource ID of the result. In this case, it's the new copy of the original item. The following example shows how you can address this new item by using the resource ID.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/me/drive/items/{item-id}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
items, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DriveItem result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let driveItem = await client.api('/me/drive/items/{item-id}')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Files

Get-MgBetaDriveItem -DriveId $driveId -DriveItemId $driveItemId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "",
    "name": "Copy of LargeFolder1",
    "folder": { },
    "size": 12019
}
```

## Supported resources

Long-running actions are supported on the following methods.

| **Resource** | **API** |
| :--- | :--- |
| driveItem | [copy](https://learn.microsoft.com/en-us/graph/api/driveitem-copy) |
