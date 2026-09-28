<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainertypeapppermissiongrant-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update fileStorageContainerTypeAppPermissionGrant

Namespace: microsoft.graph

Update the properties of a [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) object.

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
- Updated permission grants may take up to one hour to propagate.

## HTTP request

```http
PATCH /storage/fileStorage/containerTypeRegistrations/{fileStorageContainerTypeRegistrationId}/applicationPermissionGrants/{appId}
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
| applicationPermissions | fileStorageContainerTypeAppPermission collection | Allowed permissions when you use application tokens with the defined **appId**. The possible values are: `none`, `readContent`, `writeContent`, `manageContent`, `create`, `delete`, `read`, `write`, `enumeratePermissions`, `addPermissions`, `updatePermissions`, `deletePermissions`, `deleteOwnPermission`, `managePermissions`, `full`, `unknownFutureValue`. Optional. |
| delegatedPermissions | fileStorageContainerTypeAppPermission collection | Allowed permissions when you use delegated tokens with the defined **appId**. The possible values are: `none`, `readContent`, `writeContent`, `manageContent`, `create`, `delete`, `read`, `write`, `enumeratePermissions`, `addPermissions`, `updatePermissions`, `deletePermissions`, `deleteOwnPermission`, `managePermissions`, `full`, `unknownFutureValue`. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [fileStorageContainerTypeAppPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypeapppermissiongrant?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows how to update app-only permissions in an existing app permission grant.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations/21b52d99-7114-4c47-80b3-362b6a0bba3a/applicationPermissionGrants/11335700-9a00-4c00-84dd-0c210f203f00
Content-Type: application/json

{
  "applicationPermissions": ["full"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileStorageContainerTypeAppPermissionGrant
{
	ApplicationPermissions = new List<FileStorageContainerTypeAppPermission?>
	{
		FileStorageContainerTypeAppPermission.Full,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypeRegistrations["{fileStorageContainerTypeRegistration-id}"].ApplicationPermissionGrants["{fileStorageContainerTypeAppPermissionGrant-appId}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewFileStorageContainerTypeAppPermissionGrant()
applicationPermissions := []graphmodels.FileStorageContainerTypeAppPermissionable {
	fileStorageContainerTypeAppPermission := graphmodels.FULL_FILESTORAGECONTAINERTYPEAPPPERMISSION 
	requestBody.SetFileStorageContainerTypeAppPermission(&fileStorageContainerTypeAppPermission)
}
requestBody.SetApplicationPermissions(applicationPermissions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
applicationPermissionGrants, err := graphClient.Storage().FileStorage().ContainerTypeRegistrations().ByFileStorageContainerTypeRegistrationId("fileStorageContainerTypeRegistration-id").ApplicationPermissionGrants().ByFileStorageContainerTypeAppPermissionGrantAppId("fileStorageContainerTypeAppPermissionGrant-appId").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerTypeAppPermissionGrant fileStorageContainerTypeAppPermissionGrant = new FileStorageContainerTypeAppPermissionGrant();
LinkedList<FileStorageContainerTypeAppPermission> applicationPermissions = new LinkedList<FileStorageContainerTypeAppPermission>();
applicationPermissions.add(FileStorageContainerTypeAppPermission.Full);
fileStorageContainerTypeAppPermissionGrant.setApplicationPermissions(applicationPermissions);
FileStorageContainerTypeAppPermissionGrant result = graphClient.storage().fileStorage().containerTypeRegistrations().byFileStorageContainerTypeRegistrationId("{fileStorageContainerTypeRegistration-id}").applicationPermissionGrants().byFileStorageContainerTypeAppPermissionGrantAppId("{fileStorageContainerTypeAppPermissionGrant-appId}").patch(fileStorageContainerTypeAppPermissionGrant);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerTypeAppPermissionGrant = {
  applicationPermissions: ['full']
};

await client.api('/storage/fileStorage/containerTypeRegistrations/21b52d99-7114-4c47-80b3-362b6a0bba3a/applicationPermissionGrants/11335700-9a00-4c00-84dd-0c210f203f00')
	.update(fileStorageContainerTypeAppPermissionGrant);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermissionGrant;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeAppPermission;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainerTypeAppPermissionGrant();
$requestBody->setApplicationPermissions([new FileStorageContainerTypeAppPermission('full'),	]);

$result = $graphServiceClient->storage()->fileStorage()->containerTypeRegistrations()->byFileStorageContainerTypeRegistrationId('fileStorageContainerTypeRegistration-id')->applicationPermissionGrants()->byFileStorageContainerTypeAppPermissionGrantAppId('fileStorageContainerTypeAppPermissionGrant-appId')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container_type_app_permission_grant import FileStorageContainerTypeAppPermissionGrant
from msgraph.generated.models.file_storage_container_type_app_permission import FileStorageContainerTypeAppPermission
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainerTypeAppPermissionGrant(
	application_permissions = [
		FileStorageContainerTypeAppPermission.Full,
	],
)

result = await graph_client.storage.file_storage.container_type_registrations.by_file_storage_container_type_registration_id('fileStorageContainerTypeRegistration-id').application_permission_grants.by_file_storage_container_type_app_permission_grant_app_id('fileStorageContainerTypeAppPermissionGrant-appId').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainerTypeAppPermissionGrant",
  "appId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "delegatedPermissions": ["readContent", "writeContent"],
  "applicationPermissions": ["full"]
}
```
