<!-- Source: https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationjob-restart?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Restart synchronizationJob

Namespace: microsoft.graph

Restart a stopped [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0), forcing it to reprocess all the objects in the directory. Optionally clears existing the synchronization state and previous errors.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Synchronization.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application.ReadWrite.OwnedBy | Synchronization.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator
- Hybrid Identity Administrator - to configure Microsoft Entra Cloud Sync

## HTTP Request

`{servicePrincipalId}` refers to the **id** of the service principal object.

```http
POST /servicePrincipals/{servicePrincipalId}/synchronization/jobs/{jobId}/restart
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| criteria | [synchronizationJobRestartCriteria](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjobrestartcriteria?view=graph-rest-1.0) | Restart criteria |

## Response

If successful, returns a `204 No Content` response. It doesn't return anything in the response body.

## Example

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
POST https://graph.microsoft.com/v1.0/servicePrincipals/{id}/synchronization/jobs/{jobId}/restart
Authorization: Bearer <token>
Content-type: application/json

{
   "criteria": {
       "resetScope": "Watermark, Escrows, QuarantineState"
   }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.ServicePrincipals.Item.Synchronization.Jobs.Item.Restart;
using Microsoft.Graph.Models;

var requestBody = new RestartPostRequestBody
{
	Criteria = new SynchronizationJobRestartCriteria
	{
		ResetScope = SynchronizationJobRestartScope.Watermark | SynchronizationJobRestartScope.Escrows | SynchronizationJobRestartScope.QuarantineState,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.ServicePrincipals["{servicePrincipal-id}"].Synchronization.Jobs["{synchronizationJob-id}"].Restart.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Authorization", "Bearer <token>");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphserviceprincipals "github.com/microsoftgraph/msgraph-sdk-go/serviceprincipals"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Authorization", "Bearer <token>")

configuration := &graphserviceprincipals.ItemSynchronizationJobsItemRestartRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphserviceprincipals.NewRestartPostRequestBody()
criteria := graphmodels.NewSynchronizationJobRestartCriteria()
resetScope := graphmodels.WATERMARK, ESCROWS, QUARANTINESTATE_SYNCHRONIZATIONJOBRESTARTSCOPE 
criteria.SetResetScope(&resetScope) 
requestBody.SetCriteria(criteria)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").Synchronization().Jobs().BySynchronizationJobId("synchronizationJob-id").Restart().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.restart.RestartPostRequestBody restartPostRequestBody = new com.microsoft.graph.serviceprincipals.item.synchronization.jobs.item.restart.RestartPostRequestBody();
SynchronizationJobRestartCriteria criteria = new SynchronizationJobRestartCriteria();
criteria.setResetScope(EnumSet.of(SynchronizationJobRestartScope.Watermark, SynchronizationJobRestartScope.Escrows, SynchronizationJobRestartScope.QuarantineState));
restartPostRequestBody.setCriteria(criteria);
graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").synchronization().jobs().bySynchronizationJobId("{synchronizationJob-id}").restart().post(restartPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("Authorization", "Bearer <token>");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const restart = {
   criteria: {
       resetScope: 'Watermark, Escrows, QuarantineState'
   }
};

await client.api('/servicePrincipals/{id}/synchronization/jobs/{jobId}/restart')
	.post(restart);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\ServicePrincipals\Item\Synchronization\Jobs\Item\Restart\RestartRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\ServicePrincipals\Item\Synchronization\Jobs\Item\Restart\RestartPostRequestBody;
use Microsoft\Graph\Generated\Models\SynchronizationJobRestartCriteria;
use Microsoft\Graph\Generated\Models\SynchronizationJobRestartScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RestartPostRequestBody();
$criteria = new SynchronizationJobRestartCriteria();
$criteria->setResetScope(new SynchronizationJobRestartScope('watermark, Escrows, QuarantineState'));
$requestBody->setCriteria($criteria);
$requestConfiguration = new RestartRequestBuilderPostRequestConfiguration();
$headers = [
		'Authorization' => 'Bearer <token>',
	];
$requestConfiguration->headers = $headers;


$graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->synchronization()->jobs()->bySynchronizationJobId('synchronizationJob-id')->restart()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	criteria = @{
		resetScope = "Watermark, Escrows, QuarantineState"
	}
}

Restart-MgServicePrincipalSynchronizationJob -ServicePrincipalId $servicePrincipalId -SynchronizationJobId $synchronizationJobId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.service_principals.item.synchronization.jobs.item.restart.restart_request_builder import RestartRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.serviceprincipals.item.synchronization.jobs.item.restart.restart_post_request_body import RestartPostRequestBody
from msgraph.generated.models.synchronization_job_restart_criteria import SynchronizationJobRestartCriteria
from msgraph.generated.models.synchronization_job_restart_scope import SynchronizationJobRestartScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RestartPostRequestBody(
	criteria = SynchronizationJobRestartCriteria(
		reset_scope = SynchronizationJobRestartScope.Watermark | SynchronizationJobRestartScope.Escrows | SynchronizationJobRestartScope.QuarantineState,
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Authorization", "Bearer <token>")


await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').synchronization.jobs.by_synchronization_job_id('synchronizationJob-id').restart.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
