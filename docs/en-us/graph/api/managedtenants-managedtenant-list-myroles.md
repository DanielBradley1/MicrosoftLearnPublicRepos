<!-- Source: https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-myroles?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# List myRoles

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the roles that a signed-in user has through a delegated relationship across managed tenants.

For information on the types of delegated relationships between a Managed Service Provider \(MSP\) who uses Microsoft 365 Lighthouse, and their business customers with Microsoft 365 Business Premium tenants, see the following articles on the [Partner Center](https://learn.microsoft.com/en-us/partner-center/overview):

- [Delegated administration privileges](https://learn.microsoft.com/en-us/partner-center/dap-faq) \(DAP\)
- [Granular delegated admin privileges](https://learn.microsoft.com/en-us/partner-center/gdap-introduction) \(GDAP\)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ManagedTenants.Read.All | ManagedTenants.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /tenantRelationships/managedTenants/myRoles
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [myRole](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-myrole?view=graph-rest-beta) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/beta/tenantRelationships/managedTenants/myRoles
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.TenantRelationships.ManagedTenants.MyRoles.GetAsync();
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
myRoles, err := graphClient.TenantRelationships().ManagedTenants().MyRoles().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.managedtenants.MyRoleCollectionResponse result = graphClient.tenantRelationships().managedTenants().myRoles().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let myRoles = await client.api('/tenantRelationships/managedTenants/myRoles')
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


$result = $graphServiceClient->tenantRelationships()->managedTenants()->myRoles()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.ManagedTenants

Get-MgBetaTenantRelationshipManagedTenantMyRole
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.tenant_relationships.managed_tenants.my_roles.get()
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
  "@odata.context": "https://graph.microsoft.com/beta/tenantRelationships/managedTenants/$metadata#myRoles",
  "value": [
    {
      "tenantId": "06b192f6-991c-4f3a-b4f6-ed85580566cf",
      "assignments": [
        {
          "assignmentType": "delegatedAdminPrivileges",
          "roles": [
            {
              "templateId": "729827e3-9c14-49f7-bb1b-9608f156bbb8",
              "displayName": "Helpdesk Administrator",
              "description": "Can reset passwords for non-administrators and Helpdesk Administrators."
            },
            {
              "templateId": "62e90394-69f5-4237-9190-012177145e10",
              "displayName": "Global Administrator",
              "description": "Can manage all aspects of Azure AD and Microsoft services that use Azure AD identities."
            }
          ]
        },
        {
          "assignmentType": "granularDelegatedAdminPrivileges",
          "roles": [
            {
              "templateId": "3a2c62db-5318-420d-8d74-23affee5d9d5",
              "displayName": "Intune Administrator",
              "description": "Can manage all aspects of the Intune product."
            },
            {
              "templateId": "69091246-20e8-4a56-aa4d-066075b2a7a8",
              "displayName": "Teams Administrator",
              "description": "Can manage the Microsoft Teams service."
            },
            {
              "templateId": "5d6b6bb7-de71-4623-b4af-96380a352509",
              "displayName": "Security Reader",
              "description": "Can read security information and reports in Azure AD and Office 365."
            }
          ]
        }
      ]
    },
    {
      "tenantId": "5618f6-991c-4f3a-b4f6-ed85580566cf",
      "assignments": [
        {
          "assignmentType": "delegatedAdminPrivileges",
          "roles": [
            {
              "templateId": "729827e3-9c14-49f7-bb1b-9608f156bbb8",
              "displayName": "Helpdesk Administrator",
              "description": "Can reset passwords for non-administrators and Helpdesk Administrators."
            }
          ]
        },
        {
          "assignmentType": "granularDelegatedAdminPrivileges",
          "roles": [
            {
              "templateId": "194ae4cb-b126-40b2-bd5b-6091b380977d",
              "displayName": "Security Administrator",
              "description": "Can read security information and reports, and manage configuration in Azure AD and Office 365."
            },
            {
              "templateId": "11451d60-acb2-45eb-a7d6-43d0f0125c13",
              "displayName": "Windows 365 Administrator",
              "description": "Can provision and manage all aspects of Cloud PCs."
            }
          ]
        }
      ]
    }
  ]
}
```
