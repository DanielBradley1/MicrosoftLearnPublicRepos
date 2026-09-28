<!-- Source: https://learn.microsoft.com/en-us/graph/api/listitem-post-permissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Create permission on a listItem

Namespace: microsoft.graph

Create a new [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object on a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0).

> **Note:** You can only use this method to create a new application permission; you can't use it to create a new **listItem** permission for a user.

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
POST /sites/{site-id}/lists/{list-id}/items/{item-id}/permissions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/sites/contoso.sharepoint.com,48f1898f-77d9-4a1b-bddc-1f49bb6dc134,7206fc09-e4af-48b3-8730-ed7321396d7a/lists/44ca0d29-33d3-47c9-8f12-eb0c46e3c7ad/items/1/permissions
Content-Type: application/json

{
  "grantedToV2": {
    "application": {
      "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
      "displayName": "Contoso Time Manager App"
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
			DisplayName = "Contoso Time Manager App",
		},
	},
	Roles = new List<string>
	{
		"write",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Lists["{list-id}"].Items["{listItem-id}"].Permissions.PostAsync(requestBody);
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
displayName := "Contoso Time Manager App"
application.SetDisplayName(&displayName) 
grantedToV2.SetApplication(application)
requestBody.SetGrantedToV2(grantedToV2)
roles := []string {
	"write",
}
requestBody.SetRoles(roles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissions, err := graphClient.Sites().BySiteId("site-id").Lists().ByListId("list-id").Items().ByListItemId("listItem-id").Permissions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Permission permission = new Permission();
SharePointIdentitySet grantedToV2 = new SharePointIdentitySet();
Identity application = new Identity();
application.setId("89ea5c94-7736-4e25-95ad-3fa95f62b66e");
application.setDisplayName("Contoso Time Manager App");
grantedToV2.setApplication(application);
permission.setGrantedToV2(grantedToV2);
LinkedList<String> roles = new LinkedList<String>();
roles.add("write");
permission.setRoles(roles);
Permission result = graphClient.sites().bySiteId("{site-id}").lists().byListId("{list-id}").items().byListItemId("{listItem-id}").permissions().post(permission);
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
      id: '89ea5c94-7736-4e25-95ad-3fa95f62b66e',
      displayName: 'Contoso Time Manager App'
    }
  },
  roles: ['write']
};

await client.api('/sites/contoso.sharepoint.com,48f1898f-77d9-4a1b-bddc-1f49bb6dc134,7206fc09-e4af-48b3-8730-ed7321396d7a/lists/44ca0d29-33d3-47c9-8f12-eb0c46e3c7ad/items/1/permissions')
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
$grantedToV2Application->setDisplayName('Contoso Time Manager App');
$grantedToV2->setApplication($grantedToV2Application);
$requestBody->setGrantedToV2($grantedToV2);
$requestBody->setRoles(['write', 	]);

$result = $graphServiceClient->sites()->bySiteId('site-id')->lists()->byListId('list-id')->items()->byListItemId('listItem-id')->permissions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	grantedToV2 = @{
		application = @{
			id = "89ea5c94-7736-4e25-95ad-3fa95f62b66e"
			displayName = "Contoso Time Manager App"
		}
	}
	roles = @(
	"write"
)
}

New-MgSiteListItemPermission -SiteId $siteId -ListId $listId -ListItemId $listItemId -BodyParameter $params
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
			display_name = "Contoso Time Manager App",
		),
	),
	roles = [
		"write",
	],
)

result = await graph_client.sites.by_site_id('site-id').lists.by_list_id('list-id').items.by_list_item_id('listItem-id').permissions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#sites('contoso.sharepoint.com%2C48f1898f-77d9-4a1b-bddc-1f49bb6dc134%2C7206fc09-e4af-48b3-8730-ed7321396d7a')/lists('44ca0d29-33d3-47c9-8f12-eb0c46e3c7ad')/items('1')/permissions/$entity",
  "id": "2",
  "roles": ["write"],
  "grantedToV2": {
    "application": {
      "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
      "displayName": "Contoso Time Manager App"
    }
  }
}
```
