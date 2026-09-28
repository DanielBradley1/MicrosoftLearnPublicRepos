<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackage-post-resourcerolescopes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Create resourceRoleScope

Namespace: microsoft.graph

Create a new [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) for adding a resource role to an access package. The access package resource, for a group, an app, or a SharePoint Online site, must already exist in the access package catalog, and the **originId** for the resource role retrieved from the [list of the resource roles](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resourceroles?view=graph-rest-1.0). Once you add the resource role scope to the access package, the user will receive this resource role through any current and future access package assignments.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EntitlementManagement.ReadWrite.All | Not available. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged roles are:

  - *Access package manager*. **This is the least privileged option**
  - Catalog owner

- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Access package manager* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/accessPackages/{id}/resourceRoleScopes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) object. Include in the object the relationships to an [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) object and an [accessPackageResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-1.0) object, which can be obtained from a request to [list access package resources a catalog](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resourceroles?view=graph-rest-1.0), with `$expand=roles,scopes`.

## Response

If successful, this method returns a 200-series response code and a new [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Add a SharePoint Online site role to an access package

#### Request

The following example shows a request adding a SharePoint Online site role to an access package's list of resource roles. The access package resource for the site must already have been added to the access package catalog containing this access package.

The request contains an [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) object. Each type of resource defines the format of the originId field in a resource role. For a SharePoint Online site, the originId will be the sequence number of the role in the site. The resource role can be obtained from a request to [retrieve the roles of a resource for a SharePoint Online site collection](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resourceroles?view=graph-rest-1.0#example-2-retrieving-the-roles-of-a-resource-for-a-sharepoint-online-site-collection).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages/{id}/resourceRoleScopes
Content-type: application/json

{
    "role": {
        "displayName": "Contributors",
        "originSystem": "SharePointOnline",
        "originId": "4",
        "resource": {
            "id": "53c71803-a0a8-4777-aecc-075de8ee3991"
        }
    },
    "scope": {
        "displayName": "Root",
        "description": "Root Scope",
        "originId": "https://contoso.sharepoint.com/portals/Community",
        "originSystem": "SharePointOnline",
        "isRootScope": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	Role = new AccessPackageResourceRole
	{
		DisplayName = "Contributors",
		OriginSystem = "SharePointOnline",
		OriginId = "4",
		Resource = new AccessPackageResource
		{
			Id = "53c71803-a0a8-4777-aecc-075de8ee3991",
		},
	},
	Scope = new AccessPackageResourceScope
	{
		DisplayName = "Root",
		Description = "Root Scope",
		OriginId = "https://contoso.sharepoint.com/portals/Community",
		OriginSystem = "SharePointOnline",
		IsRootScope = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].ResourceRoleScopes.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
role := graphmodels.NewAccessPackageResourceRole()
displayName := "Contributors"
role.SetDisplayName(&displayName) 
originSystem := "SharePointOnline"
role.SetOriginSystem(&originSystem) 
originId := "4"
role.SetOriginId(&originId) 
resource := graphmodels.NewAccessPackageResource()
id := "53c71803-a0a8-4777-aecc-075de8ee3991"
resource.SetId(&id) 
role.SetResource(resource)
requestBody.SetRole(role)
scope := graphmodels.NewAccessPackageResourceScope()
displayName := "Root"
scope.SetDisplayName(&displayName) 
description := "Root Scope"
scope.SetDescription(&description) 
originId := "https://contoso.sharepoint.com/portals/Community"
scope.SetOriginId(&originId) 
originSystem := "SharePointOnline"
scope.SetOriginSystem(&originSystem) 
isRootScope := true
scope.SetIsRootScope(&isRootScope) 
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").ResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole role = new AccessPackageResourceRole();
role.setDisplayName("Contributors");
role.setOriginSystem("SharePointOnline");
role.setOriginId("4");
AccessPackageResource resource = new AccessPackageResource();
resource.setId("53c71803-a0a8-4777-aecc-075de8ee3991");
role.setResource(resource);
accessPackageResourceRoleScope.setRole(role);
AccessPackageResourceScope scope = new AccessPackageResourceScope();
scope.setDisplayName("Root");
scope.setDescription("Root Scope");
scope.setOriginId("https://contoso.sharepoint.com/portals/Community");
scope.setOriginSystem("SharePointOnline");
scope.setIsRootScope(true);
accessPackageResourceRoleScope.setScope(scope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").resourceRoleScopes().post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    role: {
        displayName: 'Contributors',
        originSystem: 'SharePointOnline',
        originId: '4',
        resource: {
            id: '53c71803-a0a8-4777-aecc-075de8ee3991'
        }
    },
    scope: {
        displayName: 'Root',
        description: 'Root Scope',
        originId: 'https://contoso.sharepoint.com/portals/Community',
        originSystem: 'SharePointOnline',
        isRootScope: true
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/{id}/resourceRoleScopes')
	.post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$role = new AccessPackageResourceRole();
$role->setDisplayName('Contributors');
$role->setOriginSystem('SharePointOnline');
$role->setOriginId('4');
$roleResource = new AccessPackageResource();
$roleResource->setId('53c71803-a0a8-4777-aecc-075de8ee3991');
$role->setResource($roleResource);
$requestBody->setRole($role);
$scope = new AccessPackageResourceScope();
$scope->setDisplayName('Root');
$scope->setDescription('Root Scope');
$scope->setOriginId('https://contoso.sharepoint.com/portals/Community');
$scope->setOriginSystem('SharePointOnline');
$scope->setIsRootScope(true);
$requestBody->setScope($scope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->resourceRoleScopes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	role = @{
		displayName = "Contributors"
		originSystem = "SharePointOnline"
		originId = "4"
		resource = @{
			id = "53c71803-a0a8-4777-aecc-075de8ee3991"
		}
	}
	scope = @{
		displayName = "Root"
		description = "Root Scope"
		originId = "https://contoso.sharepoint.com/portals/Community"
		originSystem = "SharePointOnline"
		isRootScope = $true
	}
}

New-MgEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	role = AccessPackageResourceRole(
		display_name = "Contributors",
		origin_system = "SharePointOnline",
		origin_id = "4",
		resource = AccessPackageResource(
			id = "53c71803-a0a8-4777-aecc-075de8ee3991",
		),
	),
	scope = AccessPackageResourceScope(
		display_name = "Root",
		description = "Root Scope",
		origin_id = "https://contoso.sharepoint.com/portals/Community",
		origin_system = "SharePointOnline",
		is_root_scope = True,
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').resource_role_scopes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
   "id": "6646a29e-da03-49f6-bcd9-dec124492de3_5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33",
    "createdDateTime": "2023-06-28T01:19:48.4216782Z"
}
```

### Example 2: Add an application role to an access package

#### Request

The following example shows a request that adds an application's role to an access package's list of resource roles. The access package resource for the application must already be added to the access package catalog that contains this access package. You can get the `role`, `resource`, and `scope` with the [list resources](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resources?view=graph-rest-1.0) method.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages/cdd5f06b-752a-4c9f-97a6-82f4eda6c76d/resourceRoleScopes
Content-type: application/json

{
    "role": {
        "id": "cde82ecb-e461-496b-98fb-4f807c7ca640",
        "displayName": "Standard User",
        "description": "Standard User",
        "originSystem": "AadApplication",
        "originId": "a29a7690-b3c4-4ed5-96c6-f640cde06fb8",
        "resource": {
            "id": "5f80c0c7-a180-4521-b585-18200048a0d8",
            "originId": "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
            "originSystem": "AadApplication"
        }
    },
    "scope": {
        "id": "dbeb8772-9907-4e95-a28e-a8d70dbcda69",
        "originId": "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
        "originSystem": "AadApplication",
        "isRootScope": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	Role = new AccessPackageResourceRole
	{
		Id = "cde82ecb-e461-496b-98fb-4f807c7ca640",
		DisplayName = "Standard User",
		Description = "Standard User",
		OriginSystem = "AadApplication",
		OriginId = "a29a7690-b3c4-4ed5-96c6-f640cde06fb8",
		Resource = new AccessPackageResource
		{
			Id = "5f80c0c7-a180-4521-b585-18200048a0d8",
			OriginId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
			OriginSystem = "AadApplication",
		},
	},
	Scope = new AccessPackageResourceScope
	{
		Id = "dbeb8772-9907-4e95-a28e-a8d70dbcda69",
		OriginId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
		OriginSystem = "AadApplication",
		IsRootScope = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].ResourceRoleScopes.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
role := graphmodels.NewAccessPackageResourceRole()
id := "cde82ecb-e461-496b-98fb-4f807c7ca640"
role.SetId(&id) 
displayName := "Standard User"
role.SetDisplayName(&displayName) 
description := "Standard User"
role.SetDescription(&description) 
originSystem := "AadApplication"
role.SetOriginSystem(&originSystem) 
originId := "a29a7690-b3c4-4ed5-96c6-f640cde06fb8"
role.SetOriginId(&originId) 
resource := graphmodels.NewAccessPackageResource()
id := "5f80c0c7-a180-4521-b585-18200048a0d8"
resource.SetId(&id) 
originId := "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
resource.SetOriginId(&originId) 
originSystem := "AadApplication"
resource.SetOriginSystem(&originSystem) 
role.SetResource(resource)
requestBody.SetRole(role)
scope := graphmodels.NewAccessPackageResourceScope()
id := "dbeb8772-9907-4e95-a28e-a8d70dbcda69"
scope.SetId(&id) 
originId := "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
scope.SetOriginId(&originId) 
originSystem := "AadApplication"
scope.SetOriginSystem(&originSystem) 
isRootScope := true
scope.SetIsRootScope(&isRootScope) 
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").ResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole role = new AccessPackageResourceRole();
role.setId("cde82ecb-e461-496b-98fb-4f807c7ca640");
role.setDisplayName("Standard User");
role.setDescription("Standard User");
role.setOriginSystem("AadApplication");
role.setOriginId("a29a7690-b3c4-4ed5-96c6-f640cde06fb8");
AccessPackageResource resource = new AccessPackageResource();
resource.setId("5f80c0c7-a180-4521-b585-18200048a0d8");
resource.setOriginId("e81d7f57-0840-45e1-894b-f505c1bdcc1f");
resource.setOriginSystem("AadApplication");
role.setResource(resource);
accessPackageResourceRoleScope.setRole(role);
AccessPackageResourceScope scope = new AccessPackageResourceScope();
scope.setId("dbeb8772-9907-4e95-a28e-a8d70dbcda69");
scope.setOriginId("e81d7f57-0840-45e1-894b-f505c1bdcc1f");
scope.setOriginSystem("AadApplication");
scope.setIsRootScope(true);
accessPackageResourceRoleScope.setScope(scope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").resourceRoleScopes().post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    role: {
        id: 'cde82ecb-e461-496b-98fb-4f807c7ca640',
        displayName: 'Standard User',
        description: 'Standard User',
        originSystem: 'AadApplication',
        originId: 'a29a7690-b3c4-4ed5-96c6-f640cde06fb8',
        resource: {
            id: '5f80c0c7-a180-4521-b585-18200048a0d8',
            originId: 'e81d7f57-0840-45e1-894b-f505c1bdcc1f',
            originSystem: 'AadApplication'
        }
    },
    scope: {
        id: 'dbeb8772-9907-4e95-a28e-a8d70dbcda69',
        originId: 'e81d7f57-0840-45e1-894b-f505c1bdcc1f',
        originSystem: 'AadApplication',
        isRootScope: true
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/cdd5f06b-752a-4c9f-97a6-82f4eda6c76d/resourceRoleScopes')
	.post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$role = new AccessPackageResourceRole();
$role->setId('cde82ecb-e461-496b-98fb-4f807c7ca640');
$role->setDisplayName('Standard User');
$role->setDescription('Standard User');
$role->setOriginSystem('AadApplication');
$role->setOriginId('a29a7690-b3c4-4ed5-96c6-f640cde06fb8');
$roleResource = new AccessPackageResource();
$roleResource->setId('5f80c0c7-a180-4521-b585-18200048a0d8');
$roleResource->setOriginId('e81d7f57-0840-45e1-894b-f505c1bdcc1f');
$roleResource->setOriginSystem('AadApplication');
$role->setResource($roleResource);
$requestBody->setRole($role);
$scope = new AccessPackageResourceScope();
$scope->setId('dbeb8772-9907-4e95-a28e-a8d70dbcda69');
$scope->setOriginId('e81d7f57-0840-45e1-894b-f505c1bdcc1f');
$scope->setOriginSystem('AadApplication');
$scope->setIsRootScope(true);
$requestBody->setScope($scope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->resourceRoleScopes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	role = @{
		id = "cde82ecb-e461-496b-98fb-4f807c7ca640"
		displayName = "Standard User"
		description = "Standard User"
		originSystem = "AadApplication"
		originId = "a29a7690-b3c4-4ed5-96c6-f640cde06fb8"
		resource = @{
			id = "5f80c0c7-a180-4521-b585-18200048a0d8"
			originId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
			originSystem = "AadApplication"
		}
	}
	scope = @{
		id = "dbeb8772-9907-4e95-a28e-a8d70dbcda69"
		originId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
		originSystem = "AadApplication"
		isRootScope = $true
	}
}

New-MgEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	role = AccessPackageResourceRole(
		id = "cde82ecb-e461-496b-98fb-4f807c7ca640",
		display_name = "Standard User",
		description = "Standard User",
		origin_system = "AadApplication",
		origin_id = "a29a7690-b3c4-4ed5-96c6-f640cde06fb8",
		resource = AccessPackageResource(
			id = "5f80c0c7-a180-4521-b585-18200048a0d8",
			origin_id = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
			origin_system = "AadApplication",
		),
	),
	scope = AccessPackageResourceScope(
		id = "dbeb8772-9907-4e95-a28e-a8d70dbcda69",
		origin_id = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
		origin_system = "AadApplication",
		is_root_scope = True,
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').resource_role_scopes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
   "id": "cde82ecb-e461-496b-98fb-4f807c7ca640_dbeb8772-9907-4e95-a28e-a8d70dbcda69",
   "createdDateTime": "2023-06-28T01:19:48.4216782Z"
}
```

### Example 3: Add group membership to an access package

#### Request

The following example shows a request that adds membership of a group to an access package's list of resource roles. The access package resource for the group must already be added to the access package catalog that contains this access package. You can get the `resource` and `scope` with the [list of the resources of a catalog](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resources?view=graph-rest-1.0) method. You can get the `role` with the [list of the roles of the resource in the catalog](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resourceroles?view=graph-rest-1.0) method. If the `role` returned from the list of the roles has a zero ID, then don't include an `id` in the `accessPackageResourceRole`.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages/cdd5f06b-752a-4c9f-97a6-82f4eda6c76d/resourceRoleScopes
Content-type: application/json

{
    "role": {
        "displayName": "Member",
        "originSystem": "AadGroup",
        "originId": "Member_0282e19d-bf41-435d-92a4-99bab93af305",
        "resource": {
            "id": "b16e0e71-17b4-4ebd-a3cd-8a468542e418",
            "displayName": "example group",
            "description": "a group whose members are to be assigned via an access package",
            "originId": "0282e19d-bf41-435d-92a4-99bab93af305",
            "originSystem": "AadGroup"
        }
    },
    "scope": {
        "id": "83b3e3e9-c8b3-481b-ad80-53e29d1eda9c",
        "displayName": "Root",
        "description": "Root Scope",
        "originId": "0282e19d-bf41-435d-92a4-99bab93af305",
        "originSystem": "AadGroup",
        "isRootScope": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	Role = new AccessPackageResourceRole
	{
		DisplayName = "Member",
		OriginSystem = "AadGroup",
		OriginId = "Member_0282e19d-bf41-435d-92a4-99bab93af305",
		Resource = new AccessPackageResource
		{
			Id = "b16e0e71-17b4-4ebd-a3cd-8a468542e418",
			DisplayName = "example group",
			Description = "a group whose members are to be assigned via an access package",
			OriginId = "0282e19d-bf41-435d-92a4-99bab93af305",
			OriginSystem = "AadGroup",
		},
	},
	Scope = new AccessPackageResourceScope
	{
		Id = "83b3e3e9-c8b3-481b-ad80-53e29d1eda9c",
		DisplayName = "Root",
		Description = "Root Scope",
		OriginId = "0282e19d-bf41-435d-92a4-99bab93af305",
		OriginSystem = "AadGroup",
		IsRootScope = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].ResourceRoleScopes.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
role := graphmodels.NewAccessPackageResourceRole()
displayName := "Member"
role.SetDisplayName(&displayName) 
originSystem := "AadGroup"
role.SetOriginSystem(&originSystem) 
originId := "Member_0282e19d-bf41-435d-92a4-99bab93af305"
role.SetOriginId(&originId) 
resource := graphmodels.NewAccessPackageResource()
id := "b16e0e71-17b4-4ebd-a3cd-8a468542e418"
resource.SetId(&id) 
displayName := "example group"
resource.SetDisplayName(&displayName) 
description := "a group whose members are to be assigned via an access package"
resource.SetDescription(&description) 
originId := "0282e19d-bf41-435d-92a4-99bab93af305"
resource.SetOriginId(&originId) 
originSystem := "AadGroup"
resource.SetOriginSystem(&originSystem) 
role.SetResource(resource)
requestBody.SetRole(role)
scope := graphmodels.NewAccessPackageResourceScope()
id := "83b3e3e9-c8b3-481b-ad80-53e29d1eda9c"
scope.SetId(&id) 
displayName := "Root"
scope.SetDisplayName(&displayName) 
description := "Root Scope"
scope.SetDescription(&description) 
originId := "0282e19d-bf41-435d-92a4-99bab93af305"
scope.SetOriginId(&originId) 
originSystem := "AadGroup"
scope.SetOriginSystem(&originSystem) 
isRootScope := true
scope.SetIsRootScope(&isRootScope) 
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").ResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole role = new AccessPackageResourceRole();
role.setDisplayName("Member");
role.setOriginSystem("AadGroup");
role.setOriginId("Member_0282e19d-bf41-435d-92a4-99bab93af305");
AccessPackageResource resource = new AccessPackageResource();
resource.setId("b16e0e71-17b4-4ebd-a3cd-8a468542e418");
resource.setDisplayName("example group");
resource.setDescription("a group whose members are to be assigned via an access package");
resource.setOriginId("0282e19d-bf41-435d-92a4-99bab93af305");
resource.setOriginSystem("AadGroup");
role.setResource(resource);
accessPackageResourceRoleScope.setRole(role);
AccessPackageResourceScope scope = new AccessPackageResourceScope();
scope.setId("83b3e3e9-c8b3-481b-ad80-53e29d1eda9c");
scope.setDisplayName("Root");
scope.setDescription("Root Scope");
scope.setOriginId("0282e19d-bf41-435d-92a4-99bab93af305");
scope.setOriginSystem("AadGroup");
scope.setIsRootScope(true);
accessPackageResourceRoleScope.setScope(scope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").resourceRoleScopes().post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    role: {
        displayName: 'Member',
        originSystem: 'AadGroup',
        originId: 'Member_0282e19d-bf41-435d-92a4-99bab93af305',
        resource: {
            id: 'b16e0e71-17b4-4ebd-a3cd-8a468542e418',
            displayName: 'example group',
            description: 'a group whose members are to be assigned via an access package',
            originId: '0282e19d-bf41-435d-92a4-99bab93af305',
            originSystem: 'AadGroup'
        }
    },
    scope: {
        id: '83b3e3e9-c8b3-481b-ad80-53e29d1eda9c',
        displayName: 'Root',
        description: 'Root Scope',
        originId: '0282e19d-bf41-435d-92a4-99bab93af305',
        originSystem: 'AadGroup',
        isRootScope: true
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/cdd5f06b-752a-4c9f-97a6-82f4eda6c76d/resourceRoleScopes')
	.post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$role = new AccessPackageResourceRole();
$role->setDisplayName('Member');
$role->setOriginSystem('AadGroup');
$role->setOriginId('Member_0282e19d-bf41-435d-92a4-99bab93af305');
$roleResource = new AccessPackageResource();
$roleResource->setId('b16e0e71-17b4-4ebd-a3cd-8a468542e418');
$roleResource->setDisplayName('example group');
$roleResource->setDescription('a group whose members are to be assigned via an access package');
$roleResource->setOriginId('0282e19d-bf41-435d-92a4-99bab93af305');
$roleResource->setOriginSystem('AadGroup');
$role->setResource($roleResource);
$requestBody->setRole($role);
$scope = new AccessPackageResourceScope();
$scope->setId('83b3e3e9-c8b3-481b-ad80-53e29d1eda9c');
$scope->setDisplayName('Root');
$scope->setDescription('Root Scope');
$scope->setOriginId('0282e19d-bf41-435d-92a4-99bab93af305');
$scope->setOriginSystem('AadGroup');
$scope->setIsRootScope(true);
$requestBody->setScope($scope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->resourceRoleScopes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	role = @{
		displayName = "Member"
		originSystem = "AadGroup"
		originId = "Member_0282e19d-bf41-435d-92a4-99bab93af305"
		resource = @{
			id = "b16e0e71-17b4-4ebd-a3cd-8a468542e418"
			displayName = "example group"
			description = "a group whose members are to be assigned via an access package"
			originId = "0282e19d-bf41-435d-92a4-99bab93af305"
			originSystem = "AadGroup"
		}
	}
	scope = @{
		id = "83b3e3e9-c8b3-481b-ad80-53e29d1eda9c"
		displayName = "Root"
		description = "Root Scope"
		originId = "0282e19d-bf41-435d-92a4-99bab93af305"
		originSystem = "AadGroup"
		isRootScope = $true
	}
}

New-MgEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	role = AccessPackageResourceRole(
		display_name = "Member",
		origin_system = "AadGroup",
		origin_id = "Member_0282e19d-bf41-435d-92a4-99bab93af305",
		resource = AccessPackageResource(
			id = "b16e0e71-17b4-4ebd-a3cd-8a468542e418",
			display_name = "example group",
			description = "a group whose members are to be assigned via an access package",
			origin_id = "0282e19d-bf41-435d-92a4-99bab93af305",
			origin_system = "AadGroup",
		),
	),
	scope = AccessPackageResourceScope(
		id = "83b3e3e9-c8b3-481b-ad80-53e29d1eda9c",
		display_name = "Root",
		description = "Root Scope",
		origin_id = "0282e19d-bf41-435d-92a4-99bab93af305",
		origin_system = "AadGroup",
		is_root_scope = True,
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').resource_role_scopes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
   "id": "748f8431-c7c6-404d-8564-df67aa8cfc5e_83b3e3e9-c8b3-481b-ad80-53e29d1eda9c",
   "createdDateTime": "2023-06-28T01:19:48.4216782Z"
}
```

### Example 4: Add an Active Subscription scoped to a Resource Group Resource Role to an access package

#### Request

The following example shows a request to add an active Subscription scoped to a Resource Group Resource Role to an access package.

Before this request, you must have already added the access package resource `b09a0288-a83e-4ae6-8a53-bc09aeb966ea` for the Subscription `828b526f-c769-4b19-9797-734b4843b978` to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-resourcerequests?view=graph-rest-1.0).

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/resourceRoleScopes
Content-type: application/json

{
    "role": {
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
        "displayName": "Access Review Operator Service Role",
        "description": "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
        "resource": {
            "id": "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
            "description": "Dev",
            "displayName": "Dev",
            "resourceType": "Subscription",
            "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
            "originSystem": "AzureResources"
        },
        "originSystem": "AzureResources",
        "type": "active"
    },
    "scope": {
        "id": "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640",
        "description": "/resourceGroups/rg",
        "displayName": "/resourceGroups/rg",
        "isRootScope": false,
        "originSystem": "AzureResources",
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	Role = new AccessPackageResourceRole
	{
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		DisplayName = "Access Review Operator Service Role",
		Description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		Resource = new AccessPackageResource
		{
			Id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			Description = "Dev",
			DisplayName = "Dev",
			OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			OriginSystem = "AzureResources",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"resourceType" , "Subscription"
				},
			},
		},
		OriginSystem = "AzureResources",
		Type = RoleType.Active,
	},
	Scope = new AccessPackageResourceScope
	{
		Id = "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640",
		Description = "/resourceGroups/rg",
		DisplayName = "/resourceGroups/rg",
		IsRootScope = false,
		OriginSystem = "AzureResources",
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].ResourceRoleScopes.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
role := graphmodels.NewAccessPackageResourceRole()
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
role.SetOriginId(&originId) 
displayName := "Access Review Operator Service Role"
role.SetDisplayName(&displayName) 
description := "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
role.SetDescription(&description) 
resource := graphmodels.NewAccessPackageResource()
id := "b09a0288-a83e-4ae6-8a53-bc09aeb966ea"
resource.SetId(&id) 
description := "Dev"
resource.SetDescription(&description) 
displayName := "Dev"
resource.SetDisplayName(&displayName) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
resource.SetOriginId(&originId) 
originSystem := "AzureResources"
resource.SetOriginSystem(&originSystem) 
additionalData := map[string]interface{}{
	"resourceType" : "Subscription", 
}
resource.SetAdditionalData(additionalData)
role.SetResource(resource)
originSystem := "AzureResources"
role.SetOriginSystem(&originSystem) 
type := graphmodels.ACTIVE_ROLETYPE 
role.SetType(&type) 
requestBody.SetRole(role)
scope := graphmodels.NewAccessPackageResourceScope()
id := "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640"
scope.SetId(&id) 
description := "/resourceGroups/rg"
scope.SetDescription(&description) 
displayName := "/resourceGroups/rg"
scope.SetDisplayName(&displayName) 
isRootScope := false
scope.SetIsRootScope(&isRootScope) 
originSystem := "AzureResources"
scope.SetOriginSystem(&originSystem) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg"
scope.SetOriginId(&originId) 
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").ResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole role = new AccessPackageResourceRole();
role.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475");
role.setDisplayName("Access Review Operator Service Role");
role.setDescription("Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.");
AccessPackageResource resource = new AccessPackageResource();
resource.setId("b09a0288-a83e-4ae6-8a53-bc09aeb966ea");
resource.setDescription("Dev");
resource.setDisplayName("Dev");
resource.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
resource.setOriginSystem("AzureResources");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("resourceType", "Subscription");
resource.setAdditionalData(additionalData);
role.setResource(resource);
role.setOriginSystem("AzureResources");
role.setType(RoleType.Active);
accessPackageResourceRoleScope.setRole(role);
AccessPackageResourceScope scope = new AccessPackageResourceScope();
scope.setId("e1e0ec8c-472d-4ec5-a8f9-29e0bc275640");
scope.setDescription("/resourceGroups/rg");
scope.setDisplayName("/resourceGroups/rg");
scope.setIsRootScope(false);
scope.setOriginSystem("AzureResources");
scope.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg");
accessPackageResourceRoleScope.setScope(scope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").resourceRoleScopes().post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    role: {
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475',
        displayName: 'Access Review Operator Service Role',
        description: 'Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.',
        resource: {
            id: 'b09a0288-a83e-4ae6-8a53-bc09aeb966ea',
            description: 'Dev',
            displayName: 'Dev',
            resourceType: 'Subscription',
            originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978',
            originSystem: 'AzureResources'
        },
        originSystem: 'AzureResources',
        type: 'active'
    },
    scope: {
        id: 'e1e0ec8c-472d-4ec5-a8f9-29e0bc275640',
        description: '/resourceGroups/rg',
        displayName: '/resourceGroups/rg',
        isRootScope: false,
        originSystem: 'AzureResources',
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/resourceRoleScopes')
	.post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\RoleType;
use Microsoft\Graph\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$role = new AccessPackageResourceRole();
$role->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475');
$role->setDisplayName('Access Review Operator Service Role');
$role->setDescription('Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.');
$roleResource = new AccessPackageResource();
$roleResource->setId('b09a0288-a83e-4ae6-8a53-bc09aeb966ea');
$roleResource->setDescription('Dev');
$roleResource->setDisplayName('Dev');
$roleResource->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$roleResource->setOriginSystem('AzureResources');
$additionalData = [
	'resourceType' => 'Subscription',
];
$roleResource->setAdditionalData($additionalData);
$role->setResource($roleResource);
$role->setOriginSystem('AzureResources');
$role->setType(new RoleType('active'));
$requestBody->setRole($role);
$scope = new AccessPackageResourceScope();
$scope->setId('e1e0ec8c-472d-4ec5-a8f9-29e0bc275640');
$scope->setDescription('/resourceGroups/rg');
$scope->setDisplayName('/resourceGroups/rg');
$scope->setIsRootScope(false);
$scope->setOriginSystem('AzureResources');
$scope->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg');
$requestBody->setScope($scope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->resourceRoleScopes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	role = @{
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
		displayName = "Access Review Operator Service Role"
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
		resource = @{
			id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea"
			description = "Dev"
			displayName = "Dev"
			resourceType = "Subscription"
			originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
			originSystem = "AzureResources"
		}
		originSystem = "AzureResources"
		type = "active"
	}
	scope = @{
		id = "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640"
		description = "/resourceGroups/rg"
		displayName = "/resourceGroups/rg"
		isRootScope = $false
		originSystem = "AzureResources"
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg"
	}
}

New-MgEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.role_type import RoleType
from msgraph.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	role = AccessPackageResourceRole(
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		display_name = "Access Review Operator Service Role",
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		resource = AccessPackageResource(
			id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			description = "Dev",
			display_name = "Dev",
			origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			origin_system = "AzureResources",
			additional_data = {
					"resource_type" : "Subscription",
			}
		),
		origin_system = "AzureResources",
		type = RoleType.Active,
	),
	scope = AccessPackageResourceScope(
		id = "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640",
		description = "/resourceGroups/rg",
		display_name = "/resourceGroups/rg",
		is_root_scope = False,
		origin_system = "AzureResources",
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').resource_role_scopes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "34b2d7de-e8d6-4ba8-843e-a03546feac63_e1e0ec8c-472d-4ec5-a8f9-29e0bc275640",
  "createdDateTime": "2026-02-09T22:31:55.3690356Z"
}
```

### Example 5: Add Eligible Management Group Resource Role to an access package

#### Request

The following example shows a request to add an eligible Management Group scoped to a Resource Role to an access package.

Before this request, you must have already added the access package resource `c347ca9b-a9cc-4df9-bc3c-00c8e0297692` for the Management Group `test-mgmtgroup` to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-resourcerequests?view=graph-rest-1.0).

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/resourceRoleScopes
Content-type: application/json

{
    "role": {
        "id": "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e",
        "originId": "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
        "displayName": "Access Review Operator Service Role",
        "description": "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
        "resource": {
            "id": "c347ca9b-a9cc-4df9-bc3c-00c8e0297692",
            "description": "test-mgmtgroup",
            "displayName": "test-mgmtgroup",
            "resourceType": "ManagementGroup",
            "originId": "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
            "originSystem": "AzureResources"
        },
        "originSystem": "AzureResources",
        "type": "eligible"
    },
    "scope": {
        "id": "338613b3-b410-4c6d-b5e9-45590bc8a357",
        "displayName": "Root",
        "description": "Root Scope",
        "isRootScope": true,
        "originId": "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
        "originSystem": "AzureResources"      
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	Role = new AccessPackageResourceRole
	{
		Id = "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e",
		OriginId = "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		DisplayName = "Access Review Operator Service Role",
		Description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		Resource = new AccessPackageResource
		{
			Id = "c347ca9b-a9cc-4df9-bc3c-00c8e0297692",
			Description = "test-mgmtgroup",
			DisplayName = "test-mgmtgroup",
			OriginId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
			OriginSystem = "AzureResources",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"resourceType" , "ManagementGroup"
				},
			},
		},
		OriginSystem = "AzureResources",
		Type = RoleType.Eligible,
	},
	Scope = new AccessPackageResourceScope
	{
		Id = "338613b3-b410-4c6d-b5e9-45590bc8a357",
		DisplayName = "Root",
		Description = "Root Scope",
		IsRootScope = true,
		OriginId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		OriginSystem = "AzureResources",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].ResourceRoleScopes.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
role := graphmodels.NewAccessPackageResourceRole()
id := "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e"
role.SetId(&id) 
originId := "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
role.SetOriginId(&originId) 
displayName := "Access Review Operator Service Role"
role.SetDisplayName(&displayName) 
description := "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
role.SetDescription(&description) 
resource := graphmodels.NewAccessPackageResource()
id := "c347ca9b-a9cc-4df9-bc3c-00c8e0297692"
resource.SetId(&id) 
description := "test-mgmtgroup"
resource.SetDescription(&description) 
displayName := "test-mgmtgroup"
resource.SetDisplayName(&displayName) 
originId := "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
resource.SetOriginId(&originId) 
originSystem := "AzureResources"
resource.SetOriginSystem(&originSystem) 
additionalData := map[string]interface{}{
	"resourceType" : "ManagementGroup", 
}
resource.SetAdditionalData(additionalData)
role.SetResource(resource)
originSystem := "AzureResources"
role.SetOriginSystem(&originSystem) 
type := graphmodels.ELIGIBLE_ROLETYPE 
role.SetType(&type) 
requestBody.SetRole(role)
scope := graphmodels.NewAccessPackageResourceScope()
id := "338613b3-b410-4c6d-b5e9-45590bc8a357"
scope.SetId(&id) 
displayName := "Root"
scope.SetDisplayName(&displayName) 
description := "Root Scope"
scope.SetDescription(&description) 
isRootScope := true
scope.SetIsRootScope(&isRootScope) 
originId := "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
scope.SetOriginId(&originId) 
originSystem := "AzureResources"
scope.SetOriginSystem(&originSystem) 
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").ResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole role = new AccessPackageResourceRole();
role.setId("055c76c1-a466-4f1a-9279-4a2ccaa7ac3e");
role.setOriginId("/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475");
role.setDisplayName("Access Review Operator Service Role");
role.setDescription("Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.");
AccessPackageResource resource = new AccessPackageResource();
resource.setId("c347ca9b-a9cc-4df9-bc3c-00c8e0297692");
resource.setDescription("test-mgmtgroup");
resource.setDisplayName("test-mgmtgroup");
resource.setOriginId("/providers/Microsoft.Management/managementGroups/test-mgmtgroup");
resource.setOriginSystem("AzureResources");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("resourceType", "ManagementGroup");
resource.setAdditionalData(additionalData);
role.setResource(resource);
role.setOriginSystem("AzureResources");
role.setType(RoleType.Eligible);
accessPackageResourceRoleScope.setRole(role);
AccessPackageResourceScope scope = new AccessPackageResourceScope();
scope.setId("338613b3-b410-4c6d-b5e9-45590bc8a357");
scope.setDisplayName("Root");
scope.setDescription("Root Scope");
scope.setIsRootScope(true);
scope.setOriginId("/providers/Microsoft.Management/managementGroups/test-mgmtgroup");
scope.setOriginSystem("AzureResources");
accessPackageResourceRoleScope.setScope(scope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").resourceRoleScopes().post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    role: {
        id: '055c76c1-a466-4f1a-9279-4a2ccaa7ac3e',
        originId: '/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475',
        displayName: 'Access Review Operator Service Role',
        description: 'Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.',
        resource: {
            id: 'c347ca9b-a9cc-4df9-bc3c-00c8e0297692',
            description: 'test-mgmtgroup',
            displayName: 'test-mgmtgroup',
            resourceType: 'ManagementGroup',
            originId: '/providers/Microsoft.Management/managementGroups/test-mgmtgroup',
            originSystem: 'AzureResources'
        },
        originSystem: 'AzureResources',
        type: 'eligible'
    },
    scope: {
        id: '338613b3-b410-4c6d-b5e9-45590bc8a357',
        displayName: 'Root',
        description: 'Root Scope',
        isRootScope: true,
        originId: '/providers/Microsoft.Management/managementGroups/test-mgmtgroup',
        originSystem: 'AzureResources'      
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/resourceRoleScopes')
	.post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\RoleType;
use Microsoft\Graph\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$role = new AccessPackageResourceRole();
$role->setId('055c76c1-a466-4f1a-9279-4a2ccaa7ac3e');
$role->setOriginId('/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475');
$role->setDisplayName('Access Review Operator Service Role');
$role->setDescription('Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.');
$roleResource = new AccessPackageResource();
$roleResource->setId('c347ca9b-a9cc-4df9-bc3c-00c8e0297692');
$roleResource->setDescription('test-mgmtgroup');
$roleResource->setDisplayName('test-mgmtgroup');
$roleResource->setOriginId('/providers/Microsoft.Management/managementGroups/test-mgmtgroup');
$roleResource->setOriginSystem('AzureResources');
$additionalData = [
	'resourceType' => 'ManagementGroup',
];
$roleResource->setAdditionalData($additionalData);
$role->setResource($roleResource);
$role->setOriginSystem('AzureResources');
$role->setType(new RoleType('eligible'));
$requestBody->setRole($role);
$scope = new AccessPackageResourceScope();
$scope->setId('338613b3-b410-4c6d-b5e9-45590bc8a357');
$scope->setDisplayName('Root');
$scope->setDescription('Root Scope');
$scope->setIsRootScope(true);
$scope->setOriginId('/providers/Microsoft.Management/managementGroups/test-mgmtgroup');
$scope->setOriginSystem('AzureResources');
$requestBody->setScope($scope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->resourceRoleScopes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	role = @{
		id = "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e"
		originId = "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
		displayName = "Access Review Operator Service Role"
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
		resource = @{
			id = "c347ca9b-a9cc-4df9-bc3c-00c8e0297692"
			description = "test-mgmtgroup"
			displayName = "test-mgmtgroup"
			resourceType = "ManagementGroup"
			originId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
			originSystem = "AzureResources"
		}
		originSystem = "AzureResources"
		type = "eligible"
	}
	scope = @{
		id = "338613b3-b410-4c6d-b5e9-45590bc8a357"
		displayName = "Root"
		description = "Root Scope"
		isRootScope = $true
		originId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
		originSystem = "AzureResources"
	}
}

New-MgEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.role_type import RoleType
from msgraph.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	role = AccessPackageResourceRole(
		id = "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e",
		origin_id = "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		display_name = "Access Review Operator Service Role",
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		resource = AccessPackageResource(
			id = "c347ca9b-a9cc-4df9-bc3c-00c8e0297692",
			description = "test-mgmtgroup",
			display_name = "test-mgmtgroup",
			origin_id = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
			origin_system = "AzureResources",
			additional_data = {
					"resource_type" : "ManagementGroup",
			}
		),
		origin_system = "AzureResources",
		type = RoleType.Eligible,
	),
	scope = AccessPackageResourceScope(
		id = "338613b3-b410-4c6d-b5e9-45590bc8a357",
		display_name = "Root",
		description = "Root Scope",
		is_root_scope = True,
		origin_id = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		origin_system = "AzureResources",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').resource_role_scopes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e_338613b3-b410-4c6d-b5e9-45590bc8a357",
  "createdDateTime": "2026-02-09T22:23:14.8561335Z"
}
```

### Example 6: Add Active Subscription Resource Role to access package

#### Request

The following example shows a request to Add Active Subscription Resource Role to an access package scoped to a Resource Role to an access package.

Before this request, you must have already added the access package resource `b09a0288-a83e-4ae6-8a53-bc09aeb966ea` for the Subscription `828b526f-c769-4b19-9797-734b4843b978` to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-resourcerequests?view=graph-rest-1.0).

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/resourceRoleScopes
Content-type: application/json

{
    "role": {
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
        "displayName": "Access Review Operator Service Role",
        "description": "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
        "resource": {
            "id": "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
            "description": "Dev",
            "displayName": "Dev",
            "resourceType": "Subscription",
            "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
            "originSystem": "AzureResources"
        },
        "originSystem": "AzureResources",
        "type": "active"
    },
    "scope": {
        "id": "c66c1e22-1093-46fb-a8a8-c0e334113ca4",
        "description": "Root",
        "displayName": "Root",
        "isRootScope": true,
        "originSystem": "AzureResources",
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	Role = new AccessPackageResourceRole
	{
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		DisplayName = "Access Review Operator Service Role",
		Description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		Resource = new AccessPackageResource
		{
			Id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			Description = "Dev",
			DisplayName = "Dev",
			OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			OriginSystem = "AzureResources",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"resourceType" , "Subscription"
				},
			},
		},
		OriginSystem = "AzureResources",
		Type = RoleType.Active,
	},
	Scope = new AccessPackageResourceScope
	{
		Id = "c66c1e22-1093-46fb-a8a8-c0e334113ca4",
		Description = "Root",
		DisplayName = "Root",
		IsRootScope = true,
		OriginSystem = "AzureResources",
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].ResourceRoleScopes.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
role := graphmodels.NewAccessPackageResourceRole()
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
role.SetOriginId(&originId) 
displayName := "Access Review Operator Service Role"
role.SetDisplayName(&displayName) 
description := "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
role.SetDescription(&description) 
resource := graphmodels.NewAccessPackageResource()
id := "b09a0288-a83e-4ae6-8a53-bc09aeb966ea"
resource.SetId(&id) 
description := "Dev"
resource.SetDescription(&description) 
displayName := "Dev"
resource.SetDisplayName(&displayName) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
resource.SetOriginId(&originId) 
originSystem := "AzureResources"
resource.SetOriginSystem(&originSystem) 
additionalData := map[string]interface{}{
	"resourceType" : "Subscription", 
}
resource.SetAdditionalData(additionalData)
role.SetResource(resource)
originSystem := "AzureResources"
role.SetOriginSystem(&originSystem) 
type := graphmodels.ACTIVE_ROLETYPE 
role.SetType(&type) 
requestBody.SetRole(role)
scope := graphmodels.NewAccessPackageResourceScope()
id := "c66c1e22-1093-46fb-a8a8-c0e334113ca4"
scope.SetId(&id) 
description := "Root"
scope.SetDescription(&description) 
displayName := "Root"
scope.SetDisplayName(&displayName) 
isRootScope := true
scope.SetIsRootScope(&isRootScope) 
originSystem := "AzureResources"
scope.SetOriginSystem(&originSystem) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
scope.SetOriginId(&originId) 
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").ResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole role = new AccessPackageResourceRole();
role.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475");
role.setDisplayName("Access Review Operator Service Role");
role.setDescription("Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.");
AccessPackageResource resource = new AccessPackageResource();
resource.setId("b09a0288-a83e-4ae6-8a53-bc09aeb966ea");
resource.setDescription("Dev");
resource.setDisplayName("Dev");
resource.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
resource.setOriginSystem("AzureResources");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("resourceType", "Subscription");
resource.setAdditionalData(additionalData);
role.setResource(resource);
role.setOriginSystem("AzureResources");
role.setType(RoleType.Active);
accessPackageResourceRoleScope.setRole(role);
AccessPackageResourceScope scope = new AccessPackageResourceScope();
scope.setId("c66c1e22-1093-46fb-a8a8-c0e334113ca4");
scope.setDescription("Root");
scope.setDisplayName("Root");
scope.setIsRootScope(true);
scope.setOriginSystem("AzureResources");
scope.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
accessPackageResourceRoleScope.setScope(scope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").resourceRoleScopes().post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    role: {
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475',
        displayName: 'Access Review Operator Service Role',
        description: 'Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.',
        resource: {
            id: 'b09a0288-a83e-4ae6-8a53-bc09aeb966ea',
            description: 'Dev',
            displayName: 'Dev',
            resourceType: 'Subscription',
            originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978',
            originSystem: 'AzureResources'
        },
        originSystem: 'AzureResources',
        type: 'active'
    },
    scope: {
        id: 'c66c1e22-1093-46fb-a8a8-c0e334113ca4',
        description: 'Root',
        displayName: 'Root',
        isRootScope: true,
        originSystem: 'AzureResources',
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/resourceRoleScopes')
	.post(accessPackageResourceRoleScope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\RoleType;
use Microsoft\Graph\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$role = new AccessPackageResourceRole();
$role->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475');
$role->setDisplayName('Access Review Operator Service Role');
$role->setDescription('Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.');
$roleResource = new AccessPackageResource();
$roleResource->setId('b09a0288-a83e-4ae6-8a53-bc09aeb966ea');
$roleResource->setDescription('Dev');
$roleResource->setDisplayName('Dev');
$roleResource->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$roleResource->setOriginSystem('AzureResources');
$additionalData = [
	'resourceType' => 'Subscription',
];
$roleResource->setAdditionalData($additionalData);
$role->setResource($roleResource);
$role->setOriginSystem('AzureResources');
$role->setType(new RoleType('active'));
$requestBody->setRole($role);
$scope = new AccessPackageResourceScope();
$scope->setId('c66c1e22-1093-46fb-a8a8-c0e334113ca4');
$scope->setDescription('Root');
$scope->setDisplayName('Root');
$scope->setIsRootScope(true);
$scope->setOriginSystem('AzureResources');
$scope->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$requestBody->setScope($scope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->resourceRoleScopes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	role = @{
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
		displayName = "Access Review Operator Service Role"
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
		resource = @{
			id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea"
			description = "Dev"
			displayName = "Dev"
			resourceType = "Subscription"
			originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
			originSystem = "AzureResources"
		}
		originSystem = "AzureResources"
		type = "active"
	}
	scope = @{
		id = "c66c1e22-1093-46fb-a8a8-c0e334113ca4"
		description = "Root"
		displayName = "Root"
		isRootScope = $true
		originSystem = "AzureResources"
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
	}
}

New-MgEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.role_type import RoleType
from msgraph.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	role = AccessPackageResourceRole(
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		display_name = "Access Review Operator Service Role",
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		resource = AccessPackageResource(
			id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			description = "Dev",
			display_name = "Dev",
			origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			origin_system = "AzureResources",
			additional_data = {
					"resource_type" : "Subscription",
			}
		),
		origin_system = "AzureResources",
		type = RoleType.Active,
	),
	scope = AccessPackageResourceScope(
		id = "c66c1e22-1093-46fb-a8a8-c0e334113ca4",
		description = "Root",
		display_name = "Root",
		is_root_scope = True,
		origin_system = "AzureResources",
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').resource_role_scopes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "34b2d7de-e8d6-4ba8-843e-a03546feac63_c66c1e22-1093-46fb-a8a8-c0e334113ca4",
  "createdDateTime": "2026-02-09T22:29:40.3420825Z"
}
```
