<!-- Source: https://learn.microsoft.com/en-us/graph/api/delegatedadmincustomer-list-servicemanagementdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List serviceManagementDetails

Namespace: microsoft.graph

Get a list of the [delegatedAdminServiceManagementDetail](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminservicemanagementdetail?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DelegatedAdminRelationship.Read.All | DelegatedAdminRelationship.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DelegatedAdminRelationship.Read.All | DelegatedAdminRelationship.ReadWrite.All |

## HTTP request

```http
GET /tenantRelationships/delegatedAdminCustomers/{delegatedAdminCustomerId}/serviceManagementDetails
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

If successful, this method returns a `200 OK` response code and a collection of [delegatedAdminServiceManagementDetail](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminservicemanagementdetail?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/tenantRelationships/delegatedAdminCustomers/4fdbff88-9d6b-42e0-9713-45c922ba8001/serviceManagementDetails
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.DelegatedAdminCustomers["{delegatedAdminCustomer-id}"].ServiceManagementDetails.GetAsync();
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
serviceManagementDetails, err := graphClient.TenantRelationships().DelegatedAdminCustomers().ByDelegatedAdminCustomerId("delegatedAdminCustomer-id").ServiceManagementDetails().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DelegatedAdminServiceManagementDetailCollectionResponse result = graphClient.tenantRelationships().delegatedAdminCustomers().byDelegatedAdminCustomerId("{delegatedAdminCustomer-id}").serviceManagementDetails().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let serviceManagementDetails = await client.api('/tenantRelationships/delegatedAdminCustomers/4fdbff88-9d6b-42e0-9713-45c922ba8001/serviceManagementDetails')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->tenantRelationships()->delegatedAdminCustomers()->byDelegatedAdminCustomerId('delegatedAdminCustomer-id')->serviceManagementDetails()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Partner

Get-MgTenantRelationshipDelegatedAdminCustomerServiceManagementDetail -DelegatedAdminCustomerId $delegatedAdminCustomerId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.tenant_relationships.delegated_admin_customers.by_delegated_admin_customer_id('delegatedAdminCustomer-id').service_management_details.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/tenantRelationships/$metadata#delegatedAdminCustomers/4fdbff88-9d6b-42e0-9713-45c922ba8001/serviceManagementDetails",
  "value": [
    {
      "@odata.type": "#microsoft.graph.delegatedAdminServiceManagementDetail",
      "id": "fa5fa04e-13df-4b7c-9e99-92573ba1fa55",
      "serviceManagementUrl": "https://aad.portal.azure.com/contoso.com",
      "serviceName": "Azure Active Directory"
    },
    {
      "@odata.type": "#microsoft.graph.delegatedAdminServiceManagementDetail",
      "id": "5d0273c3-0f0e-4e00-90e8-e792c8860fb5",
      "serviceManagementUrl": "https://lighthouse.microsoft.com",
      "serviceName": "Microsoft 365 Lighthouse"
    },
    {
      "@odata.type": "#microsoft.graph.delegatedAdminServiceManagementDetail",
      "id": "2b565abc-b0de-4974-97c0-bed0abb14a0f",
      "serviceManagementUrl": "https://businesscentral.dynamics.com/55beae45-27a6-4e7a-8c7c-2eae70816cfa/admin",
      "serviceName": "Dynamics 365 Business Central"
    },
    {
      "@odata.type": "#microsoft.graph.delegatedAdminServiceManagementDetail",
      "id": "ce0b42f4-bfde-4abe-a5f7-add83f104b23",
      "serviceManagementUrl": "https://admin.teams.microsoft.com/?delegatedOrg=contoso.com",
      "serviceName": "Teams"
    }
  ]
}
```
