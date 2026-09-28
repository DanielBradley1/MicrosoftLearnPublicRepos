<!-- Source: https://learn.microsoft.com/en-us/graph/api/driverestoreartifactsbulkadditionrequest-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get driveRestoreArtifactsBulkAdditionRequest

Namespace: microsoft.graph

Get a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object by its **id**, associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.Read.All | Not available. |

## HTTP request

```http
GET /solutions/backupRestore/oneDriveForBusinessRestoreSessions/{oneDriveForBusinessRestoreSessionId}/driveRestoreArtifactsBulkAdditionRequests/{driveRestoreArtifactsBulkAdditionRequestId}
```

## Optional query parameters

This method doesn't support the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

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
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions/493635f0-b8c0-4c7f-bcb7-b20c85d97efe/driveRestoreArtifactsBulkAdditionRequests/e79d0a79-7210-4369-9177-6297f0555242
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessRestoreSessions["{oneDriveForBusinessRestoreSession-id}"].DriveRestoreArtifactsBulkAdditionRequests["{driveRestoreArtifactsBulkAdditionRequest-id}"].GetAsync();
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
driveRestoreArtifactsBulkAdditionRequests, err := graphClient.Solutions().BackupRestore().OneDriveForBusinessRestoreSessions().ByOneDriveForBusinessRestoreSessionId("oneDriveForBusinessRestoreSession-id").DriveRestoreArtifactsBulkAdditionRequests().ByDriveRestoreArtifactsBulkAdditionRequestId("driveRestoreArtifactsBulkAdditionRequest-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DriveRestoreArtifactsBulkAdditionRequest result = graphClient.solutions().backupRestore().oneDriveForBusinessRestoreSessions().byOneDriveForBusinessRestoreSessionId("{oneDriveForBusinessRestoreSession-id}").driveRestoreArtifactsBulkAdditionRequests().byDriveRestoreArtifactsBulkAdditionRequestId("{driveRestoreArtifactsBulkAdditionRequest-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let driveRestoreArtifactsBulkAdditionRequest = await client.api('/solutions/backupRestore/oneDriveForBusinessRestoreSessions/493635f0-b8c0-4c7f-bcb7-b20c85d97efe/driveRestoreArtifactsBulkAdditionRequests/e79d0a79-7210-4369-9177-6297f0555242')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessRestoreSessions()->byOneDriveForBusinessRestoreSessionId('oneDriveForBusinessRestoreSession-id')->driveRestoreArtifactsBulkAdditionRequests()->byDriveRestoreArtifactsBulkAdditionRequestId('driveRestoreArtifactsBulkAdditionRequest-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestoreOneDriveForBusinessRestoreSessionDriveRestoreArtifactBulkAdditionRequest -OneDriveForBusinessRestoreSessionId $oneDriveForBusinessRestoreSessionId -DriveRestoreArtifactsBulkAdditionRequestId $driveRestoreArtifactsBulkAdditionRequestId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.one_drive_for_business_restore_sessions.by_one_drive_for_business_restore_session_id('oneDriveForBusinessRestoreSession-id').drive_restore_artifacts_bulk_addition_requests.by_drive_restore_artifacts_bulk_addition_request_id('driveRestoreArtifactsBulkAdditionRequest-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.driveRestoreArtifactsBulkAdditionRequest",
  "drives": [],
  "id": "e79d0a79-7210-4369-9177-6297f0555242",
  "destinationType": "new",
  "tags": "fastRestore",
  "restorePointPreference": "latest",
  "displayName": "ODB-BulkRestoreArtifacts",
  "status": "active",
  "createdDateTime": "2024-12-04T07:51:58.9045003Z",
  "lastModifiedDateTime": "2024-12-04T07:51:58.9045003Z",
  "protectionTimePeriod": {
    "startDateTime": "2024-01-01T00:00:00Z",
    "endDateTime": "2024-01-08T00:00:00Z"
  },
  "createdBy": {
    "user": {
      "identity": "6f707fc8-0250-4fd5-89b5-c0312bea7460"
    }
  },
  "lastModifiedBy": {
    "user": {
      "identity": "6f707fc8-0250-4fd5-89b5-c0312bea7460"
    }
  }
}
```
