<!-- Source: https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-validateauthenticationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-05 -->

# customAuthenticationExtension: validateAuthenticationConfiguration

Namespace: microsoft.graph

An API to check validity of the endpoint and and authentication configuration for a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) object, which can represent one of the following derived types:

- [onTokenIssuanceStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitcustomextension?view=graph-rest-1.0) resource type.
- [onOtpSendCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextension?view=graph-rest-1.0) resource type.
- [onVerifiedIdClaimValidationCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationcustomextension?view=graph-rest-1.0) resource type.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CustomAuthenticationExtension.Read.All | CustomAuthenticationExtension.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CustomAuthenticationExtension.Read.All | CustomAuthenticationExtension.ReadWrite.All |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Extensibility Administrator
- Application Administrator

## HTTP request

To validate the endpoint and authentication configuration for a customAuthenticationExtension by its ID.

```http
POST /identity/customAuthenticationExtensions/{customAuthenticationExtensionId}/validateAuthenticationConfiguration
```

To validate the endpoint and authentication configuration that's specified in the request body for a customAuthenticationExtension. The custom authentication extension object may not exist yet and you can use this endpoint to validate the configuration before creating the custom authentication extension.

```http
POST /identity/customAuthenticationExtensions/validateAuthenticationConfiguration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

Supply a **endpointConfiguration** and **authenticationConfiguration** if querying at the root level. Otherwise, for a specific custom extension, don't supply a request body for this method.

| Property | Type | Description |
| :--- | :--- | :--- |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The HTTP endpoint for the custom authentication extension to be validated. |
| authenticationConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The authentication configuration for the custom authenticaion extension to validate. |

## Response

If successful, this action returns a `200 OK` response code and a [authenticationConfigurationValidation](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconfigurationvalidation?view=graph-rest-1.0) in the response body.

## Examples

### Example 1: Supply and validate a potential custom authentication extension configuration

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/customAuthenticationExtensions/validateAuthenticationConfiguration
Content-Type: application/json

{
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://australia.contoso.com/users"
    },
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://extensibilityapi.azurwebsites.net/f9c5dc6b-d72b-4226-8ccd-801f7a290428"
    }
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.authenticationConfigurationValidation", 
    "errors": [
        {
            "code": "IncorrectResourceIdFormat",
            "message": "ResourceId should be in the format of 'api://{fully qualified domain name}/{appid}'"
        },
        {
            "code": "DomainNameDoesNotMatch",
            "message": "The fully qualified domain name in resourceId should match that of the targetUrl"
        },
        {
            "code": "ServicePrincipalNotFound",
            "message": "The appId of the resourceId should correspond to a real service principal in the tenant"
        }
    ],
    "warnings": [
        {
            "code": "PermissionNotGrantedToServicePrincipal",
            "message": "The permission CustomAuthenticationExtensions.Receive.Payload is not granted to the service principal of the resource app"
        },
    ]
}
```

### Example 2: Validate the configuration of a specific existing custom authentication extension

#### Request

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
POST https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions/9f39f3bb-457c-4a2a-8099-0e480e7ea142/validateAuthenticationConfiguration
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.CustomAuthenticationExtensions["{customAuthenticationExtension-id}"].ValidateAuthenticationConfiguration.PostAsync();
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
validateAuthenticationConfiguration, err := graphClient.Identity().CustomAuthenticationExtensions().ByCustomAuthenticationExtensionId("customAuthenticationExtension-id").ValidateAuthenticationConfiguration().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.identity().customAuthenticationExtensions().byCustomAuthenticationExtensionId("{customAuthenticationExtension-id}").validateAuthenticationConfiguration().post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identity/customAuthenticationExtensions/9f39f3bb-457c-4a2a-8099-0e480e7ea142/validateAuthenticationConfiguration')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identity()->customAuthenticationExtensions()->byCustomAuthenticationExtensionId('customAuthenticationExtension-id')->validateAuthenticationConfiguration()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Test-MgIdentityCustomAuthenticationExtensionAuthenticationConfiguration -CustomAuthenticationExtensionId $customAuthenticationExtensionId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity.custom_authentication_extensions.by_custom_authentication_extension_id('customAuthenticationExtension-id').validate_authentication_configuration.post()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.authenticationConfigurationValidation",
    "errors": [
        {
            "code": "IncorrectResourceIdFormat",
            "message": "ResourceId should be in the format of 'api://{fully qualified domain name}/{appid}'"
        },
        {
            "code": "DomainNameDoesNotMatch",
            "message": "The fully qualified domain name in resourceId should match that of the targetUrl"
        },
        {
            "code": "ServicePrincipalNotFound",
            "message": "The appId of the resourceId should correspond to a real service principal in the tenant"
        }
    ],
    "warnings": [
        {
            "code": "PermissionNotGrantedToServicePrincipal",
            "message": "The permission CustomAuthenticationExtensions.Receive.Payload is not granted to the service principal of the resource app"
        },
    ]
}
```
