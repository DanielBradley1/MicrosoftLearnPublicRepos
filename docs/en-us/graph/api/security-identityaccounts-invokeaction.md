<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-identityaccounts-invokeaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# identityAccounts: invokeAction

Namespace: microsoft.graph.security

Perform actions such as revoking accounts and forcing password reset for [identity accounts](https://learn.microsoft.com/en-us/graph/api/resources/security-identityaccounts?view=graph-rest-1.0) that are observed in Microsoft Defender for Identity. This action allows reading and performing identity security actions on behalf of the signed-in identity.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

One of the following permissions is required to call this API. Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(least privileged listed first\) |
| :--- | :--- |
| Delegated \(work or school account\) | SecurityIdentitiesActions.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | SecurityIdentitiesActions.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Security Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /security/identities/identityAccounts/{identityAccountsId}/invokeAction
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
| accountId | String | The identifier of the account to perform the action on. |
| action | microsoft.graph.security.action | The type of action to perform on the account. The possible values are: `disable`, `enable`, `forcePasswordReset`, `revokeAllSessions`, `requireUserToSignInAgain`, `markUserAsCompromised`. |
| identityProvider | microsoft.graph.security.identityProvider | The identity provider associated with the account. The possible values are: `entraID`, `activeDirectory`, `okta`. |

The following table shows the identity providers supported for each **action** value type:

| Action Value | Description | Supported identity providers |
| :--- | :--- | :--- |
| Disable | Disable account. The account is unable to authenticate. If the account recently logged in, it doesn't have access to resources. | `activeDirectory`, `okta` |
| Enable | Enable account. | `activeDirectory`, `okta` |
| ForcePasswordReset | Force password reset of the account. | `activeDirectory` |
| RevokeAllSessions | Revoke all of active sessions for the account. | `okta` |

## Response

If successful, this action returns a `200 OK` response code and a [invokeActionResult](https://learn.microsoft.com/en-us/graph/api/resources/security-invokeactionresult?view=graph-rest-1.0) in the response body.

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
POST https://graph.microsoft.com/v1.0/security/identities/identityAccounts/0104216-0539-4838-88b1-55baafdc296b/invokeAction
Content-Type: application/json

{
  "accountId": "256db173-930a-4991-9061-0d51a9a93ba5",
  "action": "disable",
  "identityProvider": "activeDirectory"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Identities.IdentityAccounts.Item.MicrosoftGraphSecurityInvokeAction;
using Microsoft.Graph.Models.Security;

var requestBody = new InvokeActionPostRequestBody
{
	AccountId = "256db173-930a-4991-9061-0d51a9a93ba5",
	Action = ActionObject.Disable,
	IdentityProvider = IdentityProvider.ActiveDirectory,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Identities.IdentityAccounts["{identityAccounts-id}"].MicrosoftGraphSecurityInvokeAction.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewInvokeActionPostRequestBody()
accountId := "256db173-930a-4991-9061-0d51a9a93ba5"
requestBody.SetAccountId(&accountId) 
action := graphmodels.DISABLE_ACTION 
requestBody.SetAction(&action) 
identityProvider := graphmodels.ACTIVEDIRECTORY_IDENTITYPROVIDER 
requestBody.SetIdentityProvider(&identityProvider) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphSecurityInvokeAction, err := graphClient.Security().Identities().IdentityAccounts().ByIdentityAccountsId("identityAccounts-id").MicrosoftGraphSecurityInvokeAction().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.identities.identityaccounts.item.microsoftgraphsecurityinvokeaction.InvokeActionPostRequestBody invokeActionPostRequestBody = new com.microsoft.graph.security.identities.identityaccounts.item.microsoftgraphsecurityinvokeaction.InvokeActionPostRequestBody();
invokeActionPostRequestBody.setAccountId("256db173-930a-4991-9061-0d51a9a93ba5");
invokeActionPostRequestBody.setAction(com.microsoft.graph.models.security.Action.Disable);
invokeActionPostRequestBody.setIdentityProvider(com.microsoft.graph.models.security.IdentityProvider.ActiveDirectory);
var result = graphClient.security().identities().identityAccounts().byIdentityAccountsId("{identityAccounts-id}").microsoftGraphSecurityInvokeAction().post(invokeActionPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const invokeActionResult = {
  accountId: '256db173-930a-4991-9061-0d51a9a93ba5',
  action: 'disable',
  identityProvider: 'activeDirectory'
};

await client.api('/security/identities/identityAccounts/0104216-0539-4838-88b1-55baafdc296b/invokeAction')
	.post(invokeActionResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Identities\IdentityAccounts\Item\MicrosoftGraphSecurityInvokeAction\InvokeActionPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\Action;
use Microsoft\Graph\Generated\Models\Security\IdentityProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new InvokeActionPostRequestBody();
$requestBody->setAccountId('256db173-930a-4991-9061-0d51a9a93ba5');
$requestBody->setAction(new Action('disable'));
$requestBody->setIdentityProvider(new IdentityProvider('activeDirectory'));

$result = $graphServiceClient->security()->identities()->identityAccounts()->byIdentityAccountsId('identityAccounts-id')->microsoftGraphSecurityInvokeAction()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	accountId = "256db173-930a-4991-9061-0d51a9a93ba5"
	action = "disable"
	identityProvider = "activeDirectory"
}

Invoke-MgInvokeSecurityIdentityAccountAction -IdentityAccountsId $identityAccountsId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.identities.identityaccounts.item.microsoft_graph_security_invoke_action.invoke_action_post_request_body import InvokeActionPostRequestBody
from msgraph.generated.models.action import Action
from msgraph.generated.models.identity_provider import IdentityProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = InvokeActionPostRequestBody(
	account_id = "256db173-930a-4991-9061-0d51a9a93ba5",
	action = Action.Disable,
	identity_provider = IdentityProvider.ActiveDirectory,
)

result = await graph_client.security.identities.identity_accounts.by_identity_accounts_id('identityAccounts-id').microsoft_graph_security_invoke_action.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": 
    {
      "accountId": "256db173-930a-4991-9061-0d51a9a93ba5",
      "action": "disable",
      "provider": "activeDirectory",
      "correlationId": "ed2f052b-2a01-4cd9-acb3-f6145f83e1a5"
    }
}
```

Note

Actions related to Entra ID are not covered in the current scope.
