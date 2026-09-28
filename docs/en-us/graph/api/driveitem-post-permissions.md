<!-- Source: https://learn.microsoft.com/en-us/graph/api/driveitem-post-permissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create permission on a driveItem

Namespace: microsoft.graph

Create a new [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

Important

This API has the following restrictions:

- For OneDrive for work or school and SharePoint Online, you can only use this method to create a new application permission. If you want to create a new user permission in a **driveItem**, see [invite](https://learn.microsoft.com/en-us/graph/api/driveitem-invite?view=graph-rest-1.0). For more information on application permissions, see [Overview of selected permissions in OneDrive and SharePoint](https://learn.microsoft.com/en-us/graph/permissions-selected-overview).
- For SharePoint Embedded, you can only use this method to create a new [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) permission with app-only access. You can't create a permission on the root item of a container.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Files.ReadWrite.All, Files.SelectedOperations.Selected, Sites.ReadWrite.All, Sites.FullControl.All, Sites.Manage.All, Sites.Selected, Lists.SelectedOperations.Selected, ListItems.SelectedOperations.Selected |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Files.ReadWrite.All |
| Application | Files.ReadWrite.All | Sites.FullControl.All, Sites.Manage.All, Sites.ReadWrite.All, Sites.Selected, Files.SelectedOperations.Selected, Lists.SelectedOperations.Selected, ListItems.SelectedOperations.Selected |

Note

SharePoint Embedded requires the `FileStorageContainer.Selected` permission to access the content of the container. This permission is different from the ones mentioned previously. In addition to Microsoft Graph permissions, your app must have the necessary [container type permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#container-type-application-permissions) to call this API. For more information, see [SharePoint Embedded authentication and authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth).

## HTTP request

```http
POST /drives/{drive-id}/items/{item-id}/permissions
POST /groups/{group-id}/drive/items/{item-id}/permissions
POST /me/drive/items/{item-id}/permissions
POST /sites/{siteId}/drive/items/{itemId}/permissions
POST /users/{userId}/drive/items/{itemId}/permissions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object.

Important

- This API only accepts **grantedToV2** as input for the **permission** object. Other properties such as **grantedToIdentitiesV2** or the deprecated **grantedTo** and **grantedToIdentities** aren't accepted.
- For SharePoint Embedded, when you create a new [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) permission, we recommend that you reference the **sharePointGroup** using the **grantedToV2.sharePointGroup.id** property in the request body. This **id** should map to the **id** of the **sharePointGroup** property. For more information, see [Example 2](#example-2-add-a-sharepoint-group-permission-to-a-driveitem-in-a-sharepoint-embedded-container-using-its-id). We don't recommend that you reference a **sharePointGroup** using its **principalId** because the **principalId** is only unique within the site, unlike the **id** of the **sharePointGroup**, which is globally unique. In that case, the request body must include both **id** and **displayName** in the **grantedToV2.siteGroup** property. The **id** must point to the **principalId** of the **sharePointGroup** and the **displayName** must point to the **title** of the **sharePointGroup**. For more information, see [Example 3](#example-3-add-a-sharepoint-group-permission-to-a-driveitem-in-a-sharepoint-embedded-container-using-the-principalid).

## Response

If successful, this method returns a `201 Created` response code and a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Add an application permission to a driveItem in OneDrive or SharePoint Online

The following example shows how to add a `write` [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) for the `Contoso Time Manager App` [application](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) identified by `89ea5c94-7736-4e25-95ad-3fa95f62b66e`, on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) identified by `01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU` in a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) identified by `b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop`.

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
POST https://graph.microsoft.com/v1.0/drives/b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop/items/01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU/permissions
Content-Type: application/json

{
  "grantedToV2": {
    "application": {
      "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e"
    }
  },
  "roles": ["write"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Permission
{
	GrantedToV2 = new SharePointIdentitySet
	{
		Application = new Identity
		{
			Id = "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
		},
	},
	Roles = new List<string>
	{
		"write",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Permissions.PostAsync(requestBody);
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

requestBody := graphmodels.NewPermission()
grantedToV2 := graphmodels.NewSharePointIdentitySet()
application := graphmodels.NewIdentity()
id := "89ea5c94-7736-4e25-95ad-3fa95f62b66e"
application.SetId(&id) 
grantedToV2.SetApplication(application)
requestBody.SetGrantedToV2(grantedToV2)
roles := []string {
	"write",
}
requestBody.SetRoles(roles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissions, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Permissions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Permission permission = new Permission();
SharePointIdentitySet grantedToV2 = new SharePointIdentitySet();
Identity application = new Identity();
application.setId("89ea5c94-7736-4e25-95ad-3fa95f62b66e");
grantedToV2.setApplication(application);
permission.setGrantedToV2(grantedToV2);
LinkedList<String> roles = new LinkedList<String>();
roles.add("write");
permission.setRoles(roles);
Permission result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").permissions().post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  grantedToV2: {
    application: {
      id: '89ea5c94-7736-4e25-95ad-3fa95f62b66e'
    }
  },
  roles: ['write']
};

await client.api('/drives/b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop/items/01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU/permissions')
	.post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Permission;
use Microsoft\Graph\Generated\Models\SharePointIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Permission();
$grantedToV2 = new SharePointIdentitySet();
$grantedToV2Application = new Identity();
$grantedToV2Application->setId('89ea5c94-7736-4e25-95ad-3fa95f62b66e');
$grantedToV2->setApplication($grantedToV2Application);
$requestBody->setGrantedToV2($grantedToV2);
$requestBody->setRoles(['write', 	]);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->permissions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	grantedToV2 = @{
		application = @{
			id = "89ea5c94-7736-4e25-95ad-3fa95f62b66e"
		}
	}
	roles = @(
	"write"
)
}

New-MgDriveItemPermission -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.permission import Permission
from msgraph.generated.models.share_point_identity_set import SharePointIdentitySet
from msgraph.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Permission(
	granted_to_v2 = SharePointIdentitySet(
		application = Identity(
			id = "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
		),
	),
	roles = [
		"write",
	],
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').permissions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "aTowaS50fG1zLnNwLmV4dHw4OWVhNWM5NC03NzM2LTRlMjUtOTVhZC0zZmE5NWY2MmI2NmVAZDljZTBmYzEtNjFkOC00YTJlLWI1ZDMtMTg3NzBkZjA2NzJj",
  "roles": [
    "write"
  ],
  "grantedTo": {
    "application": {
      "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
      "displayName": "Contoso Time Manager App"
    }
  },
  "grantedToV2": {
    "application": {
      "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
      "displayName": "Contoso Time Manager App"
    }
  }
}
```

### Example 2: Add a SharePoint group permission to a driveItem in a SharePoint Embedded container using its ID

The following example shows how to add a `write` [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) for the `internal collaborators` [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) identified by `01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU` in a SharePoint Embedded [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) identified by `b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop`.

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
POST https://graph.microsoft.com/v1.0/drives/b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop/items/01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU/permissions
Content-Type: application/json

{
  "grantedToV2": {
    "sharePointGroup": {
      "id": "ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0"
    }
  },
  "roles": ["write"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Permission
{
	GrantedToV2 = new SharePointIdentitySet
	{
		SharePointGroup = new SharePointGroupIdentity
		{
			Id = "ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0",
		},
	},
	Roles = new List<string>
	{
		"write",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Permissions.PostAsync(requestBody);
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

requestBody := graphmodels.NewPermission()
grantedToV2 := graphmodels.NewSharePointIdentitySet()
sharePointGroup := graphmodels.NewSharePointGroupIdentity()
id := "ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0"
sharePointGroup.SetId(&id) 
grantedToV2.SetSharePointGroup(sharePointGroup)
requestBody.SetGrantedToV2(grantedToV2)
roles := []string {
	"write",
}
requestBody.SetRoles(roles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissions, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Permissions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Permission permission = new Permission();
SharePointIdentitySet grantedToV2 = new SharePointIdentitySet();
SharePointGroupIdentity sharePointGroup = new SharePointGroupIdentity();
sharePointGroup.setId("ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0");
grantedToV2.setSharePointGroup(sharePointGroup);
permission.setGrantedToV2(grantedToV2);
LinkedList<String> roles = new LinkedList<String>();
roles.add("write");
permission.setRoles(roles);
Permission result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").permissions().post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  grantedToV2: {
    sharePointGroup: {
      id: 'ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0'
    }
  },
  roles: ['write']
};

await client.api('/drives/b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop/items/01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU/permissions')
	.post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Permission;
use Microsoft\Graph\Generated\Models\SharePointIdentitySet;
use Microsoft\Graph\Generated\Models\SharePointGroupIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Permission();
$grantedToV2 = new SharePointIdentitySet();
$grantedToV2SharePointGroup = new SharePointGroupIdentity();
$grantedToV2SharePointGroup->setId('ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0');
$grantedToV2->setSharePointGroup($grantedToV2SharePointGroup);
$requestBody->setGrantedToV2($grantedToV2);
$requestBody->setRoles(['write', 	]);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->permissions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	grantedToV2 = @{
		sharePointGroup = @{
			id = "ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0"
		}
	}
	roles = @(
	"write"
)
}

New-MgDriveItemPermission -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.permission import Permission
from msgraph.generated.models.share_point_identity_set import SharePointIdentitySet
from msgraph.generated.models.share_point_group_identity import SharePointGroupIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Permission(
	granted_to_v2 = SharePointIdentitySet(
		share_point_group = SharePointGroupIdentity(
			id = "ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0",
		),
	),
	roles = [
		"write",
	],
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').permissions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "aTowaS50fG1zLnNwLmV4dHwxMEBkOWNlMGZjMS02MWQ4LTRhMmUtYjVkMy0xODc3MGRmMDY3MmM=",
  "roles": [
    "write"
  ],
  "grantedToV2": {
    "sharePointGroup": {
      "id": "ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0",
      "principalId": "10",
      "title": "Internal Collaborators"
    },
    "siteGroup": {
      "id": "10",
      "displayName": "Internal Collaborators"
    }
  },
  "grantedTo": {
    "siteGroup": {
      "id": "10",
      "displayName": "Internal Collaborators"
    }
  }
}
```

### Example 3: Add a SharePoint group permission to a driveItem in a SharePoint Embedded container using the principalId

The following example shows how to add a `write` [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) for the `internal collaborators` [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0) on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) identified by `01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU` in a SharePoint Embedded [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) identified by `b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop`.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/drives/b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop/items/01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU/permissions
Content-Type: application/json

{
  "grantedToV2": {
    "siteGroup": {
      "id": "10",
      "displayName": "Internal Collaborators"
    }
  },
  "roles": ["write"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Permission
{
	GrantedToV2 = new SharePointIdentitySet
	{
		SiteGroup = new SharePointIdentity
		{
			Id = "10",
			DisplayName = "Internal Collaborators",
		},
	},
	Roles = new List<string>
	{
		"write",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Permissions.PostAsync(requestBody);
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

requestBody := graphmodels.NewPermission()
grantedToV2 := graphmodels.NewSharePointIdentitySet()
siteGroup := graphmodels.NewSharePointIdentity()
id := "10"
siteGroup.SetId(&id) 
displayName := "Internal Collaborators"
siteGroup.SetDisplayName(&displayName) 
grantedToV2.SetSiteGroup(siteGroup)
requestBody.SetGrantedToV2(grantedToV2)
roles := []string {
	"write",
}
requestBody.SetRoles(roles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissions, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Permissions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Permission permission = new Permission();
SharePointIdentitySet grantedToV2 = new SharePointIdentitySet();
SharePointIdentity siteGroup = new SharePointIdentity();
siteGroup.setId("10");
siteGroup.setDisplayName("Internal Collaborators");
grantedToV2.setSiteGroup(siteGroup);
permission.setGrantedToV2(grantedToV2);
LinkedList<String> roles = new LinkedList<String>();
roles.add("write");
permission.setRoles(roles);
Permission result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").permissions().post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  grantedToV2: {
    siteGroup: {
      id: '10',
      displayName: 'Internal Collaborators'
    }
  },
  roles: ['write']
};

await client.api('/drives/b!s8RqPCGh0ESQS2EYnKM0IKS3lM7GxjdAviiob7oc5pXv_0LiL-62Qq3IXyrXnEop/items/01V4EPHZNV2OJQJNBPWNCKDTXCQ5TSVBJU/permissions')
	.post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Permission;
use Microsoft\Graph\Generated\Models\SharePointIdentitySet;
use Microsoft\Graph\Generated\Models\SharePointIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Permission();
$grantedToV2 = new SharePointIdentitySet();
$grantedToV2SiteGroup = new SharePointIdentity();
$grantedToV2SiteGroup->setId('10');
$grantedToV2SiteGroup->setDisplayName('Internal Collaborators');
$grantedToV2->setSiteGroup($grantedToV2SiteGroup);
$requestBody->setGrantedToV2($grantedToV2);
$requestBody->setRoles(['write', 	]);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->permissions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = @{
	grantedToV2 = @{
		siteGroup = @{
			id = "10"
			displayName = "Internal Collaborators"
		}
	}
	roles = @(
	"write"
)
}

New-MgDriveItemPermission -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.permission import Permission
from msgraph.generated.models.share_point_identity_set import SharePointIdentitySet
from msgraph.generated.models.share_point_identity import SharePointIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Permission(
	granted_to_v2 = SharePointIdentitySet(
		site_group = SharePointIdentity(
			id = "10",
			display_name = "Internal Collaborators",
		),
	),
	roles = [
		"write",
	],
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').permissions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "aTowaS50fG1zLnNwLmV4dHwxMEBkOWNlMGZjMS02MWQ4LTRhMmUtYjVkMy0xODc3MGRmMDY3MmM=",
  "roles": [
    "write"
  ],
  "grantedToV2": {
    "siteGroup": {
      "id": "10",
      "displayName": "Internal Collaborators"
    }
  },
  "grantedTo": {
    "siteGroup": {
      "id": "10",
      "displayName": "Internal Collaborators"
    }
  }
}
```
