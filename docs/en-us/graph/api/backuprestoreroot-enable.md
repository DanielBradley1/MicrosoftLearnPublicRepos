<!-- Source: https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-enable?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# backupRestoreRoot: enable

Namespace: microsoft.graph

Enable the [Microsoft 365 Backup Storage](https://learn.microsoft.com/en-us/graph/api/resources/backuprestoreroot?view=graph-rest-1.0) service for a tenant.

Note

These APIs are intended for use by registered Backup Controller applications. If this API is called via Microsoft Graph PowerShell, it returns a `403 Forbidden` response code because the Microsoft Graph PowerShell SDK isn't a supported client for these operations.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Control.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Control.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/enable
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the following parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| appOwnerTenantId | String | The ID of the owning tenant. The owning tenant contains the billing profile. |

## Response

If successful, this action returns a `200 OK` response code and a [serviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/servicestatus?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/enable

{
    "appOwnerTenantId": "23014d8c-71fe-4d00-a01a-31850bc5b42a"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Solutions.BackupRestore.Enable;

var requestBody = new EnablePostRequestBody
{
	AppOwnerTenantId = "23014d8c-71fe-4d00-a01a-31850bc5b42a",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.Enable.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsolutions "github.com/microsoftgraph/msgraph-sdk-go/solutions"
	  //other-imports
)

requestBody := graphsolutions.NewEnablePostRequestBody()
appOwnerTenantId := "23014d8c-71fe-4d00-a01a-31850bc5b42a"
requestBody.SetAppOwnerTenantId(&appOwnerTenantId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
enable, err := graphClient.Solutions().BackupRestore().Enable().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.solutions.backuprestore.enable.EnablePostRequestBody enablePostRequestBody = new com.microsoft.graph.solutions.backuprestore.enable.EnablePostRequestBody();
enablePostRequestBody.setAppOwnerTenantId("23014d8c-71fe-4d00-a01a-31850bc5b42a");
var result = graphClient.solutions().backupRestore().enable().post(enablePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const serviceStatus = {
    appOwnerTenantId: '23014d8c-71fe-4d00-a01a-31850bc5b42a'
};

await client.api('/solutions/backupRestore/enable')
	.post(serviceStatus);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Solutions\BackupRestore\Enable\EnablePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EnablePostRequestBody();
$requestBody->setAppOwnerTenantId('23014d8c-71fe-4d00-a01a-31850bc5b42a');

$result = $graphServiceClient->solutions()->backupRestore()->enable()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	appOwnerTenantId = "23014d8c-71fe-4d00-a01a-31850bc5b42a"
}

Enable-MgSolutionBackupRestore -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.solutions.backuprestore.enable.enable_post_request_body import EnablePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EnablePostRequestBody(
	app_owner_tenant_id = "23014d8c-71fe-4d00-a01a-31850bc5b42a",
)

result = await graph_client.solutions.backup_restore.enable.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
    "@odata.type": "#microsoft.graph.serviceStatus",
    "id":"b3177c20-8d60-4a41-8a6f-1715ac41297f",
    "status":"enabled",
    "serviceConsumer":"thirdParty",
    "lastModifiedBy":{
        "application":{
            "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
        },
        "user":{
            "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
        }
    },
    "lastModifiedDateTime":"2023-06-19T12:01:03.45Z"
}
```
