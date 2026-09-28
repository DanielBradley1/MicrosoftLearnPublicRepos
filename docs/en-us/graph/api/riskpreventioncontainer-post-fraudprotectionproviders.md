<!-- Source: https://learn.microsoft.com/en-us/graph/api/riskpreventioncontainer-post-fraudprotectionproviders?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create fraudProtectionProviders

Namespace: microsoft.graph

Create a new [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) object. You can create one of the following subtypes that are derived from **fraudProtectionProvider**.

- [arkoseFraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/arkosefraudprotectionprovider?view=graph-rest-1.0)
- [humanSecurityFraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/humansecurityfraudprotectionprovider?view=graph-rest-1.0)

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
POST /identity/riskPrevention/fraudProtectionProviders
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) object.

You can specify the following properties when creating a **fraudProtectionProvider**. You must specify the **@odata.type** property to specify the type of **fraudProtectionProvider** to create; for example, `@odata.type": "microsoft.graph.arkoseFraudProtectionProvider"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of this fraud protection provider configuration. Supported for all providers. Required. Inherited from [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0). |
| privateKey | String | The private key available on the Arkose Portal. Contact your Arkose Customer Success Manager for assistance with your keys. Supported for Arkose only. Required. |
| publicKey | String | The public key available on the Arkose Portal. Contact your Arkose Customer Success Manager for assistance with your keys. Supported for Arkose only. Required. |
| verifySubDomain | String | Used to invoke the Arkose service from the Microsoft authentication server. Request from your Arkose Customer Success Manager or use the default `verify-api` value. Supported for Arkose only. Required. |
| clientSubDomain | String | Used to invoke the Arkose service from the client application. Request from your Arkose Customer Success Manager or use the default `client-api` value. Supported for Arkose only. Required. |
| appId | String | Unique identifier for an individual application. You can retrieve this from the HUMAN Security admin console or request it from your HUMAN Security Customer Success Manager. Supported for HUMAN Security only. Required. |
| serverToken | String | Unique identifier used to authenticate API calls between the Server side integration and the HUMAN platform. You can retrieve this from the HUMAN Security admin console or request it from your HUMAN Security Customer Success Manager. Supported for HUMAN Security only. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider?view=graph-rest-1.0) object in the response body. The **@odata.type** property specifies the type of the created object.

## Examples

### Example 1: Create a new arkoseFraudProtectionProvider object

#### Request

The following example shows a request to create a new Arkose fraudProtectionProvider object.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identity/riskPrevention/fraudProtectionProviders
Content-Type: application/json

{
   "@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider",
    "displayName": "Arkose Sign-Up Protection",
    "publicKey": "A1EE42E0-C88B-47FE-A176-5E9FB8F116FB",
    "privateKey": "19BBE628-7DEF-4E28-AB25-BF129C760B7E",
    "clientSubDomain": "client-api",
    "verifySubDomain": "verify-api"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ArkoseFraudProtectionProvider
{
	OdataType = "#microsoft.graph.arkoseFraudProtectionProvider",
	DisplayName = "Arkose Sign-Up Protection",
	PublicKey = "A1EE42E0-C88B-47FE-A176-5E9FB8F116FB",
	PrivateKey = "19BBE628-7DEF-4E28-AB25-BF129C760B7E",
	ClientSubDomain = "client-api",
	VerifySubDomain = "verify-api",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.RiskPrevention.FraudProtectionProviders.PostAsync(requestBody);
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
displayName := "Arkose Sign-Up Protection"
requestBody.SetDisplayName(&displayName) 
publicKey := "A1EE42E0-C88B-47FE-A176-5E9FB8F116FB"
requestBody.SetPublicKey(&publicKey) 
privateKey := "19BBE628-7DEF-4E28-AB25-BF129C760B7E"
requestBody.SetPrivateKey(&privateKey) 
clientSubDomain := "client-api"
requestBody.SetClientSubDomain(&clientSubDomain) 
verifySubDomain := "verify-api"
requestBody.SetVerifySubDomain(&verifySubDomain) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
fraudProtectionProviders, err := graphClient.Identity().RiskPrevention().FraudProtectionProviders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ArkoseFraudProtectionProvider fraudProtectionProvider = new ArkoseFraudProtectionProvider();
fraudProtectionProvider.setOdataType("#microsoft.graph.arkoseFraudProtectionProvider");
fraudProtectionProvider.setDisplayName("Arkose Sign-Up Protection");
fraudProtectionProvider.setPublicKey("A1EE42E0-C88B-47FE-A176-5E9FB8F116FB");
fraudProtectionProvider.setPrivateKey("19BBE628-7DEF-4E28-AB25-BF129C760B7E");
fraudProtectionProvider.setClientSubDomain("client-api");
fraudProtectionProvider.setVerifySubDomain("verify-api");
FraudProtectionProvider result = graphClient.identity().riskPrevention().fraudProtectionProviders().post(fraudProtectionProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fraudProtectionProvider = {
   '@odata.type': '#microsoft.graph.arkoseFraudProtectionProvider',
    displayName: 'Arkose Sign-Up Protection',
    publicKey: 'A1EE42E0-C88B-47FE-A176-5E9FB8F116FB',
    privateKey: '19BBE628-7DEF-4E28-AB25-BF129C760B7E',
    clientSubDomain: 'client-api',
    verifySubDomain: 'verify-api'
};

await client.api('/identity/riskPrevention/fraudProtectionProviders')
	.post(fraudProtectionProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ArkoseFraudProtectionProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ArkoseFraudProtectionProvider();
$requestBody->setOdataType('#microsoft.graph.arkoseFraudProtectionProvider');
$requestBody->setDisplayName('Arkose Sign-Up Protection');
$requestBody->setPublicKey('A1EE42E0-C88B-47FE-A176-5E9FB8F116FB');
$requestBody->setPrivateKey('19BBE628-7DEF-4E28-AB25-BF129C760B7E');
$requestBody->setClientSubDomain('client-api');
$requestBody->setVerifySubDomain('verify-api');

$result = $graphServiceClient->identity()->riskPrevention()->fraudProtectionProviders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.arkoseFraudProtectionProvider"
	displayName = "Arkose Sign-Up Protection"
	publicKey = "A1EE42E0-C88B-47FE-A176-5E9FB8F116FB"
	privateKey = "19BBE628-7DEF-4E28-AB25-BF129C760B7E"
	clientSubDomain = "client-api"
	verifySubDomain = "verify-api"
}

New-MgIdentityRiskPreventionFraudProtectionProvider -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.arkose_fraud_protection_provider import ArkoseFraudProtectionProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ArkoseFraudProtectionProvider(
	odata_type = "#microsoft.graph.arkoseFraudProtectionProvider",
	display_name = "Arkose Sign-Up Protection",
	public_key = "A1EE42E0-C88B-47FE-A176-5E9FB8F116FB",
	private_key = "19BBE628-7DEF-4E28-AB25-BF129C760B7E",
	client_sub_domain = "client-api",
	verify_sub_domain = "verify-api",
)

result = await graph_client.identity.risk_prevention.fraud_protection_providers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response with Arkose fraudProtectionProvider object.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/riskPrevention/fraudProtectionProviders/$entity",
    "@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider",
    "id": "d474f94f-0fcf-4224-a165-c1c5bad1600f",
    "displayName": "Arkose Sign-Up Protection",
    "publicKey": "A1EE42E0-C88B-47FE-A176-5E9FB8F116FB",
    "clientSubDomain": "client-api",
    "verifySubDomain": "verify-api"
}
```

