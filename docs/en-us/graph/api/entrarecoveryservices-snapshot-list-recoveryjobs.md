<!-- Source: https://learn.microsoft.com/en-us/graph/api/entrarecoveryservices-snapshot-list-recoveryjobs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# List recoveryJobs

Namespace: microsoft.graph.entraRecoveryServices

Get a list of [recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) objects for a specific snapshot.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Entra Backup Reader
- Entra Backup Administrator

## HTTP request

```http
GET /directory/recovery/snapshots/{snapshot-id}/recoveryJobs
```

## Optional query parameters

This method supports the `$select`, `$top`, `$filter`, and `$orderby` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters). The default and maximum page sizes are 100 and 999 recovery job objects respectively.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.entraRecoveryServices.recoveryJob](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-recoveryjob?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.Recovery.Snapshots["{snapshot-id}"].RecoveryJobs.GetAsync();
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
recoveryJobs, err := graphClient.Directory().Recovery().Snapshots().BySnapshotId("snapshot-id").RecoveryJobs().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.entrarecoveryservices.RecoveryJobCollectionResponse result = graphClient.directory().recovery().snapshots().bySnapshotId("{snapshot-id}").recoveryJobs().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let recoveryJobs = await client.api('/directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->directory()->recovery()->snapshots()->bySnapshotId('snapshot-id')->recoveryJobs()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Get-MgDirectoryRecoverySnapshotRecoveryJob -SnapshotId $snapshotId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.directory.recovery.snapshots.by_snapshot_id('snapshot-id').recovery_jobs.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directory/recovery/snapshots/MjAyNC0wOC0yNlQwMjozMDowMFo=/recoveryJobs",
  "value":
  [
    {
      "id": "d3f8e7e8-7e87-4a7f-9d2c-c1c2d7e8e1f1",
      "status": "successful",
      "targetStateDateTime": "2024-08-26T02:30:00Z" ,
      "jobStartDateTime":  "2024-08-26T08:30:00Z",
      "jobCompletionDateTime": "2024-08-26T13:30:00Z",
      "totalObjectsModified": 1024,
      "totalLinksModified": 124,
      "totalFailedChanges": 0,
      "totalChangedObjectsCalculated" : 1024,
      "totalChangedLinksCalculated" : 124,
      "filteringCriteria": null
    },
    {
      "id": "a1b2c3d4-5e6f-7a8b-9c0d-e1f2a3b4c5d6",
      "status": "successful",
      "targetStateDateTime": "2025-08-26T02:30:00Z" ,
      "jobStartDateTime":  "2025-08-26T08:30:00Z",
      "jobCompletionDateTime": "2025-08-26T13:30:00Z",
      "totalObjectsModified": 2048,
      "totalLinksModified": 256,
      "totalFailedChanges": 0,
      "totalChangedObjectsCalculated" : 2304,
      "totalChangedLinksCalculated" : 2304,
      "filteringCriteria": null
    }
  ]
}
```
