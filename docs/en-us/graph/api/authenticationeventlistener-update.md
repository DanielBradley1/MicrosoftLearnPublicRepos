<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationeventlistener-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Update authenticationEventListener

Namespace: microsoft.graph

Update the properties of an [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) object. You must specify the **@odata.type** property and the value of the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) object type to update. The following derived types are currently supported.

- [onTokenIssuanceStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartlistener?view=graph-rest-1.0) resource type
- [onInteractiveAuthFlowStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/oninteractiveauthflowstartlistener?view=graph-rest-1.0) resource type
- [onAuthenticationMethodLoadStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onauthenticationmethodloadstartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionlistener?view=graph-rest-1.0) resource type
- [onUserCreateStartListener resource type](https://learn.microsoft.com/en-us/graph/api/resources/onusercreatestartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartlistener?view=graph-rest-1.0) resource type
- [onAttributeCollectionSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitlistener?view=graph-rest-1.0) resource type
- [onEmailOtpSendListener](https://learn.microsoft.com/en-us/graph/api/resources/onemailotpsendlistener?view=graph-rest-1.0) resource type
- [onFraudProtectionLoadStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstartlistener?view=graph-rest-1.0) resource type
- [onPasswordSubmitListener](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitlistener?view=graph-rest-1.0) resource type
- [onVerifiedIdClaimValidationListener](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationlistener?view=graph-rest-1.0) resource type

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
PATCH /identity/authenticationEventListeners/{authenticationEventListenerId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the **@odata.type** property and the value of the [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) object type to update. For example, `"@odata.type": "#microsoft.graph.onTokenIssuanceStartListener"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [authenticationConditions](https://learn.microsoft.com/en-us/graph/api/resources/authenticationconditions?view=graph-rest-1.0) | The conditions on which this authenticationEventListener should trigger. Optional. |
| displayName | String | The display name of the authentication event listener policy. Optional. |
| handler | [onTokenIssuanceStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestarthandler?view=graph-rest-1.0) or [onFraudProtectionLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstarthandler?view=graph-rest-1.0) or [onPasswordSubmitHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmithandler?view=graph-rest-1.0) | The handler to invoke when conditions are met. For **onTokenIssuanceStartListener**, set to [onTokenIssuanceStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestarthandler?view=graph-rest-1.0). For **onFraudProtectionLoadStartListener**, set to [onFraudProtectionLoadStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstarthandler?view=graph-rest-1.0). For **onPasswordSubmitListener**, set to [onPasswordSubmitHandler](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmithandler?view=graph-rest-1.0). |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Update an authentication event listener's trigger conditions

#### Request

The following example shows a request to update an authentication event listener's trigger conditions.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
PATCH https://graph.microsoft.com/v1.0/identity/authenticationEventListeners/990d94e5-cc8f-4c4b-97b4-27e2678aac28
Content-Type: application/json

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
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.AuthenticationEventListeners["{authenticationEventListener-id}"].PatchAsync(requestBody);
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

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationEventListeners, err := graphClient.Identity().AuthenticationEventListeners().ByAuthenticationEventListenerId("authenticationEventListener-id").Patch(context.Background(), requestBody, nil)
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
AuthenticationEventListener result = graphClient.identity().authenticationEventListeners().byAuthenticationEventListenerId("{authenticationEventListener-id}").patch(authenticationEventListener);
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
};

await client.api('/identity/authenticationEventListeners/990d94e5-cc8f-4c4b-97b4-27e2678aac28')
	.update(authenticationEventListener);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnTokenIssuanceStartListener;
use Microsoft\Graph\Generated\Models\AuthenticationConditions;
use Microsoft\Graph\Generated\Models\AuthenticationConditionsApplications;
use Microsoft\Graph\Generated\Models\AuthenticationConditionApplication;


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

$result = $graphServiceClient->identity()->authenticationEventListeners()->byAuthenticationEventListenerId('authenticationEventListener-id')->patch($requestBody)->wait();
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
}

Update-MgIdentityAuthenticationEventListener -AuthenticationEventListenerId $authenticationEventListenerId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_token_issuance_start_listener import OnTokenIssuanceStartListener
from msgraph.generated.models.authentication_conditions import AuthenticationConditions
from msgraph.generated.models.authentication_conditions_applications import AuthenticationConditionsApplications
from msgraph.generated.models.authentication_condition_application import AuthenticationConditionApplication
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
)

result = await graph_client.identity.authentication_event_listeners.by_authentication_event_listener_id('authenticationEventListener-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Add an application to an authentication event listener's trigger conditions

#### Request

The following example shows a request to add an application to an authentication event listener's trigger conditions.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
POST https://graph.microsoft.com/v1.0/identity/authenticationEventListeners/0313cc37-d421-421d-857b-87804d61e33e/conditions/applications/includeApplications
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.authenticationConditionApplication",
    "appId": "63856651-13d9-4784-9abf-20758d509e19"
}
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

const authenticationConditionApplication = {
    '@odata.type': '#microsoft.graph.authenticationConditionApplication',
    appId: '63856651-13d9-4784-9abf-20758d509e19'
};

await client.api('/identity/authenticationEventListeners/0313cc37-d421-421d-857b-87804d61e33e/conditions/applications/includeApplications')
	.post(authenticationConditionApplication);
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

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response to a request to add an application to an authentication event listener's trigger conditions:

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/authenticationEventListeners('0313cc37-d421-421d-857b-87804d61e33e')/conditions/applications/includeApplications/$entity",
    "appId": "63856651-13d9-4784-9abf-20758d509e19"
}
```
