<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-accesspackageresourcerequests?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create accessPackageResourceRequest

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-beta) object to request the addition of a resource to an access package catalog, update of a resource, or the removal of a resource from a catalog. A resource must be included in an access package catalog before a [role of that resource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-beta) can be added to an access package.

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
  - If using application permissions, the application requesting to add the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta) should also be assigned the *Application.ReadWrite.All* permission.

- To add a SharePoint Online site as a resource to a catalog:

  - If using delegated permissions, the user must be assigned the *SharePoint Administrator* role or be an administrator of the SharePoint site.
  - If using application permissions, the application should also be assigned the `Sites.FullControl.All` permission.

## HTTP request

```http
POST /identityGovernance/entitlementManagement/accessPackageResourceRequests
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-beta) object. Include the `accessPackageResource` relationship with an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-beta) object as part of the request.

To add a Microsoft Entra group as a resource to a catalog, set the **catalogId** to be of the ID of the catalog, **requestType** to be `AdminAdd`, and an `accessPackageResource` representing the resource. The value of the **originSystem** property within the `accessPackageResource` should be `AadGroup` and the value of the **originId** is the identifier of the group. If using delegated permissions, the user requesting to add a group should be an owner of the group or in a directory role which allows them to modify groups. If using application permissions, the application requesting to add the group should also be assigned the `Group.ReadWrite.All` permission.

To add a Microsoft Entra application as a resource to a catalog, set the **catalogId** to be of the ID of the catalog, **requestType** to be `AdminAdd`, and an `accessPackageResource` representing the resource. The value of the **originSystem** property within the `accessPackageResource` should be `AadApplication` and the value of the **originId** is the identifier of the [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta). If using delegated permissions, the user requesting to add an application should be an owner of the application or in a directory role which allows them to modify application role assignments.

To add a SharePoint Online site as a resource to a catalog, set the **catalogId** to be of the ID of the catalog, **requestType** to be `AdminAdd`, and an `accessPackageResource` representing the resource. The value of the **originSystem** property within the `accessPackageResource` should be `SharePointOnline` and the value of the **originId** is the URI of the [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-beta). If using delegated permissions, the user should be in the the SharePoint Administrator role. If using application permissions, the application requesting to add the site should also be assigned the `Sites.FullControl.All` permission. To assign the geolocation environment for a multi-geolocation Sharepoint Online resource, include the **accessPackageResourceEnvironment** relationship in the `accessPackageResource` object. This can be done in two ways:

- Use `@odata.bind` annotation to assign the `id` of the `accessPackageResourceEnvironment` to an `accessPackageResourceEnvironment` object.
- Specify the `originId` parameter of the `accessPackageResourceEnvironment` in an `accessPackageResourceEnvironment` object.

To remove a resource from a catalog, set the **catalogId** to be of the ID of the catalog, **requestType** to be `AdminRemove`, and the `accessPackageResource` the resource object to be removed. The resource object can be retrieved using [list accessPackageResources](https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-list-accesspackageresources?view=graph-rest-beta).

## Response

If successful, this method returns a `201 Created` response code and a new [accessPackageResourceRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerequest?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create an accessPackageResourceRequest for adding a site as a resource

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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
  "catalogId":"26ac0c0a-08bc-4a7b-a313-839f58044ba5",
  "requestType": "AdminAdd",
  "justification": "",
  "accessPackageResource": {
     "displayName": "Sales",
     "description": "https://contoso.sharepoint.com/sites/Sales",
     "url": "https://contoso.sharepoint.com/sites/Sales",
     "resourceType": "SharePoint Online Site",
     "originId": "https://contoso.sharepoint.com/sites/Sales",
     "originSystem": "SharePointOnline"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "26ac0c0a-08bc-4a7b-a313-839f58044ba5",
	RequestType = "AdminAdd",
	Justification = "",
	AccessPackageResource = new AccessPackageResource
	{
		DisplayName = "Sales",
		Description = "https://contoso.sharepoint.com/sites/Sales",
		Url = "https://contoso.sharepoint.com/sites/Sales",
		ResourceType = "SharePoint Online Site",
		OriginId = "https://contoso.sharepoint.com/sites/Sales",
		OriginSystem = "SharePointOnline",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "26ac0c0a-08bc-4a7b-a313-839f58044ba5"
requestBody.SetCatalogId(&catalogId) 
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 
justification := ""
requestBody.SetJustification(&justification) 
accessPackageResource := graphmodels.NewAccessPackageResource()
displayName := "Sales"
accessPackageResource.SetDisplayName(&displayName) 
description := "https://contoso.sharepoint.com/sites/Sales"
accessPackageResource.SetDescription(&description) 
url := "https://contoso.sharepoint.com/sites/Sales"
accessPackageResource.SetUrl(&url) 
resourceType := "SharePoint Online Site"
accessPackageResource.SetResourceType(&resourceType) 
originId := "https://contoso.sharepoint.com/sites/Sales"
accessPackageResource.SetOriginId(&originId) 
originSystem := "SharePointOnline"
accessPackageResource.SetOriginSystem(&originSystem) 
requestBody.SetAccessPackageResource(accessPackageResource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("26ac0c0a-08bc-4a7b-a313-839f58044ba5");
accessPackageResourceRequest.setRequestType("AdminAdd");
accessPackageResourceRequest.setJustification("");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setDisplayName("Sales");
accessPackageResource.setDescription("https://contoso.sharepoint.com/sites/Sales");
accessPackageResource.setUrl("https://contoso.sharepoint.com/sites/Sales");
accessPackageResource.setResourceType("SharePoint Online Site");
accessPackageResource.setOriginId("https://contoso.sharepoint.com/sites/Sales");
accessPackageResource.setOriginSystem("SharePointOnline");
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  catalogId: '26ac0c0a-08bc-4a7b-a313-839f58044ba5',
  requestType: 'AdminAdd',
  justification: '',
  accessPackageResource: {
     displayName: 'Sales',
     description: 'https://contoso.sharepoint.com/sites/Sales',
     url: 'https://contoso.sharepoint.com/sites/Sales',
     resourceType: 'SharePoint Online Site',
     originId: 'https://contoso.sharepoint.com/sites/Sales',
     originSystem: 'SharePointOnline'
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('26ac0c0a-08bc-4a7b-a313-839f58044ba5');
$requestBody->setRequestType('AdminAdd');
$requestBody->setJustification('');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setDisplayName('Sales');
$accessPackageResource->setDescription('https://contoso.sharepoint.com/sites/Sales');
$accessPackageResource->setUrl('https://contoso.sharepoint.com/sites/Sales');
$accessPackageResource->setResourceType('SharePoint Online Site');
$accessPackageResource->setOriginId('https://contoso.sharepoint.com/sites/Sales');
$accessPackageResource->setOriginSystem('SharePointOnline');
$requestBody->setAccessPackageResource($accessPackageResource);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "26ac0c0a-08bc-4a7b-a313-839f58044ba5"
	requestType = "AdminAdd"
	justification = ""
	accessPackageResource = @{
		displayName = "Sales"
		description = "https://contoso.sharepoint.com/sites/Sales"
		url = "https://contoso.sharepoint.com/sites/Sales"
		resourceType = "SharePoint Online Site"
		originId = "https://contoso.sharepoint.com/sites/Sales"
		originSystem = "SharePointOnline"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "26ac0c0a-08bc-4a7b-a313-839f58044ba5",
	request_type = "AdminAdd",
	justification = "",
	access_package_resource = AccessPackageResource(
		display_name = "Sales",
		description = "https://contoso.sharepoint.com/sites/Sales",
		url = "https://contoso.sharepoint.com/sites/Sales",
		resource_type = "SharePoint Online Site",
		origin_id = "https://contoso.sharepoint.com/sites/Sales",
		origin_system = "SharePointOnline",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
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
  "catalogId": "26ac0c0a-08bc-4a7b-a313-839f58044ba5",
  "id": "1fe272f0-d463-42aa-a9a8-b07ab50a1c4d",
  "isValidationOnly": false,
  "justification": "",
  "requestState": "Delivered",
  "requestStatus": "Fulfilled",
  "requestType": "AdminAdd"
}
```

