<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-migrationjobs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create sharePointMigrationJob

Namespace: microsoft.graph

Create a new [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) object that is scheduled to run at a later time to migrate content from an intermediary storage to the target [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainer.Selected | Not available. |

## HTTP request

```http
POST /storage/fileStorage/containers/{fileStorageContainerId}/migrationJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [sharePointMigrationContainerInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationcontainerinfo?view=graph-rest-1.0) object.

You can specify the following properties when you create a **sharePointMigrationContainerInfo** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| containerInfo | [sharePointMigrationContainerInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationcontainerinfo?view=graph-rest-1.0) | The intermediate storage to temporarily store the file content and metadata. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows how to create a **sharePointMigrationJob** that runs on the **fileStorageContainer** identified by the container ID `b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/migrationJobs
Content-Type: application/json

{
  "containerInfo": {
    "dataContainerUri": "https://spoxxx.blob.core.windows.net/data?sp=rw&sig=",
    "metadataContainerUri": "https://spoxxx.blob.core.windows.net/metadata?sp=rw&sig=",
    "encryptionKey": "base64 encoded key for AES-256-CBC encryption"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SharePointMigrationJob
{
	ContainerInfo = new SharePointMigrationContainerInfo
	{
		DataContainerUri = "https://spoxxx.blob.core.windows.net/data?sp=rw&sig=",
		MetadataContainerUri = "https://spoxxx.blob.core.windows.net/metadata?sp=rw&sig=",
		EncryptionKey = "base64 encoded key for AES-256-CBC encryption",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.Containers["{fileStorageContainer-id}"].MigrationJobs.PostAsync(requestBody);
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

requestBody := graphmodels.NewSharePointMigrationJob()
containerInfo := graphmodels.NewSharePointMigrationContainerInfo()
dataContainerUri := "https://spoxxx.blob.core.windows.net/data?sp=rw&sig="
containerInfo.SetDataContainerUri(&dataContainerUri) 
metadataContainerUri := "https://spoxxx.blob.core.windows.net/metadata?sp=rw&sig="
containerInfo.SetMetadataContainerUri(&metadataContainerUri) 
encryptionKey := "base64 encoded key for AES-256-CBC encryption"
containerInfo.SetEncryptionKey(&encryptionKey) 
requestBody.SetContainerInfo(containerInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
migrationJobs, err := graphClient.Storage().FileStorage().Containers().ByFileStorageContainerId("fileStorageContainer-id").MigrationJobs().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationJob sharePointMigrationJob = new SharePointMigrationJob();
SharePointMigrationContainerInfo containerInfo = new SharePointMigrationContainerInfo();
containerInfo.setDataContainerUri("https://spoxxx.blob.core.windows.net/data?sp=rw&sig=");
containerInfo.setMetadataContainerUri("https://spoxxx.blob.core.windows.net/metadata?sp=rw&sig=");
containerInfo.setEncryptionKey("base64 encoded key for AES-256-CBC encryption");
sharePointMigrationJob.setContainerInfo(containerInfo);
SharePointMigrationJob result = graphClient.storage().fileStorage().containers().byFileStorageContainerId("{fileStorageContainer-id}").migrationJobs().post(sharePointMigrationJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sharePointMigrationJob = {
  containerInfo: {
    dataContainerUri: 'https://spoxxx.blob.core.windows.net/data?sp=rw&sig=',
    metadataContainerUri: 'https://spoxxx.blob.core.windows.net/metadata?sp=rw&sig=',
    encryptionKey: 'base64 encoded key for AES-256-CBC encryption'
  }
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/migrationJobs')
	.post(sharePointMigrationJob);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SharePointMigrationJob;
use Microsoft\Graph\Generated\Models\SharePointMigrationContainerInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePointMigrationJob();
$containerInfo = new SharePointMigrationContainerInfo();
$containerInfo->setDataContainerUri('https://spoxxx.blob.core.windows.net/data?sp=rw&sig=');
$containerInfo->setMetadataContainerUri('https://spoxxx.blob.core.windows.net/metadata?sp=rw&sig=');
$containerInfo->setEncryptionKey('base64 encoded key for AES-256-CBC encryption');
$requestBody->setContainerInfo($containerInfo);

$result = $graphServiceClient->storage()->fileStorage()->containers()->byFileStorageContainerId('fileStorageContainer-id')->migrationJobs()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.share_point_migration_job import SharePointMigrationJob
from msgraph.generated.models.share_point_migration_container_info import SharePointMigrationContainerInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePointMigrationJob(
	container_info = SharePointMigrationContainerInfo(
		data_container_uri = "https://spoxxx.blob.core.windows.net/data?sp=rw&sig=",
		metadata_container_uri = "https://spoxxx.blob.core.windows.net/metadata?sp=rw&sig=",
		encryption_key = "base64 encoded key for AES-256-CBC encryption",
	),
)

result = await graph_client.storage.file_storage.containers.by_file_storage_container_id('fileStorageContainer-id').migration_jobs.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "31090ce2-3b99-fa40-7ec5-46ebeeb5900b"
}
```
