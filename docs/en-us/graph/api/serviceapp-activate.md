<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceapp-activate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# serviceApp: activate

Namespace: microsoft.graph

Activate a [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0).

Note

This API is intended for use by registered backup controller applications. If it's called via Microsoft Graph PowerShell, it returns a `403 Forbidden` response code because the Microsoft Graph PowerShell SDK isn't a supported client for this operation.

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
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /solutions/backupRestore/serviceApps/{serviceAppId}/activate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

You can specify the following properties you activate a **serviceApp**.

| Property | Type | Description |
| :--- | :--- | :--- |
| effectiveDateTime | DateTimeOffset | The date time to activate the serviceApp. Required. |

## Response

If successful, this action returns a `202 Accepted` response code and a [serviceApp](https://learn.microsoft.com/en-us/graph/api/resources/serviceapp?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/serviceApps/{71633878-8321-4950-bfaf-ed285bdd1461}/activate
Authorization: Bearer <Access-Token>

{
    "effectiveDateTime": "2024-04-19T12:01:03.45Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Solutions.BackupRestore.ServiceApps.Item.Activate;

var requestBody = new ActivatePostRequestBody
{
	EffectiveDateTime = DateTimeOffset.Parse("2024-04-19T12:01:03.45Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BackupRestore.ServiceApps["{serviceApp-id}"].Activate.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Authorization", "Bearer <Access-Token>");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsolutions "github.com/microsoftgraph/msgraph-sdk-go/solutions"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Authorization", "Bearer <Access-Token>")

configuration := &graphsolutions.BackupRestoreServiceAppsItemActivateRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphsolutions.NewActivatePostRequestBody()
effectiveDateTime , err := time.Parse(time.RFC3339, "2024-04-19T12:01:03.45Z")
requestBody.SetEffectiveDateTime(&effectiveDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
activate, err := graphClient.Solutions().BackupRestore().ServiceApps().ByServiceAppId("serviceApp-id").Activate().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.solutions.backuprestore.serviceapps.item.activate.ActivatePostRequestBody activatePostRequestBody = new com.microsoft.graph.solutions.backuprestore.serviceapps.item.activate.ActivatePostRequestBody();
OffsetDateTime effectiveDateTime = OffsetDateTime.parse("2024-04-19T12:01:03.45Z");
activatePostRequestBody.setEffectiveDateTime(effectiveDateTime);
var result = graphClient.solutions().backupRestore().serviceApps().byServiceAppId("{serviceApp-id}").activate().post(activatePostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("Authorization", "Bearer <Access-Token>");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const serviceApp = {
    effectiveDateTime: '2024-04-19T12:01:03.45Z'
};

await client.api('/solutions/backupRestore/serviceApps/{71633878-8321-4950-bfaf-ed285bdd1461}/activate')
	.post(serviceApp);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Solutions\BackupRestore\ServiceApps\Item\Activate\ActivateRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Solutions\BackupRestore\ServiceApps\Item\Activate\ActivatePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ActivatePostRequestBody();
$requestBody->setEffectiveDateTime(new \DateTime('2024-04-19T12:01:03.45Z'));
$requestConfiguration = new ActivateRequestBuilderPostRequestConfiguration();
$headers = [
		'Authorization' => 'Bearer <Access-Token>',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->solutions()->backupRestore()->serviceApps()->byServiceAppId('serviceApp-id')->activate()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.BackupRestore

$params = @{
	effectiveDateTime = [System.DateTime]::Parse("2024-04-19T12:01:03.45Z")
}

Initialize-MgSolutionBackupRestoreServiceApp -ServiceAppId $serviceAppId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.solutions.backup_restore.service_apps.item.activate.activate_request_builder import ActivateRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.solutions.backuprestore.serviceapps.item.activate.activate_post_request_body import ActivatePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ActivatePostRequestBody(
	effective_date_time = "2024-04-19T12:01:03.45Z",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Authorization", "Bearer <Access-Token>")


result = await graph_client.solutions.backup_restore.service_apps.by_service_app_id('serviceApp-id').activate.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Location: /solutions/backupRestore/serviceApps/71633878-8321-4950-bfaf-ed285bdd1461

{
  "@odata.type": "#microsoft.graph.serviceApp",
  "id":"71633878-8321-4950-bfaf-ed285bdd1461",
  "status" : "pendingActive",
  "registrationDateTime":"2023-06-19T12:01:03.45Z",
  "effectiveDateTime": "2024-04-19T12:01:03.45Z",   
  "lastModifiedDateTime":"2023-06-19T12:01:03.45Z",
  "lastModifiedBy":{
      "application":{
          "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
          "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
  }
}
```
