<!-- Source: https://learn.microsoft.com/en-us/graph/api/driveitem-lock?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# driveItem: lock

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Acquire an exclusive lock on a file represented by a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-beta), or extend an existing lock you already hold. While the lock is held, other users are prevented from acquiring a lock on the same file. The lock automatically expires after the duration specified in the request elapses.

Note

This API applies only to **driveItems** that represent files. Locks can't be applied to folders or other non-file **driveItems**. Requests that target a non-file **driveItem** are rejected with `400 Bad Request`.

A single endpoint handles both initial acquisition and refresh. The server determines which behavior applies based on the file's current lock state and the caller's identity. The caller doesn't need to track whether they previously locked the file, and doesn't need to manage a lock identifier.

Only exclusive locks are currently supported.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Files.ReadWrite.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.ReadWrite.All | Sites.ReadWrite.All |

Note

SharePoint Embedded requires the `FileStorageContainer.Selected` permission to access the content of the container. This permission is different from the ones mentioned previously. In addition to Microsoft Graph permissions, your app must have the necessary [container type permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#container-type-application-permissions) to call this API. For more information, see [SharePoint Embedded authentication and authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth).

## HTTP request

```http
POST /drives/{drive-id}/items/{item-id}/lock
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the lock parameters.

| Property | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| durationMinutes | Int32 | Yes | Lock duration in minutes. Must be between 1 and 30 minutes. The lock expires at the request time plus this value. |

The lock identifier and lock type are server-determined and must not be provided by the caller.

## Response

The server determines whether this request acquires a new lock or refreshes an existing one based on the file's current lock state and the caller's identity:

| Current state | Caller identity | Action |
| :--- | :--- | :--- |
| File isn't locked, or the existing lock expired. | Any caller with permission. | Acquire a new lock. |
| File is locked, and the caller holds the lock. | Same caller as the lock owner. | Refresh the existing lock; **expirationDateTime** is updated. |
| File is locked by another user. | Different caller. | Return `409 Conflict`. The caller can't acquire a lock until the existing lock is released or expires. |

If successful, this method returns a `200 OK` response code and a [lockInfo](https://learn.microsoft.com/en-us/graph/api/resources/lockinfo?view=graph-rest-beta) resource in the response body.

This method returns the following error response codes.

| HTTP code | Description |
| :--- | :--- |
| 400 | Bad request. The **durationMinutes** is missing, non-positive, or exceeds the 30-minute maximum. Also returned when the target **driveItem** isn't a file \(for example, a folder\). |
| 401 | Request lacks valid authentication credentials. |
| 403 | The caller doesn't have permission to lock this file. |
| 404 | The **driveItem** wasn't found at the specified path. |
| 409 | The file is locked by another user. The caller must wait for the existing lock to be released or expire before acquiring a new lock. |

For more information about how errors are returned, see [Error responses and resource types for differences between Microsoft Graph for Microsoft accounts and Microsoft Graph for work or school accounts](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Example 1: Acquire a lock on an unlocked file

#### Request

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
POST https://graph.microsoft.com/beta/drives/{drive-id}/items/{item-id}/lock
Content-Type: application/json

{
  "durationMinutes": 30
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Drives.Item.Items.Item.Lock;

var requestBody = new LockPostRequestBody
{
	DurationMinutes = 30,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Lock.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-beta-sdk-go/drives"
	  //other-imports
)

requestBody := graphdrives.NewLockPostRequestBody()
durationMinutes := int32(30)
requestBody.SetDurationMinutes(&durationMinutes) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
lock, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Lock().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.drives.item.items.item.lock.LockPostRequestBody lockPostRequestBody = new com.microsoft.graph.beta.drives.item.items.item.lock.LockPostRequestBody();
lockPostRequestBody.setDurationMinutes(30);
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").lock().post(lockPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const lockInfo = {
  durationMinutes: 30
};

await client.api('/drives/{drive-id}/items/{item-id}/lock')
	.version('beta')
	.post(lockInfo);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Drives\Item\Items\Item\Lock\LockPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LockPostRequestBody();
$requestBody->setDurationMinutes(30);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->lock()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Files

$params = @{
	durationMinutes = 30
}

Lock-MgBetaDriveItem -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.drives.item.items.item.lock.lock_post_request_body import LockPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LockPostRequestBody(
	duration_minutes = 30,
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').lock.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "lockType": "exclusive",
  "expirationDateTime": "2026-05-13T14:30:00Z",
  "createdDateTime": "2026-05-13T14:00:00Z"
}
```

### Example 2: Refresh an existing lock the caller already holds

The request body is identical to the acquire case; only the file's current state differs.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/drives/{drive-id}/items/{item-id}/lock
Content-Type: application/json

{
  "durationMinutes": 10
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Drives.Item.Items.Item.Lock;

var requestBody = new LockPostRequestBody
{
	DurationMinutes = 10,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Lock.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphdrives "github.com/microsoftgraph/msgraph-beta-sdk-go/drives"
	  //other-imports
)

requestBody := graphdrives.NewLockPostRequestBody()
durationMinutes := int32(10)
requestBody.SetDurationMinutes(&durationMinutes) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
lock, err := graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Lock().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.drives.item.items.item.lock.LockPostRequestBody lockPostRequestBody = new com.microsoft.graph.beta.drives.item.items.item.lock.LockPostRequestBody();
lockPostRequestBody.setDurationMinutes(10);
var result = graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").lock().post(lockPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const lockInfo = {
  durationMinutes: 10
};

await client.api('/drives/{drive-id}/items/{item-id}/lock')
	.version('beta')
	.post(lockInfo);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Drives\Item\Items\Item\Lock\LockPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LockPostRequestBody();
$requestBody->setDurationMinutes(10);

$result = $graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->lock()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Files

$params = @{
	durationMinutes = 10
}

Lock-MgBetaDriveItem -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.drives.item.items.item.lock.lock_post_request_body import LockPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LockPostRequestBody(
	duration_minutes = 10,
)

result = await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').lock.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **expirationDateTime** is updated.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "lockType": "exclusive",
  "expirationDateTime": "2026-05-13T14:39:00Z",
  "createdDateTime": "2026-05-13T14:00:00Z"
}
```

## Remarks

- Only exclusive locks are currently supported. The **lockType** in the response is always `exclusive`.
- Lock duration is capped at 30 minutes per request. For longer holds, call this API again before the existing lock expires; the call is automatically handled as a refresh.
- The new **expirationDateTime** is calculated as the request time plus **durationMinutes**; it replaces the prior expiration rather than extending it. Calling with a shorter duration than the time remaining effectively reduces the lock window.
- The **createdDateTime** and **expirationDateTime** are returned in UTC.
- This API is idempotent and retry-safe: if a network failure leaves the caller uncertain whether the lock succeeded, retrying naturally results in a refresh \(if the first call succeeded\) or a fresh acquire \(if it didn't\).
