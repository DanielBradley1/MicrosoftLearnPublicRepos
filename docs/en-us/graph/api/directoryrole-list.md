<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryrole-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List directoryRoles

Namespace: microsoft.graph

Note

Microsoft recommends that you use the unified RBAC API instead of this API. The unified RBAC API provides more functionality and flexibility. For more information, see [List roleDefinitions](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roledefinitions?view=graph-rest-1.0).

List the directory roles that are activated in the tenant.

This operation only returns roles that have been activated. A role becomes activated when an admin activates the role using the [Activate directoryRole](https://learn.microsoft.com/en-us/graph/api/directoryrole-post-directoryroles?view=graph-rest-1.0) API. Not all built-in roles are initially activated.

When assigning a role using the Microsoft Entra admin center, the role activation step is implicitly done on the admin's behalf. To get the full list of roles that are available in Microsoft Entra ID, use [List directoryRoleTemplates](https://learn.microsoft.com/en-us/graph/api/directoryroletemplate-list?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagement.Read.Directory | RoleManagement.ReadWrite.Directory, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagement.Read.Directory | RoleManagement.ReadWrite.Directory, Directory.Read.All, Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- User Administrator
- Helpdesk Administrator
- Service Support Administrator
- Billing Administrator
- User
- Mailbox Administrator
- Directory Readers
- Directory Writers
- Application Administrator
- Security Reader
- Security Administrator
- Privileged Role Administrator
- Cloud Application Administrator
- Customer LockBox Access Approver
- Dynamics 365 Administrator
- Power BI Administrator
- Azure Information Protection Administrator
- Desktop Analytics Administrator
- License Administrator
- Microsoft Managed Desktop Administrator
- Authentication Administrator
- Privileged Authentication Administrator
- Teams Communications Administrator
- Teams Communications Support Engineer
- Teams Communications Support Specialist
- Teams Administrator
- Insights Administrator
- Compliance Data Administrator
- Security Operator
- Kaizala Administrator
- Global Reader
- Volume Licensing Business Center User
- Volume Licensing Service Center User
- Modern Commerce Administrator
- Microsoft Store for Business User
- Directory Reviewer

## HTTP request

```http
GET /directoryRoles
```

## Optional query parameters

This method supports the `$select`, `$filter` \(`eq` only\), and `$expand` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) objects in the response body.

## Example

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
GET https://graph.microsoft.com/v1.0/directoryRoles
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryRoles.GetAsync();
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
directoryRoles, err := graphClient.DirectoryRoles().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DirectoryRoleCollectionResponse result = graphClient.directoryRoles().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let directoryRoles = await client.api('/directoryRoles')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->directoryRoles()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgDirectoryRole
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.directory_roles.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryRoles",
  "value": [
    {
      "id": "9ed3a0c4-53e1-498c-ab4d-2473476fde14",
      "deletedDateTime": null,
      "description": "Can manage all aspects of Azure AD and Microsoft services that use Azure AD identities.",
      "displayName": "Global Administrator",
      "roleTemplateId": "62e90394-69f5-4237-9190-012177145e10"
    },
    {
      "id": "f8e85ed8-f66f-4058-b170-3efae8b9c6e5",
      "deletedDateTime": null,
      "description": "Device Administrators",
      "displayName": "Azure AD Joined Device Local Administrator",
      "roleTemplateId": "9f06204d-73c1-4d4c-880a-6edb90606fd8"
    },
    {
      "id": "fe8f10bf-c9c2-47eb-95cb-c26cc85f1830",
      "deletedDateTime": null,
      "description": "Can read basic directory information. Commonly used to grant directory read access to applications and guests.",
      "displayName": "Directory Readers",
      "roleTemplateId": "88d8e3e3-8f55-4a1e-953a-9b9898b8876b"
    }
  ]
}
```
