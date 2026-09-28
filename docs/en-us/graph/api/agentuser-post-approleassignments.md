<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentuser-post-approleassignments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create appRoleAssignment \(for agentUser\)

Namespace: microsoft.graph

Grant an app role assignment to an [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AppRoleAssignment.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AppRoleAssignment.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Synchronization Accounts - for Microsoft Entra Connect and Microsoft Entra Cloud Sync services
- Directory Writer
- Hybrid Identity Administrator
- Identity Governance Administrator
- Privileged Role Administrator - the least privileged role supported for Microsoft Graph and Azure AD Graph app roles
- User Administrator
- Application Administrator
- Cloud Application Administrator
- Agent ID Administrator - For agent users only

## HTTP request

```http
POST /users/{usersId}/appRoleAssignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and an [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/users/{usersId}/appRoleAssignments
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.appRoleAssignment",
  "deletedDateTime": "String (timestamp)",
  "appRoleId": "Guid",
  "creationTimestamp": "String (timestamp)",
  "principalDisplayName": "String",
  "principalId": "Guid",
  "principalType": "String",
  "resourceDisplayName": "String",
  "resourceId": "Guid"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AppRoleAssignment
{
	OdataType = "#microsoft.graph.appRoleAssignment",
	DeletedDateTime = DateTimeOffset.Parse("String (timestamp)"),
	AppRoleId = Guid.Parse("Guid"),
	PrincipalDisplayName = "String",
	PrincipalId = Guid.Parse("Guid"),
	PrincipalType = "String",
	ResourceDisplayName = "String",
	ResourceId = Guid.Parse("Guid"),
	AdditionalData = new Dictionary<string, object>
	{
		{
			"creationTimestamp" , "String (timestamp)"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].AppRoleAssignments.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAppRoleAssignment()
deletedDateTime , err := time.Parse(time.RFC3339, "String (timestamp)")
requestBody.SetDeletedDateTime(&deletedDateTime) 
appRoleId := uuid.MustParse("Guid")
requestBody.SetAppRoleId(&appRoleId) 
principalDisplayName := "String"
requestBody.SetPrincipalDisplayName(&principalDisplayName) 
principalId := uuid.MustParse("Guid")
requestBody.SetPrincipalId(&principalId) 
principalType := "String"
requestBody.SetPrincipalType(&principalType) 
resourceDisplayName := "String"
requestBody.SetResourceDisplayName(&resourceDisplayName) 
resourceId := uuid.MustParse("Guid")
requestBody.SetResourceId(&resourceId) 
additionalData := map[string]interface{}{
	"creationTimestamp" : "String (timestamp)", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appRoleAssignments, err := graphClient.Users().ByUserId("user-id").AppRoleAssignments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppRoleAssignment appRoleAssignment = new AppRoleAssignment();
appRoleAssignment.setOdataType("#microsoft.graph.appRoleAssignment");
OffsetDateTime deletedDateTime = OffsetDateTime.parse("String (timestamp)");
appRoleAssignment.setDeletedDateTime(deletedDateTime);
appRoleAssignment.setAppRoleId(UUID.fromString("Guid"));
appRoleAssignment.setPrincipalDisplayName("String");
appRoleAssignment.setPrincipalId(UUID.fromString("Guid"));
appRoleAssignment.setPrincipalType("String");
appRoleAssignment.setResourceDisplayName("String");
appRoleAssignment.setResourceId(UUID.fromString("Guid"));
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("creationTimestamp", "String (timestamp)");
appRoleAssignment.setAdditionalData(additionalData);
AppRoleAssignment result = graphClient.users().byUserId("{user-id}").appRoleAssignments().post(appRoleAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const appRoleAssignment = {
  '@odata.type': '#microsoft.graph.appRoleAssignment',
  deletedDateTime: 'String (timestamp)',
  appRoleId: 'Guid',
  creationTimestamp: 'String (timestamp)',
  principalDisplayName: 'String',
  principalId: 'Guid',
  principalType: 'String',
  resourceDisplayName: 'String',
  resourceId: 'Guid'
};

await client.api('/users/{usersId}/appRoleAssignments')
	.post(appRoleAssignment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AppRoleAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AppRoleAssignment();
$requestBody->setOdataType('#microsoft.graph.appRoleAssignment');
$requestBody->setDeletedDateTime(new \DateTime('String (timestamp)'));
$requestBody->setAppRoleId('Guid');
$requestBody->setPrincipalDisplayName('String');
$requestBody->setPrincipalId('Guid');
$requestBody->setPrincipalType('String');
$requestBody->setResourceDisplayName('String');
$requestBody->setResourceId('Guid');
$additionalData = [
	'creationTimestamp' => 'String (timestamp)',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->appRoleAssignments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	"@odata.type" = "#microsoft.graph.appRoleAssignment"
	deletedDateTime = [System.DateTime]::Parse("String (timestamp)")
	appRoleId = "Guid"
	creationTimestamp = "String (timestamp)"
	principalDisplayName = "String"
	principalId = "Guid"
	principalType = "String"
	resourceDisplayName = "String"
	resourceId = "Guid"
}

New-MgUserAppRoleAssignment -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.app_role_assignment import AppRoleAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AppRoleAssignment(
	odata_type = "#microsoft.graph.appRoleAssignment",
	deleted_date_time = "String (timestamp)",
	app_role_id = UUID("Guid"),
	principal_display_name = "String",
	principal_id = UUID("Guid"),
	principal_type = "String",
	resource_display_name = "String",
	resource_id = UUID("Guid"),
	additional_data = {
			"creation_timestamp" : "String (timestamp)",
	}
)

result = await graph_client.users.by_user_id('user-id').app_role_assignments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.appRoleAssignment",
  "id": "ff9f3843-845a-c408-508a-687bf19a481f",
  "deletedDateTime": "String (timestamp)",
  "appRoleId": "Guid",
  "creationTimestamp": "String (timestamp)",
  "principalDisplayName": "String",
  "principalId": "Guid",
  "principalType": "String",
  "resourceDisplayName": "String",
  "resourceId": "Guid"
}
```
