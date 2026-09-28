<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointrestoresession-list-siterestoreartifacts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List siteRestoreArtifacts

Namespace: microsoft.graph

List all the [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0) objects for a [sharePointRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/sharepointrestoresession?view=graph-rest-1.0) for the tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Restore.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Restore.Read.All | Not available. |

## HTTP request

```http
GET /solutions/backupRestore/sharePointRestoreSessions/{sharePointRestoreSessionId}/siteRestoreArtifacts
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [siteRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/siterestoreartifact?view=graph-rest-1.0) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952e/siteRestoreArtifacts
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.SharePointRestoreSessions["{sharePointRestoreSession-id}"].SiteRestoreArtifacts.GetAsync();
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
siteRestoreArtifacts, err := graphClient.Solutions().BackupRestore().SharePointRestoreSessions().BySharePointRestoreSessionId("sharePointRestoreSession-id").SiteRestoreArtifacts().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SiteRestoreArtifactCollectionResponse result = graphClient.solutions().backupRestore().sharePointRestoreSessions().bySharePointRestoreSessionId("{sharePointRestoreSession-id}").siteRestoreArtifacts().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let siteRestoreArtifacts = await client.api('/solutions/backupRestore/sharePointRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952e/siteRestoreArtifacts')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->sharePointRestoreSessions()->bySharePointRestoreSessionId('sharePointRestoreSession-id')->siteRestoreArtifacts()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestoreSharePointRestoreSessionSiteRestoreArtifact -SharePointRestoreSessionId $sharePointRestoreSessionId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.share_point_restore_sessions.by_share_point_restore_session_id('sharePointRestoreSession-id').site_restore_artifacts.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.id": "/solutions/backupRestore/sharepointRestoreSessions(845457dc-4bb2-4815-bef3-8628ebd1952e)",
  "@odata.nextLink": "/solutions/backupRestore/sharepointRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952e/siteRestoreArtifacts?$skiptoken=M2UyZDAwMDAwMDMxMzkzYTMyNjQ2MTM0NjMzMjM5NjYzNjY0MzczMDM0MzE2NTYzNjEzNzMwNjIzNjMzMzg2MjM0MzM2NDM0MzUzNDMzMzc0MDc0Njg3MjY1NjE2NDJlNzYzMjAxZThmYjY4M2Y3ODAxMDAwMDg4NjA5ODdhNzgwMTAwMDB8MTYxNjk2NDUwOTgzMg%3d%3d",
  "value": [
    {
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18a",
      "destinationType": "inPlace",
      "status": "succeeded",
      "startDateTime": "2023-12-04T12:18:55.2117521Z",
      "completionDateTime": "2023-12-04T13:22:12.7209691Z",
      "restoredSiteId": "42f0e20e-748a-4444-80bb-d641d1865574",
      "restoredSiteName": "testsite101",
      "restoredSiteWebUrl": "https://a830edad9050849odb10gb.sharepoint.com/sites/testsite101R3",
      "restorePoint": {
        "id": "c7e702b7-b5ee-4faf-9e43-5fd23b4fb0bf_1701648000_14_1",
        "protectionDateTime": "2023-12-04T00:00:00Z",
        "expirationDateTime": "2023-12-18T00:00:00Z"
      }
    },
    {
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18b",
      "destinationType": "new",
      "status": "succeeded",
      "startDateTime": "2024-02-10T12:18:55.2117521Z",
      "completionDateTime": "2024-02-10T13:22:12.7209691Z",
      "restoredSiteId": "da60e844-ba1d-49bc-b4d4-d5e36bae9019",
      "restoredSiteName": "testsite102",
      "restoredSiteWebUrl": "https://a830edad9050849odb10gb.sharepoint.com/sites/testsite102R0",
      "restorePoint": {
        "id": "28684b23-7f38-44bc-91c0-a3c92758030d_1601648000_14_1",
        "protectionDateTime": "2024-02-10T00:00:00Z",
        "expirationDateTime": "2024-02-24T00:00:00Z"
      }
    }
  ]
}
```
