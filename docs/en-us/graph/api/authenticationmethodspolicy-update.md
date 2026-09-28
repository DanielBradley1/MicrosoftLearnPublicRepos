<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationmethodspolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Update authenticationMethodsPolicy

Namespace: microsoft.graph

Update the properties of an [authenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0) object.

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
PATCH /policies/authenticationMethodsPolicy
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
| registrationEnforcement | [registrationEnforcement](https://learn.microsoft.com/en-us/graph/api/resources/registrationenforcement?view=graph-rest-1.0) | Enforce registration at sign-in time. This property can be used to prompt users to set up targeted authentication methods. |

## Response

If successful, this method returns a `200 OK` response code and an [authenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/authenticationMethodsPolicy
Content-Type: application/json

{
  "registrationEnforcement": {
    "authenticationMethodsRegistrationCampaign": {
        "snoozeDurationInDays": 1,
        "state": "enabled",
        "excludeTargets": [],
        "includeTargets": [
            {
                "id": "3ee3a9de-0a86-4e12-a287-9769accf1ba2",
                "targetType": "group",
                "targetedAuthenticationMethod": "microsoftAuthenticator"
            }
        ]
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AuthenticationMethodsPolicy
{
	RegistrationEnforcement = new RegistrationEnforcement
	{
		AuthenticationMethodsRegistrationCampaign = new AuthenticationMethodsRegistrationCampaign
		{
			SnoozeDurationInDays = 1,
			State = AdvancedConfigState.Enabled,
			ExcludeTargets = new List<ExcludeTarget>
			{
			},
			IncludeTargets = new List<AuthenticationMethodsRegistrationCampaignIncludeTarget>
			{
				new AuthenticationMethodsRegistrationCampaignIncludeTarget
				{
					Id = "3ee3a9de-0a86-4e12-a287-9769accf1ba2",
					TargetType = AuthenticationMethodTargetType.Group,
					TargetedAuthenticationMethod = "microsoftAuthenticator",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.AuthenticationMethodsPolicy.PatchAsync(requestBody);
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

requestBody := graphmodels.NewAuthenticationMethodsPolicy()
registrationEnforcement := graphmodels.NewRegistrationEnforcement()
authenticationMethodsRegistrationCampaign := graphmodels.NewAuthenticationMethodsRegistrationCampaign()
snoozeDurationInDays := int32(1)
authenticationMethodsRegistrationCampaign.SetSnoozeDurationInDays(&snoozeDurationInDays) 
state := graphmodels.ENABLED_ADVANCEDCONFIGSTATE 
authenticationMethodsRegistrationCampaign.SetState(&state) 
excludeTargets := []graphmodels.ExcludeTargetable {

}
authenticationMethodsRegistrationCampaign.SetExcludeTargets(excludeTargets)


authenticationMethodsRegistrationCampaignIncludeTarget := graphmodels.NewAuthenticationMethodsRegistrationCampaignIncludeTarget()
id := "3ee3a9de-0a86-4e12-a287-9769accf1ba2"
authenticationMethodsRegistrationCampaignIncludeTarget.SetId(&id) 
targetType := graphmodels.GROUP_AUTHENTICATIONMETHODTARGETTYPE 
authenticationMethodsRegistrationCampaignIncludeTarget.SetTargetType(&targetType) 
targetedAuthenticationMethod := "microsoftAuthenticator"
authenticationMethodsRegistrationCampaignIncludeTarget.SetTargetedAuthenticationMethod(&targetedAuthenticationMethod) 

includeTargets := []graphmodels.AuthenticationMethodsRegistrationCampaignIncludeTargetable {
	authenticationMethodsRegistrationCampaignIncludeTarget,
}
authenticationMethodsRegistrationCampaign.SetIncludeTargets(includeTargets)
registrationEnforcement.SetAuthenticationMethodsRegistrationCampaign(authenticationMethodsRegistrationCampaign)
requestBody.SetRegistrationEnforcement(registrationEnforcement)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationMethodsPolicy, err := graphClient.Policies().AuthenticationMethodsPolicy().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthenticationMethodsPolicy authenticationMethodsPolicy = new AuthenticationMethodsPolicy();
RegistrationEnforcement registrationEnforcement = new RegistrationEnforcement();
AuthenticationMethodsRegistrationCampaign authenticationMethodsRegistrationCampaign = new AuthenticationMethodsRegistrationCampaign();
authenticationMethodsRegistrationCampaign.setSnoozeDurationInDays(1);
authenticationMethodsRegistrationCampaign.setState(AdvancedConfigState.Enabled);
LinkedList<ExcludeTarget> excludeTargets = new LinkedList<ExcludeTarget>();
authenticationMethodsRegistrationCampaign.setExcludeTargets(excludeTargets);
LinkedList<AuthenticationMethodsRegistrationCampaignIncludeTarget> includeTargets = new LinkedList<AuthenticationMethodsRegistrationCampaignIncludeTarget>();
AuthenticationMethodsRegistrationCampaignIncludeTarget authenticationMethodsRegistrationCampaignIncludeTarget = new AuthenticationMethodsRegistrationCampaignIncludeTarget();
authenticationMethodsRegistrationCampaignIncludeTarget.setId("3ee3a9de-0a86-4e12-a287-9769accf1ba2");
authenticationMethodsRegistrationCampaignIncludeTarget.setTargetType(AuthenticationMethodTargetType.Group);
authenticationMethodsRegistrationCampaignIncludeTarget.setTargetedAuthenticationMethod("microsoftAuthenticator");
includeTargets.add(authenticationMethodsRegistrationCampaignIncludeTarget);
authenticationMethodsRegistrationCampaign.setIncludeTargets(includeTargets);
registrationEnforcement.setAuthenticationMethodsRegistrationCampaign(authenticationMethodsRegistrationCampaign);
authenticationMethodsPolicy.setRegistrationEnforcement(registrationEnforcement);
AuthenticationMethodsPolicy result = graphClient.policies().authenticationMethodsPolicy().patch(authenticationMethodsPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationMethodsPolicy = {
  registrationEnforcement: {
    authenticationMethodsRegistrationCampaign: {
        snoozeDurationInDays: 1,
        state: 'enabled',
        excludeTargets: [],
        includeTargets: [
            {
                id: '3ee3a9de-0a86-4e12-a287-9769accf1ba2',
                targetType: 'group',
                targetedAuthenticationMethod: 'microsoftAuthenticator'
            }
        ]
    }
  }
};

await client.api('/policies/authenticationMethodsPolicy')
	.update(authenticationMethodsPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AuthenticationMethodsPolicy;
use Microsoft\Graph\Generated\Models\RegistrationEnforcement;
use Microsoft\Graph\Generated\Models\AuthenticationMethodsRegistrationCampaign;
use Microsoft\Graph\Generated\Models\AdvancedConfigState;
use Microsoft\Graph\Generated\Models\ExcludeTarget;
use Microsoft\Graph\Generated\Models\AuthenticationMethodsRegistrationCampaignIncludeTarget;
use Microsoft\Graph\Generated\Models\AuthenticationMethodTargetType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AuthenticationMethodsPolicy();
$registrationEnforcement = new RegistrationEnforcement();
$registrationEnforcementAuthenticationMethodsRegistrationCampaign = new AuthenticationMethodsRegistrationCampaign();
$registrationEnforcementAuthenticationMethodsRegistrationCampaign->setSnoozeDurationInDays(1);
$registrationEnforcementAuthenticationMethodsRegistrationCampaign->setState(new AdvancedConfigState('enabled'));
$registrationEnforcementAuthenticationMethodsRegistrationCampaign->setExcludeTargets([	]);
$includeTargetsAuthenticationMethodsRegistrationCampaignIncludeTarget1 = new AuthenticationMethodsRegistrationCampaignIncludeTarget();
$includeTargetsAuthenticationMethodsRegistrationCampaignIncludeTarget1->setId('3ee3a9de-0a86-4e12-a287-9769accf1ba2');
$includeTargetsAuthenticationMethodsRegistrationCampaignIncludeTarget1->setTargetType(new AuthenticationMethodTargetType('group'));
$includeTargetsAuthenticationMethodsRegistrationCampaignIncludeTarget1->setTargetedAuthenticationMethod('microsoftAuthenticator');
$includeTargetsArray []= $includeTargetsAuthenticationMethodsRegistrationCampaignIncludeTarget1;
$registrationEnforcementAuthenticationMethodsRegistrationCampaign->setIncludeTargets($includeTargetsArray);

$registrationEnforcement->setAuthenticationMethodsRegistrationCampaign($registrationEnforcementAuthenticationMethodsRegistrationCampaign);
$requestBody->setRegistrationEnforcement($registrationEnforcement);

$result = $graphServiceClient->policies()->authenticationMethodsPolicy()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	registrationEnforcement = @{
		authenticationMethodsRegistrationCampaign = @{
			snoozeDurationInDays = 1
			state = "enabled"
			excludeTargets = @(
			)
			includeTargets = @(
				@{
					id = "3ee3a9de-0a86-4e12-a287-9769accf1ba2"
					targetType = "group"
					targetedAuthenticationMethod = "microsoftAuthenticator"
				}
			)
		}
	}
}

Update-MgPolicyAuthenticationMethodPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.authentication_methods_policy import AuthenticationMethodsPolicy
from msgraph.generated.models.registration_enforcement import RegistrationEnforcement
from msgraph.generated.models.authentication_methods_registration_campaign import AuthenticationMethodsRegistrationCampaign
from msgraph.generated.models.advanced_config_state import AdvancedConfigState
from msgraph.generated.models.exclude_target import ExcludeTarget
from msgraph.generated.models.authentication_methods_registration_campaign_include_target import AuthenticationMethodsRegistrationCampaignIncludeTarget
from msgraph.generated.models.authentication_method_target_type import AuthenticationMethodTargetType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AuthenticationMethodsPolicy(
	registration_enforcement = RegistrationEnforcement(
		authentication_methods_registration_campaign = AuthenticationMethodsRegistrationCampaign(
			snooze_duration_in_days = 1,
			state = AdvancedConfigState.Enabled,
			exclude_targets = [
			],
			include_targets = [
				AuthenticationMethodsRegistrationCampaignIncludeTarget(
					id = "3ee3a9de-0a86-4e12-a287-9769accf1ba2",
					target_type = AuthenticationMethodTargetType.Group,
					targeted_authentication_method = "microsoftAuthenticator",
				),
			],
		),
	),
)

result = await graph_client.policies.authentication_methods_policy.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#authenticationMethodsPolicy",
  "id": "authenticationMethodsPolicy",
  "displayName": "Authentication Methods Policy",
  "description": "The tenant-wide policy that controls which authentication methods are allowed in the tenant, authentication method registration requirements, and self-service password reset settings",
  "lastModifiedDateTime": "2021-05-25T01:08:08.6712279Z",
  "policyVersion": "1.4",
  "registrationEnforcement": {
    "authenticationMethodsRegistrationCampaign": {
        "snoozeDurationInDays": 1,
        "state": "enabled",
        "excludeTargets": [],
        "includeTargets": [
            {
                "id": "3ee3a9de-0a86-4e12-a287-9769accf1ba2",
                "targetType": "group",
                "targetedAuthenticationMethod": "microsoftAuthenticator"
            }
        ]
    }
  }
}
```
