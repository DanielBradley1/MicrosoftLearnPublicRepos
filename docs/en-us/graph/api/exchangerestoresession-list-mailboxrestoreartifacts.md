<!-- Source: https://learn.microsoft.com/en-us/graph/api/exchangerestoresession-list-mailboxrestoreartifacts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-10 -->

# List mailboxRestoreArtifacts

Namespace: microsoft.graph

Get a list of the [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) objects that are associated with an [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0) in a tenant.

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
GET /solutions/backupRestore/exchangeRestoreSessions/{exchangeRestoreSessionId}/mailboxRestoreArtifacts
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [mailboxRestoreArtifact](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifact?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952e/mailboxRestoreArtifacts
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeRestoreSessions["{exchangeRestoreSession-id}"].MailboxRestoreArtifacts.GetAsync();
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
mailboxRestoreArtifacts, err := graphClient.Solutions().BackupRestore().ExchangeRestoreSessions().ByExchangeRestoreSessionId("exchangeRestoreSession-id").MailboxRestoreArtifacts().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxRestoreArtifactCollectionResponse result = graphClient.solutions().backupRestore().exchangeRestoreSessions().byExchangeRestoreSessionId("{exchangeRestoreSession-id}").mailboxRestoreArtifacts().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let mailboxRestoreArtifacts = await client.api('/solutions/backupRestore/exchangeRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952e/mailboxRestoreArtifacts')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->exchangeRestoreSessions()->byExchangeRestoreSessionId('exchangeRestoreSession-id')->mailboxRestoreArtifacts()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestoreExchangeRestoreSessionMailboxRestoreArtifact -ExchangeRestoreSessionId $exchangeRestoreSessionId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.exchange_restore_sessions.by_exchange_restore_session_id('exchangeRestoreSession-id').mailbox_restore_artifacts.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.nextLink": "/solutions/backupRestore/exchangeRestoreSessions/845457dc-4bb2-4815-bef3-8628ebd1952e/mailboxRestoreArtifacts?$skiptoken=M2UyZDAwMDAwMDMxMzkzYTMyNjQ2MTM0NjMzMjM5NjYzNjY0MzczMDM0MzE2NTYzNjEzNzMwNjIzNjMzMzg2MjM0MzM2NDM0MzUzNDMzMzc0MDc0Njg3MjY1NjE2NDJlNzYzMjAxZThmYjY4M2Y3ODAxMDAwMDg4NjA5ODdhNzgwMTAwMDB8MTYxNjk2NDUwOTgzMg%3d%3d",
  "value": [
    {
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18c",
      "destinationType": "inPlace",
      "status": "succeeded",
      "startDateTime": "2023-12-04T12:18:55.2117521Z",
      "completionDateTime": "2023-12-04T13:22:12.7209691Z",
      "restoredFolderId": "0bdb38aa-5ad4-43ae-b63d-54426c97caa3",
      "restoredFolderName": "testmailbox101",
      "restoredItemCount": 5,
      "restorePoint": {
          "id": "ffd2687a-f507-4a82-9dff-2fa78cfdaa41_1801645000_12_2",
          "protectionDateTime": "2023-12-04T00:00:00Z",
          "expirationDateTime": "2023-12-18T00:00:00Z"
      }
    },
    {
      "id": "959ba739-70b5-43c4-8c90-b2c22014f18d",
      "destinationType": "new",
      "status": "succeeded",
      "startDateTime": "2024-02-10T12:18:55.2117521Z",
      "completionDateTime": "2024-02-10T13:22:12.7209691Z",
      "restoredFolderId": "f8bb7c43-dabd-4300-a56a-510f093bc537",
      "restoredFolderName": "testmailbox102",
      "restoredItemCount": 10,
      "restorePoint": {
          "id": "86ba0fa7-db56-4c70-bf47-62adafefc0ee_1801645000_12_2",
          "protectionDateTime": "2024-02-10T00:00:00Z",
          "expirationDateTime": "2024-02-24T00:00:00Z"
      }
    }
  ]
}
```
