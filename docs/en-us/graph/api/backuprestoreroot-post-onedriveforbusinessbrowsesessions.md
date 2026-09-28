<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-post-onedriveforbusinessbrowsesessions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Create oneDriveForBusinessBrowseSession

Namespace: microsoft.graph

Create a new [oneDriveForBusinessBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessbrowsesession?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.ReadWrite.All | Not available. |

Note

In the delegated flow, only users with the *SharePoint Backup Administrator* role can access this API.

## HTTP request

```http
POST /solutions/backupRestore/oneDriveForBusinessBrowseSessions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [oneDriveForBusinessBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessbrowsesession?view=graph-rest-1.0) object.

You can specify the following properties when you create a **oneDriveForBusinessBrowseSession**.

| Property | Type | Description |
| :--- | :--- | :--- |
| restorePointId | String | The ID of the [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) on which the user wants to create a browse session. Required. |

## Response

If successful, this method returns a `201 Created` response code and an [oneDriveForBusinessBrowseSession](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessbrowsesession?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessBrowseSessions
Content-Type: application/json

{
  "restorePointId": "TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE="
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OneDriveForBusinessBrowseSession
{
	RestorePointId = "TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE=",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.OneDriveForBusinessBrowseSessions.PostAsync(requestBody);
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

requestBody := graphmodels.NewOneDriveForBusinessBrowseSession()
restorePointId := "TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE="
requestBody.SetRestorePointId(&restorePointId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
oneDriveForBusinessBrowseSessions, err := graphClient.Solutions().BackupRestore().OneDriveForBusinessBrowseSessions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OneDriveForBusinessBrowseSession oneDriveForBusinessBrowseSession = new OneDriveForBusinessBrowseSession();
oneDriveForBusinessBrowseSession.setRestorePointId("TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE=");
OneDriveForBusinessBrowseSession result = graphClient.solutions().backupRestore().oneDriveForBusinessBrowseSessions().post(oneDriveForBusinessBrowseSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const oneDriveForBusinessBrowseSession = {
  restorePointId: 'TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE='
};

await client.api('/solutions/backupRestore/oneDriveForBusinessBrowseSessions')
	.post(oneDriveForBusinessBrowseSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OneDriveForBusinessBrowseSession;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OneDriveForBusinessBrowseSession();
$requestBody->setRestorePointId('TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE=');

$result = $graphServiceClient->solutions()->backupRestore()->oneDriveForBusinessBrowseSessions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	restorePointId = "TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE="
}

New-MgSolutionBackupRestoreOneDriveForBusinessBrowseSession -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.one_drive_for_business_browse_session import OneDriveForBusinessBrowseSession
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OneDriveForBusinessBrowseSession(
	restore_point_id = "TXpSbE5HUXpNR1l0TldZMFlpMDBNMk16TFdFeFl6WXRZall3TTJFeFl6Sm1OV000WHpFPV8xNzQ5NTY3MDAwXzE0XzE=",
)

result = await graph_client.solutions.backup_restore.one_drive_for_business_browse_sessions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#solutions/backupRestore/oneDriveForBusinessBrowseSessions/$entity",
    "id": "m_RtZ8BiiUXOK69cuN6gwubfm9_yeVlDg8s6hci01_cVOAE",
    "restorePointDateTime": "2026-01-18T03:00:15Z",
    "status": "created",
    "createdDateTime": "2026-01-20T10:42:27Z",
    "expirationDateTime": "2026-01-23T10:42:24Z",
    "backupSizeInBytes": "584316",
    "directoryObjectId": "f3846f8d-80a6-4480-ae20-5966ebdf2009"
}
```
