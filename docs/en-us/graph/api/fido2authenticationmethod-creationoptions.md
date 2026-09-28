<!-- Source: https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethod-creationoptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# fido2AuthenticationMethod: creationOptions

Namespace: microsoft.graph

Retrieve [creation options](https://learn.microsoft.com/en-us/graph/api/resources/webauthncredentialcreationoptions?view=graph-rest-1.0) required to generate and register a Microsoft Entra ID-compatible passkey. This function returns WebAuthn credential creation options that include a challenge, relying party information, and user information, which are used by the client to create a new FIDO2 credential. The **challenge** property and credential IDs in **excludeCredentials** are Base64URL-encoded without padding. All binary data in the response follows Base64URL encoding as defined in [RFC 4648 Section 5](https://www.rfc-editor.org/rfc/rfc4648#section-5).

Note

This API applies a system-defined challenge timeout of 5 minutes. Unlike the beta version of this API, custom challenge timeout values are not supported in v1.0.

This API has a [known issue](https://learn.microsoft.com/en-us/graph/known-issues#fido2-provisioning-api-requires-self-service-setup-to-be-enabled) that requires **Allow self-service setup** to be enabled in the FIDO2 authentication method policy.

Self-service operations aren't currently supported.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserAuthMethod-Passkey.ReadWrite.All | UserAuthenticationMethod.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserAuthMethod-Passkey.ReadWrite.All | UserAuthenticationMethod.ReadWrite.All |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Authentication Administrator
- Privileged Authentication Administrator

## HTTP request

```http
GET /users/{id}/authentication/fido2Methods/creationOptions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [webauthnCredentialCreationOptions](https://learn.microsoft.com/en-us/graph/api/resources/webauthncredentialcreationoptions?view=graph-rest-1.0) object in the response body.

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
GET https://graph.microsoft.com/v1.0/users/99a1915f-70a7-4b67-9dca-64095b41be73/authentication/fido2Methods/creationOptions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Authentication.Fido2Methods.CreationOptions.GetAsync();
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
creationOptions, err := graphClient.Users().ByUserId("user-id").Authentication().Fido2Methods().CreationOptions().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.users().byUserId("{user-id}").authentication().fido2Methods().creationOptions().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let webauthnCredentialCreationOptions = await client.api('/users/99a1915f-70a7-4b67-9dca-64095b41be73/authentication/fido2Methods/creationOptions')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->authentication()->fido2Methods()->creationOptions()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Invoke-MgCreationUserAuthenticationFido2MethodOption -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').authentication.fido2_methods.creation_options.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.webauthnCredentialCreationOptions",
  "challengeTimeoutDateTime": "2026-04-20T10:05:00Z",
  "publicKey": {
    "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialCreationOptions",
    "rp": {
      "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialRpEntity",
      "id": "login.microsoftonline.com",
      "name": "Microsoft"
    },
    "user": {
      "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialUserEntity",
      "id": "ZGF2aWRAY29udG9zby5jb20",
      "displayName": "David Smith",
      "name": "david@contoso.com"
    },
    "challenge": "QTU1MzNDNzAtNkM3Ni00NTRDLUJDQ0YtRTREMDZCNTBFRTRE",
    "pubKeyCredParams": [
      {
        "@odata.type": "#microsoft.graph.webauthnPublicKeyCredentialParameters",
        "type": "public-key",
        "alg": -7
      }
    ],
    "timeout": 60000,
    "excludeCredentials": [],
    "authenticatorSelection": {
      "@odata.type": "#microsoft.graph.webauthnAuthenticatorSelectionCriteria",
      "authenticatorAttachment": "platform",
      "requireResidentKey": true,
      "userVerification": "required"
    },
    "attestation": "direct",
    "extensions": {
      "@odata.type": "#microsoft.graph.webauthnAuthenticationExtensionsClientInputs"
    }
  }
}
```
