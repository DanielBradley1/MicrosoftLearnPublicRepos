<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-updateallowedcombinations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# authenticationStrengthPolicy: updateAllowedCombinations

Namespace: microsoft.graph

Update the allowedCombinations property of an [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object. To update other properties of an authenticationStrengthPolicy object, use the [Update authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-update?view=graph-rest-1.0) method.

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
POST /policies/authenticationStrengthPolicies/{authenticationStrengthPolicyId}/updateAllowedCombinations
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| allowedCombinations | authenticationMethodModes collection | The authentication method combinations allowed by this authentication strength policy. The possible values of this flagged enum are: `password`, `voice`, `hardwareOath`, `softwareOath`, `sms`, `fido2`, `windowsHelloForBusiness`, `microsoftAuthenticatorPush`, `deviceBasedPush`, `temporaryAccessPassOneTime`, `temporaryAccessPassMultiUse`, `email`, `x509CertificateSingleFactor`, `x509CertificateMultiFactor`, `federatedSingleFactor`, `federatedMultiFactor`, `unknownFutureValue`. For the list of allowed combinations, call the [List authenticationMethodModes](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-list-authenticationmethodmodes?view=graph-rest-1.0) API. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [updateAllowedCombinationsResult](https://learn.microsoft.com/en-us/graph/api/resources/updateallowedcombinationsresult?view=graph-rest-1.0) in the response body.

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
POST https://graph.microsoft.com/v1.0/policies/authenticationStrengthPolicies/33c5d2c0-884e-4b5d-a5b8-5395082b092c/updateAllowedCombinations
Content-Type: application/json
Content-length: 51

{
  "allowedCombinations": [
      "password, voice"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Policies.AuthenticationStrengthPolicies.Item.UpdateAllowedCombinations;
using Microsoft.Graph.Models;

var requestBody = new UpdateAllowedCombinationsPostRequestBody
{
	AllowedCombinations = new List<AuthenticationMethodModes?>
	{
		AuthenticationMethodModes.Password | AuthenticationMethodModes.Voice,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.AuthenticationStrengthPolicies["{authenticationStrengthPolicy-id}"].UpdateAllowedCombinations.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphpolicies "github.com/microsoftgraph/msgraph-sdk-go/policies"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphpolicies.NewUpdateAllowedCombinationsPostRequestBody()
allowedCombinations := []graphmodels.AuthenticationMethodModesable {
	authenticationMethodModes := graphmodels.PASSWORD, VOICE_AUTHENTICATIONMETHODMODES 
	requestBody.SetAuthenticationMethodModes(&authenticationMethodModes)
}
requestBody.SetAllowedCombinations(allowedCombinations)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
updateAllowedCombinations, err := graphClient.Policies().AuthenticationStrengthPolicies().ByAuthenticationStrengthPolicyId("authenticationStrengthPolicy-id").UpdateAllowedCombinations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.policies.authenticationstrengthpolicies.item.updateallowedcombinations.UpdateAllowedCombinationsPostRequestBody updateAllowedCombinationsPostRequestBody = new com.microsoft.graph.policies.authenticationstrengthpolicies.item.updateallowedcombinations.UpdateAllowedCombinationsPostRequestBody();
LinkedList<AuthenticationMethodModes> allowedCombinations = new LinkedList<AuthenticationMethodModes>();
allowedCombinations.add(AuthenticationMethodModes.Password);
allowedCombinations.add(AuthenticationMethodModes.Voice);
updateAllowedCombinationsPostRequestBody.setAllowedCombinations(allowedCombinations);
var result = graphClient.policies().authenticationStrengthPolicies().byAuthenticationStrengthPolicyId("{authenticationStrengthPolicy-id}").updateAllowedCombinations().post(updateAllowedCombinationsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateAllowedCombinationsResult = {
  allowedCombinations: [
      'password, voice'
  ]
};

await client.api('/policies/authenticationStrengthPolicies/33c5d2c0-884e-4b5d-a5b8-5395082b092c/updateAllowedCombinations')
	.post(updateAllowedCombinationsResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Policies\AuthenticationStrengthPolicies\Item\UpdateAllowedCombinations\UpdateAllowedCombinationsPostRequestBody;
use Microsoft\Graph\Generated\Models\AuthenticationMethodModes;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateAllowedCombinationsPostRequestBody();
$requestBody->setAllowedCombinations([new AuthenticationMethodModes('password, voice'),	]);

$result = $graphServiceClient->policies()->authenticationStrengthPolicies()->byAuthenticationStrengthPolicyId('authenticationStrengthPolicy-id')->updateAllowedCombinations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	allowedCombinations = @(
	"password, voice"
)
}

Update-MgPolicyAuthenticationStrengthPolicyAllowedCombination -AuthenticationStrengthPolicyId $authenticationStrengthPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.policies.authenticationstrengthpolicies.item.update_allowed_combinations.update_allowed_combinations_post_request_body import UpdateAllowedCombinationsPostRequestBody
from msgraph.generated.models.authentication_method_modes import AuthenticationMethodModes
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateAllowedCombinationsPostRequestBody(
	allowed_combinations = [
		AuthenticationMethodModes.Password | AuthenticationMethodModes.Voice,
	],
)

result = await graph_client.policies.authentication_strength_policies.by_authentication_strength_policy_id('authenticationStrengthPolicy-id').update_allowed_combinations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type" : "#microsoft.graph.updateAllowedCombinationsResult",
  "previousCombinations": [
    "fido2",
    "password, voice"
  ],
  "currentCombinations": [
    "password, voice"
  ],
  "conditionalAccessReferences": [
    "53a3968a-ae2c-4b82-a313-091d10c52bfa"
  ],
  "additionalInformation": "You have lowered the security of the My Custom Strength authentication strength by adding a lower security combination. This Authentication Strength is referenced by one or more Conditional Access policies. Review conditionalAccessReferences to understand which Conditional Access policies were impacted by this change. To reverse your changes back, use updateAllowedCombinations action with the previousCombinations values."
}
```
