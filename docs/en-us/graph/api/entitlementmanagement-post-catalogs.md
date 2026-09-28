<!-- Source: https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-catalogs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create accessPackageCatalog

Namespace: microsoft.graph

Create a new [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) object.

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

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog creator*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog creator* role is less privileged than the `EntitlementManagement.ReadWrite.All` application permission.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/catalogs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of the [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) object.

You can specify the following properties when creating an **accessPackageCatalog**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the access package catalog. |
| description | String | The description of the access package catalog. |
| state | accessPackageCatalogState | Has the value `published` if the access packages are available for management. The possible values are: `unpublished` and `published`. |
| isExternallyVisible | Boolean | Whether the access packages in this catalog can be requested by users outside of the tenant. |

## Response

If successful, this method returns a 200-series response code and a new [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs
Content-Type: application/json

{
  "displayName": "sales",
  "description": "for employees working with sales and outside sales partners",
  "state": "published",
  "isExternallyVisible": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageCatalog
{
	DisplayName = "sales",
	Description = "for employees working with sales and outside sales partners",
	State = AccessPackageCatalogState.Published,
	IsExternallyVisible = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs.PostAsync(requestBody);
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

requestBody := graphmodels.NewAccessPackageCatalog()
displayName := "sales"
requestBody.SetDisplayName(&displayName) 
description := "for employees working with sales and outside sales partners"
requestBody.SetDescription(&description) 
state := graphmodels.PUBLISHED_ACCESSPACKAGECATALOGSTATE 
requestBody.SetState(&state) 
isExternallyVisible := true
requestBody.SetIsExternallyVisible(&isExternallyVisible) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
catalogs, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageCatalog accessPackageCatalog = new AccessPackageCatalog();
accessPackageCatalog.setDisplayName("sales");
accessPackageCatalog.setDescription("for employees working with sales and outside sales partners");
accessPackageCatalog.setState(AccessPackageCatalogState.Published);
accessPackageCatalog.setIsExternallyVisible(true);
AccessPackageCatalog result = graphClient.identityGovernance().entitlementManagement().catalogs().post(accessPackageCatalog);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessPackageCatalog = {
  displayName: 'sales',
  description: 'for employees working with sales and outside sales partners',
  state: 'published',
  isExternallyVisible: true
};

await client.api('/identityGovernance/entitlementManagement/catalogs')
	.post(accessPackageCatalog);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageCatalog;
use Microsoft\Graph\Generated\Models\AccessPackageCatalogState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageCatalog();
$requestBody->setDisplayName('sales');
$requestBody->setDescription('for employees working with sales and outside sales partners');
$requestBody->setState(new AccessPackageCatalogState('published'));
$requestBody->setIsExternallyVisible(true);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "sales"
	description = "for employees working with sales and outside sales partners"
	state = "published"
	isExternallyVisible = $true
}

New-MgEntitlementManagementCatalog -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_catalog import AccessPackageCatalog
from msgraph.generated.models.access_package_catalog_state import AccessPackageCatalogState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageCatalog(
	display_name = "sales",
	description = "for employees working with sales and outside sales partners",
	state = AccessPackageCatalogState.Published,
	is_externally_visible = True,
)

result = await graph_client.identity_governance.entitlement_management.catalogs.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{

  "id": "b1bf99ed-99ed-b1bf-ed99-bfb1ed99bfb1",
  "displayName": "sales",
  "description": "for employees working with sales and outside sales partners",
  "catalogType": "userManaged",
  "state": "published",
  "isExternallyVisible": true,
  "createdDateTime": "2021-11-10T01:08:30.9134953Z",
  "modifiedDateTime": "2021-11-10T01:08:30.9134953Z"
}
```
