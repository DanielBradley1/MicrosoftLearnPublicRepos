<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# conditionalAccessRoot: evaluate

Namespace: microsoft.graph

Evaluates the applicability of Conditional Access Policies in your tenant based on the provided sign-in properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.Read.ConditionalAccess | Policy.Read.All, Policy.ReadWrite.ConditionalAccess |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.Read.ConditionalAccess | Policy.Read.All, Policy.ReadWrite.ConditionalAccess |

## HTTP request

```http
POST /identity/conditionalAccess/evaluate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters. For the evaluation to provide the most accurate results, include as many details about the sign-in as possible. If your tenant has policies with specific conditions, and the sign-in details for those conditions are missing in the request, the 'What If' tool can't evaluate those conditions.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| signInIdentity | [signInIdentity](https://learn.microsoft.com/en-us/graph/api/resources/signinidentity?view=graph-rest-1.0) | Represents the identity that is authenticating. This can be a user, external user, or single tenant service principal. Required. |
| signInContext | [signInContext](https://learn.microsoft.com/en-us/graph/api/resources/signincontext?view=graph-rest-1.0) | Represents the context of the authentication. This could involve accessing an application, performing a specific user action, or accessing data protected by an authentication context. Required. |
| signInConditions | [signInConditions](https://learn.microsoft.com/en-us/graph/api/resources/signinconditions?view=graph-rest-1.0) | Represents sign-in parameters of the authenticating identity. This includes details such as location, device information, risk information, etc. Required. |
| appliedPoliciesOnly | Boolean | This property controls whether to include all policies in the response or only the policies that would apply to the authentication event. Optional. |

## Response

If successful, this action returns a `200 OK` response code and a [whatIfAnalysisResult](https://learn.microsoft.com/en-us/graph/api/resources/whatifanalysisresult?view=graph-rest-1.0) collection in the response body. The response indicates whether each policy in the tenant would apply or not based on the sign-in properties provided in the request body.

## Examples

### Example 1: Identify conditional access policies that would apply to a user accessing an application

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
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/evaluate
Content-Type: application/json

{
    "signInIdentity": {
        "@odata.type": "#microsoft.graph.userSignIn",
        "userId": "15dc174b-f34c-4588-ac45-61d6e05dce93"
    },
    "signInContext": {
        "@odata.type": "#microsoft.graph.applicationContext",
        "includeApplications": [
            "00000003-0000-0ff1-ce00-000000000000"
        ]
    },
    "signInConditions": {
        "devicePlatform": "android",
        "clientAppType": "browser",
        "signInRiskLevel": "high",
        "userRiskLevel": "high",
        "country": "US",
        "ipAddress": "40.77.182.32",
        "insiderRiskLevel": "elevated",
        "authenticationFlow": {
            "transferMethod": "deviceCodeFlow"
        },
        "deviceInfo": {
            "isCompliant": true
        }
    },
    "appliedPoliciesOnly": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Identity.ConditionalAccess.Evaluate;
using Microsoft.Graph.Models;

var requestBody = new EvaluatePostRequestBody
{
	SignInIdentity = new UserSignIn
	{
		OdataType = "#microsoft.graph.userSignIn",
		UserId = "15dc174b-f34c-4588-ac45-61d6e05dce93",
	},
	SignInContext = new ApplicationContext
	{
		OdataType = "#microsoft.graph.applicationContext",
		IncludeApplications = new List<string>
		{
			"00000003-0000-0ff1-ce00-000000000000",
		},
	},
	SignInConditions = new SignInConditions
	{
		DevicePlatform = ConditionalAccessDevicePlatform.Android,
		ClientAppType = ConditionalAccessClientApp.Browser,
		SignInRiskLevel = RiskLevel.High,
		UserRiskLevel = RiskLevel.High,
		Country = "US",
		IpAddress = "40.77.182.32",
		InsiderRiskLevel = InsiderRiskLevel.Elevated,
		AuthenticationFlow = new AuthenticationFlow
		{
			TransferMethod = ConditionalAccessTransferMethods.DeviceCodeFlow,
		},
		DeviceInfo = new DeviceInfo
		{
			IsCompliant = true,
		},
	},
	AppliedPoliciesOnly = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Evaluate.PostAsEvaluatePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentity.NewEvaluatePostRequestBody()
signInIdentity := graphmodels.NewUserSignIn()
userId := "15dc174b-f34c-4588-ac45-61d6e05dce93"
signInIdentity.SetUserId(&userId) 
requestBody.SetSignInIdentity(signInIdentity)
signInContext := graphmodels.NewApplicationContext()
includeApplications := []string {
	"00000003-0000-0ff1-ce00-000000000000",
}
signInContext.SetIncludeApplications(includeApplications)
requestBody.SetSignInContext(signInContext)
signInConditions := graphmodels.NewSignInConditions()
devicePlatform := graphmodels.ANDROID_CONDITIONALACCESSDEVICEPLATFORM 
signInConditions.SetDevicePlatform(&devicePlatform) 
clientAppType := graphmodels.BROWSER_CONDITIONALACCESSCLIENTAPP 
signInConditions.SetClientAppType(&clientAppType) 
signInRiskLevel := graphmodels.HIGH_RISKLEVEL 
signInConditions.SetSignInRiskLevel(&signInRiskLevel) 
userRiskLevel := graphmodels.HIGH_RISKLEVEL 
signInConditions.SetUserRiskLevel(&userRiskLevel) 
country := "US"
signInConditions.SetCountry(&country) 
ipAddress := "40.77.182.32"
signInConditions.SetIpAddress(&ipAddress) 
insiderRiskLevel := graphmodels.ELEVATED_INSIDERRISKLEVEL 
signInConditions.SetInsiderRiskLevel(&insiderRiskLevel) 
authenticationFlow := graphmodels.NewAuthenticationFlow()
transferMethod := graphmodels.DEVICECODEFLOW_CONDITIONALACCESSTRANSFERMETHODS 
authenticationFlow.SetTransferMethod(&transferMethod) 
signInConditions.SetAuthenticationFlow(authenticationFlow)
deviceInfo := graphmodels.NewDeviceInfo()
isCompliant := true
deviceInfo.SetIsCompliant(&isCompliant) 
signInConditions.SetDeviceInfo(deviceInfo)
requestBody.SetSignInConditions(signInConditions)
appliedPoliciesOnly := true
requestBody.SetAppliedPoliciesOnly(&appliedPoliciesOnly) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
evaluate, err := graphClient.Identity().ConditionalAccess().Evaluate().PostAsEvaluatePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody evaluatePostRequestBody = new com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody();
UserSignIn signInIdentity = new UserSignIn();
signInIdentity.setOdataType("#microsoft.graph.userSignIn");
signInIdentity.setUserId("15dc174b-f34c-4588-ac45-61d6e05dce93");
evaluatePostRequestBody.setSignInIdentity(signInIdentity);
ApplicationContext signInContext = new ApplicationContext();
signInContext.setOdataType("#microsoft.graph.applicationContext");
LinkedList<String> includeApplications = new LinkedList<String>();
includeApplications.add("00000003-0000-0ff1-ce00-000000000000");
signInContext.setIncludeApplications(includeApplications);
evaluatePostRequestBody.setSignInContext(signInContext);
SignInConditions signInConditions = new SignInConditions();
signInConditions.setDevicePlatform(ConditionalAccessDevicePlatform.Android);
signInConditions.setClientAppType(ConditionalAccessClientApp.Browser);
signInConditions.setSignInRiskLevel(RiskLevel.High);
signInConditions.setUserRiskLevel(RiskLevel.High);
signInConditions.setCountry("US");
signInConditions.setIpAddress("40.77.182.32");
signInConditions.setInsiderRiskLevel(InsiderRiskLevel.Elevated);
AuthenticationFlow authenticationFlow = new AuthenticationFlow();
authenticationFlow.setTransferMethod(EnumSet.of(ConditionalAccessTransferMethods.DeviceCodeFlow));
signInConditions.setAuthenticationFlow(authenticationFlow);
DeviceInfo deviceInfo = new DeviceInfo();
deviceInfo.setIsCompliant(true);
signInConditions.setDeviceInfo(deviceInfo);
evaluatePostRequestBody.setSignInConditions(signInConditions);
evaluatePostRequestBody.setAppliedPoliciesOnly(true);
var result = graphClient.identity().conditionalAccess().evaluate().post(evaluatePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const whatIfAnalysisResult = {
    signInIdentity: {
        '@odata.type': '#microsoft.graph.userSignIn',
        userId: '15dc174b-f34c-4588-ac45-61d6e05dce93'
    },
    signInContext: {
        '@odata.type': '#microsoft.graph.applicationContext',
        includeApplications: [
            '00000003-0000-0ff1-ce00-000000000000'
        ]
    },
    signInConditions: {
        devicePlatform: 'android',
        clientAppType: 'browser',
        signInRiskLevel: 'high',
        userRiskLevel: 'high',
        country: 'US',
        ipAddress: '40.77.182.32',
        insiderRiskLevel: 'elevated',
        authenticationFlow: {
            transferMethod: 'deviceCodeFlow'
        },
        deviceInfo: {
            isCompliant: true
        }
    },
    appliedPoliciesOnly: true
};

await client.api('/identity/conditionalAccess/evaluate')
	.post(whatIfAnalysisResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\ConditionalAccess\Evaluate\EvaluatePostRequestBody;
use Microsoft\Graph\Generated\Models\UserSignIn;
use Microsoft\Graph\Generated\Models\ApplicationContext;
use Microsoft\Graph\Generated\Models\SignInConditions;
use Microsoft\Graph\Generated\Models\ConditionalAccessDevicePlatform;
use Microsoft\Graph\Generated\Models\ConditionalAccessClientApp;
use Microsoft\Graph\Generated\Models\RiskLevel;
use Microsoft\Graph\Generated\Models\InsiderRiskLevel;
use Microsoft\Graph\Generated\Models\AuthenticationFlow;
use Microsoft\Graph\Generated\Models\ConditionalAccessTransferMethods;
use Microsoft\Graph\Generated\Models\DeviceInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluatePostRequestBody();
$signInIdentity = new UserSignIn();
$signInIdentity->setOdataType('#microsoft.graph.userSignIn');
$signInIdentity->setUserId('15dc174b-f34c-4588-ac45-61d6e05dce93');
$requestBody->setSignInIdentity($signInIdentity);
$signInContext = new ApplicationContext();
$signInContext->setOdataType('#microsoft.graph.applicationContext');
$signInContext->setIncludeApplications(['00000003-0000-0ff1-ce00-000000000000', 	]);
$requestBody->setSignInContext($signInContext);
$signInConditions = new SignInConditions();
$signInConditions->setDevicePlatform(new ConditionalAccessDevicePlatform('android'));
$signInConditions->setClientAppType(new ConditionalAccessClientApp('browser'));
$signInConditions->setSignInRiskLevel(new RiskLevel('high'));
$signInConditions->setUserRiskLevel(new RiskLevel('high'));
$signInConditions->setCountry('US');
$signInConditions->setIpAddress('40.77.182.32');
$signInConditions->setInsiderRiskLevel(new InsiderRiskLevel('elevated'));
$signInConditionsAuthenticationFlow = new AuthenticationFlow();
$signInConditionsAuthenticationFlow->setTransferMethod(new ConditionalAccessTransferMethods('deviceCodeFlow'));
$signInConditions->setAuthenticationFlow($signInConditionsAuthenticationFlow);
$signInConditionsDeviceInfo = new DeviceInfo();
$signInConditionsDeviceInfo->setIsCompliant(true);
$signInConditions->setDeviceInfo($signInConditionsDeviceInfo);
$requestBody->setSignInConditions($signInConditions);
$requestBody->setAppliedPoliciesOnly(true);

$result = $graphServiceClient->identity()->conditionalAccess()->evaluate()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	signInIdentity = @{
		"@odata.type" = "#microsoft.graph.userSignIn"
		userId = "15dc174b-f34c-4588-ac45-61d6e05dce93"
	}
	signInContext = @{
		"@odata.type" = "#microsoft.graph.applicationContext"
		includeApplications = @(
		"00000003-0000-0ff1-ce00-000000000000"
	)
}
signInConditions = @{
	devicePlatform = "android"
	clientAppType = "browser"
	signInRiskLevel = "high"
	userRiskLevel = "high"
	country = "US"
	ipAddress = "40.77.182.32"
	insiderRiskLevel = "elevated"
	authenticationFlow = @{
		transferMethod = "deviceCodeFlow"
	}
	deviceInfo = @{
		isCompliant = $true
	}
}
appliedPoliciesOnly = $true
}

Test-MgIdentityConditionalAccess -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.conditionalaccess.evaluate.evaluate_post_request_body import EvaluatePostRequestBody
from msgraph.generated.models.user_sign_in import UserSignIn
from msgraph.generated.models.application_context import ApplicationContext
from msgraph.generated.models.sign_in_conditions import SignInConditions
from msgraph.generated.models.conditional_access_device_platform import ConditionalAccessDevicePlatform
from msgraph.generated.models.conditional_access_client_app import ConditionalAccessClientApp
from msgraph.generated.models.risk_level import RiskLevel
from msgraph.generated.models.insider_risk_level import InsiderRiskLevel
from msgraph.generated.models.authentication_flow import AuthenticationFlow
from msgraph.generated.models.conditional_access_transfer_methods import ConditionalAccessTransferMethods
from msgraph.generated.models.device_info import DeviceInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluatePostRequestBody(
	sign_in_identity = UserSignIn(
		odata_type = "#microsoft.graph.userSignIn",
		user_id = "15dc174b-f34c-4588-ac45-61d6e05dce93",
	),
	sign_in_context = ApplicationContext(
		odata_type = "#microsoft.graph.applicationContext",
		include_applications = [
			"00000003-0000-0ff1-ce00-000000000000",
		],
	),
	sign_in_conditions = SignInConditions(
		device_platform = ConditionalAccessDevicePlatform.Android,
		client_app_type = ConditionalAccessClientApp.Browser,
		sign_in_risk_level = RiskLevel.High,
		user_risk_level = RiskLevel.High,
		country = "US",
		ip_address = "40.77.182.32",
		insider_risk_level = InsiderRiskLevel.Elevated,
		authentication_flow = AuthenticationFlow(
			transfer_method = ConditionalAccessTransferMethods.DeviceCodeFlow,
		),
		device_info = DeviceInfo(
			is_compliant = True,
		),
	),
	applied_policies_only = True,
)

result = await graph_client.identity.conditional_access.evaluate.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.whatIfAnalysisResult)",
    "value": [
        {
            "id": "df9e6f15-2b60-4e78-b990-b2da33a10886",
            "templateId": null,
            "displayName": "All users except au1_Office 365_No conditions_Session control application enforced restrictions",
            "createdDateTime": "2022-04-01T18:55:43.1454565Z",
            "modifiedDateTime": "2025-03-27T21:42:26.951558Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "grantControls": null,
            "partialEnablementStrategy": null,
            "conditions": {
                "userRiskLevels": [],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "locations": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "clientApplications": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [
                        "Office365"
                    ],
                    "excludeApplications": [],
                    "includeUserActions": [],
                    "includeAuthenticationContextClassReferences": [],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [
                        "All"
                    ],
                    "excludeUsers": [
                        "f7ca74b0-8562-4083-b66c-0476f942cfd0"
                    ],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                }
            },
            "sessionControls": {
                "disableResilienceDefaults": null,
                "cloudAppSecurity": null,
                "signInFrequency": null,
                "persistentBrowser": null,
                "continuousAccessEvaluation": null,
                "secureSignInSession": null,
                "networkAccessSecurity": null,
                "globalSecureAccessFilteringProfile": null,
                "applicationEnforcedRestrictions": {
                    "isEnabled": true
                }
            }
        },
        {
            "id": "37d51c45-8c60-4f82-98e0-6e1451cecf7c",
            "templateId": null,
            "displayName": "All Users except au1_All resources_user risk H_Password change",
            "createdDateTime": "2022-03-31T22:59:59.6688974Z",
            "modifiedDateTime": "2025-03-27T19:55:43.5390544Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "partialEnablementStrategy": null,
            "sessionControls": null,
            "conditions": {
                "userRiskLevels": [
                    "high"
                ],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "locations": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "clientApplications": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [
                        "All"
                    ],
                    "excludeApplications": [],
                    "includeUserActions": [],
                    "includeAuthenticationContextClassReferences": [],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [
                        "All"
                    ],
                    "excludeUsers": [
                        "f7ca74b0-8562-4083-b66c-0476f942cfd0"
                    ],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                }
            },
            "grantControls": {
                "operator": "AND",
                "builtInControls": [
                    "mfa",
                    "passwordChange"
                ],
                "customAuthenticationFactors": [],
                "termsOfUse": [],
                "authenticationStrength": null
            }
        }
    ]
}
```

