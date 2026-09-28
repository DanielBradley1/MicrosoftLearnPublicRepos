<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-authenticationeventlisteners?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create authenticationEventListener

Namespace: microsoft.graph

Create a new [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) object. You can create one of the following subtypes that are derived from **authenticationEventListener**.

- [onTokenIssuanceStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartlistener?view=graph-rest-1.0)
- [onInteractiveAuthFlowStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstartlistener?view=graph-rest-1.0)
- [onAuthenticationMethodLoadStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstartlistener?view=graph-rest-1.0)
- [onAttributeCollectionListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionlistener?view=graph-rest-1.0)
- [onUserCreateStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestartlistener?view=graph-rest-1.0)
- [onAttributeCollectionStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartlistener?view=graph-rest-1.0)
- [onAttributeCollectionSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitlistener?view=graph-rest-1.0)
- [onEmailOtpSendListener](https://learn.microsoft.com/en-us/graph/api/resources/onemailotpsendlistener?view=graph-rest-1.0)
- [onFraudProtectionLoadStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstartlistener?view=graph-rest-1.0) resource type
- [onPasswordSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitlistener?view=graph-rest-1.0) resource type

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EventListener.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EventListener.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Extensibility Administrator
- Application Administrator

## HTTP request

```http
POST /identity/authenticationEventListeners
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) object.

You can specify the following properties when creating an **authenticationEventListener**. You must specify the **@odata.type** property to specify the type of authenticationEventListener to create; for example, `@odata.type": "microsoft.graph.onTokenIssuanceStartListener"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | The conditions on which this authenticationEventListener should trigger. Optional. |
| displayName | String | The display name of the authentication event listener policy. Optional. |
| handler | [onTokenIssuanceStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestarthandler?view=graph-rest-1.0) or [onFraudProtectionLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstarthandler?view=graph-rest-1.0) | The handler to invoke when conditions are met. For **onTokenIssuanceStartListener**, set to [onTokenIssuanceStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestarthandler?view=graph-rest-1.0). For **onFraudProtectionLoadStartListener**, set to [onFraudProtectionLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstarthandler?view=graph-rest-1.0). |
| handler | [onPasswordSubmitHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmithandler?view=graph-rest-1.0) | The handler to invoke when conditions are met. Can be set for the **onPasswordSubmitListener** listener type. |

## Response

If successful, this method returns a `201 Created` response code and an [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) object in the response body. The **@odata.type** property specifies the type of the created object.

## Examples

### Example 1: Create authenticationEventListener

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
POST https://graph.microsoft.com/v1.0/identity/authenticationEventListeners
Content-Type: application/json
Content-length: 312

{
    "@odata.type": "#microsoft.graph.onTokenIssuanceStartListener",
    "conditions": {
        "applications": {
            "includeApplications": [
                {
                    "appId": "a13d0fc1-04ab-4ede-b215-63de0174cbb4"
                }
            ]
        }
    },
    "handler": {
        "@odata.type": "#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler",
        "customExtension": {
            "id": "6fc5012e-7665-43d6-9708-4370863f4e6e"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnTokenIssuanceStartListener
{
	OdataType = "#microsoft.graph.onTokenIssuanceStartListener",
	Conditions = new AuthenticationConditions
	{
		Applications = new AuthenticationConditionsApplications
		{
			IncludeApplications = new List<AuthenticationConditionApplication>
			{
				new AuthenticationConditionApplication
				{
					AppId = "a13d0fc1-04ab-4ede-b215-63de0174cbb4",
				},
			},
		},
	},
	Handler = new OnTokenIssuanceStartCustomExtensionHandler
	{
		OdataType = "#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler",
		CustomExtension = new OnTokenIssuanceStartCustomExtension
		{
			Id = "6fc5012e-7665-43d6-9708-4370863f4e6e",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventListeners.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationEventListener()
conditions := graphmodels.NewAuthenticationConditions()
applications := graphmodels.NewAuthenticationConditionsApplications()


authenticationConditionApplication := graphmodels.NewAuthenticationConditionApplication()
appId := "a13d0fc1-04ab-4ede-b215-63de0174cbb4"
authenticationConditionApplication.SetAppId(&appId) 

includeApplications := []graphmodels.AuthenticationConditionApplicationable {
	authenticationConditionApplication,
}
applications.SetIncludeApplications(includeApplications)
conditions.SetApplications(applications)
requestBody.SetConditions(conditions)
handler := graphmodels.NewOnTokenIssuanceStartCustomExtensionHandler()
customExtension := graphmodels.NewOnTokenIssuanceStartCustomExtension()
id := "6fc5012e-7665-43d6-9708-4370863f4e6e"
customExtension.SetId(&id) 
handler.SetCustomExtension(customExtension)
requestBody.SetHandler(handler)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventListeners, err := graphClient.Identity().AuthenticationEventListeners().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnTokenIssuanceStartListener authenticationEventListener = new OnTokenIssuanceStartListener();
authenticationEventListener.setOdataType("#microsoft.graph.onTokenIssuanceStartListener");
AuthenticationConditions conditions = new AuthenticationConditions();
AuthenticationConditionsApplications applications = new AuthenticationConditionsApplications();
LinkedList<AuthenticationConditionApplication> includeApplications = new LinkedList<AuthenticationConditionApplication>();
AuthenticationConditionApplication authenticationConditionApplication = new AuthenticationConditionApplication();
authenticationConditionApplication.setAppId("a13d0fc1-04ab-4ede-b215-63de0174cbb4");
includeApplications.add(authenticationConditionApplication);
applications.setIncludeApplications(includeApplications);
conditions.setApplications(applications);
authenticationEventListener.setConditions(conditions);
OnTokenIssuanceStartCustomExtensionHandler handler = new OnTokenIssuanceStartCustomExtensionHandler();
handler.setOdataType("#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler");
OnTokenIssuanceStartCustomExtension customExtension = new OnTokenIssuanceStartCustomExtension();
customExtension.setId("6fc5012e-7665-43d6-9708-4370863f4e6e");
handler.setCustomExtension(customExtension);
authenticationEventListener.setHandler(handler);
AuthenticationEventListener result = graphClient.identity().authenticationEventListeners().post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventListener = {
    '@odata.type': '#microsoft.graph.onTokenIssuanceStartListener',
    conditions: {
        applications: {
            includeApplications: [
                {
                    appId: 'a13d0fc1-04ab-4ede-b215-63de0174cbb4'
                }
            ]
        }
    },
    handler: {
        '@odata.type': '#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler',
        customExtension: {
            id: '6fc5012e-7665-43d6-9708-4370863f4e6e'
        }
    }
};

await client.api('/identity/authenticationEventListeners')
	.post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnTokenIssuanceStartListener;
use Microsoft\Graph\Generated\Models\AuthenticationConditions;
use Microsoft\Graph\Generated\Models\AuthenticationConditionsApplications;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;
use Microsoft\Graph\Generated\Models\OnTokenIssuanceStartCustomExtensionHandler;
use Microsoft\Graph\Generated\Models\OnTokenIssuanceStartCustomExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnTokenIssuanceStartListener();
$requestBody->setOdataType('#microsoft.graph.onTokenIssuanceStartListener');
$conditions = new AuthenticationConditions();
$conditionsApplications = new AuthenticationConditionsApplications();
$includeApplicationsAuthenticationConditionApplication1 = new AuthenticationConditionApplication();
$includeApplicationsAuthenticationConditionApplication1->setAppId('a13d0fc1-04ab-4ede-b215-63de0174cbb4');
$includeApplicationsArray []= $includeApplicationsAuthenticationConditionApplication1;
$conditionsApplications->setIncludeApplications($includeApplicationsArray);

$conditions->setApplications($conditionsApplications);
$requestBody->setConditions($conditions);
$handler = new OnTokenIssuanceStartCustomExtensionHandler();
$handler->setOdataType('#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler');
$handlerCustomExtension = new OnTokenIssuanceStartCustomExtension();
$handlerCustomExtension->setId('6fc5012e-7665-43d6-9708-4370863f4e6e');
$handler->setCustomExtension($handlerCustomExtension);
$requestBody->setHandler($handler);

$result = $graphServiceClient->identity()->authenticationEventListeners()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onTokenIssuanceStartListener"
	conditions = @{
		applications = @{
			includeApplications = @(
				@{
					appId = "a13d0fc1-04ab-4ede-b215-63de0174cbb4"
				}
			)
		}
	}
	handler = @{
		"@odata.type" = "#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler"
		customExtension = @{
			id = "6fc5012e-7665-43d6-9708-4370863f4e6e"
		}
	}
}

New-MgIdentityAuthenticationEventListener -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_token_issuance_start_listener import OnTokenIssuanceStartListener
from msgraph.generated.models.authentication_conditions import AuthenticationConditions
from msgraph.generated.models.authentication_conditions_applications import AuthenticationConditionsApplications
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
from msgraph.generated.models.on_token_issuance_start_custom_extension_handler import OnTokenIssuanceStartCustomExtensionHandler
from msgraph.generated.models.on_token_issuance_start_custom_extension import OnTokenIssuanceStartCustomExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnTokenIssuanceStartListener(
	odata_type = "#microsoft.graph.onTokenIssuanceStartListener",
	conditions = AuthenticationConditions(
		applications = AuthenticationConditionsApplications(
			include_applications = [
				AuthenticationConditionApplication(
					app_id = "a13d0fc1-04ab-4ede-b215-63de0174cbb4",
				),
			],
		),
	),
	handler = OnTokenIssuanceStartCustomExtensionHandler(
		odata_type = "#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler",
		custom_extension = OnTokenIssuanceStartCustomExtension(
			id = "6fc5012e-7665-43d6-9708-4370863f4e6e",
		),
	),
)

result = await graph_client.identity.authentication_event_listeners.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventListeners/$entity",
    "@odata.type": "#microsoft.graph.onTokenIssuanceStartListener",
    "id": "990d94e5-cc8f-4c4b-97b4-27e2678aac28",
    "conditions": {
        "applications": {
            "includeApplications": [
                {
                    "appId": "a13d0fc1-04ab-4ede-b215-63de0174cbb4"
                }
            ]
        }
    },
    "handler": {
        "@odata.type": "#microsoft.graph.onTokenIssuanceStartCustomExtensionHandler",
        "customExtension": {
            "id": "6fc5012e-7665-43d6-9708-4370863f4e6e"
        }
    }
}
```

### Example 2: Enable Fraud Protection during sign-up with Arkose Labs

#### Request

The following example shows a request that enables fraud protection during sign-up using Arkose Labs.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identity/authenticationEventListeners
Content-Type: application/json

{   
  "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartListener", 
  "conditions": { 
    "applications": { 
      "includeApplications": [ 
        { 
          "appId": "0001111-aaaa-2222-bbbb-3333cccc4444" 
        } 
      ] 
    } 
  }, 
  "handler": { 
    "@odata.type": 
"#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler", 
    "signUp": { 
      "@odata.type": "#microsoft.graph.fraudProtectionProviderConfiguration", 
      "fraudProtectionProvider": { 
        "@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider", 
        "id": "6fedd01b-0afb-4a07-967f-d1ccbd81102b" 
      } 
    } 
  } 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnFraudProtectionLoadStartListener
{
	OdataType = "#microsoft.graph.onFraudProtectionLoadStartListener",
	Conditions = new AuthenticationConditions
	{
		Applications = new AuthenticationConditionsApplications
		{
			IncludeApplications = new List<AuthenticationConditionApplication>
			{
				new AuthenticationConditionApplication
				{
					AppId = "0001111-aaaa-2222-bbbb-3333cccc4444",
				},
			},
		},
	},
	Handler = new OnFraudProtectionLoadStartExternalUsersAuthHandler
	{
		OdataType = "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler",
		SignUp = new FraudProtectionProviderConfiguration
		{
			OdataType = "#microsoft.graph.fraudProtectionProviderConfiguration",
			FraudProtectionProvider = new ArkoseFraudProtectionProvider
			{
				OdataType = "#microsoft.graph.arkoseFraudProtectionProvider",
				Id = "6fedd01b-0afb-4a07-967f-d1ccbd81102b",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventListeners.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationEventListener()
conditions := graphmodels.NewAuthenticationConditions()
applications := graphmodels.NewAuthenticationConditionsApplications()


authenticationConditionApplication := graphmodels.NewAuthenticationConditionApplication()
appId := "0001111-aaaa-2222-bbbb-3333cccc4444"
authenticationConditionApplication.SetAppId(&appId) 

includeApplications := []graphmodels.AuthenticationConditionApplicationable {
	authenticationConditionApplication,
}
applications.SetIncludeApplications(includeApplications)
conditions.SetApplications(applications)
requestBody.SetConditions(conditions)
handler := graphmodels.NewOnFraudProtectionLoadStartExternalUsersAuthHandler()
signUp := graphmodels.NewFraudProtectionProviderConfiguration()
fraudProtectionProvider := graphmodels.NewArkoseFraudProtectionProvider()
id := "6fedd01b-0afb-4a07-967f-d1ccbd81102b"
fraudProtectionProvider.SetId(&id) 
signUp.SetFraudProtectionProvider(fraudProtectionProvider)
handler.SetSignUp(signUp)
requestBody.SetHandler(handler)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventListeners, err := graphClient.Identity().AuthenticationEventListeners().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnFraudProtectionLoadStartListener authenticationEventListener = new OnFraudProtectionLoadStartListener();
authenticationEventListener.setOdataType("#microsoft.graph.onFraudProtectionLoadStartListener");
AuthenticationConditions conditions = new AuthenticationConditions();
AuthenticationConditionsApplications applications = new AuthenticationConditionsApplications();
LinkedList<AuthenticationConditionApplication> includeApplications = new LinkedList<AuthenticationConditionApplication>();
AuthenticationConditionApplication authenticationConditionApplication = new AuthenticationConditionApplication();
authenticationConditionApplication.setAppId("0001111-aaaa-2222-bbbb-3333cccc4444");
includeApplications.add(authenticationConditionApplication);
applications.setIncludeApplications(includeApplications);
conditions.setApplications(applications);
authenticationEventListener.setConditions(conditions);
OnFraudProtectionLoadStartExternalUsersAuthHandler handler = new OnFraudProtectionLoadStartExternalUsersAuthHandler();
handler.setOdataType("#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler");
FraudProtectionProviderConfiguration signUp = new FraudProtectionProviderConfiguration();
signUp.setOdataType("#microsoft.graph.fraudProtectionProviderConfiguration");
ArkoseFraudProtectionProvider fraudProtectionProvider = new ArkoseFraudProtectionProvider();
fraudProtectionProvider.setOdataType("#microsoft.graph.arkoseFraudProtectionProvider");
fraudProtectionProvider.setId("6fedd01b-0afb-4a07-967f-d1ccbd81102b");
signUp.setFraudProtectionProvider(fraudProtectionProvider);
handler.setSignUp(signUp);
authenticationEventListener.setHandler(handler);
AuthenticationEventListener result = graphClient.identity().authenticationEventListeners().post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventListener = {
  '@odata.type': '#microsoft.graph.onFraudProtectionLoadStartListener', 
  conditions: { 
    applications: { 
      includeApplications: [ 
        { 
          appId: '0001111-aaaa-2222-bbbb-3333cccc4444' 
        } 
      ] 
    } 
  }, 
  handler: { 
    '@odata.type': 
'#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler', 
    signUp: { 
      '@odata.type': '#microsoft.graph.fraudProtectionProviderConfiguration', 
      fraudProtectionProvider: { 
        '@odata.type': '#microsoft.graph.arkoseFraudProtectionProvider', 
        id: '6fedd01b-0afb-4a07-967f-d1ccbd81102b' 
      } 
    } 
  } 
};

await client.api('/identity/authenticationEventListeners')
	.post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnFraudProtectionLoadStartListener;
use Microsoft\Graph\Generated\Models\AuthenticationConditions;
use Microsoft\Graph\Generated\Models\AuthenticationConditionsApplications;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;
use Microsoft\Graph\Generated\Models\OnFraudProtectionLoadStartExternalUsersAuthHandler;
use Microsoft\Graph\Generated\Models\FraudProtectionProviderConfiguration;
use Microsoft\Graph\Generated\Models\ArkoseFraudProtectionProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnFraudProtectionLoadStartListener();
$requestBody->setOdataType('#microsoft.graph.onFraudProtectionLoadStartListener');
$conditions = new AuthenticationConditions();
$conditionsApplications = new AuthenticationConditionsApplications();
$includeApplicationsAuthenticationConditionApplication1 = new AuthenticationConditionApplication();
$includeApplicationsAuthenticationConditionApplication1->setAppId('0001111-aaaa-2222-bbbb-3333cccc4444');
$includeApplicationsArray []= $includeApplicationsAuthenticationConditionApplication1;
$conditionsApplications->setIncludeApplications($includeApplicationsArray);

$conditions->setApplications($conditionsApplications);
$requestBody->setConditions($conditions);
$handler = new OnFraudProtectionLoadStartExternalUsersAuthHandler();
$handler->setOdataType('#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler');
$handlerSignUp = new FraudProtectionProviderConfiguration();
$handlerSignUp->setOdataType('#microsoft.graph.fraudProtectionProviderConfiguration');
$handlerSignUpFraudProtectionProvider = new ArkoseFraudProtectionProvider();
$handlerSignUpFraudProtectionProvider->setOdataType('#microsoft.graph.arkoseFraudProtectionProvider');
$handlerSignUpFraudProtectionProvider->setId('6fedd01b-0afb-4a07-967f-d1ccbd81102b');
$handlerSignUp->setFraudProtectionProvider($handlerSignUpFraudProtectionProvider);
$handler->setSignUp($handlerSignUp);
$requestBody->setHandler($handler);

$result = $graphServiceClient->identity()->authenticationEventListeners()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onFraudProtectionLoadStartListener"
	conditions = @{
		applications = @{
			includeApplications = @(
				@{
					appId = "0001111-aaaa-2222-bbbb-3333cccc4444"
				}
			)
		}
	}
	handler = @{
		"@odata.type" = "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler"
		signUp = @{
			"@odata.type" = "#microsoft.graph.fraudProtectionProviderConfiguration"
			fraudProtectionProvider = @{
				"@odata.type" = "#microsoft.graph.arkoseFraudProtectionProvider"
				id = "6fedd01b-0afb-4a07-967f-d1ccbd81102b"
			}
		}
	}
}

New-MgIdentityAuthenticationEventListener -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_fraud_protection_load_start_listener import OnFraudProtectionLoadStartListener
from msgraph.generated.models.authentication_conditions import AuthenticationConditions
from msgraph.generated.models.authentication_conditions_applications import AuthenticationConditionsApplications
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
from msgraph.generated.models.on_fraud_protection_load_start_external_users_auth_handler import OnFraudProtectionLoadStartExternalUsersAuthHandler
from msgraph.generated.models.fraud_protection_provider_configuration import FraudProtectionProviderConfiguration
from msgraph.generated.models.arkose_fraud_protection_provider import ArkoseFraudProtectionProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnFraudProtectionLoadStartListener(
	odata_type = "#microsoft.graph.onFraudProtectionLoadStartListener",
	conditions = AuthenticationConditions(
		applications = AuthenticationConditionsApplications(
			include_applications = [
				AuthenticationConditionApplication(
					app_id = "0001111-aaaa-2222-bbbb-3333cccc4444",
				),
			],
		),
	),
	handler = OnFraudProtectionLoadStartExternalUsersAuthHandler(
		odata_type = "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler",
		sign_up = FraudProtectionProviderConfiguration(
			odata_type = "#microsoft.graph.fraudProtectionProviderConfiguration",
			fraud_protection_provider = ArkoseFraudProtectionProvider(
				odata_type = "#microsoft.graph.arkoseFraudProtectionProvider",
				id = "6fedd01b-0afb-4a07-967f-d1ccbd81102b",
			),
		),
	),
)

result = await graph_client.identity.authentication_event_listeners.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventListeners/$entity",
  "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartListener",
  "id": "49eb23d9-998b-47df-a462-aa12a20ae5fb",
  "conditions": {
    "applications": {
      "includeApplications": [
        {
          "appId": "0001111-aaaa-2222-bbbb-3333cccc4444"
        }
      ]
    }
  },
  "handler": {
    "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler",
    "signUp": {
      "fraudProtectionProvider": {
        "@odata.type": "#microsoft.graph.arkoseFraudProtectionProvider",
        "id": "fabe5100-cc02-46c1-bd0e-ce885fe367fd"
      }
    }
  }
}
```

### Example 3: Enable Fraud Protection during sign-up with HUMAN Security

#### Request

The following example shows a request that enables fraud protection during sign-up using HUMAN Security.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identity/authenticationEventListeners
Content-Type: application/json

{   
  "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartListener", 
  "conditions": { 
    "applications": { 
      "includeApplications": [ 
        { 
          "appId": "0001111-aaaa-2222-bbbb-3333cccc4444" 
        } 
      ] 
    } 
  }, 
  "handler": { 
    "@odata.type": 
"#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler", 
    "signUp": { 
      "@odata.type": "#microsoft.graph.fraudProtectionProviderConfiguration", 
      "fraudProtectionProvider": { 
        "@odata.type": "#microsoft.graph.humanSecurityFraudProtectionProvider", 
        "id": "fabe5100-cc02-46c1-bd0e-ce885fe367fd" 
      } 
    } 
  } 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnFraudProtectionLoadStartListener
{
	OdataType = "#microsoft.graph.onFraudProtectionLoadStartListener",
	Conditions = new AuthenticationConditions
	{
		Applications = new AuthenticationConditionsApplications
		{
			IncludeApplications = new List<AuthenticationConditionApplication>
			{
				new AuthenticationConditionApplication
				{
					AppId = "0001111-aaaa-2222-bbbb-3333cccc4444",
				},
			},
		},
	},
	Handler = new OnFraudProtectionLoadStartExternalUsersAuthHandler
	{
		OdataType = "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler",
		SignUp = new FraudProtectionProviderConfiguration
		{
			OdataType = "#microsoft.graph.fraudProtectionProviderConfiguration",
			FraudProtectionProvider = new HumanSecurityFraudProtectionProvider
			{
				OdataType = "#microsoft.graph.humanSecurityFraudProtectionProvider",
				Id = "fabe5100-cc02-46c1-bd0e-ce885fe367fd",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventListeners.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationEventListener()
conditions := graphmodels.NewAuthenticationConditions()
applications := graphmodels.NewAuthenticationConditionsApplications()


authenticationConditionApplication := graphmodels.NewAuthenticationConditionApplication()
appId := "0001111-aaaa-2222-bbbb-3333cccc4444"
authenticationConditionApplication.SetAppId(&appId) 

includeApplications := []graphmodels.AuthenticationConditionApplicationable {
	authenticationConditionApplication,
}
applications.SetIncludeApplications(includeApplications)
conditions.SetApplications(applications)
requestBody.SetConditions(conditions)
handler := graphmodels.NewOnFraudProtectionLoadStartExternalUsersAuthHandler()
signUp := graphmodels.NewFraudProtectionProviderConfiguration()
fraudProtectionProvider := graphmodels.NewHumanSecurityFraudProtectionProvider()
id := "fabe5100-cc02-46c1-bd0e-ce885fe367fd"
fraudProtectionProvider.SetId(&id) 
signUp.SetFraudProtectionProvider(fraudProtectionProvider)
handler.SetSignUp(signUp)
requestBody.SetHandler(handler)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventListeners, err := graphClient.Identity().AuthenticationEventListeners().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnFraudProtectionLoadStartListener authenticationEventListener = new OnFraudProtectionLoadStartListener();
authenticationEventListener.setOdataType("#microsoft.graph.onFraudProtectionLoadStartListener");
AuthenticationConditions conditions = new AuthenticationConditions();
AuthenticationConditionsApplications applications = new AuthenticationConditionsApplications();
LinkedList<AuthenticationConditionApplication> includeApplications = new LinkedList<AuthenticationConditionApplication>();
AuthenticationConditionApplication authenticationConditionApplication = new AuthenticationConditionApplication();
authenticationConditionApplication.setAppId("0001111-aaaa-2222-bbbb-3333cccc4444");
includeApplications.add(authenticationConditionApplication);
applications.setIncludeApplications(includeApplications);
conditions.setApplications(applications);
authenticationEventListener.setConditions(conditions);
OnFraudProtectionLoadStartExternalUsersAuthHandler handler = new OnFraudProtectionLoadStartExternalUsersAuthHandler();
handler.setOdataType("#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler");
FraudProtectionProviderConfiguration signUp = new FraudProtectionProviderConfiguration();
signUp.setOdataType("#microsoft.graph.fraudProtectionProviderConfiguration");
HumanSecurityFraudProtectionProvider fraudProtectionProvider = new HumanSecurityFraudProtectionProvider();
fraudProtectionProvider.setOdataType("#microsoft.graph.humanSecurityFraudProtectionProvider");
fraudProtectionProvider.setId("fabe5100-cc02-46c1-bd0e-ce885fe367fd");
signUp.setFraudProtectionProvider(fraudProtectionProvider);
handler.setSignUp(signUp);
authenticationEventListener.setHandler(handler);
AuthenticationEventListener result = graphClient.identity().authenticationEventListeners().post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventListener = {
  '@odata.type': '#microsoft.graph.onFraudProtectionLoadStartListener', 
  conditions: { 
    applications: { 
      includeApplications: [ 
        { 
          appId: '0001111-aaaa-2222-bbbb-3333cccc4444' 
        } 
      ] 
    } 
  }, 
  handler: { 
    '@odata.type': 
'#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler', 
    signUp: { 
      '@odata.type': '#microsoft.graph.fraudProtectionProviderConfiguration', 
      fraudProtectionProvider: { 
        '@odata.type': '#microsoft.graph.humanSecurityFraudProtectionProvider', 
        id: 'fabe5100-cc02-46c1-bd0e-ce885fe367fd' 
      } 
    } 
  } 
};

await client.api('/identity/authenticationEventListeners')
	.post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnFraudProtectionLoadStartListener;
use Microsoft\Graph\Generated\Models\AuthenticationConditions;
use Microsoft\Graph\Generated\Models\AuthenticationConditionsApplications;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;
use Microsoft\Graph\Generated\Models\OnFraudProtectionLoadStartExternalUsersAuthHandler;
use Microsoft\Graph\Generated\Models\FraudProtectionProviderConfiguration;
use Microsoft\Graph\Generated\Models\HumanSecurityFraudProtectionProvider;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnFraudProtectionLoadStartListener();
$requestBody->setOdataType('#microsoft.graph.onFraudProtectionLoadStartListener');
$conditions = new AuthenticationConditions();
$conditionsApplications = new AuthenticationConditionsApplications();
$includeApplicationsAuthenticationConditionApplication1 = new AuthenticationConditionApplication();
$includeApplicationsAuthenticationConditionApplication1->setAppId('0001111-aaaa-2222-bbbb-3333cccc4444');
$includeApplicationsArray []= $includeApplicationsAuthenticationConditionApplication1;
$conditionsApplications->setIncludeApplications($includeApplicationsArray);

$conditions->setApplications($conditionsApplications);
$requestBody->setConditions($conditions);
$handler = new OnFraudProtectionLoadStartExternalUsersAuthHandler();
$handler->setOdataType('#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler');
$handlerSignUp = new FraudProtectionProviderConfiguration();
$handlerSignUp->setOdataType('#microsoft.graph.fraudProtectionProviderConfiguration');
$handlerSignUpFraudProtectionProvider = new HumanSecurityFraudProtectionProvider();
$handlerSignUpFraudProtectionProvider->setOdataType('#microsoft.graph.humanSecurityFraudProtectionProvider');
$handlerSignUpFraudProtectionProvider->setId('fabe5100-cc02-46c1-bd0e-ce885fe367fd');
$handlerSignUp->setFraudProtectionProvider($handlerSignUpFraudProtectionProvider);
$handler->setSignUp($handlerSignUp);
$requestBody->setHandler($handler);

$result = $graphServiceClient->identity()->authenticationEventListeners()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onFraudProtectionLoadStartListener"
	conditions = @{
		applications = @{
			includeApplications = @(
				@{
					appId = "0001111-aaaa-2222-bbbb-3333cccc4444"
				}
			)
		}
	}
	handler = @{
		"@odata.type" = "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler"
		signUp = @{
			"@odata.type" = "#microsoft.graph.fraudProtectionProviderConfiguration"
			fraudProtectionProvider = @{
				"@odata.type" = "#microsoft.graph.humanSecurityFraudProtectionProvider"
				id = "fabe5100-cc02-46c1-bd0e-ce885fe367fd"
			}
		}
	}
}

New-MgIdentityAuthenticationEventListener -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_fraud_protection_load_start_listener import OnFraudProtectionLoadStartListener
from msgraph.generated.models.authentication_conditions import AuthenticationConditions
from msgraph.generated.models.authentication_conditions_applications import AuthenticationConditionsApplications
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
from msgraph.generated.models.on_fraud_protection_load_start_external_users_auth_handler import OnFraudProtectionLoadStartExternalUsersAuthHandler
from msgraph.generated.models.fraud_protection_provider_configuration import FraudProtectionProviderConfiguration
from msgraph.generated.models.human_security_fraud_protection_provider import HumanSecurityFraudProtectionProvider
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnFraudProtectionLoadStartListener(
	odata_type = "#microsoft.graph.onFraudProtectionLoadStartListener",
	conditions = AuthenticationConditions(
		applications = AuthenticationConditionsApplications(
			include_applications = [
				AuthenticationConditionApplication(
					app_id = "0001111-aaaa-2222-bbbb-3333cccc4444",
				),
			],
		),
	),
	handler = OnFraudProtectionLoadStartExternalUsersAuthHandler(
		odata_type = "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler",
		sign_up = FraudProtectionProviderConfiguration(
			odata_type = "#microsoft.graph.fraudProtectionProviderConfiguration",
			fraud_protection_provider = HumanSecurityFraudProtectionProvider(
				odata_type = "#microsoft.graph.humanSecurityFraudProtectionProvider",
				id = "fabe5100-cc02-46c1-bd0e-ce885fe367fd",
			),
		),
	),
)

result = await graph_client.identity.authentication_event_listeners.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventListeners/$entity",
  "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartListener",
  "id": "49eb23d9-998b-47df-a462-aa12a20ae5fb",
  "conditions": {
    "applications": {
      "includeApplications": [
        {
          "appId": "0001111-aaaa-2222-bbbb-3333cccc4444"
        }
      ]
    }
  },
  "handler": {
    "@odata.type": "#microsoft.graph.onFraudProtectionLoadStartExternalUsersAuthHandler",
    "signUp": {
      "isContinueOnProviderErrorEnabled": false,
      "fraudProtectionProvider": {
        "@odata.type": "#microsoft.graph.humanSecurityFraudProtectionProvider",
        "id": "fabe5100-cc02-46c1-bd0e-ce885fe367fd"
      }
    }
  }
}
```

### Example 4: Create an onPasswordSubmitListener object

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
POST https://graph.microsoft.com/v1.0/identity/authenticationEventListeners
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onPasswordSubmitListener",
  "displayName": "JIT migration listener",
  "conditions": {
    "applications": {
      "includeAllApplications": false,
      "includeApplications": [
        {
          "appId": "00011111-aaaa-2222-bbbb-3333cccc4444"
        }
      ]
    }
  },
  "handler": {
    "@odata.type": "#microsoft.graph.onPasswordMigrationCustomExtensionHandler",
    "migrationPropertyId": "extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration",
    "customExtension": {
      "id": "6fc5012e-7665-43d6-9708-4370863f4e6e"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnPasswordSubmitListener
{
	OdataType = "#microsoft.graph.onPasswordSubmitListener",
	DisplayName = "JIT migration listener",
	Conditions = new AuthenticationConditions
	{
		Applications = new AuthenticationConditionsApplications
		{
			IncludeApplications = new List<AuthenticationConditionApplication>
			{
				new AuthenticationConditionApplication
				{
					AppId = "00011111-aaaa-2222-bbbb-3333cccc4444",
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"includeAllApplications" , false
				},
			},
		},
	},
	Handler = new OnPasswordMigrationCustomExtensionHandler
	{
		OdataType = "#microsoft.graph.onPasswordMigrationCustomExtensionHandler",
		MigrationPropertyId = "extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration",
		CustomExtension = new OnPasswordSubmitCustomExtension
		{
			Id = "6fc5012e-7665-43d6-9708-4370863f4e6e",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventListeners.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationEventListener()
displayName := "JIT migration listener"
requestBody.SetDisplayName(&displayName) 
conditions := graphmodels.NewAuthenticationConditions()
applications := graphmodels.NewAuthenticationConditionsApplications()


authenticationConditionApplication := graphmodels.NewAuthenticationConditionApplication()
appId := "00011111-aaaa-2222-bbbb-3333cccc4444"
authenticationConditionApplication.SetAppId(&appId) 

includeApplications := []graphmodels.AuthenticationConditionApplicationable {
	authenticationConditionApplication,
}
applications.SetIncludeApplications(includeApplications)
additionalData := map[string]interface{}{
	includeAllApplications := false
applications.SetIncludeAllApplications(&includeAllApplications) 
}
applications.SetAdditionalData(additionalData)
conditions.SetApplications(applications)
requestBody.SetConditions(conditions)
handler := graphmodels.NewOnPasswordMigrationCustomExtensionHandler()
migrationPropertyId := "extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration"
handler.SetMigrationPropertyId(&migrationPropertyId) 
customExtension := graphmodels.NewOnPasswordSubmitCustomExtension()
id := "6fc5012e-7665-43d6-9708-4370863f4e6e"
customExtension.SetId(&id) 
handler.SetCustomExtension(customExtension)
requestBody.SetHandler(handler)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventListeners, err := graphClient.Identity().AuthenticationEventListeners().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnPasswordSubmitListener authenticationEventListener = new OnPasswordSubmitListener();
authenticationEventListener.setOdataType("#microsoft.graph.onPasswordSubmitListener");
authenticationEventListener.setDisplayName("JIT migration listener");
AuthenticationConditions conditions = new AuthenticationConditions();
AuthenticationConditionsApplications applications = new AuthenticationConditionsApplications();
LinkedList<AuthenticationConditionApplication> includeApplications = new LinkedList<AuthenticationConditionApplication>();
AuthenticationConditionApplication authenticationConditionApplication = new AuthenticationConditionApplication();
authenticationConditionApplication.setAppId("00011111-aaaa-2222-bbbb-3333cccc4444");
includeApplications.add(authenticationConditionApplication);
applications.setIncludeApplications(includeApplications);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("includeAllApplications", false);
applications.setAdditionalData(additionalData);
conditions.setApplications(applications);
authenticationEventListener.setConditions(conditions);
OnPasswordMigrationCustomExtensionHandler handler = new OnPasswordMigrationCustomExtensionHandler();
handler.setOdataType("#microsoft.graph.onPasswordMigrationCustomExtensionHandler");
handler.setMigrationPropertyId("extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration");
OnPasswordSubmitCustomExtension customExtension = new OnPasswordSubmitCustomExtension();
customExtension.setId("6fc5012e-7665-43d6-9708-4370863f4e6e");
handler.setCustomExtension(customExtension);
authenticationEventListener.setHandler(handler);
AuthenticationEventListener result = graphClient.identity().authenticationEventListeners().post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventListener = {
  '@odata.type': '#microsoft.graph.onPasswordSubmitListener',
  displayName: 'JIT migration listener',
  conditions: {
    applications: {
      includeAllApplications: false,
      includeApplications: [
        {
          appId: '00011111-aaaa-2222-bbbb-3333cccc4444'
        }
      ]
    }
  },
  handler: {
    '@odata.type': '#microsoft.graph.onPasswordMigrationCustomExtensionHandler',
    migrationPropertyId: 'extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration',
    customExtension: {
      id: '6fc5012e-7665-43d6-9708-4370863f4e6e'
    }
  }
};

await client.api('/identity/authenticationEventListeners')
	.post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnPasswordSubmitListener;
use Microsoft\Graph\Generated\Models\AuthenticationConditions;
use Microsoft\Graph\Generated\Models\AuthenticationConditionsApplications;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;
use Microsoft\Graph\Generated\Models\OnPasswordMigrationCustomExtensionHandler;
use Microsoft\Graph\Generated\Models\OnPasswordSubmitCustomExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnPasswordSubmitListener();
$requestBody->setOdataType('#microsoft.graph.onPasswordSubmitListener');
$requestBody->setDisplayName('JIT migration listener');
$conditions = new AuthenticationConditions();
$conditionsApplications = new AuthenticationConditionsApplications();
$includeApplicationsAuthenticationConditionApplication1 = new AuthenticationConditionApplication();
$includeApplicationsAuthenticationConditionApplication1->setAppId('00011111-aaaa-2222-bbbb-3333cccc4444');
$includeApplicationsArray []= $includeApplicationsAuthenticationConditionApplication1;
$conditionsApplications->setIncludeApplications($includeApplicationsArray);

$additionalData = [
'includeAllApplications' => false,
];
$conditionsApplications->setAdditionalData($additionalData);
$conditions->setApplications($conditionsApplications);
$requestBody->setConditions($conditions);
$handler = new OnPasswordMigrationCustomExtensionHandler();
$handler->setOdataType('#microsoft.graph.onPasswordMigrationCustomExtensionHandler');
$handler->setMigrationPropertyId('extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration');
$handlerCustomExtension = new OnPasswordSubmitCustomExtension();
$handlerCustomExtension->setId('6fc5012e-7665-43d6-9708-4370863f4e6e');
$handler->setCustomExtension($handlerCustomExtension);
$requestBody->setHandler($handler);

$result = $graphServiceClient->identity()->authenticationEventListeners()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onPasswordSubmitListener"
	displayName = "JIT migration listener"
	conditions = @{
		applications = @{
			includeAllApplications = $false
			includeApplications = @(
				@{
					appId = "00011111-aaaa-2222-bbbb-3333cccc4444"
				}
			)
		}
	}
	handler = @{
		"@odata.type" = "#microsoft.graph.onPasswordMigrationCustomExtensionHandler"
		migrationPropertyId = "extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration"
		customExtension = @{
			id = "6fc5012e-7665-43d6-9708-4370863f4e6e"
		}
	}
}

New-MgIdentityAuthenticationEventListener -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_password_submit_listener import OnPasswordSubmitListener
from msgraph.generated.models.authentication_conditions import AuthenticationConditions
from msgraph.generated.models.authentication_conditions_applications import AuthenticationConditionsApplications
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
from msgraph.generated.models.on_password_migration_custom_extension_handler import OnPasswordMigrationCustomExtensionHandler
from msgraph.generated.models.on_password_submit_custom_extension import OnPasswordSubmitCustomExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnPasswordSubmitListener(
	odata_type = "#microsoft.graph.onPasswordSubmitListener",
	display_name = "JIT migration listener",
	conditions = AuthenticationConditions(
		applications = AuthenticationConditionsApplications(
			include_applications = [
				AuthenticationConditionApplication(
					app_id = "00011111-aaaa-2222-bbbb-3333cccc4444",
				),
			],
			additional_data = {
					"include_all_applications" : False,
			}
		),
	),
	handler = OnPasswordMigrationCustomExtensionHandler(
		odata_type = "#microsoft.graph.onPasswordMigrationCustomExtensionHandler",
		migration_property_id = "extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration",
		custom_extension = OnPasswordSubmitCustomExtension(
			id = "6fc5012e-7665-43d6-9708-4370863f4e6e",
		),
	),
)

result = await graph_client.identity.authentication_event_listeners.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventListeners/$entity",
  "@odata.type": "#microsoft.graph.onPasswordSubmitListener",
  "id": "4a6cb5f0-1234-5678-abcd-ef9012345678",
  "displayName": "JIT migration listener",
  "authenticationEventsFlowId": null,
  "conditions": {
    "applications": {
      "includeAllApplications": false,
      "includeApplications": [
        {
          "appId": "00011111-aaaa-2222-bbbb-3333cccc4444"
        }
      ]
    }
  },
  "handler": {
    "@odata.type": "#microsoft.graph.onPasswordMigrationCustomExtensionHandler",
    "migrationPropertyId": "extension_b7b1c57b532f40b8b5ed4b7a7ba67401_requiresMigration",
    "configuration": null
  }
}
```

### Example 5: Create an onVerifiedIdClaimValidationListener object

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/identity/authenticationEventListeners
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationListener",
  "displayName": "Verified ID Claim Validation Listener",
  "priority": 500,
  "conditions": {
    "applications": {
      "includeAllApplications": false,
      "includeApplications": [
        {
          "appId": "63856651-13d9-4784-9abf-20758d509e19"
        }
      ]
    }
  },
  "authenticationEventsFlowId": "5a8e8f57-82b2-4cbf-b145-3e6e0c154897",
  "handler": {
    "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler",
    "configuration": {
      "@odata.type": "#microsoft.graph.customExtensionOverwriteConfiguration",
      "clientConfiguration": {
        "@odata.type": "#microsoft.graph.customExtensionClientConfiguration",
        "maximumRetries": 1,
        "timeoutInMilliseconds": 2000
      },
      "behaviorOnError": {
        "@odata.type": "#microsoft.graph.customExtensionBehaviorOnError"
      }
    },
    "customExtension": {
      "id": "6a0a3429-be77-0aed-951e-1c8aed62bf8a"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnVerifiedIdClaimValidationListener
{
	OdataType = "#microsoft.graph.onVerifiedIdClaimValidationListener",
	DisplayName = "Verified ID Claim Validation Listener",
	Conditions = new AuthenticationConditions
	{
		Applications = new AuthenticationConditionsApplications
		{
			IncludeApplications = new List<AuthenticationConditionApplication>
			{
				new AuthenticationConditionApplication
				{
					AppId = "63856651-13d9-4784-9abf-20758d509e19",
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"includeAllApplications" , false
				},
			},
		},
	},
	AuthenticationEventsFlowId = "5a8e8f57-82b2-4cbf-b145-3e6e0c154897",
	Handler = new OnVerifiedIdClaimValidationCustomExtensionHandler
	{
		OdataType = "#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler",
		Configuration = new CustomExtensionOverwriteConfiguration
		{
			OdataType = "#microsoft.graph.customExtensionOverwriteConfiguration",
			ClientConfiguration = new CustomExtensionClientConfiguration
			{
				OdataType = "#microsoft.graph.customExtensionClientConfiguration",
				MaximumRetries = 1,
				TimeoutInMilliseconds = 2000,
			},
			BehaviorOnError = new CustomExtensionBehaviorOnError
			{
				OdataType = "#microsoft.graph.customExtensionBehaviorOnError",
			},
		},
		CustomExtension = new OnVerifiedIdClaimValidationCustomExtension
		{
			Id = "6a0a3429-be77-0aed-951e-1c8aed62bf8a",
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"priority" , 500
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventListeners.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationEventListener()
displayName := "Verified ID Claim Validation Listener"
requestBody.SetDisplayName(&displayName) 
conditions := graphmodels.NewAuthenticationConditions()
applications := graphmodels.NewAuthenticationConditionsApplications()


authenticationConditionApplication := graphmodels.NewAuthenticationConditionApplication()
appId := "63856651-13d9-4784-9abf-20758d509e19"
authenticationConditionApplication.SetAppId(&appId) 

includeApplications := []graphmodels.AuthenticationConditionApplicationable {
	authenticationConditionApplication,
}
applications.SetIncludeApplications(includeApplications)
additionalData := map[string]interface{}{
	includeAllApplications := false
applications.SetIncludeAllApplications(&includeAllApplications) 
}
applications.SetAdditionalData(additionalData)
conditions.SetApplications(applications)
requestBody.SetConditions(conditions)
authenticationEventsFlowId := "5a8e8f57-82b2-4cbf-b145-3e6e0c154897"
requestBody.SetAuthenticationEventsFlowId(&authenticationEventsFlowId) 
handler := graphmodels.NewOnVerifiedIdClaimValidationCustomExtensionHandler()
configuration := graphmodels.NewCustomExtensionOverwriteConfiguration()
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
timeoutInMilliseconds := int32(2000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
configuration.SetClientConfiguration(clientConfiguration)
behaviorOnError := graphmodels.NewCustomExtensionBehaviorOnError()
configuration.SetBehaviorOnError(behaviorOnError)
handler.SetConfiguration(configuration)
customExtension := graphmodels.NewOnVerifiedIdClaimValidationCustomExtension()
id := "6a0a3429-be77-0aed-951e-1c8aed62bf8a"
customExtension.SetId(&id) 
handler.SetCustomExtension(customExtension)
requestBody.SetHandler(handler)
additionalData := map[string]interface{}{
	"priority" : int32(500) , 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventListeners, err := graphClient.Identity().AuthenticationEventListeners().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnVerifiedIdClaimValidationListener authenticationEventListener = new OnVerifiedIdClaimValidationListener();
authenticationEventListener.setOdataType("#microsoft.graph.onVerifiedIdClaimValidationListener");
authenticationEventListener.setDisplayName("Verified ID Claim Validation Listener");
AuthenticationConditions conditions = new AuthenticationConditions();
AuthenticationConditionsApplications applications = new AuthenticationConditionsApplications();
LinkedList<AuthenticationConditionApplication> includeApplications = new LinkedList<AuthenticationConditionApplication>();
AuthenticationConditionApplication authenticationConditionApplication = new AuthenticationConditionApplication();
authenticationConditionApplication.setAppId("63856651-13d9-4784-9abf-20758d509e19");
includeApplications.add(authenticationConditionApplication);
applications.setIncludeApplications(includeApplications);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("includeAllApplications", false);
applications.setAdditionalData(additionalData);
conditions.setApplications(applications);
authenticationEventListener.setConditions(conditions);
authenticationEventListener.setAuthenticationEventsFlowId("5a8e8f57-82b2-4cbf-b145-3e6e0c154897");
OnVerifiedIdClaimValidationCustomExtensionHandler handler = new OnVerifiedIdClaimValidationCustomExtensionHandler();
handler.setOdataType("#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler");
CustomExtensionOverwriteConfiguration configuration = new CustomExtensionOverwriteConfiguration();
configuration.setOdataType("#microsoft.graph.customExtensionOverwriteConfiguration");
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setOdataType("#microsoft.graph.customExtensionClientConfiguration");
clientConfiguration.setMaximumRetries(1);
clientConfiguration.setTimeoutInMilliseconds(2000);
configuration.setClientConfiguration(clientConfiguration);
CustomExtensionBehaviorOnError behaviorOnError = new CustomExtensionBehaviorOnError();
behaviorOnError.setOdataType("#microsoft.graph.customExtensionBehaviorOnError");
configuration.setBehaviorOnError(behaviorOnError);
handler.setConfiguration(configuration);
OnVerifiedIdClaimValidationCustomExtension customExtension = new OnVerifiedIdClaimValidationCustomExtension();
customExtension.setId("6a0a3429-be77-0aed-951e-1c8aed62bf8a");
handler.setCustomExtension(customExtension);
authenticationEventListener.setHandler(handler);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("priority", 500);
authenticationEventListener.setAdditionalData(additionalData1);
AuthenticationEventListener result = graphClient.identity().authenticationEventListeners().post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationEventListener = {
  '@odata.type': '#microsoft.graph.onVerifiedIdClaimValidationListener',
  displayName: 'Verified ID Claim Validation Listener',
  priority: 500,
  conditions: {
    applications: {
      includeAllApplications: false,
      includeApplications: [
        {
          appId: '63856651-13d9-4784-9abf-20758d509e19'
        }
      ]
    }
  },
  authenticationEventsFlowId: '5a8e8f57-82b2-4cbf-b145-3e6e0c154897',
  handler: {
    '@odata.type': '#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler',
    configuration: {
      '@odata.type': '#microsoft.graph.customExtensionOverwriteConfiguration',
      clientConfiguration: {
        '@odata.type': '#microsoft.graph.customExtensionClientConfiguration',
        maximumRetries: 1,
        timeoutInMilliseconds: 2000
      },
      behaviorOnError: {
        '@odata.type': '#microsoft.graph.customExtensionBehaviorOnError'
      }
    },
    customExtension: {
      id: '6a0a3429-be77-0aed-951e-1c8aed62bf8a'
    }
  }
};

await client.api('/identity/authenticationEventListeners')
	.post(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnVerifiedIdClaimValidationListener;
use Microsoft\Graph\Generated\Models\AuthenticationConditions;
use Microsoft\Graph\Generated\Models\AuthenticationConditionsApplications;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;
use Microsoft\Graph\Generated\Models\OnVerifiedIdClaimValidationCustomExtensionHandler;
use Microsoft\Graph\Generated\Models\CustomExtensionOverwriteConfiguration;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;
use Microsoft\Graph\Generated\Models\CustomExtensionBehaviorOnError;
use Microsoft\Graph\Generated\Models\OnVerifiedIdClaimValidationCustomExtension;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnVerifiedIdClaimValidationListener();
$requestBody->setOdataType('#microsoft.graph.onVerifiedIdClaimValidationListener');
$requestBody->setDisplayName('Verified ID Claim Validation Listener');
$conditions = new AuthenticationConditions();
$conditionsApplications = new AuthenticationConditionsApplications();
$includeApplicationsAuthenticationConditionApplication1 = new AuthenticationConditionApplication();
$includeApplicationsAuthenticationConditionApplication1->setAppId('63856651-13d9-4784-9abf-20758d509e19');
$includeApplicationsArray []= $includeApplicationsAuthenticationConditionApplication1;
$conditionsApplications->setIncludeApplications($includeApplicationsArray);

$additionalData = [
'includeAllApplications' => false,
];
$conditionsApplications->setAdditionalData($additionalData);
$conditions->setApplications($conditionsApplications);
$requestBody->setConditions($conditions);
$requestBody->setAuthenticationEventsFlowId('5a8e8f57-82b2-4cbf-b145-3e6e0c154897');
$handler = new OnVerifiedIdClaimValidationCustomExtensionHandler();
$handler->setOdataType('#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler');
$handlerConfiguration = new CustomExtensionOverwriteConfiguration();
$handlerConfiguration->setOdataType('#microsoft.graph.customExtensionOverwriteConfiguration');
$handlerConfigurationClientConfiguration = new CustomExtensionClientConfiguration();
$handlerConfigurationClientConfiguration->setOdataType('#microsoft.graph.customExtensionClientConfiguration');
$handlerConfigurationClientConfiguration->setMaximumRetries(1);
$handlerConfigurationClientConfiguration->setTimeoutInMilliseconds(2000);
$handlerConfiguration->setClientConfiguration($handlerConfigurationClientConfiguration);
$handlerConfigurationBehaviorOnError = new CustomExtensionBehaviorOnError();
$handlerConfigurationBehaviorOnError->setOdataType('#microsoft.graph.customExtensionBehaviorOnError');
$handlerConfiguration->setBehaviorOnError($handlerConfigurationBehaviorOnError);
$handler->setConfiguration($handlerConfiguration);
$handlerCustomExtension = new OnVerifiedIdClaimValidationCustomExtension();
$handlerCustomExtension->setId('6a0a3429-be77-0aed-951e-1c8aed62bf8a');
$handler->setCustomExtension($handlerCustomExtension);
$requestBody->setHandler($handler);
$additionalData = [
'priority' => 500,
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identity()->authenticationEventListeners()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onVerifiedIdClaimValidationListener"
	displayName = "Verified ID Claim Validation Listener"
	priority = 
	conditions = @{
		applications = @{
			includeAllApplications = $false
			includeApplications = @(
				@{
					appId = "63856651-13d9-4784-9abf-20758d509e19"
				}
			)
		}
	}
	authenticationEventsFlowId = "5a8e8f57-82b2-4cbf-b145-3e6e0c154897"
	handler = @{
		"@odata.type" = "#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler"
		configuration = @{
			"@odata.type" = "#microsoft.graph.customExtensionOverwriteConfiguration"
			clientConfiguration = @{
				"@odata.type" = "#microsoft.graph.customExtensionClientConfiguration"
				maximumRetries = 
				timeoutInMilliseconds = 
			}
			behaviorOnError = @{
				"@odata.type" = "#microsoft.graph.customExtensionBehaviorOnError"
			}
		}
		customExtension = @{
			id = "6a0a3429-be77-0aed-951e-1c8aed62bf8a"
		}
	}
}

New-MgIdentityAuthenticationEventListener -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_verified_id_claim_validation_listener import OnVerifiedIdClaimValidationListener
from msgraph.generated.models.authentication_conditions import AuthenticationConditions
from msgraph.generated.models.authentication_conditions_applications import AuthenticationConditionsApplications
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
from msgraph.generated.models.on_verified_id_claim_validation_custom_extension_handler import OnVerifiedIdClaimValidationCustomExtensionHandler
from msgraph.generated.models.custom_extension_overwrite_configuration import CustomExtensionOverwriteConfiguration
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
from msgraph.generated.models.custom_extension_behavior_on_error import CustomExtensionBehaviorOnError
from msgraph.generated.models.on_verified_id_claim_validation_custom_extension import OnVerifiedIdClaimValidationCustomExtension
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnVerifiedIdClaimValidationListener(
	odata_type = "#microsoft.graph.onVerifiedIdClaimValidationListener",
	display_name = "Verified ID Claim Validation Listener",
	conditions = AuthenticationConditions(
		applications = AuthenticationConditionsApplications(
			include_applications = [
				AuthenticationConditionApplication(
					app_id = "63856651-13d9-4784-9abf-20758d509e19",
				),
			],
			additional_data = {
					"include_all_applications" : False,
			}
		),
	),
	authentication_events_flow_id = "5a8e8f57-82b2-4cbf-b145-3e6e0c154897",
	handler = OnVerifiedIdClaimValidationCustomExtensionHandler(
		odata_type = "#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler",
		configuration = CustomExtensionOverwriteConfiguration(
			odata_type = "#microsoft.graph.customExtensionOverwriteConfiguration",
			client_configuration = CustomExtensionClientConfiguration(
				odata_type = "#microsoft.graph.customExtensionClientConfiguration",
				maximum_retries = 1,
				timeout_in_milliseconds = 2000,
			),
			behavior_on_error = CustomExtensionBehaviorOnError(
				odata_type = "#microsoft.graph.customExtensionBehaviorOnError",
			),
		),
		custom_extension = OnVerifiedIdClaimValidationCustomExtension(
			id = "6a0a3429-be77-0aed-951e-1c8aed62bf8a",
		),
	),
	additional_data = {
			"priority" : 500,
	}
)

result = await graph_client.identity.authentication_event_listeners.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventListeners/$entity",
    "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationListener",
    "id": "6a7455ef-0906-bbc3-f902-0f9ab8903082",
    "displayName": "Verified ID Claim Validation Listener",
    "priority": 500,
    "conditions": {
        "applications": {
            "includeAllApplications": false,
            "includeApplications": [
                {
                    "appId": "63856651-13d9-4784-9abf-20758d509e19"
                }
            ]
        }
    },
    "authenticationEventsFlowId": "5a8e8f57-82b2-4cbf-b145-3e6e0c154897",
    "handler": {
        "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationCustomExtensionHandler",
        "configuration": {
            "@odata.type": "#microsoft.graph.customExtensionOverwriteConfiguration",
            "clientConfiguration": {
                "@odata.type": "#microsoft.graph.customExtensionClientConfiguration",
                "maximumRetries": 1,
                "timeoutInMilliseconds": 2000
            },
            "behaviorOnError": {
                "@odata.type": "#microsoft.graph.customExtensionBehaviorOnError"
            }
        },
        "customExtension": {
            "id": "6a0a3429-be77-0aed-951e-1c8aed62bf8a"
        }
    }
}
```
