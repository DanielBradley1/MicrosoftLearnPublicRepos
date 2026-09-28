<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainertype-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update fileStorageContainerType

Namespace: microsoft.graph

Update the properties of a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) object. The properties updated are reflected in each registered [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) in a maximum of 24 hours. Settings overridden in a tenant aren't updated.

> **Note**: When the settings are updated, the behavior of any new **fileStorageContainer** changes, but existing containers might require their [settings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) to be updated directly or might not be updated; for example, storage size.

ETag is used for optimistic concurrency control. It must match the value from [Create](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertypes?view=graph-rest-1.0), [Get](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertype-get?view=graph-rest-1.0) or the previous Update.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainerType.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /storage/fileStorage/containerTypes/{fileStorageContainerTypeId}
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
| name | String | Name of the fileStorageContainerType. Optional. |
| settings | [fileStorageContainerTypeSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertypesettings?view=graph-rest-1.0) | fileStorageContainerType settings. Optional. |
| etag | String | Used for optimistic concurrency control. Must match the value returned from a [Create](https://learn.microsoft.com/en-us/graph/api/filestorage-post-containertypes?view=graph-rest-1.0) or [Get](https://learn.microsoft.com/en-us/graph/api/filestoragecontainertype-get?view=graph-rest-1.0) request. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update a fileStorageContainerType

The following example shows how to update a **fileStorageContainerType**.

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
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00
Content-Type: application/json

{
  "settings": {
    "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
    "isItemVersioningEnabled": true,
    "isSharingRestricted": false
  },
  "etag": "RVRhZw=="
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileStorageContainerType
{
	Settings = new FileStorageContainerTypeSettings
	{
		UrlTemplate = "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
		IsItemVersioningEnabled = true,
		IsSharingRestricted = false,
	},
	Etag = "RVRhZw==",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypes["{fileStorageContainerType-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewFileStorageContainerType()
settings := graphmodels.NewFileStorageContainerTypeSettings()
urlTemplate := "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}"
settings.SetUrlTemplate(&urlTemplate) 
isItemVersioningEnabled := true
settings.SetIsItemVersioningEnabled(&isItemVersioningEnabled) 
isSharingRestricted := false
settings.SetIsSharingRestricted(&isSharingRestricted) 
requestBody.SetSettings(settings)
etag := "RVRhZw=="
requestBody.SetEtag(&etag) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containerTypes, err := graphClient.Storage().FileStorage().ContainerTypes().ByFileStorageContainerTypeId("fileStorageContainerType-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerType fileStorageContainerType = new FileStorageContainerType();
FileStorageContainerTypeSettings settings = new FileStorageContainerTypeSettings();
settings.setUrlTemplate("https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}");
settings.setIsItemVersioningEnabled(true);
settings.setIsSharingRestricted(false);
fileStorageContainerType.setSettings(settings);
fileStorageContainerType.setEtag("RVRhZw==");
FileStorageContainerType result = graphClient.storage().fileStorage().containerTypes().byFileStorageContainerTypeId("{fileStorageContainerType-id}").patch(fileStorageContainerType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerType = {
  settings: {
    urlTemplate: 'https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}',
    isItemVersioningEnabled: true,
    isSharingRestricted: false
  },
  etag: 'RVRhZw=='
};

await client.api('/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00')
	.update(fileStorageContainerType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainerType;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainerType();
$settings = new FileStorageContainerTypeSettings();
$settings->setUrlTemplate('https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}');
$settings->setIsItemVersioningEnabled(true);
$settings->setIsSharingRestricted(false);
$requestBody->setSettings($settings);
$requestBody->setEtag('RVRhZw==');

$result = $graphServiceClient->storage()->fileStorage()->containerTypes()->byFileStorageContainerTypeId('fileStorageContainerType-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container_type import FileStorageContainerType
from msgraph.generated.models.file_storage_container_type_settings import FileStorageContainerTypeSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainerType(
	settings = FileStorageContainerTypeSettings(
		url_template = "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
		is_item_versioning_enabled = True,
		is_sharing_restricted = False,
	),
	etag = "RVRhZw==",
)

result = await graph_client.storage.file_storage.container_types.by_file_storage_container_type_id('fileStorageContainerType-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainerType",
  "id": "de988700-d700-020e-0a00-0831f3042f00",
  "name": "Container Type Name",
  "owningAppId": "11335700-9a00-4c00-84dd-0c210f203f00",
  "billingClassification": "trial",
  "billingStatus": "valid",
  "createdDateTime": "01/20/2025",
  "expirationDateTime": "02/20/2025",
  "etag": "RVRhZyArIDE=",
  "settings": {
    "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
    "isDiscoverabilityEnabled": true,
    "isSearchEnabled": true,
    "isItemVersioningEnabled": true,
    "itemMajorVersionLimit": 50,
    "maxStoragePerContainerInBytes": 104857600,
    "isSharingRestricted": false,
    "consumingTenantOverridables": ""
  }
}
```

### Example 2: Update a fileStorageContainerType without ETag

The following example shows how to update a **fileStorageContainerType** without an **etag**.

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
PATCH https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainerType",
  "settings": {
    "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
    "isItemVersioningEnabled": true,
    "isSharingRestricted": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileStorageContainerType
{
	OdataType = "#microsoft.graph.fileStorageContainerType",
	Settings = new FileStorageContainerTypeSettings
	{
		UrlTemplate = "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
		IsItemVersioningEnabled = true,
		IsSharingRestricted = false,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypes["{fileStorageContainerType-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewFileStorageContainerType()
settings := graphmodels.NewFileStorageContainerTypeSettings()
urlTemplate := "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}"
settings.SetUrlTemplate(&urlTemplate) 
isItemVersioningEnabled := true
settings.SetIsItemVersioningEnabled(&isItemVersioningEnabled) 
isSharingRestricted := false
settings.SetIsSharingRestricted(&isSharingRestricted) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containerTypes, err := graphClient.Storage().FileStorage().ContainerTypes().ByFileStorageContainerTypeId("fileStorageContainerType-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerType fileStorageContainerType = new FileStorageContainerType();
fileStorageContainerType.setOdataType("#microsoft.graph.fileStorageContainerType");
FileStorageContainerTypeSettings settings = new FileStorageContainerTypeSettings();
settings.setUrlTemplate("https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}");
settings.setIsItemVersioningEnabled(true);
settings.setIsSharingRestricted(false);
fileStorageContainerType.setSettings(settings);
FileStorageContainerType result = graphClient.storage().fileStorage().containerTypes().byFileStorageContainerTypeId("{fileStorageContainerType-id}").patch(fileStorageContainerType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainerType = {
  '@odata.type': '#microsoft.graph.fileStorageContainerType',
  settings: {
    urlTemplate: 'https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}',
    isItemVersioningEnabled: true,
    isSharingRestricted: false
  }
};

await client.api('/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00')
	.update(fileStorageContainerType);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainerType;
use Microsoft\Graph\Generated\Models\FileStorageContainerTypeSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainerType();
$requestBody->setOdataType('#microsoft.graph.fileStorageContainerType');
$settings = new FileStorageContainerTypeSettings();
$settings->setUrlTemplate('https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}');
$settings->setIsItemVersioningEnabled(true);
$settings->setIsSharingRestricted(false);
$requestBody->setSettings($settings);

$result = $graphServiceClient->storage()->fileStorage()->containerTypes()->byFileStorageContainerTypeId('fileStorageContainerType-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container_type import FileStorageContainerType
from msgraph.generated.models.file_storage_container_type_settings import FileStorageContainerTypeSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainerType(
	odata_type = "#microsoft.graph.fileStorageContainerType",
	settings = FileStorageContainerTypeSettings(
		url_template = "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
		is_item_versioning_enabled = True,
		is_sharing_restricted = False,
	),
)

result = await graph_client.storage.file_storage.container_types.by_file_storage_container_type_id('fileStorageContainerType-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 400 Bad Request
```
