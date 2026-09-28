<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointsettings-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-18 -->

# Update settings

Namespace: microsoft.graph

Update one or more tenant-level [settings](https://learn.microsoft.com/en-us/graph/api/resources/sharepointsettings?view=graph-rest-1.0) for SharePoint and OneDrive.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SharePointTenantSettings.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SharePointTenantSettings.ReadWrite.All | Not available. |

When calling on behalf of a user, the user needs to belong to the SharePoint Administrator role. To learn more about admin roles, see [About admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

## HTTP request

```http
PATCH /admin/sharepoint/settings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedDomainGuidsForSyncApp | GUID collection | Collection of trusted domain GUIDs for the OneDrive sync app. |
| deletedUserPersonalSiteRetentionPeriodInDays | Int32 | The number of days for preserving a deleted user's OneDrive. |
| excludedFileExtensionsForSyncApp | String collection | Collection of file extensions not uploaded by the OneDrive sync app. |
| idleSessionSignOut | [microsoft.graph.idleSessionSignOut](https://learn.microsoft.com/en-us/graph/api/resources/idlesessionsignout?view=graph-rest-1.0) | Specifies the idle session sign-out policies for the tenant. |
| imageTaggingOption | imageTaggingChoice | Specifies the image tagging option for the tenant. The possible values are: `disabled`, `basic`, `enhanced`. |
| isCommentingOnSitePagesEnabled | Boolean | Indicates whether comments are allowed on modern site pages in SharePoint. |
| isFileActivityNotificationEnabled | Boolean | Indicates whether push notifications are enabled for OneDrive events. |
| isLegacyAuthProtocolsEnabled | Boolean | Indicates whether legacy authentication protocols are enabled for the tenant. |
| isLoopEnabled | Boolean | Indicates whether Fluid Framework is allowed on SharePoint sites. |
| isMacSyncAppEnabled | Boolean | Indicates whether files can be synced using the OneDrive sync app for Mac. |
| isRequireAcceptingUserToMatchInvitedUserEnabled | Boolean | Indicates whether guests must sign in using the same account to which sharing invitations are sent. |
| isResharingByExternalUsersEnabled | Boolean | Indicates whether guests are allowed to reshare files, folders, and sites they don't own. |
| isSharePointMobileNotificationEnabled | Boolean | Indicates whether mobile push notifications are enabled for SharePoint. |
| isSharePointNewsfeedEnabled | Boolean | Indicates whether the newsfeed is allowed on the modern site pages in SharePoint. |
| isSiteCreationEnabled | Boolean | Indicates whether users are allowed to create sites. |
| isSiteCreationUIEnabled | Boolean | Indicates whether the UI commands for creating sites are shown. |
| isSitePagesCreationEnabled | Boolean | Indicates whether creating new modern pages is allowed on SharePoint sites. |
| isSitesStorageLimitAutomatic | Boolean | Indicates whether site storage space is automatically managed or if specific storage limits are set per site. |
| isSyncButtonHiddenOnPersonalSite | Boolean | Indicates whether the sync button in OneDrive is hidden. |
| isUnmanagedSyncAppForTenantRestricted | Boolean | Indicates whether users are allowed to sync files only on PCs joined to specific domains. |
| personalSiteDefaultStorageLimitInMB | Int64 | The default OneDrive storage limit for all new and existing users who are assigned a qualifying license. Measured in megabytes \(MB\). |
| sharingAllowedDomainList | String collection | Collection of email domains that are allowed for sharing outside the organization. |
| sharingBlockedDomainList | String collection | Collection of email domains that are blocked for sharing outside the organization. |
| sharingCapability | sharingCapabilities | Sharing capability for the tenant. The possible values are: `disabled`, `externalUserSharingOnly`, `externalUserAndGuestSharing`, `existingExternalUserSharingOnly`. |
| sharingDomainRestrictionMode | sharingDomainRestrictionMode | Specifies the external sharing mode for domains. The possible values are: `none`, `allowList`, `blockList`. |
| siteCreationDefaultManagedPath | String | The value of the team site managed path. This is the path under which new team sites will be created. |
| siteCreationDefaultStorageLimitInMB | Int32 | The default storage quota for a new site upon creation. Measured in megabytes \(MB\). |
| tenantDefaultTimezone | String | The default timezone of a tenant for newly created sites. For a list of possible values, see [SPRegionalSettings.TimeZones property](https://learn.microsoft.com/en-us/sharepoint/dev/schema/regional-settings-schema). |

## Response

If successful, this method returns a `200 OK` response code and an updated [settings](https://learn.microsoft.com/en-us/graph/api/resources/sharepointsettings?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/admin/sharepoint/settings
Content-Type: application/json
Content-length: 1323

{
    "deletedUserPersonalSiteRetentionPeriodInDays": 365,
    "excludedFileExtensionsForSyncApp": [".mp3"],
    "imageTaggingOption": "enhanced",
    "isLegacyAuthProtocolsEnabled": true,
    "isSitesStorageLimitAutomatic": false,
    "isSyncButtonHiddenOnPersonalSite": false,
    "isUnmanagedSyncAppForTenantRestricted": false,
    "personalSiteDefaultStorageLimitInMB": 120000
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SharepointSettings
{
	DeletedUserPersonalSiteRetentionPeriodInDays = 365,
	ExcludedFileExtensionsForSyncApp = new List<string>
	{
		".mp3",
	},
	ImageTaggingOption = ImageTaggingChoice.Enhanced,
	IsLegacyAuthProtocolsEnabled = true,
	IsSitesStorageLimitAutomatic = false,
	IsSyncButtonHiddenOnPersonalSite = false,
	IsUnmanagedSyncAppForTenantRestricted = false,
	PersonalSiteDefaultStorageLimitInMB = 120000L,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Sharepoint.Settings.PatchAsync(requestBody);
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

requestBody := graphmodels.NewSharepointSettings()
deletedUserPersonalSiteRetentionPeriodInDays := int32(365)
requestBody.SetDeletedUserPersonalSiteRetentionPeriodInDays(&deletedUserPersonalSiteRetentionPeriodInDays) 
excludedFileExtensionsForSyncApp := []string {
	".mp3",
}
requestBody.SetExcludedFileExtensionsForSyncApp(excludedFileExtensionsForSyncApp)
imageTaggingOption := graphmodels.ENHANCED_IMAGETAGGINGCHOICE 
requestBody.SetImageTaggingOption(&imageTaggingOption) 
isLegacyAuthProtocolsEnabled := true
requestBody.SetIsLegacyAuthProtocolsEnabled(&isLegacyAuthProtocolsEnabled) 
isSitesStorageLimitAutomatic := false
requestBody.SetIsSitesStorageLimitAutomatic(&isSitesStorageLimitAutomatic) 
isSyncButtonHiddenOnPersonalSite := false
requestBody.SetIsSyncButtonHiddenOnPersonalSite(&isSyncButtonHiddenOnPersonalSite) 
isUnmanagedSyncAppForTenantRestricted := false
requestBody.SetIsUnmanagedSyncAppForTenantRestricted(&isUnmanagedSyncAppForTenantRestricted) 
personalSiteDefaultStorageLimitInMB := int64(120000)
requestBody.SetPersonalSiteDefaultStorageLimitInMB(&personalSiteDefaultStorageLimitInMB) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
settings, err := graphClient.Admin().Sharepoint().Settings().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharepointSettings sharepointSettings = new SharepointSettings();
sharepointSettings.setDeletedUserPersonalSiteRetentionPeriodInDays(365);
LinkedList<String> excludedFileExtensionsForSyncApp = new LinkedList<String>();
excludedFileExtensionsForSyncApp.add(".mp3");
sharepointSettings.setExcludedFileExtensionsForSyncApp(excludedFileExtensionsForSyncApp);
sharepointSettings.setImageTaggingOption(ImageTaggingChoice.Enhanced);
sharepointSettings.setIsLegacyAuthProtocolsEnabled(true);
sharepointSettings.setIsSitesStorageLimitAutomatic(false);
sharepointSettings.setIsSyncButtonHiddenOnPersonalSite(false);
sharepointSettings.setIsUnmanagedSyncAppForTenantRestricted(false);
sharepointSettings.setPersonalSiteDefaultStorageLimitInMB(120000L);
SharepointSettings result = graphClient.admin().sharepoint().settings().patch(sharepointSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharepointSettings = {
    deletedUserPersonalSiteRetentionPeriodInDays: 365,
    excludedFileExtensionsForSyncApp: ['.mp3'],
    imageTaggingOption: 'enhanced',
    isLegacyAuthProtocolsEnabled: true,
    isSitesStorageLimitAutomatic: false,
    isSyncButtonHiddenOnPersonalSite: false,
    isUnmanagedSyncAppForTenantRestricted: false,
    personalSiteDefaultStorageLimitInMB: 120000
};

await client.api('/admin/sharepoint/settings')
	.update(sharepointSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharepointSettings;
use Microsoft\Graph\Generated\Models\ImageTaggingChoice;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharepointSettings();
$requestBody->setDeletedUserPersonalSiteRetentionPeriodInDays(365);
$requestBody->setExcludedFileExtensionsForSyncApp(['.mp3', 	]);
$requestBody->setImageTaggingOption(new ImageTaggingChoice('enhanced'));
$requestBody->setIsLegacyAuthProtocolsEnabled(true);
$requestBody->setIsSitesStorageLimitAutomatic(false);
$requestBody->setIsSyncButtonHiddenOnPersonalSite(false);
$requestBody->setIsUnmanagedSyncAppForTenantRestricted(false);
$requestBody->setPersonalSiteDefaultStorageLimitInMB(120000);

$result = $graphServiceClient->admin()->sharepoint()->settings()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	deletedUserPersonalSiteRetentionPeriodInDays = 365
	excludedFileExtensionsForSyncApp = @(
	".mp3"
)
imageTaggingOption = "enhanced"
isLegacyAuthProtocolsEnabled = $true
isSitesStorageLimitAutomatic = $false
isSyncButtonHiddenOnPersonalSite = $false
isUnmanagedSyncAppForTenantRestricted = $false
personalSiteDefaultStorageLimitInMB = 120000
}

Update-MgAdminSharepointSetting -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.sharepoint_settings import SharepointSettings
from msgraph.generated.models.image_tagging_choice import ImageTaggingChoice
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharepointSettings(
	deleted_user_personal_site_retention_period_in_days = 365,
	excluded_file_extensions_for_sync_app = [
		".mp3",
	],
	image_tagging_option = ImageTaggingChoice.Enhanced,
	is_legacy_auth_protocols_enabled = True,
	is_sites_storage_limit_automatic = False,
	is_sync_button_hidden_on_personal_site = False,
	is_unmanaged_sync_app_for_tenant_restricted = False,
	personal_site_default_storage_limit_in_m_b = 120000,
)

result = await graph_client.admin.sharepoint.settings.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.sharepointSettings",
    "allowedDomainGuidsForSyncApp": [
        "bdd1ab9b-3fd0-4def-a761-ec8d7471732c", 
        "ad31vb6b-5zd0-7tyg-m231-kj8d6578432c"
    ],
    "availableManagedPathsForSiteCreation": [
        "/sites/",
        "/teams/"
    ],
    "deletedUserPersonalSiteRetentionPeriodInDays": 365,
    "excludedFileExtensionsForSyncApp": [
        ".mp3"
    ],
    "idleSessionSignOut": {
        "isEnabled": true,
        "warnAfterInSeconds": 120,
        "signOutAfterInSeconds": 300
    },
    "imageTaggingOption": "basic",
    "isCommentingOnSitePagesEnabled": true,
    "isFileActivityNotificationEnabled": true,
    "isLegacyAuthProtocolsEnabled": true,
    "isLoopEnabled": true,
    "isMacSyncAppEnabled": false,
    "isRequireAcceptingUserToMatchInvitedUserEnabled": true,
    "isResharingByExternalUsersEnabled": true,
    "isSharePointMobileNotificationEnabled": true,
    "isSharePointNewsfeedEnabled": true,
    "isSiteCreationEnabled": true,
    "isSiteCreationUIEnabled": true,
    "isSitePagesCreationEnabled": true,
    "isSitesStorageLimitAutomatic": false,
    "isSyncButtonHiddenOnPersonalSite": false,
    "isUnmanagedSyncAppForTenantRestricted": false,
    "personalSiteDefaultStorageLimitInMB": 120000,
    "sharingAllowedDomainList" : [
        "contoso.com",
        "fabrikam.com"
    ],
    "sharingBlockedDomainList" : [
        "contoso.com",
        "fabrikam.com"
    ],
    "sharingCapability": "externalUserAndGuestSharing",
    "sharingDomainRestrictionMode": "allowList",
    "siteCreationDefaultManagedPath": "/sites/",
    "siteCreationDefaultStorageLimitInMB": 808034,
    "tenantDefaultTimezone": "(UTC-05:00) Eastern Time (US and Canada)"
}
```
