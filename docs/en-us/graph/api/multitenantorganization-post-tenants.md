<!-- Source: https://learn.microsoft.com/en-us/graph/api/multitenantorganization-post-tenants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Add multiTenantOrganizationMember

Namespace: microsoft.graph

Add a tenant to a multitenant organization. The administrator of an owner tenant has the permissions to add tenants to the multitenant organization. The added tenant is in the pending state until the administrator of the added tenant joins the multitenant organization by submitting a join request. A tenant can be part of only one multitenant organization.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MultiTenantOrganization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MultiTenantOrganization.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /tenantRelationships/multiTenantOrganization/tenants
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) object.

You can specify the following properties when creating a **multiTenantOrganizationMember**.

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantId | String | Tenant ID of the Microsoft Entra tenant to add to the multitenant organization. Required. |
| displayName | String | Display name of the tenant added to the multitenant organization. Currently, can't be changed once set. Required. |
| role | multiTenantOrganizationMemberRole | Role of the tenant in the multitenant organization. The possible values are: `owner`, `member` \(default\), `unknownFutureValue`. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) object in the response body. If the tenant is already pending or active in this multitenant organization, you get a 'Request\_BadRequest' error.

## Examples

The following example adds the Fabrikam tenant to the multitenant organization.

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
POST https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization/tenants
Content-Type: application/json

{
  "tenantId": "4a12efe6-aa14-4d03-8dff-88fc89e2e2ad",
  "displayName": "Fabrikam"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MultiTenantOrganizationMember
{
	TenantId = "4a12efe6-aa14-4d03-8dff-88fc89e2e2ad",
	DisplayName = "Fabrikam",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.MultiTenantOrganization.Tenants.PostAsync(requestBody);
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

requestBody := graphmodels.NewMultiTenantOrganizationMember()
tenantId := "4a12efe6-aa14-4d03-8dff-88fc89e2e2ad"
requestBody.SetTenantId(&tenantId) 
displayName := "Fabrikam"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tenants, err := graphClient.TenantRelationships().MultiTenantOrganization().Tenants().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MultiTenantOrganizationMember multiTenantOrganizationMember = new MultiTenantOrganizationMember();
multiTenantOrganizationMember.setTenantId("4a12efe6-aa14-4d03-8dff-88fc89e2e2ad");
multiTenantOrganizationMember.setDisplayName("Fabrikam");
MultiTenantOrganizationMember result = graphClient.tenantRelationships().multiTenantOrganization().tenants().post(multiTenantOrganizationMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const multiTenantOrganizationMember = {
  tenantId: '4a12efe6-aa14-4d03-8dff-88fc89e2e2ad',
  displayName: 'Fabrikam'
};

await client.api('/tenantRelationships/multiTenantOrganization/tenants')
	.post(multiTenantOrganizationMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MultiTenantOrganizationMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MultiTenantOrganizationMember();
$requestBody->setTenantId('4a12efe6-aa14-4d03-8dff-88fc89e2e2ad');
$requestBody->setDisplayName('Fabrikam');

$result = $graphServiceClient->tenantRelationships()->multiTenantOrganization()->tenants()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	tenantId = "4a12efe6-aa14-4d03-8dff-88fc89e2e2ad"
	displayName = "Fabrikam"
}

New-MgTenantRelationshipMultiTenantOrganizationTenant -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.multi_tenant_organization_member import MultiTenantOrganizationMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MultiTenantOrganizationMember(
	tenant_id = "4a12efe6-aa14-4d03-8dff-88fc89e2e2ad",
	display_name = "Fabrikam",
)

result = await graph_client.tenant_relationships.multi_tenant_organization.tenants.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/tenants/$entity",
    "tenantId": "4a12efe6-aa14-4d03-8dff-88fc89e2e2ad",
    "displayName": "Fabrikam",
    "addedDateTime": "2023-05-27T19:24:29Z",
    "joinedDateTime": null,
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325",
    "role": "member",
    "state": "pending",
    "transitionDetails": null
}
```

If tenant is already pending or active in this multitenant organization, you get a 'Request\_BadRequest' error.

```http
HTTP/1.1 400 Bad Request
Content-Type: application/json

{
    "error": {
        "code": "Request_BadRequest",
        "message": "Tenant is already being added in Multi-Tenant Organization.",
        "innerError": {
            "date": "2023-05-27T20:56:14",
            "request-id": "a1e5973c-66f1-4853-9e3d-39e6b4f606d1",
            "client-request-id": "651548c3-e864-4509-837b-4f5d4cf546a5"
        }
    }
}
```
