<!-- Source: https://learn.microsoft.com/en-us/graph/api/signin-confirmcompromised?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# signIn: confirmCompromised

Namespace: microsoft.graph

Mark an event in the Microsoft Entra [sign-in](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-1.0) logs as risky. Events marked as risky by an admin are immediately flagged as high risk in Microsoft Entra ID Protection, overriding previous risk states. Admins can confirm that events flagged as risky by Microsoft Entra ID Protection are in fact risky.

For details about investigating Identity Protection risks, see [How to investigate risk](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityRiskyUser.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityRiskEvent.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /auditLogs/signIns/confirmCompromised
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| requestIds | String collection | The IDs of the sign-in events that should be marked risky for Microsoft Entra ID Protection. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/auditLogs/signIns/confirmCompromised
Content-Type: application/json

{
  "requestIds": [
    "29f270bb-4d23-4f68-8a57-dc73dc0d4caf",
    "20f91ec9-d140-4d90-9cd9-f618587a1471"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.AuditLogs.SignIns.ConfirmCompromised;

var requestBody = new ConfirmCompromisedPostRequestBody
{
	RequestIds = new List<string>
	{
		"29f270bb-4d23-4f68-8a57-dc73dc0d4caf",
		"20f91ec9-d140-4d90-9cd9-f618587a1471",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.AuditLogs.SignIns.ConfirmCompromised.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphauditlogs "github.com/microsoftgraph/msgraph-sdk-go/auditlogs"
	  //other-imports
)

requestBody := graphauditlogs.NewConfirmCompromisedPostRequestBody()
requestIds := []string {
	"29f270bb-4d23-4f68-8a57-dc73dc0d4caf",
	"20f91ec9-d140-4d90-9cd9-f618587a1471",
}
requestBody.SetRequestIds(requestIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.AuditLogs().SignIns().ConfirmCompromised().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.auditlogs.signins.confirmcompromised.ConfirmCompromisedPostRequestBody confirmCompromisedPostRequestBody = new com.microsoft.graph.auditlogs.signins.confirmcompromised.ConfirmCompromisedPostRequestBody();
LinkedList<String> requestIds = new LinkedList<String>();
requestIds.add("29f270bb-4d23-4f68-8a57-dc73dc0d4caf");
requestIds.add("20f91ec9-d140-4d90-9cd9-f618587a1471");
confirmCompromisedPostRequestBody.setRequestIds(requestIds);
graphClient.auditLogs().signIns().confirmCompromised().post(confirmCompromisedPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const confirmCompromised = {
  requestIds: [
    '29f270bb-4d23-4f68-8a57-dc73dc0d4caf',
    '20f91ec9-d140-4d90-9cd9-f618587a1471'
  ]
};

await client.api('/auditLogs/signIns/confirmCompromised')
	.post(confirmCompromised);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\AuditLogs\SignIns\ConfirmCompromised\ConfirmCompromisedPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConfirmCompromisedPostRequestBody();
$requestBody->setRequestIds(['29f270bb-4d23-4f68-8a57-dc73dc0d4caf', '20f91ec9-d140-4d90-9cd9-f618587a1471', 	]);

$graphServiceClient->auditLogs()->signIns()->confirmCompromised()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Reports

$params = @{
	requestIds = @(
	"29f270bb-4d23-4f68-8a57-dc73dc0d4caf"
"20f91ec9-d140-4d90-9cd9-f618587a1471"
)
}

Confirm-MgAuditLogSignInCompromised -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.auditlogs.signins.confirm_compromised.confirm_compromised_post_request_body import ConfirmCompromisedPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConfirmCompromisedPostRequestBody(
	request_ids = [
		"29f270bb-4d23-4f68-8a57-dc73dc0d4caf",
		"20f91ec9-d140-4d90-9cd9-f618587a1471",
	],
)

await graph_client.audit_logs.sign_ins.confirm_compromised.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
