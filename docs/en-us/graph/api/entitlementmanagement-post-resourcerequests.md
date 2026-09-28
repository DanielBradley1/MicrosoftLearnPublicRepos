<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-resourcerequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Create accessPackageResourceRequest

Namespace: microsoft.graph

Create a new [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0) object to request the addition of a resource to an access package catalog, update of a resource, or the removal of a resource from a catalog. A resource must be included in an access package catalog before a [role of that resource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-1.0) can be added to an access package.

- To add a Microsoft Entra group as a resource to a catalog, set the **requestType** to be `adminAdd`, and a `resource` representing the resource. The value of the **originSystem** property within the `resource` should be `AadGroup` and the value of the **originId** is the identifier of the group.
- To add a Microsoft Entra application as a resource to a catalog, set the **requestType** to be `adminAdd`, and a `resource` representing the resource. The value of the **originSystem** property within the `resource` should be `AadApplication` and the value of the **originId** is the identifier of the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0).
- To add a SharePoint Online site as a resource to a catalog, set the **requestType** to be `adminAdd`, and a `resource` representing the resource. The value of the **originSystem** property within the `resource` should be `SharePointOnline` and the value of the **originId** is the URI of the site.
- To remove a resource from a catalog, set the **requestType** to be `adminRemove`, and the `resource` to contain the `id` of the [resource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) object to be removed. The resource object can be retrieved using [list resources](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-resources?view=graph-rest-1.0).

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

In delegated scenarios with work or school accounts, the signed-in user must also be assigned an administrator role with supported role permissions through one of the following options:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog owner*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog owner* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

Additionally you must also have the following permissions on the resource being added:

- To add a Microsoft Entra group as a resource to a catalog:

  - If using delegated permissions, the user requesting to add a group should be an owner of the group or in a directory role that allows them to modify groups.
  - If using application permissions, the application requesting to add the group should also be assigned the `Group.ReadWrite.All` permission.

- To add a Microsoft Entra role as a resource to a catalog:

  - If using delegated permissions, the user who wants to add the role to the catalog needs to be a Global Administrator or a Privileged Role Administrator with Catalog Owner permissions.
  - Applications with the Entitlement Management.ReadWrite.All permissions cannot add Microsoft Entra roles to catalogs unless they also have Global Administrator or Privilege Role Administrator permissions.

- To add a Microsoft Entra application as a resource to a catalog:

  - If using delegated permissions, the user requesting to add an application should be an owner of the application or in a directory role that allows them to modify application role assignments.
  - If using application permissions, the application requesting to add the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) should also be assigned the *Application.ReadWrite.All* permission.

- To add a SharePoint Online site as a resource to a catalog:

  - If using delegated permissions, the user must be assigned the *SharePoint Administrator* role or be an administrator of the SharePoint site.
  - If using application permissions, the application should also be assigned the `Sites.FullControl.All` permission. For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/resourceRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0) object. Include the `resource` relationship with an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) object as part of the request, and a `catalog` object containing its `id`.

