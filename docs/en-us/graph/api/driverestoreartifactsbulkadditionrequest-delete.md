<!-- Source: https://learn.microsoft.com/en-us/graph/api/driverestoreartifactsbulkadditionrequest-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-28 -->

# Delete driveRestoreArtifactsBulkAdditionRequest

Namespace: microsoft.graph

Delete a [driveRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/driverestoreartifactsbulkadditionrequest?view=graph-rest-1.0) object associated with a [oneDriveForBusinessRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessrestoresession?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

## HTTP request

```http
DELETE /solutions/backupRestore/oneDriveForBusinessRestoreSessions/{oneDriveForBusinessRestoreSessionId}/driveRestoreArtifactsBulkAdditionRequests/{driveRestoreArtifactsBulkAdditionRequestId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

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
DELETE https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessRestoreSessions/d8078599-3b3c-468d-b6ff-adf161a42760/driveRestoreArtifactsBulkAdditionRequests/4437afcf-e520-463c-90a7-ca96401d8039
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Solutions.BackupRestore.OneDriveForBusinessRestoreSessions["{oneDriveForBusinessRestoreSession-id}"].DriveRestoreArtifactsBulkAdditionRequests["{driveRestoreArtifactsBulkAdditionRequest-id}"].DeleteAsync();
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
graphClient.Solutions().BackupRestore().OneDriveForBusinessRestoreSessions().ByOneDriveForBusinessRestoreSessionId("oneDriveForBusinessRestoreSession-id").DriveRestoreArtifactsBulkAdditionRequests().ByDriveRestoreArtifactsBulkAdditionRequestId("driveRestoreArtifactsBulkAdditionRequest-id").Delete(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.solutions().backupRestore().oneDriveForBusinessRestoreSessions().byOneDriveForBusinessRestoreSessionId("{oneDriveForBusinessRestoreSession-id}").driveRestoreArtifactsBulkAdditionRequests().byDriveRestoreArtifactsBulkAdditionRequestId("{driveRestoreArtifactsBulkAdditionRequest-id}").delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/oneDriveForBusinessRestoreSessions/d8078599-3b3c-468d-b6ff-adf161a42760/driveRestoreArtifactsBulkAdditionRequests/4437afcf-e520-463c-90a7-ca96401d8039')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessRestoreSessions()->byOneDriveForBusinessRestoreSessionId('oneDriveForBusinessRestoreSession-id')->driveRestoreArtifactsBulkAdditionRequests()->byDriveRestoreArtifactsBulkAdditionRequestId('driveRestoreArtifactsBulkAdditionRequest-id')->delete()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Remove-MgSolutionBackupRestoreOneDriveForBusinessRestoreSessionDriveRestoreArtifactBulkAdditionRequest -OneDriveForBusinessRestoreSessionId $oneDriveForBusinessRestoreSessionId -DriveRestoreArtifactsBulkAdditionRequestId $driveRestoreArtifactsBulkAdditionRequestId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.solutions.backup_restore.one_drive_for_business_restore_sessions.by_one_drive_for_business_restore_session_id('oneDriveForBusinessRestoreSession-id').drive_restore_artifacts_bulk_addition_requests.by_drive_restore_artifacts_bulk_addition_request_id('driveRestoreArtifactsBulkAdditionRequest-id').delete()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
