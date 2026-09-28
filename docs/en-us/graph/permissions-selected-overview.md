<!-- Source: https://learn.microsoft.com/en-us/graph/permissions-selected-overview -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Overview of Selected permissions in OneDrive and SharePoint

SharePoint and OneDrive have a long-established permissions model that doesn't fit exactly into the scopes model. For example, a global scope that provides ReadWrite access to a single list in your tenant doesn't exist. Instead, Selected scopes support these scenarios. Initially, Sites.Selected existed to restrict an application's access to a single site collection. Now, lists, list items, folders, and files are also supported, and all Selected scopes now support delegated and application modes.

Note

Due to the evolution of scope naming requirements, newer scopes are listed as a full tuple `*.SelectedOperations.Selected`. There is no functional difference between this format and the `Sites.Selected` format.

## Scopes

The following table lists the Selected permission scopes.

| Scopes | Description |
| --- | --- |
| Sites.Selected | Manages application access at the site collection level, providing access to a specific site collection |
| Lists.SelectedOperations.Selected | Manages application access at the list level, providing access to a specific list |
| ListItems.SelectedOperations.Selected | Manages application access at the files, list item, or folder level, providing access to one or more list items |
| Files.SelectedOperations.Selected | Manages application access at the file or library folder level, providing access to one or more files |

## How Selected scopes work with SharePoint and OneDrive permissions

When an administrator consents to Selected scopes for an application, they're delegating management of resource permissions to the owners of that resource within the workload. For other scopes, such as Files.Read.All, as soon as the scope is consented, the application can access the resources it represents. Selected scopes require an explicit assignment action; an application consented for Lists.SelectedOperations.Selected would initially have no access.

Selected scopes require a series of steps to work, which provides several means of control for administrators. The following example uses the `Lists.SelectedOperations.Selected` scope, but the steps apply to all \*.Selected scopes.

1. The application must be consented in Entra ID to have either the application or delegated `Lists.SelectedOperations.Selected` scope.
2. The application must be granted permissions to a list via a call to `POST /sites/{siteid}/lists/{listid}/permissions` with a specific role.
3. The application must acquire a valid token that contains the `Lists.SelectedOperations.Selected` scope for calls to the permissioned list.

If any of the three steps are missed, the application doesn't have access. Administrators two points of control:

- Remove the permissions on a specific list via a call to `DELETE /sites/{siteid}/lists/{listid}/permissions/{id}`, which removes access to the list for that application.
- Revoke the `Lists.SelectedOperations.Selected` scope consent in Entra ID, which blocks the application from access to any list to which it was previously granted permissions.

Based on this, you can consent an application the `Lists.SelectedOperations.Selected` scope in Entra ID, but not grant permissions to any list - which means the application doesn't have access. Likewise, you can call `POST /sites/{siteid}/lists/{listid}/permissions` for any application, but without the proper scopes appearing in the token, the application doesn't have access. All three steps must be completed to ensure the expected access. This applies as well for the other \*.Selected scopes and their respective levels.

Note

