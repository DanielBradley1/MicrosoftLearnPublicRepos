<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointmigrationjob-list-progressevents?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List progressEvents

Namespace: microsoft.graph

Get a list of [migration events](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) for a particular job in a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). The migration events remain valid for four days and can be queried as frequently as needed within the validity period.

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
GET /storage/fileStorage/containers/{fileStorageContainerId}/migrationJobs/{migrationJobId}/progressEvents
```

## Optional query parameters

This method supports the `$skipToken` OData query parameter to help paginate results. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows how to retrieve a list of **sharePointMigrationEvent** instances that are related to the **sharePointMigrationJob** identified by the ID `7b04bfdd-5f8c-4bd9-97faa166a7922c61` that runs on the **fileStorageContainer** identified by the container ID `b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/migrationJobs/7b04bfdd-5f8c-4bd9-97faa166a7922c61/progressEvents
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.Containers["{fileStorageContainer-id}"].MigrationJobs["{sharePointMigrationJob-id}"].ProgressEvents.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
progressEvents, err := graphClient.Storage().FileStorage().Containers().ByFileStorageContainerId("fileStorageContainer-id").MigrationJobs().BySharePointMigrationJobId("sharePointMigrationJob-id").ProgressEvents().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SharePointMigrationEventCollectionResponse result = graphClient.storage().fileStorage().containers().byFileStorageContainerId("{fileStorageContainer-id}").migrationJobs().bySharePointMigrationJobId("{sharePointMigrationJob-id}").progressEvents().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let progressEvents = await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/migrationJobs/7b04bfdd-5f8c-4bd9-97faa166a7922c61/progressEvents')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->storage()->fileStorage()->containers()->byFileStorageContainerId('fileStorageContainer-id')->migrationJobs()->bySharePointMigrationJobId('sharePointMigrationJob-id')->progressEvents()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.storage.file_storage.containers.by_file_storage_container_id('fileStorageContainer-id').migration_jobs.by_share_point_migration_job_id('sharePointMigrationJob-id').progress_events.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.sharePointMigrationJobStartEvent",
      "id": "ef788cc0-ff2c-02a7-5150-7aeb53a89445",
      "jobId": "7b04bfdd-5f8c-4bd9-97fa-a166a7922c61",
      "eventDateTime": "2025-05-08T09:08:04.451Z",
      "correlationId": "3f24ae21-8e47-4147-aa3d-31ce6b675337",
      "isRestarted": false,
      "totalRetryCount": 0
    },
    {
      "@odata.type": "#microsoft.graph.sharePointMigrationJobCancelledEvent",
      "id": "8ae8a944-1d91-4e16-3447-0e31ba915e1f",
      "jobId": "7b04bfdd-5f8c-4bd9-97fa-a166a7922c61",
      "eventDateTime": "2025-05-08T09:13:18.333Z",
      "correlationId": "3f24ae21-8e47-4147-aa3d-31ce6b675337",
      "totalRetryCount": 0,
      "isCancelledByUser": true
    },
    {
      "@odata.type": "#microsoft.graph.sharePointMigrationJobProgressEvent",
      "id": "e439f60c-1022-4eaa-dbbf-75c51361effe",
      "jobId": "7b04bfdd-5f8c-4bd9-97fa-a166a7922c61",
      "eventDateTime": "2025-05-08T09:13:45.565Z",
      "correlationId": "3f24ae21-8e47-4147-aa3d-31ce6b675337",
      "isCompleted": false,
      "filesProcessed": 12,
      "bytesProcessed": 12,
      "objectsProcessed": 23,
      "totalExpectedObjects": 15,
      "totalErrors": 1,
      "totalWarnings": 0,
      "totalRetryCount": 0,
      "waitTimeOnSqlThrottlingMs": 0,
      "totalDurationMs": 0,
      "cpuDurationMs": 0,
      "sqlDurationMs": 0,
      "sqlQueryCount": 0,
      "totalExpectedBytes": 0,
      "filesProcessedOnlyCurrentVersion": 11,
      "bytesProcessedOnlyCurrentVersion": 11
    },
    {
      "@odata.type": "#microsoft.graph.sharePointMigrationJobErrorEvent",
      "id": "8e37738c-76b2-bb16-346a-5b21cff6d1d0",
      "jobId": "7b04bfdd-5f8c-4bd9-97fa-a166a7922c61",
      "eventDateTime": "2025-05-08T09:13:46.028Z",
      "correlationId": "3f24ae21-8e47-4147-aa3d-31ce6b675337",
      "errorLevel": "FatalError",
      "totalRetryCount": 0,
      "objectType": "UnknownFutureValue",
      "error": 
      {
        "code": "-2147213196",
        "errorType": "microsoft.SharePoint.SPException",
        "message": "Operation canceled."
      }
    },
    {
      "@odata.type": "#microsoft.graph.sharePointMigrationJobProgressEvent",
      "id": "16ea963f-b78d-5016-e8b7-3c663ca30fd5",
      "jobId": "7b04bfdd-5f8c-4bd9-97fa-a166a7922c61",
      "eventDateTime": "2025-05-08T09:13:46.509Z",
      "correlationId": "3f24ae21-8e47-4147-aa3d-31ce6b675337",
      "isCompleted": true,
      "filesProcessed": 12,
      "bytesProcessed": 12,
      "objectsProcessed": 24,
      "totalExpectedObjects": 15,
      "totalErrors": 2,
      "totalWarnings": 0,
      "totalRetryCount": 0,
      "waitTimeOnSqlThrottlingMs": 0,
      "totalDurationMs": 0,
      "cpuDurationMs": 0,
      "sqlDurationMs": 0,
      "sqlQueryCount": 0,
      "totalExpectedBytes": 0,
      "filesProcessedOnlyCurrentVersion": 12,
      "bytesProcessedOnlyCurrentVersion": 12
    }
  ],
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/migrationJobs/7b04bfdd-5f8c-4bd9-97fa-a166a7922c61/progressEvents?$skiptoken=ODY4MA"
}
```
