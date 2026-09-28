<!-- Source: https://learn.microsoft.com/en-us/graph/api/drive-post-bundles?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create bundle

Namespace: microsoft.graph

Add a new [bundle](https://learn.microsoft.com/en-us/graph/api/resources/bundle?view=graph-rest-1.0) to the user's drive.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Files.ReadWrite.All |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /drive/bundles
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the bundle to be created.

## Response

If the request is successful, the [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) representing the newly created bundle will be returned.

For information about error responses, see [Error responses](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Example 1: Create a bundle

The following example shows how to create a basic new bundle. This request will create a new bundle named `Just some files` and add two existing items to the bundle. This bundle can be used to share a collection of files with other users without sharing the folder those items are stored in.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/drive/bundles
Content-Type: application/json

{
  "name": "Just some files",
  "@microsoft.graph.conflictBehavior" : "rename",
  "bundle": { },
  "children": [
    { "id": "1234asdf" },
    { "id": "1234qwerty" }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new DriveItem
{
	Name = "Just some files",
	Bundle = new Bundle
	{
	},
	Children = new List<DriveItem>
	{
		new DriveItem
		{
			Id = "1234asdf",
		},
		new DriveItem
		{
			Id = "1234qwerty",
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@microsoft.graph.conflictBehavior" , "rename"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Bundles.PostAsync(requestBody);
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

requestBody := graphmodels.NewDriveItem()
name := "Just some files"
requestBody.SetName(&name) 
bundle := graphmodels.NewBundle()
requestBody.SetBundle(bundle)


driveItem := graphmodels.NewDriveItem()
id := "1234asdf"
driveItem.SetId(&id) 
driveItem1 := graphmodels.NewDriveItem()
id := "1234qwerty"
driveItem1.SetId(&id) 

children := []graphmodels.DriveItemable {
	driveItem,
	driveItem1,
}
requestBody.SetChildren(children)
additionalData := map[string]interface{}{
	"@microsoft.graph.conflictBehavior" : "rename", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bundles, err := graphClient.Drives().ByDriveId("drive-id").Bundles().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DriveItem driveItem = new DriveItem();
driveItem.setName("Just some files");
Bundle bundle = new Bundle();
driveItem.setBundle(bundle);
LinkedList<DriveItem> children = new LinkedList<DriveItem>();
DriveItem driveItem1 = new DriveItem();
driveItem1.setId("1234asdf");
children.add(driveItem1);
DriveItem driveItem2 = new DriveItem();
driveItem2.setId("1234qwerty");
children.add(driveItem2);
driveItem.setChildren(children);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@microsoft.graph.conflictBehavior", "rename");
driveItem.setAdditionalData(additionalData);
DriveItem result = graphClient.drives().byDriveId("{drive-id}").bundles().post(driveItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const driveItem = {
  name: 'Just some files',
  '@microsoft.graph.conflictBehavior': 'rename',
  bundle: { },
  children: [
    { id: '1234asdf' },
    { id: '1234qwerty' }
  ]
};

await client.api('/drive/bundles')
	.post(driveItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\DriveItem;
use Microsoft\Graph\Generated\Models\Bundle;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DriveItem();
$requestBody->setName('Just some files');
$bundle = new Bundle();
$requestBody->setBundle($bundle);
$childrenDriveItem1 = new DriveItem();
$childrenDriveItem1->setId('1234asdf');
$childrenArray []= $childrenDriveItem1;
$childrenDriveItem2 = new DriveItem();
$childrenDriveItem2->setId('1234qwerty');
$childrenArray []= $childrenDriveItem2;
$requestBody->setChildren($childrenArray);

$additionalData = [
'@microsoft.graph.conflictBehavior' => 'rename',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->bundles()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	name = "Just some files"
	"@microsoft.graph.conflictBehavior" = "rename"
	bundle = @{
	}
	children = @(
		@{
			id = "1234asdf"
		}
		@{
			id = "1234qwerty"
		}
	)
}

New-MgDriveBundle -DriveId $driveId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.drive_item import DriveItem
from msgraph.generated.models.bundle import Bundle
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DriveItem(
	name = "Just some files",
	bundle = Bundle(
	),
	children = [
		DriveItem(
			id = "1234asdf",
		),
		DriveItem(
			id = "1234qwerty",
		),
	],
	additional_data = {
			"@microsoft_graph_conflict_behavior" : "rename",
	}
)

result = await graph_client.drives.by_drive_id('drive-id').bundles.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "1234321!abc",
  "name": "Just some files",
  "bundle": {
    "childCount": 2
  }
}
```

The response object shown here might be shortened for readability.

### Example 2: Create an album

The request to create a new photo album is similar, although inside the bundle facet, the album property is set to a non-null value.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/drive/bundles
Content-Type: application/json

{
  "name": "My Day at the Beach",
  "@microsoft.graph.conflictBehavior" : "rename",
  "bundle": { "album": {} },
  "children": [
    { "id": "1234asdf" }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new DriveItem
{
	Name = "My Day at the Beach",
	Bundle = new Bundle
	{
		Album = new Album
		{
		},
	},
	Children = new List<DriveItem>
	{
		new DriveItem
		{
			Id = "1234asdf",
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@microsoft.graph.conflictBehavior" , "rename"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Bundles.PostAsync(requestBody);
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

requestBody := graphmodels.NewDriveItem()
name := "My Day at the Beach"
requestBody.SetName(&name) 
bundle := graphmodels.NewBundle()
album := graphmodels.NewAlbum()
bundle.SetAlbum(album)
requestBody.SetBundle(bundle)


driveItem := graphmodels.NewDriveItem()
id := "1234asdf"
driveItem.SetId(&id) 

children := []graphmodels.DriveItemable {
	driveItem,
}
requestBody.SetChildren(children)
additionalData := map[string]interface{}{
	"@microsoft.graph.conflictBehavior" : "rename", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bundles, err := graphClient.Drives().ByDriveId("drive-id").Bundles().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DriveItem driveItem = new DriveItem();
driveItem.setName("My Day at the Beach");
Bundle bundle = new Bundle();
Album album = new Album();
bundle.setAlbum(album);
driveItem.setBundle(bundle);
LinkedList<DriveItem> children = new LinkedList<DriveItem>();
DriveItem driveItem1 = new DriveItem();
driveItem1.setId("1234asdf");
children.add(driveItem1);
driveItem.setChildren(children);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@microsoft.graph.conflictBehavior", "rename");
driveItem.setAdditionalData(additionalData);
DriveItem result = graphClient.drives().byDriveId("{drive-id}").bundles().post(driveItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const driveItem = {
  name: 'My Day at the Beach',
  '@microsoft.graph.conflictBehavior': 'rename',
  bundle: { album: {} },
  children: [
    { id: '1234asdf' }
  ]
};

await client.api('/drive/bundles')
	.post(driveItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\DriveItem;
use Microsoft\Graph\Generated\Models\Bundle;
use Microsoft\Graph\Generated\Models\Album;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DriveItem();
$requestBody->setName('My Day at the Beach');
$bundle = new Bundle();
$bundleAlbum = new Album();
$bundle->setAlbum($bundleAlbum);
$requestBody->setBundle($bundle);
$childrenDriveItem1 = new DriveItem();
$childrenDriveItem1->setId('1234asdf');
$childrenArray []= $childrenDriveItem1;
$requestBody->setChildren($childrenArray);

$additionalData = [
'@microsoft.graph.conflictBehavior' => 'rename',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->bundles()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	name = "My Day at the Beach"
	"@microsoft.graph.conflictBehavior" = "rename"
	bundle = @{
		album = @{
		}
	}
	children = @(
		@{
			id = "1234asdf"
		}
	)
}

New-MgDriveBundle -DriveId $driveId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.drive_item import DriveItem
from msgraph.generated.models.bundle import Bundle
from msgraph.generated.models.album import Album
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DriveItem(
	name = "My Day at the Beach",
	bundle = Bundle(
		album = Album(
		),
	),
	children = [
		DriveItem(
			id = "1234asdf",
		),
	],
	additional_data = {
			"@microsoft_graph_conflict_behavior" : "rename",
	}
)

result = await graph_client.drives.by_drive_id('drive-id').bundles.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "1234321!abc",
  "name": "Just some files",
  "bundle": {
    "childCount": 2,
    "album": { }
 }
}
```

The response object shown here might be shortened for readability.

If *@microsoft.graph.conflictBehavior* is set to **rename** and a bundle with the same name already exists, the new bundle name will be updated to be unique. OneDrive will append a number to the end of the bundle name.

For example, `My Day at the Beach` would be renamed `My Day at the Beach 1`. If `My Day at the Beach 1` is taken, then the number would be incremented again until a unique bundle name is discovered.
