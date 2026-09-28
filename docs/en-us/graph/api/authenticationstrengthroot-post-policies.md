<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-post-policies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create authenticationStrengthPolicy

Namespace: microsoft.graph

Create a new custom [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ConditionalAccess | Policy.ReadWrite.AuthenticationMethod |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ConditionalAccess | Policy.ReadWrite.AuthenticationMethod |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Conditional Access administrator
- Security Administrator

## HTTP request

```http
POST /policies/authenticationStrengthPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object.

You can specify the following properties when creating an **authenticationStrengthPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the policy to be created. Required. |
| description | String | The description of the policy to be created. Optional. |
| allowedCombinations | authenticationMethodModes collection | The authentication method combinations allowed by this authentication strength policy. The possible values of this flagged enum are: `password`, `voice`, `hardwareOath`, `softwareOath`, `sms`, `fido2`, `windowsHelloForBusiness`, `microsoftAuthenticatorPush`, `deviceBasedPush`, `temporaryAccessPassOneTime`, `temporaryAccessPassMultiUse`, `email`, `x509CertificateSingleFactor`, `x509CertificateMultiFactor`, `federatedSingleFactor`, `federatedMultiFactor`, `unknownFutureValue`. For the list of allowed combinations, call the [List authenticationMethodModes](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-list-authenticationmethodmodes?view=graph-rest-1.0) API. Required. |

## Response

If successful, this method returns a `201 Created` response code and an [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/policies/authenticationStrengthPolicies
Content-Type: application/json

{
    "displayName": "Example",
    "requirementsSatisfied": "mfa",
    "allowedCombinations": [
        "fido2"
    ],
    "combinationConfigurations@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies('5790842a-5bab-44c2-9cf1-b38d675b70ea')/combinationConfigurations",
    "combinationConfigurations": [
        {
            "@odata.type": "#microsoft.graph.fido2CombinationConfiguration",
            "id": "42235320-c8db-4d8c-9344-8f1ce87f734b",
            "appliesToCombinations": [
                "fido2"
            ],
            "allowedAAGUIDs": [
                "de1e552d-db1d-4423-a619-566b625cdc84",
                "90a3ccdf-635c-4729-a248-9b709135078f"
            ]
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AuthenticationStrengthPolicy
{
	DisplayName = "Example",
	RequirementsSatisfied = AuthenticationStrengthRequirements.Mfa,
	AllowedCombinations = new List<AuthenticationMethodModes?>
	{
		AuthenticationMethodModes.Fido2,
	},
	CombinationConfigurations = new List<AuthenticationCombinationConfiguration>
	{
		new Fido2CombinationConfiguration
		{
			OdataType = "#microsoft.graph.fido2CombinationConfiguration",
			Id = "42235320-c8db-4d8c-9344-8f1ce87f734b",
			AppliesToCombinations = new List<AuthenticationMethodModes?>
			{
				AuthenticationMethodModes.Fido2,
			},
			AllowedAAGUIDs = new List<string>
			{
				"de1e552d-db1d-4423-a619-566b625cdc84",
				"90a3ccdf-635c-4729-a248-9b709135078f",
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"combinationConfigurations@odata.context" , "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies('5790842a-5bab-44c2-9cf1-b38d675b70ea')/combinationConfigurations"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.AuthenticationStrengthPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationStrengthPolicy()
displayName := "Example"
requestBody.SetDisplayName(&displayName) 
requirementsSatisfied := graphmodels.MFA_AUTHENTICATIONSTRENGTHREQUIREMENTS 
requestBody.SetRequirementsSatisfied(&requirementsSatisfied) 
allowedCombinations := []graphmodels.AuthenticationMethodModesable {
	authenticationMethodModes := graphmodels.FIDO2_AUTHENTICATIONMETHODMODES 
	requestBody.SetAuthenticationMethodModes(&authenticationMethodModes)
}
requestBody.SetAllowedCombinations(allowedCombinations)


authenticationCombinationConfiguration := graphmodels.NewFido2CombinationConfiguration()
id := "42235320-c8db-4d8c-9344-8f1ce87f734b"
authenticationCombinationConfiguration.SetId(&id) 
appliesToCombinations := []graphmodels.AuthenticationMethodModesable {
	authenticationMethodModes := graphmodels.FIDO2_AUTHENTICATIONMETHODMODES 
	authenticationCombinationConfiguration.SetAuthenticationMethodModes(&authenticationMethodModes)
}
authenticationCombinationConfiguration.SetAppliesToCombinations(appliesToCombinations)
allowedAAGUIDs := []string {
	"de1e552d-db1d-4423-a619-566b625cdc84",
	"90a3ccdf-635c-4729-a248-9b709135078f",
}
authenticationCombinationConfiguration.SetAllowedAAGUIDs(allowedAAGUIDs)

combinationConfigurations := []graphmodels.AuthenticationCombinationConfigurationable {
	authenticationCombinationConfiguration,
}
requestBody.SetCombinationConfigurations(combinationConfigurations)
additionalData := map[string]interface{}{
	"combinationConfigurations@odata.context" : "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies('5790842a-5bab-44c2-9cf1-b38d675b70ea')/combinationConfigurations", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationStrengthPolicies, err := graphClient.Policies().AuthenticationStrengthPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationStrengthPolicy authenticationStrengthPolicy = new AuthenticationStrengthPolicy();
authenticationStrengthPolicy.setDisplayName("Example");
authenticationStrengthPolicy.setRequirementsSatisfied(EnumSet.of(AuthenticationStrengthRequirements.Mfa));
LinkedList<AuthenticationMethodModes> allowedCombinations = new LinkedList<AuthenticationMethodModes>();
allowedCombinations.add(AuthenticationMethodModes.Fido2);
authenticationStrengthPolicy.setAllowedCombinations(allowedCombinations);
LinkedList<AuthenticationCombinationConfiguration> combinationConfigurations = new LinkedList<AuthenticationCombinationConfiguration>();
Fido2CombinationConfiguration authenticationCombinationConfiguration = new Fido2CombinationConfiguration();
authenticationCombinationConfiguration.setOdataType("#microsoft.graph.fido2CombinationConfiguration");
authenticationCombinationConfiguration.setId("42235320-c8db-4d8c-9344-8f1ce87f734b");
LinkedList<AuthenticationMethodModes> appliesToCombinations = new LinkedList<AuthenticationMethodModes>();
appliesToCombinations.add(AuthenticationMethodModes.Fido2);
authenticationCombinationConfiguration.setAppliesToCombinations(appliesToCombinations);
LinkedList<String> allowedAAGUIDs = new LinkedList<String>();
allowedAAGUIDs.add("de1e552d-db1d-4423-a619-566b625cdc84");
allowedAAGUIDs.add("90a3ccdf-635c-4729-a248-9b709135078f");
authenticationCombinationConfiguration.setAllowedAAGUIDs(allowedAAGUIDs);
combinationConfigurations.add(authenticationCombinationConfiguration);
authenticationStrengthPolicy.setCombinationConfigurations(combinationConfigurations);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("combinationConfigurations@odata.context", "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies('5790842a-5bab-44c2-9cf1-b38d675b70ea')/combinationConfigurations");
authenticationStrengthPolicy.setAdditionalData(additionalData);
AuthenticationStrengthPolicy result = graphClient.policies().authenticationStrengthPolicies().post(authenticationStrengthPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationStrengthPolicy = {
    displayName: 'Example',
    requirementsSatisfied: 'mfa',
    allowedCombinations: [
        'fido2'
    ],
    'combinationConfigurations@odata.context': 'https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies(\'5790842a-5bab-44c2-9cf1-b38d675b70ea\')/combinationConfigurations',
    combinationConfigurations: [
        {
            '@odata.type': '#microsoft.graph.fido2CombinationConfiguration',
            id: '42235320-c8db-4d8c-9344-8f1ce87f734b',
            appliesToCombinations: [
                'fido2'
            ],
            allowedAAGUIDs: [
                'de1e552d-db1d-4423-a619-566b625cdc84',
                '90a3ccdf-635c-4729-a248-9b709135078f'
            ]
        }
    ]
};

await client.api('/policies/authenticationStrengthPolicies')
	.post(authenticationStrengthPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AuthenticationStrengthPolicy;
use Microsoft\Graph\Generated\Models\AuthenticationStrengthRequirements;
use Microsoft\Graph\Generated\Models\AuthenticationMethodModes;
use Microsoft\Graph\Generated\Models\AuthenticationCombinationConfiguration;
use Microsoft\Graph\Generated\Models\Fido2CombinationConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AuthenticationStrengthPolicy();
$requestBody->setDisplayName('Example');
$requestBody->setRequirementsSatisfied(new AuthenticationStrengthRequirements('mfa'));
$requestBody->setAllowedCombinations([new AuthenticationMethodModes('fido2'),	]);
$combinationConfigurationsAuthenticationCombinationConfiguration1 = new Fido2CombinationConfiguration();
$combinationConfigurationsAuthenticationCombinationConfiguration1->setOdataType('#microsoft.graph.fido2CombinationConfiguration');
$combinationConfigurationsAuthenticationCombinationConfiguration1->setId('42235320-c8db-4d8c-9344-8f1ce87f734b');
$combinationConfigurationsAuthenticationCombinationConfiguration1->setAppliesToCombinations([new AuthenticationMethodModes('fido2'),	]);
$combinationConfigurationsAuthenticationCombinationConfiguration1->setAllowedAAGUIDs(['de1e552d-db1d-4423-a619-566b625cdc84', '90a3ccdf-635c-4729-a248-9b709135078f', 	]);
$combinationConfigurationsArray []= $combinationConfigurationsAuthenticationCombinationConfiguration1;
$requestBody->setCombinationConfigurations($combinationConfigurationsArray);

$additionalData = [
'combinationConfigurations@odata.context' => 'https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies(\'5790842a-5bab-44c2-9cf1-b38d675b70ea\')/combinationConfigurations',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->policies()->authenticationStrengthPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	displayName = "Example"
	requirementsSatisfied = "mfa"
	allowedCombinations = @(
	"fido2"
)
"combinationConfigurations@odata.context" = "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies('5790842a-5bab-44c2-9cf1-b38d675b70ea')/combinationConfigurations"
combinationConfigurations = @(
	@{
		"@odata.type" = "#microsoft.graph.fido2CombinationConfiguration"
		id = "42235320-c8db-4d8c-9344-8f1ce87f734b"
		appliesToCombinations = @(
		"fido2"
	)
	allowedAAGUIDs = @(
	"de1e552d-db1d-4423-a619-566b625cdc84"
"90a3ccdf-635c-4729-a248-9b709135078f"
)
}
)
}

New-MgPolicyAuthenticationStrengthPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.authentication_strength_policy import AuthenticationStrengthPolicy
from msgraph.generated.models.authentication_strength_requirements import AuthenticationStrengthRequirements
from msgraph.generated.models.authentication_method_modes import AuthenticationMethodModes
from msgraph.generated.models.authentication_combination_configuration import AuthenticationCombinationConfiguration
from msgraph.generated.models.fido2_combination_configuration import Fido2CombinationConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AuthenticationStrengthPolicy(
	display_name = "Example",
	requirements_satisfied = AuthenticationStrengthRequirements.Mfa,
	allowed_combinations = [
		AuthenticationMethodModes.Fido2,
	],
	combination_configurations = [
		Fido2CombinationConfiguration(
			odata_type = "#microsoft.graph.fido2CombinationConfiguration",
			id = "42235320-c8db-4d8c-9344-8f1ce87f734b",
			applies_to_combinations = [
				AuthenticationMethodModes.Fido2,
			],
			allowed_a_a_g_u_i_ds = [
				"de1e552d-db1d-4423-a619-566b625cdc84",
				"90a3ccdf-635c-4729-a248-9b709135078f",
			],
		),
	],
	additional_data = {
			"combination_configurations@odata_context" : "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies('5790842a-5bab-44c2-9cf1-b38d675b70ea')/combinationConfigurations",
	}
)

result = await graph_client.policies.authentication_strength_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies/$entity",
    "id": "7daf2132-6a2d-4e78-a699-b823babf4436",
    "createdDateTime": "2024-07-23T17:10:58.1492045Z",
    "modifiedDateTime": "2024-07-23T17:10:58.1492045Z",
    "displayName": "Example",
    "description": "",
    "policyType": "custom",
    "requirementsSatisfied": "mfa",
    "allowedCombinations": [
        "fido2"
    ],
    "combinationConfigurations@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/authenticationStrengthPolicies('7daf2132-6a2d-4e78-a699-b823babf4436')/combinationConfigurations",
    "combinationConfigurations": [
        {
            "@odata.type": "#microsoft.graph.fido2CombinationConfiguration",
            "id": "c0fdf2f9-3b3f-4bbf-988c-17606ea4b4e4",
            "appliesToCombinations": [
                "fido2"
            ],
            "allowedAAGUIDs": [
                "de1e552d-db1d-4423-a619-566b625cdc84",
                "90a3ccdf-635c-4729-a248-9b709135078f"
            ]
        }
    ]
}
```
