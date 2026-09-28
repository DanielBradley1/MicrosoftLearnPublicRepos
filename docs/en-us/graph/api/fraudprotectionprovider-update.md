<!-- Source: https://learn.microsoft.com/en-us/graph/api/fraudprotectionprovider-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update fraudProtectionProvider

Namespace: microsoft.graph

Update the properties of a [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) object. The following derived types are currently supported.

- [arkoseFraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/arkosefraudprotectionprovider?view=graph-rest-1.0) resource type
- [humanSecurityFraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/humansecurityfraudprotectionprovider?view=graph-rest-1.0) resource type

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RiskPreventionProviders.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- External ID User Flow Administrator
- Application Administrator
- Security Administrator

## HTTP request

```http
PATCH /identity/riskPrevention/fraudProtectionProviders/{fraudProtectionProviderId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the **@odata.type** property and the value of the [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) object type to update. For example, `"@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | Unique identifier for an individual application. You can retrieve this from the HUMAN Security admin console or request it from your HUMAN Security Customer Success Manager. Supported for HUMAN Security only. Optional. |
| clientSubDomain | String | Used to invoke the Arkose service from the client application. Request from your Arkose Customer Success Manager or use the default `client-api` value. Supported for Arkose only. Optional. |
| displayName | String | The display name of the fraud protection provider configuration. Supported for all providers. Optional. |
| privateKey | String | The private key available on the Arkose Portal. Contact your Arkose Customer Success Manager for assistance with your keys. Supported for Arkose only. Optional. |
| publicKey | String | The public key available on the Arkose Portal. Contact your Arkose Customer Success Manager for assistance with your keys. Supported for Arkose only. Optional. |
| serverToken | String | Unique identifier used to authenticate API calls between the Server side integration and the HUMAN platform. You can retrieve this from the HUMAN Security admin console or request it from your HUMAN Security Customer Success Manager. Supported for HUMAN Security only. Optional. |
| verifySubDomain | String | Used to invoke the Arkose service from the Microsoft authentication server. Request from your Arkose Customer Success Manager or use the default `verify-api` value. Supported for Arkose only. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request to update Arkose fraud protection provider.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/identity/riskPrevention/fraudProtectionProviders/9826466a-5275-438d-98e1-f3df6470a4b5
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider",
    "displayName": "Arkose Sign-Up Protection Updated",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ArkoseFraudProtectionProvider
{
	OdataType = "#microsoft.graph.arkoseFraudProtectionProvider",
	DisplayName = "Arkose Sign-Up Protection Updated",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.RiskPrevention.FraudProtectionProviders["{fraudProtectionProvider-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewFraudProtectionProvider()
displayName := "Arkose Sign-Up Protection Updated"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
fraudProtectionProviders, err := graphClient.Identity().RiskPrevention().FraudProtectionProviders().ByFraudProtectionProviderId("fraudProtectionProvider-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ArkoseFraudProtectionProvider fraudProtectionProvider = new ArkoseFraudProtectionProvider();
fraudProtectionProvider.setOdataType("#microsoft.graph.arkoseFraudProtectionProvider");
fraudProtectionProvider.setDisplayName("Arkose Sign-Up Protection Updated");
FraudProtectionProvider result = graphClient.identity().riskPrevention().fraudProtectionProviders().byFraudProtectionProviderId("{fraudProtectionProvider-id}").patch(fraudProtectionProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fraudProtectionProvider = {
    '@odata.type': '#microsoft.graph.arkoseFraudProtectionProvider',
    displayName: 'Arkose Sign-Up Protection Updated',
};

await client.api('/identity/riskPrevention/fraudProtectionProviders/9826466a-5275-438d-98e1-f3df6470a4b5')
	.update(fraudProtectionProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ArkoseFraudProtectionProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ArkoseFraudProtectionProvider();
$requestBody->setOdataType('#microsoft.graph.arkoseFraudProtectionProvider');
$requestBody->setDisplayName('Arkose Sign-Up Protection Updated');

$result = $graphServiceClient->identity()->riskPrevention()->fraudProtectionProviders()->byFraudProtectionProviderId('fraudProtectionProvider-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.arkoseFraudProtectionProvider"
	displayName = "Arkose Sign-Up Protection Updated"
}

Update-MgIdentityRiskPreventionFraudProtectionProvider -FraudProtectionProviderId $fraudProtectionProviderId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.arkose_fraud_protection_provider import ArkoseFraudProtectionProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ArkoseFraudProtectionProvider(
	odata_type = "#microsoft.graph.arkoseFraudProtectionProvider",
	display_name = "Arkose Sign-Up Protection Updated",
)

result = await graph_client.identity.risk_prevention.fraud_protection_providers.by_fraud_protection_provider_id('fraudProtectionProvider-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
