<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-list-authenticationmethodmodes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List authenticationMethodModes

Namespace: microsoft.graph

Get a list of all supported authentication methods, or all supported authentication method combinations as a list of **authenticationMethodModes** objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.Read.AuthenticationMethod | Policy.Read.All, Policy.ReadWrite.AuthenticationMethod, Policy.ReadWrite.ConditionalAccess |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.Read.AuthenticationMethod | Policy.Read.All, Policy.ReadWrite.AuthenticationMethod, Policy.ReadWrite.ConditionalAccess |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Conditional Access administrator
- Security Administrator
- Security Reader

## HTTP request

Retrieve the collection of **authenticationMethodModes** objects and their descriptions.

```http
GET /identity/conditionalAccess/authenticationStrength/authenticationMethodModes
```

Retrieve the flat collection of authenticationCombinations objects, representing all the allowed combinations \(allowedCombinations\) in an authenticationStrengthPolicy object.

```http
GET /identity/conditionalAccess/authenticationStrength/combinations
```

## Optional query parameters

This method doesn't support OData query parameters.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [authenticationMethodModeDetail](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodedetail?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve authenticationMethodModes objects and their descriptions

#### Request

The following example shows a request to retrieve the collection of **authenticationMethodModes** objects and their descriptions.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/identity/conditionalAccess/authenticationStrength/authenticationMethodModes
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.AuthenticationStrength.AuthenticationMethodModes.GetAsync();
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
authenticationMethodModes, err := graphClient.Identity().ConditionalAccess().AuthenticationStrength().AuthenticationMethodModes().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationMethodModeDetailCollectionResponse result = graphClient.identity().conditionalAccess().authenticationStrength().authenticationMethodModes().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let authenticationMethodModes = await client.api('/identity/conditionalAccess/authenticationStrength/authenticationMethodModes')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identity()->conditionalAccess()->authenticationStrength()->authenticationMethodModes()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity.conditional_access.authentication_strength.authentication_method_modes.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#authenticationMethodModeDetail",
  "value": [
    {
        "id" : "password",
        "displayName" : "Password",
        "authenticationMethod" : "password"
    },
    {
        "id" : "voice",
        "displayName" : "Voice",
        "authenticationMethod" : "voice"
    },
    {
        "id" : "softwareOath",
        "displayName" : "Software OATH tokens",
        "authenticationMethod" : "softwareOath"
    },
    {
        "id" : "sms",
        "displayName" : "SMS",
        "authenticationMethod" : "sms"
    },
    {
        "id" : "fido2",
        "displayName" : "FIDO2 Security Key",
        "authenticationMethod" : "fido2"
    },
    {
        "id" : "windowsHelloForBusiness",
        "displayName" : "Windows Hello for Business",
        "authenticationMethod" : "windowsHelloForBusiness"
    },
    {
        "id" : "microsoftAuthenticatorPush",
        "displayName" : "Microsoft Authenticator (push notification)",
        "authenticationMethod" : "microsoftAuthenticator"
    },
    {
        "id" : "deviceBasedPush",
        "displayName" : "Microsoft Authenticator (Passwordless)",
        "authenticationMethod" : "microsoftAuthenticator"
    },
    {
        "id" : "temporaryAccessPassOneTime",
        "displayName" : "Temporary Access Pass (one-time use)",
        "authenticationMethod" : "temporaryAccessPass"
    },
    {
        "id" : "temporaryAccessPassMultiUse",
        "displayName" : "Temporary Access Pass (multi-use)",
        "authenticationMethod" : "temporaryAccessPass"
    },
    {
        "id" : "email",
        "displayName" : "Email one-time passcode",
        "authenticationMethod" : "email"
    },
    {
        "id" : "x509CertificateSingleFactor",
        "displayName" : "Certificate-based authentication (single factor)",
        "authenticationMethod" : "x509Certificate"
    },
    {
        "id" : "federatedMultiFactor",
        "displayName" : "Federation (multifactor)",
        "authenticationMethod" : "federation"
    },
    {
        "id" : "federatedSingleFactor",
        "displayName" : "Federation (single factor)",
        "authenticationMethod" : "federation"
    },
    {
        "id": "x509CertificateMultiFactor",
        "displayName" : "Certificate-based authentication (multifactor)",
        "authenticationMethod" : "x509Certificate"
    }
  ]
}
```

### Example 2: Retrieve the allowed authentication combinations

#### Request

The following example shows a request to retrieve the flat collection of authenticationCombinations objects, representing all the possible allowed combinations \(allowedCombinations\) that may be used in an authenticationStrengthPolicy object.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/identity/conditionalAccess/authenticationStrength/combinations
```

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let combinations = await client.api('/identity/conditionalAccess/authenticationStrength/combinations')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/conditionalAccess/authenticationStrength/combinations",
    "value": [
        "windowsHelloForBusiness",
        "fido2",
        "x509CertificateMultiFactor",
        "deviceBasedPush",
        "temporaryAccessPassOneTime",
        "temporaryAccessPassMultiUse",
        "password,microsoftAuthenticatorPush",
        "password,softwareOath",
        "password,hardwareOath",
        "password,sms",
        "password,voice",
        "federatedMultiFactor",
        "microsoftAuthenticatorPush,federatedSingleFactor",
        "softwareOath,federatedSingleFactor",
        "hardwareOath,federatedSingleFactor",
        "sms,federatedSingleFactor",
        "voice,federatedSingleFactor",
        "x509CertificateSingleFactor",
        "sms",
        "password",
        "federatedSingleFactor",
        "email"
    ]
}
```
