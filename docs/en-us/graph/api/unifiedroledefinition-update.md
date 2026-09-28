<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedroledefinition-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update unifiedRoleDefinition

Namespace: microsoft.graph

Update the properties of a [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) object. You cannot update built-in roles. This feature requires a Microsoft Entra ID P1 or P2 license.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagement.ReadWrite.Directory | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagement.ReadWrite.Directory | Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Privileged Role Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /roleManagement/directory/roleDefinitions/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For the best performance, don't include existing values that haven't changed.

The following table shows the properties that are required when you update the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description for the role definition. Read-only when **isBuiltIn** is `true`. |
| displayName | String | The display name for the role definition. Read-only when **isBuiltIn** is `true`. Required. |
| isEnabled | Boolean | Flag indicating if the role is enabled for assignment. If `false`, the role is not available for assignment. Read-only when **isBuiltIn** is true. |
| rolePermissions | [unifiedRolePermission](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolepermission?view=graph-rest-1.0) collection | List of permissions included in the role. Read-only when **isBuiltIn** is `true`. Required. |
| templateId | String | Custom template identifier that can be set when **isBuiltIn** is `false`. This identifier is typically used if one needs an identifier to be the same across different directories. Read-only when **isBuiltIn** is `true`. |
| version | String | Indicates version of the role definition. Read-only when **isBuiltIn** is `true`. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

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
PATCH https://graph.microsoft.com/v1.0/roleManagement/directory/roleDefinitions/0d55728d-3e24-4309-9b1b-5ac09921475a
Content-type: application/json

{
  "description": "Update basic properties of application registrations",
  "displayName": "Application Registration Support Administrator",
  "rolePermissions":
    [
        {
            "allowedResourceActions": 
            [
                "microsoft.directory/applications/basic/read"
            ]
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleDefinition
{
	Description = "Update basic properties of application registrations",
	DisplayName = "Application Registration Support Administrator",
	RolePermissions = new List<UnifiedRolePermission>
	{
		new UnifiedRolePermission
		{
			AllowedResourceActions = new List<string>
			{
				"microsoft.directory/applications/basic/read",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Directory.RoleDefinitions["{unifiedRoleDefinition-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewUnifiedRoleDefinition()
description := "Update basic properties of application registrations"
requestBody.SetDescription(&description) 
displayName := "Application Registration Support Administrator"
requestBody.SetDisplayName(&displayName) 


unifiedRolePermission := graphmodels.NewUnifiedRolePermission()
allowedResourceActions := []string {
	"microsoft.directory/applications/basic/read",
}
unifiedRolePermission.SetAllowedResourceActions(allowedResourceActions)

rolePermissions := []graphmodels.UnifiedRolePermissionable {
	unifiedRolePermission,
}
requestBody.SetRolePermissions(rolePermissions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleDefinitions, err := graphClient.RoleManagement().Directory().RoleDefinitions().ByUnifiedRoleDefinitionId("unifiedRoleDefinition-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleDefinition unifiedRoleDefinition = new UnifiedRoleDefinition();
unifiedRoleDefinition.setDescription("Update basic properties of application registrations");
unifiedRoleDefinition.setDisplayName("Application Registration Support Administrator");
LinkedList<UnifiedRolePermission> rolePermissions = new LinkedList<UnifiedRolePermission>();
UnifiedRolePermission unifiedRolePermission = new UnifiedRolePermission();
LinkedList<String> allowedResourceActions = new LinkedList<String>();
allowedResourceActions.add("microsoft.directory/applications/basic/read");
unifiedRolePermission.setAllowedResourceActions(allowedResourceActions);
rolePermissions.add(unifiedRolePermission);
unifiedRoleDefinition.setRolePermissions(rolePermissions);
UnifiedRoleDefinition result = graphClient.roleManagement().directory().roleDefinitions().byUnifiedRoleDefinitionId("{unifiedRoleDefinition-id}").patch(unifiedRoleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleDefinition = {
  description: 'Update basic properties of application registrations',
  displayName: 'Application Registration Support Administrator',
  rolePermissions: 
    [
        {
            allowedResourceActions: 
            [
                'microsoft.directory/applications/basic/read'
            ]
        }
    ]
};

await client.api('/roleManagement/directory/roleDefinitions/0d55728d-3e24-4309-9b1b-5ac09921475a')
	.update(unifiedRoleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleDefinition;
use Microsoft\Graph\Generated\Models\UnifiedRolePermission;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleDefinition();
$requestBody->setDescription('Update basic properties of application registrations');
$requestBody->setDisplayName('Application Registration Support Administrator');
$rolePermissionsUnifiedRolePermission1 = new UnifiedRolePermission();
$rolePermissionsUnifiedRolePermission1->setAllowedResourceActions(['microsoft.directory/applications/basic/read', 	]);
$rolePermissionsArray []= $rolePermissionsUnifiedRolePermission1;
$requestBody->setRolePermissions($rolePermissionsArray);


$result = $graphServiceClient->roleManagement()->directory()->roleDefinitions()->byUnifiedRoleDefinitionId('unifiedRoleDefinition-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	description = "Update basic properties of application registrations"
	displayName = "Application Registration Support Administrator"
	rolePermissions = @(
		@{
			allowedResourceActions = @(
			"microsoft.directory/applications/basic/read"
		)
	}
)
}

Update-MgRoleManagementDirectoryRoleDefinition -UnifiedRoleDefinitionId $unifiedRoleDefinitionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_definition import UnifiedRoleDefinition
from msgraph.generated.models.unified_role_permission import UnifiedRolePermission
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleDefinition(
	description = "Update basic properties of application registrations",
	display_name = "Application Registration Support Administrator",
	role_permissions = [
		UnifiedRolePermission(
			allowed_resource_actions = [
				"microsoft.directory/applications/basic/read",
			],
		),
	],
)

result = await graph_client.role_management.directory.role_definitions.by_unified_role_definition_id('unifiedRoleDefinition-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 OK
Content-type: application/json
```