If successful, this method returns a `201 Created` response code and a new [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an accessPackageResourceRequest for adding a group as a resource

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
  "requestType": "adminAdd",
  "resource": {
    "displayName": "Test group",
    "originId": "8ab659d0-3839-427d-8c54-5ae92f0b3e2e",
    "originSystem": "AadGroup"
  },
  "catalog": {
    "id": "beedadfe-01d5-4025-910b-84abb9369997"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	Resource = new AccessPackageResource
	{
		DisplayName = "Test group",
		OriginId = "8ab659d0-3839-427d-8c54-5ae92f0b3e2e",
		OriginSystem = "AadGroup",
	},
	Catalog = new AccessPackageCatalog
	{
		Id = "beedadfe-01d5-4025-910b-84abb9369997",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
resource := graphmodels.NewAccessPackageResource()
displayName := "Test group"
resource.SetDisplayName(&displayName) 
originId := "8ab659d0-3839-427d-8c54-5ae92f0b3e2e"
resource.SetOriginId(&originId) 
originSystem := "AadGroup"
resource.SetOriginSystem(&originSystem) 
requestBody.SetResource(resource)
catalog := graphmodels.NewAccessPackageCatalog()
id := "beedadfe-01d5-4025-910b-84abb9369997"
catalog.SetId(&id) 
requestBody.SetCatalog(catalog)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminAdd);
AccessPackageResource resource = new AccessPackageResource();
resource.setDisplayName("Test group");
resource.setOriginId("8ab659d0-3839-427d-8c54-5ae92f0b3e2e");
resource.setOriginSystem("AadGroup");
accessPackageResourceRequest.setResource(resource);
AccessPackageCatalog catalog = new AccessPackageCatalog();
catalog.setId("beedadfe-01d5-4025-910b-84abb9369997");
accessPackageResourceRequest.setCatalog(catalog);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  requestType: 'adminAdd',
  resource: {
    displayName: 'Test group',
    originId: '8ab659d0-3839-427d-8c54-5ae92f0b3e2e',
    originSystem: 'AadGroup'
  },
  catalog: {
    id: 'beedadfe-01d5-4025-910b-84abb9369997'
  }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$resource = new AccessPackageResource();
$resource->setDisplayName('Test group');
$resource->setOriginId('8ab659d0-3839-427d-8c54-5ae92f0b3e2e');
$resource->setOriginSystem('AadGroup');
$requestBody->setResource($resource);
$catalog = new AccessPackageCatalog();
$catalog->setId('beedadfe-01d5-4025-910b-84abb9369997');
$requestBody->setCatalog($catalog);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminAdd"
	resource = @{
		displayName = "Test group"
		originId = "8ab659d0-3839-427d-8c54-5ae92f0b3e2e"
		originSystem = "AadGroup"
	}
	catalog = @{
		id = "beedadfe-01d5-4025-910b-84abb9369997"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	resource = AccessPackageResource(
		display_name = "Test group",
		origin_id = "8ab659d0-3839-427d-8c54-5ae92f0b3e2e",
		origin_system = "AadGroup",
	),
	catalog = AccessPackageCatalog(
		id = "beedadfe-01d5-4025-910b-84abb9369997",
	),
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "acc2294e-f37f-42d3-981d-4e83847ed0ce",
  "requestType": "adminAdd",
  "state": "delivered"
}
```

### Example 2: Create an accessPackageResourceRequest for adding an application as a resource

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
  "requestType": "adminAdd",
  "resource": {
    "originId": "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
    "originSystem": "AadApplication"
  },
  "catalog": {
    "id": "beedadfe-01d5-4025-910b-84abb9369997"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	Resource = new AccessPackageResource
	{
		OriginId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
		OriginSystem = "AadApplication",
	},
	Catalog = new AccessPackageCatalog
	{
		Id = "beedadfe-01d5-4025-910b-84abb9369997",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
resource := graphmodels.NewAccessPackageResource()
originId := "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
resource.SetOriginId(&originId) 
originSystem := "AadApplication"
resource.SetOriginSystem(&originSystem) 
requestBody.SetResource(resource)
catalog := graphmodels.NewAccessPackageCatalog()
id := "beedadfe-01d5-4025-910b-84abb9369997"
catalog.SetId(&id) 
requestBody.SetCatalog(catalog)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminAdd);
AccessPackageResource resource = new AccessPackageResource();
resource.setOriginId("e81d7f57-0840-45e1-894b-f505c1bdcc1f");
resource.setOriginSystem("AadApplication");
accessPackageResourceRequest.setResource(resource);
AccessPackageCatalog catalog = new AccessPackageCatalog();
catalog.setId("beedadfe-01d5-4025-910b-84abb9369997");
accessPackageResourceRequest.setCatalog(catalog);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  requestType: 'adminAdd',
  resource: {
    originId: 'e81d7f57-0840-45e1-894b-f505c1bdcc1f',
    originSystem: 'AadApplication'
  },
  catalog: {
    id: 'beedadfe-01d5-4025-910b-84abb9369997'
  }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$resource = new AccessPackageResource();
$resource->setOriginId('e81d7f57-0840-45e1-894b-f505c1bdcc1f');
$resource->setOriginSystem('AadApplication');
$requestBody->setResource($resource);
$catalog = new AccessPackageCatalog();
$catalog->setId('beedadfe-01d5-4025-910b-84abb9369997');
$requestBody->setCatalog($catalog);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminAdd"
	resource = @{
		originId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
		originSystem = "AadApplication"
	}
	catalog = @{
		id = "beedadfe-01d5-4025-910b-84abb9369997"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	resource = AccessPackageResource(
		origin_id = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
		origin_system = "AadApplication",
	),
	catalog = AccessPackageCatalog(
		id = "beedadfe-01d5-4025-910b-84abb9369997",
	),
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "acc2294e-f37f-42d3-981d-4e83847ed0ce",
  "requestType": "adminAdd",
  "state": "delivered"
}
```

### Example 3: Create an accessPackageResourceRequest for adding a SharePoint Online site as a resource

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
  "requestType": "adminAdd",
  "resource": {
    "originId": "https://microsoft.sharepoint.com/sites/Example",
    "originSystem": "SharePointOnline"
  },
  "catalog": {
    "id": "beedadfe-01d5-4025-910b-84abb9369997"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	Resource = new AccessPackageResource
	{
		OriginId = "https://microsoft.sharepoint.com/sites/Example",
		OriginSystem = "SharePointOnline",
	},
	Catalog = new AccessPackageCatalog
	{
		Id = "beedadfe-01d5-4025-910b-84abb9369997",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
resource := graphmodels.NewAccessPackageResource()
originId := "https://microsoft.sharepoint.com/sites/Example"
resource.SetOriginId(&originId) 
originSystem := "SharePointOnline"
resource.SetOriginSystem(&originSystem) 
requestBody.SetResource(resource)
catalog := graphmodels.NewAccessPackageCatalog()
id := "beedadfe-01d5-4025-910b-84abb9369997"
catalog.SetId(&id) 
requestBody.SetCatalog(catalog)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminAdd);
AccessPackageResource resource = new AccessPackageResource();
resource.setOriginId("https://microsoft.sharepoint.com/sites/Example");
resource.setOriginSystem("SharePointOnline");
accessPackageResourceRequest.setResource(resource);
AccessPackageCatalog catalog = new AccessPackageCatalog();
catalog.setId("beedadfe-01d5-4025-910b-84abb9369997");
accessPackageResourceRequest.setCatalog(catalog);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  requestType: 'adminAdd',
  resource: {
    originId: 'https://microsoft.sharepoint.com/sites/Example',
    originSystem: 'SharePointOnline'
  },
  catalog: {
    id: 'beedadfe-01d5-4025-910b-84abb9369997'
  }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$resource = new AccessPackageResource();
$resource->setOriginId('https://microsoft.sharepoint.com/sites/Example');
$resource->setOriginSystem('SharePointOnline');
$requestBody->setResource($resource);
$catalog = new AccessPackageCatalog();
$catalog->setId('beedadfe-01d5-4025-910b-84abb9369997');
$requestBody->setCatalog($catalog);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminAdd"
	resource = @{
		originId = "https://microsoft.sharepoint.com/sites/Example"
		originSystem = "SharePointOnline"
	}
	catalog = @{
		id = "beedadfe-01d5-4025-910b-84abb9369997"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	resource = AccessPackageResource(
		origin_id = "https://microsoft.sharepoint.com/sites/Example",
		origin_system = "SharePointOnline",
	),
	catalog = AccessPackageCatalog(
		id = "beedadfe-01d5-4025-910b-84abb9369997",
	),
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "acc2294e-f37f-42d3-981d-4e83847ed0ce",
  "requestType": "adminAdd",
  "state": "delivered"
}
```

### Example 4: Create an accessPackageResourceRequest for removing a resource

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
  "requestType": "adminRemove",
  "resource": {
    "id": "1d0bb962-5bb0-4b16-a488-fda7a788b9ec"
  },
  "catalog": {
    "id": "beedadfe-01d5-4025-910b-84abb9369997"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminRemove,
	Resource = new AccessPackageResource
	{
		Id = "1d0bb962-5bb0-4b16-a488-fda7a788b9ec",
	},
	Catalog = new AccessPackageCatalog
	{
		Id = "beedadfe-01d5-4025-910b-84abb9369997",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINREMOVE_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
resource := graphmodels.NewAccessPackageResource()
id := "1d0bb962-5bb0-4b16-a488-fda7a788b9ec"
resource.SetId(&id) 
requestBody.SetResource(resource)
catalog := graphmodels.NewAccessPackageCatalog()
id := "beedadfe-01d5-4025-910b-84abb9369997"
catalog.SetId(&id) 
requestBody.SetCatalog(catalog)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminRemove);
AccessPackageResource resource = new AccessPackageResource();
resource.setId("1d0bb962-5bb0-4b16-a488-fda7a788b9ec");
accessPackageResourceRequest.setResource(resource);
AccessPackageCatalog catalog = new AccessPackageCatalog();
catalog.setId("beedadfe-01d5-4025-910b-84abb9369997");
accessPackageResourceRequest.setCatalog(catalog);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  requestType: 'adminRemove',
  resource: {
    id: '1d0bb962-5bb0-4b16-a488-fda7a788b9ec'
  },
  catalog: {
    id: 'beedadfe-01d5-4025-910b-84abb9369997'
  }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminRemove'));
$resource = new AccessPackageResource();
$resource->setId('1d0bb962-5bb0-4b16-a488-fda7a788b9ec');
$requestBody->setResource($resource);
$catalog = new AccessPackageCatalog();
$catalog->setId('beedadfe-01d5-4025-910b-84abb9369997');
$requestBody->setCatalog($catalog);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminRemove"
	resource = @{
		id = "1d0bb962-5bb0-4b16-a488-fda7a788b9ec"
	}
	catalog = @{
		id = "beedadfe-01d5-4025-910b-84abb9369997"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminRemove,
	resource = AccessPackageResource(
		id = "1d0bb962-5bb0-4b16-a488-fda7a788b9ec",
	),
	catalog = AccessPackageCatalog(
		id = "beedadfe-01d5-4025-910b-84abb9369997",
	),
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "acc2294e-f37f-42d3-981d-4e83847ed0ce",
  "requestType": "adminRemove",
  "state": "delivered"
}
```

### Example 5: Create an accessPackageResourceRequest for updating an application as a resource with attributes

The following example shows a request to update a resource in a catalog, for an application that was already added as a resource, with two attributes.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
  "requestType": "adminUpdate",
  "resource": {
    "originId": "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
    "originSystem": "AadApplication",
    "attributes": [
      {
        "destination": {
          "@odata.type": "microsoft.graph.accessPackageUserDirectoryAttributeStore"
        },
        "name": "officeLocation",
        "source": {
          "@odata.type": "#microsoft.graph.accessPackageResourceAttributeQuestion",
          "question": {
            "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
            "sequence": 1,
            "isRequired": true,
            "isAnswerEditable": true,
            "text": "What office do you work at?",
            "isSingleLineQuestion": true,
            "regexPattern": "[a-zA-Z]+[a-zA-Z\\s]*"
          }
        }
      },
      {
        "destination": {
          "@odata.type": "microsoft.graph.accessPackageUserDirectoryAttributeStore"
        },
        "name": "extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter",
        "source": {
          "@odata.type": "#microsoft.graph.accessPackageResourceAttributeQuestion",
          "question": {
            "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
            "isRequired": false,
            "text": "What is your cost center number?",
            "sequence": 0,
            "isSingleLineQuestion": true,
            "regexPattern": "[0-9]*"
          }
        }
      }
    ]
  },
  "catalog": {
    "id": "beedadfe-01d5-4025-910b-84abb9369997"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminUpdate,
	Resource = new AccessPackageResource
	{
		OriginId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
		OriginSystem = "AadApplication",
		Attributes = new List<AccessPackageResourceAttribute>
		{
			new AccessPackageResourceAttribute
			{
				Destination = new AccessPackageUserDirectoryAttributeStore
				{
					OdataType = "microsoft.graph.accessPackageUserDirectoryAttributeStore",
				},
				Name = "officeLocation",
				Source = new AccessPackageResourceAttributeQuestion
				{
					OdataType = "#microsoft.graph.accessPackageResourceAttributeQuestion",
					Question = new AccessPackageTextInputQuestion
					{
						OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
						Sequence = 1,
						IsRequired = true,
						IsAnswerEditable = true,
						Text = "What office do you work at?",
						IsSingleLineQuestion = true,
						RegexPattern = "[a-zA-Z]+[a-zA-Z\s]*",
					},
				},
			},
			new AccessPackageResourceAttribute
			{
				Destination = new AccessPackageUserDirectoryAttributeStore
				{
					OdataType = "microsoft.graph.accessPackageUserDirectoryAttributeStore",
				},
				Name = "extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter",
				Source = new AccessPackageResourceAttributeQuestion
				{
					OdataType = "#microsoft.graph.accessPackageResourceAttributeQuestion",
					Question = new AccessPackageTextInputQuestion
					{
						OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
						IsRequired = false,
						Text = "What is your cost center number?",
						Sequence = 0,
						IsSingleLineQuestion = true,
						RegexPattern = "[0-9]*",
					},
				},
			},
		},
	},
	Catalog = new AccessPackageCatalog
	{
		Id = "beedadfe-01d5-4025-910b-84abb9369997",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINUPDATE_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
resource := graphmodels.NewAccessPackageResource()
originId := "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
resource.SetOriginId(&originId) 
originSystem := "AadApplication"
resource.SetOriginSystem(&originSystem) 


accessPackageResourceAttribute := graphmodels.NewAccessPackageResourceAttribute()
destination := graphmodels.NewAccessPackageUserDirectoryAttributeStore()
accessPackageResourceAttribute.SetDestination(destination)
name := "officeLocation"
accessPackageResourceAttribute.SetName(&name) 
source := graphmodels.NewAccessPackageResourceAttributeQuestion()
question := graphmodels.NewAccessPackageTextInputQuestion()
sequence := int32(1)
question.SetSequence(&sequence) 
isRequired := true
question.SetIsRequired(&isRequired) 
isAnswerEditable := true
question.SetIsAnswerEditable(&isAnswerEditable) 
text := "What office do you work at?"
question.SetText(&text) 
isSingleLineQuestion := true
question.SetIsSingleLineQuestion(&isSingleLineQuestion) 
regexPattern := "[a-zA-Z]+[a-zA-Z\s]*"
question.SetRegexPattern(&regexPattern) 
source.SetQuestion(question)
accessPackageResourceAttribute.SetSource(source)
accessPackageResourceAttribute1 := graphmodels.NewAccessPackageResourceAttribute()
destination := graphmodels.NewAccessPackageUserDirectoryAttributeStore()
accessPackageResourceAttribute1.SetDestination(destination)
name := "extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter"
accessPackageResourceAttribute1.SetName(&name) 
source := graphmodels.NewAccessPackageResourceAttributeQuestion()
question := graphmodels.NewAccessPackageTextInputQuestion()
isRequired := false
question.SetIsRequired(&isRequired) 
text := "What is your cost center number?"
question.SetText(&text) 
sequence := int32(0)
question.SetSequence(&sequence) 
isSingleLineQuestion := true
question.SetIsSingleLineQuestion(&isSingleLineQuestion) 
regexPattern := "[0-9]*"
question.SetRegexPattern(&regexPattern) 
source.SetQuestion(question)
accessPackageResourceAttribute1.SetSource(source)

attributes := []graphmodels.AccessPackageResourceAttributeable {
	accessPackageResourceAttribute,
	accessPackageResourceAttribute1,
}
resource.SetAttributes(attributes)
requestBody.SetResource(resource)
catalog := graphmodels.NewAccessPackageCatalog()
id := "beedadfe-01d5-4025-910b-84abb9369997"
catalog.SetId(&id) 
requestBody.SetCatalog(catalog)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminUpdate);
AccessPackageResource resource = new AccessPackageResource();
resource.setOriginId("e81d7f57-0840-45e1-894b-f505c1bdcc1f");
resource.setOriginSystem("AadApplication");
LinkedList<AccessPackageResourceAttribute> attributes = new LinkedList<AccessPackageResourceAttribute>();
AccessPackageResourceAttribute accessPackageResourceAttribute = new AccessPackageResourceAttribute();
AccessPackageUserDirectoryAttributeStore destination = new AccessPackageUserDirectoryAttributeStore();
destination.setOdataType("microsoft.graph.accessPackageUserDirectoryAttributeStore");
accessPackageResourceAttribute.setDestination(destination);
accessPackageResourceAttribute.setName("officeLocation");
AccessPackageResourceAttributeQuestion source = new AccessPackageResourceAttributeQuestion();
source.setOdataType("#microsoft.graph.accessPackageResourceAttributeQuestion");
AccessPackageTextInputQuestion question = new AccessPackageTextInputQuestion();
question.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
question.setSequence(1);
question.setIsRequired(true);
question.setIsAnswerEditable(true);
question.setText("What office do you work at?");
question.setIsSingleLineQuestion(true);
question.setRegexPattern("[a-zA-Z]+[a-zA-Z\s]*");
source.setQuestion(question);
accessPackageResourceAttribute.setSource(source);
attributes.add(accessPackageResourceAttribute);
AccessPackageResourceAttribute accessPackageResourceAttribute1 = new AccessPackageResourceAttribute();
AccessPackageUserDirectoryAttributeStore destination1 = new AccessPackageUserDirectoryAttributeStore();
destination1.setOdataType("microsoft.graph.accessPackageUserDirectoryAttributeStore");
accessPackageResourceAttribute1.setDestination(destination1);
accessPackageResourceAttribute1.setName("extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter");
AccessPackageResourceAttributeQuestion source1 = new AccessPackageResourceAttributeQuestion();
source1.setOdataType("#microsoft.graph.accessPackageResourceAttributeQuestion");
AccessPackageTextInputQuestion question1 = new AccessPackageTextInputQuestion();
question1.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
question1.setIsRequired(false);
question1.setText("What is your cost center number?");
question1.setSequence(0);
question1.setIsSingleLineQuestion(true);
question1.setRegexPattern("[0-9]*");
source1.setQuestion(question1);
accessPackageResourceAttribute1.setSource(source1);
attributes.add(accessPackageResourceAttribute1);
resource.setAttributes(attributes);
accessPackageResourceRequest.setResource(resource);
AccessPackageCatalog catalog = new AccessPackageCatalog();
catalog.setId("beedadfe-01d5-4025-910b-84abb9369997");
accessPackageResourceRequest.setCatalog(catalog);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  requestType: 'adminUpdate',
  resource: {
    originId: 'e81d7f57-0840-45e1-894b-f505c1bdcc1f',
    originSystem: 'AadApplication',
    attributes: [
      {
        destination: {
          '@odata.type': 'microsoft.graph.accessPackageUserDirectoryAttributeStore'
        },
        name: 'officeLocation',
        source: {
          '@odata.type': '#microsoft.graph.accessPackageResourceAttributeQuestion',
          question: {
            '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
            sequence: 1,
            isRequired: true,
            isAnswerEditable: true,
            text: 'What office do you work at?',
            isSingleLineQuestion: true,
            regexPattern: '[a-zA-Z]+[a-zA-Z\\s]*'
          }
        }
      },
      {
        destination: {
          '@odata.type': 'microsoft.graph.accessPackageUserDirectoryAttributeStore'
        },
        name: 'extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter',
        source: {
          '@odata.type': '#microsoft.graph.accessPackageResourceAttributeQuestion',
          question: {
            '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
            isRequired: false,
            text: 'What is your cost center number?',
            sequence: 0,
            isSingleLineQuestion: true,
            regexPattern: '[0-9]*'
          }
        }
      }
    ]
  },
  catalog: {
    id: 'beedadfe-01d5-4025-910b-84abb9369997'
  }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageResourceAttribute;
use Microsoft\Graph\Generated\Models\AccessPackageUserDirectoryAttributeStore;
use Microsoft\Graph\Generated\Models\AccessPackageResourceAttributeQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageTextInputQuestion;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminUpdate'));
$resource = new AccessPackageResource();
$resource->setOriginId('e81d7f57-0840-45e1-894b-f505c1bdcc1f');
$resource->setOriginSystem('AadApplication');
$attributesAccessPackageResourceAttribute1 = new AccessPackageResourceAttribute();
$attributesAccessPackageResourceAttribute1Destination = new AccessPackageUserDirectoryAttributeStore();
$attributesAccessPackageResourceAttribute1Destination->setOdataType('microsoft.graph.accessPackageUserDirectoryAttributeStore');
$attributesAccessPackageResourceAttribute1->setDestination($attributesAccessPackageResourceAttribute1Destination);
$attributesAccessPackageResourceAttribute1->setName('officeLocation');
$attributesAccessPackageResourceAttribute1Source = new AccessPackageResourceAttributeQuestion();
$attributesAccessPackageResourceAttribute1Source->setOdataType('#microsoft.graph.accessPackageResourceAttributeQuestion');
$attributesAccessPackageResourceAttribute1SourceQuestion = new AccessPackageTextInputQuestion();
$attributesAccessPackageResourceAttribute1SourceQuestion->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$attributesAccessPackageResourceAttribute1SourceQuestion->setSequence(1);
$attributesAccessPackageResourceAttribute1SourceQuestion->setIsRequired(true);
$attributesAccessPackageResourceAttribute1SourceQuestion->setIsAnswerEditable(true);
$attributesAccessPackageResourceAttribute1SourceQuestion->setText('What office do you work at?');
$attributesAccessPackageResourceAttribute1SourceQuestion->setIsSingleLineQuestion(true);
$attributesAccessPackageResourceAttribute1SourceQuestion->setRegexPattern('[a-zA-Z]+[a-zA-Z\s]*');
$attributesAccessPackageResourceAttribute1Source->setQuestion($attributesAccessPackageResourceAttribute1SourceQuestion);
$attributesAccessPackageResourceAttribute1->setSource($attributesAccessPackageResourceAttribute1Source);
$attributesArray []= $attributesAccessPackageResourceAttribute1;
$attributesAccessPackageResourceAttribute2 = new AccessPackageResourceAttribute();
$attributesAccessPackageResourceAttribute2Destination = new AccessPackageUserDirectoryAttributeStore();
$attributesAccessPackageResourceAttribute2Destination->setOdataType('microsoft.graph.accessPackageUserDirectoryAttributeStore');
$attributesAccessPackageResourceAttribute2->setDestination($attributesAccessPackageResourceAttribute2Destination);
$attributesAccessPackageResourceAttribute2->setName('extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter');
$attributesAccessPackageResourceAttribute2Source = new AccessPackageResourceAttributeQuestion();
$attributesAccessPackageResourceAttribute2Source->setOdataType('#microsoft.graph.accessPackageResourceAttributeQuestion');
$attributesAccessPackageResourceAttribute2SourceQuestion = new AccessPackageTextInputQuestion();
$attributesAccessPackageResourceAttribute2SourceQuestion->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$attributesAccessPackageResourceAttribute2SourceQuestion->setIsRequired(false);
$attributesAccessPackageResourceAttribute2SourceQuestion->setText('What is your cost center number?');
$attributesAccessPackageResourceAttribute2SourceQuestion->setSequence(0);
$attributesAccessPackageResourceAttribute2SourceQuestion->setIsSingleLineQuestion(true);
$attributesAccessPackageResourceAttribute2SourceQuestion->setRegexPattern('[0-9]*');
$attributesAccessPackageResourceAttribute2Source->setQuestion($attributesAccessPackageResourceAttribute2SourceQuestion);
$attributesAccessPackageResourceAttribute2->setSource($attributesAccessPackageResourceAttribute2Source);
$attributesArray []= $attributesAccessPackageResourceAttribute2;
$resource->setAttributes($attributesArray);

$requestBody->setResource($resource);
$catalog = new AccessPackageCatalog();
$catalog->setId('beedadfe-01d5-4025-910b-84abb9369997');
$requestBody->setCatalog($catalog);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminUpdate"
	resource = @{
		originId = "e81d7f57-0840-45e1-894b-f505c1bdcc1f"
		originSystem = "AadApplication"
		attributes = @(
			@{
				destination = @{
					"@odata.type" = "microsoft.graph.accessPackageUserDirectoryAttributeStore"
				}
				name = "officeLocation"
				source = @{
					"@odata.type" = "#microsoft.graph.accessPackageResourceAttributeQuestion"
					question = @{
						"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
						sequence = 
						isRequired = $true
						isAnswerEditable = $true
						text = "What office do you work at?"
						isSingleLineQuestion = $true
						regexPattern = "[a-zA-Z]+[a-zA-Z\s]*"
					}
				}
			}
			@{
				destination = @{
					"@odata.type" = "microsoft.graph.accessPackageUserDirectoryAttributeStore"
				}
				name = "extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter"
				source = @{
					"@odata.type" = "#microsoft.graph.accessPackageResourceAttributeQuestion"
					question = @{
						"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
						isRequired = $false
						text = "What is your cost center number?"
						sequence = 
						isSingleLineQuestion = $true
						regexPattern = "[0-9]*"
					}
				}
			}
		)
	}
	catalog = @{
		id = "beedadfe-01d5-4025-910b-84abb9369997"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_resource_attribute import AccessPackageResourceAttribute
from msgraph.generated.models.access_package_user_directory_attribute_store import AccessPackageUserDirectoryAttributeStore
from msgraph.generated.models.access_package_resource_attribute_question import AccessPackageResourceAttributeQuestion
from msgraph.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminUpdate,
	resource = AccessPackageResource(
		origin_id = "e81d7f57-0840-45e1-894b-f505c1bdcc1f",
		origin_system = "AadApplication",
		attributes = [
			AccessPackageResourceAttribute(
				destination = AccessPackageUserDirectoryAttributeStore(
					odata_type = "microsoft.graph.accessPackageUserDirectoryAttributeStore",
				),
				name = "officeLocation",
				source = AccessPackageResourceAttributeQuestion(
					odata_type = "#microsoft.graph.accessPackageResourceAttributeQuestion",
					question = AccessPackageTextInputQuestion(
						odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
						sequence = 1,
						is_required = True,
						is_answer_editable = True,
						text = "What office do you work at?",
						is_single_line_question = True,
						regex_pattern = "[a-zA-Z]+[a-zA-Z\s]*",
					),
				),
			),
			AccessPackageResourceAttribute(
				destination = AccessPackageUserDirectoryAttributeStore(
					odata_type = "microsoft.graph.accessPackageUserDirectoryAttributeStore",
				),
				name = "extension_e409fedc08ab4807a9eb53ebc0d6cc9f_Expense_CostCenter",
				source = AccessPackageResourceAttributeQuestion(
					odata_type = "#microsoft.graph.accessPackageResourceAttributeQuestion",
					question = AccessPackageTextInputQuestion(
						odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
						is_required = False,
						text = "What is your cost center number?",
						sequence = 0,
						is_single_line_question = True,
						regex_pattern = "[0-9]*",
					),
				),
			),
		],
	),
	catalog = AccessPackageCatalog(
		id = "beedadfe-01d5-4025-910b-84abb9369997",
	),
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "acc2294e-f37f-42d3-981d-4e83847ed0ce",
  "requestType": "adminAdd",
  "state": "delivered"
}
```

### Example 6: Add a Management Group Resource to catalog

#### Request

The following example shows a request for adding a management group resource to a catalog.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
    "requestType": "adminAdd",
    "resource": {
        "displayName": "test-mgmtgroup",
        "description": "test-mgmtgroup",
        "resourceType": "ManagementGroup",
        "originId": "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
        "originSystem": "AzureResources"
    },
    "catalog": {
        "id": "e8368470-afaf-44da-ba86-13a7318f1995"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	Resource = new AccessPackageResource
	{
		DisplayName = "test-mgmtgroup",
		Description = "test-mgmtgroup",
		OriginId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		OriginSystem = "AzureResources",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"resourceType" , "ManagementGroup"
			},
		},
	},
	Catalog = new AccessPackageCatalog
	{
		Id = "e8368470-afaf-44da-ba86-13a7318f1995",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
resource := graphmodels.NewAccessPackageResource()
displayName := "test-mgmtgroup"
resource.SetDisplayName(&displayName) 
description := "test-mgmtgroup"
resource.SetDescription(&description) 
originId := "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
resource.SetOriginId(&originId) 
originSystem := "AzureResources"
resource.SetOriginSystem(&originSystem) 
additionalData := map[string]interface{}{
	"resourceType" : "ManagementGroup", 
}
resource.SetAdditionalData(additionalData)
requestBody.SetResource(resource)
catalog := graphmodels.NewAccessPackageCatalog()
id := "e8368470-afaf-44da-ba86-13a7318f1995"
catalog.SetId(&id) 
requestBody.SetCatalog(catalog)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminAdd);
AccessPackageResource resource = new AccessPackageResource();
resource.setDisplayName("test-mgmtgroup");
resource.setDescription("test-mgmtgroup");
resource.setOriginId("/providers/Microsoft.Management/managementGroups/test-mgmtgroup");
resource.setOriginSystem("AzureResources");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("resourceType", "ManagementGroup");
resource.setAdditionalData(additionalData);
accessPackageResourceRequest.setResource(resource);
AccessPackageCatalog catalog = new AccessPackageCatalog();
catalog.setId("e8368470-afaf-44da-ba86-13a7318f1995");
accessPackageResourceRequest.setCatalog(catalog);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
    requestType: 'adminAdd',
    resource: {
        displayName: 'test-mgmtgroup',
        description: 'test-mgmtgroup',
        resourceType: 'ManagementGroup',
        originId: '/providers/Microsoft.Management/managementGroups/test-mgmtgroup',
        originSystem: 'AzureResources'
    },
    catalog: {
        id: 'e8368470-afaf-44da-ba86-13a7318f1995'
    }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$resource = new AccessPackageResource();
$resource->setDisplayName('test-mgmtgroup');
$resource->setDescription('test-mgmtgroup');
$resource->setOriginId('/providers/Microsoft.Management/managementGroups/test-mgmtgroup');
$resource->setOriginSystem('AzureResources');
$additionalData = [
	'resourceType' => 'ManagementGroup',
];
$resource->setAdditionalData($additionalData);
$requestBody->setResource($resource);
$catalog = new AccessPackageCatalog();
$catalog->setId('e8368470-afaf-44da-ba86-13a7318f1995');
$requestBody->setCatalog($catalog);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminAdd"
	resource = @{
		displayName = "test-mgmtgroup"
		description = "test-mgmtgroup"
		resourceType = "ManagementGroup"
		originId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
		originSystem = "AzureResources"
	}
	catalog = @{
		id = "e8368470-afaf-44da-ba86-13a7318f1995"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	resource = AccessPackageResource(
		display_name = "test-mgmtgroup",
		description = "test-mgmtgroup",
		origin_id = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		origin_system = "AzureResources",
		additional_data = {
				"resource_type" : "ManagementGroup",
		}
	),
	catalog = AccessPackageCatalog(
		id = "e8368470-afaf-44da-ba86-13a7318f1995",
	),
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "99e156fe-d152-4005-b019-6ba816f411ea",
  "requestType": "adminAdd",
  "state": "delivered"
}
```

### Example 7: Add a Subscription Resource to catalog

#### Request

The following example shows a request for adding a Subscription resource to a catalog.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/resourceRequests
Content-type: application/json

{
    "requestType": "adminAdd",
    "resource": {
        "displayName": "Dev",
        "description": "Dev",
        "resourceType": "Subscription",
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
        "originSystem": "AzureResources"
    },
    "catalog": {
        "id": "e8368470-afaf-44da-ba86-13a7318f1995"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageResourceRequest
{
	RequestType = AccessPackageRequestType.AdminAdd,
	Resource = new AccessPackageResource
	{
		DisplayName = "Dev",
		Description = "Dev",
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
		OriginSystem = "AzureResources",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"resourceType" , "Subscription"
			},
		},
	},
	Catalog = new AccessPackageCatalog
	{
		Id = "e8368470-afaf-44da-ba86-13a7318f1995",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.ResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
requestType := graphmodels.ADMINADD_ACCESSPACKAGEREQUESTTYPE 
requestBody.SetRequestType(&requestType) 
resource := graphmodels.NewAccessPackageResource()
displayName := "Dev"
resource.SetDisplayName(&displayName) 
description := "Dev"
resource.SetDescription(&description) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
resource.SetOriginId(&originId) 
originSystem := "AzureResources"
resource.SetOriginSystem(&originSystem) 
additionalData := map[string]interface{}{
	"resourceType" : "Subscription", 
}
resource.SetAdditionalData(additionalData)
requestBody.SetResource(resource)
catalog := graphmodels.NewAccessPackageCatalog()
id := "e8368470-afaf-44da-ba86-13a7318f1995"
catalog.SetId(&id) 
requestBody.SetCatalog(catalog)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().ResourceRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setRequestType(AccessPackageRequestType.AdminAdd);
AccessPackageResource resource = new AccessPackageResource();
resource.setDisplayName("Dev");
resource.setDescription("Dev");
resource.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
resource.setOriginSystem("AzureResources");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("resourceType", "Subscription");
resource.setAdditionalData(additionalData);
accessPackageResourceRequest.setResource(resource);
AccessPackageCatalog catalog = new AccessPackageCatalog();
catalog.setId("e8368470-afaf-44da-ba86-13a7318f1995");
accessPackageResourceRequest.setCatalog(catalog);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().resourceRequests().post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
    requestType: 'adminAdd',
    resource: {
        displayName: 'Dev',
        description: 'Dev',
        resourceType: 'Subscription',
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978',
        originSystem: 'AzureResources'
    },
    catalog: {
        id: 'e8368470-afaf-44da-ba86-13a7318f1995'
    }
};

await client.api('/identityGovernance/entitlementManagement/resourceRequests')
	.post(accessPackageResourceRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Generated\Models\AccessPackageRequestType;
use Microsoft\Graph\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setRequestType(new AccessPackageRequestType('adminAdd'));
$resource = new AccessPackageResource();
$resource->setDisplayName('Dev');
$resource->setDescription('Dev');
$resource->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$resource->setOriginSystem('AzureResources');
$additionalData = [
	'resourceType' => 'Subscription',
];
$resource->setAdditionalData($additionalData);
$requestBody->setResource($resource);
$catalog = new AccessPackageCatalog();
$catalog->setId('e8368470-afaf-44da-ba86-13a7318f1995');
$requestBody->setCatalog($catalog);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->resourceRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	requestType = "adminAdd"
	resource = @{
		displayName = "Dev"
		description = "Dev"
		resourceType = "Subscription"
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
		originSystem = "AzureResources"
	}
	catalog = @{
		id = "e8368470-afaf-44da-ba86-13a7318f1995"
	}
}

New-MgEntitlementManagementResourceRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph.generated.models.access_package_request_type import AccessPackageRequestType
from msgraph.generated.models.access_package_resource import AccessPackageResource
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	request_type = AccessPackageRequestType.AdminAdd,
	resource = AccessPackageResource(
		display_name = "Dev",
		description = "Dev",
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
		origin_system = "AzureResources",
		additional_data = {
				"resource_type" : "Subscription",
		}
	),
	catalog = AccessPackageCatalog(
		id = "e8368470-afaf-44da-ba86-13a7318f1995",
	),
)

result = await graph_client.identity_governance.entitlement_management.resource_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "13ac6518-0597-452c-98ff-59c52b391dae",
  "requestType": "adminAdd",
  "state": "delivered"
}
```
