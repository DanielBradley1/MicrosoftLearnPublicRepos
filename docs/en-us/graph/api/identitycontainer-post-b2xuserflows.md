<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-b2xuserflows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create b2xIdentityUserFlow

Namespace: microsoft.graph

Create a new [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ✅ |

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
POST /identity/b2xUserFlows
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON representation of a [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Required. The name of the user flow. The name will be prepended with `B2X_1` after creation. |
| userFlowType | String | Required. The type of user flow you're creating. This value will always be `signUpOrSignIn`. |
| userFlowTypeVersion | Float | Required. The version of the user flow. This value will always be 1. |
| apiConnectorConfiguration | [userFlowApiConnectorConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowapiconnectorconfiguration?view=graph-rest-1.0) | Optional. Configuration for enabling an API connector for use as part of the user flow. |

## Response

If successful, this method returns a `201 Created` response code and a Location header with a URI to the [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-1.0) object created for this request, with the `B2X_1` prefix added to the name. If unsuccessful, a `4xx` error is returned with specific details.

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
POST https://graph.microsoft.com/v1.0/identity/b2xUserFlows
Content-type: application/json

{
    "id": "Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new B2xIdentityUserFlow
{
	Id = "Partner",
	UserFlowType = UserFlowType.SignUpOrSignIn,
	UserFlowTypeVersion = 1f,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.B2xUserFlows.PostAsync(requestBody);
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

requestBody := graphmodels.NewB2xIdentityUserFlow()
id := "Partner"
requestBody.SetId(&id) 
userFlowType := graphmodels.SIGNUPORSIGNIN_USERFLOWTYPE 
requestBody.SetUserFlowType(&userFlowType) 
userFlowTypeVersion := float32(1)
requestBody.SetUserFlowTypeVersion(&userFlowTypeVersion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
b2xUserFlows, err := graphClient.Identity().B2xUserFlows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

B2xIdentityUserFlow b2xIdentityUserFlow = new B2xIdentityUserFlow();
b2xIdentityUserFlow.setId("Partner");
b2xIdentityUserFlow.setUserFlowType(UserFlowType.SignUpOrSignIn);
b2xIdentityUserFlow.setUserFlowTypeVersion(1f);
B2xIdentityUserFlow result = graphClient.identity().b2xUserFlows().post(b2xIdentityUserFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2xIdentityUserFlow = {
    id: 'Partner',
    userFlowType: 'signUpOrSignIn',
    userFlowTypeVersion: 1
};

await client.api('/identity/b2xUserFlows')
	.post(b2xIdentityUserFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\B2xIdentityUserFlow;
use Microsoft\Graph\Generated\Models\UserFlowType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new B2xIdentityUserFlow();
$requestBody->setId('Partner');
$requestBody->setUserFlowType(new UserFlowType('signUpOrSignIn'));
$requestBody->setUserFlowTypeVersion(1);

$result = $graphServiceClient->identity()->b2xUserFlows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	id = "Partner"
	userFlowType = "signUpOrSignIn"
	userFlowTypeVersion = 1
}

New-MgIdentityB2XUserFlow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.b2x_identity_user_flow import B2xIdentityUserFlow
from msgraph.generated.models.user_flow_type import UserFlowType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = B2xIdentityUserFlow(
	id = "Partner",
	user_flow_type = UserFlowType.SignUpOrSignIn,
	user_flow_type_version = 1,
)

result = await graph_client.identity.b2x_user_flows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/identity/b2xUserFlows/B2X_1_Partner
Content-type: application/json

{
    "id": "B2X_1_Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1
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
POST https://graph.microsoft.com/v1.0/identity/b2xUserFlows
Content-type: application/json

{
    "id": "Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1,
    "identityProviders": [
        {
            "id": "Facebook-OAuth",
            "type": "Facebook",
            "name": "Facebook"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new B2xIdentityUserFlow
{
	Id = "Partner",
	UserFlowType = UserFlowType.SignUpOrSignIn,
	UserFlowTypeVersion = 1f,
	IdentityProviders = new List<IdentityProvider>
	{
		new IdentityProvider
		{
			Id = "Facebook-OAuth",
			Type = "Facebook",
			Name = "Facebook",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.B2xUserFlows.PostAsync(requestBody);
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

requestBody := graphmodels.NewB2xIdentityUserFlow()
id := "Partner"
requestBody.SetId(&id) 
userFlowType := graphmodels.SIGNUPORSIGNIN_USERFLOWTYPE 
requestBody.SetUserFlowType(&userFlowType) 
userFlowTypeVersion := float32(1)
requestBody.SetUserFlowTypeVersion(&userFlowTypeVersion) 


identityProvider := graphmodels.NewIdentityProvider()
id := "Facebook-OAuth"
identityProvider.SetId(&id) 
type := "Facebook"
identityProvider.SetType(&type) 
name := "Facebook"
identityProvider.SetName(&name) 

identityProviders := []graphmodels.IdentityProviderable {
	identityProvider,
}
requestBody.SetIdentityProviders(identityProviders)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
b2xUserFlows, err := graphClient.Identity().B2xUserFlows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

B2xIdentityUserFlow b2xIdentityUserFlow = new B2xIdentityUserFlow();
b2xIdentityUserFlow.setId("Partner");
b2xIdentityUserFlow.setUserFlowType(UserFlowType.SignUpOrSignIn);
b2xIdentityUserFlow.setUserFlowTypeVersion(1f);
LinkedList<IdentityProvider> identityProviders = new LinkedList<IdentityProvider>();
IdentityProvider identityProvider = new IdentityProvider();
identityProvider.setId("Facebook-OAuth");
identityProvider.setType("Facebook");
identityProvider.setName("Facebook");
identityProviders.add(identityProvider);
b2xIdentityUserFlow.setIdentityProviders(identityProviders);
B2xIdentityUserFlow result = graphClient.identity().b2xUserFlows().post(b2xIdentityUserFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2xIdentityUserFlow = {
    id: 'Partner',
    userFlowType: 'signUpOrSignIn',
    userFlowTypeVersion: 1,
    identityProviders: [
        {
            id: 'Facebook-OAuth',
            type: 'Facebook',
            name: 'Facebook'
        }
    ]
};

await client.api('/identity/b2xUserFlows')
	.post(b2xIdentityUserFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\B2xIdentityUserFlow;
use Microsoft\Graph\Generated\Models\UserFlowType;
use Microsoft\Graph\Generated\Models\IdentityProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new B2xIdentityUserFlow();
$requestBody->setId('Partner');
$requestBody->setUserFlowType(new UserFlowType('signUpOrSignIn'));
$requestBody->setUserFlowTypeVersion(1);
$identityProvidersIdentityProvider1 = new IdentityProvider();
$identityProvidersIdentityProvider1->setId('Facebook-OAuth');
$identityProvidersIdentityProvider1->setType('Facebook');
$identityProvidersIdentityProvider1->setName('Facebook');
$identityProvidersArray []= $identityProvidersIdentityProvider1;
$requestBody->setIdentityProviders($identityProvidersArray);


$result = $graphServiceClient->identity()->b2xUserFlows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	id = "Partner"
	userFlowType = "signUpOrSignIn"
	userFlowTypeVersion = 1
	identityProviders = @(
		@{
			id = "Facebook-OAuth"
			type = "Facebook"
			name = "Facebook"
		}
	)
}

New-MgIdentityB2XUserFlow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.b2x_identity_user_flow import B2xIdentityUserFlow
from msgraph.generated.models.user_flow_type import UserFlowType
from msgraph.generated.models.identity_provider import IdentityProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = B2xIdentityUserFlow(
	id = "Partner",
	user_flow_type = UserFlowType.SignUpOrSignIn,
	user_flow_type_version = 1,
	identity_providers = [
		IdentityProvider(
			id = "Facebook-OAuth",
			type = "Facebook",
			name = "Facebook",
		),
	],
)

result = await graph_client.identity.b2x_user_flows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/identity/b2xUserFlows/B2X_1_Partner
Content-type: application/json

{
    "id": "B2X_1_Partner",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1
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
POST https://graph.microsoft.com/v1.0/identity/b2xUserFlows
Content-type: application/json

{
    "id": "UserFlowWithAPIConnector",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1,
    "apiConnectorConfiguration":{
        "postFederationSignup":{
            "@odata.id": "https://graph.microsoft.com/v1/identity/apiConnectors/{id}"
        },
        "postAttributeCollection":{
            "@odata.id": "https://graph.microsoft.com/v1/identity/apiConnectors/{id}"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new B2xIdentityUserFlow
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
					"@odata.id" , "https://graph.microsoft.com/v1/identity/apiConnectors/{id}"
				},
			},
		},
		PostAttributeCollection = new IdentityApiConnector
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@odata.id" , "https://graph.microsoft.com/v1/identity/apiConnectors/{id}"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.B2xUserFlows.PostAsync(requestBody);
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

requestBody := graphmodels.NewB2xIdentityUserFlow()
id := "UserFlowWithAPIConnector"
requestBody.SetId(&id) 
userFlowType := graphmodels.SIGNUPORSIGNIN_USERFLOWTYPE 
requestBody.SetUserFlowType(&userFlowType) 
userFlowTypeVersion := float32(1)
requestBody.SetUserFlowTypeVersion(&userFlowTypeVersion) 
apiConnectorConfiguration := graphmodels.NewUserFlowApiConnectorConfiguration()
postFederationSignup := graphmodels.NewIdentityApiConnector()
additionalData := map[string]interface{}{
	"@odata.id" : "https://graph.microsoft.com/v1/identity/apiConnectors/{id}", 
}
postFederationSignup.SetAdditionalData(additionalData)
apiConnectorConfiguration.SetPostFederationSignup(postFederationSignup)
postAttributeCollection := graphmodels.NewIdentityApiConnector()
additionalData := map[string]interface{}{
	"@odata.id" : "https://graph.microsoft.com/v1/identity/apiConnectors/{id}", 
}
postAttributeCollection.SetAdditionalData(additionalData)
apiConnectorConfiguration.SetPostAttributeCollection(postAttributeCollection)
requestBody.SetApiConnectorConfiguration(apiConnectorConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
b2xUserFlows, err := graphClient.Identity().B2xUserFlows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

B2xIdentityUserFlow b2xIdentityUserFlow = new B2xIdentityUserFlow();
b2xIdentityUserFlow.setId("UserFlowWithAPIConnector");
b2xIdentityUserFlow.setUserFlowType(UserFlowType.SignUpOrSignIn);
b2xIdentityUserFlow.setUserFlowTypeVersion(1f);
UserFlowApiConnectorConfiguration apiConnectorConfiguration = new UserFlowApiConnectorConfiguration();
IdentityApiConnector postFederationSignup = new IdentityApiConnector();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.id", "https://graph.microsoft.com/v1/identity/apiConnectors/{id}");
postFederationSignup.setAdditionalData(additionalData);
apiConnectorConfiguration.setPostFederationSignup(postFederationSignup);
IdentityApiConnector postAttributeCollection = new IdentityApiConnector();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("@odata.id", "https://graph.microsoft.com/v1/identity/apiConnectors/{id}");
postAttributeCollection.setAdditionalData(additionalData1);
apiConnectorConfiguration.setPostAttributeCollection(postAttributeCollection);
b2xIdentityUserFlow.setApiConnectorConfiguration(apiConnectorConfiguration);
B2xIdentityUserFlow result = graphClient.identity().b2xUserFlows().post(b2xIdentityUserFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const b2xIdentityUserFlow = {
    id: 'UserFlowWithAPIConnector',
    userFlowType: 'signUpOrSignIn',
    userFlowTypeVersion: 1,
    apiConnectorConfiguration: {
        postFederationSignup: {
            '@odata.id': 'https://graph.microsoft.com/v1/identity/apiConnectors/{id}'
        },
        postAttributeCollection: {
            '@odata.id': 'https://graph.microsoft.com/v1/identity/apiConnectors/{id}'
        }
    }
};

await client.api('/identity/b2xUserFlows')
	.post(b2xIdentityUserFlow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\B2xIdentityUserFlow;
use Microsoft\Graph\Generated\Models\UserFlowType;
use Microsoft\Graph\Generated\Models\UserFlowApiConnectorConfiguration;
use Microsoft\Graph\Generated\Models\IdentityApiConnector;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new B2xIdentityUserFlow();
$requestBody->setId('UserFlowWithAPIConnector');
$requestBody->setUserFlowType(new UserFlowType('signUpOrSignIn'));
$requestBody->setUserFlowTypeVersion(1);
$apiConnectorConfiguration = new UserFlowApiConnectorConfiguration();
$apiConnectorConfigurationPostFederationSignup = new IdentityApiConnector();
$additionalData = [
	'@odata.id' => 'https://graph.microsoft.com/v1/identity/apiConnectors/{id}',
];
$apiConnectorConfigurationPostFederationSignup->setAdditionalData($additionalData);
$apiConnectorConfiguration->setPostFederationSignup($apiConnectorConfigurationPostFederationSignup);
$apiConnectorConfigurationPostAttributeCollection = new IdentityApiConnector();
$additionalData = [
	'@odata.id' => 'https://graph.microsoft.com/v1/identity/apiConnectors/{id}',
];
$apiConnectorConfigurationPostAttributeCollection->setAdditionalData($additionalData);
$apiConnectorConfiguration->setPostAttributeCollection($apiConnectorConfigurationPostAttributeCollection);
$requestBody->setApiConnectorConfiguration($apiConnectorConfiguration);

$result = $graphServiceClient->identity()->b2xUserFlows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	id = "UserFlowWithAPIConnector"
	userFlowType = "signUpOrSignIn"
	userFlowTypeVersion = 1
	apiConnectorConfiguration = @{
		postFederationSignup = @{
			"@odata.id" = "https://graph.microsoft.com/v1/identity/apiConnectors/{id}"
		}
		postAttributeCollection = @{
			"@odata.id" = "https://graph.microsoft.com/v1/identity/apiConnectors/{id}"
		}
	}
}

New-MgIdentityB2XUserFlow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.b2x_identity_user_flow import B2xIdentityUserFlow
from msgraph.generated.models.user_flow_type import UserFlowType
from msgraph.generated.models.user_flow_api_connector_configuration import UserFlowApiConnectorConfiguration
from msgraph.generated.models.identity_api_connector import IdentityApiConnector
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = B2xIdentityUserFlow(
	id = "UserFlowWithAPIConnector",
	user_flow_type = UserFlowType.SignUpOrSignIn,
	user_flow_type_version = 1,
	api_connector_configuration = UserFlowApiConnectorConfiguration(
		post_federation_signup = IdentityApiConnector(
			additional_data = {
					"@odata_id" : "https://graph.microsoft.com/v1/identity/apiConnectors/{id}",
			}
		),
		post_attribute_collection = IdentityApiConnector(
			additional_data = {
					"@odata_id" : "https://graph.microsoft.com/v1/identity/apiConnectors/{id}",
			}
		),
	),
)

result = await graph_client.identity.b2x_user_flows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

**Note:** The response object shown here might be shortened for readability.

**Note:** The `apiConnectorConfiguration` property always returns a '{}' value. To see full value with the navigation properties, use [this](https://learn.microsoft.com/en-us/graph/api/b2xidentityuserflow-get-apiconnectorconfiguration?view=graph-rest-1.0) API.

```http
HTTP/1.1 201 Created
Location: https://graph.microsoft.com/v1.0/identity/b2xUserFlows/B2X_1_Partner
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/b2xUserFlows/$entity",
    "id": "B2X_1_UserFlowWithAPIConnector",
    "userFlowType": "signUpOrSignIn",
    "userFlowTypeVersion": 1,
    "apiConnectorConfiguration": {}
}
```