### Example 2: Create an accessPackageResourceRequest for adding a site as a resource and assign an accessPackageResourceEnvironment using @odata.bind

#### Request

The following example shows a request. In this example, the `@odata.bind` annotation is used to assign the `id` of the `accessPackageResourceEnvironment` to an `accessPackageResourceEnvironment` object.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
    "catalogId": "de9315c1-272b-4905-924b-cc112ca180c7",
    "accessPackageResource": {
        "displayName": "Community Outreach",
        "description": "https://contoso.sharepoint.com/sites/CSR",
        "resourceType": "SharePoint Online Site",
        "originId": "https://contoso.sharepoint.com/sites/CSR",
        "originSystem": "SharePointOnline",
        "accessPackageResourceEnvironment@odata.bind": "accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57"
    },
    "requestType": "AdminAdd"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "de9315c1-272b-4905-924b-cc112ca180c7",
	AccessPackageResource = new AccessPackageResource
	{
		DisplayName = "Community Outreach",
		Description = "https://contoso.sharepoint.com/sites/CSR",
		ResourceType = "SharePoint Online Site",
		OriginId = "https://contoso.sharepoint.com/sites/CSR",
		OriginSystem = "SharePointOnline",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"accessPackageResourceEnvironment@odata.bind" , "accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57"
			},
		},
	},
	RequestType = "AdminAdd",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "de9315c1-272b-4905-924b-cc112ca180c7"
requestBody.SetCatalogId(&catalogId) 
accessPackageResource := graphmodels.NewAccessPackageResource()
displayName := "Community Outreach"
accessPackageResource.SetDisplayName(&displayName) 
description := "https://contoso.sharepoint.com/sites/CSR"
accessPackageResource.SetDescription(&description) 
resourceType := "SharePoint Online Site"
accessPackageResource.SetResourceType(&resourceType) 
originId := "https://contoso.sharepoint.com/sites/CSR"
accessPackageResource.SetOriginId(&originId) 
originSystem := "SharePointOnline"
accessPackageResource.SetOriginSystem(&originSystem) 
additionalData := map[string]interface{}{
	"accessPackageResourceEnvironment@odata.bind" : "accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57", 
}
accessPackageResource.SetAdditionalData(additionalData)
requestBody.SetAccessPackageResource(accessPackageResource)
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("de9315c1-272b-4905-924b-cc112ca180c7");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setDisplayName("Community Outreach");
accessPackageResource.setDescription("https://contoso.sharepoint.com/sites/CSR");
accessPackageResource.setResourceType("SharePoint Online Site");
accessPackageResource.setOriginId("https://contoso.sharepoint.com/sites/CSR");
accessPackageResource.setOriginSystem("SharePointOnline");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("accessPackageResourceEnvironment@odata.bind", "accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57");
accessPackageResource.setAdditionalData(additionalData);
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
accessPackageResourceRequest.setRequestType("AdminAdd");
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
    catalogId: 'de9315c1-272b-4905-924b-cc112ca180c7',
    accessPackageResource: {
        displayName: 'Community Outreach',
        description: 'https://contoso.sharepoint.com/sites/CSR',
        resourceType: 'SharePoint Online Site',
        originId: 'https://contoso.sharepoint.com/sites/CSR',
        originSystem: 'SharePointOnline',
        'accessPackageResourceEnvironment@odata.bind': 'accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57'
    },
    requestType: 'AdminAdd'
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('de9315c1-272b-4905-924b-cc112ca180c7');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setDisplayName('Community Outreach');
$accessPackageResource->setDescription('https://contoso.sharepoint.com/sites/CSR');
$accessPackageResource->setResourceType('SharePoint Online Site');
$accessPackageResource->setOriginId('https://contoso.sharepoint.com/sites/CSR');
$accessPackageResource->setOriginSystem('SharePointOnline');
$additionalData = [
	'accessPackageResourceEnvironment@odata.bind' => 'accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57',
];
$accessPackageResource->setAdditionalData($additionalData);
$requestBody->setAccessPackageResource($accessPackageResource);
$requestBody->setRequestType('AdminAdd');

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "de9315c1-272b-4905-924b-cc112ca180c7"
	accessPackageResource = @{
		displayName = "Community Outreach"
		description = "https://contoso.sharepoint.com/sites/CSR"
		resourceType = "SharePoint Online Site"
		originId = "https://contoso.sharepoint.com/sites/CSR"
		originSystem = "SharePointOnline"
		"accessPackageResourceEnvironment@odata.bind" = "accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57"
	}
	requestType = "AdminAdd"
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "de9315c1-272b-4905-924b-cc112ca180c7",
	access_package_resource = AccessPackageResource(
		display_name = "Community Outreach",
		description = "https://contoso.sharepoint.com/sites/CSR",
		resource_type = "SharePoint Online Site",
		origin_id = "https://contoso.sharepoint.com/sites/CSR",
		origin_system = "SharePointOnline",
		additional_data = {
				"access_package_resource_environment@odata_bind" : "accessPackageResourceEnvironments/615f2218-678f-471f-a60a-02c2f4f80c57",
		}
	),
	request_type = "AdminAdd",
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/entitlementManagement/accessPackageResourceRequests/$entity",
    "catalogId": "de9315c1-272b-4905-924b-cc112ca180c7",
    "executeImmediately": false,
    "id": "d3f800d5-0dd6-47f3-9e90-ef562c7551dc",
    "requestType": "AdminAdd",
    "requestState": "Delivered",
    "requestStatus": "Fulfilled",
    "isValidationOnly": false,
    "expirationDateTime": null,
    "justification": null
}
```

### Example 3: Create an accessPackageResourceRequest for adding a site as a resource and assign an accessPackageResourceEnvironment using originId

#### Request

The following example shows a request. In this example, the parameters of an `accessPackageResourceEnvironment` are specified in an `accessPackageResourceEnvironment` object.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
    "catalogId": "de9315c1-272b-4905-924b-cc112ca180c7",
    "accessPackageResource": {
        "displayName": "Community Outreach",
        "description": "https://contoso.sharepoint.com/sites/CSR",
        "resourceType": "SharePoint Online Site",
        "originId": "https://contoso.sharepoint.com/sites/CSR",
        "originSystem": "SharePointOnline",
        "accessPackageResourceEnvironment": {
            "originId": "https://contoso-admin.sharepoint.com/"
        }
    },
    "requestType": "AdminAdd"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "de9315c1-272b-4905-924b-cc112ca180c7",
	AccessPackageResource = new AccessPackageResource
	{
		DisplayName = "Community Outreach",
		Description = "https://contoso.sharepoint.com/sites/CSR",
		ResourceType = "SharePoint Online Site",
		OriginId = "https://contoso.sharepoint.com/sites/CSR",
		OriginSystem = "SharePointOnline",
		AccessPackageResourceEnvironment = new AccessPackageResourceEnvironment
		{
			OriginId = "https://contoso-admin.sharepoint.com/",
		},
	},
	RequestType = "AdminAdd",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "de9315c1-272b-4905-924b-cc112ca180c7"
requestBody.SetCatalogId(&catalogId) 
accessPackageResource := graphmodels.NewAccessPackageResource()
displayName := "Community Outreach"
accessPackageResource.SetDisplayName(&displayName) 
description := "https://contoso.sharepoint.com/sites/CSR"
accessPackageResource.SetDescription(&description) 
resourceType := "SharePoint Online Site"
accessPackageResource.SetResourceType(&resourceType) 
originId := "https://contoso.sharepoint.com/sites/CSR"
accessPackageResource.SetOriginId(&originId) 
originSystem := "SharePointOnline"
accessPackageResource.SetOriginSystem(&originSystem) 
accessPackageResourceEnvironment := graphmodels.NewAccessPackageResourceEnvironment()
originId := "https://contoso-admin.sharepoint.com/"
accessPackageResourceEnvironment.SetOriginId(&originId) 
accessPackageResource.SetAccessPackageResourceEnvironment(accessPackageResourceEnvironment)
requestBody.SetAccessPackageResource(accessPackageResource)
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("de9315c1-272b-4905-924b-cc112ca180c7");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setDisplayName("Community Outreach");
accessPackageResource.setDescription("https://contoso.sharepoint.com/sites/CSR");
accessPackageResource.setResourceType("SharePoint Online Site");
accessPackageResource.setOriginId("https://contoso.sharepoint.com/sites/CSR");
accessPackageResource.setOriginSystem("SharePointOnline");
AccessPackageResourceEnvironment accessPackageResourceEnvironment = new AccessPackageResourceEnvironment();
accessPackageResourceEnvironment.setOriginId("https://contoso-admin.sharepoint.com/");
accessPackageResource.setAccessPackageResourceEnvironment(accessPackageResourceEnvironment);
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
accessPackageResourceRequest.setRequestType("AdminAdd");
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
    catalogId: 'de9315c1-272b-4905-924b-cc112ca180c7',
    accessPackageResource: {
        displayName: 'Community Outreach',
        description: 'https://contoso.sharepoint.com/sites/CSR',
        resourceType: 'SharePoint Online Site',
        originId: 'https://contoso.sharepoint.com/sites/CSR',
        originSystem: 'SharePointOnline',
        accessPackageResourceEnvironment: {
            originId: 'https://contoso-admin.sharepoint.com/'
        }
    },
    requestType: 'AdminAdd'
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceEnvironment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('de9315c1-272b-4905-924b-cc112ca180c7');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setDisplayName('Community Outreach');
$accessPackageResource->setDescription('https://contoso.sharepoint.com/sites/CSR');
$accessPackageResource->setResourceType('SharePoint Online Site');
$accessPackageResource->setOriginId('https://contoso.sharepoint.com/sites/CSR');
$accessPackageResource->setOriginSystem('SharePointOnline');
$accessPackageResourceAccessPackageResourceEnvironment = new AccessPackageResourceEnvironment();
$accessPackageResourceAccessPackageResourceEnvironment->setOriginId('https://contoso-admin.sharepoint.com/');
$accessPackageResource->setAccessPackageResourceEnvironment($accessPackageResourceAccessPackageResourceEnvironment);
$requestBody->setAccessPackageResource($accessPackageResource);
$requestBody->setRequestType('AdminAdd');

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "de9315c1-272b-4905-924b-cc112ca180c7"
	accessPackageResource = @{
		displayName = "Community Outreach"
		description = "https://contoso.sharepoint.com/sites/CSR"
		resourceType = "SharePoint Online Site"
		originId = "https://contoso.sharepoint.com/sites/CSR"
		originSystem = "SharePointOnline"
		accessPackageResourceEnvironment = @{
			originId = "https://contoso-admin.sharepoint.com/"
		}
	}
	requestType = "AdminAdd"
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.access_package_resource_environment import AccessPackageResourceEnvironment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "de9315c1-272b-4905-924b-cc112ca180c7",
	access_package_resource = AccessPackageResource(
		display_name = "Community Outreach",
		description = "https://contoso.sharepoint.com/sites/CSR",
		resource_type = "SharePoint Online Site",
		origin_id = "https://contoso.sharepoint.com/sites/CSR",
		origin_system = "SharePointOnline",
		access_package_resource_environment = AccessPackageResourceEnvironment(
			origin_id = "https://contoso-admin.sharepoint.com/",
		),
	),
	request_type = "AdminAdd",
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/entitlementManagement/accessPackageResourceRequests/$entity",
    "catalogId": "de9315c1-272b-4905-924b-cc112ca180c7",
    "executeImmediately": false,
    "id": "eadf3fbb-668c-4c3a-8d84-7c8bd73dc3e4",
    "requestType": "AdminAdd",
    "requestState": "Delivered",
    "requestStatus": "Fulfilled",
    "isValidationOnly": false,
    "expirationDateTime": null,
    "justification": null
}
```