Assigning application permissions to lists, list items, folders, or files breaks inheritance on the assigned resource, so be mindful of [service limits for unique permissions](https://learn.microsoft.com/en-us/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits#unique-security-scopes-per-list-or-library) in your solution design. Permissions at the site collection level do not break inheritance because this is the root of permission inheritance.

An example of setting permissions is shown for [sites](https://learn.microsoft.com/en-us/graph/api/site-post-permissions); the logic is similar for [lists](https://learn.microsoft.com/en-us/graph/api/list-post-permissions), [list items](https://learn.microsoft.com/en-us/graph/api/listitem-post-permissions), [files](https://learn.microsoft.com/en-us/graph/api/driveitem-post-permissions), or [folders](https://learn.microsoft.com/en-us/graph/api/listitem-post-permissions).

### What's the difference between files and listItems scopes?

Within SharePoint, all files are list items, but all list items are not files. As a result, applications that carry the `ListItems.SelectedOperations.Selected` scope can access and operate on all list items and files up to their allowed role. Applications with `Files.SelectedOperations.Selected` can only operate on files \(list items\) within document libraries or other lists marked as containing documents. This mimics the Files.Read.All and Files.ReadWrite.All behavior that exists today, but isolated to a single file. This behavior doesn't change based on the Microsoft Graph path used such as with `/drives/{driveid}/items/{itemid}` and `/sites/{siteid}/lists/{listid}/items/{itemid}`; rather, the destination to be accessed controls the behavior.

### Roles

The following table lists the four roles that can be assigned to an application for a given resource.

| Role | Description |
| --- | --- |
| read | Read the metadata and contents of the resource. |
| write | Read and modify the metadata and contents of the resource. |
| owner | Represents the owner role. |
| fullcontrol | Represents full control of the resource. |

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
POST https://graph.microsoft.com/v1.0/sites/{siteId}/permissions
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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

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

For examples that show how to manage permissions, see the `/permissions` API topics for [site](https://learn.microsoft.com/en-us/graph/api/site-post-permissions), [list](https://learn.microsoft.com/en-us/graph/api/list-post-permissions), [listItem](https://learn.microsoft.com/en-us/graph/api/listitem-post-permissions), and [driveItem](https://learn.microsoft.com/en-us/graph/api/driveitem-post-permissions).

### What permissions do I need to manage permissions?

The permission requirements vary by level. In all delegated, cases the current user also needs sufficient permissions to manage access by calling the API. The following table includes scopes and scopes + assigned roles to the parent resource. For example, if you have the Sites.Selected scope AND FullControl role \(Sites.Selected+FullControl\), you can manage resources within that site collection.

| Resource | Required resource permissions | Notes |
| --- | --- | --- |
| site | Sites.FullControl.All | Because you can grant full control permissions to a site collection by using Sites.Selected, this requirement is necessarily high. |
| list | Sites.FullControl.All, Sites.Selected+FullControl, Sites.Selected+Owner |  |
| listItem | Sites.FullControl.All, Sites.Selected+FullControl, Sites.Selected+Owner, Lists.SelectedOperations.Selected+FullControl, Lists.SelectedOperations.Selected+Owner |  |
| file | Sites.FullControl.All, Sites.Selected+FullControl, Sites.Selected+Owner, Lists.SelectedOperations.Selected+FullControl, Lists.SelectedOperations.Selected+Owner |  |

### How access is calculated

There are two types of tokens: application only and delegated. Application only scenarios have no user present and are considered higher risk. With delegated, the application can never exceed the current user's existing permissions and can be considered lower-risk for many scenarios. Delegated is preferred when possible, but both modes are available to meet your needs.

A tuple of application ID, resource ID, and role is stored. As such, the \[application\] has \[role\] access to the \[resource\]. You specify the application and role when a permission is created through the API, and the resolved path gives you the resource. For example, application Z has read access to the list at /sites/dev/lists/list1.

To calculate access, use the values provided in the token to roughly follow this flow:

1. Review token type \(application or delegated\).
2. Find the application record for the supplied application ID on the resource or a securable hierarchical parent \(inheritance\).
3. One of the following occurs:

   - For application access, if a record is found for the application, and the role allows for the operation requested \(read an item, update a list\), access is granted.
   - In the delegated scenario, both the application and user permissions are calculated and then intersected, which means that the application can never exceed the user's permissions, and the user can never exceed \(through the application\) the consented application permissions.

### Consent behavior notes

The following notes apply to consent behavior:

- Applications can have multiple Selected consents and those consents can apply at various levels across the tenant.
- Application access is lost as soon as a scope is revoked. If an application has Lists.\* and Sites.\* and is given access to a site collection and a specific list in that site collection, and then the Sites.\* consent is revoked, the application maintains access to the list it was given specific access to via the Lists.\* consent and the previous call to `list/permissions`.
- If an application has permissions to a list via a call to `list/permissions`, and the access is removed via a call to `DELETE lists/permissions/id`, it loses access to that list and all items within that list, regardless of any explicit permissions set on those list items. You can later regrant specific item permissions if needed.
- Higher-level scopes such as Sites.\* can be used to grant file-specific permissions, but lower scopes can never provide access to higher-level resources. This allows applications to have access at a specific level.
- Consent is an external concept, consumed by OneDrive and SharePoint through the provided token, and any scopes presented in the token are honored.
