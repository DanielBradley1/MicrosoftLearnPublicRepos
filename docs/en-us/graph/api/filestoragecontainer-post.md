<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Create fileStorageContainer

Namespace: microsoft.graph

Create a new [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object.

The container type identified by **containerTypeId** must be registered in the tenant.

For delegated calls, the calling user is set as the owner of the **fileStorageContainer**.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | Not available. |
| Delegated \(personal Microsoft account\) | FileStorageContainer.Selected | Not available. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

## HTTP request

```http
POST /storage/fileStorage/containers
```

## Optional query parameters

This method supports the following OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Description |
| :--- | :--- |
| dataLocation | Specifies the desired data location for container creation in Multi-Geo tenants. Omitting the `dataLocation` parameter in the request creates the container at the tenant's default location. For more information, see [available Multi-Geo regions and their location codes](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo#microsoft-365-multi-geo-availability). |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object.

You can specify the following properties when you create a **fileStorageContainer**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the container. Required. |
| description | String | User-visible description of the container. Optional. |
| containerTypeId | GUID | The container type of the container instance. Required. |
| settings | [fileStorageContainerSettings](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainersettings?view=graph-rest-1.0) | Settings associated with the container. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows how to create a **fileStorageContainer**.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers
Content-Type: application/json

{
  "displayName": "My Application Storage Container",
  "description": "Description of My Application Storage Container",
  "containerTypeId": "91710488-5756-407f-9046-fbe5f0b4de73",
  "settings": {
    "isOcrEnabled": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileStorageContainer
{
	DisplayName = "My Application Storage Container",
	Description = "Description of My Application Storage Container",
	ContainerTypeId = Guid.Parse("91710488-5756-407f-9046-fbe5f0b4de73"),
	Settings = new FileStorageContainerSettings
	{
		IsOcrEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.Containers.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "github.com/google/uuid"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewFileStorageContainer()
displayName := "My Application Storage Container"
requestBody.SetDisplayName(&displayName) 
description := "Description of My Application Storage Container"
requestBody.SetDescription(&description) 
containerTypeId := uuid.MustParse("91710488-5756-407f-9046-fbe5f0b4de73")
requestBody.SetContainerTypeId(&containerTypeId) 
settings := graphmodels.NewFileStorageContainerSettings()
isOcrEnabled := true
settings.SetIsOcrEnabled(&isOcrEnabled) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
containers, err := graphClient.Storage().FileStorage().Containers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainer fileStorageContainer = new FileStorageContainer();
fileStorageContainer.setDisplayName("My Application Storage Container");
fileStorageContainer.setDescription("Description of My Application Storage Container");
fileStorageContainer.setContainerTypeId(UUID.fromString("91710488-5756-407f-9046-fbe5f0b4de73"));
FileStorageContainerSettings settings = new FileStorageContainerSettings();
settings.setIsOcrEnabled(true);
fileStorageContainer.setSettings(settings);
FileStorageContainer result = graphClient.storage().fileStorage().containers().post(fileStorageContainer);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fileStorageContainer = {
  displayName: 'My Application Storage Container',
  description: 'Description of My Application Storage Container',
  containerTypeId: '91710488-5756-407f-9046-fbe5f0b4de73',
  settings: {
    isOcrEnabled: true
  }
};

await client.api('/storage/fileStorage/containers')
	.post(fileStorageContainer);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileStorageContainer;
use Microsoft\Graph\Generated\Models\FileStorageContainerSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileStorageContainer();
$requestBody->setDisplayName('My Application Storage Container');
$requestBody->setDescription('Description of My Application Storage Container');
$requestBody->setContainerTypeId('91710488-5756-407f-9046-fbe5f0b4de73');
$settings = new FileStorageContainerSettings();
$settings->setIsOcrEnabled(true);
$requestBody->setSettings($settings);

$result = $graphServiceClient->storage()->fileStorage()->containers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_storage_container import FileStorageContainer
from msgraph.generated.models.file_storage_container_settings import FileStorageContainerSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileStorageContainer(
	display_name = "My Application Storage Container",
	description = "Description of My Application Storage Container",
	container_type_id = UUID("91710488-5756-407f-9046-fbe5f0b4de73"),
	settings = FileStorageContainerSettings(
		is_ocr_enabled = True,
	),
)

result = await graph_client.storage.file_storage.containers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.fileStorageContainer",
  "id": "b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z",
  "displayName": "My Application Storage Container",
  "description": "Description of My Application Storage Container",
  "containerTypeId": "91710488-5756-407f-9046-fbe5f0b4de73",
  "status": "inactive",
  "createdDateTime": "2021-11-24T15:41:52.347Z",
  "settings": {
    "isOcrEnabled": false,
    "itemMajorVersionLimit": 50,
    "isItemVersioningEnabled": true
  }
}
```
