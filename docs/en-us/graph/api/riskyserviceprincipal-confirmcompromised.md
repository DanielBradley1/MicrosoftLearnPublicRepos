<!-- Source: https://learn.microsoft.com/en-us/graph/api/riskyserviceprincipal-confirmcompromised?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# riskyServicePrincipal: confirmCompromised

Namespace: microsoft.graph

Confirm one or more [riskyServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/riskyserviceprincipal?view=graph-rest-1.0) objects as compromised. This action sets the targeted service principal account's risk level to `high`.

> **Note:** Using the riskyServicePrincipal API requires a Microsoft Entra Workload ID Premium license.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityRiskyServicePrincipal.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityRiskyServicePrincipal.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identityProtection/riskyServicePrincipals/confirmCompromised
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, specify the collection of ids of the risky service principals in a **servicePrincipalIds** property.

## Response

If successful, this action returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

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
POST https://graph.microsoft.com/v1.0/identityProtection/riskyServicePrincipals/confirmCompromised
Content-Type: application/json

{
  "servicePrincipalIds": [
    "9089a539-a539-9089-39a5-899039a58990"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityProtection.RiskyServicePrincipals.ConfirmCompromised;

var requestBody = new ConfirmCompromisedPostRequestBody
{
	ServicePrincipalIds = new List<string>
	{
		"9089a539-a539-9089-39a5-899039a58990",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityProtection.RiskyServicePrincipals.ConfirmCompromised.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentityprotection "github.com/microsoftgraph/msgraph-sdk-go/identityprotection"
	  //other-imports
)

requestBody := graphidentityprotection.NewConfirmCompromisedPostRequestBody()
servicePrincipalIds := []string {
	"9089a539-a539-9089-39a5-899039a58990",
}
requestBody.SetServicePrincipalIds(servicePrincipalIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityProtection().RiskyServicePrincipals().ConfirmCompromised().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identityprotection.riskyserviceprincipals.confirmcompromised.ConfirmCompromisedPostRequestBody confirmCompromisedPostRequestBody = new com.microsoft.graph.identityprotection.riskyserviceprincipals.confirmcompromised.ConfirmCompromisedPostRequestBody();
LinkedList<String> servicePrincipalIds = new LinkedList<String>();
servicePrincipalIds.add("9089a539-a539-9089-39a5-899039a58990");
confirmCompromisedPostRequestBody.setServicePrincipalIds(servicePrincipalIds);
graphClient.identityProtection().riskyServicePrincipals().confirmCompromised().post(confirmCompromisedPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const confirmCompromised = {
  servicePrincipalIds: [
    '9089a539-a539-9089-39a5-899039a58990'
  ]
};

await client.api('/identityProtection/riskyServicePrincipals/confirmCompromised')
	.post(confirmCompromised);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityProtection\RiskyServicePrincipals\ConfirmCompromised\ConfirmCompromisedPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConfirmCompromisedPostRequestBody();
$requestBody->setServicePrincipalIds(['9089a539-a539-9089-39a5-899039a58990', 	]);

$graphServiceClient->identityProtection()->riskyServicePrincipals()->confirmCompromised()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	servicePrincipalIds = @(
	"9089a539-a539-9089-39a5-899039a58990"
)
}

Confirm-MgRiskyServicePrincipalCompromised -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identityprotection.riskyserviceprincipals.confirm_compromised.confirm_compromised_post_request_body import ConfirmCompromisedPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConfirmCompromisedPostRequestBody(
	service_principal_ids = [
		"9089a539-a539-9089-39a5-899039a58990",
	],
)

await graph_client.identity_protection.risky_service_principals.confirm_compromised.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
