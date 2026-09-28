<!-- Source: https://learn.microsoft.com/en-us/graph/api/userteamwork-post-installedapps?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Install app for user

Namespace: microsoft.graph

Install an [app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the personal scope of the specified [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0).

> **Note:** This API works differently in one or more national clouds. For details, see [Microsoft Teams API implementation differences in national clouds](https://learn.microsoft.com/en-us/graph/teamwork-national-cloud-differences).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsAppInstallation.ReadWriteSelfForUser | TeamsAppInstallation.ManageSelectedForUser, TeamsAppInstallation.ReadWriteAndConsentForUser, TeamsAppInstallation.ReadWriteAndConsentSelfForUser, TeamsAppInstallation.ReadWriteForUser, TeamsAppInstallation.ReadWriteSelectedForUser |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsAppInstallation.ReadWriteSelfForUser.All | TeamsAppInstallation.ManageSelectedForUser.All, TeamsAppInstallation.ReadWriteAndConsentForUser.All, TeamsAppInstallation.ReadWriteAndConsentSelfForUser.All, TeamsAppInstallation.ReadWriteForUser.All, TeamsAppInstallation.ReadWriteSelectedForUser.All |

Note

If you want your app to install, get, upgrade, or remove an app for the user, you must use the `TeamsAppInstallation.ReadWriteForUser` permission.

## HTTP request

```http
POST /users/{user-id | user-principal-name}/teamwork/installedApps
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

The request body should contain the catalog generated app ID for the app catalog. For details, see [teamsApp properties](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0#properties). The following table lists additional parameters that can be used with the request body.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| consentedPermissionSet | [teamsAppPermissionSet](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) | Set of resource-specific permissions that are being consented to. |

> **Note:** The permissions consented to during the install must be same as the resource-specific permissions present in the [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) of the app. To get the application and delegated resource-specific permissions, see [List apps installed in the personal scope of a user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps?view=graph-rest-1.0). If only delegated resource-specific permissions are present in **teamsAppDefinition**, permissions can be omitted in the body of this request.

## Response

If successful, this method returns a `201 Created` response code. It doesn't return anything in the response body.

## Examples

### Example 1: Install an app for a user

#### Request

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
POST https://graph.microsoft.com/v1.0/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps
Content-type: application/json

{
   "teamsApp@odata.bind":"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UserScopeTeamsAppInstallation
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.InstalledApps.PostAsync(requestBody);
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

requestBody := graphmodels.NewUserScopeTeamsAppInstallation()
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
installedApps, err := graphClient.Users().ByUserId("user-id").Teamwork().InstalledApps().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserScopeTeamsAppInstallation userScopeTeamsAppInstallation = new UserScopeTeamsAppInstallation();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a");
userScopeTeamsAppInstallation.setAdditionalData(additionalData);
UserScopeTeamsAppInstallation result = graphClient.users().byUserId("{user-id}").teamwork().installedApps().post(userScopeTeamsAppInstallation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const userScopeTeamsAppInstallation = {
   'teamsApp@odata.bind':'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a'
};

await client.api('/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps')
	.post(userScopeTeamsAppInstallation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UserScopeTeamsAppInstallation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UserScopeTeamsAppInstallation();
$additionalData = [
	'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->installedApps()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a"
}

New-MgUserTeamworkInstalledApp -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user_scope_teams_app_installation import UserScopeTeamsAppInstallation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UserScopeTeamsAppInstallation(
	additional_data = {
			"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a",
	}
)

result = await graph_client.users.by_user_id('user-id').teamwork.installed_apps.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
```

### Example 2: Install an app for a user and consent to the resource-specific permissions required by the app

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
POST https://graph.microsoft.com/v1.0/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps
Content-Type: application/json

{
  "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a",
  "consentedPermissionSet": {
    "resourceSpecificPermissions": [
      {
        "permissionValue": "TeamsActivity.Send.User",
        "permissionType": "Application"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UserScopeTeamsAppInstallation
{
	ConsentedPermissionSet = new TeamsAppPermissionSet
	{
		ResourceSpecificPermissions = new List<TeamsAppResourceSpecificPermission>
		{
			new TeamsAppResourceSpecificPermission
			{
				PermissionValue = "TeamsActivity.Send.User",
				PermissionType = TeamsAppResourceSpecificPermissionType.Application,
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.InstalledApps.PostAsync(requestBody);
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

requestBody := graphmodels.NewUserScopeTeamsAppInstallation()
consentedPermissionSet := graphmodels.NewTeamsAppPermissionSet()


teamsAppResourceSpecificPermission := graphmodels.NewTeamsAppResourceSpecificPermission()
permissionValue := "TeamsActivity.Send.User"
teamsAppResourceSpecificPermission.SetPermissionValue(&permissionValue) 
permissionType := graphmodels.APPLICATION_TEAMSAPPRESOURCESPECIFICPERMISSIONTYPE 
teamsAppResourceSpecificPermission.SetPermissionType(&permissionType) 

resourceSpecificPermissions := []graphmodels.TeamsAppResourceSpecificPermissionable {
	teamsAppResourceSpecificPermission,
}
consentedPermissionSet.SetResourceSpecificPermissions(resourceSpecificPermissions)
requestBody.SetConsentedPermissionSet(consentedPermissionSet)
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
installedApps, err := graphClient.Users().ByUserId("user-id").Teamwork().InstalledApps().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UserScopeTeamsAppInstallation userScopeTeamsAppInstallation = new UserScopeTeamsAppInstallation();
TeamsAppPermissionSet consentedPermissionSet = new TeamsAppPermissionSet();
LinkedList<TeamsAppResourceSpecificPermission> resourceSpecificPermissions = new LinkedList<TeamsAppResourceSpecificPermission>();
TeamsAppResourceSpecificPermission teamsAppResourceSpecificPermission = new TeamsAppResourceSpecificPermission();
teamsAppResourceSpecificPermission.setPermissionValue("TeamsActivity.Send.User");
teamsAppResourceSpecificPermission.setPermissionType(TeamsAppResourceSpecificPermissionType.Application);
resourceSpecificPermissions.add(teamsAppResourceSpecificPermission);
consentedPermissionSet.setResourceSpecificPermissions(resourceSpecificPermissions);
userScopeTeamsAppInstallation.setConsentedPermissionSet(consentedPermissionSet);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a");
userScopeTeamsAppInstallation.setAdditionalData(additionalData);
UserScopeTeamsAppInstallation result = graphClient.users().byUserId("{user-id}").teamwork().installedApps().post(userScopeTeamsAppInstallation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const userScopeTeamsAppInstallation = {
  'teamsApp@odata.bind': 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a',
  consentedPermissionSet: {
    resourceSpecificPermissions: [
      {
        permissionValue: 'TeamsActivity.Send.User',
        permissionType: 'Application'
      }
    ]
  }
};

await client.api('/users/5b649834-7412-4cce-9e69-176e95a394f5/teamwork/installedApps')
	.post(userScopeTeamsAppInstallation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UserScopeTeamsAppInstallation;
use Microsoft\Graph\Generated\Models\TeamsAppPermissionSet;
use Microsoft\Graph\Generated\Models\TeamsAppResourceSpecificPermission;
use Microsoft\Graph\Generated\Models\TeamsAppResourceSpecificPermissionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UserScopeTeamsAppInstallation();
$consentedPermissionSet = new TeamsAppPermissionSet();
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission1 = new TeamsAppResourceSpecificPermission();
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission1->setPermissionValue('TeamsActivity.Send.User');
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission1->setPermissionType(new TeamsAppResourceSpecificPermissionType('application'));
$resourceSpecificPermissionsArray []= $resourceSpecificPermissionsTeamsAppResourceSpecificPermission1;
$consentedPermissionSet->setResourceSpecificPermissions($resourceSpecificPermissionsArray);

$requestBody->setConsentedPermissionSet($consentedPermissionSet);
$additionalData = [
'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->installedApps()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a"
	consentedPermissionSet = @{
		resourceSpecificPermissions = @(
			@{
				permissionValue = "TeamsActivity.Send.User"
				permissionType = "Application"
			}
		)
	}
}

New-MgUserTeamworkInstalledApp -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.user_scope_teams_app_installation import UserScopeTeamsAppInstallation
from msgraph.generated.models.teams_app_permission_set import TeamsAppPermissionSet
from msgraph.generated.models.teams_app_resource_specific_permission import TeamsAppResourceSpecificPermission
from msgraph.generated.models.teams_app_resource_specific_permission_type import TeamsAppResourceSpecificPermissionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UserScopeTeamsAppInstallation(
	consented_permission_set = TeamsAppPermissionSet(
		resource_specific_permissions = [
			TeamsAppResourceSpecificPermission(
				permission_value = "TeamsActivity.Send.User",
				permission_type = TeamsAppResourceSpecificPermissionType.Application,
			),
		],
	),
	additional_data = {
			"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/12345678-9abc-def0-123456789a",
	}
)

result = await graph_client.users.by_user_id('user-id').teamwork.installed_apps.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
```

## Related content

[Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
