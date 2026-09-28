<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-identityproviders?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create identityProvider

Namespace: microsoft.graph

Create an identity provider object that is of the type specified in the request body.

Among the types of providers derived from identityProviderBase, you can currently create a [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) resource in Microsoft Entra ID. In Azure AD B2C, this operation can currently create a [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0), or an [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) resource.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityProvider.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityProvider.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External Identity Provider Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identity/identityProviders
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON representation of [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) object in Microsoft Entra ID.

In Azure AD B2C provide a JSON representation of [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0), or an [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) object.

### socialIdentityProvider object

| Property | Type | Description |
| :--- | :--- | :--- |
| clientId | String | The client identifier for the application obtained when registering the application with the identity provider. |
| clientSecret | String | The client secret for the application that is obtained when the application is registered with the identity provider. This is write-only. A read operation returns `****`. |
| displayName | String | The display name of the identity provider. |
| identityProviderType | String | For a B2B scenario, possible values: `Google`, `Facebook`. For a B2C scenario, possible values: `Microsoft`, `Google`, `Amazon`, `LinkedIn`, `Facebook`, `GitHub`, `Twitter`, `Weibo`, `QQ`, `WeChat`. |
| scope | String | Scope defines the information and permissions you are looking to gather from your custom identity provider. |

### appleIdentityProvider object

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity provider. |
| developerId | String | The Apple developer identifier. |
| serviceId | String | The Apple service identifier. |
| keyId | String | The Apple key identifier. |
| certificateData | String | The certificate data which is a long string of text from the certificate, can be null. |

## Response

If successful, this method returns a `201 Created` response code and a JSON representation of a [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) object in the response body for a Microsoft Entra tenant.

For an Azure AD B2C tenant, this method returns a `201 Created` response code and a JSON representation of a [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0), or an [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) object in the response body.

If unsuccessful, a `4xx` error will be returned with specific details.

## Examples

### Example 1: Create a specific social identity provider \(Microsoft Entra ID and Azure AD B2C\)

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
POST https://graph.microsoft.com/v1.0/identity/identityProviders
Content-type: application/json

