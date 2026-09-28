<!-- Source: https://learn.microsoft.com/en-us/graph/api/externalauthenticationmethodconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update externalAuthenticationMethodConfiguration

Namespace: microsoft.graph

Update the properties of an [externalAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/externalauthenticationmethodconfiguration?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.AuthenticationMethod | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.AuthenticationMethod | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Authentication Policy Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PATCH /policies/authenticationMethodsPolicy/authenticationMethodConfigurations/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| appId | String | **appId** for the app registration in Microsoft Entra ID representing the integration with the external provider. |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups representing the users that should be excluded from the policy. |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | Groups representing the users that are included in the policy and that can use the external authentication method. |
| state | authenticationMethodState | The state of the method in the policy. The possible values are: `enabled`, `disabled`. |
| openIdConnectSetting | [openIdConnectSetting](https://learn.microsoft.com/en-us/graph/api/resources/openidconnectsetting?view=graph-rest-1.0) | Object representing the required settings for the OIDC request to the external provider. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/v1.0/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/b183b746-e7db-4fa2-bafc-69ecf18850dd
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.externalAuthenticationMethodConfiguration",
  "includeTargets": [
    {
        "targetType": "group",
        "id": "b183b746-e7db-4fa2-bafc-69ecf18850dd",
        "isRegistrationRequired": false,
    }
  ],
  "state": "enabled"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ExternalAuthenticationMethodConfiguration
{
	OdataType = "#microsoft.graph.externalAuthenticationMethodConfiguration",
	IncludeTargets = new List<AuthenticationMethodTarget>
	{
		new AuthenticationMethodTarget
		{
			TargetType = AuthenticationMethodTargetType.Group,
			Id = "b183b746-e7db-4fa2-bafc-69ecf18850dd",
			IsRegistrationRequired = false,
		},
	},
	State = AuthenticationMethodState.Enabled,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.AuthenticationMethodsPolicy.AuthenticationMethodConfigurations["{authenticationMethodConfiguration-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationMethodConfiguration()


authenticationMethodTarget := graphmodels.NewAuthenticationMethodTarget()
targetType := graphmodels.GROUP_AUTHENTICATIONMETHODTARGETTYPE 
authenticationMethodTarget.SetTargetType(&targetType) 
id := "b183b746-e7db-4fa2-bafc-69ecf18850dd"
authenticationMethodTarget.SetId(&id) 
isRegistrationRequired := false
authenticationMethodTarget.SetIsRegistrationRequired(&isRegistrationRequired) 

includeTargets := []graphmodels.AuthenticationMethodTargetable {
	authenticationMethodTarget,
}
requestBody.SetIncludeTargets(includeTargets)
state := graphmodels.ENABLED_AUTHENTICATIONMETHODSTATE 
requestBody.SetState(&state) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationMethodConfigurations, err := graphClient.Policies().AuthenticationMethodsPolicy().AuthenticationMethodConfigurations().ByAuthenticationMethodConfigurationId("authenticationMethodConfiguration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ExternalAuthenticationMethodConfiguration authenticationMethodConfiguration = new ExternalAuthenticationMethodConfiguration();
authenticationMethodConfiguration.setOdataType("#microsoft.graph.externalAuthenticationMethodConfiguration");
LinkedList<AuthenticationMethodTarget> includeTargets = new LinkedList<AuthenticationMethodTarget>();
AuthenticationMethodTarget authenticationMethodTarget = new AuthenticationMethodTarget();
authenticationMethodTarget.setTargetType(AuthenticationMethodTargetType.Group);
authenticationMethodTarget.setId("b183b746-e7db-4fa2-bafc-69ecf18850dd");
authenticationMethodTarget.setIsRegistrationRequired(false);
includeTargets.add(authenticationMethodTarget);
authenticationMethodConfiguration.setIncludeTargets(includeTargets);
authenticationMethodConfiguration.setState(AuthenticationMethodState.Enabled);
AuthenticationMethodConfiguration result = graphClient.policies().authenticationMethodsPolicy().authenticationMethodConfigurations().byAuthenticationMethodConfigurationId("{authenticationMethodConfiguration-id}").patch(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationMethodConfiguration = {
  '@odata.type': '#microsoft.graph.externalAuthenticationMethodConfiguration',
  includeTargets: [
    {
        targetType: 'group',
        id: 'b183b746-e7db-4fa2-bafc-69ecf18850dd',
        isRegistrationRequired: false,
    }
  ],
  state: 'enabled'
};

await client.api('/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/b183b746-e7db-4fa2-bafc-69ecf18850dd')
	.update(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ExternalAuthenticationMethodConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationMethodTarget;
use Microsoft\Graph\Generated\Models\AuthenticationMethodTargetType;
use Microsoft\Graph\Generated\Models\AuthenticationMethodState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExternalAuthenticationMethodConfiguration();
$requestBody->setOdataType('#microsoft.graph.externalAuthenticationMethodConfiguration');
$includeTargetsAuthenticationMethodTarget1 = new AuthenticationMethodTarget();
$includeTargetsAuthenticationMethodTarget1->setTargetType(new AuthenticationMethodTargetType('group'));
$includeTargetsAuthenticationMethodTarget1->setId('b183b746-e7db-4fa2-bafc-69ecf18850dd');
$includeTargetsAuthenticationMethodTarget1->setIsRegistrationRequired(false);
$includeTargetsArray []= $includeTargetsAuthenticationMethodTarget1;
$requestBody->setIncludeTargets($includeTargetsArray);

$requestBody->setState(new AuthenticationMethodState('enabled'));

$result = $graphServiceClient->policies()->authenticationMethodsPolicy()->authenticationMethodConfigurations()->byAuthenticationMethodConfigurationId('authenticationMethodConfiguration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.externalAuthenticationMethodConfiguration"
	includeTargets = @(
		@{
			targetType = "group"
			id = "b183b746-e7db-4fa2-bafc-69ecf18850dd"
			isRegistrationRequired = $false
		}
	)
	state = "enabled"
}

Update-MgPolicyAuthenticationMethodPolicyAuthenticationMethodConfiguration -AuthenticationMethodConfigurationId $authenticationMethodConfigurationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.external_authentication_method_configuration import ExternalAuthenticationMethodConfiguration
from msgraph.generated.models.authentication_method_target import AuthenticationMethodTarget
from msgraph.generated.models.authentication_method_target_type import AuthenticationMethodTargetType
from msgraph.generated.models.authentication_method_state import AuthenticationMethodState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExternalAuthenticationMethodConfiguration(
	odata_type = "#microsoft.graph.externalAuthenticationMethodConfiguration",
	include_targets = [
		AuthenticationMethodTarget(
			target_type = AuthenticationMethodTargetType.Group,
			id = "b183b746-e7db-4fa2-bafc-69ecf18850dd",
			is_registration_required = False,
		),
	],
	state = AuthenticationMethodState.Enabled,
)

result = await graph_client.policies.authentication_methods_policy.authentication_method_configurations.by_authentication_method_configuration_id('authenticationMethodConfiguration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
