<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryrole-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get directoryRole

Namespace: microsoft.graph

Note

Microsoft recommends that you use the unified RBAC API instead of this API. The unified RBAC API provides more functionality and flexibility. For more information, see [Get unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/unifiedroledefinition-get?view=graph-rest-1.0).

Retrieve the properties of a [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) object. The role must be activated in tenant for a successful response.

You can use both the object ID and template ID of the **directoryRole** with this API. The template ID of a built-in role is immutable and can be seen in the role description on the Microsoft Entra admin center. For details, see [Role template IDs](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles#role-template-ids).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagement.Read.Directory | Directory.Read.All, Directory.ReadWrite.All, RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagement.Read.Directory | Directory.Read.All, Directory.ReadWrite.All, RoleManagement.ReadWrite.Directory |

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

You can address the directory role using either its **id** or **roleTemplateId**.

```http
GET /directoryRoles/{role-id}
GET /directoryRoles(roleTemplateId='{roleTemplateId}')
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get the definition of a directory role using role id

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directoryRoles/43a63cc2-582b-4d81-a79d-1591f91d5558
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryRoles["{directoryRole-id}"].GetAsync();
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
directoryRoles, err := graphClient.DirectoryRoles().ByDirectoryRoleId("directoryRole-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DirectoryRole result = graphClient.directoryRoles().byDirectoryRoleId("{directoryRole-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let directoryRole = await client.api('/directoryRoles/43a63cc2-582b-4d81-a79d-1591f91d5558')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->directoryRoles()->byDirectoryRoleId('directoryRole-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgDirectoryRole -DirectoryRoleId $directoryRoleId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.directory_roles.by_directory_role_id('directoryRole-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryRoles/$entity",
    "id": "43a63cc2-582b-4d81-a79d-1591f91d5558",
    "deletedDateTime": null,
    "description": "Can manage all aspects of Azure AD and Microsoft services that use Azure AD identities.",
    "displayName": "Global Administrator",
    "roleTemplateId": "62e90394-69f5-4237-9190-012177145e10"
}
```

### Example 2: Get the definition of a directory role using roleTemplateId

#### Request

```msgraph
GET https://graph.microsoft.com/v1.0/directoryRoles(roleTemplateId='43a63cc2-582b-4d81-a79d-1591f91d5558')
```

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryRoles/$entity",
    "id": "43a63cc2-582b-4d81-a79d-1591f91d5558",
    "deletedDateTime": null,
    "description": "Can manage all aspects of Azure AD and Microsoft services that use Azure AD identities.",
    "displayName": "Global Administrator",
    "roleTemplateId": "62e90394-69f5-4237-9190-012177145e10"
}
```
