<!-- Source: https://learn.microsoft.com/en-us/graph/api/multitenantorganizationmember-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Get multiTenantOrganizationMember

Namespace: microsoft.graph

Get a tenant and its properties in the multitenant organization.

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

The properties returned depend on the permission granted:

- *MultiTenantOrganization.ReadBasic.All* \(delegated\): Returns only the **displayName** and **tenantId** properties.
- *MultiTenantOrganization.Read.All*, *MultiTenantOrganization.ReadWrite.All*, or *Directory.Read.All* \(delegated or application\): Returns all properties.

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Reader
- Global Reader

## HTTP request

```http
GET /tenantRelationships/multiTenantOrganization/tenants/{tenantId}
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [multiTenantOrganizationMember](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationmember?view=graph-rest-1.0) object in the response body.

## Examples

The following example gets a tenant and its properties in the multitenant organization.

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization/tenants/1fd6544e-e994-4de2-9f1b-787b51c7d325
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.MultiTenantOrganization.Tenants["{multiTenantOrganizationMember-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tenants, err := graphClient.TenantRelationships().MultiTenantOrganization().Tenants().ByMultiTenantOrganizationMemberId("multiTenantOrganizationMember-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MultiTenantOrganizationMember result = graphClient.tenantRelationships().multiTenantOrganization().tenants().byMultiTenantOrganizationMemberId("{multiTenantOrganizationMember-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let multiTenantOrganizationMember = await client.api('/tenantRelationships/multiTenantOrganization/tenants/1fd6544e-e994-4de2-9f1b-787b51c7d325')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->tenantRelationships()->multiTenantOrganization()->tenants()->byMultiTenantOrganizationMemberId('multiTenantOrganizationMember-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgTenantRelationshipMultiTenantOrganizationTenant -MultiTenantOrganizationMemberId $multiTenantOrganizationMemberId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.tenant_relationships.multi_tenant_organization.tenants.by_multi_tenant_organization_member_id('multiTenantOrganizationMember-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/tenants/$entity",
    "tenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325",
    "displayName": "Contoso",
    "addedDateTime": "2023-05-26T22:05:23Z",
    "joinedDateTime": null,
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325",
    "role": "owner",
    "state": "active",
    "transitionDetails": null
}
```

If an update is in progress, `transitionDetails` lists information about the update. The following response indicates the role is being changed from member to owner.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/tenants/$entity",
    "tenantId": "5036a0a0-a7a4-4933-9086-5dd54535dd6e",
    "displayName": "Woodgrove Bank",
    "addedDateTime": "2023-05-27T21:52:40Z",
    "joinedDateTime": null,
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325",
    "role": "member",
    "state": "pending",
    "transitionDetails": {
        "desiredState": "active",
        "desiredRole": "owner",
        "status": "notStarted",
        "details": null
    }
}
```
