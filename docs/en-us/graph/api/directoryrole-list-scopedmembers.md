<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryrole-list-scopedmembers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List scopedMembers for a directory role

Namespace: microsoft.graph

Note

Microsoft recommends that you use the unified RBAC API instead of this API. The unified RBAC API provides more functionality and flexibility. For more information, see [List unifiedRoleAssignments](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleassignments?view=graph-rest-1.0).

Retrieve a list of [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) objects for a directory role.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

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
GET /directoryroles/{role-id}/scopedMembers
GET /directoryRoles(roleTemplateId='{roleTemplateId}')/scopedMembers
```

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get the members of a directory role using role id

#### Request

The following example shows a request for a directory role **id** `43a63cc2-582b-4d81-a79d-1591f91d5558`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/directoryRoles/43a63cc2-582b-4d81-a79d-1591f91d5558/scopedMembers
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DirectoryRoles["{directoryRole-id}"].ScopedMembers.GetAsync();
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
scopedMembers, err := graphClient.DirectoryRoles().ByDirectoryRoleId("directoryRole-id").ScopedMembers().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ScopedRoleMembershipCollectionResponse result = graphClient.directoryRoles().byDirectoryRoleId("{directoryRole-id}").scopedMembers().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let scopedMembers = await client.api('/directoryRoles/43a63cc2-582b-4d81-a79d-1591f91d5558/scopedMembers')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->directoryRoles()->byDirectoryRoleId('directoryRole-id')->scopedMembers()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgDirectoryRoleScopedMember -DirectoryRoleId $directoryRoleId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.directory_roles.by_directory_role_id('directoryRole-id').scoped_members.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#scopedRoleMemberships",
    "value": [
        {
            "id": "LyrRQajKPk66FAXlECzghXFuYtw3SOtAvkq8KdiKEXiTwZeOU-r8RIHrq2vQ4F1wU",
            "roleId": "43a63cc2-582b-4d81-a79d-1591f91d5558",
            "administrativeUnitId": "dc626e71-4837-40eb-be4a-bc29d88a1178",
            "roleMemberInfo": {
                "id": "8e97c193-ea53-44fc-81eb-ab6bd0e05d70",
                "displayName": "Adele Vance"
            }
        }
    ]
}
```

### Example 2: Get the scoped members of a directory role using roleTemplateId

#### Request

The following example shows a request for a directory role with **roleTemplateId** `fdd7a751-b60b-444a-984c-02652fe8fa1c`.

```http
GET https://graph.microsoft.com/v1.0/directoryRoles(roleTemplateId='fdd7a751-b60b-444a-984c-02652fe8fa1c')/scopedMembers
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#scopedRoleMemberships",
    "value": [
        {
            "id": "LyrRQajKPk66FAXlECzghXFuYtw3SOtAvkq8KdiKEXiTwZeOU-r8RIHrq2vQ4F1wU",
            "roleId": "41d12a2f-caa8-4e3e-ba14-05e5102ce085",
            "administrativeUnitId": "dc626e71-4837-40eb-be4a-bc29d88a1178",
            "roleMemberInfo": {
                "id": "8e97c193-ea53-44fc-81eb-ab6bd0e05d70",
                "displayName": "Adele Vance"
            }
        }
    ]
}
```
