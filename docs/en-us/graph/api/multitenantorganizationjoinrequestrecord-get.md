<!-- Source: https://learn.microsoft.com/en-us/graph/api/multitenantorganizationjoinrequestrecord-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# Get multiTenantOrganizationJoinRequestRecord

Namespace: microsoft.graph

Get the status of a tenant joining a multitenant organization.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MultiTenantOrganization.Read.All | MultiTenantOrganization.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MultiTenantOrganization.Read.All | MultiTenantOrganization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Reader
- Global Reader

## HTTP request

```http
GET /tenantRelationships/multiTenantOrganization/joinRequest
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

If successful, this method returns a `200 OK` response code and a [multiTenantOrganizationJoinRequestRecord](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationjoinrequestrecord?view=graph-rest-1.0) object in the response body.

## Examples

The following example gets the status of a tenant joining a multitenant organization.

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
GET https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization/joinRequest
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.MultiTenantOrganization.JoinRequest.GetAsync();
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
joinRequest, err := graphClient.TenantRelationships().MultiTenantOrganization().JoinRequest().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MultiTenantOrganizationJoinRequestRecord result = graphClient.tenantRelationships().multiTenantOrganization().joinRequest().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let multiTenantOrganizationJoinRequestRecord = await client.api('/tenantRelationships/multiTenantOrganization/joinRequest')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->tenantRelationships()->multiTenantOrganization()->joinRequest()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgTenantRelationshipMultiTenantOrganizationJoinRequest
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.tenant_relationships.multi_tenant_organization.join_request.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response before an added tenant joins a multitenant organization.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/joinRequest/$entity",
    "id": "7149c406-fac5-4be9-ad4b-f46fac7fe60c",
    "addedByTenantId": "00000000-0000-0000-0000-000000000000",
    "memberState": null,
    "role": null,
    "transitionDetails": null
}
```

The following example shows the response after an added tenant [requests to join a multitenant organization](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationjoinrequestrecord-update?view=graph-rest-1.0) and the state is still `pending`.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/joinRequest/$entity",
    "id": "3e536776-7489-43e9-9637-742d62ec3fc5",
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325",
    "memberState": "pending",
    "role": null,
    "transitionDetails": {
        "desiredMemberState": "active",
        "status": "notStarted",
        "details": ""
    }
}
```

The following example shows the response after an added tenant successfully joins a multitenant organization and the state is changed to `active`.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/joinRequest/$entity",
    "id": "3e536776-7489-43e9-9637-742d62ec3fc5",
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325",
    "memberState": "active",
    "role": member,
    "transitionDetails": null
}
```

The following example shows the response when an added tenant fails to join a multitenant organization. To reset a failed join request, see [Update multiTenantOrganizationJoinRequestRecord](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationjoinrequestrecord-update?view=graph-rest-1.0).

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#tenantRelationships/multiTenantOrganization/joinRequest/$entity",
    "id": "3e536776-7489-43e9-9637-742d62ec3fc5",
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325",
    "memberState": "pending",
    "role": null,
    "transitionDetails": {
        "desiredMemberState": "active",
        "status": "failed",
        "details": "DirectoryService Exception"
    }
}
```
