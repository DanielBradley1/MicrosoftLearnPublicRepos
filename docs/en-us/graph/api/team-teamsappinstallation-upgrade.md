<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-teamsappinstallation-upgrade?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# teamsAppInstallation in a team: upgrade

Namespace: microsoft.graph

Upgrade an [app installation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) to the latest version of the app.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsAppInstallation.ReadWriteSelfForTeam | Directory.ReadWrite.All, Group.ReadWrite.All, TeamsAppInstallation.ManageSelectedForTeam, TeamsAppInstallation.ReadWriteAndConsentForTeam, TeamsAppInstallation.ReadWriteAndConsentSelfForTeam, TeamsAppInstallation.ReadWriteForTeam |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsAppInstallation.ReadWriteSelfForTeam.All | Directory.ReadWrite.All, Group.ReadWrite.All, TeamsAppInstallation.ManageSelectedForTeam.All, TeamsAppInstallation.ReadWriteAndConsentForTeam.All, TeamsAppInstallation.ReadWriteAndConsentSelfForTeam.All, TeamsAppInstallation.ReadWriteForTeam.All |

Note

- The `TeamsAppInstallation.ReadWriteSelfForTeam`, `TeamsAppInstallation.ReadWriteForTeampermissions`, `TeamsAppInstallation.ReadWriteSelfForTeam.All`, and `TeamsAppInstallation.ReadWriteForTeam.All` permissions can't be used to install apps that require consent to [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent) permissions.
- The `Group.ReadWrite.All` and `Directory.ReadWrite.All` permissions are supported only for backward compatibility. We recommend that you update your solutions to use an alternative permission and avoid using these permissions going forward.
- The `TeamsAppInstallation.ManageSelectedForTeam.All` is the least privileged application permission required to install or upgrade a Teams app that requires consent to [resource-specific consent \(RSC\)](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent) permissions.

## HTTP request