### Example 4: Create an accessPackageResourceRequest for adding a group as a resource

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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{

  "catalogId":"beedadfe-01d5-4025-910b-84abb9369997",
  "requestType": "AdminAdd",
  "accessPackageResource": {
     "originId": "c6294667-7348-4f5a-be73-9d2c65f574f3",
     "originSystem": "AadGroup"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "beedadfe-01d5-4025-910b-84abb9369997",
	RequestType = "AdminAdd",
	AccessPackageResource = new AccessPackageResource
	{
		OriginId = "c6294667-7348-4f5a-be73-9d2c65f574f3",
		OriginSystem = "AadGroup",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "beedadfe-01d5-4025-910b-84abb9369997"
requestBody.SetCatalogId(&catalogId) 
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 
accessPackageResource := graphmodels.NewAccessPackageResource()
originId := "c6294667-7348-4f5a-be73-9d2c65f574f3"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AadGroup"
accessPackageResource.SetOriginSystem(&originSystem) 
requestBody.SetAccessPackageResource(accessPackageResource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("beedadfe-01d5-4025-910b-84abb9369997");
accessPackageResourceRequest.setRequestType("AdminAdd");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setOriginId("c6294667-7348-4f5a-be73-9d2c65f574f3");
accessPackageResource.setOriginSystem("AadGroup");
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {

  catalogId: 'beedadfe-01d5-4025-910b-84abb9369997',
  requestType: 'AdminAdd',
  accessPackageResource: {
     originId: 'c6294667-7348-4f5a-be73-9d2c65f574f3',
     originSystem: 'AadGroup'
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('beedadfe-01d5-4025-910b-84abb9369997');
$requestBody->setRequestType('AdminAdd');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setOriginId('c6294667-7348-4f5a-be73-9d2c65f574f3');
$accessPackageResource->setOriginSystem('AadGroup');
$requestBody->setAccessPackageResource($accessPackageResource);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "beedadfe-01d5-4025-910b-84abb9369997"
	requestType = "AdminAdd"
	accessPackageResource = @{
		originId = "c6294667-7348-4f5a-be73-9d2c65f574f3"
		originSystem = "AadGroup"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "beedadfe-01d5-4025-910b-84abb9369997",
	request_type = "AdminAdd",
	access_package_resource = AccessPackageResource(
		origin_id = "c6294667-7348-4f5a-be73-9d2c65f574f3",
		origin_system = "AadGroup",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
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
  "catalogId": "beedadfe-01d5-4025-910b-84abb9369997",
  "id": "acc2294e-f37f-42d3-981d-4e83847ed0ce",
  "requestType": "AdminAdd",
  "requestState": "Delivered",
  "requestStatus": "Fulfilled"
}
```

### Example 5: Create an accessPackageResourceRequest for removing a resource

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
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
  "catalogId": "beedadfe-01d5-4025-910b-84abb9369997",
  "requestType": "AdminRemove",
  "accessPackageResource": {
    "id": "354078e5-dbce-4894-8af4-0ab274d41662"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "beedadfe-01d5-4025-910b-84abb9369997",
	RequestType = "AdminRemove",
	AccessPackageResource = new AccessPackageResource
	{
		Id = "354078e5-dbce-4894-8af4-0ab274d41662",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "beedadfe-01d5-4025-910b-84abb9369997"
requestBody.SetCatalogId(&catalogId) 
requestType := "AdminRemove"
requestBody.SetRequestType(&requestType) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := "354078e5-dbce-4894-8af4-0ab274d41662"
accessPackageResource.SetId(&id) 
requestBody.SetAccessPackageResource(accessPackageResource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("beedadfe-01d5-4025-910b-84abb9369997");
accessPackageResourceRequest.setRequestType("AdminRemove");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("354078e5-dbce-4894-8af4-0ab274d41662");
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  catalogId: 'beedadfe-01d5-4025-910b-84abb9369997',
  requestType: 'AdminRemove',
  accessPackageResource: {
    id: '354078e5-dbce-4894-8af4-0ab274d41662'
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('beedadfe-01d5-4025-910b-84abb9369997');
$requestBody->setRequestType('AdminRemove');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setId('354078e5-dbce-4894-8af4-0ab274d41662');
$requestBody->setAccessPackageResource($accessPackageResource);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "beedadfe-01d5-4025-910b-84abb9369997"
	requestType = "AdminRemove"
	accessPackageResource = @{
		id = "354078e5-dbce-4894-8af4-0ab274d41662"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "beedadfe-01d5-4025-910b-84abb9369997",
	request_type = "AdminRemove",
	access_package_resource = AccessPackageResource(
		id = "354078e5-dbce-4894-8af4-0ab274d41662",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
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
  "catalogId": "beedadfe-01d5-4025-910b-84abb9369997",
  "id": "65c3340d-defb-49a9-8930-63841fda0e68",
  "requestType": "AdminRemove",
  "requestState": "Delivered",
  "requestStatus": "Fulfilled"
}
```

### Example 6: Create an accessPackageResourceRequest for adding an application

#### Request

The following example shows a request for adding an application to a catalog, including specifying a required attribute of that application.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
  "catalogId": "26ac0c0a-08bc-4a7b-a313-839f58044ba5",
  "requestType": "AdminAdd",
  "justification": "",
  "accessPackageResource": {
      "displayName": "Faculty cafeteria ordering",
      "description": "Example application",
      "url": "https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/",
      "resourceType": "Application",
      "originId": "2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e",
      "originSystem": "AadApplication",
      "attributes": [
        {
          "attributeName": "extension_2b676109c7c74ae2b41549205f1947ed_personalTitle",
          "isEditable": true,
          "isPersistedOnAssignmentRemoval": true,
          "attributeSource": {
              "@odata.type": "#microsoft.graph.accessPackageResourceAttributeQuestion",
              "question": {
                  "@odata.type": "#microsoft.graph.accessPackageTextInputQuestion",
                  "isRequired": false,
                  "sequence": 0,
                  "isSingleLineQuestion": true,
                  "text": {
                      "defaultText": "Title",
                      "localizedTexts": []
                  }
              }
          },
          "attributeDestination": {
              "@odata.type": "#microsoft.graph.accessPackageUserDirectoryAttributeStore"
          }
        }
      ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "26ac0c0a-08bc-4a7b-a313-839f58044ba5",
	RequestType = "AdminAdd",
	Justification = "",
	AccessPackageResource = new AccessPackageResource
	{
		DisplayName = "Faculty cafeteria ordering",
		Description = "Example application",
		Url = "https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/",
		ResourceType = "Application",
		OriginId = "2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e",
		OriginSystem = "AadApplication",
		Attributes = new List<AccessPackageResourceAttribute>
		{
			new AccessPackageResourceAttribute
			{
				AttributeName = "extension_2b676109c7c74ae2b41549205f1947ed_personalTitle",
				IsEditable = true,
				IsPersistedOnAssignmentRemoval = true,
				AttributeSource = new AccessPackageResourceAttributeQuestion
				{
					OdataType = "#microsoft.graph.accessPackageResourceAttributeQuestion",
					Question = new AccessPackageTextInputQuestion
					{
						OdataType = "#microsoft.graph.accessPackageTextInputQuestion",
						IsRequired = false,
						Sequence = 0,
						IsSingleLineQuestion = true,
						Text = new AccessPackageLocalizedContent
						{
							DefaultText = "Title",
							LocalizedTexts = new List<AccessPackageLocalizedText>
							{
							},
						},
					},
				},
				AttributeDestination = new AccessPackageUserDirectoryAttributeStore
				{
					OdataType = "#microsoft.graph.accessPackageUserDirectoryAttributeStore",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "26ac0c0a-08bc-4a7b-a313-839f58044ba5"
requestBody.SetCatalogId(&catalogId) 
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 
justification := ""
requestBody.SetJustification(&justification) 
accessPackageResource := graphmodels.NewAccessPackageResource()
displayName := "Faculty cafeteria ordering"
accessPackageResource.SetDisplayName(&displayName) 
description := "Example application"
accessPackageResource.SetDescription(&description) 
url := "https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/"
accessPackageResource.SetUrl(&url) 
resourceType := "Application"
accessPackageResource.SetResourceType(&resourceType) 
originId := "2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AadApplication"
accessPackageResource.SetOriginSystem(&originSystem) 


accessPackageResourceAttribute := graphmodels.NewAccessPackageResourceAttribute()
attributeName := "extension_2b676109c7c74ae2b41549205f1947ed_personalTitle"
accessPackageResourceAttribute.SetAttributeName(&attributeName) 
isEditable := true
accessPackageResourceAttribute.SetIsEditable(&isEditable) 
isPersistedOnAssignmentRemoval := true
accessPackageResourceAttribute.SetIsPersistedOnAssignmentRemoval(&isPersistedOnAssignmentRemoval) 
attributeSource := graphmodels.NewAccessPackageResourceAttributeQuestion()
question := graphmodels.NewAccessPackageTextInputQuestion()
isRequired := false
question.SetIsRequired(&isRequired) 
sequence := int32(0)
question.SetSequence(&sequence) 
isSingleLineQuestion := true
question.SetIsSingleLineQuestion(&isSingleLineQuestion) 
text := graphmodels.NewAccessPackageLocalizedContent()
defaultText := "Title"
text.SetDefaultText(&defaultText) 
localizedTexts := []graphmodels.AccessPackageLocalizedTextable {

}
text.SetLocalizedTexts(localizedTexts)
question.SetText(text)
attributeSource.SetQuestion(question)
accessPackageResourceAttribute.SetAttributeSource(attributeSource)
attributeDestination := graphmodels.NewAccessPackageUserDirectoryAttributeStore()
accessPackageResourceAttribute.SetAttributeDestination(attributeDestination)

attributes := []graphmodels.AccessPackageResourceAttributeable {
	accessPackageResourceAttribute,
}
accessPackageResource.SetAttributes(attributes)
requestBody.SetAccessPackageResource(accessPackageResource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("26ac0c0a-08bc-4a7b-a313-839f58044ba5");
accessPackageResourceRequest.setRequestType("AdminAdd");
accessPackageResourceRequest.setJustification("");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setDisplayName("Faculty cafeteria ordering");
accessPackageResource.setDescription("Example application");
accessPackageResource.setUrl("https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/");
accessPackageResource.setResourceType("Application");
accessPackageResource.setOriginId("2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e");
accessPackageResource.setOriginSystem("AadApplication");
LinkedList<AccessPackageResourceAttribute> attributes = new LinkedList<AccessPackageResourceAttribute>();
AccessPackageResourceAttribute accessPackageResourceAttribute = new AccessPackageResourceAttribute();
accessPackageResourceAttribute.setAttributeName("extension_2b676109c7c74ae2b41549205f1947ed_personalTitle");
accessPackageResourceAttribute.setIsEditable(true);
accessPackageResourceAttribute.setIsPersistedOnAssignmentRemoval(true);
AccessPackageResourceAttributeQuestion attributeSource = new AccessPackageResourceAttributeQuestion();
attributeSource.setOdataType("#microsoft.graph.accessPackageResourceAttributeQuestion");
AccessPackageTextInputQuestion question = new AccessPackageTextInputQuestion();
question.setOdataType("#microsoft.graph.accessPackageTextInputQuestion");
question.setIsRequired(false);
question.setSequence(0);
question.setIsSingleLineQuestion(true);
AccessPackageLocalizedContent text = new AccessPackageLocalizedContent();
text.setDefaultText("Title");
LinkedList<AccessPackageLocalizedText> localizedTexts = new LinkedList<AccessPackageLocalizedText>();
text.setLocalizedTexts(localizedTexts);
question.setText(text);
attributeSource.setQuestion(question);
accessPackageResourceAttribute.setAttributeSource(attributeSource);
AccessPackageUserDirectoryAttributeStore attributeDestination = new AccessPackageUserDirectoryAttributeStore();
attributeDestination.setOdataType("#microsoft.graph.accessPackageUserDirectoryAttributeStore");
accessPackageResourceAttribute.setAttributeDestination(attributeDestination);
attributes.add(accessPackageResourceAttribute);
accessPackageResource.setAttributes(attributes);
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  catalogId: '26ac0c0a-08bc-4a7b-a313-839f58044ba5',
  requestType: 'AdminAdd',
  justification: '',
  accessPackageResource: {
      displayName: 'Faculty cafeteria ordering',
      description: 'Example application',
      url: 'https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/',
      resourceType: 'Application',
      originId: '2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e',
      originSystem: 'AadApplication',
      attributes: [
        {
          attributeName: 'extension_2b676109c7c74ae2b41549205f1947ed_personalTitle',
          isEditable: true,
          isPersistedOnAssignmentRemoval: true,
          attributeSource: {
              '@odata.type': '#microsoft.graph.accessPackageResourceAttributeQuestion',
              question: {
                  '@odata.type': '#microsoft.graph.accessPackageTextInputQuestion',
                  isRequired: false,
                  sequence: 0,
                  isSingleLineQuestion: true,
                  text: {
                      defaultText: 'Title',
                      localizedTexts: []
                  }
              }
          },
          attributeDestination: {
              '@odata.type': '#microsoft.graph.accessPackageUserDirectoryAttributeStore'
          }
        }
      ]
  }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceAttribute;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceAttributeQuestion;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageTextInputQuestion;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageLocalizedContent;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageLocalizedText;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageUserDirectoryAttributeStore;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('26ac0c0a-08bc-4a7b-a313-839f58044ba5');
$requestBody->setRequestType('AdminAdd');
$requestBody->setJustification('');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setDisplayName('Faculty cafeteria ordering');
$accessPackageResource->setDescription('Example application');
$accessPackageResource->setUrl('https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/');
$accessPackageResource->setResourceType('Application');
$accessPackageResource->setOriginId('2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e');
$accessPackageResource->setOriginSystem('AadApplication');
$attributesAccessPackageResourceAttribute1 = new AccessPackageResourceAttribute();
$attributesAccessPackageResourceAttribute1->setAttributeName('extension_2b676109c7c74ae2b41549205f1947ed_personalTitle');
$attributesAccessPackageResourceAttribute1->setIsEditable(true);
$attributesAccessPackageResourceAttribute1->setIsPersistedOnAssignmentRemoval(true);
$attributesAccessPackageResourceAttribute1AttributeSource = new AccessPackageResourceAttributeQuestion();
$attributesAccessPackageResourceAttribute1AttributeSource->setOdataType('#microsoft.graph.accessPackageResourceAttributeQuestion');
$attributesAccessPackageResourceAttribute1AttributeSourceQuestion = new AccessPackageTextInputQuestion();
$attributesAccessPackageResourceAttribute1AttributeSourceQuestion->setOdataType('#microsoft.graph.accessPackageTextInputQuestion');
$attributesAccessPackageResourceAttribute1AttributeSourceQuestion->setIsRequired(false);
$attributesAccessPackageResourceAttribute1AttributeSourceQuestion->setSequence(0);
$attributesAccessPackageResourceAttribute1AttributeSourceQuestion->setIsSingleLineQuestion(true);
$attributesAccessPackageResourceAttribute1AttributeSourceQuestionText = new AccessPackageLocalizedContent();
$attributesAccessPackageResourceAttribute1AttributeSourceQuestionText->setDefaultText('Title');
$attributesAccessPackageResourceAttribute1AttributeSourceQuestionText->setLocalizedTexts([	]);
$attributesAccessPackageResourceAttribute1AttributeSourceQuestion->setText($attributesAccessPackageResourceAttribute1AttributeSourceQuestionText);
$attributesAccessPackageResourceAttribute1AttributeSource->setQuestion($attributesAccessPackageResourceAttribute1AttributeSourceQuestion);
$attributesAccessPackageResourceAttribute1->setAttributeSource($attributesAccessPackageResourceAttribute1AttributeSource);
$attributesAccessPackageResourceAttribute1AttributeDestination = new AccessPackageUserDirectoryAttributeStore();
$attributesAccessPackageResourceAttribute1AttributeDestination->setOdataType('#microsoft.graph.accessPackageUserDirectoryAttributeStore');
$attributesAccessPackageResourceAttribute1->setAttributeDestination($attributesAccessPackageResourceAttribute1AttributeDestination);
$attributesArray []= $attributesAccessPackageResourceAttribute1;
$accessPackageResource->setAttributes($attributesArray);

$requestBody->setAccessPackageResource($accessPackageResource);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "26ac0c0a-08bc-4a7b-a313-839f58044ba5"
	requestType = "AdminAdd"
	justification = ""
	accessPackageResource = @{
		displayName = "Faculty cafeteria ordering"
		description = "Example application"
		url = "https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/"
		resourceType = "Application"
		originId = "2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e"
		originSystem = "AadApplication"
		attributes = @(
			@{
				attributeName = "extension_2b676109c7c74ae2b41549205f1947ed_personalTitle"
				isEditable = $true
				isPersistedOnAssignmentRemoval = $true
				attributeSource = @{
					"@odata.type" = "#microsoft.graph.accessPackageResourceAttributeQuestion"
					question = @{
						"@odata.type" = "#microsoft.graph.accessPackageTextInputQuestion"
						isRequired = $false
						sequence = 
						isSingleLineQuestion = $true
						text = @{
							defaultText = "Title"
							localizedTexts = @(
							)
						}
					}
				}
				attributeDestination = @{
					"@odata.type" = "#microsoft.graph.accessPackageUserDirectoryAttributeStore"
				}
			}
		)
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.access_package_resource_attribute import AccessPackageResourceAttribute
from msgraph_beta.generated.models.access_package_resource_attribute_question import AccessPackageResourceAttributeQuestion
from msgraph_beta.generated.models.access_package_text_input_question import AccessPackageTextInputQuestion
from msgraph_beta.generated.models.access_package_localized_content import AccessPackageLocalizedContent
from msgraph_beta.generated.models.access_package_localized_text import AccessPackageLocalizedText
from msgraph_beta.generated.models.access_package_user_directory_attribute_store import AccessPackageUserDirectoryAttributeStore
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "26ac0c0a-08bc-4a7b-a313-839f58044ba5",
	request_type = "AdminAdd",
	justification = "",
	access_package_resource = AccessPackageResource(
		display_name = "Faculty cafeteria ordering",
		description = "Example application",
		url = "https://myapps.microsoft.com/example.com/signin/Faculty%20cafeteria%20ordering/f1e3b407-942d-4934-9a3f-cef1975cb988/",
		resource_type = "Application",
		origin_id = "2f1099a6-d4fc-4cc9-a0ef-ddd3f1bf0b7e",
		origin_system = "AadApplication",
		attributes = [
			AccessPackageResourceAttribute(
				attribute_name = "extension_2b676109c7c74ae2b41549205f1947ed_personalTitle",
				is_editable = True,
				is_persisted_on_assignment_removal = True,
				attribute_source = AccessPackageResourceAttributeQuestion(
					odata_type = "#microsoft.graph.accessPackageResourceAttributeQuestion",
					question = AccessPackageTextInputQuestion(
						odata_type = "#microsoft.graph.accessPackageTextInputQuestion",
						is_required = False,
						sequence = 0,
						is_single_line_question = True,
						text = AccessPackageLocalizedContent(
							default_text = "Title",
							localized_texts = [
							],
						),
					),
				),
				attribute_destination = AccessPackageUserDirectoryAttributeStore(
					odata_type = "#microsoft.graph.accessPackageUserDirectoryAttributeStore",
				),
			),
		],
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
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
  "id": "f0e632ed-afd2-41d3-8d6e-ccefda457e5e",
  "requestType": "AdminAdd",
  "requestState": "Delivered",
  "requestStatus": "Fulfilled"
}
```

### Example 7: Create an accessPackageResourceRequest for adding a SAP IAG Access Rights as a resource

#### Request

The following example shows a request for adding an external origin resource connector to a catalog, including specifying a required attribute of that resource connector.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
  "catalogId": "bcb19bf7-cdf7-4a70-a106-f6543620b2a5",
  "accessPackageResource": {
    "id": "88eb460d-ca08-4eb9-afae-8d60a8b00377",
    "displayName": "SAP IAG Access Rights",
    "description": "This resource represents the business roles of SAP IAG",
    "resourceType": "Business role",
    "originId": "https://iagintgorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com",
    "originSystem": "External",
    "accessPackageResourceScopes": [],
    "externalOriginResourceConnector": {
      "id": "1a53cea5-48bd-467c-af81-a24245b0df2b",
      "displayName": "SAP IAG 10.0",
      "description": "SAP IAG 10.0.0",
      "connectorType": "sapIag",
      "connectionInfo": {
        "@odata.type": "microsoft.graph.externalTokenBasedSapIagConnectionInfo",
        "url": "https://iagigorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com",
        "subscriptionId": "8e072eb5-73f5-4ed2-9324-a734dcb9728",
        "resourceGroup": "SAPResourceGroup",
        "accessTokenUrl": "https://entra-docu-intg-mrrd3gv.authentication.sap.hana.ondemand.com/oauth/token",
        "clientId": "sb-72062308-a7ae-456f-b9a4-24302b8a4aa!b247012|iagapi-iag-intg-space!b11378",
        "keyVaultName": "SAPIAG-KV",
        "secretName": "ClientSecret"
      }
    },
    "accessPackageResourceEnvironment": null
  },
  "requestType": "AdminAdd",
  "history": [],
  "executeImmediately": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "bcb19bf7-cdf7-4a70-a106-f6543620b2a5",
	AccessPackageResource = new AccessPackageResource
	{
		Id = "88eb460d-ca08-4eb9-afae-8d60a8b00377",
		DisplayName = "SAP IAG Access Rights",
		Description = "This resource represents the business roles of SAP IAG",
		ResourceType = "Business role",
		OriginId = "https://iagintgorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com",
		OriginSystem = "External",
		AccessPackageResourceScopes = new List<AccessPackageResourceScope>
		{
		},
		ExternalOriginResourceConnector = new ExternalOriginResourceConnector
		{
			Id = "1a53cea5-48bd-467c-af81-a24245b0df2b",
			DisplayName = "SAP IAG 10.0",
			Description = "SAP IAG 10.0.0",
			ConnectorType = ConnectorType.SapIag,
			ConnectionInfo = new ExternalTokenBasedSapIagConnectionInfo
			{
				OdataType = "microsoft.graph.externalTokenBasedSapIagConnectionInfo",
				Url = "https://iagigorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com",
				SubscriptionId = "8e072eb5-73f5-4ed2-9324-a734dcb9728",
				ResourceGroup = "SAPResourceGroup",
				AccessTokenUrl = "https://entra-docu-intg-mrrd3gv.authentication.sap.hana.ondemand.com/oauth/token",
				ClientId = "sb-72062308-a7ae-456f-b9a4-24302b8a4aa!b247012|iagapi-iag-intg-space!b11378",
				KeyVaultName = "SAPIAG-KV",
				SecretName = "ClientSecret",
			},
		},
		AccessPackageResourceEnvironment = null,
	},
	RequestType = "AdminAdd",
	ExecuteImmediately = true,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"history" , new List<object>
			{
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("bcb19bf7-cdf7-4a70-a106-f6543620b2a5");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("88eb460d-ca08-4eb9-afae-8d60a8b00377");
accessPackageResource.setDisplayName("SAP IAG Access Rights");
accessPackageResource.setDescription("This resource represents the business roles of SAP IAG");
accessPackageResource.setResourceType("Business role");
accessPackageResource.setOriginId("https://iagintgorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com");
accessPackageResource.setOriginSystem("External");
LinkedList<AccessPackageResourceScope> accessPackageResourceScopes = new LinkedList<AccessPackageResourceScope>();
accessPackageResource.setAccessPackageResourceScopes(accessPackageResourceScopes);
ExternalOriginResourceConnector externalOriginResourceConnector = new ExternalOriginResourceConnector();
externalOriginResourceConnector.setId("1a53cea5-48bd-467c-af81-a24245b0df2b");
externalOriginResourceConnector.setDisplayName("SAP IAG 10.0");
externalOriginResourceConnector.setDescription("SAP IAG 10.0.0");
externalOriginResourceConnector.setConnectorType(ConnectorType.SapIag);
ExternalTokenBasedSapIagConnectionInfo connectionInfo = new ExternalTokenBasedSapIagConnectionInfo();
connectionInfo.setOdataType("microsoft.graph.externalTokenBasedSapIagConnectionInfo");
connectionInfo.setUrl("https://iagigorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com");
connectionInfo.setSubscriptionId("8e072eb5-73f5-4ed2-9324-a734dcb9728");
connectionInfo.setResourceGroup("SAPResourceGroup");
connectionInfo.setAccessTokenUrl("https://entra-docu-intg-mrrd3gv.authentication.sap.hana.ondemand.com/oauth/token");
connectionInfo.setClientId("sb-72062308-a7ae-456f-b9a4-24302b8a4aa!b247012|iagapi-iag-intg-space!b11378");
connectionInfo.setKeyVaultName("SAPIAG-KV");
connectionInfo.setSecretName("ClientSecret");
externalOriginResourceConnector.setConnectionInfo(connectionInfo);
accessPackageResource.setExternalOriginResourceConnector(externalOriginResourceConnector);
accessPackageResource.setAccessPackageResourceEnvironment(null);
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
accessPackageResourceRequest.setRequestType("AdminAdd");
accessPackageResourceRequest.setExecuteImmediately(true);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> history = new LinkedList<Object>();
additionalData.put("history", history);
accessPackageResourceRequest.setAdditionalData(additionalData);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
  catalogId: 'bcb19bf7-cdf7-4a70-a106-f6543620b2a5',
  accessPackageResource: {
    id: '88eb460d-ca08-4eb9-afae-8d60a8b00377',
    displayName: 'SAP IAG Access Rights',
    description: 'This resource represents the business roles of SAP IAG',
    resourceType: 'Business role',
    originId: 'https://iagintgorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com',
    originSystem: 'External',
    accessPackageResourceScopes: [],
    externalOriginResourceConnector: {
      id: '1a53cea5-48bd-467c-af81-a24245b0df2b',
      displayName: 'SAP IAG 10.0',
      description: 'SAP IAG 10.0.0',
      connectorType: 'sapIag',
      connectionInfo: {
        '@odata.type': 'microsoft.graph.externalTokenBasedSapIagConnectionInfo',
        url: 'https://iagigorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com',
        subscriptionId: '8e072eb5-73f5-4ed2-9324-a734dcb9728',
        resourceGroup: 'SAPResourceGroup',
        accessTokenUrl: 'https://entra-docu-intg-mrrd3gv.authentication.sap.hana.ondemand.com/oauth/token',
        clientId: 'sb-72062308-a7ae-456f-b9a4-24302b8a4aa!b247012|iagapi-iag-intg-space!b11378',
        keyVaultName: 'SAPIAG-KV',
        secretName: 'ClientSecret'
      }
    },
    accessPackageResourceEnvironment: null
  },
  requestType: 'AdminAdd',
  history: [],
  executeImmediately: true
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceScope;
use Microsoft\Graph\Beta\Generated\Models\ExternalOriginResourceConnector;
use Microsoft\Graph\Beta\Generated\Models\ConnectorType;
use Microsoft\Graph\Beta\Generated\Models\ExternalTokenBasedSapIagConnectionInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('bcb19bf7-cdf7-4a70-a106-f6543620b2a5');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setId('88eb460d-ca08-4eb9-afae-8d60a8b00377');
$accessPackageResource->setDisplayName('SAP IAG Access Rights');
$accessPackageResource->setDescription('This resource represents the business roles of SAP IAG');
$accessPackageResource->setResourceType('Business role');
$accessPackageResource->setOriginId('https://iagintgorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com');
$accessPackageResource->setOriginSystem('External');
$accessPackageResource->setAccessPackageResourceScopes([	]);
$accessPackageResourceExternalOriginResourceConnector = new ExternalOriginResourceConnector();
$accessPackageResourceExternalOriginResourceConnector->setId('1a53cea5-48bd-467c-af81-a24245b0df2b');
$accessPackageResourceExternalOriginResourceConnector->setDisplayName('SAP IAG 10.0');
$accessPackageResourceExternalOriginResourceConnector->setDescription('SAP IAG 10.0.0');
$accessPackageResourceExternalOriginResourceConnector->setConnectorType(new ConnectorType('sapIag'));
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo = new ExternalTokenBasedSapIagConnectionInfo();
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setOdataType('microsoft.graph.externalTokenBasedSapIagConnectionInfo');
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setUrl('https://iagigorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com');
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setSubscriptionId('8e072eb5-73f5-4ed2-9324-a734dcb9728');
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setResourceGroup('SAPResourceGroup');
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setAccessTokenUrl('https://entra-docu-intg-mrrd3gv.authentication.sap.hana.ondemand.com/oauth/token');
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setClientId('sb-72062308-a7ae-456f-b9a4-24302b8a4aa!b247012|iagapi-iag-intg-space!b11378');
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setKeyVaultName('SAPIAG-KV');
$accessPackageResourceExternalOriginResourceConnectorConnectionInfo->setSecretName('ClientSecret');
$accessPackageResourceExternalOriginResourceConnector->setConnectionInfo($accessPackageResourceExternalOriginResourceConnectorConnectionInfo);
$accessPackageResource->setExternalOriginResourceConnector($accessPackageResourceExternalOriginResourceConnector);
$accessPackageResource->setAccessPackageResourceEnvironment(null);
$requestBody->setAccessPackageResource($accessPackageResource);
$requestBody->setRequestType('AdminAdd');
$requestBody->setExecuteImmediately(true);
$additionalData = [
	'history' => [],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "bcb19bf7-cdf7-4a70-a106-f6543620b2a5"
	accessPackageResource = @{
		id = "88eb460d-ca08-4eb9-afae-8d60a8b00377"
		displayName = "SAP IAG Access Rights"
		description = "This resource represents the business roles of SAP IAG"
		resourceType = "Business role"
		originId = "https://iagintgorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com"
		originSystem = "External"
		accessPackageResourceScopes = @(
		)
		externalOriginResourceConnector = @{
			id = "1a53cea5-48bd-467c-af81-a24245b0df2b"
			displayName = "SAP IAG 10.0"
			description = "SAP IAG 10.0.0"
			connectorType = "sapIag"
			connectionInfo = @{
				"@odata.type" = "microsoft.graph.externalTokenBasedSapIagConnectionInfo"
				url = "https://iagigorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com"
				subscriptionId = "8e072eb5-73f5-4ed2-9324-a734dcb9728"
				resourceGroup = "SAPResourceGroup"
				accessTokenUrl = "https://entra-docu-intg-mrrd3gv.authentication.sap.hana.ondemand.com/oauth/token"
				clientId = "sb-72062308-a7ae-456f-b9a4-24302b8a4aa!b247012|iagapi-iag-intg-space!b11378"
				keyVaultName = "SAPIAG-KV"
				secretName = "ClientSecret"
			}
		}
		accessPackageResourceEnvironment = $null
	}
	requestType = "AdminAdd"
	history = @(
	)
	executeImmediately = $true
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
from msgraph_beta.generated.models.access_package_resource_scope import AccessPackageResourceScope
from msgraph_beta.generated.models.external_origin_resource_connector import ExternalOriginResourceConnector
from msgraph_beta.generated.models.connector_type import ConnectorType
from msgraph_beta.generated.models.external_token_based_sap_iag_connection_info import ExternalTokenBasedSapIagConnectionInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "bcb19bf7-cdf7-4a70-a106-f6543620b2a5",
	access_package_resource = AccessPackageResource(
		id = "88eb460d-ca08-4eb9-afae-8d60a8b00377",
		display_name = "SAP IAG Access Rights",
		description = "This resource represents the business roles of SAP IAG",
		resource_type = "Business role",
		origin_id = "https://iagintgorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com",
		origin_system = "External",
		access_package_resource_scopes = [
		],
		external_origin_resource_connector = ExternalOriginResourceConnector(
			id = "1a53cea5-48bd-467c-af81-a24245b0df2b",
			display_name = "SAP IAG 10.0",
			description = "SAP IAG 10.0.0",
			connector_type = ConnectorType.SapIag,
			connection_info = ExternalTokenBasedSapIagConnectionInfo(
				odata_type = "microsoft.graph.externalTokenBasedSapIagConnectionInfo",
				url = "https://iagigorg-iag-intg-space-java-rest-arqapi.cfapps.sap.hana.ondemand.com",
				subscription_id = "8e072eb5-73f5-4ed2-9324-a734dcb9728",
				resource_group = "SAPResourceGroup",
				access_token_url = "https://entra-docu-intg-mrrd3gv.authentication.sap.hana.ondemand.com/oauth/token",
				client_id = "sb-72062308-a7ae-456f-b9a4-24302b8a4aa!b247012|iagapi-iag-intg-space!b11378",
				key_vault_name = "SAPIAG-KV",
				secret_name = "ClientSecret",
			),
		),
		access_package_resource_environment = None,
	),
	request_type = "AdminAdd",
	execute_immediately = True,
	additional_data = {
			"history" : [
			],
	}
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
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
  "id": "0e37f047-c6b9-4d5c-99cd-e3fab4007be4",
  "requestType": "AdminAdd",
  "requestState": "Delivered",
  "requestStatus": "Fulfilled"
}
```

### Example 8: Add a Management Group Resource to catalog

#### Request

The following example shows a request for adding a management group resource to a catalog.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
    "catalogId": "e8368470-afaf-44da-ba86-13a7318f1995",
    "requestType": "AdminAdd",
    "justification": "",
    "accessPackageResource": {
        "id": "",
        "displayName": "test-mgmtgroup",
        "description": "test-mgmtgroup",
        "resourceType": "ManagementGroup",
        "originId": "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
        "originSystem": "AzureResources"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "e8368470-afaf-44da-ba86-13a7318f1995",
	RequestType = "AdminAdd",
	Justification = "",
	AccessPackageResource = new AccessPackageResource
	{
		Id = "",
		DisplayName = "test-mgmtgroup",
		Description = "test-mgmtgroup",
		ResourceType = "ManagementGroup",
		OriginId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		OriginSystem = "AzureResources",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "e8368470-afaf-44da-ba86-13a7318f1995"
requestBody.SetCatalogId(&catalogId) 
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 
justification := ""
requestBody.SetJustification(&justification) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := ""
accessPackageResource.SetId(&id) 
displayName := "test-mgmtgroup"
accessPackageResource.SetDisplayName(&displayName) 
description := "test-mgmtgroup"
accessPackageResource.SetDescription(&description) 
resourceType := "ManagementGroup"
accessPackageResource.SetResourceType(&resourceType) 
originId := "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AzureResources"
accessPackageResource.SetOriginSystem(&originSystem) 
requestBody.SetAccessPackageResource(accessPackageResource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("e8368470-afaf-44da-ba86-13a7318f1995");
accessPackageResourceRequest.setRequestType("AdminAdd");
accessPackageResourceRequest.setJustification("");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("");
accessPackageResource.setDisplayName("test-mgmtgroup");
accessPackageResource.setDescription("test-mgmtgroup");
accessPackageResource.setResourceType("ManagementGroup");
accessPackageResource.setOriginId("/providers/Microsoft.Management/managementGroups/test-mgmtgroup");
accessPackageResource.setOriginSystem("AzureResources");
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
    catalogId: 'e8368470-afaf-44da-ba86-13a7318f1995',
    requestType: 'AdminAdd',
    justification: '',
    accessPackageResource: {
        id: '',
        displayName: 'test-mgmtgroup',
        description: 'test-mgmtgroup',
        resourceType: 'ManagementGroup',
        originId: '/providers/Microsoft.Management/managementGroups/test-mgmtgroup',
        originSystem: 'AzureResources'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('e8368470-afaf-44da-ba86-13a7318f1995');
$requestBody->setRequestType('AdminAdd');
$requestBody->setJustification('');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setId('');
$accessPackageResource->setDisplayName('test-mgmtgroup');
$accessPackageResource->setDescription('test-mgmtgroup');
$accessPackageResource->setResourceType('ManagementGroup');
$accessPackageResource->setOriginId('/providers/Microsoft.Management/managementGroups/test-mgmtgroup');
$accessPackageResource->setOriginSystem('AzureResources');
$requestBody->setAccessPackageResource($accessPackageResource);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "e8368470-afaf-44da-ba86-13a7318f1995"
	requestType = "AdminAdd"
	justification = ""
	accessPackageResource = @{
		id = ""
		displayName = "test-mgmtgroup"
		description = "test-mgmtgroup"
		resourceType = "ManagementGroup"
		originId = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup"
		originSystem = "AzureResources"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "e8368470-afaf-44da-ba86-13a7318f1995",
	request_type = "AdminAdd",
	justification = "",
	access_package_resource = AccessPackageResource(
		id = "",
		display_name = "test-mgmtgroup",
		description = "test-mgmtgroup",
		resource_type = "ManagementGroup",
		origin_id = "/providers/Microsoft.Management/managementGroups/test-mgmtgroup",
		origin_system = "AzureResources",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
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
    "catalogId": "e8368470-afaf-44da-ba86-13a7318f1995",
    "id": "99e156fe-d152-4005-b019-6ba816f411ea",
    "justification": "",
    "requestState": "Delivered",
    "requestStatus": "Fulfilled",
    "requestType": "AdminAdd",
}
```

### Example 9: Add a Subscription Resource to catalog

#### Request

The following example shows a request for adding a Subscription resource to a catalog.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageResourceRequests
Content-type: application/json

{
    "catalogId": "e8368470-afaf-44da-ba86-13a7318f1995",
    "requestType": "AdminAdd",
    "justification": "",
    "accessPackageResource": {
        "id": "",
        "displayName": "Dev",
        "description": "Dev",
        "resourceType": "Subscription",
        "originId": "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
        "originSystem": "AzureResources"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessPackageResourceRequest
{
	CatalogId = "e8368470-afaf-44da-ba86-13a7318f1995",
	RequestType = "AdminAdd",
	Justification = "",
	AccessPackageResource = new AccessPackageResource
	{
		Id = "",
		DisplayName = "Dev",
		Description = "Dev",
		ResourceType = "Subscription",
		OriginId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
		OriginSystem = "AzureResources",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageResourceRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageResourceRequest()
catalogId := "e8368470-afaf-44da-ba86-13a7318f1995"
requestBody.SetCatalogId(&catalogId) 
requestType := "AdminAdd"
requestBody.SetRequestType(&requestType) 
justification := ""
requestBody.SetJustification(&justification) 
accessPackageResource := graphmodels.NewAccessPackageResource()
id := ""
accessPackageResource.SetId(&id) 
displayName := "Dev"
accessPackageResource.SetDisplayName(&displayName) 
description := "Dev"
accessPackageResource.SetDescription(&description) 
resourceType := "Subscription"
accessPackageResource.SetResourceType(&resourceType) 
originId := "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
accessPackageResource.SetOriginId(&originId) 
originSystem := "AzureResources"
accessPackageResource.SetOriginSystem(&originSystem) 
requestBody.SetAccessPackageResource(accessPackageResource)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessPackageResourceRequests, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageResourceRequests().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageResourceRequest accessPackageResourceRequest = new AccessPackageResourceRequest();
accessPackageResourceRequest.setCatalogId("e8368470-afaf-44da-ba86-13a7318f1995");
accessPackageResourceRequest.setRequestType("AdminAdd");
accessPackageResourceRequest.setJustification("");
AccessPackageResource accessPackageResource = new AccessPackageResource();
accessPackageResource.setId("");
accessPackageResource.setDisplayName("Dev");
accessPackageResource.setDescription("Dev");
accessPackageResource.setResourceType("Subscription");
accessPackageResource.setOriginId("/subscriptions/828b526f-c769-4b19-9797-734b4843b978");
accessPackageResource.setOriginSystem("AzureResources");
accessPackageResourceRequest.setAccessPackageResource(accessPackageResource);
AccessPackageResourceRequest result = graphClient.identityGovernance().entitlementManagement().accessPackageResourceRequests().post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageResourceRequest = {
    catalogId: 'e8368470-afaf-44da-ba86-13a7318f1995',
    requestType: 'AdminAdd',
    justification: '',
    accessPackageResource: {
        id: '',
        displayName: 'Dev',
        description: 'Dev',
        resourceType: 'Subscription',
        originId: '/subscriptions/828b526f-c769-4b19-9797-734b4843b978',
        originSystem: 'AzureResources'
    }
};

await client.api('/identityGovernance/entitlementManagement/accessPackageResourceRequests')
	.version('beta')
	.post(accessPackageResourceRequest);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResourceRequest;
use Microsoft\Graph\Beta\Generated\Models\AccessPackageResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageResourceRequest();
$requestBody->setCatalogId('e8368470-afaf-44da-ba86-13a7318f1995');
$requestBody->setRequestType('AdminAdd');
$requestBody->setJustification('');
$accessPackageResource = new AccessPackageResource();
$accessPackageResource->setId('');
$accessPackageResource->setDisplayName('Dev');
$accessPackageResource->setDescription('Dev');
$accessPackageResource->setResourceType('Subscription');
$accessPackageResource->setOriginId('/subscriptions/828b526f-c769-4b19-9797-734b4843b978');
$accessPackageResource->setOriginSystem('AzureResources');
$requestBody->setAccessPackageResource($accessPackageResource);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageResourceRequests()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	catalogId = "e8368470-afaf-44da-ba86-13a7318f1995"
	requestType = "AdminAdd"
	justification = ""
	accessPackageResource = @{
		id = ""
		displayName = "Dev"
		description = "Dev"
		resourceType = "Subscription"
		originId = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978"
		originSystem = "AzureResources"
	}
}

New-MgBetaEntitlementManagementAccessPackageResourceRequest -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_package_resource_request import AccessPackageResourceRequest
from msgraph_beta.generated.models.access_package_resource import AccessPackageResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageResourceRequest(
	catalog_id = "e8368470-afaf-44da-ba86-13a7318f1995",
	request_type = "AdminAdd",
	justification = "",
	access_package_resource = AccessPackageResource(
		id = "",
		display_name = "Dev",
		description = "Dev",
		resource_type = "Subscription",
		origin_id = "/subscriptions/828b526f-c769-4b19-9797-734b4843b978",
		origin_system = "AzureResources",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_resource_requests.post(request_body)
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
    "catalogId": "e8368470-afaf-44da-ba86-13a7318f1995",
    "id": "13ac6518-0597-452c-98ff-59c52b391dae",
    "justification": "",
    "requestState": "Delivered",
    "requestStatus": "Fulfilled",
    "requestType": "AdminAdd",
}
```
