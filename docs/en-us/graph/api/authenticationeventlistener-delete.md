<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationeventlistener-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# Delete authenticationEventListener

Namespace: microsoft.graph

Delete an [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) object. The following derived types are currently supported.

- [onTokenIssuanceStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartlistener?view=graph-rest-1.0) resource type
- [onInteractiveAuthFlowStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstartlistener?view=graph-rest-1.0) resource type
- [onAuthenticationMethodLoadStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionlistener?view=graph-rest-1.0) resource type
- [onUserCreateStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitlistener?view=graph-rest-1.0) resource type
- [onEmailOtpSendListener](https://learn.microsoft.com/en-us/graph/api/resources/onemailotpsendlistener?view=graph-rest-1.0) resource type
- [onFraudProtectionLoadStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstartlistener?view=graph-rest-1.0) resource type
- [onPasswordSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitlistener?view=graph-rest-1.0) resource type
- [onVerifiedIdClaimValidationListener](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationlistener?view=graph-rest-1.0) resource type

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EventListener.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EventListener.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Extensibility Administrator
- Application Administrator

## HTTP request

```http
DELETE /identity/authenticationEventListeners/{authenticationEventListenerId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

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
DELETE https://graph.microsoft.com/v1.0/identity/authenticationEventListeners/c7a1f2c5-3d36-4b3f-b75c-143af30a5246
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Identity.AuthenticationEventListeners["{authenticationEventListener-id}"].DeleteAsync();
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
graphClient.Identity().AuthenticationEventListeners().ByAuthenticationEventListenerId("authenticationEventListener-id").Delete(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.identity().authenticationEventListeners().byAuthenticationEventListenerId("{authenticationEventListener-id}").delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identity/authenticationEventListeners/c7a1f2c5-3d36-4b3f-b75c-143af30a5246')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->identity()->authenticationEventListeners()->byAuthenticationEventListenerId('authenticationEventListener-id')->delete()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Remove-MgIdentityAuthenticationEventListener -AuthenticationEventListenerId $authenticationEventListenerId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.identity.authentication_event_listeners.by_authentication_event_listener_id('authenticationEventListener-id').delete()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
