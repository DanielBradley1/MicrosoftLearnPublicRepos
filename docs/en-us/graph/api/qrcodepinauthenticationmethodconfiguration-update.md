<!-- Source: https://learn.microsoft.com/en-us/graph/api/qrcodepinauthenticationmethodconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update qrCodePinAuthenticationMethodConfiguration

Namespace: microsoft.graph

Update the properties of a [qrCodePinAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethodconfiguration?view=graph-rest-1.0) object, which represents the QR code PIN authentication method policy for the Microsoft Entra tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.AuthenticationMethod | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.AuthenticationMethod | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Authentication Policy Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /policies/authenticationMethodsPolicy/authenticationMethodConfigurations/qrCodePin
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [qrCodePinAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethodconfiguration?view=graph-rest-1.0) object with the values of properties that should be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| pinLength | Int32 | The required length of the PIN. The minimum is 8 digits and maximum is 20 digits. |
| standardQRCodeLifetimeInDays | Int32 | The default lifetime of standard QR codes in days. The minimum is 1 day and maximum is 395 days. The default is 365 days. |
| state | authenticationMethodState | The state of the policy. The possible values are: `enabled`, `disabled`. |

> **Note:** The `@odata.type` property with a value of `#microsoft.graph.qrCodePinAuthenticationMethodConfiguration` must be included in the body.

## Response

If successful, this method returns a `200 OK` response code and an updated [qrCodePinAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/qrcodepinauthenticationmethodconfiguration?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/qrCodePin
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCodePinAuthenticationMethodConfiguration",
  "state": "enabled",
  "standardQRCodeLifetimeInDays": 180,
  "pinLength": 10
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new QrCodePinAuthenticationMethodConfiguration
{
	OdataType = "#microsoft.graph.qrCodePinAuthenticationMethodConfiguration",
	State = AuthenticationMethodState.Enabled,
	StandardQRCodeLifetimeInDays = 180,
	PinLength = 10,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.AuthenticationMethodsPolicy.AuthenticationMethodConfigurations["{authenticationMethodConfiguration-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAuthenticationMethodConfiguration()
state := graphmodels.ENABLED_AUTHENTICATIONMETHODSTATE 
requestBody.SetState(&state) 
standardQRCodeLifetimeInDays := int32(180)
requestBody.SetStandardQRCodeLifetimeInDays(&standardQRCodeLifetimeInDays) 
pinLength := int32(10)
requestBody.SetPinLength(&pinLength) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationMethodConfigurations, err := graphClient.Policies().AuthenticationMethodsPolicy().AuthenticationMethodConfigurations().ByAuthenticationMethodConfigurationId("authenticationMethodConfiguration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

QrCodePinAuthenticationMethodConfiguration authenticationMethodConfiguration = new QrCodePinAuthenticationMethodConfiguration();
authenticationMethodConfiguration.setOdataType("#microsoft.graph.qrCodePinAuthenticationMethodConfiguration");
authenticationMethodConfiguration.setState(AuthenticationMethodState.Enabled);
authenticationMethodConfiguration.setStandardQRCodeLifetimeInDays(180);
authenticationMethodConfiguration.setPinLength(10);
AuthenticationMethodConfiguration result = graphClient.policies().authenticationMethodsPolicy().authenticationMethodConfigurations().byAuthenticationMethodConfigurationId("{authenticationMethodConfiguration-id}").patch(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationMethodConfiguration = {
  '@odata.type': '#microsoft.graph.qrCodePinAuthenticationMethodConfiguration',
  state: 'enabled',
  standardQRCodeLifetimeInDays: 180,
  pinLength: 10
};

await client.api('/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/qrCodePin')
	.update(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\QrCodePinAuthenticationMethodConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationMethodState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new QrCodePinAuthenticationMethodConfiguration();
$requestBody->setOdataType('#microsoft.graph.qrCodePinAuthenticationMethodConfiguration');
$requestBody->setState(new AuthenticationMethodState('enabled'));
$requestBody->setStandardQRCodeLifetimeInDays(180);
$requestBody->setPinLength(10);

$result = $graphServiceClient->policies()->authenticationMethodsPolicy()->authenticationMethodConfigurations()->byAuthenticationMethodConfigurationId('authenticationMethodConfiguration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.qrCodePinAuthenticationMethodConfiguration"
	state = "enabled"
	standardQRCodeLifetimeInDays = 
	pinLength = 
}

Update-MgPolicyAuthenticationMethodPolicyAuthenticationMethodConfiguration -AuthenticationMethodConfigurationId $authenticationMethodConfigurationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.qr_code_pin_authentication_method_configuration import QrCodePinAuthenticationMethodConfiguration
from msgraph.generated.models.authentication_method_state import AuthenticationMethodState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = QrCodePinAuthenticationMethodConfiguration(
	odata_type = "#microsoft.graph.qrCodePinAuthenticationMethodConfiguration",
	state = AuthenticationMethodState.Enabled,
	standard_q_r_code_lifetime_in_days = 180,
	pin_length = 10,
)

result = await graph_client.policies.authentication_methods_policy.authentication_method_configurations.by_authentication_method_configuration_id('authenticationMethodConfiguration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.qrCodePinAuthenticationMethodConfiguration",
  "id": "qrCodePin",
  "state": "enabled",
  "standardQRCodeLifetimeInDays": 180,
  "pinLength": 10,
  "excludeTargets": []
}
```