### Example 2: Create a new humanSecurityFraudProtectionProvider object

#### Request

The following example shows a request to create a new HUMAN Security fraudProtectionProvider object.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identity/riskPrevention/fraudProtectionProviders
Content-Type: application/json

{
   "@odata.type": "#microsoft.graph.humanSecurityFraudProtectionProvider",
    "displayName": "HUMAN Security Sign-Up Protection",
    "appId": "XXyy1XXXy",
    "serverToken": "xxYYxxXXX1"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new HumanSecurityFraudProtectionProvider
{
	OdataType = "#microsoft.graph.humanSecurityFraudProtectionProvider",
	DisplayName = "HUMAN Security Sign-Up Protection",
	AppId = "XXyy1XXXy",
	ServerToken = "xxYYxxXXX1",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.RiskPrevention.FraudProtectionProviders.PostAsync(requestBody);
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
displayName := "HUMAN Security Sign-Up Protection"
requestBody.SetDisplayName(&displayName) 
appId := "XXyy1XXXy"
requestBody.SetAppId(&appId) 
serverToken := "xxYYxxXXX1"
requestBody.SetServerToken(&serverToken) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
fraudProtectionProviders, err := graphClient.Identity().RiskPrevention().FraudProtectionProviders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

HumanSecurityFraudProtectionProvider fraudProtectionProvider = new HumanSecurityFraudProtectionProvider();
fraudProtectionProvider.setOdataType("#microsoft.graph.humanSecurityFraudProtectionProvider");
fraudProtectionProvider.setDisplayName("HUMAN Security Sign-Up Protection");
fraudProtectionProvider.setAppId("XXyy1XXXy");
fraudProtectionProvider.setServerToken("xxYYxxXXX1");
FraudProtectionProvider result = graphClient.identity().riskPrevention().fraudProtectionProviders().post(fraudProtectionProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const fraudProtectionProvider = {
   '@odata.type': '#microsoft.graph.humanSecurityFraudProtectionProvider',
    displayName: 'HUMAN Security Sign-Up Protection',
    appId: 'XXyy1XXXy',
    serverToken: 'xxYYxxXXX1'
};

await client.api('/identity/riskPrevention/fraudProtectionProviders')
	.post(fraudProtectionProvider);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\HumanSecurityFraudProtectionProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new HumanSecurityFraudProtectionProvider();
$requestBody->setOdataType('#microsoft.graph.humanSecurityFraudProtectionProvider');
$requestBody->setDisplayName('HUMAN Security Sign-Up Protection');
$requestBody->setAppId('XXyy1XXXy');
$requestBody->setServerToken('xxYYxxXXX1');

$result = $graphServiceClient->identity()->riskPrevention()->fraudProtectionProviders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.humanSecurityFraudProtectionProvider"
	displayName = "HUMAN Security Sign-Up Protection"
	appId = "XXyy1XXXy"
	serverToken = "xxYYxxXXX1"
}

New-MgIdentityRiskPreventionFraudProtectionProvider -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.human_security_fraud_protection_provider import HumanSecurityFraudProtectionProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = HumanSecurityFraudProtectionProvider(
	odata_type = "#microsoft.graph.humanSecurityFraudProtectionProvider",
	display_name = "HUMAN Security Sign-Up Protection",
	app_id = "XXyy1XXXy",
	server_token = "xxYYxxXXX1",
)

result = await graph_client.identity.risk_prevention.fraud_protection_providers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response with Human Security fraudProtectionProvider object.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/riskPrevention/fraudProtectionProviders/$entity",
    "@odata.type": "#microsoft.graph.humanSecurityFraudProtectionProvider",
    "id": "6b09e36f-7e92-4448-842a-3959bcbc4f9f",
    "displayName": "HUMAN security Sign-Up provider",
    "appId": "XXyy1XXXy"
}
```
