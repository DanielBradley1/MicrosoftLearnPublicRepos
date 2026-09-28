<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-relatedtenant-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Get relatedTenant

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-RelatedTenant.Read.All | TenantGovernance-RelatedTenant.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TenantGovernance-RelatedTenant.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). The following least privileged roles are supported for this operation.

- Tenant Governance Administrator
- Global Reader
- Tenant Governance Reader

## HTTP request

```http
GET /directory/tenantGovernance/relatedTenants/{relatedTenantId}
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.relatedTenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) object in the response body.

## Examples

### Request

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
GET https://graph.microsoft.com/beta/directory/tenantGovernance/relatedTenants/{relatedTenantId}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.TenantGovernance.RelatedTenants["{relatedTenant-id}"].GetAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
relatedTenants, err := graphClient.Directory().TenantGovernance().RelatedTenants().ByRelatedTenantId("relatedTenant-id").Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

RelatedTenant result = graphClient.directory().tenantGovernance().relatedTenants().byRelatedTenantId("{relatedTenant-id}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let relatedTenant = await client.api('/directory/tenantGovernance/relatedTenants/{relatedTenantId}')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->directory()->tenantGovernance()->relatedTenants()->byRelatedTenantId('relatedTenant-id')->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

Get-MgBetaDirectoryTenantGovernanceRelatedTenant -RelatedTenantId $relatedTenantId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.directory.tenant_governance.related_tenants.by_related_tenant_id('relatedTenant-id').get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.relatedTenant",
  "id": "aaaabbbb-0000-cccc-1111-dddd2222eeee",
  "createdDateTime": "2026-02-15T05:34:29.4426526Z",
  "b2BRegistrationMetrics": {
    "initial": {
      "createdDateTime": "2026-02-13T20:54:25Z",
      "watermarkDateTime": "2026-02-12T00:00:00Z",
      "inboundTotalUsers": 1,
      "outboundTotalUsers": 0
    },
    "recent": {
      "updateDateTime": "2026-02-16T23:13:49Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundTotalUsers": 0,
      "outboundTotalUsers": 0
    }
  },
  "b2BSignInActivityMetrics": {
    "initial": {
      "createdDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "appB2BSignInActivityMetrics": {
    "initial": {
      "createdDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 1,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-02-17T08:08:23Z",
      "watermarkDateTime": "2026-02-15T00:00:00Z",
      "inboundMonthlyTotalUsers": 1,
      "outboundMonthlyTotalUsers": 0,
      "inboundMonthlyTotalApplications": 1,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "multiTenantApplicationMetrics": {
    "initial": {
      "createdDateTime": "2026-01-01T00:00:00Z",
      "watermarkDateTime": "2026-12-30T04:00:00Z",
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    },
    "recent": {
      "updateDateTime": "2026-01-01T00:00:00Z",
      "watermarkDateTime": "2026-12-30T04:00:00Z",
      "inboundMonthlyTotalApplications": 10,
      "outboundMonthlyTotalApplications": 0
    }
  },
  "billingMetrics": {
    "initial": {
      "createdDateTime": "2025-10-02T12:09:40Z",
      "watermarkDateTime": "2025-10-01T00:00:00Z",
      "localAssociatedTenantCount": 2,
      "localAssociatedTenantBillingManagementActiveCount": 1,
      "localAssociatedTenantProvisioningActiveCount": 2,
      "localAssociatedTenantIds": [
        "/providers/Microsoft.Billing/billingAccounts/00000000-0000-0000-0000-000000000000:00000000-0000-0000-0000-000000000000_2019-05-31/associatedTenants/11111111-1111-1111-1111-111111111111",
        "/providers/Microsoft.Billing/billingAccounts/9a157b81-1503-516b-4fe8-7849e97ca70e:e6bd1c01-9e9b-4fa7-a9f1-6fe6cbad31fa_2019-05-31/associatedTenants/22222222-2222-2222-2222-222222222222"
      ],
      "foreignAssociatedTenantCount": 0,
      "foreignAssociatedTenantBillingManagementActiveCount": 0,
      "foreignAssociatedTenantProvisioningActiveCount": 0
    },
    "recent": {
      "updateDateTime": "2025-11-02T12:09:40Z",
      "watermarkDateTime": "2025-11-01T00:00:00Z",
      "localAssociatedTenantCount": 3,
      "localAssociatedTenantBillingManagementActiveCount": 2,
      "localAssociatedTenantProvisioningActiveCount": 2,
      "localAssociatedTenantIds": [
        "/providers/Microsoft.Billing/billingAccounts/00000000-0000-0000-0000-000000000000:00000000-0000-0000-0000-000000000000_2019-05-31/associatedTenants/11111111-1111-1111-1111-111111111111",
        "/providers/Microsoft.Billing/billingAccounts/9a157b81-1503-516b-4fe8-7849e97ca70e:e6bd1c01-9e9b-4fa7-a9f1-6fe6cbad31fa_2019-05-31/associatedTenants/22222222-2222-2222-2222-222222222222",
        "/providers/Microsoft.Billing/billingAccounts/ffffffff-ffff-ffff-ffff-ffffffffffff:eeeeeeee-eeee-eeee-eeee-eeeeeeeeeeee_2019-05-31/associatedTenants/33333333-3333-3333-3333-333333333333"
      ],
      "foreignAssociatedTenantCount": 1,
      "foreignAssociatedTenantBillingManagementActiveCount": 0,
      "foreignAssociatedTenantProvisioningActiveCount": 1,
    }
  }
}
```
