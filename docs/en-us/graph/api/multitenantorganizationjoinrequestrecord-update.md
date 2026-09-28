<!-- Source: https://learn.microsoft.com/en-us/graph/api/multitenantorganizationjoinrequestrecord-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update multiTenantOrganizationJoinRequestRecord

Namespace: microsoft.graph

Join a multitenant organization, after the owner of the multitenant organization has added your tenant to the multitenant organization as pending.

Before a tenant added to a multitenant organization can participate in the multitenant organization, the administrator of the joining tenant must submit a join request.

To allow for asynchronous processing, you must wait **up to 2 hours** before joining a multitenant organization is completed.

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
PATCH /tenantRelationships/multiTenantOrganization/joinRequest
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| addedByTenantId | String | Tenant ID of the Microsoft Entra tenant that added the current tenant to the multitenant organization. To reset a failed join request, set `addedByTenantId` to `00000000-0000-0000-0000-000000000000`. Required. |

## Response

If successful, this method returns a `204 No Content` response code.

A join request might be unsuccessful. The following are some scenarios:

- The joining tenant has not been added to the multitenant organization by its owner.
- The owner or joiner tenant exceeds the maximum number of internal users per tenant.
- The multitenant organization would exceed the maximum number of tenants.
- The joining tenant is already part of a different multitenant organization.

## Examples

### Example 1: Join a multitenant organization

The following example shows a request by the current tenant to join a multitenant organization. It can take a few minutes for the join to complete. If the join succeeds, the state of the tenant is changed to `active`.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization/joinRequest
Content-Type: application/json

{
    "addedByTenantId": "1fd6544e-e994-4de2-9f1b-787b51c7d325"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MultiTenantOrganizationJoinRequestRecord
{
	AddedByTenantId = "1fd6544e-e994-4de2-9f1b-787b51c7d325",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.MultiTenantOrganization.JoinRequest.PatchAsync(requestBody);
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

requestBody := graphmodels.NewMultiTenantOrganizationJoinRequestRecord()
addedByTenantId := "1fd6544e-e994-4de2-9f1b-787b51c7d325"
requestBody.SetAddedByTenantId(&addedByTenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
joinRequest, err := graphClient.TenantRelationships().MultiTenantOrganization().JoinRequest().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MultiTenantOrganizationJoinRequestRecord multiTenantOrganizationJoinRequestRecord = new MultiTenantOrganizationJoinRequestRecord();
multiTenantOrganizationJoinRequestRecord.setAddedByTenantId("1fd6544e-e994-4de2-9f1b-787b51c7d325");
MultiTenantOrganizationJoinRequestRecord result = graphClient.tenantRelationships().multiTenantOrganization().joinRequest().patch(multiTenantOrganizationJoinRequestRecord);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const multiTenantOrganizationJoinRequestRecord = {
    addedByTenantId: '1fd6544e-e994-4de2-9f1b-787b51c7d325'
};

await client.api('/tenantRelationships/multiTenantOrganization/joinRequest')
	.update(multiTenantOrganizationJoinRequestRecord);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MultiTenantOrganizationJoinRequestRecord;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MultiTenantOrganizationJoinRequestRecord();
$requestBody->setAddedByTenantId('1fd6544e-e994-4de2-9f1b-787b51c7d325');

$result = $graphServiceClient->tenantRelationships()->multiTenantOrganization()->joinRequest()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	addedByTenantId = "1fd6544e-e994-4de2-9f1b-787b51c7d325"
}

Update-MgTenantRelationshipMultiTenantOrganizationJoinRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.multi_tenant_organization_join_request_record import MultiTenantOrganizationJoinRequestRecord
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MultiTenantOrganizationJoinRequestRecord(
	added_by_tenant_id = "1fd6544e-e994-4de2-9f1b-787b51c7d325",
)

result = await graph_client.tenant_relationships.multi_tenant_organization.join_request.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Reset a failed join request

The following example shows a request by the current tenant to reset a failed join request. To reset a failed join request, set `addedByTenantId` to `00000000-0000-0000-0000-000000000000`.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/tenantRelationships/multiTenantOrganization/joinRequest
Content-Type: application/json

{
    "addedByTenantId": "00000000-0000-0000-0000-000000000000"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MultiTenantOrganizationJoinRequestRecord
{
	AddedByTenantId = "00000000-0000-0000-0000-000000000000",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.MultiTenantOrganization.JoinRequest.PatchAsync(requestBody);
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

requestBody := graphmodels.NewMultiTenantOrganizationJoinRequestRecord()
addedByTenantId := "00000000-0000-0000-0000-000000000000"
requestBody.SetAddedByTenantId(&addedByTenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
joinRequest, err := graphClient.TenantRelationships().MultiTenantOrganization().JoinRequest().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MultiTenantOrganizationJoinRequestRecord multiTenantOrganizationJoinRequestRecord = new MultiTenantOrganizationJoinRequestRecord();
multiTenantOrganizationJoinRequestRecord.setAddedByTenantId("00000000-0000-0000-0000-000000000000");
MultiTenantOrganizationJoinRequestRecord result = graphClient.tenantRelationships().multiTenantOrganization().joinRequest().patch(multiTenantOrganizationJoinRequestRecord);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const multiTenantOrganizationJoinRequestRecord = {
    addedByTenantId: '00000000-0000-0000-0000-000000000000'
};

await client.api('/tenantRelationships/multiTenantOrganization/joinRequest')
	.update(multiTenantOrganizationJoinRequestRecord);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MultiTenantOrganizationJoinRequestRecord;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MultiTenantOrganizationJoinRequestRecord();
$requestBody->setAddedByTenantId('00000000-0000-0000-0000-000000000000');

$result = $graphServiceClient->tenantRelationships()->multiTenantOrganization()->joinRequest()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	addedByTenantId = "00000000-0000-0000-0000-000000000000"
}

Update-MgTenantRelationshipMultiTenantOrganizationJoinRequest -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.multi_tenant_organization_join_request_record import MultiTenantOrganizationJoinRequestRecord
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MultiTenantOrganizationJoinRequestRecord(
	added_by_tenant_id = "00000000-0000-0000-0000-000000000000",
)

result = await graph_client.tenant_relationships.multi_tenant_organization.join_request.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```