```http
POST /teams/{team-id}/installedApps/{app-installation-id}/upgrade
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows more parameters that can be used with the upgrade action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| consentedPermissionSet | [teamsAppPermissionSet](https://learn.microsoft.com/en-us/graph/api/resources/teamsapppermissionset?view=graph-rest-1.0) | Set of resource specific permissions that are being consented. |

> **Note**: The permissions consented to during the installation must match the resource-specific permissions specified in the [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0) of the app. To get the application and delegated resource-specific permissions, see [Example 6](https://learn.microsoft.com/en-us/graph/api/appcatalogs-list-teamsapps?view=graph-rest-1.0#example-6-list-applications-with-a-given-id-and-return-only-the-resource-specific-permissions-required-by-the-app). If only delegated resource-specific permissions are specified in the **teamsAppDefinition**, permissions can be omitted in the request body.

## Response

If successful, this method returns `204 No Content` response code. It doesn't return anything in the response body.

## Examples

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
POST https://graph.microsoft.com/v1.0/teams/db5e04be-daa2-4a35-beb1-5e73cc381599/installedApps/NjkwM2ZhOTMtNjA1Yi00M2VmLTkyMGUtNzdjNDcyOWY4MjU4IyMwMjQwYTM2OC0yNWUwLTQ1NjktOGViZS0xMzYwMWNiNTVhMTg=/upgrade

{

}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.InstalledApps.Item.Upgrade;

var requestBody = new UpgradePostRequestBody
{
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].InstalledApps["{teamsAppInstallation-id}"].Upgrade.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  //other-imports
)

requestBody := graphteams.NewUpgradePostRequestBody()

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").InstalledApps().ByTeamsAppInstallationId("teamsAppInstallation-id").Upgrade().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.installedapps.item.upgrade.UpgradePostRequestBody upgradePostRequestBody = new com.microsoft.graph.teams.item.installedapps.item.upgrade.UpgradePostRequestBody();
graphClient.teams().byTeamId("{team-id}").installedApps().byTeamsAppInstallationId("{teamsAppInstallation-id}").upgrade().post(upgradePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const upgrade = {

};

await client.api('/teams/db5e04be-daa2-4a35-beb1-5e73cc381599/installedApps/NjkwM2ZhOTMtNjA1Yi00M2VmLTkyMGUtNzdjNDcyOWY4MjU4IyMwMjQwYTM2OC0yNWUwLTQ1NjktOGViZS0xMzYwMWNiNTVhMTg=/upgrade')
	.post(upgrade);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\InstalledApps\Item\Upgrade\UpgradePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpgradePostRequestBody();

$graphServiceClient->teams()->byTeamId('team-id')->installedApps()->byTeamsAppInstallationId('teamsAppInstallation-id')->upgrade()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
}

Update-MgTeamInstalledApp -TeamId $teamId -TeamsAppInstallationId $teamsAppInstallationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.installedapps.item.upgrade.upgrade_post_request_body import UpgradePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpgradePostRequestBody(
)

await graph_client.teams.by_team_id('team-id').installed_apps.by_teams_app_installation_id('teamsAppInstallation-id').upgrade.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Upgrade app installed in a team and consent to the resource-specific permissions required by the app

To get the list of resource-specific permissions required by the app, get the app from **appCatalog**, as shown in [Example 6](https://learn.microsoft.com/en-us/graph/api/appcatalogs-list-teamsapps?view=graph-rest-1.0#example-6-list-applications-with-a-given-id-and-return-only-the-resource-specific-permissions-required-by-the-app).

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/teams/20988f0f-a647-42f6-be30-79e04de3c2ed/installedApps/MjA5ODhmMGYtYTY0Ny00MmY2LWJlMzAtNzllMDRkZTNjMmVkIyNmYTkzN2Y4OS1iYWNhLTQ5NzktYmY4YS00MmY5ODE5MWY3ODA=/upgrade
Content-Type: application/json

{
  "consentedPermissionSet": {
    "resourceSpecificPermissions": [
      {
        "permissionValue": "Channel.Create.Group",
        "permissionType": "application"
      },
      {
        "permissionValue": "ChannelMeeting.ReadBasic.Group",
        "permissionType": "delegated"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.InstalledApps.Item.Upgrade;
using Microsoft.Graph.Models;

var requestBody = new UpgradePostRequestBody
{
	ConsentedPermissionSet = new TeamsAppPermissionSet
	{
		ResourceSpecificPermissions = new List<TeamsAppResourceSpecificPermission>
		{
			new TeamsAppResourceSpecificPermission
			{
				PermissionValue = "Channel.Create.Group",
				PermissionType = TeamsAppResourceSpecificPermissionType.Application,
			},
			new TeamsAppResourceSpecificPermission
			{
				PermissionValue = "ChannelMeeting.ReadBasic.Group",
				PermissionType = TeamsAppResourceSpecificPermissionType.Delegated,
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].InstalledApps["{teamsAppInstallation-id}"].Upgrade.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewUpgradePostRequestBody()
consentedPermissionSet := graphmodels.NewTeamsAppPermissionSet()


teamsAppResourceSpecificPermission := graphmodels.NewTeamsAppResourceSpecificPermission()
permissionValue := "Channel.Create.Group"
teamsAppResourceSpecificPermission.SetPermissionValue(&permissionValue) 
permissionType := graphmodels.APPLICATION_TEAMSAPPRESOURCESPECIFICPERMISSIONTYPE 
teamsAppResourceSpecificPermission.SetPermissionType(&permissionType) 
teamsAppResourceSpecificPermission1 := graphmodels.NewTeamsAppResourceSpecificPermission()
permissionValue := "ChannelMeeting.ReadBasic.Group"
teamsAppResourceSpecificPermission1.SetPermissionValue(&permissionValue) 
permissionType := graphmodels.DELEGATED_TEAMSAPPRESOURCESPECIFICPERMISSIONTYPE 
teamsAppResourceSpecificPermission1.SetPermissionType(&permissionType) 

resourceSpecificPermissions := []graphmodels.TeamsAppResourceSpecificPermissionable {
	teamsAppResourceSpecificPermission,
	teamsAppResourceSpecificPermission1,
}
consentedPermissionSet.SetResourceSpecificPermissions(resourceSpecificPermissions)
requestBody.SetConsentedPermissionSet(consentedPermissionSet)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").InstalledApps().ByTeamsAppInstallationId("teamsAppInstallation-id").Upgrade().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.installedapps.item.upgrade.UpgradePostRequestBody upgradePostRequestBody = new com.microsoft.graph.teams.item.installedapps.item.upgrade.UpgradePostRequestBody();
TeamsAppPermissionSet consentedPermissionSet = new TeamsAppPermissionSet();
LinkedList<TeamsAppResourceSpecificPermission> resourceSpecificPermissions = new LinkedList<TeamsAppResourceSpecificPermission>();
TeamsAppResourceSpecificPermission teamsAppResourceSpecificPermission = new TeamsAppResourceSpecificPermission();
teamsAppResourceSpecificPermission.setPermissionValue("Channel.Create.Group");
teamsAppResourceSpecificPermission.setPermissionType(TeamsAppResourceSpecificPermissionType.Application);
resourceSpecificPermissions.add(teamsAppResourceSpecificPermission);
TeamsAppResourceSpecificPermission teamsAppResourceSpecificPermission1 = new TeamsAppResourceSpecificPermission();
teamsAppResourceSpecificPermission1.setPermissionValue("ChannelMeeting.ReadBasic.Group");
teamsAppResourceSpecificPermission1.setPermissionType(TeamsAppResourceSpecificPermissionType.Delegated);
resourceSpecificPermissions.add(teamsAppResourceSpecificPermission1);
consentedPermissionSet.setResourceSpecificPermissions(resourceSpecificPermissions);
upgradePostRequestBody.setConsentedPermissionSet(consentedPermissionSet);
graphClient.teams().byTeamId("{team-id}").installedApps().byTeamsAppInstallationId("{teamsAppInstallation-id}").upgrade().post(upgradePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const upgrade = {
  consentedPermissionSet: {
    resourceSpecificPermissions: [
      {
        permissionValue: 'Channel.Create.Group',
        permissionType: 'application'
      },
      {
        permissionValue: 'ChannelMeeting.ReadBasic.Group',
        permissionType: 'delegated'
      }
    ]
  }
};

await client.api('/teams/20988f0f-a647-42f6-be30-79e04de3c2ed/installedApps/MjA5ODhmMGYtYTY0Ny00MmY2LWJlMzAtNzllMDRkZTNjMmVkIyNmYTkzN2Y4OS1iYWNhLTQ5NzktYmY4YS00MmY5ODE5MWY3ODA=/upgrade')
	.post(upgrade);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\InstalledApps\Item\Upgrade\UpgradePostRequestBody;
use Microsoft\Graph\Generated\Models\TeamsAppPermissionSet;
use Microsoft\Graph\Generated\Models\TeamsAppResourceSpecificPermission;
use Microsoft\Graph\Generated\Models\TeamsAppResourceSpecificPermissionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpgradePostRequestBody();
$consentedPermissionSet = new TeamsAppPermissionSet();
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission1 = new TeamsAppResourceSpecificPermission();
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission1->setPermissionValue('Channel.Create.Group');
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission1->setPermissionType(new TeamsAppResourceSpecificPermissionType('application'));
$resourceSpecificPermissionsArray []= $resourceSpecificPermissionsTeamsAppResourceSpecificPermission1;
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission2 = new TeamsAppResourceSpecificPermission();
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission2->setPermissionValue('ChannelMeeting.ReadBasic.Group');
$resourceSpecificPermissionsTeamsAppResourceSpecificPermission2->setPermissionType(new TeamsAppResourceSpecificPermissionType('delegated'));
$resourceSpecificPermissionsArray []= $resourceSpecificPermissionsTeamsAppResourceSpecificPermission2;
$consentedPermissionSet->setResourceSpecificPermissions($resourceSpecificPermissionsArray);

$requestBody->setConsentedPermissionSet($consentedPermissionSet);

$graphServiceClient->teams()->byTeamId('team-id')->installedApps()->byTeamsAppInstallationId('teamsAppInstallation-id')->upgrade()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	consentedPermissionSet = @{
		resourceSpecificPermissions = @(
			@{
				permissionValue = "Channel.Create.Group"
				permissionType = "application"
			}
			@{
				permissionValue = "ChannelMeeting.ReadBasic.Group"
				permissionType = "delegated"
			}
		)
	}
}

Update-MgTeamInstalledApp -TeamId $teamId -TeamsAppInstallationId $teamsAppInstallationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.installedapps.item.upgrade.upgrade_post_request_body import UpgradePostRequestBody
from msgraph.generated.models.teams_app_permission_set import TeamsAppPermissionSet
from msgraph.generated.models.teams_app_resource_specific_permission import TeamsAppResourceSpecificPermission
from msgraph.generated.models.teams_app_resource_specific_permission_type import TeamsAppResourceSpecificPermissionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpgradePostRequestBody(
	consented_permission_set = TeamsAppPermissionSet(
		resource_specific_permissions = [
			TeamsAppResourceSpecificPermission(
				permission_value = "Channel.Create.Group",
				permission_type = TeamsAppResourceSpecificPermissionType.Application,
			),
			TeamsAppResourceSpecificPermission(
				permission_value = "ChannelMeeting.ReadBasic.Group",
				permission_type = TeamsAppResourceSpecificPermissionType.Delegated,
			),
		],
	),
)

await graph_client.teams.by_team_id('team-id').installed_apps.by_teams_app_installation_id('teamsAppInstallation-id').upgrade.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

## Related content

- [List apps in catalog](https://learn.microsoft.com/en-us/graph/api/appcatalogs-list-teamsapps?view=graph-rest-1.0)
- [Request resource-specific consent for apps](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent)
