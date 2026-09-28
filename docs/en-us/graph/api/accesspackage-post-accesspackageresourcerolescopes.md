<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackage-post-accesspackageresourcerolescopes?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create accessPackageResourceRoleScope

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-beta) for adding a resource role to an access package. The access package resource, for a group, an app, or a SharePoint Online site, must already exist in the access package catalog, and the **originId** for the resource role retrieved from the [list of the resource roles](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-accesspackageresourceroles?view=graph-rest-beta). Once you add the resource role scope to the access package, the user will receive this resource role through any current and future access package assignments.

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
POST /identityGovernance/entitlementManagement/accessPackages/{id}/accessPackageResourceRoleScopes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-beta) object. Include in the object the relationships to an [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-beta) object, which can be obtained from a request to [list access package resource roles of a resource in a catalog](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-accesspackageresourceroles?view=graph-rest-beta), and an [accessPackageResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-beta) object, which can be obtained from a request to [list access package resources](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-accesspackageresources?view=graph-rest-beta) with `$expand=accessPackageResourceScopes`.

## Response

If successful, this method returns a 200-series response code and a new [accessPackageResourceRoleScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerolescope?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Add group membership as a resource role to an access package

#### Request

The following example shows a request. Previous to this request, the access package resource `1d08498d-72a1-403f-8511-6b1f875746a0` for the group `b31fe1f1-3651-488f-bd9a-1711887fd4ca` must already have been added to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageresourcerequests?view=graph-rest-beta).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/{id}/accessPackageResourceRoleScopes
Content-type: application/json