{
  "@odata.type": "microsoft.graph.socialIdentityProvider",
  "displayName": "Login with Amazon",
  "identityProviderType": "Amazon",
  "clientId": "56433757-cadd-4135-8431-2c9e3fd68ae8",
  "clientSecret": "000000000000"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SocialIdentityProvider
{
	OdataType = "microsoft.graph.socialIdentityProvider",
	DisplayName = "Login with Amazon",
	IdentityProviderType = "Amazon",
	ClientId = "56433757-cadd-4135-8431-2c9e3fd68ae8",
	ClientSecret = "000000000000",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.IdentityProviders.PostAsync(requestBody);
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

requestBody := graphmodels.NewIdentityProviderBase()
displayName := "Login with Amazon"
requestBody.SetDisplayName(&displayName) 
identityProviderType := "Amazon"
requestBody.SetIdentityProviderType(&identityProviderType) 
clientId := "56433757-cadd-4135-8431-2c9e3fd68ae8"
requestBody.SetClientId(&clientId) 
clientSecret := "000000000000"
requestBody.SetClientSecret(&clientSecret) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
identityProviders, err := graphClient.Identity().IdentityProviders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SocialIdentityProvider identityProviderBase = new SocialIdentityProvider();
identityProviderBase.setOdataType("microsoft.graph.socialIdentityProvider");
identityProviderBase.setDisplayName("Login with Amazon");
identityProviderBase.setIdentityProviderType("Amazon");
identityProviderBase.setClientId("56433757-cadd-4135-8431-2c9e3fd68ae8");
identityProviderBase.setClientSecret("000000000000");
IdentityProviderBase result = graphClient.identity().identityProviders().post(identityProviderBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const identityProviderBase = {
  '@odata.type': 'microsoft.graph.socialIdentityProvider',
  displayName: 'Login with Amazon',
  identityProviderType: 'Amazon',
  clientId: '56433757-cadd-4135-8431-2c9e3fd68ae8',
  clientSecret: '000000000000'
};

await client.api('/identity/identityProviders')
	.post(identityProviderBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SocialIdentityProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SocialIdentityProvider();
$requestBody->setOdataType('microsoft.graph.socialIdentityProvider');
$requestBody->setDisplayName('Login with Amazon');
$requestBody->setIdentityProviderType('Amazon');
$requestBody->setClientId('56433757-cadd-4135-8431-2c9e3fd68ae8');
$requestBody->setClientSecret('000000000000');

$result = $graphServiceClient->identity()->identityProviders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "microsoft.graph.socialIdentityProvider"
	displayName = "Login with Amazon"
	identityProviderType = "Amazon"
	clientId = "56433757-cadd-4135-8431-2c9e3fd68ae8"
	clientSecret = "000000000000"
}

New-MgIdentityProvider -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.social_identity_provider import SocialIdentityProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SocialIdentityProvider(
	odata_type = "microsoft.graph.socialIdentityProvider",
	display_name = "Login with Amazon",
	identity_provider_type = "Amazon",
	client_id = "56433757-cadd-4135-8431-2c9e3fd68ae8",
	client_secret = "000000000000",
)

result = await graph_client.identity.identity_providers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.type": "microsoft.graph.socialIdentityProvider",
    "id": "Amazon-OAUTH",
    "displayName": "Login with Amazon",
    "identityProviderType": "Amazon",
    "clientId": "56433757-cadd-4135-8431-2c9e3fd68ae8",
    "clientSecret": "000000000000"
}
```

### Example 2: Create Apple identity provider \(only for Azure AD B2C\)

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identity/identityProviders
Content-type: application/json

{
  "@odata.type": "microsoft.graph.appleManagedIdentityProvider",
  "displayName": "Sign in with Apple",
  "developerId": "UBF8T346G9",
  "serviceId": "com.microsoft.rts.b2c.test.client",
  "keyId": "99P6D879C4",
  "certificateData": "******"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AppleManagedIdentityProvider
{
	OdataType = "microsoft.graph.appleManagedIdentityProvider",
	DisplayName = "Sign in with Apple",
	DeveloperId = "UBF8T346G9",
	ServiceId = "com.microsoft.rts.b2c.test.client",
	KeyId = "99P6D879C4",
	CertificateData = "******",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.IdentityProviders.PostAsync(requestBody);
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

requestBody := graphmodels.NewIdentityProviderBase()
displayName := "Sign in with Apple"
requestBody.SetDisplayName(&displayName) 
developerId := "UBF8T346G9"
requestBody.SetDeveloperId(&developerId) 
serviceId := "com.microsoft.rts.b2c.test.client"
requestBody.SetServiceId(&serviceId) 
keyId := "99P6D879C4"
requestBody.SetKeyId(&keyId) 
certificateData := "******"
requestBody.SetCertificateData(&certificateData) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
identityProviders, err := graphClient.Identity().IdentityProviders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppleManagedIdentityProvider identityProviderBase = new AppleManagedIdentityProvider();
identityProviderBase.setOdataType("microsoft.graph.appleManagedIdentityProvider");
identityProviderBase.setDisplayName("Sign in with Apple");
identityProviderBase.setDeveloperId("UBF8T346G9");
identityProviderBase.setServiceId("com.microsoft.rts.b2c.test.client");
identityProviderBase.setKeyId("99P6D879C4");
identityProviderBase.setCertificateData("******");
IdentityProviderBase result = graphClient.identity().identityProviders().post(identityProviderBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const identityProviderBase = {
  '@odata.type': 'microsoft.graph.appleManagedIdentityProvider',
  displayName: 'Sign in with Apple',
  developerId: 'UBF8T346G9',
  serviceId: 'com.microsoft.rts.b2c.test.client',
  keyId: '99P6D879C4',
  certificateData: '******'
};

await client.api('/identity/identityProviders')
	.post(identityProviderBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AppleManagedIdentityProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AppleManagedIdentityProvider();
$requestBody->setOdataType('microsoft.graph.appleManagedIdentityProvider');
$requestBody->setDisplayName('Sign in with Apple');
$requestBody->setDeveloperId('UBF8T346G9');
$requestBody->setServiceId('com.microsoft.rts.b2c.test.client');
$requestBody->setKeyId('99P6D879C4');
$requestBody->setCertificateData('******');

$result = $graphServiceClient->identity()->identityProviders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "microsoft.graph.appleManagedIdentityProvider"
	displayName = "Sign in with Apple"
	developerId = "UBF8T346G9"
	serviceId = "com.microsoft.rts.b2c.test.client"
	keyId = "99P6D879C4"
	certificateData = "******"
}

New-MgIdentityProvider -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.apple_managed_identity_provider import AppleManagedIdentityProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AppleManagedIdentityProvider(
	odata_type = "microsoft.graph.appleManagedIdentityProvider",
	display_name = "Sign in with Apple",
	developer_id = "UBF8T346G9",
	service_id = "com.microsoft.rts.b2c.test.client",
	key_id = "99P6D879C4",
	certificate_data = "******",
)

result = await graph_client.identity.identity_providers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.type": "microsoft.graph.appleManagedIdentityProvider",
  "id": "Apple-Managed-OIDC",
  "displayName": "Sign in with Apple",
  "developerId": "UBF8T346G9",
  "serviceId": "com.microsoft.rts.b2c.test.client",
  "keyId": "99P6D879C4",
  "certificateData": "******"
}
```
