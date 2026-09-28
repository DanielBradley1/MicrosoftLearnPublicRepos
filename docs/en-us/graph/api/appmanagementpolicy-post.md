<!-- Source: https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Create appManagementPolicy

Namespace: microsoft.graph

Create an [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ApplicationConfiguration | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ApplicationConfiguration | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Cloud Application Administrator
- Application Administrator

## HTTP request

```http
POST /policies/appManagementPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

Important

Service principals with a createdDateTime `null` are treated as having being created on 01/01/2019.

## Request body

In the request body, supply a JSON representation of the [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) object.

You can specify the following properties when creating an **appManagementPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the policy. Required. |
| description | String | The description of the policy. Required. |
| isEnabled | Boolean | Denotes whether the policy is enabled. Optional. |
| restrictions | [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0) | Restrictions that apply to an application or service principal object. Optional. |

## Response

If successful, this method returns a `201 Created` response code with the new [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) object in the response payload.

## Examples

### Request

The following example shows a request. This request created an app management policy with the following settings:

- Enables the policy.
- Blocks creating of new passwords for applications and service principals created on or after October 19th 2019 at 10:37 AM UTC time.
- Limits password secrets for apps and service principals created after October 19th 2014 at 10:37 AM UTC time to less than 90 days.
- Disables the nonDefaultUriAddition restriction. This means that apps with this policy applied to them can add new nondefault identifier URIs to their apps, even if the tenant default policy would typically block it.
- Doesn't specify any other restrictions. This means that the behavior for those restrictions on apps/service principals with this policy applied falls back to however the tenant default policy is configured.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/policies/appManagementPolicies

{
    "displayName": "Credential management policy",
    "description": "Cred policy sample",
    "isEnabled": true,
    "restrictions": {
        "passwordCredentials": [
            {
                "restrictionType": "passwordAddition",
                "state": "enabled",
                "maxLifetime": null,
                "restrictForAppsCreatedAfterDateTime": "2019-10-19T10:37:00Z"
            },
            {
                "restrictionType": "passwordLifetime",
                "state": "enabled",
                "maxLifetime": "P90D",
                "restrictForAppsCreatedAfterDateTime": "2014-10-19T10:37:00Z"
            },
            {
                "restrictionType": "symmetricKeyAddition",
                "state": "enabled",
                "maxLifetime": null,
                "restrictForAppsCreatedAfterDateTime": "2019-10-19T10:37:00Z"
            },
            {
                "restrictionType": "symmetricKeyLifetime",
                "state": "enabled",
                "maxLifetime": "P90D",
                "restrictForAppsCreatedAfterDateTime": "2014-10-19T10:37:00Z"
            }
        ],
        "keyCredentials": [],
        "applicationRestrictions": {
            "identifierUris": {
                "nonDefaultUriAddition": {
                    "state": "disabled",
                    "excludeAppsReceivingV2Tokens": true,
                    "excludeSaml": true
                }
            }
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AppManagementPolicy
{
	DisplayName = "Credential management policy",
	Description = "Cred policy sample",
	IsEnabled = true,
	Restrictions = new CustomAppManagementConfiguration
	{
		PasswordCredentials = new List<PasswordCredentialConfiguration>
		{
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.PasswordAddition,
				State = AppManagementRestrictionState.Enabled,
				MaxLifetime = null,
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2019-10-19T10:37:00Z"),
			},
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.PasswordLifetime,
				State = AppManagementRestrictionState.Enabled,
				MaxLifetime = TimeSpan.Parse("P90D"),
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2014-10-19T10:37:00Z"),
			},
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.SymmetricKeyAddition,
				State = AppManagementRestrictionState.Enabled,
				MaxLifetime = null,
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2019-10-19T10:37:00Z"),
			},
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.SymmetricKeyLifetime,
				State = AppManagementRestrictionState.Enabled,
				MaxLifetime = TimeSpan.Parse("P90D"),
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2014-10-19T10:37:00Z"),
			},
		},
		KeyCredentials = new List<KeyCredentialConfiguration>
		{
		},
		ApplicationRestrictions = new CustomAppManagementApplicationConfiguration
		{
			IdentifierUris = new IdentifierUriConfiguration
			{
				NonDefaultUriAddition = new IdentifierUriRestriction
				{
					State = AppManagementRestrictionState.Disabled,
					ExcludeAppsReceivingV2Tokens = true,
					ExcludeSaml = true,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.AppManagementPolicies.PostAsync(requestBody);
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

requestBody := graphmodels.NewAppManagementPolicy()
displayName := "Credential management policy"
requestBody.SetDisplayName(&displayName) 
description := "Cred policy sample"
requestBody.SetDescription(&description) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
restrictions := graphmodels.NewCustomAppManagementConfiguration()


passwordCredentialConfiguration := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.PASSWORDADDITION_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration.SetRestrictionType(&restrictionType) 
state := graphmodels.ENABLED_APPMANAGEMENTRESTRICTIONSTATE 
passwordCredentialConfiguration.SetState(&state) 
maxLifetime := null
passwordCredentialConfiguration.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2019-10-19T10:37:00Z")
passwordCredentialConfiguration.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
passwordCredentialConfiguration1 := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.PASSWORDLIFETIME_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration1.SetRestrictionType(&restrictionType) 
state := graphmodels.ENABLED_APPMANAGEMENTRESTRICTIONSTATE 
passwordCredentialConfiguration1.SetState(&state) 
maxLifetime , err := abstractions.ParseISODuration("P90D")
passwordCredentialConfiguration1.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2014-10-19T10:37:00Z")
passwordCredentialConfiguration1.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
passwordCredentialConfiguration2 := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.SYMMETRICKEYADDITION_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration2.SetRestrictionType(&restrictionType) 
state := graphmodels.ENABLED_APPMANAGEMENTRESTRICTIONSTATE 
passwordCredentialConfiguration2.SetState(&state) 
maxLifetime := null
passwordCredentialConfiguration2.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2019-10-19T10:37:00Z")
passwordCredentialConfiguration2.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
passwordCredentialConfiguration3 := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.SYMMETRICKEYLIFETIME_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration3.SetRestrictionType(&restrictionType) 
state := graphmodels.ENABLED_APPMANAGEMENTRESTRICTIONSTATE 
passwordCredentialConfiguration3.SetState(&state) 
maxLifetime , err := abstractions.ParseISODuration("P90D")
passwordCredentialConfiguration3.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2014-10-19T10:37:00Z")
passwordCredentialConfiguration3.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 

passwordCredentials := []graphmodels.PasswordCredentialConfigurationable {
	passwordCredentialConfiguration,
	passwordCredentialConfiguration1,
	passwordCredentialConfiguration2,
	passwordCredentialConfiguration3,
}
restrictions.SetPasswordCredentials(passwordCredentials)
keyCredentials := []graphmodels.KeyCredentialConfigurationable {

}
restrictions.SetKeyCredentials(keyCredentials)
applicationRestrictions := graphmodels.NewCustomAppManagementApplicationConfiguration()
identifierUris := graphmodels.NewIdentifierUriConfiguration()
nonDefaultUriAddition := graphmodels.NewIdentifierUriRestriction()
state := graphmodels.DISABLED_APPMANAGEMENTRESTRICTIONSTATE 
nonDefaultUriAddition.SetState(&state) 
excludeAppsReceivingV2Tokens := true
nonDefaultUriAddition.SetExcludeAppsReceivingV2Tokens(&excludeAppsReceivingV2Tokens) 
excludeSaml := true
nonDefaultUriAddition.SetExcludeSaml(&excludeSaml) 
identifierUris.SetNonDefaultUriAddition(nonDefaultUriAddition)
applicationRestrictions.SetIdentifierUris(identifierUris)
restrictions.SetApplicationRestrictions(applicationRestrictions)
requestBody.SetRestrictions(restrictions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appManagementPolicies, err := graphClient.Policies().AppManagementPolicies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AppManagementPolicy appManagementPolicy = new AppManagementPolicy();
appManagementPolicy.setDisplayName("Credential management policy");
appManagementPolicy.setDescription("Cred policy sample");
appManagementPolicy.setIsEnabled(true);
CustomAppManagementConfiguration restrictions = new CustomAppManagementConfiguration();
LinkedList<PasswordCredentialConfiguration> passwordCredentials = new LinkedList<PasswordCredentialConfiguration>();
PasswordCredentialConfiguration passwordCredentialConfiguration = new PasswordCredentialConfiguration();
passwordCredentialConfiguration.setRestrictionType(AppCredentialRestrictionType.PasswordAddition);
passwordCredentialConfiguration.setState(AppManagementRestrictionState.Enabled);
passwordCredentialConfiguration.setMaxLifetime(null);
OffsetDateTime restrictForAppsCreatedAfterDateTime = OffsetDateTime.parse("2019-10-19T10:37:00Z");
passwordCredentialConfiguration.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime);
passwordCredentials.add(passwordCredentialConfiguration);
PasswordCredentialConfiguration passwordCredentialConfiguration1 = new PasswordCredentialConfiguration();
passwordCredentialConfiguration1.setRestrictionType(AppCredentialRestrictionType.PasswordLifetime);
passwordCredentialConfiguration1.setState(AppManagementRestrictionState.Enabled);
PeriodAndDuration maxLifetime1 = PeriodAndDuration.ofDuration(Duration.parse("P90D"));
passwordCredentialConfiguration1.setMaxLifetime(maxLifetime1);
OffsetDateTime restrictForAppsCreatedAfterDateTime1 = OffsetDateTime.parse("2014-10-19T10:37:00Z");
passwordCredentialConfiguration1.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime1);
passwordCredentials.add(passwordCredentialConfiguration1);
PasswordCredentialConfiguration passwordCredentialConfiguration2 = new PasswordCredentialConfiguration();
passwordCredentialConfiguration2.setRestrictionType(AppCredentialRestrictionType.SymmetricKeyAddition);
passwordCredentialConfiguration2.setState(AppManagementRestrictionState.Enabled);
passwordCredentialConfiguration2.setMaxLifetime(null);
OffsetDateTime restrictForAppsCreatedAfterDateTime2 = OffsetDateTime.parse("2019-10-19T10:37:00Z");
passwordCredentialConfiguration2.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime2);
passwordCredentials.add(passwordCredentialConfiguration2);
PasswordCredentialConfiguration passwordCredentialConfiguration3 = new PasswordCredentialConfiguration();
passwordCredentialConfiguration3.setRestrictionType(AppCredentialRestrictionType.SymmetricKeyLifetime);
passwordCredentialConfiguration3.setState(AppManagementRestrictionState.Enabled);
PeriodAndDuration maxLifetime3 = PeriodAndDuration.ofDuration(Duration.parse("P90D"));
passwordCredentialConfiguration3.setMaxLifetime(maxLifetime3);
OffsetDateTime restrictForAppsCreatedAfterDateTime3 = OffsetDateTime.parse("2014-10-19T10:37:00Z");
passwordCredentialConfiguration3.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime3);
passwordCredentials.add(passwordCredentialConfiguration3);
restrictions.setPasswordCredentials(passwordCredentials);
LinkedList<KeyCredentialConfiguration> keyCredentials = new LinkedList<KeyCredentialConfiguration>();
restrictions.setKeyCredentials(keyCredentials);
CustomAppManagementApplicationConfiguration applicationRestrictions = new CustomAppManagementApplicationConfiguration();
IdentifierUriConfiguration identifierUris = new IdentifierUriConfiguration();
IdentifierUriRestriction nonDefaultUriAddition = new IdentifierUriRestriction();
nonDefaultUriAddition.setState(AppManagementRestrictionState.Disabled);
nonDefaultUriAddition.setExcludeAppsReceivingV2Tokens(true);
nonDefaultUriAddition.setExcludeSaml(true);
identifierUris.setNonDefaultUriAddition(nonDefaultUriAddition);
applicationRestrictions.setIdentifierUris(identifierUris);
restrictions.setApplicationRestrictions(applicationRestrictions);
appManagementPolicy.setRestrictions(restrictions);
AppManagementPolicy result = graphClient.policies().appManagementPolicies().post(appManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const appManagementPolicy = {
    displayName: 'Credential management policy',
    description: 'Cred policy sample',
    isEnabled: true,
    restrictions: {
        passwordCredentials: [
            {
                restrictionType: 'passwordAddition',
                state: 'enabled',
                maxLifetime: null,
                restrictForAppsCreatedAfterDateTime: '2019-10-19T10:37:00Z'
            },
            {
                restrictionType: 'passwordLifetime',
                state: 'enabled',
                maxLifetime: 'P90D',
                restrictForAppsCreatedAfterDateTime: '2014-10-19T10:37:00Z'
            },
            {
                restrictionType: 'symmetricKeyAddition',
                state: 'enabled',
                maxLifetime: null,
                restrictForAppsCreatedAfterDateTime: '2019-10-19T10:37:00Z'
            },
            {
                restrictionType: 'symmetricKeyLifetime',
                state: 'enabled',
                maxLifetime: 'P90D',
                restrictForAppsCreatedAfterDateTime: '2014-10-19T10:37:00Z'
            }
        ],
        keyCredentials: [],
        applicationRestrictions: {
            identifierUris: {
                nonDefaultUriAddition: {
                    state: 'disabled',
                    excludeAppsReceivingV2Tokens: true,
                    excludeSaml: true
                }
            }
        }
    }
};

await client.api('/policies/appManagementPolicies')
	.post(appManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AppManagementPolicy;
use Microsoft\Graph\Generated\Models\CustomAppManagementConfiguration;
use Microsoft\Graph\Generated\Models\PasswordCredentialConfiguration;
use Microsoft\Graph\Generated\Models\AppCredentialRestrictionType;
use Microsoft\Graph\Generated\Models\AppManagementRestrictionState;
use Microsoft\Graph\Generated\Models\KeyCredentialConfiguration;
use Microsoft\Graph\Generated\Models\CustomAppManagementApplicationConfiguration;
use Microsoft\Graph\Generated\Models\IdentifierUriConfiguration;
use Microsoft\Graph\Generated\Models\IdentifierUriRestriction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AppManagementPolicy();
$requestBody->setDisplayName('Credential management policy');
$requestBody->setDescription('Cred policy sample');
$requestBody->setIsEnabled(true);
$restrictions = new CustomAppManagementConfiguration();
$passwordCredentialsPasswordCredentialConfiguration1 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration1->setRestrictionType(new AppCredentialRestrictionType('passwordAddition'));
$passwordCredentialsPasswordCredentialConfiguration1->setState(new AppManagementRestrictionState('enabled'));
$passwordCredentialsPasswordCredentialConfiguration1->setMaxLifetime(null);
$passwordCredentialsPasswordCredentialConfiguration1->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2019-10-19T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration1;
$passwordCredentialsPasswordCredentialConfiguration2 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration2->setRestrictionType(new AppCredentialRestrictionType('passwordLifetime'));
$passwordCredentialsPasswordCredentialConfiguration2->setState(new AppManagementRestrictionState('enabled'));
$passwordCredentialsPasswordCredentialConfiguration2->setMaxLifetime(new \DateInterval('P90D'));
$passwordCredentialsPasswordCredentialConfiguration2->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2014-10-19T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration2;
$passwordCredentialsPasswordCredentialConfiguration3 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration3->setRestrictionType(new AppCredentialRestrictionType('symmetricKeyAddition'));
$passwordCredentialsPasswordCredentialConfiguration3->setState(new AppManagementRestrictionState('enabled'));
$passwordCredentialsPasswordCredentialConfiguration3->setMaxLifetime(null);
$passwordCredentialsPasswordCredentialConfiguration3->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2019-10-19T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration3;
$passwordCredentialsPasswordCredentialConfiguration4 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration4->setRestrictionType(new AppCredentialRestrictionType('symmetricKeyLifetime'));
$passwordCredentialsPasswordCredentialConfiguration4->setState(new AppManagementRestrictionState('enabled'));
$passwordCredentialsPasswordCredentialConfiguration4->setMaxLifetime(new \DateInterval('P90D'));
$passwordCredentialsPasswordCredentialConfiguration4->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2014-10-19T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration4;
$restrictions->setPasswordCredentials($passwordCredentialsArray);

$restrictions->setKeyCredentials([]);
$restrictionsApplicationRestrictions = new CustomAppManagementApplicationConfiguration();
$restrictionsApplicationRestrictionsIdentifierUris = new IdentifierUriConfiguration();
$restrictionsApplicationRestrictionsIdentifierUrisNonDefaultUriAddition = new IdentifierUriRestriction();
$restrictionsApplicationRestrictionsIdentifierUrisNonDefaultUriAddition->setState(new AppManagementRestrictionState('disabled'));
$restrictionsApplicationRestrictionsIdentifierUrisNonDefaultUriAddition->setExcludeAppsReceivingV2Tokens(true);
$restrictionsApplicationRestrictionsIdentifierUrisNonDefaultUriAddition->setExcludeSaml(true);
$restrictionsApplicationRestrictionsIdentifierUris->setNonDefaultUriAddition($restrictionsApplicationRestrictionsIdentifierUrisNonDefaultUriAddition);
$restrictionsApplicationRestrictions->setIdentifierUris($restrictionsApplicationRestrictionsIdentifierUris);
$restrictions->setApplicationRestrictions($restrictionsApplicationRestrictions);
$requestBody->setRestrictions($restrictions);

$result = $graphServiceClient->policies()->appManagementPolicies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	displayName = "Credential management policy"
	description = "Cred policy sample"
	isEnabled = $true
	restrictions = @{
		passwordCredentials = @(
			@{
				restrictionType = "passwordAddition"
				state = "enabled"
				maxLifetime = $null
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2019-10-19T10:37:00Z")
			}
			@{
				restrictionType = "passwordLifetime"
				state = "enabled"
				maxLifetime = "P90D"
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2014-10-19T10:37:00Z")
			}
			@{
				restrictionType = "symmetricKeyAddition"
				state = "enabled"
				maxLifetime = $null
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2019-10-19T10:37:00Z")
			}
			@{
				restrictionType = "symmetricKeyLifetime"
				state = "enabled"
				maxLifetime = "P90D"
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2014-10-19T10:37:00Z")
			}
		)
		keyCredentials = @(
		)
		applicationRestrictions = @{
			identifierUris = @{
				nonDefaultUriAddition = @{
					state = "disabled"
					excludeAppsReceivingV2Tokens = $true
					excludeSaml = $true
				}
			}
		}
	}
}

New-MgPolicyAppManagementPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.app_management_policy import AppManagementPolicy
from msgraph.generated.models.custom_app_management_configuration import CustomAppManagementConfiguration
from msgraph.generated.models.password_credential_configuration import PasswordCredentialConfiguration
from msgraph.generated.models.app_credential_restriction_type import AppCredentialRestrictionType
from msgraph.generated.models.app_management_restriction_state import AppManagementRestrictionState
from msgraph.generated.models.key_credential_configuration import KeyCredentialConfiguration
from msgraph.generated.models.custom_app_management_application_configuration import CustomAppManagementApplicationConfiguration
from msgraph.generated.models.identifier_uri_configuration import IdentifierUriConfiguration
from msgraph.generated.models.identifier_uri_restriction import IdentifierUriRestriction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AppManagementPolicy(
	display_name = "Credential management policy",
	description = "Cred policy sample",
	is_enabled = True,
	restrictions = CustomAppManagementConfiguration(
		password_credentials = [
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.PasswordAddition,
				state = AppManagementRestrictionState.Enabled,
				max_lifetime = None,
				restrict_for_apps_created_after_date_time = "2019-10-19T10:37:00Z",
			),
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.PasswordLifetime,
				state = AppManagementRestrictionState.Enabled,
				max_lifetime = "P90D",
				restrict_for_apps_created_after_date_time = "2014-10-19T10:37:00Z",
			),
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.SymmetricKeyAddition,
				state = AppManagementRestrictionState.Enabled,
				max_lifetime = None,
				restrict_for_apps_created_after_date_time = "2019-10-19T10:37:00Z",
			),
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.SymmetricKeyLifetime,
				state = AppManagementRestrictionState.Enabled,
				max_lifetime = "P90D",
				restrict_for_apps_created_after_date_time = "2014-10-19T10:37:00Z",
			),
		],
		key_credentials = [
		],
		application_restrictions = CustomAppManagementApplicationConfiguration(
			identifier_uris = IdentifierUriConfiguration(
				non_default_uri_addition = IdentifierUriRestriction(
					state = AppManagementRestrictionState.Disabled,
					exclude_apps_receiving_v2_tokens = True,
					exclude_saml = True,
				),
			),
		),
	),
)

result = await graph_client.policies.app_management_policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/appManagementPolicies/$entity",
    "id": "a4ab1ed9-46bb-4bef-88d4-86fd6398dd5d",
    "displayName": "credential management policy",
    "description": "Lorem ipsum",
    "isEnabled": true,
    "restrictions": {
        "passwordCredentials": [
            {
                "restrictionType": "passwordAddition",
                "state": "enabled",
                "maxLifetime": null,
                "restrictForAppsCreatedAfterDateTime": "2019-10-19T10:37:00Z"
            },
            {
                "restrictionType": "passwordLifetime",
                "state": "enabled",
                "maxLifetime": "P90D",
                "restrictForAppsCreatedAfterDateTime": "2018-10-19T10:37:00Z"
            },
            {
                "restrictionType": "symmetricKeyAddition",
                "state": "enabled",
                "maxLifetime": null,
                "restrictForAppsCreatedAfterDateTime": "2019-10-19T10:37:00Z"
            },
            {
                "restrictionType": "symmetricKeyLifetime",
                "state": "enabled",
                "maxLifetime": "P90D",
                "restrictForAppsCreatedAfterDateTime": "2014-10-19T10:37:00Z"
            }
        ],
        "keyCredentials": [],
        "applicationRestrictions": {
            "identifierUris": {
                "nonDefaultUriAddition": {
                    "state": "disabled",
                    "restrictForAppsCreatedAfterDateTime": null,
                    "excludeAppsReceivingV2Tokens": true,
                    "excludeSaml": true
                }
            }
        }
    }
}
```
