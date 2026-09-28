<!-- Source: https://learn.microsoft.com/en-us/graph/api/rbacapplicationmultiple-post-roleassignments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-21 -->

# Create unifiedRoleAssignmentMultiple

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) object for an RBAC provider.

The following RBAC providers are currently supported:

- Cloud PC
- device management \(Intune\)
- Defender \(Microsoft Defender XDR\)

For other Microsoft 365 applications \(like Microsoft Entra ID\), use [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### For Cloud PC provider

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | DeviceManagementRBAC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | DeviceManagementRBAC.ReadWrite.All |

### For Device management \(Intune\) provider

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | DeviceManagementRBAC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | DeviceManagementRBAC.ReadWrite.All |

### For Defender provider

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagement.ReadWrite.Defender | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagement.ReadWrite.Defender | Not available. |

## HTTP request

To create role assignment for a Cloud PC provider:

```http
POST /roleManagement/cloudPC/roleAssignments
```

To create role assignment for an Intune provider:

```http
POST /roleManagement/deviceManagement/roleAssignments
```

To create role assignment for a Defender provider:

```http
POST /roleManagement/defender/roleAssignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) object. The request must have either a scope defined in Microsoft Entra ID, such as `directoryScopeIds`, or an application-specific scope, such as `appScopeId`. Examples of Microsoft Entra scope are tenant \("/"\), administrative units, or applications.

## Response

If successful, this method returns a `201 Created` response code and a new [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create a role assignment in Intune over two scope groups \(which are Microsoft Entra objects\)

#### Request

The following example shows a request.

> **Note:** the use of the **roleTemplateId** for **roleDefinitionId**. **roleDefinitionId** can be either the service-wide template ID or the directory-specific **roleDefinitionId**.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/roleManagement/deviceManagement/roleAssignments
Content-type: application/json

{ 
    "@odata.type": "#microsoft.graph.unifiedRoleAssignmentMultiple",
    "displayName": "My test role assignment 1",
    "roleDefinitionId": "c2cf284d-6c41-4e6b-afac-4b80928c9034",
    "principalIds": ["f8ca5a85-489a-49a0-b555-0a6d81e56f0d", "c1518aa9-4da5-4c84-a902-a31404023890"],
    "directoryScopeIds": ["28ca5a85-489a-49a0-b555-0a6d81e56f0d", "8152656a-cf9a-4928-a457-1512d4cae295"],
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new UnifiedRoleAssignmentMultiple
{
	OdataType = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	DisplayName = "My test role assignment 1",
	RoleDefinitionId = "c2cf284d-6c41-4e6b-afac-4b80928c9034",
	PrincipalIds = new List<string>
	{
		"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"c1518aa9-4da5-4c84-a902-a31404023890",
	},
	DirectoryScopeIds = new List<string>
	{
		"28ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"8152656a-cf9a-4928-a457-1512d4cae295",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.DeviceManagement.RoleAssignments.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleAssignmentMultiple()
displayName := "My test role assignment 1"
requestBody.SetDisplayName(&displayName) 
roleDefinitionId := "c2cf284d-6c41-4e6b-afac-4b80928c9034"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
principalIds := []string {
	"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
	"c1518aa9-4da5-4c84-a902-a31404023890",
}
requestBody.SetPrincipalIds(principalIds)
directoryScopeIds := []string {
	"28ca5a85-489a-49a0-b555-0a6d81e56f0d",
	"8152656a-cf9a-4928-a457-1512d4cae295",
}
requestBody.SetDirectoryScopeIds(directoryScopeIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignments, err := graphClient.RoleManagement().DeviceManagement().RoleAssignments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentMultiple unifiedRoleAssignmentMultiple = new UnifiedRoleAssignmentMultiple();
unifiedRoleAssignmentMultiple.setOdataType("#microsoft.graph.unifiedRoleAssignmentMultiple");
unifiedRoleAssignmentMultiple.setDisplayName("My test role assignment 1");
unifiedRoleAssignmentMultiple.setRoleDefinitionId("c2cf284d-6c41-4e6b-afac-4b80928c9034");
LinkedList<String> principalIds = new LinkedList<String>();
principalIds.add("f8ca5a85-489a-49a0-b555-0a6d81e56f0d");
principalIds.add("c1518aa9-4da5-4c84-a902-a31404023890");
unifiedRoleAssignmentMultiple.setPrincipalIds(principalIds);
LinkedList<String> directoryScopeIds = new LinkedList<String>();
directoryScopeIds.add("28ca5a85-489a-49a0-b555-0a6d81e56f0d");
directoryScopeIds.add("8152656a-cf9a-4928-a457-1512d4cae295");
unifiedRoleAssignmentMultiple.setDirectoryScopeIds(directoryScopeIds);
UnifiedRoleAssignmentMultiple result = graphClient.roleManagement().deviceManagement().roleAssignments().post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleAssignmentMultiple = {
    '@odata.type': '#microsoft.graph.unifiedRoleAssignmentMultiple',
    displayName: 'My test role assignment 1',
    roleDefinitionId: 'c2cf284d-6c41-4e6b-afac-4b80928c9034',
    principalIds: ['f8ca5a85-489a-49a0-b555-0a6d81e56f0d', 'c1518aa9-4da5-4c84-a902-a31404023890'],
    directoryScopeIds: ['28ca5a85-489a-49a0-b555-0a6d81e56f0d', '8152656a-cf9a-4928-a457-1512d4cae295'],
};

await client.api('/roleManagement/deviceManagement/roleAssignments')
	.version('beta')
	.post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\UnifiedRoleAssignmentMultiple;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleAssignmentMultiple();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleAssignmentMultiple');
$requestBody->setDisplayName('My test role assignment 1');
$requestBody->setRoleDefinitionId('c2cf284d-6c41-4e6b-afac-4b80928c9034');
$requestBody->setPrincipalIds(['f8ca5a85-489a-49a0-b555-0a6d81e56f0d', 'c1518aa9-4da5-4c84-a902-a31404023890', 	]);
$requestBody->setDirectoryScopeIds(['28ca5a85-489a-49a0-b555-0a6d81e56f0d', '8152656a-cf9a-4928-a457-1512d4cae295', 	]);

$result = $graphServiceClient->roleManagement()->deviceManagement()->roleAssignments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Enrollment

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleAssignmentMultiple"
	displayName = "My test role assignment 1"
	roleDefinitionId = "c2cf284d-6c41-4e6b-afac-4b80928c9034"
	principalIds = @(
	"f8ca5a85-489a-49a0-b555-0a6d81e56f0d"
"c1518aa9-4da5-4c84-a902-a31404023890"
)
directoryScopeIds = @(
"28ca5a85-489a-49a0-b555-0a6d81e56f0d"
"8152656a-cf9a-4928-a457-1512d4cae295"
)
}

New-MgBetaRoleManagementDeviceManagementRoleAssignment -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.unified_role_assignment_multiple import UnifiedRoleAssignmentMultiple
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleAssignmentMultiple(
	odata_type = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	display_name = "My test role assignment 1",
	role_definition_id = "c2cf284d-6c41-4e6b-afac-4b80928c9034",
	principal_ids = [
		"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"c1518aa9-4da5-4c84-a902-a31404023890",
	],
	directory_scope_ids = [
		"28ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"8152656a-cf9a-4928-a457-1512d4cae295",
	],
)

result = await graph_client.role_management.device_management.role_assignments.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/deviceManagement/roleAssignments/$entity",
    "@odata.type": "#microsoft.graph.unifiedRoleAssignmentMultiple",
    "id": "28ca5a85-489a-49a0-b555-0a6d81e56f0d",
    "roleDefinitionId": "c2cf284d-6c41-4e6b-afac-4b80928c9034",
    "principalIds": ["f8ca5a85-489a-49a0-b555-0a6d81e56f0d", "c1518aa9-4da5-4c84-a902-a31404023890"],
    "directoryScopeIds": ["28ca5a85-489a-49a0-b555-0a6d81e56f0d", "8152656a-cf9a-4928-a457-1512d4cae295"]
}
```

### Example 2: Create a role assignment in Intune at Intune-specific scope of "all Devices"

Use the following information for creating Intune role assignments:

- To allow assignments over all Intune devices, use the `AllDevices` value in **appScopeIds**.
- To allow assignments over all Intune licensed users, use the `AllLicensedUsers` value in **appScopeIds**.
- To allow assignments over all Intune devices and licensed users, use the `/` value in **directoryScopeIds**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/roleManagement/deviceManagement/roleAssignments
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleAssignmentMultiple",
    "displayName": "My test role assignment 1",
    "roleDefinitionId": "c2cf284d-6c41-4e6b-afac-4b80928c9034",
    "principalIds": ["f8ca5a85-489a-49a0-b555-0a6d81e56f0d", "c1518aa9-4da5-4c84-a902-a31404023890"],
    "appScopeIds": ["allDevices"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new UnifiedRoleAssignmentMultiple
{
	OdataType = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	DisplayName = "My test role assignment 1",
	RoleDefinitionId = "c2cf284d-6c41-4e6b-afac-4b80928c9034",
	PrincipalIds = new List<string>
	{
		"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"c1518aa9-4da5-4c84-a902-a31404023890",
	},
	AppScopeIds = new List<string>
	{
		"allDevices",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.DeviceManagement.RoleAssignments.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleAssignmentMultiple()
displayName := "My test role assignment 1"
requestBody.SetDisplayName(&displayName) 
roleDefinitionId := "c2cf284d-6c41-4e6b-afac-4b80928c9034"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
principalIds := []string {
	"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
	"c1518aa9-4da5-4c84-a902-a31404023890",
}
requestBody.SetPrincipalIds(principalIds)
appScopeIds := []string {
	"allDevices",
}
requestBody.SetAppScopeIds(appScopeIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignments, err := graphClient.RoleManagement().DeviceManagement().RoleAssignments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentMultiple unifiedRoleAssignmentMultiple = new UnifiedRoleAssignmentMultiple();
unifiedRoleAssignmentMultiple.setOdataType("#microsoft.graph.unifiedRoleAssignmentMultiple");
unifiedRoleAssignmentMultiple.setDisplayName("My test role assignment 1");
unifiedRoleAssignmentMultiple.setRoleDefinitionId("c2cf284d-6c41-4e6b-afac-4b80928c9034");
LinkedList<String> principalIds = new LinkedList<String>();
principalIds.add("f8ca5a85-489a-49a0-b555-0a6d81e56f0d");
principalIds.add("c1518aa9-4da5-4c84-a902-a31404023890");
unifiedRoleAssignmentMultiple.setPrincipalIds(principalIds);
LinkedList<String> appScopeIds = new LinkedList<String>();
appScopeIds.add("allDevices");
unifiedRoleAssignmentMultiple.setAppScopeIds(appScopeIds);
UnifiedRoleAssignmentMultiple result = graphClient.roleManagement().deviceManagement().roleAssignments().post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleAssignmentMultiple = {
    '@odata.type': '#microsoft.graph.unifiedRoleAssignmentMultiple',
    displayName: 'My test role assignment 1',
    roleDefinitionId: 'c2cf284d-6c41-4e6b-afac-4b80928c9034',
    principalIds: ['f8ca5a85-489a-49a0-b555-0a6d81e56f0d', 'c1518aa9-4da5-4c84-a902-a31404023890'],
    appScopeIds: ['allDevices']
};

await client.api('/roleManagement/deviceManagement/roleAssignments')
	.version('beta')
	.post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\UnifiedRoleAssignmentMultiple;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleAssignmentMultiple();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleAssignmentMultiple');
$requestBody->setDisplayName('My test role assignment 1');
$requestBody->setRoleDefinitionId('c2cf284d-6c41-4e6b-afac-4b80928c9034');
$requestBody->setPrincipalIds(['f8ca5a85-489a-49a0-b555-0a6d81e56f0d', 'c1518aa9-4da5-4c84-a902-a31404023890', 	]);
$requestBody->setAppScopeIds(['allDevices', 	]);

$result = $graphServiceClient->roleManagement()->deviceManagement()->roleAssignments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Enrollment

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleAssignmentMultiple"
	displayName = "My test role assignment 1"
	roleDefinitionId = "c2cf284d-6c41-4e6b-afac-4b80928c9034"
	principalIds = @(
	"f8ca5a85-489a-49a0-b555-0a6d81e56f0d"
"c1518aa9-4da5-4c84-a902-a31404023890"
)
appScopeIds = @(
"allDevices"
)
}

New-MgBetaRoleManagementDeviceManagementRoleAssignment -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.unified_role_assignment_multiple import UnifiedRoleAssignmentMultiple
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleAssignmentMultiple(
	odata_type = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	display_name = "My test role assignment 1",
	role_definition_id = "c2cf284d-6c41-4e6b-afac-4b80928c9034",
	principal_ids = [
		"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"c1518aa9-4da5-4c84-a902-a31404023890",
	],
	app_scope_ids = [
		"allDevices",
	],
)

result = await graph_client.role_management.device_management.role_assignments.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/deviceManagement/roleAssignments/$entity",
    "@odata.type": "#microsoft.graph.unifiedRoleAssignmentMultiple",
    "id": "28ca5a85-489a-49a0-b555-0a6d81e56f0d",
    "roleDefinitionId": "c2cf284d-6c41-4e6b-afac-4b80928c9034",
    "principalIds": ["f8ca5a85-489a-49a0-b555-0a6d81e56f0d", "c1518aa9-4da5-4c84-a902-a31404023890"],
    "appScopeIds": ["allDevices"]
}
```

### Example 3: Create a role assignment for a Cloud PC provider

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/roleManagement/cloudPC/roleAssignments
Content-type: application/json

{ 
    "@odata.type": "#microsoft.graph.unifiedRoleAssignmentMultiple",
    "displayName": "My test role assignment 1",
    "description": "My role assignment description",
    "roleDefinitionId": "b5c08161-a7af-481c-ace2-a20a69a48fb1",
    "principalIds": ["f8ca5a85-489a-49a0-b555-0a6d81e56f0d", "c1518aa9-4da5-4c84-a902-a31404023890"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new UnifiedRoleAssignmentMultiple
{
	OdataType = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	DisplayName = "My test role assignment 1",
	Description = "My role assignment description",
	RoleDefinitionId = "b5c08161-a7af-481c-ace2-a20a69a48fb1",
	PrincipalIds = new List<string>
	{
		"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"c1518aa9-4da5-4c84-a902-a31404023890",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.CloudPC.RoleAssignments.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleAssignmentMultiple()
displayName := "My test role assignment 1"
requestBody.SetDisplayName(&displayName) 
description := "My role assignment description"
requestBody.SetDescription(&description) 
roleDefinitionId := "b5c08161-a7af-481c-ace2-a20a69a48fb1"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
principalIds := []string {
	"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
	"c1518aa9-4da5-4c84-a902-a31404023890",
}
requestBody.SetPrincipalIds(principalIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignments, err := graphClient.RoleManagement().CloudPC().RoleAssignments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentMultiple unifiedRoleAssignmentMultiple = new UnifiedRoleAssignmentMultiple();
unifiedRoleAssignmentMultiple.setOdataType("#microsoft.graph.unifiedRoleAssignmentMultiple");
unifiedRoleAssignmentMultiple.setDisplayName("My test role assignment 1");
unifiedRoleAssignmentMultiple.setDescription("My role assignment description");
unifiedRoleAssignmentMultiple.setRoleDefinitionId("b5c08161-a7af-481c-ace2-a20a69a48fb1");
LinkedList<String> principalIds = new LinkedList<String>();
principalIds.add("f8ca5a85-489a-49a0-b555-0a6d81e56f0d");
principalIds.add("c1518aa9-4da5-4c84-a902-a31404023890");
unifiedRoleAssignmentMultiple.setPrincipalIds(principalIds);
UnifiedRoleAssignmentMultiple result = graphClient.roleManagement().cloudPC().roleAssignments().post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleAssignmentMultiple = {
    '@odata.type': '#microsoft.graph.unifiedRoleAssignmentMultiple',
    displayName: 'My test role assignment 1',
    description: 'My role assignment description',
    roleDefinitionId: 'b5c08161-a7af-481c-ace2-a20a69a48fb1',
    principalIds: ['f8ca5a85-489a-49a0-b555-0a6d81e56f0d', 'c1518aa9-4da5-4c84-a902-a31404023890']
};

await client.api('/roleManagement/cloudPC/roleAssignments')
	.version('beta')
	.post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\UnifiedRoleAssignmentMultiple;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleAssignmentMultiple();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleAssignmentMultiple');
$requestBody->setDisplayName('My test role assignment 1');
$requestBody->setDescription('My role assignment description');
$requestBody->setRoleDefinitionId('b5c08161-a7af-481c-ace2-a20a69a48fb1');
$requestBody->setPrincipalIds(['f8ca5a85-489a-49a0-b555-0a6d81e56f0d', 'c1518aa9-4da5-4c84-a902-a31404023890', 	]);

$result = $graphServiceClient->roleManagement()->cloudPC()->roleAssignments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Enrollment

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleAssignmentMultiple"
	displayName = "My test role assignment 1"
	description = "My role assignment description"
	roleDefinitionId = "b5c08161-a7af-481c-ace2-a20a69a48fb1"
	principalIds = @(
	"f8ca5a85-489a-49a0-b555-0a6d81e56f0d"
"c1518aa9-4da5-4c84-a902-a31404023890"
)
}

New-MgBetaRoleManagementCloudPcRoleAssignment -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.unified_role_assignment_multiple import UnifiedRoleAssignmentMultiple
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleAssignmentMultiple(
	odata_type = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	display_name = "My test role assignment 1",
	description = "My role assignment description",
	role_definition_id = "b5c08161-a7af-481c-ace2-a20a69a48fb1",
	principal_ids = [
		"f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
		"c1518aa9-4da5-4c84-a902-a31404023890",
	],
)

result = await graph_client.role_management.cloud_p_c.role_assignments.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability. All the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#roleManagement/cloudPC/roleAssignments/$entity",
    "id": "47c88dcd-cc79-4b0c-ba7d-7af2199649c5",
    "displayName": "My role assignment",
    "description": "My role assignment description",
    "roleDefinitionId": "b5c08161-a7af-481c-ace2-a20a69a48fb1",
    "principalIds": [
        "f8ca5a85-489a-49a0-b555-0a6d81e56f0d",
        "c1518aa9-4da5-4c84-a902-a31404023890"
    ],
    "directoryScopeIds": [
        "/"
    ],
    "appScopeIds": []
}
```

### Example 4: Create a role assignment in Defender over all and future workloads, in scope of CloudSet '123':

Use the following information for creating Intune role assignments:

- To allow assignments over all and future workloads, use the `/` value in **appScopeIds**.
- To allow assignments over workload, on all scopes, don't add any scope after the following workload IDs in **appScopeIds**: `Mdi`, `Mdc`, `Mda`, `Mde`, `Mdo`, `SecureScoreExternal`.
- To allow assignments over specific scope, use `/<ScopeType>/<ScopeId>` in **appScopeIds**.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/beta/roleManagement/defender/roleAssignments
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleAssignmentMultiple",
     "displayName": "Example role assignment",
    "roleDefinitionId": "b5c08161-a7af-481c-ace2-a20a69a48fb1",
    "principalIds": [
        "8e811502-ebda-4782-8f81-071d17f0f892",
        "30e3492f-964c-4d73-88c6-986a53c6e2a0"
    ],
    "appScopeIds": [
        "Mdc", "/CloudSet/123"
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new UnifiedRoleAssignmentMultiple
{
	OdataType = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	DisplayName = "Example role assignment",
	RoleDefinitionId = "b5c08161-a7af-481c-ace2-a20a69a48fb1",
	PrincipalIds = new List<string>
	{
		"8e811502-ebda-4782-8f81-071d17f0f892",
		"30e3492f-964c-4d73-88c6-986a53c6e2a0",
	},
	AppScopeIds = new List<string>
	{
		"Mdc",
		"/CloudSet/123",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.RoleManagement.Defender.RoleAssignments.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleAssignmentMultiple()
displayName := "Example role assignment"
requestBody.SetDisplayName(&displayName) 
roleDefinitionId := "b5c08161-a7af-481c-ace2-a20a69a48fb1"
requestBody.SetRoleDefinitionId(&roleDefinitionId) 
principalIds := []string {
	"8e811502-ebda-4782-8f81-071d17f0f892",
	"30e3492f-964c-4d73-88c6-986a53c6e2a0",
}
requestBody.SetPrincipalIds(principalIds)
appScopeIds := []string {
	"Mdc",
	"/CloudSet/123",
}
requestBody.SetAppScopeIds(appScopeIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleAssignments, err := graphClient.RoleManagement().Defender().RoleAssignments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleAssignmentMultiple unifiedRoleAssignmentMultiple = new UnifiedRoleAssignmentMultiple();
unifiedRoleAssignmentMultiple.setOdataType("#microsoft.graph.unifiedRoleAssignmentMultiple");
unifiedRoleAssignmentMultiple.setDisplayName("Example role assignment");
unifiedRoleAssignmentMultiple.setRoleDefinitionId("b5c08161-a7af-481c-ace2-a20a69a48fb1");
LinkedList<String> principalIds = new LinkedList<String>();
principalIds.add("8e811502-ebda-4782-8f81-071d17f0f892");
principalIds.add("30e3492f-964c-4d73-88c6-986a53c6e2a0");
unifiedRoleAssignmentMultiple.setPrincipalIds(principalIds);
LinkedList<String> appScopeIds = new LinkedList<String>();
appScopeIds.add("Mdc");
appScopeIds.add("/CloudSet/123");
unifiedRoleAssignmentMultiple.setAppScopeIds(appScopeIds);
UnifiedRoleAssignmentMultiple result = graphClient.roleManagement().defender().roleAssignments().post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleAssignmentMultiple = {
    '@odata.type': '#microsoft.graph.unifiedRoleAssignmentMultiple',
     displayName: 'Example role assignment',
    roleDefinitionId: 'b5c08161-a7af-481c-ace2-a20a69a48fb1',
    principalIds: [
        '8e811502-ebda-4782-8f81-071d17f0f892',
        '30e3492f-964c-4d73-88c6-986a53c6e2a0'
    ],
    appScopeIds: [
        'Mdc', '/CloudSet/123'
    ]
};

await client.api('/roleManagement/defender/roleAssignments')
	.version('beta')
	.post(unifiedRoleAssignmentMultiple);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\UnifiedRoleAssignmentMultiple;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleAssignmentMultiple();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleAssignmentMultiple');
$requestBody->setDisplayName('Example role assignment');
$requestBody->setRoleDefinitionId('b5c08161-a7af-481c-ace2-a20a69a48fb1');
$requestBody->setPrincipalIds(['8e811502-ebda-4782-8f81-071d17f0f892', '30e3492f-964c-4d73-88c6-986a53c6e2a0', 	]);
$requestBody->setAppScopeIds(['Mdc', '/CloudSet/123', 	]);

$result = $graphServiceClient->roleManagement()->defender()->roleAssignments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.unified_role_assignment_multiple import UnifiedRoleAssignmentMultiple
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleAssignmentMultiple(
	odata_type = "#microsoft.graph.unifiedRoleAssignmentMultiple",
	display_name = "Example role assignment",
	role_definition_id = "b5c08161-a7af-481c-ace2-a20a69a48fb1",
	principal_ids = [
		"8e811502-ebda-4782-8f81-071d17f0f892",
		"30e3492f-964c-4d73-88c6-986a53c6e2a0",
	],
	app_scope_ids = [
		"Mdc",
		"/CloudSet/123",
	],
)

result = await graph_client.role_management.defender.role_assignments.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#roleManagement/defender/roleAssignments/$entity",
    "@odata.type": "#microsoft.graph.unifiedRoleAssignmentMultiple",
    "id": "28ca5a85-489a-49a0-b555-0a6d81e56f0d",
    "roleDefinitionId": "b5c08161-a7af-481c-ace2-a20a69a48fb1",
    "principalIds": [
        "8e811502-ebda-4782-8f81-071d17f0f892",
        "30e3492f-964c-4d73-88c6-986a53c6e2a0"
    ],
    "appScopeIds": [
        "Mdc", "/CloudSet/123"
    ]
}
```