### Example 2: Identify conditional access policies that would apply to a user accessing a sensitive file protected by an authentication context

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
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/evaluate
Content-Type: application/json

{
    "signInIdentity": {
        "@odata.type": "#microsoft.graph.userSignIn",
        "userId": "15dc174b-f34c-4588-ac45-61d6e05dce93"
    },
    "signInContext": {
        "@odata.type": "#microsoft.graph.authContext",
        "authenticationContextValue": "c37"
    },
    "signInConditions": {
        "devicePlatform": "windows",
        "clientAppType": "mobileAppsAndDesktopClients",
        "signInRiskLevel": "medium",
        "userRiskLevel": "none",
        "country": "US",
        "ipAddress": "40.77.182.32",
        "insiderRiskLevel": "moderate",
        "authenticationFlow": {
            "transferMethod": "authenticationTransfer"
        },
        "deviceInfo": {
            "profileType": "Standard"
        }
    },
    "appliedPoliciesOnly": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Identity.ConditionalAccess.Evaluate;
using Microsoft.Graph.Models;

var requestBody = new EvaluatePostRequestBody
{
	SignInIdentity = new UserSignIn
	{
		OdataType = "#microsoft.graph.userSignIn",
		UserId = "15dc174b-f34c-4588-ac45-61d6e05dce93",
	},
	SignInContext = new AuthContext
	{
		OdataType = "#microsoft.graph.authContext",
		AuthenticationContextValue = "c37",
	},
	SignInConditions = new SignInConditions
	{
		DevicePlatform = ConditionalAccessDevicePlatform.Windows,
		ClientAppType = ConditionalAccessClientApp.MobileAppsAndDesktopClients,
		SignInRiskLevel = RiskLevel.Medium,
		UserRiskLevel = RiskLevel.None,
		Country = "US",
		IpAddress = "40.77.182.32",
		InsiderRiskLevel = InsiderRiskLevel.Moderate,
		AuthenticationFlow = new AuthenticationFlow
		{
			TransferMethod = ConditionalAccessTransferMethods.AuthenticationTransfer,
		},
		DeviceInfo = new DeviceInfo
		{
			ProfileType = "Standard",
		},
	},
	AppliedPoliciesOnly = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Evaluate.PostAsEvaluatePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentity.NewEvaluatePostRequestBody()
signInIdentity := graphmodels.NewUserSignIn()
userId := "15dc174b-f34c-4588-ac45-61d6e05dce93"
signInIdentity.SetUserId(&userId) 
requestBody.SetSignInIdentity(signInIdentity)
signInContext := graphmodels.NewAuthContext()
authenticationContextValue := "c37"
signInContext.SetAuthenticationContextValue(&authenticationContextValue) 
requestBody.SetSignInContext(signInContext)
signInConditions := graphmodels.NewSignInConditions()
devicePlatform := graphmodels.WINDOWS_CONDITIONALACCESSDEVICEPLATFORM 
signInConditions.SetDevicePlatform(&devicePlatform) 
clientAppType := graphmodels.MOBILEAPPSANDDESKTOPCLIENTS_CONDITIONALACCESSCLIENTAPP 
signInConditions.SetClientAppType(&clientAppType) 
signInRiskLevel := graphmodels.MEDIUM_RISKLEVEL 
signInConditions.SetSignInRiskLevel(&signInRiskLevel) 
userRiskLevel := graphmodels.NONE_RISKLEVEL 
signInConditions.SetUserRiskLevel(&userRiskLevel) 
country := "US"
signInConditions.SetCountry(&country) 
ipAddress := "40.77.182.32"
signInConditions.SetIpAddress(&ipAddress) 
insiderRiskLevel := graphmodels.MODERATE_INSIDERRISKLEVEL 
signInConditions.SetInsiderRiskLevel(&insiderRiskLevel) 
authenticationFlow := graphmodels.NewAuthenticationFlow()
transferMethod := graphmodels.AUTHENTICATIONTRANSFER_CONDITIONALACCESSTRANSFERMETHODS 
authenticationFlow.SetTransferMethod(&transferMethod) 
signInConditions.SetAuthenticationFlow(authenticationFlow)
deviceInfo := graphmodels.NewDeviceInfo()
profileType := "Standard"
deviceInfo.SetProfileType(&profileType) 
signInConditions.SetDeviceInfo(deviceInfo)
requestBody.SetSignInConditions(signInConditions)
appliedPoliciesOnly := true
requestBody.SetAppliedPoliciesOnly(&appliedPoliciesOnly) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
evaluate, err := graphClient.Identity().ConditionalAccess().Evaluate().PostAsEvaluatePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody evaluatePostRequestBody = new com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody();
UserSignIn signInIdentity = new UserSignIn();
signInIdentity.setOdataType("#microsoft.graph.userSignIn");
signInIdentity.setUserId("15dc174b-f34c-4588-ac45-61d6e05dce93");
evaluatePostRequestBody.setSignInIdentity(signInIdentity);
AuthContext signInContext = new AuthContext();
signInContext.setOdataType("#microsoft.graph.authContext");
signInContext.setAuthenticationContextValue("c37");
evaluatePostRequestBody.setSignInContext(signInContext);
SignInConditions signInConditions = new SignInConditions();
signInConditions.setDevicePlatform(ConditionalAccessDevicePlatform.Windows);
signInConditions.setClientAppType(ConditionalAccessClientApp.MobileAppsAndDesktopClients);
signInConditions.setSignInRiskLevel(RiskLevel.Medium);
signInConditions.setUserRiskLevel(RiskLevel.None);
signInConditions.setCountry("US");
signInConditions.setIpAddress("40.77.182.32");
signInConditions.setInsiderRiskLevel(InsiderRiskLevel.Moderate);
AuthenticationFlow authenticationFlow = new AuthenticationFlow();
authenticationFlow.setTransferMethod(EnumSet.of(ConditionalAccessTransferMethods.AuthenticationTransfer));
signInConditions.setAuthenticationFlow(authenticationFlow);
DeviceInfo deviceInfo = new DeviceInfo();
deviceInfo.setProfileType("Standard");
signInConditions.setDeviceInfo(deviceInfo);
evaluatePostRequestBody.setSignInConditions(signInConditions);
evaluatePostRequestBody.setAppliedPoliciesOnly(true);
var result = graphClient.identity().conditionalAccess().evaluate().post(evaluatePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const whatIfAnalysisResult = {
    signInIdentity: {
        '@odata.type': '#microsoft.graph.userSignIn',
        userId: '15dc174b-f34c-4588-ac45-61d6e05dce93'
    },
    signInContext: {
        '@odata.type': '#microsoft.graph.authContext',
        authenticationContextValue: 'c37'
    },
    signInConditions: {
        devicePlatform: 'windows',
        clientAppType: 'mobileAppsAndDesktopClients',
        signInRiskLevel: 'medium',
        userRiskLevel: 'none',
        country: 'US',
        ipAddress: '40.77.182.32',
        insiderRiskLevel: 'moderate',
        authenticationFlow: {
            transferMethod: 'authenticationTransfer'
        },
        deviceInfo: {
            profileType: 'Standard'
        }
    },
    appliedPoliciesOnly: true
};

await client.api('/identity/conditionalAccess/evaluate')
	.post(whatIfAnalysisResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\ConditionalAccess\Evaluate\EvaluatePostRequestBody;
use Microsoft\Graph\Generated\Models\UserSignIn;
use Microsoft\Graph\Generated\Models\AuthContext;
use Microsoft\Graph\Generated\Models\SignInConditions;
use Microsoft\Graph\Generated\Models\ConditionalAccessDevicePlatform;
use Microsoft\Graph\Generated\Models\ConditionalAccessClientApp;
use Microsoft\Graph\Generated\Models\RiskLevel;
use Microsoft\Graph\Generated\Models\InsiderRiskLevel;
use Microsoft\Graph\Generated\Models\AuthenticationFlow;
use Microsoft\Graph\Generated\Models\ConditionalAccessTransferMethods;
use Microsoft\Graph\Generated\Models\DeviceInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluatePostRequestBody();
$signInIdentity = new UserSignIn();
$signInIdentity->setOdataType('#microsoft.graph.userSignIn');
$signInIdentity->setUserId('15dc174b-f34c-4588-ac45-61d6e05dce93');
$requestBody->setSignInIdentity($signInIdentity);
$signInContext = new AuthContext();
$signInContext->setOdataType('#microsoft.graph.authContext');
$signInContext->setAuthenticationContextValue('c37');
$requestBody->setSignInContext($signInContext);
$signInConditions = new SignInConditions();
$signInConditions->setDevicePlatform(new ConditionalAccessDevicePlatform('windows'));
$signInConditions->setClientAppType(new ConditionalAccessClientApp('mobileAppsAndDesktopClients'));
$signInConditions->setSignInRiskLevel(new RiskLevel('medium'));
$signInConditions->setUserRiskLevel(new RiskLevel('none'));
$signInConditions->setCountry('US');
$signInConditions->setIpAddress('40.77.182.32');
$signInConditions->setInsiderRiskLevel(new InsiderRiskLevel('moderate'));
$signInConditionsAuthenticationFlow = new AuthenticationFlow();
$signInConditionsAuthenticationFlow->setTransferMethod(new ConditionalAccessTransferMethods('authenticationTransfer'));
$signInConditions->setAuthenticationFlow($signInConditionsAuthenticationFlow);
$signInConditionsDeviceInfo = new DeviceInfo();
$signInConditionsDeviceInfo->setProfileType('Standard');
$signInConditions->setDeviceInfo($signInConditionsDeviceInfo);
$requestBody->setSignInConditions($signInConditions);
$requestBody->setAppliedPoliciesOnly(true);

$result = $graphServiceClient->identity()->conditionalAccess()->evaluate()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	signInIdentity = @{
		"@odata.type" = "#microsoft.graph.userSignIn"
		userId = "15dc174b-f34c-4588-ac45-61d6e05dce93"
	}
	signInContext = @{
		"@odata.type" = "#microsoft.graph.authContext"
		authenticationContextValue = "c37"
	}
	signInConditions = @{
		devicePlatform = "windows"
		clientAppType = "mobileAppsAndDesktopClients"
		signInRiskLevel = "medium"
		userRiskLevel = "none"
		country = "US"
		ipAddress = "40.77.182.32"
		insiderRiskLevel = "moderate"
		authenticationFlow = @{
			transferMethod = "authenticationTransfer"
		}
		deviceInfo = @{
			profileType = "Standard"
		}
	}
	appliedPoliciesOnly = $true
}

Test-MgIdentityConditionalAccess -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.conditionalaccess.evaluate.evaluate_post_request_body import EvaluatePostRequestBody
from msgraph.generated.models.user_sign_in import UserSignIn
from msgraph.generated.models.auth_context import AuthContext
from msgraph.generated.models.sign_in_conditions import SignInConditions
from msgraph.generated.models.conditional_access_device_platform import ConditionalAccessDevicePlatform
from msgraph.generated.models.conditional_access_client_app import ConditionalAccessClientApp
from msgraph.generated.models.risk_level import RiskLevel
from msgraph.generated.models.insider_risk_level import InsiderRiskLevel
from msgraph.generated.models.authentication_flow import AuthenticationFlow
from msgraph.generated.models.conditional_access_transfer_methods import ConditionalAccessTransferMethods
from msgraph.generated.models.device_info import DeviceInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluatePostRequestBody(
	sign_in_identity = UserSignIn(
		odata_type = "#microsoft.graph.userSignIn",
		user_id = "15dc174b-f34c-4588-ac45-61d6e05dce93",
	),
	sign_in_context = AuthContext(
		odata_type = "#microsoft.graph.authContext",
		authentication_context_value = "c37",
	),
	sign_in_conditions = SignInConditions(
		device_platform = ConditionalAccessDevicePlatform.Windows,
		client_app_type = ConditionalAccessClientApp.MobileAppsAndDesktopClients,
		sign_in_risk_level = RiskLevel.Medium,
		user_risk_level = RiskLevel.None,
		country = "US",
		ip_address = "40.77.182.32",
		insider_risk_level = InsiderRiskLevel.Moderate,
		authentication_flow = AuthenticationFlow(
			transfer_method = ConditionalAccessTransferMethods.AuthenticationTransfer,
		),
		device_info = DeviceInfo(
			profile_type = "Standard",
		),
	),
	applied_policies_only = True,
)

result = await graph_client.identity.conditional_access.evaluate.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json


{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.whatIfAnalysisResult)",
    "value": [
        {
            "id": "e897c693-c0e6-4386-abc3-f46dee5940fb",
            "templateId": null,
            "displayName": "All users_auth context_No conditions_Auth strength MFA",
            "createdDateTime": "2023-07-10T17:27:37.9735926Z",
            "modifiedDateTime": "2025-03-27T20:03:41.92628Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "partialEnablementStrategy": null,
            "sessionControls": null,
            "conditions": {
                "userRiskLevels": [],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "locations": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "clientApplications": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [],
                    "excludeApplications": [],
                    "includeUserActions": [],
                    "includeAuthenticationContextClassReferences": [
                        "c1",
                        "c37"
                    ],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [
                        "All"
                    ],
                    "excludeUsers": [],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                }
            },
            "grantControls": {
                "operator": "OR",
                "builtInControls": [],
                "customAuthenticationFactors": [],
                "termsOfUse": [],
                "authenticationStrength": {
                    "id": "00000000-0000-0000-0000-000000000002",
                    "createdDateTime": "2021-12-01T08:00:00Z",
                    "modifiedDateTime": "2021-12-01T08:00:00Z",
                    "displayName": "Multifactor authentication",
                    "description": "Combinations of methods that satisfy strong authentication, such as a password + SMS",
                    "policyType": "builtIn",
                    "requirementsSatisfied": "mfa",
                    "allowedCombinations": [
                        "windowsHelloForBusiness",
                        "fido2",
                        "x509CertificateMultiFactor",
                        "deviceBasedPush",
                        "temporaryAccessPassOneTime",
                        "temporaryAccessPassMultiUse",
                        "password,microsoftAuthenticatorPush",
                        "password,softwareOath",
                        "password,hardwareOath",
                        "password,x509CertificateSingleFactor",
                        "password,x509CertificateMultiFactor",
                        "password,sms",
                        "password,voice",
                        "federatedMultiFactor",
                        "microsoftAuthenticatorPush,federatedSingleFactor",
                        "softwareOath,federatedSingleFactor",
                        "hardwareOath,federatedSingleFactor",
                        "sms,federatedSingleFactor",
                        "voice,federatedSingleFactor"
                    ],
                    "combinationConfigurations": []
                }
            }
        }
    ]
}
```

### Example 3: Identify conditional access policies that would apply to a user performing a user action

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
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/evaluate
Content-Type: application/json

{
    "signInIdentity": {
        "@odata.type": "#microsoft.graph.userSignIn",
        "userId": "15dc174b-f34c-4588-ac45-61d6e05dce93"
    },
    "signInContext": {
        "@odata.type": "#microsoft.graph.userActionContext",
        "userAction": "registerSecurityInformation"
    },
    "signInConditions": {
        "devicePlatform": "macOS",
        "clientAppType": "browser",
        "signInRiskLevel": "low",
        "userRiskLevel": "high",
        "servicePrincipalRiskLevel": "none",
        "country": "CA",
        "ipAddress": "40.77.182.32",
        "insiderRiskLevel": "minor",
        "authenticationFlow": {
            "transferMethod": "deviceCodeFlow"
        },
        "deviceInfo": {
            "trustType": "EntraID"
        }
    },
    "appliedPoliciesOnly": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Identity.ConditionalAccess.Evaluate;
using Microsoft.Graph.Models;

var requestBody = new EvaluatePostRequestBody
{
	SignInIdentity = new UserSignIn
	{
		OdataType = "#microsoft.graph.userSignIn",
		UserId = "15dc174b-f34c-4588-ac45-61d6e05dce93",
	},
	SignInContext = new UserActionContext
	{
		OdataType = "#microsoft.graph.userActionContext",
		UserAction = UserAction.RegisterSecurityInformation,
	},
	SignInConditions = new SignInConditions
	{
		DevicePlatform = ConditionalAccessDevicePlatform.MacOS,
		ClientAppType = ConditionalAccessClientApp.Browser,
		SignInRiskLevel = RiskLevel.Low,
		UserRiskLevel = RiskLevel.High,
		ServicePrincipalRiskLevel = RiskLevel.None,
		Country = "CA",
		IpAddress = "40.77.182.32",
		InsiderRiskLevel = InsiderRiskLevel.Minor,
		AuthenticationFlow = new AuthenticationFlow
		{
			TransferMethod = ConditionalAccessTransferMethods.DeviceCodeFlow,
		},
		DeviceInfo = new DeviceInfo
		{
			TrustType = "EntraID",
		},
	},
	AppliedPoliciesOnly = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Evaluate.PostAsEvaluatePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentity.NewEvaluatePostRequestBody()
signInIdentity := graphmodels.NewUserSignIn()
userId := "15dc174b-f34c-4588-ac45-61d6e05dce93"
signInIdentity.SetUserId(&userId) 
requestBody.SetSignInIdentity(signInIdentity)
signInContext := graphmodels.NewUserActionContext()
userAction := graphmodels.REGISTERSECURITYINFORMATION_USERACTION 
signInContext.SetUserAction(&userAction) 
requestBody.SetSignInContext(signInContext)
signInConditions := graphmodels.NewSignInConditions()
devicePlatform := graphmodels.MACOS_CONDITIONALACCESSDEVICEPLATFORM 
signInConditions.SetDevicePlatform(&devicePlatform) 
clientAppType := graphmodels.BROWSER_CONDITIONALACCESSCLIENTAPP 
signInConditions.SetClientAppType(&clientAppType) 
signInRiskLevel := graphmodels.LOW_RISKLEVEL 
signInConditions.SetSignInRiskLevel(&signInRiskLevel) 
userRiskLevel := graphmodels.HIGH_RISKLEVEL 
signInConditions.SetUserRiskLevel(&userRiskLevel) 
servicePrincipalRiskLevel := graphmodels.NONE_RISKLEVEL 
signInConditions.SetServicePrincipalRiskLevel(&servicePrincipalRiskLevel) 
country := "CA"
signInConditions.SetCountry(&country) 
ipAddress := "40.77.182.32"
signInConditions.SetIpAddress(&ipAddress) 
insiderRiskLevel := graphmodels.MINOR_INSIDERRISKLEVEL 
signInConditions.SetInsiderRiskLevel(&insiderRiskLevel) 
authenticationFlow := graphmodels.NewAuthenticationFlow()
transferMethod := graphmodels.DEVICECODEFLOW_CONDITIONALACCESSTRANSFERMETHODS 
authenticationFlow.SetTransferMethod(&transferMethod) 
signInConditions.SetAuthenticationFlow(authenticationFlow)
deviceInfo := graphmodels.NewDeviceInfo()
trustType := "EntraID"
deviceInfo.SetTrustType(&trustType) 
signInConditions.SetDeviceInfo(deviceInfo)
requestBody.SetSignInConditions(signInConditions)
appliedPoliciesOnly := true
requestBody.SetAppliedPoliciesOnly(&appliedPoliciesOnly) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
evaluate, err := graphClient.Identity().ConditionalAccess().Evaluate().PostAsEvaluatePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody evaluatePostRequestBody = new com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody();
UserSignIn signInIdentity = new UserSignIn();
signInIdentity.setOdataType("#microsoft.graph.userSignIn");
signInIdentity.setUserId("15dc174b-f34c-4588-ac45-61d6e05dce93");
evaluatePostRequestBody.setSignInIdentity(signInIdentity);
UserActionContext signInContext = new UserActionContext();
signInContext.setOdataType("#microsoft.graph.userActionContext");
signInContext.setUserAction(UserAction.RegisterSecurityInformation);
evaluatePostRequestBody.setSignInContext(signInContext);
SignInConditions signInConditions = new SignInConditions();
signInConditions.setDevicePlatform(ConditionalAccessDevicePlatform.MacOS);
signInConditions.setClientAppType(ConditionalAccessClientApp.Browser);
signInConditions.setSignInRiskLevel(RiskLevel.Low);
signInConditions.setUserRiskLevel(RiskLevel.High);
signInConditions.setServicePrincipalRiskLevel(RiskLevel.None);
signInConditions.setCountry("CA");
signInConditions.setIpAddress("40.77.182.32");
signInConditions.setInsiderRiskLevel(InsiderRiskLevel.Minor);
AuthenticationFlow authenticationFlow = new AuthenticationFlow();
authenticationFlow.setTransferMethod(EnumSet.of(ConditionalAccessTransferMethods.DeviceCodeFlow));
signInConditions.setAuthenticationFlow(authenticationFlow);
DeviceInfo deviceInfo = new DeviceInfo();
deviceInfo.setTrustType("EntraID");
signInConditions.setDeviceInfo(deviceInfo);
evaluatePostRequestBody.setSignInConditions(signInConditions);
evaluatePostRequestBody.setAppliedPoliciesOnly(true);
var result = graphClient.identity().conditionalAccess().evaluate().post(evaluatePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const whatIfAnalysisResult = {
    signInIdentity: {
        '@odata.type': '#microsoft.graph.userSignIn',
        userId: '15dc174b-f34c-4588-ac45-61d6e05dce93'
    },
    signInContext: {
        '@odata.type': '#microsoft.graph.userActionContext',
        userAction: 'registerSecurityInformation'
    },
    signInConditions: {
        devicePlatform: 'macOS',
        clientAppType: 'browser',
        signInRiskLevel: 'low',
        userRiskLevel: 'high',
        servicePrincipalRiskLevel: 'none',
        country: 'CA',
        ipAddress: '40.77.182.32',
        insiderRiskLevel: 'minor',
        authenticationFlow: {
            transferMethod: 'deviceCodeFlow'
        },
        deviceInfo: {
            trustType: 'EntraID'
        }
    },
    appliedPoliciesOnly: true
};

await client.api('/identity/conditionalAccess/evaluate')
	.post(whatIfAnalysisResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\ConditionalAccess\Evaluate\EvaluatePostRequestBody;
use Microsoft\Graph\Generated\Models\UserSignIn;
use Microsoft\Graph\Generated\Models\UserActionContext;
use Microsoft\Graph\Generated\Models\UserAction;
use Microsoft\Graph\Generated\Models\SignInConditions;
use Microsoft\Graph\Generated\Models\ConditionalAccessDevicePlatform;
use Microsoft\Graph\Generated\Models\ConditionalAccessClientApp;
use Microsoft\Graph\Generated\Models\RiskLevel;
use Microsoft\Graph\Generated\Models\InsiderRiskLevel;
use Microsoft\Graph\Generated\Models\AuthenticationFlow;
use Microsoft\Graph\Generated\Models\ConditionalAccessTransferMethods;
use Microsoft\Graph\Generated\Models\DeviceInfo;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluatePostRequestBody();
$signInIdentity = new UserSignIn();
$signInIdentity->setOdataType('#microsoft.graph.userSignIn');
$signInIdentity->setUserId('15dc174b-f34c-4588-ac45-61d6e05dce93');
$requestBody->setSignInIdentity($signInIdentity);
$signInContext = new UserActionContext();
$signInContext->setOdataType('#microsoft.graph.userActionContext');
$signInContext->setUserAction(new UserAction('registerSecurityInformation'));
$requestBody->setSignInContext($signInContext);
$signInConditions = new SignInConditions();
$signInConditions->setDevicePlatform(new ConditionalAccessDevicePlatform('macOS'));
$signInConditions->setClientAppType(new ConditionalAccessClientApp('browser'));
$signInConditions->setSignInRiskLevel(new RiskLevel('low'));
$signInConditions->setUserRiskLevel(new RiskLevel('high'));
$signInConditions->setServicePrincipalRiskLevel(new RiskLevel('none'));
$signInConditions->setCountry('CA');
$signInConditions->setIpAddress('40.77.182.32');
$signInConditions->setInsiderRiskLevel(new InsiderRiskLevel('minor'));
$signInConditionsAuthenticationFlow = new AuthenticationFlow();
$signInConditionsAuthenticationFlow->setTransferMethod(new ConditionalAccessTransferMethods('deviceCodeFlow'));
$signInConditions->setAuthenticationFlow($signInConditionsAuthenticationFlow);
$signInConditionsDeviceInfo = new DeviceInfo();
$signInConditionsDeviceInfo->setTrustType('EntraID');
$signInConditions->setDeviceInfo($signInConditionsDeviceInfo);
$requestBody->setSignInConditions($signInConditions);
$requestBody->setAppliedPoliciesOnly(true);

$result = $graphServiceClient->identity()->conditionalAccess()->evaluate()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	signInIdentity = @{
		"@odata.type" = "#microsoft.graph.userSignIn"
		userId = "15dc174b-f34c-4588-ac45-61d6e05dce93"
	}
	signInContext = @{
		"@odata.type" = "#microsoft.graph.userActionContext"
		userAction = "registerSecurityInformation"
	}
	signInConditions = @{
		devicePlatform = "macOS"
		clientAppType = "browser"
		signInRiskLevel = "low"
		userRiskLevel = "high"
		servicePrincipalRiskLevel = "none"
		country = "CA"
		ipAddress = "40.77.182.32"
		insiderRiskLevel = "minor"
		authenticationFlow = @{
			transferMethod = "deviceCodeFlow"
		}
		deviceInfo = @{
			trustType = "EntraID"
		}
	}
	appliedPoliciesOnly = $true
}

Test-MgIdentityConditionalAccess -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.conditionalaccess.evaluate.evaluate_post_request_body import EvaluatePostRequestBody
from msgraph.generated.models.user_sign_in import UserSignIn
from msgraph.generated.models.user_action_context import UserActionContext
from msgraph.generated.models.user_action import UserAction
from msgraph.generated.models.sign_in_conditions import SignInConditions
from msgraph.generated.models.conditional_access_device_platform import ConditionalAccessDevicePlatform
from msgraph.generated.models.conditional_access_client_app import ConditionalAccessClientApp
from msgraph.generated.models.risk_level import RiskLevel
from msgraph.generated.models.insider_risk_level import InsiderRiskLevel
from msgraph.generated.models.authentication_flow import AuthenticationFlow
from msgraph.generated.models.conditional_access_transfer_methods import ConditionalAccessTransferMethods
from msgraph.generated.models.device_info import DeviceInfo
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluatePostRequestBody(
	sign_in_identity = UserSignIn(
		odata_type = "#microsoft.graph.userSignIn",
		user_id = "15dc174b-f34c-4588-ac45-61d6e05dce93",
	),
	sign_in_context = UserActionContext(
		odata_type = "#microsoft.graph.userActionContext",
		user_action = UserAction.RegisterSecurityInformation,
	),
	sign_in_conditions = SignInConditions(
		device_platform = ConditionalAccessDevicePlatform.MacOS,
		client_app_type = ConditionalAccessClientApp.Browser,
		sign_in_risk_level = RiskLevel.Low,
		user_risk_level = RiskLevel.High,
		service_principal_risk_level = RiskLevel.None,
		country = "CA",
		ip_address = "40.77.182.32",
		insider_risk_level = InsiderRiskLevel.Minor,
		authentication_flow = AuthenticationFlow(
			transfer_method = ConditionalAccessTransferMethods.DeviceCodeFlow,
		),
		device_info = DeviceInfo(
			trust_type = "EntraID",
		),
	),
	applied_policies_only = True,
)

result = await graph_client.identity.conditional_access.evaluate.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.whatIfAnalysisResult)",
    "value": [
        {
            "id": "37d51c45-8c60-4f82-98e0-6e1451cecf7c",
            "templateId": null,
            "displayName": "All Users except au1_All resources_user risk H_Password change",
            "createdDateTime": "2022-03-31T22:59:59.6688974Z",
            "modifiedDateTime": "2025-03-27T19:55:43.5390544Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "partialEnablementStrategy": null,
            "sessionControls": null,
            "conditions": {
                "userRiskLevels": [
                    "high"
                ],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "locations": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "clientApplications": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [
                        "All"
                    ],
                    "excludeApplications": [],
                    "includeUserActions": [],
                    "includeAuthenticationContextClassReferences": [],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [
                        "All"
                    ],
                    "excludeUsers": [
                        "f7ca74b0-8562-4083-b66c-0476f942cfd0"
                    ],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                }
            },
            "grantControls": {
                "operator": "AND",
                "builtInControls": [
                    "mfa",
                    "passwordChange"
                ],
                "customAuthenticationFactors": [],
                "termsOfUse": [],
                "authenticationStrength": null
            }
        },
        {
            "id": "4aa7d105-d92b-4c07-9834-0e810ddb89ac",
            "templateId": null,
            "displayName": "All admin roles except au1_All resources_No conditions_MFA",
            "createdDateTime": "2022-03-29T20:39:24.3899939Z",
            "modifiedDateTime": "2025-03-27T21:40:19.6686701Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "partialEnablementStrategy": null,
            "sessionControls": null,
            "conditions": {
                "userRiskLevels": [],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "locations": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "clientApplications": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [
                        "All"
                    ],
                    "excludeApplications": [],
                    "includeUserActions": [],
                    "includeAuthenticationContextClassReferences": [],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [],
                    "excludeUsers": [
                        "f7ca74b0-8562-4083-b66c-0476f942cfd0"
                    ],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [
                        "62e90394-69f5-4237-9190-012177145e10",
                        "194ae4cb-b126-40b2-bd5b-6091b380977d",
                        "f28a1f50-f6e7-4571-818b-6a12f2af6b6c",
                        "29232cdf-9323-42fd-ade2-1d097af3e4de",
                        "b1be1c3e-b65d-4f19-8427-f6fa0d97feb9",
                        "729827e3-9c14-49f7-bb1b-9608f156bbb8",
                        "b0f54661-2d74-4c50-afa3-1ec803f12efe",
                        "fe930be7-5e62-47db-91af-98c3a49a38b1",
                        "c4e39bd9-1100-46d3-8c65-fb160da0071f",
                        "9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
                        "158c047a-c907-4556-b7ef-446551a6b5f7",
                        "966707d0-3269-4727-9be2-8c3a10f19b9d",
                        "7be44c8a-adaf-4e2a-84d6-ab2649e08a13",
                        "e8611ab8-c189-46e8-94e1-60213ab1f814"
                    ],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                }
            },
            "grantControls": {
                "operator": "OR",
                "builtInControls": [
                    "mfa"
                ],
                "customAuthenticationFactors": [],
                "termsOfUse": [],
                "authenticationStrength": null
            }
        },
        {
            "id": "11083471-5a50-43ad-90c0-23f1af0869e1",
            "templateId": null,
            "displayName": "All users except au1_User action RS info_No conditions_Auth strenfth MFA",
            "createdDateTime": "2024-10-16T15:06:45.0788027Z",
            "modifiedDateTime": "2025-03-27T20:08:22.6064571Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "partialEnablementStrategy": null,
            "sessionControls": null,
            "conditions": {
                "userRiskLevels": [],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "locations": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "clientApplications": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [],
                    "excludeApplications": [],
                    "includeUserActions": [
                        "urn:user:registersecurityinfo"
                    ],
                    "includeAuthenticationContextClassReferences": [],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [
                        "All"
                    ],
                    "excludeUsers": [
                        "f7ca74b0-8562-4083-b66c-0476f942cfd0"
                    ],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                }
            },
            "grantControls": {
                "operator": "OR",
                "builtInControls": [],
                "customAuthenticationFactors": [],
                "termsOfUse": [],
                "authenticationStrength": {
                    "id": "00000000-0000-0000-0000-000000000002",
                    "createdDateTime": "2021-12-01T08:00:00Z",
                    "modifiedDateTime": "2021-12-01T08:00:00Z",
                    "displayName": "Multifactor authentication",
                    "description": "Combinations of methods that satisfy strong authentication, such as a password + SMS",
                    "policyType": "builtIn",
                    "requirementsSatisfied": "mfa",
                    "allowedCombinations": [
                        "windowsHelloForBusiness",
                        "fido2",
                        "x509CertificateMultiFactor",
                        "deviceBasedPush",
                        "temporaryAccessPassOneTime",
                        "temporaryAccessPassMultiUse",
                        "password,microsoftAuthenticatorPush",
                        "password,softwareOath",
                        "password,hardwareOath",
                        "password,x509CertificateSingleFactor",
                        "password,x509CertificateMultiFactor",
                        "password,sms",
                        "password,voice",
                        "federatedMultiFactor",
                        "microsoftAuthenticatorPush,federatedSingleFactor",
                        "softwareOath,federatedSingleFactor",
                        "hardwareOath,federatedSingleFactor",
                        "sms,federatedSingleFactor",
                        "voice,federatedSingleFactor"
                    ],
                    "combinationConfigurations": []
                }
            }
        }
    ]
}
```

### Example 4: Identify conditional access policies that apply to a service principal

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

```http
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/evaluate
Content-Type: application/json

{
    "signInIdentity": {
        "@odata.type": "#microsoft.graph.servicePrincipalSignIn",
        "servicePrincipalId": "c65b94a5-0049-439a-a6fd-bce307077730"
    },
    "signInContext": {
        "@odata.type": "#microsoft.graph.applicationContext",
        "includeApplications": [
            "00000003-0000-0ff1-ce00-000000000000"
        ]
    },
    "signInConditions": {
        "servicePrincipalRiskLevel": "high",
        "country": "CA",
        "ipAddress": "40.77.182.32"
    },
    "appliedPoliciesOnly": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Identity.ConditionalAccess.Evaluate;
using Microsoft.Graph.Models;

var requestBody = new EvaluatePostRequestBody
{
	SignInIdentity = new ServicePrincipalSignIn
	{
		OdataType = "#microsoft.graph.servicePrincipalSignIn",
		ServicePrincipalId = "c65b94a5-0049-439a-a6fd-bce307077730",
	},
	SignInContext = new ApplicationContext
	{
		OdataType = "#microsoft.graph.applicationContext",
		IncludeApplications = new List<string>
		{
			"00000003-0000-0ff1-ce00-000000000000",
		},
	},
	SignInConditions = new SignInConditions
	{
		ServicePrincipalRiskLevel = RiskLevel.High,
		Country = "CA",
		IpAddress = "40.77.182.32",
	},
	AppliedPoliciesOnly = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Evaluate.PostAsEvaluatePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentity "github.com/microsoftgraph/msgraph-sdk-go/identity"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentity.NewEvaluatePostRequestBody()
signInIdentity := graphmodels.NewServicePrincipalSignIn()
servicePrincipalId := "c65b94a5-0049-439a-a6fd-bce307077730"
signInIdentity.SetServicePrincipalId(&servicePrincipalId) 
requestBody.SetSignInIdentity(signInIdentity)
signInContext := graphmodels.NewApplicationContext()
includeApplications := []string {
	"00000003-0000-0ff1-ce00-000000000000",
}
signInContext.SetIncludeApplications(includeApplications)
requestBody.SetSignInContext(signInContext)
signInConditions := graphmodels.NewSignInConditions()
servicePrincipalRiskLevel := graphmodels.HIGH_RISKLEVEL 
signInConditions.SetServicePrincipalRiskLevel(&servicePrincipalRiskLevel) 
country := "CA"
signInConditions.SetCountry(&country) 
ipAddress := "40.77.182.32"
signInConditions.SetIpAddress(&ipAddress) 
requestBody.SetSignInConditions(signInConditions)
appliedPoliciesOnly := true
requestBody.SetAppliedPoliciesOnly(&appliedPoliciesOnly) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
evaluate, err := graphClient.Identity().ConditionalAccess().Evaluate().PostAsEvaluatePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody evaluatePostRequestBody = new com.microsoft.graph.identity.conditionalaccess.evaluate.EvaluatePostRequestBody();
ServicePrincipalSignIn signInIdentity = new ServicePrincipalSignIn();
signInIdentity.setOdataType("#microsoft.graph.servicePrincipalSignIn");
signInIdentity.setServicePrincipalId("c65b94a5-0049-439a-a6fd-bce307077730");
evaluatePostRequestBody.setSignInIdentity(signInIdentity);
ApplicationContext signInContext = new ApplicationContext();
signInContext.setOdataType("#microsoft.graph.applicationContext");
LinkedList<String> includeApplications = new LinkedList<String>();
includeApplications.add("00000003-0000-0ff1-ce00-000000000000");
signInContext.setIncludeApplications(includeApplications);
evaluatePostRequestBody.setSignInContext(signInContext);
SignInConditions signInConditions = new SignInConditions();
signInConditions.setServicePrincipalRiskLevel(RiskLevel.High);
signInConditions.setCountry("CA");
signInConditions.setIpAddress("40.77.182.32");
evaluatePostRequestBody.setSignInConditions(signInConditions);
evaluatePostRequestBody.setAppliedPoliciesOnly(true);
var result = graphClient.identity().conditionalAccess().evaluate().post(evaluatePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const whatIfAnalysisResult = {
    signInIdentity: {
        '@odata.type': '#microsoft.graph.servicePrincipalSignIn',
        servicePrincipalId: 'c65b94a5-0049-439a-a6fd-bce307077730'
    },
    signInContext: {
        '@odata.type': '#microsoft.graph.applicationContext',
        includeApplications: [
            '00000003-0000-0ff1-ce00-000000000000'
        ]
    },
    signInConditions: {
        servicePrincipalRiskLevel: 'high',
        country: 'CA',
        ipAddress: '40.77.182.32'
    },
    appliedPoliciesOnly: true
};

await client.api('/identity/conditionalAccess/evaluate')
	.post(whatIfAnalysisResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Identity\ConditionalAccess\Evaluate\EvaluatePostRequestBody;
use Microsoft\Graph\Generated\Models\ServicePrincipalSignIn;
use Microsoft\Graph\Generated\Models\ApplicationContext;
use Microsoft\Graph\Generated\Models\SignInConditions;
use Microsoft\Graph\Generated\Models\RiskLevel;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EvaluatePostRequestBody();
$signInIdentity = new ServicePrincipalSignIn();
$signInIdentity->setOdataType('#microsoft.graph.servicePrincipalSignIn');
$signInIdentity->setServicePrincipalId('c65b94a5-0049-439a-a6fd-bce307077730');
$requestBody->setSignInIdentity($signInIdentity);
$signInContext = new ApplicationContext();
$signInContext->setOdataType('#microsoft.graph.applicationContext');
$signInContext->setIncludeApplications(['00000003-0000-0ff1-ce00-000000000000', 	]);
$requestBody->setSignInContext($signInContext);
$signInConditions = new SignInConditions();
$signInConditions->setServicePrincipalRiskLevel(new RiskLevel('high'));
$signInConditions->setCountry('CA');
$signInConditions->setIpAddress('40.77.182.32');
$requestBody->setSignInConditions($signInConditions);
$requestBody->setAppliedPoliciesOnly(true);

$result = $graphServiceClient->identity()->conditionalAccess()->evaluate()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	signInIdentity = @{
		"@odata.type" = "#microsoft.graph.servicePrincipalSignIn"
		servicePrincipalId = "c65b94a5-0049-439a-a6fd-bce307077730"
	}
	signInContext = @{
		"@odata.type" = "#microsoft.graph.applicationContext"
		includeApplications = @(
		"00000003-0000-0ff1-ce00-000000000000"
	)
}
signInConditions = @{
	servicePrincipalRiskLevel = "high"
	country = "CA"
	ipAddress = "40.77.182.32"
}
appliedPoliciesOnly = $true
}

Test-MgIdentityConditionalAccess -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity.conditionalaccess.evaluate.evaluate_post_request_body import EvaluatePostRequestBody
from msgraph.generated.models.service_principal_sign_in import ServicePrincipalSignIn
from msgraph.generated.models.application_context import ApplicationContext
from msgraph.generated.models.sign_in_conditions import SignInConditions
from msgraph.generated.models.risk_level import RiskLevel
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EvaluatePostRequestBody(
	sign_in_identity = ServicePrincipalSignIn(
		odata_type = "#microsoft.graph.servicePrincipalSignIn",
		service_principal_id = "c65b94a5-0049-439a-a6fd-bce307077730",
	),
	sign_in_context = ApplicationContext(
		odata_type = "#microsoft.graph.applicationContext",
		include_applications = [
			"00000003-0000-0ff1-ce00-000000000000",
		],
	),
	sign_in_conditions = SignInConditions(
		service_principal_risk_level = RiskLevel.High,
		country = "CA",
		ip_address = "40.77.182.32",
	),
	applied_policies_only = True,
)

result = await graph_client.identity.conditional_access.evaluate.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.whatIfAnalysisResult)",
    "value": [
        {
            "id": "461478d2-5896-4761-84ba-4d241c396a29",
            "templateId": null,
            "displayName": "All ST SPs_All resources_Any location_Block",
            "createdDateTime": "2022-04-08T19:31:15.6087842Z",
            "modifiedDateTime": "2025-03-27T20:08:54.0912734Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "partialEnablementStrategy": null,
            "sessionControls": null,
            "conditions": {
                "userRiskLevels": [],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [
                        "All"
                    ],
                    "excludeApplications": [],
                    "includeUserActions": [],
                    "includeAuthenticationContextClassReferences": [],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [
                        "None"
                    ],
                    "excludeUsers": [],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                },
                "locations": {
                    "includeLocations": [
                        "All"
                    ],
                    "excludeLocations": []
                },
                "clientApplications": {
                    "includeServicePrincipals": [
                        "ServicePrincipalsInMyTenant"
                    ],
                    "excludeServicePrincipals": [],
                    "servicePrincipalFilter": null
                }
            },
            "grantControls": {
                "operator": "OR",
                "builtInControls": [
                    "block"
                ],
                "customAuthenticationFactors": [],
                "termsOfUse": [],
                "authenticationStrength": null
            }
        },
        {
            "id": "4f1d2ff3-50db-4299-bbdd-0a114c98e97e",
            "templateId": null,
            "displayName": "All ST SPs_All resources_No conditions_Block",
            "createdDateTime": "2025-02-21T07:04:44.777856Z",
            "modifiedDateTime": "2025-03-28T06:15:41.2376665Z",
            "state": "enabledForReportingButNotEnforced",
            "policyApplies": true,
            "analysisReasons": "notSet",
            "partialEnablementStrategy": null,
            "sessionControls": null,
            "conditions": {
                "userRiskLevels": [],
                "signInRiskLevels": [],
                "clientAppTypes": [
                    "all"
                ],
                "servicePrincipalRiskLevels": [],
                "insiderRiskLevels": null,
                "clients": null,
                "platforms": null,
                "locations": null,
                "times": null,
                "deviceStates": null,
                "devices": null,
                "authenticationFlows": null,
                "applications": {
                    "includeApplications": [
                        "All"
                    ],
                    "excludeApplications": [],
                    "includeUserActions": [],
                    "includeAuthenticationContextClassReferences": [],
                    "applicationFilter": null,
                    "networkAccess": null,
                    "globalSecureAccess": null
                },
                "users": {
                    "includeUsers": [
                        "None"
                    ],
                    "excludeUsers": [],
                    "includeGroups": [],
                    "excludeGroups": [],
                    "includeRoles": [],
                    "excludeRoles": [],
                    "includeGuestsOrExternalUsers": null,
                    "excludeGuestsOrExternalUsers": null
                },
                "clientApplications": {
                    "includeServicePrincipals": [
                        "ServicePrincipalsInMyTenant"
                    ],
                    "excludeServicePrincipals": [],
                    "servicePrincipalFilter": null
                }
            },
            "grantControls": {
                "operator": "OR",
                "builtInControls": [
                    "block"
                ],
                "customAuthenticationFactors": [],
                "termsOfUse": [],
                "authenticationStrength": null
            }
        }
    ]
}
```
