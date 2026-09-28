<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-post-combinationconfigurations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# Create authenticationCombinationConfiguration

Namespace: microsoft.graph

Create a new authenticationCombinationConfiguration object which can be of one of the following derived types:

- [fido2combinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fido2combinationconfiguration?view=graph-rest-1.0)
- [x509certificatecombinationconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificatecombinationconfiguration?view=graph-rest-1.0)

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
POST /identity/conditionalAccess/authenticationStrength/policies/{authenticationStrengthPolicyId}/combinationConfigurations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) object.

You can specify the following properties when creating an **authenticationCombinationConfiguration**. Additionally, you must supply the @odata.type and required properties of the derived type of [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) that you're creating. For example, `"@odata.type" : "#microsoft.graph.fido2CombinationConfiguration"`.

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesToCombinations | authenticationMethodModes collection | The combinations where this configuration applies. For **fido2combinationConfigurations** use `"fido2"`, for **x509certificatecombinationconfiguration** use `"x509CertificateSingleFactor"` or `"x509CertificateMultiFactor"`. Required. |

## Response

If successful, this method returns a `201 Created` response code and an [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) object which can be a [fido2combinationConfigurations](https://learn.microsoft.com/en-us/graph/api/resources/fido2combinationconfiguration?view=graph-rest-1.0) or an [x509certificatecombinationconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificatecombinationconfiguration?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a fido2combinationConfiguration object

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
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/authenticationStrength/policies/{authenticationStrengthPolicyId}/combinationConfigurations
Content-Type: application/json
Content-length: 130

{
  "@odata.type" : "#microsoft.graph.fido2CombinationConfiguration",
  "allowedAAGUIDs": [
    "486c3b50-889c-480a-abc5-c04ef7c873e0",
    "c042882f-a621-40c8-94d3-9cde3a826fed",
    "ec454c08-4c77-4012-9d48-45f7f0fccdfb"
  ],
  "appliesToCombinations": ["fido2"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Fido2CombinationConfiguration
{
	OdataType = "#microsoft.graph.fido2CombinationConfiguration",
	AllowedAAGUIDs = new List<string>
	{
		"486c3b50-889c-480a-abc5-c04ef7c873e0",
		"c042882f-a621-40c8-94d3-9cde3a826fed",
		"ec454c08-4c77-4012-9d48-45f7f0fccdfb",
	},
	AppliesToCombinations = new List<AuthenticationMethodModes?>
	{
		AuthenticationMethodModes.Fido2,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.AuthenticationStrength.Policies["{authenticationStrengthPolicy-id}"].CombinationConfigurations.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationCombinationConfiguration()
allowedAAGUIDs := []string {
	"486c3b50-889c-480a-abc5-c04ef7c873e0",
	"c042882f-a621-40c8-94d3-9cde3a826fed",
	"ec454c08-4c77-4012-9d48-45f7f0fccdfb",
}
requestBody.SetAllowedAAGUIDs(allowedAAGUIDs)
appliesToCombinations := []graphmodels.AuthenticationMethodModesable {
	authenticationMethodModes := graphmodels.FIDO2_AUTHENTICATIONMETHODMODES 
	requestBody.SetAuthenticationMethodModes(&authenticationMethodModes)
}
requestBody.SetAppliesToCombinations(appliesToCombinations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
combinationConfigurations, err := graphClient.Identity().ConditionalAccess().AuthenticationStrength().Policies().ByAuthenticationStrengthPolicyId("authenticationStrengthPolicy-id").CombinationConfigurations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Fido2CombinationConfiguration authenticationCombinationConfiguration = new Fido2CombinationConfiguration();
authenticationCombinationConfiguration.setOdataType("#microsoft.graph.fido2CombinationConfiguration");
LinkedList<String> allowedAAGUIDs = new LinkedList<String>();
allowedAAGUIDs.add("486c3b50-889c-480a-abc5-c04ef7c873e0");
allowedAAGUIDs.add("c042882f-a621-40c8-94d3-9cde3a826fed");
allowedAAGUIDs.add("ec454c08-4c77-4012-9d48-45f7f0fccdfb");
authenticationCombinationConfiguration.setAllowedAAGUIDs(allowedAAGUIDs);
LinkedList<AuthenticationMethodModes> appliesToCombinations = new LinkedList<AuthenticationMethodModes>();
appliesToCombinations.add(AuthenticationMethodModes.Fido2);
authenticationCombinationConfiguration.setAppliesToCombinations(appliesToCombinations);
AuthenticationCombinationConfiguration result = graphClient.identity().conditionalAccess().authenticationStrength().policies().byAuthenticationStrengthPolicyId("{authenticationStrengthPolicy-id}").combinationConfigurations().post(authenticationCombinationConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationCombinationConfiguration = {
  '@odata.type': '#microsoft.graph.fido2CombinationConfiguration',
  allowedAAGUIDs: [
    '486c3b50-889c-480a-abc5-c04ef7c873e0',
    'c042882f-a621-40c8-94d3-9cde3a826fed',
    'ec454c08-4c77-4012-9d48-45f7f0fccdfb'
  ],
  appliesToCombinations: ['fido2']
};

await client.api('/identity/conditionalAccess/authenticationStrength/policies/{authenticationStrengthPolicyId}/combinationConfigurations')
	.post(authenticationCombinationConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Fido2CombinationConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationMethodModes;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Fido2CombinationConfiguration();
$requestBody->setOdataType('#microsoft.graph.fido2CombinationConfiguration');
$requestBody->setAllowedAAGUIDs(['486c3b50-889c-480a-abc5-c04ef7c873e0', 'c042882f-a621-40c8-94d3-9cde3a826fed', 'ec454c08-4c77-4012-9d48-45f7f0fccdfb', 	]);
$requestBody->setAppliesToCombinations([new AuthenticationMethodModes('fido2'),	]);

$result = $graphServiceClient->identity()->conditionalAccess()->authenticationStrength()->policies()->byAuthenticationStrengthPolicyId('authenticationStrengthPolicy-id')->combinationConfigurations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.fido2CombinationConfiguration"
	allowedAAGUIDs = @(
	"486c3b50-889c-480a-abc5-c04ef7c873e0"
"c042882f-a621-40c8-94d3-9cde3a826fed"
"ec454c08-4c77-4012-9d48-45f7f0fccdfb"
)
appliesToCombinations = @(
"fido2"
)
}

New-MgIdentityConditionalAccessAuthenticationStrengthPolicyCombinationConfiguration -AuthenticationStrengthPolicyId $authenticationStrengthPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.fido2_combination_configuration import Fido2CombinationConfiguration
from msgraph.generated.models.authentication_method_modes import AuthenticationMethodModes
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Fido2CombinationConfiguration(
	odata_type = "#microsoft.graph.fido2CombinationConfiguration",
	allowed_a_a_g_u_i_ds = [
		"486c3b50-889c-480a-abc5-c04ef7c873e0",
		"c042882f-a621-40c8-94d3-9cde3a826fed",
		"ec454c08-4c77-4012-9d48-45f7f0fccdfb",
	],
	applies_to_combinations = [
		AuthenticationMethodModes.Fido2,
	],
)

result = await graph_client.identity.conditional_access.authentication_strength.policies.by_authentication_strength_policy_id('authenticationStrengthPolicy-id').combination_configurations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type" : "#microsoft.graph.fido2CombinationConfiguration",
  "id": "96cb1a17-e45e-4b4f-8b4b-4a9490d63d66",
  "allowedAAGUIDs": [
    "486c3b50-889c-480a-abc5-c04ef7c873e0",
    "c042882f-a621-40c8-94d3-9cde3a826fed",
    "ec454c08-4c77-4012-9d48-45f7f0fccdfb"
  ],
  "appliesToCombinations": ["fido2"]
}
```

### Example 2: Create a x509CertificateCombinationConfiguration object

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
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/authenticationStrength/policies/{authenticationStrengthPolicyId}/combinationConfigurations 
 
{ 
    "@odata.type": "#microsoft.graph.x509CertificateCombinationConfiguration", 
    "allowedIssuerSkis": [ 
        "9A4248C6AC8C2931AB2A86537818E92E7B6C97B6" 
    ], 
    "allowedPolicyOIDs": [], 
    "appliesToCombinations": [ 
        "x509CertificateSingleFactor " 
    ] 
} 
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new X509CertificateCombinationConfiguration
{
	OdataType = "#microsoft.graph.x509CertificateCombinationConfiguration",
	AllowedIssuerSkis = new List<string>
	{
		"9A4248C6AC8C2931AB2A86537818E92E7B6C97B6",
	},
	AllowedPolicyOIDs = new List<string>
	{
	},
	AppliesToCombinations = new List<AuthenticationMethodModes?>
	{
		AuthenticationMethodModes.X509CertificateSingleFactor,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.AuthenticationStrength.Policies["{authenticationStrengthPolicy-id}"].CombinationConfigurations.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationCombinationConfiguration()
allowedIssuerSkis := []string {
	"9A4248C6AC8C2931AB2A86537818E92E7B6C97B6",
}
requestBody.SetAllowedIssuerSkis(allowedIssuerSkis)
allowedPolicyOIDs := []string {

}
requestBody.SetAllowedPolicyOIDs(allowedPolicyOIDs)
appliesToCombinations := []graphmodels.AuthenticationMethodModesable {
	authenticationMethodModes := graphmodels.X509CERTIFICATESINGLEFACTOR _AUTHENTICATIONMETHODMODES 
	requestBody.SetAuthenticationMethodModes(&authenticationMethodModes)
}
requestBody.SetAppliesToCombinations(appliesToCombinations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
combinationConfigurations, err := graphClient.Identity().ConditionalAccess().AuthenticationStrength().Policies().ByAuthenticationStrengthPolicyId("authenticationStrengthPolicy-id").CombinationConfigurations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

X509CertificateCombinationConfiguration authenticationCombinationConfiguration = new X509CertificateCombinationConfiguration();
authenticationCombinationConfiguration.setOdataType("#microsoft.graph.x509CertificateCombinationConfiguration");
LinkedList<String> allowedIssuerSkis = new LinkedList<String>();
allowedIssuerSkis.add("9A4248C6AC8C2931AB2A86537818E92E7B6C97B6");
authenticationCombinationConfiguration.setAllowedIssuerSkis(allowedIssuerSkis);
LinkedList<String> allowedPolicyOIDs = new LinkedList<String>();
authenticationCombinationConfiguration.setAllowedPolicyOIDs(allowedPolicyOIDs);
LinkedList<AuthenticationMethodModes> appliesToCombinations = new LinkedList<AuthenticationMethodModes>();
appliesToCombinations.add(AuthenticationMethodModes.X509CertificateSingleFactor);
authenticationCombinationConfiguration.setAppliesToCombinations(appliesToCombinations);
AuthenticationCombinationConfiguration result = graphClient.identity().conditionalAccess().authenticationStrength().policies().byAuthenticationStrengthPolicyId("{authenticationStrengthPolicy-id}").combinationConfigurations().post(authenticationCombinationConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationCombinationConfiguration = {
    '@odata.type': '#microsoft.graph.x509CertificateCombinationConfiguration', 
    allowedIssuerSkis: [ 
        '9A4248C6AC8C2931AB2A86537818E92E7B6C97B6' 
    ], 
    allowedPolicyOIDs: [], 
    appliesToCombinations: [ 
        'x509CertificateSingleFactor ' 
    ] 
};

await client.api('/identity/conditionalAccess/authenticationStrength/policies/{authenticationStrengthPolicyId}/combinationConfigurations')
	.post(authenticationCombinationConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\X509CertificateCombinationConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationMethodModes;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new X509CertificateCombinationConfiguration();
$requestBody->setOdataType('#microsoft.graph.x509CertificateCombinationConfiguration');
$requestBody->setAllowedIssuerSkis(['9A4248C6AC8C2931AB2A86537818E92E7B6C97B6', 	]);
$requestBody->setAllowedPolicyOIDs([	]);
$requestBody->setAppliesToCombinations([new AuthenticationMethodModes('x509CertificateSingleFactor '),	]);

$result = $graphServiceClient->identity()->conditionalAccess()->authenticationStrength()->policies()->byAuthenticationStrengthPolicyId('authenticationStrengthPolicy-id')->combinationConfigurations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.x509CertificateCombinationConfiguration"
	allowedIssuerSkis = @(
	"9A4248C6AC8C2931AB2A86537818E92E7B6C97B6"
)
allowedPolicyOIDs = @(
)
appliesToCombinations = @(
"x509CertificateSingleFactor "
)
}

New-MgIdentityConditionalAccessAuthenticationStrengthPolicyCombinationConfiguration -AuthenticationStrengthPolicyId $authenticationStrengthPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.x509_certificate_combination_configuration import X509CertificateCombinationConfiguration
from msgraph.generated.models.authentication_method_modes import AuthenticationMethodModes
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = X509CertificateCombinationConfiguration(
	odata_type = "#microsoft.graph.x509CertificateCombinationConfiguration",
	allowed_issuer_skis = [
		"9A4248C6AC8C2931AB2A86537818E92E7B6C97B6",
	],
	allowed_policy_o_i_ds = [
	],
	applies_to_combinations = [
		AuthenticationMethodModes.X509CertificateSingleFactor,
	],
)

result = await graph_client.identity.conditional_access.authentication_strength.policies.by_authentication_strength_policy_id('authenticationStrengthPolicy-id').combination_configurations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{ 
    "@odata.type": "#microsoft.graph.x509CertificateCombinationConfiguration", 
    "id" : "96cb1a17-e45e-4b4f-8b4b-4a9490d63d66",
    "allowedIssuerSkis": [ 
        "9A4248C6AC8C2931AB2A86537818E92E7B6C97B6" 
    ], 
    "allowedPolicyOIDs": [], 
    "appliesToCombinations": [ 
        "x509CertificateSingleFactor " 
    ] 
} 
```