{
  "accessPackageResourceRole":{
    "originId":"Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca",
    "displayName":"Member",
    "originSystem":"AadGroup",
    "accessPackageResource":{"id":"1d08498d-72a1-403f-8511-6b1f875746a0","resourceType":"O365 Group","originId":"b31fe1f1-3651-488f-bd9a-1711887fd4ca","originSystem":"AadGroup"}
  },
 "accessPackageResourceScope":{
   "originId":"b31fe1f1-3651-488f-bd9a-1711887fd4ca","originSystem":"AadGroup"
 }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	AccessPackageResourceRole = new AccessPackageResourceRole
	{
		OriginId = "Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca",
		DisplayName = "Member",
		OriginSystem = "AadGroup",
		AccessPackageResource = new AccessPackageResource
		{
			Id = "1d08498d-72a1-403f-8511-6b1f875746a0",
			ResourceType = "O365 Group",
			OriginId = "b31fe1f1-3651-488f-bd9a-1711887fd4ca",
			OriginSystem = "AadGroup",
		},
	},
	AccessPackageResourceScope = new AccessPackageResourceScope
	{
		OriginId = "b31fe1f1-3651-488f-bd9a-1711887fd4ca",
		OriginSystem = "AadGroup",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].AccessPackageResourceRoleScopes.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
accessPackageResourceRole := graphmodels.NewAccessPackageResourceRole()
originId := "Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca"
accessPackageResourceRole.SetOriginId(&originId) 
displayName := "Member"
accessPackageResourceRole.SetDisplayName(&displayName) 
originSystem := "AadGroup"
accessPackageResourceRole.SetOriginSystem(&originSystem) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := "1d08498d-72a1-403f-8511-6b1f875746a0"
accessPackageResource.SetId(&id) 
resourceType := "O365 Group"
accessPackageResource.SetResourceType(&resourceType) 
originId := "b31fe1f1-3651-488f-bd9a-1711887fd4ca"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AadGroup"
accessPackageResource.SetOriginSystem(&originSystem) 
accessPackageResourceRole.SetAccessPackageResource(accessPackageResource)
requestBody.SetAccessPackageResourceRole(accessPackageResourceRole)
accessPackageResourceScope := graphmodels.NewAccessPackageResourceScope()
originId := "b31fe1f1-3651-488f-bd9a-1711887fd4ca"
accessPackageResourceScope.SetOriginId(&originId) 
originSystem := "AadGroup"
accessPackageResourceScope.SetOriginSystem(&originSystem) 
requestBody.SetAccessPackageResourceScope(accessPackageResourceScope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").AccessPackageResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole accessPackageResourceRole = new AccessPackageResourceRole();
accessPackageResourceRole.setOriginId("Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca");
accessPackageResourceRole.setDisplayName("Member");
accessPackageResourceRole.setOriginSystem("AadGroup");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("1d08498d-72a1-403f-8511-6b1f875746a0");
accessPackageResource.setResourceType("O365 Group");
accessPackageResource.setOriginId("b31fe1f1-3651-488f-bd9a-1711887fd4ca");
accessPackageResource.setOriginSystem("AadGroup");
accessPackageResourceRole.setAccessPackageResource(accessPackageResource);
accessPackageResourceRoleScope.setAccessPackageResourceRole(accessPackageResourceRole);
AccessPackageResourceScope accessPackageResourceScope = new AccessPackageResourceScope();
accessPackageResourceScope.setOriginId("b31fe1f1-3651-488f-bd9a-1711887fd4ca");
accessPackageResourceScope.setOriginSystem("AadGroup");
accessPackageResourceRoleScope.setAccessPackageResourceScope(accessPackageResourceScope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").accessPackageResourceRoleScopes().post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
  accessPackageResourceRole: {
    originId: 'Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca',
    displayName: 'Member',
    originSystem: 'AadGroup',
    accessPackageResource: {id: '1d08498d-72a1-403f-8511-6b1f875746a0',resourceType: 'O365 Group',originId: 'b31fe1f1-3651-488f-bd9a-1711887fd4ca',originSystem: 'AadGroup'}
  },
 accessPackageResourceScope: {
   originId: 'b31fe1f1-3651-488f-bd9a-1711887fd4ca',originSystem: 'AadGroup'
 }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/{id}/accessPackageResourceRoleScopes')
	.version('beta')
	.post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$accessPackageResourceRole = new AccessPackageResourceRole();
$accessPackageResourceRole->setOriginId('Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca');
$accessPackageResourceRole->setDisplayName('Member');
$accessPackageResourceRole->setOriginSystem('AadGroup');
$accessPackageResourceRoleAccessPackageResource = new AccessPackageResource();
$accessPackageResourceRoleAccessPackageResource->setId('1d08498d-72a1-403f-8511-6b1f875746a0');
$accessPackageResourceRoleAccessPackageResource->setResourceType('O365 Group');
$accessPackageResourceRoleAccessPackageResource->setOriginId('b31fe1f1-3651-488f-bd9a-1711887fd4ca');
$accessPackageResourceRoleAccessPackageResource->setOriginSystem('AadGroup');
$accessPackageResourceRole->setAccessPackageResource($accessPackageResourceRoleAccessPackageResource);
$requestBody->setAccessPackageResourceRole($accessPackageResourceRole);
$accessPackageResourceScope = new AccessPackageResourceScope();
$accessPackageResourceScope->setOriginId('b31fe1f1-3651-488f-bd9a-1711887fd4ca');
$accessPackageResourceScope->setOriginSystem('AadGroup');
$requestBody->setAccessPackageResourceScope($accessPackageResourceScope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->accessPackageResourceRoleScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageResourceRole = @{
		originId = "Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca"
		displayName = "Member"
		originSystem = "AadGroup"
		accessPackageResource = @{
			id = "1d08498d-72a1-403f-8511-6b1f875746a0"
			resourceType = "O365 Group"
			originId = "b31fe1f1-3651-488f-bd9a-1711887fd4ca"
			originSystem = "AadGroup"
		}
	}
	accessPackageResourceScope = @{
		originId = "b31fe1f1-3651-488f-bd9a-1711887fd4ca"
		originSystem = "AadGroup"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph_beta.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	access_package_resource_role = AccessPackageResourceRole(
		origin_id = "Member_b31fe1f1-3651-488f-bd9a-1711887fd4ca",
		display_name = "Member",
		origin_system = "AadGroup",
		access_package_resource = AccessPackageResource(
			id = "1d08498d-72a1-403f-8511-6b1f875746a0",
			resource_type = "O365 Group",
			origin_id = "b31fe1f1-3651-488f-bd9a-1711887fd4ca",
			origin_system = "AadGroup",
		),
	),
	access_package_resource_scope = AccessPackageResourceScope(
		origin_id = "b31fe1f1-3651-488f-bd9a-1711887fd4ca",
		origin_system = "AadGroup",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').access_package_resource_role_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageResourceRoleScopes/$entity",
    "id": "ad5c7636-e481-4528-991f-198e3b38dd56_ffd4004a-f4a9-4b22-b027-759e55c0d1db",
    "createdBy": "admin@example.com",
    "createdDateTime": "2019-12-11T01:35:26.4754081Z",
    "modifiedBy": "admin@example.com",
    "modifiedDateTime": "2019-12-11T01:35:26.4754081Z"
}
```

### Example 2: Add a SharePoint Online site role to an access package

#### Request

The following example shows a request for a non-root scope resource. The access package resource for the site must already have been added to the access package catalog containing this access package.

The request contains an [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-beta) object, which can be obtained from an earlier request to [list access package resource roles of a resource in a catalog](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-accesspackageresourceroles?view=graph-rest-beta). Each type of resource defines the format of the originId field in a resource role. For a SharePoint Online site, the originId is the sequence number of the role in the site.

If the [accessPackageResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-beta) object obtained from an earlier request to [list access package resources](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-accesspackageresources?view=graph-rest-beta) has the resource as a root scope \(**isRootScope** set to `true`\), include the **isRootScope** property in the **accessPackageResourceScope** object of the request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/{id}/accessPackageResourceRoleScopes
Content-type: application/json

{
    "accessPackageResourceRole": {
        "originId": "4",
        "originSystem": "SharePointOnline",
        "accessPackageResource": {
            "id": "53c71803-a0a8-4777-aecc-075de8ee3991"
        }
    },
    "accessPackageResourceScope": {
        "id": "5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33",
        "originId": "https://microsoft.sharepoint.com/portals/Community",
        "originSystem": "SharePointOnline"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	AccessPackageResourceRole = new AccessPackageResourceRole
	{
		OriginId = "4",
		OriginSystem = "SharePointOnline",
		AccessPackageResource = new AccessPackageResource
		{
			Id = "53c71803-a0a8-4777-aecc-075de8ee3991",
		},
	},
	AccessPackageResourceScope = new AccessPackageResourceScope
	{
		Id = "5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33",
		OriginId = "https://microsoft.sharepoint.com/portals/Community",
		OriginSystem = "SharePointOnline",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].AccessPackageResourceRoleScopes.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
accessPackageResourceRole := graphmodels.NewAccessPackageResourceRole()
originId := "4"
accessPackageResourceRole.SetOriginId(&originId) 
originSystem := "SharePointOnline"
accessPackageResourceRole.SetOriginSystem(&originSystem) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := "53c71803-a0a8-4777-aecc-075de8ee3991"
accessPackageResource.SetId(&id) 
accessPackageResourceRole.SetAccessPackageResource(accessPackageResource)
requestBody.SetAccessPackageResourceRole(accessPackageResourceRole)
accessPackageResourceScope := graphmodels.NewAccessPackageResourceScope()
id := "5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33"
accessPackageResourceScope.SetId(&id) 
originId := "https://microsoft.sharepoint.com/portals/Community"
accessPackageResourceScope.SetOriginId(&originId) 
originSystem := "SharePointOnline"
accessPackageResourceScope.SetOriginSystem(&originSystem) 
requestBody.SetAccessPackageResourceScope(accessPackageResourceScope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").AccessPackageResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole accessPackageResourceRole = new AccessPackageResourceRole();
accessPackageResourceRole.setOriginId("4");
accessPackageResourceRole.setOriginSystem("SharePointOnline");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("53c71803-a0a8-4777-aecc-075de8ee3991");
accessPackageResourceRole.setAccessPackageResource(accessPackageResource);
accessPackageResourceRoleScope.setAccessPackageResourceRole(accessPackageResourceRole);
AccessPackageResourceScope accessPackageResourceScope = new AccessPackageResourceScope();
accessPackageResourceScope.setId("5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33");
accessPackageResourceScope.setOriginId("https://microsoft.sharepoint.com/portals/Community");
accessPackageResourceScope.setOriginSystem("SharePointOnline");
accessPackageResourceRoleScope.setAccessPackageResourceScope(accessPackageResourceScope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").accessPackageResourceRoleScopes().post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    accessPackageResourceRole: {
        originId: '4',
        originSystem: 'SharePointOnline',
        accessPackageResource: {
            id: '53c71803-a0a8-4777-aecc-075de8ee3991'
        }
    },
    accessPackageResourceScope: {
        id: '5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33',
        originId: 'https://microsoft.sharepoint.com/portals/Community',
        originSystem: 'SharePointOnline'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/{id}/accessPackageResourceRoleScopes')
	.version('beta')
	.post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$accessPackageResourceRole = new AccessPackageResourceRole();
$accessPackageResourceRole->setOriginId('4');
$accessPackageResourceRole->setOriginSystem('SharePointOnline');
$accessPackageResourceRoleAccessPackageResource = new AccessPackageResource();
$accessPackageResourceRoleAccessPackageResource->setId('53c71803-a0a8-4777-aecc-075de8ee3991');
$accessPackageResourceRole->setAccessPackageResource($accessPackageResourceRoleAccessPackageResource);
$requestBody->setAccessPackageResourceRole($accessPackageResourceRole);
$accessPackageResourceScope = new AccessPackageResourceScope();
$accessPackageResourceScope->setId('5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33');
$accessPackageResourceScope->setOriginId('https://microsoft.sharepoint.com/portals/Community');
$accessPackageResourceScope->setOriginSystem('SharePointOnline');
$requestBody->setAccessPackageResourceScope($accessPackageResourceScope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->accessPackageResourceRoleScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageResourceRole = @{
		originId = "4"
		originSystem = "SharePointOnline"
		accessPackageResource = @{
			id = "53c71803-a0a8-4777-aecc-075de8ee3991"
		}
	}
	accessPackageResourceScope = @{
		id = "5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33"
		originId = "https://microsoft.sharepoint.com/portals/Community"
		originSystem = "SharePointOnline"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph_beta.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	access_package_resource_role = AccessPackageResourceRole(
		origin_id = "4",
		origin_system = "SharePointOnline",
		access_package_resource = AccessPackageResource(
			id = "53c71803-a0a8-4777-aecc-075de8ee3991",
		),
	),
	access_package_resource_scope = AccessPackageResourceScope(
		id = "5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33",
		origin_id = "https://microsoft.sharepoint.com/portals/Community",
		origin_system = "SharePointOnline",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').access_package_resource_role_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
   "id": "6646a29e-da03-49f6-bcd9-dec124492de3_5ae0ae7c-d0a5-42aa-ab37-1f15e9a61d33"
}
```

### Example 3: Add a Microsoft Entra role as a resource in an access package

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/{id}/accessPackageResourceRoleScopes
Content-type: application/json

{
    "role": {
        "originId": "Eligible",
        "displayName": "Eligible Member",
        "originSystem": "DirectoryRole",
        "resource": {
            "id": "ea036095-57a6-4c90-a640-013edf151eb1"
        }
    },
    "scope": {
        "description": "Root Scope",
        "displayName": "Root",
        "isRootScope": true,
        "originSystem": "DirectoryRole",
        "originId": "c4e39bd9-1100-46d3-8c65-fb160da0071f"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessPackageResourceRoleScope
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"role" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"originId", new UntypedString("Eligible")
				},
				{
					"displayName", new UntypedString("Eligible Member")
				},
				{
					"originSystem", new UntypedString("DirectoryRole")
				},
				{
					"resource", new UntypedObject(new Dictionary<string, UntypedNode>
					{
						{
							"id", new UntypedString("ea036095-57a6-4c90-a640-013edf151eb1")
						},
					})
				},
			})
		},
		{
			"scope" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"description", new UntypedString("Root Scope")
				},
				{
					"displayName", new UntypedString("Root")
				},
				{
					"isRootScope", new UntypedBoolean(true)
				},
				{
					"originSystem", new UntypedString("DirectoryRole")
				},
				{
					"originId", new UntypedString("c4e39bd9-1100-46d3-8c65-fb160da0071f")
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].AccessPackageResourceRoleScopes.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
additionalData := map[string]interface{}{
role := graph.New()
originId := "Eligible"
role.SetOriginId(&originId) 
displayName := "Eligible Member"
role.SetDisplayName(&displayName) 
originSystem := "DirectoryRole"
role.SetOriginSystem(&originSystem) 
resource := graph.New()
id := "ea036095-57a6-4c90-a640-013edf151eb1"
resource.SetId(&id) 
	role.SetResource(resource)
	requestBody.SetRole(role)
scope := graph.New()
description := "Root Scope"
scope.SetDescription(&description) 
displayName := "Root"
scope.SetDisplayName(&displayName) 
	isRootScope := true
scope.SetIsRootScope(&isRootScope) 
originSystem := "DirectoryRole"
scope.SetOriginSystem(&originSystem) 
originId := "c4e39bd9-1100-46d3-8c65-fb160da0071f"
scope.SetOriginId(&originId) 
	requestBody.SetScope(scope)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").AccessPackageResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
 role = new ();
role.setOriginId("Eligible");
role.setDisplayName("Eligible Member");
role.setOriginSystem("DirectoryRole");
 resource = new ();
resource.setId("ea036095-57a6-4c90-a640-013edf151eb1");
role.setResource(resource);
additionalData.put("role", role);
 scope = new ();
scope.setDescription("Root Scope");
scope.setDisplayName("Root");
scope.setIsRootScope(true);
scope.setOriginSystem("DirectoryRole");
scope.setOriginId("c4e39bd9-1100-46d3-8c65-fb160da0071f");
additionalData.put("scope", scope);
accessPackageResourceRoleScope.setAdditionalData(additionalData);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").accessPackageResourceRoleScopes().post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    role: {
        originId: 'Eligible',
        displayName: 'Eligible Member',
        originSystem: 'DirectoryRole',
        resource: {
            id: 'ea036095-57a6-4c90-a640-013edf151eb1'
        }
    },
    scope: {
        description: 'Root Scope',
        displayName: 'Root',
        isRootScope: true,
        originSystem: 'DirectoryRole',
        originId: 'c4e39bd9-1100-46d3-8c65-fb160da0071f'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/{id}/accessPackageResourceRoleScopes')
	.version('beta')
	.post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRoleScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$additionalData = [
	'role' => [
		'originId' => 'Eligible',
		'displayName' => 'Eligible Member',
		'originSystem' => 'DirectoryRole',
		'resource' => [
			'id' => 'ea036095-57a6-4c90-a640-013edf151eb1',
		],
	],
	'scope' => [
		'description' => 'Root Scope',
		'displayName' => 'Root',
		'isRootScope' => true,
		'originSystem' => 'DirectoryRole',
		'originId' => 'c4e39bd9-1100-46d3-8c65-fb160da0071f',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->accessPackageResourceRoleScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	role = @{
		originId = "Eligible"
		displayName = "Eligible Member"
		originSystem = "DirectoryRole"
		resource = @{
			id = "ea036095-57a6-4c90-a640-013edf151eb1"
		}
	}
	scope = @{
		description = "Root Scope"
		displayName = "Root"
		isRootScope = $true
		originSystem = "DirectoryRole"
		originId = "c4e39bd9-1100-46d3-8c65-fb160da0071f"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	additional_data = {
			"role" : {
					"origin_id" : "Eligible",
					"display_name" : "Eligible Member",
					"origin_system" : "DirectoryRole",
					"resource" : {
							"id" : "ea036095-57a6-4c90-a640-013edf151eb1",
					},
			},
			"scope" : {
					"description" : "Root Scope",
					"display_name" : "Root",
					"is_root_scope" : True,
					"origin_system" : "DirectoryRole",
					"origin_id" : "c4e39bd9-1100-46d3-8c65-fb160da0071f",
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').access_package_resource_role_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
   "id": "ea036095-57a6-4c90-a640-013edf151eb1_c4e39bd9-1100-46d3-8c65-fb160da0071f",
   "createdDateTime": "2023-06-28T01:19:48.4216782Z"
}
```

### Example 4: Add a PIM-managed group as a resource role to an access package

#### Request

The following example shows a request to add a PIM-managed group as a resource role to an access package. The group's members are eligible to the group.

Before this request, you must have already added the access package resource `b86a1828-3171-409e-8343-32a224f324a0` for the PIM-managed group `bcfae74a-91a6-46e9-99bf-89d6487cc3f3` to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageresourcerequests?view=graph-rest-beta).

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/b86a1828-3171-409e-8343-32a224f324a0/accessPackageResourceRoleScopes
Content-type: application/json

{
  "accessPackageResourceRole":{
    "originId":"EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18",
    "displayName":"Eligible Member",
    "originSystem":"AadGroup",
    "accessPackageResource":{"id":"b86a1828-3171-409e-8343-32a224f324a0","resourceType":"O365 Group","originId":"bcfae74a-91a6-46e9-99bf-89d6487cc3f3","originSystem":"AadGroup"}
  },
 "accessPackageResourceScope":{
   "originId":"bcfae74a-91a6-46e9-99bf-89d6487cc3f3","originSystem":"AadGroup"
 }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	AccessPackageResourceRole = new AccessPackageResourceRole
	{
		OriginId = "EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18",
		DisplayName = "Eligible Member",
		OriginSystem = "AadGroup",
		AccessPackageResource = new AccessPackageResource
		{
			Id = "b86a1828-3171-409e-8343-32a224f324a0",
			ResourceType = "O365 Group",
			OriginId = "bcfae74a-91a6-46e9-99bf-89d6487cc3f3",
			OriginSystem = "AadGroup",
		},
	},
	AccessPackageResourceScope = new AccessPackageResourceScope
	{
		OriginId = "bcfae74a-91a6-46e9-99bf-89d6487cc3f3",
		OriginSystem = "AadGroup",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].AccessPackageResourceRoleScopes.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
accessPackageResourceRole := graphmodels.NewAccessPackageResourceRole()
originId := "EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18"
accessPackageResourceRole.SetOriginId(&originId) 
displayName := "Eligible Member"
accessPackageResourceRole.SetDisplayName(&displayName) 
originSystem := "AadGroup"
accessPackageResourceRole.SetOriginSystem(&originSystem) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := "b86a1828-3171-409e-8343-32a224f324a0"
accessPackageResource.SetId(&id) 
resourceType := "O365 Group"
accessPackageResource.SetResourceType(&resourceType) 
originId := "bcfae74a-91a6-46e9-99bf-89d6487cc3f3"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AadGroup"
accessPackageResource.SetOriginSystem(&originSystem) 
accessPackageResourceRole.SetAccessPackageResource(accessPackageResource)
requestBody.SetAccessPackageResourceRole(accessPackageResourceRole)
accessPackageResourceScope := graphmodels.NewAccessPackageResourceScope()
originId := "bcfae74a-91a6-46e9-99bf-89d6487cc3f3"
accessPackageResourceScope.SetOriginId(&originId) 
originSystem := "AadGroup"
accessPackageResourceScope.SetOriginSystem(&originSystem) 
requestBody.SetAccessPackageResourceScope(accessPackageResourceScope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").AccessPackageResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole accessPackageResourceRole = new AccessPackageResourceRole();
accessPackageResourceRole.setOriginId("EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18");
accessPackageResourceRole.setDisplayName("Eligible Member");
accessPackageResourceRole.setOriginSystem("AadGroup");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("b86a1828-3171-409e-8343-32a224f324a0");
accessPackageResource.setResourceType("O365 Group");
accessPackageResource.setOriginId("bcfae74a-91a6-46e9-99bf-89d6487cc3f3");
accessPackageResource.setOriginSystem("AadGroup");
accessPackageResourceRole.setAccessPackageResource(accessPackageResource);
accessPackageResourceRoleScope.setAccessPackageResourceRole(accessPackageResourceRole);
AccessPackageResourceScope accessPackageResourceScope = new AccessPackageResourceScope();
accessPackageResourceScope.setOriginId("bcfae74a-91a6-46e9-99bf-89d6487cc3f3");
accessPackageResourceScope.setOriginSystem("AadGroup");
accessPackageResourceRoleScope.setAccessPackageResourceScope(accessPackageResourceScope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").accessPackageResourceRoleScopes().post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
  accessPackageResourceRole: {
    originId: 'EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18',
    displayName: 'Eligible Member',
    originSystem: 'AadGroup',
    accessPackageResource: {id: 'b86a1828-3171-409e-8343-32a224f324a0',resourceType: 'O365 Group',originId: 'bcfae74a-91a6-46e9-99bf-89d6487cc3f3',originSystem: 'AadGroup'}
  },
 accessPackageResourceScope: {
   originId: 'bcfae74a-91a6-46e9-99bf-89d6487cc3f3',originSystem: 'AadGroup'
 }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/b86a1828-3171-409e-8343-32a224f324a0/accessPackageResourceRoleScopes')
	.version('beta')
	.post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$accessPackageResourceRole = new AccessPackageResourceRole();
$accessPackageResourceRole->setOriginId('EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18');
$accessPackageResourceRole->setDisplayName('Eligible Member');
$accessPackageResourceRole->setOriginSystem('AadGroup');
$accessPackageResourceRoleAccessPackageResource = new AccessPackageResource();
$accessPackageResourceRoleAccessPackageResource->setId('b86a1828-3171-409e-8343-32a224f324a0');
$accessPackageResourceRoleAccessPackageResource->setResourceType('O365 Group');
$accessPackageResourceRoleAccessPackageResource->setOriginId('bcfae74a-91a6-46e9-99bf-89d6487cc3f3');
$accessPackageResourceRoleAccessPackageResource->setOriginSystem('AadGroup');
$accessPackageResourceRole->setAccessPackageResource($accessPackageResourceRoleAccessPackageResource);
$requestBody->setAccessPackageResourceRole($accessPackageResourceRole);
$accessPackageResourceScope = new AccessPackageResourceScope();
$accessPackageResourceScope->setOriginId('bcfae74a-91a6-46e9-99bf-89d6487cc3f3');
$accessPackageResourceScope->setOriginSystem('AadGroup');
$requestBody->setAccessPackageResourceScope($accessPackageResourceScope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->accessPackageResourceRoleScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageResourceRole = @{
		originId = "EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18"
		displayName = "Eligible Member"
		originSystem = "AadGroup"
		accessPackageResource = @{
			id = "b86a1828-3171-409e-8343-32a224f324a0"
			resourceType = "O365 Group"
			originId = "bcfae74a-91a6-46e9-99bf-89d6487cc3f3"
			originSystem = "AadGroup"
		}
	}
	accessPackageResourceScope = @{
		originId = "bcfae74a-91a6-46e9-99bf-89d6487cc3f3"
		originSystem = "AadGroup"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph_beta.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	access_package_resource_role = AccessPackageResourceRole(
		origin_id = "EligibleMember_89590e41-f49d-4792-b531-6ed6fe6cfe18",
		display_name = "Eligible Member",
		origin_system = "AadGroup",
		access_package_resource = AccessPackageResource(
			id = "b86a1828-3171-409e-8343-32a224f324a0",
			resource_type = "O365 Group",
			origin_id = "bcfae74a-91a6-46e9-99bf-89d6487cc3f3",
			origin_system = "AadGroup",
		),
	),
	access_package_resource_scope = AccessPackageResourceScope(
		origin_id = "bcfae74a-91a6-46e9-99bf-89d6487cc3f3",
		origin_system = "AadGroup",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').access_package_resource_role_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#accessPackageResourceRoleScopes/$entity",
    "id": "ad5c7636-e481-4528-991f-198e3b38dd56_ffd4004a-f4a9-4b22-b027-759e55c0d1db",
    "createdBy": "admin@example.com",
    "createdDateTime": "2019-12-11T01:35:26.4754081Z",
    "modifiedBy": "admin@example.com",
    "modifiedDateTime": "2019-12-11T01:35:26.4754081Z"
}
```

### Example 5: Add an Active Subscription scoped to a Resource Group Resource Role to an access package

#### Request

The following example shows a request to add an active Subscription scoped to a Resource Group Resource Role to an access package.

Before this request, you must have already added the access package resource `b09a0288-a83e-4ae6-8a53-bc09aeb966ea` for the Subscription `828b526f-c769-4b19-9797-734b4843b978` to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageresourcerequests?view=graph-rest-beta).

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/accessPackageResourceRoleScopes
Content-type: application/json

{
    "accessPackageResourceRole": {
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
        "displayName": "Access Review Operator Service Role",
        "description": "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
        "accessPackageResource": {
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
    "accessPackageResourceScope": {
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
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	AccessPackageResourceRole = new AccessPackageResourceRole
	{
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		DisplayName = "Access Review Operator Service Role",
		Description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		AccessPackageResource = new AccessPackageResource
		{
			Id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			Description = "Dev",
			DisplayName = "Dev",
			ResourceType = "Subscription",
			OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			OriginSystem = "AzureResources",
		},
		OriginSystem = "AzureResources",
		Type = RoleType.Active,
	},
	AccessPackageResourceScope = new AccessPackageResourceScope
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
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].AccessPackageResourceRoleScopes.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
accessPackageResourceRole := graphmodels.NewAccessPackageResourceRole()
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
accessPackageResourceRole.SetOriginId(&originId) 
displayName := "Access Review Operator Service Role"
accessPackageResourceRole.SetDisplayName(&displayName) 
description := "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
accessPackageResourceRole.SetDescription(&description) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := "b09a0288-a83e-4ae6-8a53-bc09aeb966ea"
accessPackageResource.SetId(&id) 
description := "Dev"
accessPackageResource.SetDescription(&description) 
displayName := "Dev"
accessPackageResource.SetDisplayName(&displayName) 
resourceType := "Subscription"
accessPackageResource.SetResourceType(&resourceType) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AzureResources"
accessPackageResource.SetOriginSystem(&originSystem) 
accessPackageResourceRole.SetAccessPackageResource(accessPackageResource)
originSystem := "AzureResources"
accessPackageResourceRole.SetOriginSystem(&originSystem) 
type := graphmodels.ACTIVE_ROLETYPE 
accessPackageResourceRole.SetType(&type) 
requestBody.SetAccessPackageResourceRole(accessPackageResourceRole)
accessPackageResourceScope := graphmodels.NewAccessPackageResourceScope()
id := "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640"
accessPackageResourceScope.SetId(&id) 
description := "/resourceGroups/rg"
accessPackageResourceScope.SetDescription(&description) 
displayName := "/resourceGroups/rg"
accessPackageResourceScope.SetDisplayName(&displayName) 
isRootScope := false
accessPackageResourceScope.SetIsRootScope(&isRootScope) 
originSystem := "AzureResources"
accessPackageResourceScope.SetOriginSystem(&originSystem) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg"
accessPackageResourceScope.SetOriginId(&originId) 
requestBody.SetAccessPackageResourceScope(accessPackageResourceScope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").AccessPackageResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole accessPackageResourceRole = new AccessPackageResourceRole();
accessPackageResourceRole.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475");
accessPackageResourceRole.setDisplayName("Access Review Operator Service Role");
accessPackageResourceRole.setDescription("Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("b09a0288-a83e-4ae6-8a53-bc09aeb966ea");
accessPackageResource.setDescription("Dev");
accessPackageResource.setDisplayName("Dev");
accessPackageResource.setResourceType("Subscription");
accessPackageResource.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
accessPackageResource.setOriginSystem("AzureResources");
accessPackageResourceRole.setAccessPackageResource(accessPackageResource);
accessPackageResourceRole.setOriginSystem("AzureResources");
accessPackageResourceRole.setType(RoleType.Active);
accessPackageResourceRoleScope.setAccessPackageResourceRole(accessPackageResourceRole);
AccessPackageResourceScope accessPackageResourceScope = new AccessPackageResourceScope();
accessPackageResourceScope.setId("e1e0ec8c-472d-4ec5-a8f9-29e0bc275640");
accessPackageResourceScope.setDescription("/resourceGroups/rg");
accessPackageResourceScope.setDisplayName("/resourceGroups/rg");
accessPackageResourceScope.setIsRootScope(false);
accessPackageResourceScope.setOriginSystem("AzureResources");
accessPackageResourceScope.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg");
accessPackageResourceRoleScope.setAccessPackageResourceScope(accessPackageResourceScope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").accessPackageResourceRoleScopes().post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    accessPackageResourceRole: {
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475',
        displayName: 'Access Review Operator Service Role',
        description: 'Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.',
        accessPackageResource: {
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
    accessPackageResourceScope: {
        id: 'e1e0ec8c-472d-4ec5-a8f9-29e0bc275640',
        description: '/resourceGroups/rg',
        displayName: '/resourceGroups/rg',
        isRootScope: false,
        originSystem: 'AzureResources',
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/accessPackageResourceRoleScopes')
	.version('beta')
	.post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\RoleType;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$accessPackageResourceRole = new AccessPackageResourceRole();
$accessPackageResourceRole->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475');
$accessPackageResourceRole->setDisplayName('Access Review Operator Service Role');
$accessPackageResourceRole->setDescription('Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.');
$accessPackageResourceRoleAccessPackageResource = new AccessPackageResource();
$accessPackageResourceRoleAccessPackageResource->setId('b09a0288-a83e-4ae6-8a53-bc09aeb966ea');
$accessPackageResourceRoleAccessPackageResource->setDescription('Dev');
$accessPackageResourceRoleAccessPackageResource->setDisplayName('Dev');
$accessPackageResourceRoleAccessPackageResource->setResourceType('Subscription');
$accessPackageResourceRoleAccessPackageResource->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$accessPackageResourceRoleAccessPackageResource->setOriginSystem('AzureResources');
$accessPackageResourceRole->setAccessPackageResource($accessPackageResourceRoleAccessPackageResource);
$accessPackageResourceRole->setOriginSystem('AzureResources');
$accessPackageResourceRole->setType(new RoleType('active'));
$requestBody->setAccessPackageResourceRole($accessPackageResourceRole);
$accessPackageResourceScope = new AccessPackageResourceScope();
$accessPackageResourceScope->setId('e1e0ec8c-472d-4ec5-a8f9-29e0bc275640');
$accessPackageResourceScope->setDescription('/resourceGroups/rg');
$accessPackageResourceScope->setDisplayName('/resourceGroups/rg');
$accessPackageResourceScope->setIsRootScope(false);
$accessPackageResourceScope->setOriginSystem('AzureResources');
$accessPackageResourceScope->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg');
$requestBody->setAccessPackageResourceScope($accessPackageResourceScope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->accessPackageResourceRoleScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageResourceRole = @{
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
		displayName = "Access Review Operator Service Role"
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
		accessPackageResource = @{
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
	accessPackageResourceScope = @{
		id = "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640"
		description = "/resourceGroups/rg"
		displayName = "/resourceGroups/rg"
		isRootScope = $false
		originSystem = "AzureResources"
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph_beta.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.role_type import RoleType
from msgraph_beta.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	access_package_resource_role = AccessPackageResourceRole(
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		display_name = "Access Review Operator Service Role",
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		access_package_resource = AccessPackageResource(
			id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			description = "Dev",
			display_name = "Dev",
			resource_type = "Subscription",
			origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			origin_system = "AzureResources",
		),
		origin_system = "AzureResources",
		type = RoleType.Active,
	),
	access_package_resource_scope = AccessPackageResourceScope(
		id = "e1e0ec8c-472d-4ec5-a8f9-29e0bc275640",
		description = "/resourceGroups/rg",
		display_name = "/resourceGroups/rg",
		is_root_scope = False,
		origin_system = "AzureResources",
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/resourceGroups/rg",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').access_package_resource_role_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "34b2d7de-e8d6-4ba8-843e-a03546feac63_e1e0ec8c-472d-4ec5-a8f9-29e0bc275640",
  "createdBy": "admin@example.com",
  "createdDateTime": "2026-02-09T22:31:55.3690356Z",
  "modifiedBy": "admin@example.com",
  "modifiedDateTime": "2026-02-09T22:31:55.3690356Z"
}
```

### Example 6: Add Eligible Management Group Resource Role to an access package

#### Request

The following example shows a request to add an eligible Management Group scoped to a Resource Role to an access package.

Before this request, you must have already added the access package resource `c347ca9b-a9cc-4df9-bc3c-00c8e0297692` for the Management Group `test-mgmtgroup` to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageresourcerequests?view=graph-rest-beta).

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/accessPackageResourceRoleScopes
Content-type: application/json

{
    "accessPackageResourceRole": {
        "id": "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e",
        "originId": "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
        "displayName": "Access Review Operator Service Role",
        "description": "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
        "accessPackageResource": {
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
    "accessPackageResourceScope": {
        "id": "338613b3-b410-4c6d-b5e9-45590bc8a357",
        "displayName": "Root",
        "description": "Root Scope",
        "originId": "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
        "originSystem": "AzureResources",
        "isRootScope": true
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	AccessPackageResourceRole = new AccessPackageResourceRole
	{
		Id = "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e",
		OriginId = "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		DisplayName = "Access Review Operator Service Role",
		Description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		AccessPackageResource = new AccessPackageResource
		{
			Id = "c347ca9b-a9cc-4df9-bc3c-00c8e0297692",
			Description = "test-mgmtgroup",
			DisplayName = "test-mgmtgroup",
			ResourceType = "ManagementGroup",
			OriginId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
			OriginSystem = "AzureResources",
		},
		OriginSystem = "AzureResources",
		Type = RoleType.Eligible,
	},
	AccessPackageResourceScope = new AccessPackageResourceScope
	{
		Id = "338613b3-b410-4c6d-b5e9-45590bc8a357",
		DisplayName = "Root",
		Description = "Root Scope",
		OriginId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		OriginSystem = "AzureResources",
		IsRootScope = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].AccessPackageResourceRoleScopes.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
accessPackageResourceRole := graphmodels.NewAccessPackageResourceRole()
id := "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e"
accessPackageResourceRole.SetId(&id) 
originId := "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
accessPackageResourceRole.SetOriginId(&originId) 
displayName := "Access Review Operator Service Role"
accessPackageResourceRole.SetDisplayName(&displayName) 
description := "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
accessPackageResourceRole.SetDescription(&description) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := "c347ca9b-a9cc-4df9-bc3c-00c8e0297692"
accessPackageResource.SetId(&id) 
description := "test-mgmtgroup"
accessPackageResource.SetDescription(&description) 
displayName := "test-mgmtgroup"
accessPackageResource.SetDisplayName(&displayName) 
resourceType := "ManagementGroup"
accessPackageResource.SetResourceType(&resourceType) 
originId := "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AzureResources"
accessPackageResource.SetOriginSystem(&originSystem) 
accessPackageResourceRole.SetAccessPackageResource(accessPackageResource)
originSystem := "AzureResources"
accessPackageResourceRole.SetOriginSystem(&originSystem) 
type := graphmodels.ELIGIBLE_ROLETYPE 
accessPackageResourceRole.SetType(&type) 
requestBody.SetAccessPackageResourceRole(accessPackageResourceRole)
accessPackageResourceScope := graphmodels.NewAccessPackageResourceScope()
id := "338613b3-b410-4c6d-b5e9-45590bc8a357"
accessPackageResourceScope.SetId(&id) 
displayName := "Root"
accessPackageResourceScope.SetDisplayName(&displayName) 
description := "Root Scope"
accessPackageResourceScope.SetDescription(&description) 
originId := "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
accessPackageResourceScope.SetOriginId(&originId) 
originSystem := "AzureResources"
accessPackageResourceScope.SetOriginSystem(&originSystem) 
isRootScope := true
accessPackageResourceScope.SetIsRootScope(&isRootScope) 
requestBody.SetAccessPackageResourceScope(accessPackageResourceScope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").AccessPackageResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole accessPackageResourceRole = new AccessPackageResourceRole();
accessPackageResourceRole.setId("055c76c1-a466-4f1a-9279-4a2ccaa7ac3e");
accessPackageResourceRole.setOriginId("/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475");
accessPackageResourceRole.setDisplayName("Access Review Operator Service Role");
accessPackageResourceRole.setDescription("Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("c347ca9b-a9cc-4df9-bc3c-00c8e0297692");
accessPackageResource.setDescription("test-mgmtgroup");
accessPackageResource.setDisplayName("test-mgmtgroup");
accessPackageResource.setResourceType("ManagementGroup");
accessPackageResource.setOriginId("/providers/Microsoft.Management/managementGroups/test-mgmtgroup");
accessPackageResource.setOriginSystem("AzureResources");
accessPackageResourceRole.setAccessPackageResource(accessPackageResource);
accessPackageResourceRole.setOriginSystem("AzureResources");
accessPackageResourceRole.setType(RoleType.Eligible);
accessPackageResourceRoleScope.setAccessPackageResourceRole(accessPackageResourceRole);
AccessPackageResourceScope accessPackageResourceScope = new AccessPackageResourceScope();
accessPackageResourceScope.setId("338613b3-b410-4c6d-b5e9-45590bc8a357");
accessPackageResourceScope.setDisplayName("Root");
accessPackageResourceScope.setDescription("Root Scope");
accessPackageResourceScope.setOriginId("/providers/Microsoft.Management/managementGroups/test-mgmtgroup");
accessPackageResourceScope.setOriginSystem("AzureResources");
accessPackageResourceScope.setIsRootScope(true);
accessPackageResourceRoleScope.setAccessPackageResourceScope(accessPackageResourceScope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").accessPackageResourceRoleScopes().post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    accessPackageResourceRole: {
        id: '055c76c1-a466-4f1a-9279-4a2ccaa7ac3e',
        originId: '/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475',
        displayName: 'Access Review Operator Service Role',
        description: 'Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.',
        accessPackageResource: {
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
    accessPackageResourceScope: {
        id: '338613b3-b410-4c6d-b5e9-45590bc8a357',
        displayName: 'Root',
        description: 'Root Scope',
        originId: '/providers/Microsoft.Management/managementGroups/test-mgmtgroup',
        originSystem: 'AzureResources',
        isRootScope: true
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/accessPackageResourceRoleScopes')
	.version('beta')
	.post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\RoleType;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$accessPackageResourceRole = new AccessPackageResourceRole();
$accessPackageResourceRole->setId('055c76c1-a466-4f1a-9279-4a2ccaa7ac3e');
$accessPackageResourceRole->setOriginId('/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475');
$accessPackageResourceRole->setDisplayName('Access Review Operator Service Role');
$accessPackageResourceRole->setDescription('Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.');
$accessPackageResourceRoleAccessPackageResource = new AccessPackageResource();
$accessPackageResourceRoleAccessPackageResource->setId('c347ca9b-a9cc-4df9-bc3c-00c8e0297692');
$accessPackageResourceRoleAccessPackageResource->setDescription('test-mgmtgroup');
$accessPackageResourceRoleAccessPackageResource->setDisplayName('test-mgmtgroup');
$accessPackageResourceRoleAccessPackageResource->setResourceType('ManagementGroup');
$accessPackageResourceRoleAccessPackageResource->setOriginId('/providers/Microsoft.Management/managementGroups/test-mgmtgroup');
$accessPackageResourceRoleAccessPackageResource->setOriginSystem('AzureResources');
$accessPackageResourceRole->setAccessPackageResource($accessPackageResourceRoleAccessPackageResource);
$accessPackageResourceRole->setOriginSystem('AzureResources');
$accessPackageResourceRole->setType(new RoleType('eligible'));
$requestBody->setAccessPackageResourceRole($accessPackageResourceRole);
$accessPackageResourceScope = new AccessPackageResourceScope();
$accessPackageResourceScope->setId('338613b3-b410-4c6d-b5e9-45590bc8a357');
$accessPackageResourceScope->setDisplayName('Root');
$accessPackageResourceScope->setDescription('Root Scope');
$accessPackageResourceScope->setOriginId('/providers/Microsoft.Management/managementGroups/test-mgmtgroup');
$accessPackageResourceScope->setOriginSystem('AzureResources');
$accessPackageResourceScope->setIsRootScope(true);
$requestBody->setAccessPackageResourceScope($accessPackageResourceScope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->accessPackageResourceRoleScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageResourceRole = @{
		id = "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e"
		originId = "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
		displayName = "Access Review Operator Service Role"
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
		accessPackageResource = @{
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
	accessPackageResourceScope = @{
		id = "338613b3-b410-4c6d-b5e9-45590bc8a357"
		displayName = "Root"
		description = "Root Scope"
		originId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
		originSystem = "AzureResources"
		isRootScope = $true
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph_beta.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.role_type import RoleType
from msgraph_beta.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	access_package_resource_role = AccessPackageResourceRole(
		id = "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e",
		origin_id = "/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		display_name = "Access Review Operator Service Role",
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		access_package_resource = AccessPackageResource(
			id = "c347ca9b-a9cc-4df9-bc3c-00c8e0297692",
			description = "test-mgmtgroup",
			display_name = "test-mgmtgroup",
			resource_type = "ManagementGroup",
			origin_id = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
			origin_system = "AzureResources",
		),
		origin_system = "AzureResources",
		type = RoleType.Eligible,
	),
	access_package_resource_scope = AccessPackageResourceScope(
		id = "338613b3-b410-4c6d-b5e9-45590bc8a357",
		display_name = "Root",
		description = "Root Scope",
		origin_id = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		origin_system = "AzureResources",
		is_root_scope = True,
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').access_package_resource_role_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "055c76c1-a466-4f1a-9279-4a2ccaa7ac3e_338613b3-b410-4c6d-b5e9-45590bc8a357",
  "createdBy": "admin@example.com",
  "createdDateTime": "2026-02-09T22:23:14.8561335Z",
  "modifiedBy": "admin@example.com",
  "modifiedDateTime": "2026-02-09T22:23:14.8561335Z"
}
```

### Example 7: Add Active Subscription Resource Role to access package

#### Request

The following example shows a request to Add Active Subscription Resource Role to an access package scoped to a Resource Role to an access package.

Before this request, you must have already added the access package resource `b09a0288-a83e-4ae6-8a53-bc09aeb966ea` for the Subscription `828b526f-c769-4b19-9797-734b4843b978` to the access package catalog containing this access package. The resource could have been added to the catalog by [creating an access package resource request](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageresourcerequests?view=graph-rest-beta).

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/accessPackageResourceRoleScopes
Content-type: application/json

{
    "accessPackageResourceRole": {
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
        "displayName": "Access Review Operator Service Role",
        "description": "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
        "accessPackageResource": {
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
    "accessPackageResourceScope": {
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
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRoleScope
{
	AccessPackageResourceRole = new AccessPackageResourceRole
	{
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		DisplayName = "Access Review Operator Service Role",
		Description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		AccessPackageResource = new AccessPackageResource
		{
			Id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			Description = "Dev",
			DisplayName = "Dev",
			ResourceType = "Subscription",
			OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			OriginSystem = "AzureResources",
		},
		OriginSystem = "AzureResources",
		Type = RoleType.Active,
	},
	AccessPackageResourceScope = new AccessPackageResourceScope
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
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackages["{accessPackage-id}"].AccessPackageResourceRoleScopes.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessPackageResourceRoleScope()
accessPackageResourceRole := graphmodels.NewAccessPackageResourceRole()
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
accessPackageResourceRole.SetOriginId(&originId) 
displayName := "Access Review Operator Service Role"
accessPackageResourceRole.SetDisplayName(&displayName) 
description := "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
accessPackageResourceRole.SetDescription(&description) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := "b09a0288-a83e-4ae6-8a53-bc09aeb966ea"
accessPackageResource.SetId(&id) 
description := "Dev"
accessPackageResource.SetDescription(&description) 
displayName := "Dev"
accessPackageResource.SetDisplayName(&displayName) 
resourceType := "Subscription"
accessPackageResource.SetResourceType(&resourceType) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AzureResources"
accessPackageResource.SetOriginSystem(&originSystem) 
accessPackageResourceRole.SetAccessPackageResource(accessPackageResource)
originSystem := "AzureResources"
accessPackageResourceRole.SetOriginSystem(&originSystem) 
type := graphmodels.ACTIVE_ROLETYPE 
accessPackageResourceRole.SetType(&type) 
requestBody.SetAccessPackageResourceRole(accessPackageResourceRole)
accessPackageResourceScope := graphmodels.NewAccessPackageResourceScope()
id := "c66c1e22-1093-46fb-a8a8-c0e334113ca4"
accessPackageResourceScope.SetId(&id) 
description := "Root"
accessPackageResourceScope.SetDescription(&description) 
displayName := "Root"
accessPackageResourceScope.SetDisplayName(&displayName) 
isRootScope := true
accessPackageResourceScope.SetIsRootScope(&isRootScope) 
originSystem := "AzureResources"
accessPackageResourceScope.SetOriginSystem(&originSystem) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
accessPackageResourceScope.SetOriginId(&originId) 
requestBody.SetAccessPackageResourceScope(accessPackageResourceScope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRoleScopes, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackages().ByAccessPackageId("accessPackage-id").AccessPackageResourceRoleScopes().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRoleScope accessPackageResourceRoleScope = new AccessPackageResourceRoleScope();
AccessPackageResourceRole accessPackageResourceRole = new AccessPackageResourceRole();
accessPackageResourceRole.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475");
accessPackageResourceRole.setDisplayName("Access Review Operator Service Role");
accessPackageResourceRole.setDescription("Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("b09a0288-a83e-4ae6-8a53-bc09aeb966ea");
accessPackageResource.setDescription("Dev");
accessPackageResource.setDisplayName("Dev");
accessPackageResource.setResourceType("Subscription");
accessPackageResource.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
accessPackageResource.setOriginSystem("AzureResources");
accessPackageResourceRole.setAccessPackageResource(accessPackageResource);
accessPackageResourceRole.setOriginSystem("AzureResources");
accessPackageResourceRole.setType(RoleType.Active);
accessPackageResourceRoleScope.setAccessPackageResourceRole(accessPackageResourceRole);
AccessPackageResourceScope accessPackageResourceScope = new AccessPackageResourceScope();
accessPackageResourceScope.setId("c66c1e22-1093-46fb-a8a8-c0e334113ca4");
accessPackageResourceScope.setDescription("Root");
accessPackageResourceScope.setDisplayName("Root");
accessPackageResourceScope.setIsRootScope(true);
accessPackageResourceScope.setOriginSystem("AzureResources");
accessPackageResourceScope.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
accessPackageResourceRoleScope.setAccessPackageResourceScope(accessPackageResourceScope);
AccessPackageResourceRoleScope result = graphClient.identityGovernance().entitlementManagement().accessPackages().byAccessPackageId("{accessPackage-id}").accessPackageResourceRoleScopes().post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRoleScope = {
    accessPackageResourceRole: {
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475',
        displayName: 'Access Review Operator Service Role',
        description: 'Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.',
        accessPackageResource: {
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
    accessPackageResourceScope: {
        id: 'c66c1e22-1093-46fb-a8a8-c0e334113ca4',
        description: 'Root',
        displayName: 'Root',
        isRootScope: true,
        originSystem: 'AzureResources',
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackages/5f7f4c7d-b3f5-4988-a17b-3f09b6f5a9ee/accessPackageResourceRoleScopes')
	.version('beta')
	.post(accessPackageResourceRoleScope);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRoleScope;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRole;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\RoleType;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRoleScope();
$accessPackageResourceRole = new AccessPackageResourceRole();
$accessPackageResourceRole->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475');
$accessPackageResourceRole->setDisplayName('Access Review Operator Service Role');
$accessPackageResourceRole->setDescription('Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.');
$accessPackageResourceRoleAccessPackageResource = new AccessPackageResource();
$accessPackageResourceRoleAccessPackageResource->setId('b09a0288-a83e-4ae6-8a53-bc09aeb966ea');
$accessPackageResourceRoleAccessPackageResource->setDescription('Dev');
$accessPackageResourceRoleAccessPackageResource->setDisplayName('Dev');
$accessPackageResourceRoleAccessPackageResource->setResourceType('Subscription');
$accessPackageResourceRoleAccessPackageResource->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$accessPackageResourceRoleAccessPackageResource->setOriginSystem('AzureResources');
$accessPackageResourceRole->setAccessPackageResource($accessPackageResourceRoleAccessPackageResource);
$accessPackageResourceRole->setOriginSystem('AzureResources');
$accessPackageResourceRole->setType(new RoleType('active'));
$requestBody->setAccessPackageResourceRole($accessPackageResourceRole);
$accessPackageResourceScope = new AccessPackageResourceScope();
$accessPackageResourceScope->setId('c66c1e22-1093-46fb-a8a8-c0e334113ca4');
$accessPackageResourceScope->setDescription('Root');
$accessPackageResourceScope->setDisplayName('Root');
$accessPackageResourceScope->setIsRootScope(true);
$accessPackageResourceScope->setOriginSystem('AzureResources');
$accessPackageResourceScope->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$requestBody->setAccessPackageResourceScope($accessPackageResourceScope);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackages()->byAccessPackageId('accessPackage-id')->accessPackageResourceRoleScopes()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	accessPackageResourceRole = @{
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475"
		displayName = "Access Review Operator Service Role"
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process."
		accessPackageResource = @{
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
	accessPackageResourceScope = @{
		id = "c66c1e22-1093-46fb-a8a8-c0e334113ca4"
		description = "Root"
		displayName = "Root"
		isRootScope = $true
		originSystem = "AzureResources"
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRoleScope -AccessPackageId $accessPackageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_role_scope import AccessPackageResourceRoleScope
from msgraph_beta.generated.models.access_package_resource_role import AccessPackageResourceRole
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.role_type import RoleType
from msgraph_beta.generated.models.access_package_resource_scope import AccessPackageResourceScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRoleScope(
	access_package_resource_role = AccessPackageResourceRole(
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978/providers/Microsoft.Authorization/roleDefinitions/76cc9ee4-d5d3-4a45-a930-26add3d73475",
		display_name = "Access Review Operator Service Role",
		description = "Lets you grant Access Review System app permissions to discover and revoke access as needed by the access review process.",
		access_package_resource = AccessPackageResource(
			id = "b09a0288-a83e-4ae6-8a53-bc09aeb966ea",
			description = "Dev",
			display_name = "Dev",
			resource_type = "Subscription",
			origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
			origin_system = "AzureResources",
		),
		origin_system = "AzureResources",
		type = RoleType.Active,
	),
	access_package_resource_scope = AccessPackageResourceScope(
		id = "c66c1e22-1093-46fb-a8a8-c0e334113ca4",
		description = "Root",
		display_name = "Root",
		is_root_scope = True,
		origin_system = "AzureResources",
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_packages.by_access_package_id('accessPackage-id').access_package_resource_role_scopes.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "34b2d7de-e8d6-4ba8-843e-a03546feac63_c66c1e22-1093-46fb-a8a8-c0e334113ca4",
  "createdBy": "admin@example.com",
  "createdDateTime": "2026-02-09T22:29:40.3420825Z",
  "modifiedBy": "admin@example.com",
  "modifiedDateTime": "2026-02-09T22:29:40.3420825Z"
}
```
