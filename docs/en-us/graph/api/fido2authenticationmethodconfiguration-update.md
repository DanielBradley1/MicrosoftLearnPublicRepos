<!-- Source: https://learn.microsoft.com/en-us/graph/api/fido2authenticationmethodconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Update fido2AuthenticationMethodConfiguration

Namespace: microsoft.graph

Update the properties of a [fido2AuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0) object, which represents the passkey \(FIDO2\) authentication method policy for the Microsoft Entra tenant.

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
PATCH /policies/authenticationMethodsPolicy/authenticationMethodConfigurations/fido2
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [fido2AuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0) object with the values of fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

For the list of properties that can be updated, see [fido2AuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/fido2authenticationmethodconfiguration?view=graph-rest-1.0).

> **Note:** The `@odata.type` property with a value of `#microsoft.graph.fido2AuthenticationMethodConfiguration` must be included in the body.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

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
PATCH https://graph.microsoft.com/v1.0/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/fido2
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.fido2AuthenticationMethodConfiguration",
    "id": "Fido2",
    "state": "disabled",
    "isSelfServiceRegistrationAllowed": true,
    "isAttestationEnforced": true,
    "keyRestrictions": {
        "isEnforced": false,
        "enforcementType": "block",
        "aaGuids": []
    },
    "includeTargets": [
        {
            "targetType": "group",
            "id": "all_users",
            "isRegistrationRequired": false,
            "allowedPasskeyProfiles": [
                "00000000-0000-0000-0000-000000000001"
            ]
        }
    ],
    "excludeTargets": [],
    "passkeyProfiles": [
        {
            "id": "00000000-0000-0000-0000-000000000001",
            "name": "Default passkey profile",
            "passkeyTypes": "deviceBound,synced",
            "attestationEnforcement": "disabled",
            "keyRestrictions": {
                "isEnforced": false,
                "enforcementType": "allow",
                "aaGuids": [
                ]
            }
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Fido2AuthenticationMethodConfiguration
{
	OdataType = "#microsoft.graph.fido2AuthenticationMethodConfiguration",
	Id = "Fido2",
	State = AuthenticationMethodState.Disabled,
	IsSelfServiceRegistrationAllowed = true,
	IsAttestationEnforced = true,
	KeyRestrictions = new Fido2KeyRestrictions
	{
		IsEnforced = false,
		EnforcementType = Fido2RestrictionEnforcementType.Block,
		AaGuids = new List<string>
		{
		},
	},
	IncludeTargets = new List<PasskeyAuthenticationMethodTarget>
	{
		new PasskeyAuthenticationMethodTarget
		{
			TargetType = AuthenticationMethodTargetType.Group,
			Id = "all_users",
			IsRegistrationRequired = false,
			AllowedPasskeyProfiles = new List<Guid?>
			{
				Guid.Parse("00000000-0000-0000-0000-000000000001"),
			},
		},
	},
	ExcludeTargets = new List<ExcludeTarget>
	{
	},
	PasskeyProfiles = new List<PasskeyProfile>
	{
		new PasskeyProfile
		{
			Id = "00000000-0000-0000-0000-000000000001",
			Name = "Default passkey profile",
			PasskeyTypes = PasskeyTypes.DeviceBound | PasskeyTypes.Synced,
			AttestationEnforcement = AttestationEnforcement.Disabled,
			KeyRestrictions = new Fido2KeyRestrictions
			{
				IsEnforced = false,
				EnforcementType = Fido2RestrictionEnforcementType.Allow,
				AaGuids = new List<string>
				{
				},
			},
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
id := "Fido2"
requestBody.SetId(&id) 
state := graphmodels.DISABLED_AUTHENTICATIONMETHODSTATE 
requestBody.SetState(&state) 
isSelfServiceRegistrationAllowed := true
requestBody.SetIsSelfServiceRegistrationAllowed(&isSelfServiceRegistrationAllowed) 
isAttestationEnforced := true
requestBody.SetIsAttestationEnforced(&isAttestationEnforced) 
keyRestrictions := graphmodels.NewFido2KeyRestrictions()
isEnforced := false
keyRestrictions.SetIsEnforced(&isEnforced) 
enforcementType := graphmodels.BLOCK_FIDO2RESTRICTIONENFORCEMENTTYPE 
keyRestrictions.SetEnforcementType(&enforcementType) 
aaGuids := []string {

}
keyRestrictions.SetAaGuids(aaGuids)
requestBody.SetKeyRestrictions(keyRestrictions)


passkeyAuthenticationMethodTarget := graphmodels.NewPasskeyAuthenticationMethodTarget()
targetType := graphmodels.GROUP_AUTHENTICATIONMETHODTARGETTYPE 
passkeyAuthenticationMethodTarget.SetTargetType(&targetType) 
id := "all_users"
passkeyAuthenticationMethodTarget.SetId(&id) 
isRegistrationRequired := false
passkeyAuthenticationMethodTarget.SetIsRegistrationRequired(&isRegistrationRequired) 
allowedPasskeyProfiles := []uuid.UUID {
	uuid.MustParse("00000000-0000-0000-0000-000000000001"),
}
passkeyAuthenticationMethodTarget.SetAllowedPasskeyProfiles(allowedPasskeyProfiles)

includeTargets := []graphmodels.PasskeyAuthenticationMethodTargetable {
	passkeyAuthenticationMethodTarget,
}
requestBody.SetIncludeTargets(includeTargets)
excludeTargets := []graphmodels.ExcludeTargetable {

}
requestBody.SetExcludeTargets(excludeTargets)


passkeyProfile := graphmodels.NewPasskeyProfile()
id := "00000000-0000-0000-0000-000000000001"
passkeyProfile.SetId(&id) 
name := "Default passkey profile"
passkeyProfile.SetName(&name) 
passkeyTypes := graphmodels.DEVICEBOUND,SYNCED_PASSKEYTYPES 
passkeyProfile.SetPasskeyTypes(&passkeyTypes) 
attestationEnforcement := graphmodels.DISABLED_ATTESTATIONENFORCEMENT 
passkeyProfile.SetAttestationEnforcement(&attestationEnforcement) 
keyRestrictions := graphmodels.NewFido2KeyRestrictions()
isEnforced := false
keyRestrictions.SetIsEnforced(&isEnforced) 
enforcementType := graphmodels.ALLOW_FIDO2RESTRICTIONENFORCEMENTTYPE 
keyRestrictions.SetEnforcementType(&enforcementType) 
aaGuids := []string {

}
keyRestrictions.SetAaGuids(aaGuids)
passkeyProfile.SetKeyRestrictions(keyRestrictions)

passkeyProfiles := []graphmodels.PasskeyProfileable {
	passkeyProfile,
}
requestBody.SetPasskeyProfiles(passkeyProfiles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
authenticationMethodConfigurations, err := graphClient.Policies().AuthenticationMethodsPolicy().AuthenticationMethodConfigurations().ByAuthenticationMethodConfigurationId("authenticationMethodConfiguration-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Fido2AuthenticationMethodConfiguration authenticationMethodConfiguration = new Fido2AuthenticationMethodConfiguration();
authenticationMethodConfiguration.setOdataType("#microsoft.graph.fido2AuthenticationMethodConfiguration");
authenticationMethodConfiguration.setId("Fido2");
authenticationMethodConfiguration.setState(AuthenticationMethodState.Disabled);
authenticationMethodConfiguration.setIsSelfServiceRegistrationAllowed(true);
authenticationMethodConfiguration.setIsAttestationEnforced(true);
Fido2KeyRestrictions keyRestrictions = new Fido2KeyRestrictions();
keyRestrictions.setIsEnforced(false);
keyRestrictions.setEnforcementType(Fido2RestrictionEnforcementType.Block);
LinkedList<String> aaGuids = new LinkedList<String>();
keyRestrictions.setAaGuids(aaGuids);
authenticationMethodConfiguration.setKeyRestrictions(keyRestrictions);
LinkedList<PasskeyAuthenticationMethodTarget> includeTargets = new LinkedList<PasskeyAuthenticationMethodTarget>();
PasskeyAuthenticationMethodTarget passkeyAuthenticationMethodTarget = new PasskeyAuthenticationMethodTarget();
passkeyAuthenticationMethodTarget.setTargetType(AuthenticationMethodTargetType.Group);
passkeyAuthenticationMethodTarget.setId("all_users");
passkeyAuthenticationMethodTarget.setIsRegistrationRequired(false);
LinkedList<UUID> allowedPasskeyProfiles = new LinkedList<UUID>();
allowedPasskeyProfiles.add(UUID.fromString("00000000-0000-0000-0000-000000000001"));
passkeyAuthenticationMethodTarget.setAllowedPasskeyProfiles(allowedPasskeyProfiles);
includeTargets.add(passkeyAuthenticationMethodTarget);
authenticationMethodConfiguration.setIncludeTargets(includeTargets);
LinkedList<ExcludeTarget> excludeTargets = new LinkedList<ExcludeTarget>();
authenticationMethodConfiguration.setExcludeTargets(excludeTargets);
LinkedList<PasskeyProfile> passkeyProfiles = new LinkedList<PasskeyProfile>();
PasskeyProfile passkeyProfile = new PasskeyProfile();
passkeyProfile.setId("00000000-0000-0000-0000-000000000001");
passkeyProfile.setName("Default passkey profile");
passkeyProfile.setPasskeyTypes(EnumSet.of(PasskeyTypes.DeviceBound, PasskeyTypes.Synced));
passkeyProfile.setAttestationEnforcement(AttestationEnforcement.Disabled);
Fido2KeyRestrictions keyRestrictions1 = new Fido2KeyRestrictions();
keyRestrictions1.setIsEnforced(false);
keyRestrictions1.setEnforcementType(Fido2RestrictionEnforcementType.Allow);
LinkedList<String> aaGuids1 = new LinkedList<String>();
keyRestrictions1.setAaGuids(aaGuids1);
passkeyProfile.setKeyRestrictions(keyRestrictions1);
passkeyProfiles.add(passkeyProfile);
authenticationMethodConfiguration.setPasskeyProfiles(passkeyProfiles);
AuthenticationMethodConfiguration result = graphClient.policies().authenticationMethodsPolicy().authenticationMethodConfigurations().byAuthenticationMethodConfigurationId("{authenticationMethodConfiguration-id}").patch(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authenticationMethodConfiguration = {
    '@odata.type': '#microsoft.graph.fido2AuthenticationMethodConfiguration',
    id: 'Fido2',
    state: 'disabled',
    isSelfServiceRegistrationAllowed: true,
    isAttestationEnforced: true,
    keyRestrictions: {
        isEnforced: false,
        enforcementType: 'block',
        aaGuids: []
    },
    includeTargets: [
        {
            targetType: 'group',
            id: 'all_users',
            isRegistrationRequired: false,
            allowedPasskeyProfiles: [
                '00000000-0000-0000-0000-000000000001'
            ]
        }
    ],
    excludeTargets: [],
    passkeyProfiles: [
        {
            id: '00000000-0000-0000-0000-000000000001',
            name: 'Default passkey profile',
            passkeyTypes: 'deviceBound,synced',
            attestationEnforcement: 'disabled',
            keyRestrictions: {
                isEnforced: false,
                enforcementType: 'allow',
                aaGuids: [
                ]
            }
        }
    ]
};

await client.api('/policies/authenticationMethodsPolicy/authenticationMethodConfigurations/fido2')
	.update(authenticationMethodConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Fido2AuthenticationMethodConfiguration;
use Microsoft\Graph\Generated\Models\AuthenticationMethodState;
use Microsoft\Graph\Generated\Models\Fido2KeyRestrictions;
use Microsoft\Graph\Generated\Models\Fido2RestrictionEnforcementType;
use Microsoft\Graph\Generated\Models\PasskeyAuthenticationMethodTarget;
use Microsoft\Graph\Generated\Models\AuthenticationMethodTargetType;
use Microsoft\Graph\Generated\Models\ExcludeTarget;
use Microsoft\Graph\Generated\Models\PasskeyProfile;
use Microsoft\Graph\Generated\Models\PasskeyTypes;
use Microsoft\Graph\Generated\Models\AttestationEnforcement;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Fido2AuthenticationMethodConfiguration();
$requestBody->setOdataType('#microsoft.graph.fido2AuthenticationMethodConfiguration');
$requestBody->setId('Fido2');
$requestBody->setState(new AuthenticationMethodState('disabled'));
$requestBody->setIsSelfServiceRegistrationAllowed(true);
$requestBody->setIsAttestationEnforced(true);
$keyRestrictions = new Fido2KeyRestrictions();
$keyRestrictions->setIsEnforced(false);
$keyRestrictions->setEnforcementType(new Fido2RestrictionEnforcementType('block'));
$keyRestrictions->setAaGuids([	]);
$requestBody->setKeyRestrictions($keyRestrictions);
$includeTargetsPasskeyAuthenticationMethodTarget1 = new PasskeyAuthenticationMethodTarget();
$includeTargetsPasskeyAuthenticationMethodTarget1->setTargetType(new AuthenticationMethodTargetType('group'));
$includeTargetsPasskeyAuthenticationMethodTarget1->setId('all_users');
$includeTargetsPasskeyAuthenticationMethodTarget1->setIsRegistrationRequired(false);
$includeTargetsPasskeyAuthenticationMethodTarget1->setAllowedPasskeyProfiles(['00000000-0000-0000-0000-000000000001', 	]);
$includeTargetsArray []= $includeTargetsPasskeyAuthenticationMethodTarget1;
$requestBody->setIncludeTargets($includeTargetsArray);

$requestBody->setExcludeTargets([]);
$passkeyProfilesPasskeyProfile1 = new PasskeyProfile();
$passkeyProfilesPasskeyProfile1->setId('00000000-0000-0000-0000-000000000001');
$passkeyProfilesPasskeyProfile1->setName('Default passkey profile');
$passkeyProfilesPasskeyProfile1->setPasskeyTypes(new PasskeyTypes('deviceBound,synced'));
$passkeyProfilesPasskeyProfile1->setAttestationEnforcement(new AttestationEnforcement('disabled'));
$passkeyProfilesPasskeyProfile1KeyRestrictions = new Fido2KeyRestrictions();
$passkeyProfilesPasskeyProfile1KeyRestrictions->setIsEnforced(false);
$passkeyProfilesPasskeyProfile1KeyRestrictions->setEnforcementType(new Fido2RestrictionEnforcementType('allow'));
$passkeyProfilesPasskeyProfile1KeyRestrictions->setAaGuids([]);
$passkeyProfilesPasskeyProfile1->setKeyRestrictions($passkeyProfilesPasskeyProfile1KeyRestrictions);
$passkeyProfilesArray []= $passkeyProfilesPasskeyProfile1;
$requestBody->setPasskeyProfiles($passkeyProfilesArray);


$result = $graphServiceClient->policies()->authenticationMethodsPolicy()->authenticationMethodConfigurations()->byAuthenticationMethodConfigurationId('authenticationMethodConfiguration-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.fido2AuthenticationMethodConfiguration"
	id = "Fido2"
	state = "disabled"
	isSelfServiceRegistrationAllowed = $true
	isAttestationEnforced = $true
	keyRestrictions = @{
		isEnforced = $false
		enforcementType = "block"
		aaGuids = @(
		)
	}
	includeTargets = @(
		@{
			targetType = "group"
			id = "all_users"
			isRegistrationRequired = $false
			allowedPasskeyProfiles = @(
			"00000000-0000-0000-0000-000000000001"
		)
	}
)
excludeTargets = @(
)
passkeyProfiles = @(
	@{
		id = "00000000-0000-0000-0000-000000000001"
		name = "Default passkey profile"
		passkeyTypes = "deviceBound,synced"
		attestationEnforcement = "disabled"
		keyRestrictions = @{
			isEnforced = $false
			enforcementType = "allow"
			aaGuids = @(
			)
		}
	}
)
}

Update-MgPolicyAuthenticationMethodPolicyAuthenticationMethodConfiguration -AuthenticationMethodConfigurationId $authenticationMethodConfigurationId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.fido2_authentication_method_configuration import Fido2AuthenticationMethodConfiguration
from msgraph.generated.models.authentication_method_state import AuthenticationMethodState
from msgraph.generated.models.fido2_key_restrictions import Fido2KeyRestrictions
from msgraph.generated.models.fido2_restriction_enforcement_type import Fido2RestrictionEnforcementType
from msgraph.generated.models.passkey_authentication_method_target import PasskeyAuthenticationMethodTarget
from msgraph.generated.models.authentication_method_target_type import AuthenticationMethodTargetType
from msgraph.generated.models.exclude_target import ExcludeTarget
from msgraph.generated.models.passkey_profile import PasskeyProfile
from msgraph.generated.models.passkey_types import PasskeyTypes
from msgraph.generated.models.attestation_enforcement import AttestationEnforcement
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Fido2AuthenticationMethodConfiguration(
	odata_type = "#microsoft.graph.fido2AuthenticationMethodConfiguration",
	id = "Fido2",
	state = AuthenticationMethodState.Disabled,
	is_self_service_registration_allowed = True,
	is_attestation_enforced = True,
	key_restrictions = Fido2KeyRestrictions(
		is_enforced = False,
		enforcement_type = Fido2RestrictionEnforcementType.Block,
		aa_guids = [
		],
	),
	include_targets = [
		PasskeyAuthenticationMethodTarget(
			target_type = AuthenticationMethodTargetType.Group,
			id = "all_users",
			is_registration_required = False,
			allowed_passkey_profiles = [
				UUID("00000000-0000-0000-0000-000000000001"),
			],
		),
	],
	exclude_targets = [
	],
	passkey_profiles = [
		PasskeyProfile(
			id = "00000000-0000-0000-0000-000000000001",
			name = "Default passkey profile",
			passkey_types = PasskeyTypes.DeviceBound | PasskeyTypes.Synced,
			attestation_enforcement = AttestationEnforcement.Disabled,
			key_restrictions = Fido2KeyRestrictions(
				is_enforced = False,
				enforcement_type = Fido2RestrictionEnforcementType.Allow,
				aa_guids = [
				],
			),
		),
	],
)

result = await graph_client.policies.authentication_methods_policy.authentication_method_configurations.by_authentication_method_configuration_id('authenticationMethodConfiguration-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
