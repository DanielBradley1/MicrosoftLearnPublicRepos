<!-- Source: https://learn.microsoft.com/en-us/graph/api/exchangerestoresession-list-mailboxrestoreartifactsbulkadditionrequests?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List mailboxRestoreArtifactsBulkAdditionRequests

Namespace: microsoft.graph

Get a list of the [maiboxRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifactsbulkadditionrequest?view=graph-rest-1.0) objects associated with an [exchangeRestoreSession](https://learn.microsoft.com/en-us/graph/api/resources/exchangerestoresession?view=graph-rest-1.0). The **mailboxes** property is deliberately omitted from the response body in order to limit the response size.

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
GET /solutions/backupRestore/exchangeRestoreSessions/{exchangeRestoreSessionId}/mailboxRestoreArtifactsBulkAdditionRequests
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

If successful, this method returns a `200 OK` response code and a collection of [mailboxRestoreArtifactsBulkAdditionRequest](https://learn.microsoft.com/en-us/graph/api/resources/mailboxrestoreartifactsbulkadditionrequest?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeRestoreSessions/dc3a3fc8-eb4b-45eb-9ca6-4955696344b8/mailboxRestoreArtifactsBulkAdditionRequests
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ExchangeRestoreSessions["{exchangeRestoreSession-id}"].MailboxRestoreArtifactsBulkAdditionRequests.GetAsync();
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
mailboxRestoreArtifactsBulkAdditionRequests, err := graphClient.Solutions().BackupRestore().ExchangeRestoreSessions().ByExchangeRestoreSessionId("exchangeRestoreSession-id").MailboxRestoreArtifactsBulkAdditionRequests().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxRestoreArtifactsBulkAdditionRequestCollectionResponse result = graphClient.solutions().backupRestore().exchangeRestoreSessions().byExchangeRestoreSessionId("{exchangeRestoreSession-id}").mailboxRestoreArtifactsBulkAdditionRequests().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let mailboxRestoreArtifactsBulkAdditionRequests = await client.api('/solutions/backupRestore/exchangeRestoreSessions/dc3a3fc8-eb4b-45eb-9ca6-4955696344b8/mailboxRestoreArtifactsBulkAdditionRequests')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->backupRestore()->exchangeRestoreSessions()->byExchangeRestoreSessionId('exchangeRestoreSession-id')->mailboxRestoreArtifactsBulkAdditionRequests()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

Get-MgSolutionBackupRestoreExchangeRestoreSessionMailboxRestoreArtifactBulkAdditionRequest -ExchangeRestoreSessionId $exchangeRestoreSessionId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.backup_restore.exchange_restore_sessions.by_exchange_restore_session_id('exchangeRestoreSession-id').mailbox_restore_artifacts_bulk_addition_requests.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.mailboxRestoreArtifactsBulkAdditionRequest",
  "value": [
    {
      "id": "b4318e3a-3eae-4ce5-87f3-bad51e1527c4",
      "destinationType": "new",
      "tags": "fastRestore",
      "restorePointPreference": "latest",
      "displayName": "EXO-BulkRestoreArtifacts",
      "status": "active",
      "createdDateTime": "2024-12-03T13:17:19.8862272Z",
      "lastModifiedDateTime": "2024-12-03T13:17:19.8862272Z",
      "mailboxes": [],
      "protectionTimePeriod": {
        "startDateTime": "2024-11-26T00:00:00Z",
        "endDateTime": "2024-12-03T00:00:00Z"
      },
      "createdBy": {
        "user": {
          "identity": "fb70be35-8c8e-4c8a-b55d-f8cd95c5e23a"
        }
      },
      "lastModifiedBy": {
        "user": {
          "identity": "fb70be35-8c8e-4c8a-b55d-f8cd95c5e23a"
        }
      }
    }
  ]
}
```
