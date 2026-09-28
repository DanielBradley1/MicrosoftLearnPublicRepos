<!-- Source: https://learn.microsoft.com/en-us/graph/api/site-post-permissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create permission

Namespace: microsoft.graph

Create a new [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object on a site.

> **Note:** You can only use this method to create a new application permission; you can't use it to create a new user site permission.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(work or school account\) | Sites.FullControl.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |

> **Note:** In delegated workflows, the user must have an administrator role, such as SharePoint Administrator or higher.

## HTTP request

```http
POST /sites/{sitesId}/permissions
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

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/sites/{sitesId}/permissions
Content-Type: application/json

{
  "roles": ["write"],
  "grantedToIdentities": [{
    "application": {
      "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
      "displayName": "Contoso Time Manager App"
    }
  }]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Permission
{
	Roles = new List<string>
	{
		"write",
	},
	GrantedToIdentities = new List<IdentitySet>
	{
		new IdentitySet
		{
			Application = new Identity
			{
				Id = "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
				DisplayName = "Contoso Time Manager App",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Permissions.PostAsync(requestBody);
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
roles := []string {
	"write",
}
requestBody.SetRoles(roles)


identitySet := graphmodels.NewIdentitySet()
application := graphmodels.NewIdentity()
id := "89ea5c94-7736-4e25-95ad-3fa95f62b66e"
application.SetId(&id) 
displayName := "Contoso Time Manager App"
application.SetDisplayName(&displayName) 
identitySet.SetApplication(application)

grantedToIdentities := []graphmodels.IdentitySetable {
	identitySet,
}
requestBody.SetGrantedToIdentities(grantedToIdentities)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissions, err := graphClient.Sites().BySiteId("site-id").Permissions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Permission permission = new Permission();
LinkedList<String> roles = new LinkedList<String>();
roles.add("write");
permission.setRoles(roles);
LinkedList<IdentitySet> grantedToIdentities = new LinkedList<IdentitySet>();
IdentitySet identitySet = new IdentitySet();
Identity application = new Identity();
application.setId("89ea5c94-7736-4e25-95ad-3fa95f62b66e");
application.setDisplayName("Contoso Time Manager App");
identitySet.setApplication(application);
grantedToIdentities.add(identitySet);
permission.setGrantedToIdentities(grantedToIdentities);
Permission result = graphClient.sites().bySiteId("{site-id}").permissions().post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  roles: ['write'],
  grantedToIdentities: [{
    application: {
      id: '89ea5c94-7736-4e25-95ad-3fa95f62b66e',
      displayName: 'Contoso Time Manager App'
    }
  }]
};

await client.api('/sites/{siteId}/permissions')
	.post(permission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Permission;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Permission();
$requestBody->setRoles(['write', 	]);
$grantedToIdentitiesIdentitySet1 = new IdentitySet();
$grantedToIdentitiesIdentitySet1Application = new Identity();
$grantedToIdentitiesIdentitySet1Application->setId('89ea5c94-7736-4e25-95ad-3fa95f62b66e');
$grantedToIdentitiesIdentitySet1Application->setDisplayName('Contoso Time Manager App');
$grantedToIdentitiesIdentitySet1->setApplication($grantedToIdentitiesIdentitySet1Application);
$grantedToIdentitiesArray []= $grantedToIdentitiesIdentitySet1;
$requestBody->setGrantedToIdentities($grantedToIdentitiesArray);


$result = $graphServiceClient->sites()->bySiteId('site-id')->permissions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	roles = @(
	"write"
)
grantedToIdentities = @(
	@{
		application = @{
			id = "89ea5c94-7736-4e25-95ad-3fa95f62b66e"
			displayName = "Contoso Time Manager App"
		}
	}
)
}

New-MgSitePermission -SiteId $siteId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.permission import Permission
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Permission(
	roles = [
		"write",
	],
	granted_to_identities = [
		IdentitySet(
			application = Identity(
				id = "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
				display_name = "Contoso Time Manager App",
			),
		),
	],
)

result = await graph_client.sites.by_site_id('site-id').permissions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "id": "1",
    "@deprecated.GrantedToIdentities": "GrantedToIdentities has been deprecated. Refer to GrantedToIdentitiesV2",
    "roles": ["write"],
    "grantedToIdentities": [{
      "application": {
        "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
        "displayName": "Contoso Time Manager App"
      }
    }],
    "grantedToIdentitiesV2": [{
      "application": {
        "id": "89ea5c94-7736-4e25-95ad-3fa95f62b66e",
        "displayName": "Contoso Time Manager App"
      }
    }]
}
```
