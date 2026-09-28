<!-- Source: https://learn.microsoft.com/en-us/graph/api/verifiablecredentialsauthenticationmethodconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Update verifiableCredentialsAuthenticationMethodConfiguration

Namespace: microsoft.graph

Update the properties of a [verifiableCredentialsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsauthenticationmethodconfiguration?view=graph-rest-1.0) object.

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
PATCH /policies/authenticationMethodsPolicy/authenticationMethodConfigurations/VerifiableCredentials
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
| state | authenticationMethodState | Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). The possible values are: `enabled`, `disabled`. Optional. |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). Optional. |

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
PATCH https://graph.microsoft.com/v1.0/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/VerifiableCredentials
Content-Type: application/json

{
    "state": "disabled",
    "excludeTargets": [
        {
            "id": "10051f25-53a8-4f81-8a0b-9fc22887e640",
            "targetType": "group"
        },
        {
            "id": "e2c2244f-66cc-4d5b-9042-686f9fa42986",
            "targetType": "group"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AuthenticationMethodConfiguration
{
	State = AuthenticationMethodState.Disabled,
	ExcludeTargets = new List<ExcludeTarget>
	{
		new ExcludeTarget
		{
			Id = "10051f25-53a8-4f81-8a0b-9fc22887e640",
			TargetType = AuthenticationMethodTargetType.Group,
		},
		new ExcludeTarget
		{
			Id = "e2c2244f-66cc-4d5b-9042-686f9fa42986",
			TargetType = AuthenticationMethodTargetType.Group,
		},
	},
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
state := graphmodels.DISABLED_AUTHENTICATIONMETHODSTATE 
requestBody.SetState(&state) 


excludeTarget := graphmodels.NewExcludeTarget()
id := "10051f25-53a8-4f81-8a0b-9fc22887e640"
excludeTarget.SetId(&id) 
targetType := graphmodels.GROUP_AUTHENTICATIONMETHODTARGETTYPE 
excludeTarget.SetTargetType(&targetType) 
excludeTarget1 := graphmodels.NewExcludeTarget()
id := "e2c2244f-66cc-4d5b-9042-686f9fa42986"
excludeTarget1.SetId(&id) 
targetType := graphmodels.GROUP_AUTHENTICATIONMETHODTARGETTYPE 
excludeTarget1.SetTargetType(&targetType) 

excludeTargets := []graphmodels.ExcludeTargetable {
	excludeTarget,
	excludeTarget1,
}
requestBody.SetExcludeTargets(excludeTargets)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationMethodConfigurations, err := graphClient.Policies().AuthenticationMethodsPolicy().AuthenticationMethodConfigurations().ByAuthenticationMethodConfigurationId("authenticationMethodConfiguration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationMethodConfiguration authenticationMethodConfiguration = new AuthenticationMethodConfiguration();
authenticationMethodConfiguration.setState(AuthenticationMethodState.Disabled);
LinkedList<ExcludeTarget> excludeTargets = new LinkedList<ExcludeTarget>();
ExcludeTarget excludeTarget = new ExcludeTarget();
excludeTarget.setId("10051f25-53a8-4f81-8a0b-9fc22887e640");
excludeTarget.setTargetType(AuthenticationMethodTargetType.Group);
excludeTargets.add(excludeTarget);
ExcludeTarget excludeTarget1 = new ExcludeTarget();
excludeTarget1.setId("e2c2244f-66cc-4d5b-9042-686f9fa42986");
excludeTarget1.setTargetType(AuthenticationMethodTargetType.Group);
excludeTargets.add(excludeTarget1);
authenticationMethodConfiguration.setExcludeTargets(excludeTargets);
AuthenticationMethodConfiguration result = graphClient.policies().authenticationMethodsPolicy().authenticationMethodConfigurations().byAuthenticationMethodConfigurationId("{authenticationMethodConfiguration-id}").patch(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationMethodConfiguration = {
    state: 'disabled',
    excludeTargets: [
        {
            id: '10051f25-53a8-4f81-8a0b-9fc22887e640',
            targetType: 'group'
        },
        {
            id: 'e2c2244f-66cc-4d5b-9042-686f9fa42986',
            targetType: 'group'
        }
    ]
};

await client.api('/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/VerifiableCredentials')
	.update(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AuthenticationMethodConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationMethodState;
use Microsoft\Graph\Generated\Models\ExcludeTarget;
use Microsoft\Graph\Generated\Models\AuthenticationMethodTargetType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AuthenticationMethodConfiguration();
$requestBody->setState(new AuthenticationMethodState('disabled'));
$excludeTargetsExcludeTarget1 = new ExcludeTarget();
$excludeTargetsExcludeTarget1->setId('10051f25-53a8-4f81-8a0b-9fc22887e640');
$excludeTargetsExcludeTarget1->setTargetType(new AuthenticationMethodTargetType('group'));
$excludeTargetsArray []= $excludeTargetsExcludeTarget1;
$excludeTargetsExcludeTarget2 = new ExcludeTarget();
$excludeTargetsExcludeTarget2->setId('e2c2244f-66cc-4d5b-9042-686f9fa42986');
$excludeTargetsExcludeTarget2->setTargetType(new AuthenticationMethodTargetType('group'));
$excludeTargetsArray []= $excludeTargetsExcludeTarget2;
$requestBody->setExcludeTargets($excludeTargetsArray);


$result = $graphServiceClient->policies()->authenticationMethodsPolicy()->authenticationMethodConfigurations()->byAuthenticationMethodConfigurationId('authenticationMethodConfiguration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	state = "disabled"
	excludeTargets = @(
		@{
			id = "10051f25-53a8-4f81-8a0b-9fc22887e640"
			targetType = "group"
		}
		@{
			id = "e2c2244f-66cc-4d5b-9042-686f9fa42986"
			targetType = "group"
		}
	)
}

Update-MgPolicyAuthenticationMethodPolicyAuthenticationMethodConfiguration -AuthenticationMethodConfigurationId $authenticationMethodConfigurationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.authentication_method_configuration import AuthenticationMethodConfiguration
from msgraph.generated.models.authentication_method_state import AuthenticationMethodState
from msgraph.generated.models.exclude_target import ExcludeTarget
from msgraph.generated.models.authentication_method_target_type import AuthenticationMethodTargetType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AuthenticationMethodConfiguration(
	state = AuthenticationMethodState.Disabled,
	exclude_targets = [
		ExcludeTarget(
			id = "10051f25-53a8-4f81-8a0b-9fc22887e640",
			target_type = AuthenticationMethodTargetType.Group,
		),
		ExcludeTarget(
			id = "e2c2244f-66cc-4d5b-9042-686f9fa42986",
			target_type = AuthenticationMethodTargetType.Group,
		),
	],
)

result = await graph_client.policies.authentication_methods_policy.authentication_method_configurations.by_authentication_method_configuration_id('authenticationMethodConfiguration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
