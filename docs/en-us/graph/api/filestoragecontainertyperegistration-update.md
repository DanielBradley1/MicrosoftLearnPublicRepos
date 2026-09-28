<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update fileStorageContainerTypeRegistration

Namespace: microsoft.graph

Update the properties of a [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object.

Note

- [The settings in the fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypesettings?view=graph-rest-1.0) control which [settings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistrationsettings?view=graph-rest-1.0) can be updated.
- The updated settings change the behavior of new **fileStorageContainer** objects, but existing containers might require their [settings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) to be updated directly. Some settings can't be updated at all, for example, changing the storage capability.
- Agent-related settings have additional restrictions when overriding them in a consuming tenant. An override for `agent.chatEmbedAllowedHosts` must be a subset of the value defined in the [owning container type](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0). For example, if the owning container type sets `agent.chatEmbedAllowedHosts` to `["https://contoso.com", "https://localhost:5000"]`, an override can be either `["https://contoso.com"]`, `["https://localhost:5000"]`, or even `[]`. However, the setting cannot be overridden to `["https://fabrikam.com"]`. Learn more about [SharePoint Embedded agent](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/declarative-agent/spe-da-adv)
- Updated settings and permission grants may take up to one hour to propagate.

ETag is used for optimistic concurrency control. It must match the value from [Create](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertyperegistrations?view=graph-rest-1.0), [Get](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-get?view=graph-rest-1.0) or the previous Update.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainerTypeReg.Selected | FileStorageContainerTypeReg.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainerTypeReg.Selected | Not available. |

Note

- When delegated tokens are used, either the SharePoint Embedded admin role or the Global admin role is required.
- If the `FileStorageContainerTypeReg.Selected` permission is used, changes are limited to [registrations](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) owned by the application that makes the call.

## HTTP request

```http
PATCH /storage/fileStorage/containerTypeRegistrations/{fileStorageContainerTypeRegistrationId}
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
| settings | [fileStorageContainerTypeRegistrationSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistrationsettings?view=graph-rest-1.0) | fileStorageContainerTypeRegistration settings. The subset that can be updated depends on the overridable settings in the [fileStorageContainerTypeSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypesettings?view=graph-rest-1.0). Optional. |
| applicationPermissionGrants | [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) collection | define the access privileges of applications on containers of a specific fileStorageContainerType. Optional. |
| etag | String | Used for optimistic concurrency control. Must match the value returned from a [Create](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertyperegistrations?view=graph-rest-1.0) or [Get](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertyperegistration-get?view=graph-rest-1.0) request. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update a fileStorageContainerTypeRegistration setting

The following example shows how to update a **fileStorageContainerTypeRegistration** where the owning **fileStorageContainerType** marked **isSearchEnabled** as an overridable setting. The **sharingCapability** property can always be overridden.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00
Content-Type: application/json

{
  "settings": {
    "sharingCapability": "externalUserAndGuestSharing",
    "isSearchEnabled": false
  },
  "applicationPermissionGrants": [
    {
      "appId": "33225700-9a00-4c00-84dd-0c210f203f01",
      "delegatedPermissions": ["full"],
      "applicationPermissions": ["none"]
    }
  ],
  "etag": "RVRhZw=="
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileStorageContainerTypeRegistration
{
	Settings = new FileStorageContainerTypeRegistrationSettings
	{
		SharingCapability = SharingCapabilities.ExternalUserAndGuestSharing,
		IsSearchEnabled = false,
	},
	ApplicationPermissionGrants = new List<FileStorageContainerTypeAppPermissionGrant>
	{
		new FileStorageContainerTypeAppPermissionGrant
		{
			AppId = "33225700-9a00-4c00-84dd-0c210f203f01",
			DelegatedPermissions = new List<FileStorageContainerTypeAppPermission?>
			{
				FileStorageContainerTypeAppPermission.Full,
			},
			ApplicationPermissions = new List<FileStorageContainerTypeAppPermission?>
			{
				FileStorageContainerTypeAppPermission.None,
			},
		},
	},
	Etag = "RVRhZw==",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypeRegistrations["{fileStorageContainerTypeRegistration-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewFileStorageContainerTypeRegistration()
settings := graphmodels.NewFileStorageContainerTypeRegistrationSettings()
sharingCapability := graphmodels.EXTERNALUSERANDGUESTSHARING_SHARINGCAPABILITIES 
settings.SetSharingCapability(&sharingCapability) 
isSearchEnabled := false
settings.SetIsSearchEnabled(&isSearchEnabled) 
requestBody.SetSettings(settings)


fileStorageContainerTypeAppPermissionGrant := graphmodels.NewFileStorageContainerTypeAppPermissionGrant()
appId := "33225700-9a00-4c00-84dd-0c210f203f01"
fileStorageContainerTypeAppPermissionGrant.SetAppId(&appId) 
delegatedPermissions := []graphmodels.FileStorageContainerTypeAppPermissionable {
	fileStorageContainerTypeAppPermission := graphmodels.FULL_FILESTORAGECONTAINERTYPEAPPPERMISSION 
	fileStorageContainerTypeAppPermissionGrant.SetFileStorageContainerTypeAppPermission(&fileStorageContainerTypeAppPermission)
}
fileStorageContainerTypeAppPermissionGrant.SetDelegatedPermissions(delegatedPermissions)
applicationPermissions := []graphmodels.FileStorageContainerTypeAppPermissionable {
	fileStorageContainerTypeAppPermission := graphmodels.NONE_FILESTORAGECONTAINERTYPEAPPPERMISSION 
	fileStorageContainerTypeAppPermissionGrant.SetFileStorageContainerTypeAppPermission(&fileStorageContainerTypeAppPermission)
}
fileStorageContainerTypeAppPermissionGrant.SetApplicationPermissions(applicationPermissions)

applicationPermissionGrants := []graphmodels.FileStorageContainerTypeAppPermissionGrantable {
	fileStorageContainerTypeAppPermissionGrant,
}
requestBody.SetApplicationPermissionGrants(applicationPermissionGrants)
etag := "RVRhZw=="
requestBody.SetEtag(&etag) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containerTypeRegistrations, err := graphClient.Storage().FileStorage().ContainerTypeRegistrations().ByFileStorageContainerTypeRegistrationId("fileStorageContainerTypeRegistration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerTypeRegistration fileStorageContainerTypeRegistration = new FileStorageContainerTypeRegistration();
FileStorageContainerTypeRegistrationSettings settings = new FileStorageContainerTypeRegistrationSettings();
settings.setSharingCapability(SharingCapabilities.ExternalUserAndGuestSharing);
settings.setIsSearchEnabled(false);
fileStorageContainerTypeRegistration.setSettings(settings);
LinkedList<FileStorageContainerTypeAppPermissionGrant> applicationPermissionGrants = new LinkedList<FileStorageContainerTypeAppPermissionGrant>();
FileStorageContainerTypeAppPermissionGrant fileStorageContainerTypeAppPermissionGrant = new FileStorageContainerTypeAppPermissionGrant();
fileStorageContainerTypeAppPermissionGrant.setAppId("33225700-9a00-4c00-84dd-0c210f203f01");
LinkedList<FileStorageContainerTypeAppPermission> delegatedPermissions = new LinkedList<FileStorageContainerTypeAppPermission>();
delegatedPermissions.add(FileStorageContainerTypeAppPermission.Full);
fileStorageContainerTypeAppPermissionGrant.setDelegatedPermissions(delegatedPermissions);
LinkedList<FileStorageContainerTypeAppPermission> applicationPermissions = new LinkedList<FileStorageContainerTypeAppPermission>();
applicationPermissions.add(FileStorageContainerTypeAppPermission.None);
fileStorageContainerTypeAppPermissionGrant.setApplicationPermissions(applicationPermissions);
applicationPermissionGrants.add(fileStorageContainerTypeAppPermissionGrant);
fileStorageContainerTypeRegistration.setApplicationPermissionGrants(applicationPermissionGrants);
fileStorageContainerTypeRegistration.setEtag("RVRhZw==");
FileStorageContainerTypeRegistration result = graphClient.storage().fileStorage().containerTypeRegistrations().byFileStorageContainerTypeRegistrationId("{fileStorageContainerTypeRegistration-id}").patch(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerTypeRegistration = {
  settings: {
    sharingCapability: 'externalUserAndGuestSharing',
    isSearchEnabled: false
  },
  applicationPermissionGrants: [
    {
      appId: '33225700-9a00-4c00-84dd-0c210f203f01',
      delegatedPermissions: ['full'],
      applicationPermissions: ['none']
    }
  ],
  etag: 'RVRhZw=='
};

await client.api('/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00')
	.update(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeRegistration;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeRegistrationSettings;
use Microsoft\Graph\Generated\Models\SharingCapabilities;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermissionGrant;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermission;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainerTypeRegistration();
$settings = new FileStorageContainerTypeRegistrationSettings();
$settings->setSharingCapability(new SharingCapabilities('externalUserAndGuestSharing'));
$settings->setIsSearchEnabled(false);
$requestBody->setSettings($settings);
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1 = new FileStorageContainerTypeAppPermissionGrant();
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setAppId('33225700-9a00-4c00-84dd-0c210f203f01');
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setDelegatedPermissions([new FileStorageContainerTypeAppPermission('full'),	]);
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setApplicationPermissions([new FileStorageContainerTypeAppPermission('none'),	]);
$applicationPermissionGrantsArray []= $applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1;
$requestBody->setApplicationPermissionGrants($applicationPermissionGrantsArray);

$requestBody->setEtag('RVRhZw==');

$result = $graphServiceClient->storage()->fileStorage()->containerTypeRegistrations()->byFileStorageContainerTypeRegistrationId('fileStorageContainerTypeRegistration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container_type_registration import FileStorageContainerTypeRegistration
from msgraph.generated.models.file_storage_container_type_registration_settings import FileStorageContainerTypeRegistrationSettings
from msgraph.generated.models.sharing_capabilities import SharingCapabilities
from msgraph.generated.models.file_storage_container_type_app_permission_grant import FileStorageContainerTypeAppPermissionGrant
from msgraph.generated.models.file_storage_container_type_app_permission import FileStorageContainerTypeAppPermission
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainerTypeRegistration(
	settings = FileStorageContainerTypeRegistrationSettings(
		sharing_capability = SharingCapabilities.ExternalUserAndGuestSharing,
		is_search_enabled = False,
	),
	application_permission_grants = [
		FileStorageContainerTypeAppPermissionGrant(
			app_id = "33225700-9a00-4c00-84dd-0c210f203f01",
			delegated_permissions = [
				FileStorageContainerTypeAppPermission.Full,
			],
			application_permissions = [
				FileStorageContainerTypeAppPermission.None,
			],
		),
	],
	etag = "RVRhZw==",
)

result = await graph_client.storage.file_storage.container_type_registrations.by_file_storage_container_type_registration_id('fileStorageContainerTypeRegistration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypeRegistration",
  "id": "de988700-d700-020e-0a00-0831f3042f00",
  "name": "Container Type Name",
  "owningAppId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "billingStatus": "valid",
  "registredDateTime": "01/20/2025",
  "expirationDateTime": "02/20/2025",
  "etag": "RVRhZyArIDE=",
  "settings": {
    "sharingCapability": "externalUserAndGuestSharing",
    "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
    "isDiscoverabilityEnabled": true,
    "isSearchEnabled": false,
    "isItemVersioningEnabled": true,
    "itemMajorVersionLimit": 50,
    "maxStoragePerContainerInBytes": 104857600,
    "isSharingRestricted": false
  },
  "applicationPermissionGrants": [
    {
      "appId": "33225700-9a00-4c00-84dd-0c210f203f01",
      "delegatedPermissions": ["full"],
      "applicationPermissions": ["none"]
    }
  ]
}
```

### Example 2: Update a fileStorageContainerTypeRegistration without ETag

The following example shows how to update a **fileStorageContainerTypeRegistration** without an **etag** that results in a `400 Bad Request`.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00
Content-Type: application/json

{
  "settings": {
    "sharingCapability": "externalUserAndGuestSharing"
  },
  "applicationPermissionGrants": [
    {
      "appId": "33225700-9a00-4c00-84dd-0c210f203f01",
      "delegatedPermissions": ["full"],
      "applicationPermissions": ["none"]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileStorageContainerTypeRegistration
{
	Settings = new FileStorageContainerTypeRegistrationSettings
	{
		SharingCapability = SharingCapabilities.ExternalUserAndGuestSharing,
	},
	ApplicationPermissionGrants = new List<FileStorageContainerTypeAppPermissionGrant>
	{
		new FileStorageContainerTypeAppPermissionGrant
		{
			AppId = "33225700-9a00-4c00-84dd-0c210f203f01",
			DelegatedPermissions = new List<FileStorageContainerTypeAppPermission?>
			{
				FileStorageContainerTypeAppPermission.Full,
			},
			ApplicationPermissions = new List<FileStorageContainerTypeAppPermission?>
			{
				FileStorageContainerTypeAppPermission.None,
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypeRegistrations["{fileStorageContainerTypeRegistration-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewFileStorageContainerTypeRegistration()
settings := graphmodels.NewFileStorageContainerTypeRegistrationSettings()
sharingCapability := graphmodels.EXTERNALUSERANDGUESTSHARING_SHARINGCAPABILITIES 
settings.SetSharingCapability(&sharingCapability) 
requestBody.SetSettings(settings)


fileStorageContainerTypeAppPermissionGrant := graphmodels.NewFileStorageContainerTypeAppPermissionGrant()
appId := "33225700-9a00-4c00-84dd-0c210f203f01"
fileStorageContainerTypeAppPermissionGrant.SetAppId(&appId) 
delegatedPermissions := []graphmodels.FileStorageContainerTypeAppPermissionable {
	fileStorageContainerTypeAppPermission := graphmodels.FULL_FILESTORAGECONTAINERTYPEAPPPERMISSION 
	fileStorageContainerTypeAppPermissionGrant.SetFileStorageContainerTypeAppPermission(&fileStorageContainerTypeAppPermission)
}
fileStorageContainerTypeAppPermissionGrant.SetDelegatedPermissions(delegatedPermissions)
applicationPermissions := []graphmodels.FileStorageContainerTypeAppPermissionable {
	fileStorageContainerTypeAppPermission := graphmodels.NONE_FILESTORAGECONTAINERTYPEAPPPERMISSION 
	fileStorageContainerTypeAppPermissionGrant.SetFileStorageContainerTypeAppPermission(&fileStorageContainerTypeAppPermission)
}
fileStorageContainerTypeAppPermissionGrant.SetApplicationPermissions(applicationPermissions)

applicationPermissionGrants := []graphmodels.FileStorageContainerTypeAppPermissionGrantable {
	fileStorageContainerTypeAppPermissionGrant,
}
requestBody.SetApplicationPermissionGrants(applicationPermissionGrants)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containerTypeRegistrations, err := graphClient.Storage().FileStorage().ContainerTypeRegistrations().ByFileStorageContainerTypeRegistrationId("fileStorageContainerTypeRegistration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerTypeRegistration fileStorageContainerTypeRegistration = new FileStorageContainerTypeRegistration();
FileStorageContainerTypeRegistrationSettings settings = new FileStorageContainerTypeRegistrationSettings();
settings.setSharingCapability(SharingCapabilities.ExternalUserAndGuestSharing);
fileStorageContainerTypeRegistration.setSettings(settings);
LinkedList<FileStorageContainerTypeAppPermissionGrant> applicationPermissionGrants = new LinkedList<FileStorageContainerTypeAppPermissionGrant>();
FileStorageContainerTypeAppPermissionGrant fileStorageContainerTypeAppPermissionGrant = new FileStorageContainerTypeAppPermissionGrant();
fileStorageContainerTypeAppPermissionGrant.setAppId("33225700-9a00-4c00-84dd-0c210f203f01");
LinkedList<FileStorageContainerTypeAppPermission> delegatedPermissions = new LinkedList<FileStorageContainerTypeAppPermission>();
delegatedPermissions.add(FileStorageContainerTypeAppPermission.Full);
fileStorageContainerTypeAppPermissionGrant.setDelegatedPermissions(delegatedPermissions);
LinkedList<FileStorageContainerTypeAppPermission> applicationPermissions = new LinkedList<FileStorageContainerTypeAppPermission>();
applicationPermissions.add(FileStorageContainerTypeAppPermission.None);
fileStorageContainerTypeAppPermissionGrant.setApplicationPermissions(applicationPermissions);
applicationPermissionGrants.add(fileStorageContainerTypeAppPermissionGrant);
fileStorageContainerTypeRegistration.setApplicationPermissionGrants(applicationPermissionGrants);
FileStorageContainerTypeRegistration result = graphClient.storage().fileStorage().containerTypeRegistrations().byFileStorageContainerTypeRegistrationId("{fileStorageContainerTypeRegistration-id}").patch(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerTypeRegistration = {
  settings: {
    sharingCapability: 'externalUserAndGuestSharing'
  },
  applicationPermissionGrants: [
    {
      appId: '33225700-9a00-4c00-84dd-0c210f203f01',
      delegatedPermissions: ['full'],
      applicationPermissions: ['none']
    }
  ]
};

await client.api('/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00')
	.update(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeRegistration;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeRegistrationSettings;
use Microsoft\Graph\Generated\Models\SharingCapabilities;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermissionGrant;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermission;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainerTypeRegistration();
$settings = new FileStorageContainerTypeRegistrationSettings();
$settings->setSharingCapability(new SharingCapabilities('externalUserAndGuestSharing'));
$requestBody->setSettings($settings);
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1 = new FileStorageContainerTypeAppPermissionGrant();
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setAppId('33225700-9a00-4c00-84dd-0c210f203f01');
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setDelegatedPermissions([new FileStorageContainerTypeAppPermission('full'),	]);
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setApplicationPermissions([new FileStorageContainerTypeAppPermission('none'),	]);
$applicationPermissionGrantsArray []= $applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1;
$requestBody->setApplicationPermissionGrants($applicationPermissionGrantsArray);


$result = $graphServiceClient->storage()->fileStorage()->containerTypeRegistrations()->byFileStorageContainerTypeRegistrationId('fileStorageContainerTypeRegistration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container_type_registration import FileStorageContainerTypeRegistration
from msgraph.generated.models.file_storage_container_type_registration_settings import FileStorageContainerTypeRegistrationSettings
from msgraph.generated.models.sharing_capabilities import SharingCapabilities
from msgraph.generated.models.file_storage_container_type_app_permission_grant import FileStorageContainerTypeAppPermissionGrant
from msgraph.generated.models.file_storage_container_type_app_permission import FileStorageContainerTypeAppPermission
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainerTypeRegistration(
	settings = FileStorageContainerTypeRegistrationSettings(
		sharing_capability = SharingCapabilities.ExternalUserAndGuestSharing,
	),
	application_permission_grants = [
		FileStorageContainerTypeAppPermissionGrant(
			app_id = "33225700-9a00-4c00-84dd-0c210f203f01",
			delegated_permissions = [
				FileStorageContainerTypeAppPermission.Full,
			],
			application_permissions = [
				FileStorageContainerTypeAppPermission.None,
			],
		),
	],
)

result = await graph_client.storage.file_storage.container_type_registrations.by_file_storage_container_type_registration_id('fileStorageContainerTypeRegistration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 400 Bad Request
```

### Example 3: Update a non-overridable fileStorageContainerTypeRegistration setting

The following example shows how to update a **fileStorageContainerTypeRegistration** setting that isn't overridable in the **fileStorageContainerType**. In this example, the **urlTemplate** property isn't overridable.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00
Content-Type: application/json

{
  "settings": {
    "urlTemplate": "https://fabrikam.example.com/{0}"
  },
  "applicationPermissionGrants": [
    {
      "appId": "33225700-9a00-4c00-84dd-0c210f203f01",
      "delegatedPermissions": ["full"],
      "applicationPermissions": ["none"]
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileStorageContainerTypeRegistration
{
	Settings = new FileStorageContainerTypeRegistrationSettings
	{
		UrlTemplate = "https://fabrikam.example.com/{0}",
	},
	ApplicationPermissionGrants = new List<FileStorageContainerTypeAppPermissionGrant>
	{
		new FileStorageContainerTypeAppPermissionGrant
		{
			AppId = "33225700-9a00-4c00-84dd-0c210f203f01",
			DelegatedPermissions = new List<FileStorageContainerTypeAppPermission?>
			{
				FileStorageContainerTypeAppPermission.Full,
			},
			ApplicationPermissions = new List<FileStorageContainerTypeAppPermission?>
			{
				FileStorageContainerTypeAppPermission.None,
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypeRegistrations["{fileStorageContainerTypeRegistration-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewFileStorageContainerTypeRegistration()
settings := graphmodels.NewFileStorageContainerTypeRegistrationSettings()
urlTemplate := "https://fabrikam.example.com/{0}"
settings.SetUrlTemplate(&urlTemplate) 
requestBody.SetSettings(settings)


fileStorageContainerTypeAppPermissionGrant := graphmodels.NewFileStorageContainerTypeAppPermissionGrant()
appId := "33225700-9a00-4c00-84dd-0c210f203f01"
fileStorageContainerTypeAppPermissionGrant.SetAppId(&appId) 
delegatedPermissions := []graphmodels.FileStorageContainerTypeAppPermissionable {
	fileStorageContainerTypeAppPermission := graphmodels.FULL_FILESTORAGECONTAINERTYPEAPPPERMISSION 
	fileStorageContainerTypeAppPermissionGrant.SetFileStorageContainerTypeAppPermission(&fileStorageContainerTypeAppPermission)
}
fileStorageContainerTypeAppPermissionGrant.SetDelegatedPermissions(delegatedPermissions)
applicationPermissions := []graphmodels.FileStorageContainerTypeAppPermissionable {
	fileStorageContainerTypeAppPermission := graphmodels.NONE_FILESTORAGECONTAINERTYPEAPPPERMISSION 
	fileStorageContainerTypeAppPermissionGrant.SetFileStorageContainerTypeAppPermission(&fileStorageContainerTypeAppPermission)
}
fileStorageContainerTypeAppPermissionGrant.SetApplicationPermissions(applicationPermissions)

applicationPermissionGrants := []graphmodels.FileStorageContainerTypeAppPermissionGrantable {
	fileStorageContainerTypeAppPermissionGrant,
}
requestBody.SetApplicationPermissionGrants(applicationPermissionGrants)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containerTypeRegistrations, err := graphClient.Storage().FileStorage().ContainerTypeRegistrations().ByFileStorageContainerTypeRegistrationId("fileStorageContainerTypeRegistration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerTypeRegistration fileStorageContainerTypeRegistration = new FileStorageContainerTypeRegistration();
FileStorageContainerTypeRegistrationSettings settings = new FileStorageContainerTypeRegistrationSettings();
settings.setUrlTemplate("https://fabrikam.example.com/{0}");
fileStorageContainerTypeRegistration.setSettings(settings);
LinkedList<FileStorageContainerTypeAppPermissionGrant> applicationPermissionGrants = new LinkedList<FileStorageContainerTypeAppPermissionGrant>();
FileStorageContainerTypeAppPermissionGrant fileStorageContainerTypeAppPermissionGrant = new FileStorageContainerTypeAppPermissionGrant();
fileStorageContainerTypeAppPermissionGrant.setAppId("33225700-9a00-4c00-84dd-0c210f203f01");
LinkedList<FileStorageContainerTypeAppPermission> delegatedPermissions = new LinkedList<FileStorageContainerTypeAppPermission>();
delegatedPermissions.add(FileStorageContainerTypeAppPermission.Full);
fileStorageContainerTypeAppPermissionGrant.setDelegatedPermissions(delegatedPermissions);
LinkedList<FileStorageContainerTypeAppPermission> applicationPermissions = new LinkedList<FileStorageContainerTypeAppPermission>();
applicationPermissions.add(FileStorageContainerTypeAppPermission.None);
fileStorageContainerTypeAppPermissionGrant.setApplicationPermissions(applicationPermissions);
applicationPermissionGrants.add(fileStorageContainerTypeAppPermissionGrant);
fileStorageContainerTypeRegistration.setApplicationPermissionGrants(applicationPermissionGrants);
FileStorageContainerTypeRegistration result = graphClient.storage().fileStorage().containerTypeRegistrations().byFileStorageContainerTypeRegistrationId("{fileStorageContainerTypeRegistration-id}").patch(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerTypeRegistration = {
  settings: {
    urlTemplate: 'https://fabrikam.example.com/{0}'
  },
  applicationPermissionGrants: [
    {
      appId: '33225700-9a00-4c00-84dd-0c210f203f01',
      delegatedPermissions: ['full'],
      applicationPermissions: ['none']
    }
  ]
};

await client.api('/storage/fileStorage/containerTypeRegistrations/de988700-d700-020e-0a00-0831f3042f00')
	.update(fileStorageContainerTypeRegistration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeRegistration;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeRegistrationSettings;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermissionGrant;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermission;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainerTypeRegistration();
$settings = new FileStorageContainerTypeRegistrationSettings();
$settings->setUrlTemplate('https://fabrikam.example.com/{0}');
$requestBody->setSettings($settings);
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1 = new FileStorageContainerTypeAppPermissionGrant();
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setAppId('33225700-9a00-4c00-84dd-0c210f203f01');
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setDelegatedPermissions([new FileStorageContainerTypeAppPermission('full'),	]);
$applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1->setApplicationPermissions([new FileStorageContainerTypeAppPermission('none'),	]);
$applicationPermissionGrantsArray []= $applicationPermissionGrantsFileStorageContainerTypeAppPermissionGrant1;
$requestBody->setApplicationPermissionGrants($applicationPermissionGrantsArray);


$result = $graphServiceClient->storage()->fileStorage()->containerTypeRegistrations()->byFileStorageContainerTypeRegistrationId('fileStorageContainerTypeRegistration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container_type_registration import FileStorageContainerTypeRegistration
from msgraph.generated.models.file_storage_container_type_registration_settings import FileStorageContainerTypeRegistrationSettings
from msgraph.generated.models.file_storage_container_type_app_permission_grant import FileStorageContainerTypeAppPermissionGrant
from msgraph.generated.models.file_storage_container_type_app_permission import FileStorageContainerTypeAppPermission
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainerTypeRegistration(
	settings = FileStorageContainerTypeRegistrationSettings(
		url_template = "https://fabrikam.example.com/{0}",
	),
	application_permission_grants = [
		FileStorageContainerTypeAppPermissionGrant(
			app_id = "33225700-9a00-4c00-84dd-0c210f203f01",
			delegated_permissions = [
				FileStorageContainerTypeAppPermission.Full,
			],
			application_permissions = [
				FileStorageContainerTypeAppPermission.None,
			],
		),
	],
)

result = await graph_client.storage.file_storage.container_type_registrations.by_file_storage_container_type_registration_id('fileStorageContainerTypeRegistration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 400 Bad Request
```
