<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-b2cuserflows?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Create b2cIdentityUserFlow

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [b2cIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2cidentityuserflow?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | IdentityUserFlow.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | IdentityUserFlow.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *External ID User Flow Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identity/b2cUserFlows
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON representation of a [b2cIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2cidentityuserflow?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Required. The name of the user flow. The name will be prepended with `B2C_1_` after creation if the prefix wasn't added to the name during your request. |
| userFlowType | String | Required. The type of user flow you're creating. The supported values for **userFlowType** are:  <br><br><br>- `signUp`<br>- `signIn`<br>- `signUpOrSignIn`<br>- `passwordReset`<br>- `profileUpdate`<br>- `resourceOwner` |
| userFlowTypeVersion | Float | Required. The version of the user flow. |
| isLanguageCustomizationEnabled | Boolean | Optional. Determines whether language customization is enabled within the Azure AD B2C user flow. Language customization isn't enabled by default for Azure AD B2C user flows. |
| defaultLanguageTag | String | Optional. Specifies the default language of the b2cIdentityUserFlow that is used when no `ui_locale` tag is specified in the request. This field is [RFC 5646](https://tools.ietf.org/html/rfc5646) compliant. |
| identityProviders | [identityProvider](https://learn.microsoft.com/en-us/graph/api/resources/identityprovider?view=graph-rest-beta) collection | Optional. The identity providers you want to include in the user flow. |

## Response

If successful, this method returns a `201 Created` response code and a Location header with a URI to the [b2cIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2cidentityuserflow?view=graph-rest-beta) object created for this request, with the `B2C_1_` prefix added to the name. If unsuccessful, a `4xx` error is returned with specific details.

## Examples

### Example 1: Create a user flow with the default values

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
POST https://graph.microsoft.com/beta/identity/b2cUserFlows
Content-type: application/json

{
    "id": "Customer",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 3
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new B2cIdentityUserFlow
{
	Id = "Customer",
	UserFlowType = UserFlowType.SignUpOrSignIn,
	UserFlowTypeVersion = 3f,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.B2cUserFlows.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewB2cIdentityUserFlow()
id := "Customer"
requestBody.SetId(&id) 
userFlowType := graphmodels.SIGNUPORSIGNIN_USERFLOWTYPE 
requestBody.SetUserFlowType(&userFlowType) 
userFlowTypeVersion := float32(3)
requestBody.SetUserFlowTypeVersion(&userFlowTypeVersion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
b2cUserFlows, err := graphClient.Identity().B2cUserFlows().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

B2cIdentityUserFlow b2cIdentityUserFlow = new B2cIdentityUserFlow();
b2cIdentityUserFlow.setId("Customer");
b2cIdentityUserFlow.setUserFlowType(UserFlowType.SignUpOrSignIn);
b2cIdentityUserFlow.setUserFlowTypeVersion(3f);
B2cIdentityUserFlow result = graphClient.identity().b2cUserFlows().post(b2cIdentityUserFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2cIdentityUserFlow = {
    id: 'Customer',
    userFlowType: 'signUpOrSignIn',
    userFlowTypeVersion: 3
};

await client.api('/identity/b2cUserFlows')
	.version('beta')
	.post(b2cIdentityUserFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\B2cIdentityUserFlow;
use Microsoft\Graph\Beta\Generated\Models\UserFlowType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new B2cIdentityUserFlow();
$requestBody->setId('Customer');
$requestBody->setUserFlowType(new UserFlowType('signUpOrSignIn'));
$requestBody->setUserFlowTypeVersion(3);

$result = $graphServiceClient->identity()->b2cUserFlows()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	id = "Customer"
	userFlowType = "signUpOrSignIn"
	userFlowTypeVersion = 3
}

New-MgBetaIdentityB2CUserFlow -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.b2c_identity_user_flow import B2cIdentityUserFlow
from msgraph_beta.generated.models.user_flow_type import UserFlowType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = B2cIdentityUserFlow(
	id = "Customer",
	user_flow_type = UserFlowType.SignUpOrSignIn,
	user_flow_type_version = 3,
)

result = await graph_client.identity.b2c_user_flows.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/beta/identity/b2cUserFlows('B2C_1_Customer')
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identity/b2cUserFlows/$entity",
    "id": "B2C_1_Customer",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 3,
    "isLanguageCustomizationEnabled": false,
    "defaultLanguageTag": "en",
    "authenticationMethods": "emailWithPassword",
    "tokenClaimsConfiguration": {
        "isIssuerEntityUserFlow": false
    },
    "apiConnectorConfiguration": {}
}
```

### Example 2: Create a user flow with the default values and an identity provider

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
POST https://graph.microsoft.com/beta/identity/b2cUserFlows
Location: https://graph.microsoft.com/beta/identity/b2cUserFlows('B2C_1_Customer')
Content-type: application/json

{
    "id": "Customer",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 3,
    "identityProviders": [
        {
            "id": "Facebook-OAuth"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new B2cIdentityUserFlow
{
	Id = "Customer",
	UserFlowType = UserFlowType.SignUpOrSignIn,
	UserFlowTypeVersion = 3f,
	IdentityProviders = new List<IdentityProvider>
	{
		new IdentityProvider
		{
			Id = "Facebook-OAuth",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.B2cUserFlows.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Location", "https://graph.microsoft.com/beta/identity/b2cUserFlows('B2C_1_Customer')");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  graphidentity "github.com/microsoftgraph/msgraph-beta-sdk-go/identity"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Location", "https://graph.microsoft.com/beta/identity/b2cUserFlows('B2C_1_Customer')")

configuration := &graphidentity.IdentityB2cUserFlowsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewB2cIdentityUserFlow()
id := "Customer"
requestBody.SetId(&id) 
userFlowType := graphmodels.SIGNUPORSIGNIN_USERFLOWTYPE 
requestBody.SetUserFlowType(&userFlowType) 
userFlowTypeVersion := float32(3)
requestBody.SetUserFlowTypeVersion(&userFlowTypeVersion) 


identityProvider := graphmodels.NewIdentityProvider()
id := "Facebook-OAuth"
identityProvider.SetId(&id) 

identityProviders := []graphmodels.IdentityProviderable {
	identityProvider,
}
requestBody.SetIdentityProviders(identityProviders)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
b2cUserFlows, err := graphClient.Identity().B2cUserFlows().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

B2cIdentityUserFlow b2cIdentityUserFlow = new B2cIdentityUserFlow();
b2cIdentityUserFlow.setId("Customer");
b2cIdentityUserFlow.setUserFlowType(UserFlowType.SignUpOrSignIn);
b2cIdentityUserFlow.setUserFlowTypeVersion(3f);
LinkedList<IdentityProvider> identityProviders = new LinkedList<IdentityProvider>();
IdentityProvider identityProvider = new IdentityProvider();
identityProvider.setId("Facebook-OAuth");
identityProviders.add(identityProvider);
b2cIdentityUserFlow.setIdentityProviders(identityProviders);
B2cIdentityUserFlow result = graphClient.identity().b2cUserFlows().post(b2cIdentityUserFlow, requestConfiguration -> {
	requestConfiguration.headers.add("Location", "https://graph.microsoft.com/beta/identity/b2cUserFlows('B2C_1_Customer')");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2cIdentityUserFlow = {
    id: 'Customer',
    userFlowType: 'signUpOrSignIn',
    userFlowTypeVersion: 3,
    identityProviders: [
        {
            id: 'Facebook-OAuth'
        }
    ]
};

await client.api('/identity/b2cUserFlows')
	.version('beta')
	.post(b2cIdentityUserFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Identity\B2cUserFlows\B2cUserFlowsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\B2cIdentityUserFlow;
use Microsoft\Graph\Beta\Generated\Models\UserFlowType;
use Microsoft\Graph\Beta\Generated\Models\IdentityProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new B2cIdentityUserFlow();
$requestBody->setId('Customer');
$requestBody->setUserFlowType(new UserFlowType('signUpOrSignIn'));
$requestBody->setUserFlowTypeVersion(3);
$identityProvidersIdentityProvider1 = new IdentityProvider();
$identityProvidersIdentityProvider1->setId('Facebook-OAuth');
$identityProvidersArray []= $identityProvidersIdentityProvider1;
$requestBody->setIdentityProviders($identityProvidersArray);

$requestConfiguration = new B2cUserFlowsRequestBuilderPostRequestConfiguration();
$headers = [
	'Location' => 'https://graph.microsoft.com/beta/identity/b2cUserFlows(\'B2C_1_Customer\')',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->identity()->b2cUserFlows()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	id = "Customer"
	userFlowType = "signUpOrSignIn"
	userFlowTypeVersion = 3
	identityProviders = @(
		@{
			id = "Facebook-OAuth"
		}
	)
}

New-MgBetaIdentityB2CUserFlow -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.identity.b2c_user_flows.b2c_user_flows_request_builder import B2cUserFlowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.b2c_identity_user_flow import B2cIdentityUserFlow
from msgraph_beta.generated.models.user_flow_type import UserFlowType
from msgraph_beta.generated.models.identity_provider import IdentityProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = B2cIdentityUserFlow(
	id = "Customer",
	user_flow_type = UserFlowType.SignUpOrSignIn,
	user_flow_type_version = 3,
	identity_providers = [
		IdentityProvider(
			id = "Facebook-OAuth",
		),
	],
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Location", "https://graph.microsoft.com/beta/identity/b2cUserFlows('B2C_1_Customer')")


result = await graph_client.identity.b2c_user_flows.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identity/b2cUserFlows/$entity",
    "id": "B2C_1_Customer",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 3,
    "isLanguageCustomizationEnabled": false,
    "defaultLanguageTag": "en",
    "authenticationMethods": "0",
    "tokenClaimsConfiguration": {
        "isIssuerEntityUserFlow": false
    },
    "apiConnectorConfiguration": {}
}
```

### Example 3: Create a user flow with the default values and configuration for API connectors

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/identity/b2cUserFlows
Content-type: application/json

{
    "id": "UserFlowWithAPIConnector",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1,
    "apiConnectorConfiguration":{
        "postFederationSignup":{
            "@odata.id": "{apiConnectorId}"
        },
        "postAttributeCollection":{
            "@odata.id": "{apiConnectorId}"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new B2cIdentityUserFlow
{
	Id = "UserFlowWithAPIConnector",
	UserFlowType = UserFlowType.SignUpOrSignIn,
	UserFlowTypeVersion = 1f,
	ApiConnectorConfiguration = new UserFlowApiConnectorConfiguration
	{
		PostFederationSignup = new IdentityApiConnector
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@odata.id" , "{apiConnectorId}"
				},
			},
		},
		PostAttributeCollection = new IdentityApiConnector
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@odata.id" , "{apiConnectorId}"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.B2cUserFlows.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewB2cIdentityUserFlow()
id := "UserFlowWithAPIConnector"
requestBody.SetId(&id) 
userFlowType := graphmodels.SIGNUPORSIGNIN_USERFLOWTYPE 
requestBody.SetUserFlowType(&userFlowType) 
userFlowTypeVersion := float32(1)
requestBody.SetUserFlowTypeVersion(&userFlowTypeVersion) 
apiConnectorConfiguration := graphmodels.NewUserFlowApiConnectorConfiguration()
postFederationSignup := graphmodels.NewIdentityApiConnector()
additionalData := map[string]interface{}{
	"@odata.id" : "{apiConnectorId}", 
}
postFederationSignup.SetAdditionalData(additionalData)
apiConnectorConfiguration.SetPostFederationSignup(postFederationSignup)
postAttributeCollection := graphmodels.NewIdentityApiConnector()
additionalData := map[string]interface{}{
	"@odata.id" : "{apiConnectorId}", 
}
postAttributeCollection.SetAdditionalData(additionalData)
apiConnectorConfiguration.SetPostAttributeCollection(postAttributeCollection)
requestBody.SetApiConnectorConfiguration(apiConnectorConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
b2cUserFlows, err := graphClient.Identity().B2cUserFlows().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

B2cIdentityUserFlow b2cIdentityUserFlow = new B2cIdentityUserFlow();
b2cIdentityUserFlow.setId("UserFlowWithAPIConnector");
b2cIdentityUserFlow.setUserFlowType(UserFlowType.SignUpOrSignIn);
b2cIdentityUserFlow.setUserFlowTypeVersion(1f);
UserFlowApiConnectorConfiguration apiConnectorConfiguration = new UserFlowApiConnectorConfiguration();
IdentityApiConnector postFederationSignup = new IdentityApiConnector();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.id", "{apiConnectorId}");
postFederationSignup.setAdditionalData(additionalData);
apiConnectorConfiguration.setPostFederationSignup(postFederationSignup);
IdentityApiConnector postAttributeCollection = new IdentityApiConnector();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("@odata.id", "{apiConnectorId}");
postAttributeCollection.setAdditionalData(additionalData1);
apiConnectorConfiguration.setPostAttributeCollection(postAttributeCollection);
b2cIdentityUserFlow.setApiConnectorConfiguration(apiConnectorConfiguration);
B2cIdentityUserFlow result = graphClient.identity().b2cUserFlows().post(b2cIdentityUserFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2cIdentityUserFlow = {
    id: 'UserFlowWithAPIConnector',
    userFlowType: 'signUpOrSignIn',
    userFlowTypeVersion: 1,
    apiConnectorConfiguration: {
        postFederationSignup: {
            '@odata.id': '{apiConnectorId}'
        },
        postAttributeCollection: {
            '@odata.id': '{apiConnectorId}'
        }
    }
};

await client.api('/identity/b2cUserFlows')
	.version('beta')
	.post(b2cIdentityUserFlow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\B2cIdentityUserFlow;
use Microsoft\Graph\Beta\Generated\Models\UserFlowType;
use Microsoft\Graph\Beta\Generated\Models\UserFlowApiConnectorConfiguration;
use Microsoft\Graph\Beta\Generated\Models\IdentityApiConnector;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new B2cIdentityUserFlow();
$requestBody->setId('UserFlowWithAPIConnector');
$requestBody->setUserFlowType(new UserFlowType('signUpOrSignIn'));
$requestBody->setUserFlowTypeVersion(1);
$apiConnectorConfiguration = new UserFlowApiConnectorConfiguration();
$apiConnectorConfigurationPostFederationSignup = new IdentityApiConnector();
$additionalData = [
	'@odata.id' => '{apiConnectorId}',
];
$apiConnectorConfigurationPostFederationSignup->setAdditionalData($additionalData);
$apiConnectorConfiguration->setPostFederationSignup($apiConnectorConfigurationPostFederationSignup);
$apiConnectorConfigurationPostAttributeCollection = new IdentityApiConnector();
$additionalData = [
	'@odata.id' => '{apiConnectorId}',
];
$apiConnectorConfigurationPostAttributeCollection->setAdditionalData($additionalData);
$apiConnectorConfiguration->setPostAttributeCollection($apiConnectorConfigurationPostAttributeCollection);
$requestBody->setApiConnectorConfiguration($apiConnectorConfiguration);

$result = $graphServiceClient->identity()->b2cUserFlows()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.SignIns

$params = @{
	id = "UserFlowWithAPIConnector"
	userFlowType = "signUpOrSignIn"
	userFlowTypeVersion = 1
	apiConnectorConfiguration = @{
		postFederationSignup = @{
			"@odata.id" = '{apiConnectorId}'
		}
		postAttributeCollection = @{
			"@odata.id" = '{apiConnectorId}'
		}
	}
}

New-MgBetaIdentityB2CUserFlow -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.b2c_identity_user_flow import B2cIdentityUserFlow
from msgraph_beta.generated.models.user_flow_type import UserFlowType
from msgraph_beta.generated.models.user_flow_api_connector_configuration import UserFlowApiConnectorConfiguration
from msgraph_beta.generated.models.identity_api_connector import IdentityApiConnector
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = B2cIdentityUserFlow(
	id = "UserFlowWithAPIConnector",
	user_flow_type = UserFlowType.SignUpOrSignIn,
	user_flow_type_version = 1,
	api_connector_configuration = UserFlowApiConnectorConfiguration(
		post_federation_signup = IdentityApiConnector(
			additional_data = {
					"@odata_id" : "{apiConnectorId}",
			}
		),
		post_attribute_collection = IdentityApiConnector(
			additional_data = {
					"@odata_id" : "{apiConnectorId}",
			}
		),
	),
)

result = await graph_client.identity.b2c_user_flows.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

**Note:** The response object shown here might be shortened for readability.

**Note:** The `apiConnectorConfiguration` property always returns a '{}' value. To see full value with the navigation properties, use [this](https://learn.microsoft.com/en-us/graph/api/b2cidentityuserflow-get-apiconnectorconfiguration?view=graph-rest-beta) API.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/beta/identity/b2cUserFlows/B2C_1_Partner
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identity/b2cUserFlows/$entity",
    "id": "B2C_1_UserFlowWithAPIConnector",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1,
    "apiConnectorConfiguration": {}
}
```
