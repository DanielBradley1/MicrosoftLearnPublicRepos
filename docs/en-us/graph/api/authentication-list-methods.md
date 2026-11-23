<!-- Source: https://learn.microsoft.com/en-us/graph/api/authentication-list-methods?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List methods

Namespace: microsoft.graph

Retrieve a list of authentication methods registered to a user. The authentication methods are defined by the types derived from the [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) resource type, and only the methods supported on this API version. See [Microsoft Entra authentication methods API overview](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview?view=graph-rest-1.0) for a list of currently supported methods.

We don't recommend using the authentication methods APIs for scenarios where you need to iterate over your entire user population for auditing or security check purposes. For these types of scenarios, we recommend using the [authentication method registration and usage reporting APIs](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-usage-insights-overview).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Permissions acting on self

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthenticationMethod.Read | UserAuthenticationMethod.Read.All, UserAuthenticationMethod.ReadWrite, UserAuthenticationMethod.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

### Permissions acting on other users

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthenticationMethod.Read.All | UserAuthenticationMethod.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthenticationMethod.Read.All | UserAuthenticationMethod.ReadWrite.All |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Authentication Administrator
- Privileged Authentication Administrator

Note

The authentication administrator only sees masked phone numbers.

## HTTP request

List your own authentication methods.

```http
GET /me/authentication/methods
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

List your own or another user's authentication methods.

```http
GET /users/{id | userPrincipalName}/authentication/methods
```

## Optional query parameters

This method doesn't support optional query parameters to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [authenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethod?view=graph-rest-1.0) objects in the response body.

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

```
GET https://graph.microsoft.com/v1.0/me/authentication/methods
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Authentication.Methods.GetAsync();
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
methods, err := graphClient.Me().Authentication().Methods().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationMethodCollectionResponse result = graphClient.me().authentication().methods().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let methods = await client.api('/me/authentication/methods')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->authentication()->methods()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

# A UPN can also be used as -UserId.
Get-MgUserAuthenticationMethod -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.authentication.methods.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.fido2AuthenticationMethod",
      "id": "-2_GRUg2-HYz6_1YG4YRAQ2",
      "displayName": "Red key",
      "creationDateTime": "2020-08-10T06:44:09Z",
      "aaGuid": "2fc0579f-8113-47ea-b116-555a8db9202a",
      "model": "NFC key",
      "attestationCertificates": [
          "dbe793efdf1945e2df25d93653a1e8a3268a9075"
      ],
      "attestationLevel": "attested"
    },
    {
    "@odata.type": "#microsoft.graph.windowsHelloForBusinessAuthenticationMethod",
    "id": "b5e01f81-1f81-b5e0-811f-e0b5811fe0b5",
    "displayName": "Jordan's Surface Book",
    "createdDateTime": "2020-11-27T23:12:49Z",
    "keyStrength": "normal"
    }
  ]
}
```
