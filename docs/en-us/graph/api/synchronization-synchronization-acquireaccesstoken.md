<!-- Source: https://learn.microsoft.com/en-us/graph/api/synchronization-synchronization-acquireaccesstoken?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronization: acquireAccessToken

Namespace: microsoft.graph

Acquire an OAuth access token from the [synchronization](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronization?view=graph-rest-1.0) resource to authorize the Microsoft Entra provisioning service to provision users into an application.

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

## HTTP request

```http
POST /applications/{applicationsId}/synchronization/acquireAccessToken
POST /servicePrincipals/{servicePrincipalsId}/synchronization/acquireAccessToken
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| credentials | [synchronizationSecretKeyStringValuePair](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationsecretkeystringvaluepair?view=graph-rest-1.0) collection | Represents a single secret value. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/applications/{applicationsId}/synchronization/acquireAccessToken
Content-Type: application/json

{
  "credentials": [
    {
      "@odata.type": "microsoft.graph.synchronizationSecretKeyStringValuePair"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Applications.Item.Synchronization.AcquireAccessToken;
using Microsoft.Graph.Models;

var requestBody = new AcquireAccessTokenPostRequestBody
{
	Credentials = new List<SynchronizationSecretKeyStringValuePair>
	{
		new SynchronizationSecretKeyStringValuePair
		{
			OdataType = "microsoft.graph.synchronizationSecretKeyStringValuePair",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Applications["{application-id}"].Synchronization.AcquireAccessToken.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphapplications "github.com/microsoftgraph/msgraph-sdk-go/applications"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphapplications.NewAcquireAccessTokenPostRequestBody()


synchronizationSecretKeyStringValuePair := graphmodels.NewSynchronizationSecretKeyStringValuePair()

credentials := []graphmodels.SynchronizationSecretKeyStringValuePairable {
	synchronizationSecretKeyStringValuePair,
}
requestBody.SetCredentials(credentials)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Applications().ByApplicationId("application-id").Synchronization().AcquireAccessToken().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.applications.item.synchronization.acquireaccesstoken.AcquireAccessTokenPostRequestBody acquireAccessTokenPostRequestBody = new com.microsoft.graph.applications.item.synchronization.acquireaccesstoken.AcquireAccessTokenPostRequestBody();
LinkedList<SynchronizationSecretKeyStringValuePair> credentials = new LinkedList<SynchronizationSecretKeyStringValuePair>();
SynchronizationSecretKeyStringValuePair synchronizationSecretKeyStringValuePair = new SynchronizationSecretKeyStringValuePair();
synchronizationSecretKeyStringValuePair.setOdataType("microsoft.graph.synchronizationSecretKeyStringValuePair");
credentials.add(synchronizationSecretKeyStringValuePair);
acquireAccessTokenPostRequestBody.setCredentials(credentials);
graphClient.applications().byApplicationId("{application-id}").synchronization().acquireAccessToken().post(acquireAccessTokenPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const acquireAccessToken = {
  credentials: [
    {
      '@odata.type': 'microsoft.graph.synchronizationSecretKeyStringValuePair'
    }
  ]
};

await client.api('/applications/{applicationsId}/synchronization/acquireAccessToken')
	.post(acquireAccessToken);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Applications\Item\Synchronization\AcquireAccessToken\AcquireAccessTokenPostRequestBody;
use Microsoft\Graph\Generated\Models\SynchronizationSecretKeyStringValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AcquireAccessTokenPostRequestBody();
$credentialsSynchronizationSecretKeyStringValuePair1 = new SynchronizationSecretKeyStringValuePair();
$credentialsSynchronizationSecretKeyStringValuePair1->setOdataType('microsoft.graph.synchronizationSecretKeyStringValuePair');
$credentialsArray []= $credentialsSynchronizationSecretKeyStringValuePair1;
$requestBody->setCredentials($credentialsArray);


$graphServiceClient->applications()->byApplicationId('application-id')->synchronization()->acquireAccessToken()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	credentials = @(
		@{
			"@odata.type" = "microsoft.graph.synchronizationSecretKeyStringValuePair"
		}
	)
}

Get-MgApplicationSynchronizationAccessToken -ApplicationId $applicationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.applications.item.synchronization.acquire_access_token.acquire_access_token_post_request_body import AcquireAccessTokenPostRequestBody
from msgraph.generated.models.synchronization_secret_key_string_value_pair import SynchronizationSecretKeyStringValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AcquireAccessTokenPostRequestBody(
	credentials = [
		SynchronizationSecretKeyStringValuePair(
			odata_type = "microsoft.graph.synchronizationSecretKeyStringValuePair",
		),
	],
)

await graph_client.applications.by_application_id('application-id').synchronization.acquire_access_token.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
