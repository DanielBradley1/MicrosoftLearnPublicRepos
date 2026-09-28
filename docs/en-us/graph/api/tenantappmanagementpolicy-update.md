<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantappmanagementpolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-10 -->

# Update tenantAppManagementPolicy

Namespace: microsoft.graph

Update the properties of a [tenantAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantappmanagementpolicy?view=graph-rest-1.0) object.

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
PATCH /policies/defaultAppManagementPolicy
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

Important

Service principals with a createdDateTime `null` are treated as having being created on 01/01/2019.

## Request body

In the request body, supply the values for relevant fields from the [tenantAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantappmanagementpolicy?view=graph-rest-1.0) that should be updated. Existing properties that are not included in the request body will maintain their previous values. For best performance, don't include unchanged values in the request payload.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the default policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| description | String | The description of the default policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| isEnabled | Boolean | Denotes if the policy is enabled. Default value is false. |
| applicationRestrictions | [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0) | Restrictions that apply as default to all application objects in the tenant. |
| servicePrincipalRestrictions | [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0) | Restrictions that apply as default to all service principal objects in the tenant. |

Important

Service principals with a createdDateTime `null` are treated as having being created on 01/01/2019.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

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

```msgraph
PATCH https://graph.microsoft.com/v1.0/policies/defaultAppManagementPolicy
Content-Type: application/json

{
    "isEnabled": true,
    "applicationRestrictions": {
        "passwordCredentials": [
            {
                "restrictionType": "passwordAddition",
                "maxLifetime": null,
                "restrictForAppsCreatedAfterDateTime": "2021-01-01T10:37:00Z"
            },
            {
                "restrictionType": "passwordLifetime",
                "maxLifetime": "P4DT12H30M5S",
                "restrictForAppsCreatedAfterDateTime": "2017-01-01T10:37:00Z"
            },
            {
                "restrictionType": "symmetricKeyAddition",
                "maxLifetime": null,
                "restrictForAppsCreatedAfterDateTime": "2021-01-01T10:37:00Z"
            },
            {
                "restrictionType": "customPasswordAddition",
                "maxLifetime": null,
                "restrictForAppsCreatedAfterDateTime": "2015-01-01T10:37:00Z"
            },
            {
                "restrictionType": "symmetricKeyLifetime",
                "maxLifetime": "P40D",
                "restrictForAppsCreatedAfterDateTime": "2015-01-01T10:37:00Z"
            }
        ],
        "keyCredentials":[
            {
                "restrictionType": "asymmetricKeyLifetime",
                "maxLifetime": "P30D",
                "restrictForAppsCreatedAfterDateTime": "2015-01-01T10:37:00Z"
            },
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TenantAppManagementPolicy
{
	IsEnabled = true,
	ApplicationRestrictions = new AppManagementApplicationConfiguration
	{
		PasswordCredentials = new List<PasswordCredentialConfiguration>
		{
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.PasswordAddition,
				MaxLifetime = null,
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2021-01-01T10:37:00Z"),
			},
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.PasswordLifetime,
				MaxLifetime = TimeSpan.Parse("P4DT12H30M5S"),
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2017-01-01T10:37:00Z"),
			},
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.SymmetricKeyAddition,
				MaxLifetime = null,
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2021-01-01T10:37:00Z"),
			},
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.CustomPasswordAddition,
				MaxLifetime = null,
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2015-01-01T10:37:00Z"),
			},
			new PasswordCredentialConfiguration
			{
				RestrictionType = AppCredentialRestrictionType.SymmetricKeyLifetime,
				MaxLifetime = TimeSpan.Parse("P40D"),
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2015-01-01T10:37:00Z"),
			},
		},
		KeyCredentials = new List<KeyCredentialConfiguration>
		{
			new KeyCredentialConfiguration
			{
				RestrictionType = AppKeyCredentialRestrictionType.AsymmetricKeyLifetime,
				MaxLifetime = TimeSpan.Parse("P30D"),
				RestrictForAppsCreatedAfterDateTime = DateTimeOffset.Parse("2015-01-01T10:37:00Z"),
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.DefaultAppManagementPolicy.PatchAsync(requestBody);
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

requestBody := graphmodels.NewTenantAppManagementPolicy()
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
applicationRestrictions := graphmodels.NewAppManagementApplicationConfiguration()


passwordCredentialConfiguration := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.PASSWORDADDITION_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration.SetRestrictionType(&restrictionType) 
maxLifetime := null
passwordCredentialConfiguration.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2021-01-01T10:37:00Z")
passwordCredentialConfiguration.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
passwordCredentialConfiguration1 := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.PASSWORDLIFETIME_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration1.SetRestrictionType(&restrictionType) 
maxLifetime , err := abstractions.ParseISODuration("P4DT12H30M5S")
passwordCredentialConfiguration1.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2017-01-01T10:37:00Z")
passwordCredentialConfiguration1.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
passwordCredentialConfiguration2 := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.SYMMETRICKEYADDITION_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration2.SetRestrictionType(&restrictionType) 
maxLifetime := null
passwordCredentialConfiguration2.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2021-01-01T10:37:00Z")
passwordCredentialConfiguration2.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
passwordCredentialConfiguration3 := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.CUSTOMPASSWORDADDITION_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration3.SetRestrictionType(&restrictionType) 
maxLifetime := null
passwordCredentialConfiguration3.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2015-01-01T10:37:00Z")
passwordCredentialConfiguration3.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 
passwordCredentialConfiguration4 := graphmodels.NewPasswordCredentialConfiguration()
restrictionType := graphmodels.SYMMETRICKEYLIFETIME_APPCREDENTIALRESTRICTIONTYPE 
passwordCredentialConfiguration4.SetRestrictionType(&restrictionType) 
maxLifetime , err := abstractions.ParseISODuration("P40D")
passwordCredentialConfiguration4.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2015-01-01T10:37:00Z")
passwordCredentialConfiguration4.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 

passwordCredentials := []graphmodels.PasswordCredentialConfigurationable {
	passwordCredentialConfiguration,
	passwordCredentialConfiguration1,
	passwordCredentialConfiguration2,
	passwordCredentialConfiguration3,
	passwordCredentialConfiguration4,
}
applicationRestrictions.SetPasswordCredentials(passwordCredentials)


keyCredentialConfiguration := graphmodels.NewKeyCredentialConfiguration()
restrictionType := graphmodels.ASYMMETRICKEYLIFETIME_APPKEYCREDENTIALRESTRICTIONTYPE 
keyCredentialConfiguration.SetRestrictionType(&restrictionType) 
maxLifetime , err := abstractions.ParseISODuration("P30D")
keyCredentialConfiguration.SetMaxLifetime(&maxLifetime) 
restrictForAppsCreatedAfterDateTime , err := time.Parse(time.RFC3339, "2015-01-01T10:37:00Z")
keyCredentialConfiguration.SetRestrictForAppsCreatedAfterDateTime(&restrictForAppsCreatedAfterDateTime) 

keyCredentials := []graphmodels.KeyCredentialConfigurationable {
	keyCredentialConfiguration,
}
applicationRestrictions.SetKeyCredentials(keyCredentials)
requestBody.SetApplicationRestrictions(applicationRestrictions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
defaultAppManagementPolicy, err := graphClient.Policies().DefaultAppManagementPolicy().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TenantAppManagementPolicy tenantAppManagementPolicy = new TenantAppManagementPolicy();
tenantAppManagementPolicy.setIsEnabled(true);
AppManagementApplicationConfiguration applicationRestrictions = new AppManagementApplicationConfiguration();
LinkedList<PasswordCredentialConfiguration> passwordCredentials = new LinkedList<PasswordCredentialConfiguration>();
PasswordCredentialConfiguration passwordCredentialConfiguration = new PasswordCredentialConfiguration();
passwordCredentialConfiguration.setRestrictionType(AppCredentialRestrictionType.PasswordAddition);
passwordCredentialConfiguration.setMaxLifetime(null);
OffsetDateTime restrictForAppsCreatedAfterDateTime = OffsetDateTime.parse("2021-01-01T10:37:00Z");
passwordCredentialConfiguration.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime);
passwordCredentials.add(passwordCredentialConfiguration);
PasswordCredentialConfiguration passwordCredentialConfiguration1 = new PasswordCredentialConfiguration();
passwordCredentialConfiguration1.setRestrictionType(AppCredentialRestrictionType.PasswordLifetime);
PeriodAndDuration maxLifetime1 = PeriodAndDuration.ofDuration(Duration.parse("P4DT12H30M5S"));
passwordCredentialConfiguration1.setMaxLifetime(maxLifetime1);
OffsetDateTime restrictForAppsCreatedAfterDateTime1 = OffsetDateTime.parse("2017-01-01T10:37:00Z");
passwordCredentialConfiguration1.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime1);
passwordCredentials.add(passwordCredentialConfiguration1);
PasswordCredentialConfiguration passwordCredentialConfiguration2 = new PasswordCredentialConfiguration();
passwordCredentialConfiguration2.setRestrictionType(AppCredentialRestrictionType.SymmetricKeyAddition);
passwordCredentialConfiguration2.setMaxLifetime(null);
OffsetDateTime restrictForAppsCreatedAfterDateTime2 = OffsetDateTime.parse("2021-01-01T10:37:00Z");
passwordCredentialConfiguration2.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime2);
passwordCredentials.add(passwordCredentialConfiguration2);
PasswordCredentialConfiguration passwordCredentialConfiguration3 = new PasswordCredentialConfiguration();
passwordCredentialConfiguration3.setRestrictionType(AppCredentialRestrictionType.CustomPasswordAddition);
passwordCredentialConfiguration3.setMaxLifetime(null);
OffsetDateTime restrictForAppsCreatedAfterDateTime3 = OffsetDateTime.parse("2015-01-01T10:37:00Z");
passwordCredentialConfiguration3.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime3);
passwordCredentials.add(passwordCredentialConfiguration3);
PasswordCredentialConfiguration passwordCredentialConfiguration4 = new PasswordCredentialConfiguration();
passwordCredentialConfiguration4.setRestrictionType(AppCredentialRestrictionType.SymmetricKeyLifetime);
PeriodAndDuration maxLifetime4 = PeriodAndDuration.ofDuration(Duration.parse("P40D"));
passwordCredentialConfiguration4.setMaxLifetime(maxLifetime4);
OffsetDateTime restrictForAppsCreatedAfterDateTime4 = OffsetDateTime.parse("2015-01-01T10:37:00Z");
passwordCredentialConfiguration4.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime4);
passwordCredentials.add(passwordCredentialConfiguration4);
applicationRestrictions.setPasswordCredentials(passwordCredentials);
LinkedList<KeyCredentialConfiguration> keyCredentials = new LinkedList<KeyCredentialConfiguration>();
KeyCredentialConfiguration keyCredentialConfiguration = new KeyCredentialConfiguration();
keyCredentialConfiguration.setRestrictionType(AppKeyCredentialRestrictionType.AsymmetricKeyLifetime);
PeriodAndDuration maxLifetime5 = PeriodAndDuration.ofDuration(Duration.parse("P30D"));
keyCredentialConfiguration.setMaxLifetime(maxLifetime5);
OffsetDateTime restrictForAppsCreatedAfterDateTime5 = OffsetDateTime.parse("2015-01-01T10:37:00Z");
keyCredentialConfiguration.setRestrictForAppsCreatedAfterDateTime(restrictForAppsCreatedAfterDateTime5);
keyCredentials.add(keyCredentialConfiguration);
applicationRestrictions.setKeyCredentials(keyCredentials);
tenantAppManagementPolicy.setApplicationRestrictions(applicationRestrictions);
TenantAppManagementPolicy result = graphClient.policies().defaultAppManagementPolicy().patch(tenantAppManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const tenantAppManagementPolicy = {
    isEnabled: true,
    applicationRestrictions: {
        passwordCredentials: [
            {
                restrictionType: 'passwordAddition',
                maxLifetime: null,
                restrictForAppsCreatedAfterDateTime: '2021-01-01T10:37:00Z'
            },
            {
                restrictionType: 'passwordLifetime',
                maxLifetime: 'P4DT12H30M5S',
                restrictForAppsCreatedAfterDateTime: '2017-01-01T10:37:00Z'
            },
            {
                restrictionType: 'symmetricKeyAddition',
                maxLifetime: null,
                restrictForAppsCreatedAfterDateTime: '2021-01-01T10:37:00Z'
            },
            {
                restrictionType: 'customPasswordAddition',
                maxLifetime: null,
                restrictForAppsCreatedAfterDateTime: '2015-01-01T10:37:00Z'
            },
            {
                restrictionType: 'symmetricKeyLifetime',
                maxLifetime: 'P40D',
                restrictForAppsCreatedAfterDateTime: '2015-01-01T10:37:00Z'
            }
        ],
        keyCredentials: [
            {
                restrictionType: 'asymmetricKeyLifetime',
                maxLifetime: 'P30D',
                restrictForAppsCreatedAfterDateTime: '2015-01-01T10:37:00Z'
            },
        ]
    }
};

await client.api('/policies/defaultAppManagementPolicy')
	.update(tenantAppManagementPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TenantAppManagementPolicy;
use Microsoft\Graph\Generated\Models\AppManagementApplicationConfiguration;
use Microsoft\Graph\Generated\Models\PasswordCredentialConfiguration;
use Microsoft\Graph\Generated\Models\AppCredentialRestrictionType;
use Microsoft\Graph\Generated\Models\KeyCredentialConfiguration;
use Microsoft\Graph\Generated\Models\AppKeyCredentialRestrictionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TenantAppManagementPolicy();
$requestBody->setIsEnabled(true);
$applicationRestrictions = new AppManagementApplicationConfiguration();
$passwordCredentialsPasswordCredentialConfiguration1 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration1->setRestrictionType(new AppCredentialRestrictionType('passwordAddition'));
$passwordCredentialsPasswordCredentialConfiguration1->setMaxLifetime(null);
$passwordCredentialsPasswordCredentialConfiguration1->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2021-01-01T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration1;
$passwordCredentialsPasswordCredentialConfiguration2 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration2->setRestrictionType(new AppCredentialRestrictionType('passwordLifetime'));
$passwordCredentialsPasswordCredentialConfiguration2->setMaxLifetime(new \DateInterval('P4DT12H30M5S'));
$passwordCredentialsPasswordCredentialConfiguration2->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2017-01-01T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration2;
$passwordCredentialsPasswordCredentialConfiguration3 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration3->setRestrictionType(new AppCredentialRestrictionType('symmetricKeyAddition'));
$passwordCredentialsPasswordCredentialConfiguration3->setMaxLifetime(null);
$passwordCredentialsPasswordCredentialConfiguration3->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2021-01-01T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration3;
$passwordCredentialsPasswordCredentialConfiguration4 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration4->setRestrictionType(new AppCredentialRestrictionType('customPasswordAddition'));
$passwordCredentialsPasswordCredentialConfiguration4->setMaxLifetime(null);
$passwordCredentialsPasswordCredentialConfiguration4->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2015-01-01T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration4;
$passwordCredentialsPasswordCredentialConfiguration5 = new PasswordCredentialConfiguration();
$passwordCredentialsPasswordCredentialConfiguration5->setRestrictionType(new AppCredentialRestrictionType('symmetricKeyLifetime'));
$passwordCredentialsPasswordCredentialConfiguration5->setMaxLifetime(new \DateInterval('P40D'));
$passwordCredentialsPasswordCredentialConfiguration5->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2015-01-01T10:37:00Z'));
$passwordCredentialsArray []= $passwordCredentialsPasswordCredentialConfiguration5;
$applicationRestrictions->setPasswordCredentials($passwordCredentialsArray);

$keyCredentialsKeyCredentialConfiguration1 = new KeyCredentialConfiguration();
$keyCredentialsKeyCredentialConfiguration1->setRestrictionType(new AppKeyCredentialRestrictionType('asymmetricKeyLifetime'));
$keyCredentialsKeyCredentialConfiguration1->setMaxLifetime(new \DateInterval('P30D'));
$keyCredentialsKeyCredentialConfiguration1->setRestrictForAppsCreatedAfterDateTime(new \DateTime('2015-01-01T10:37:00Z'));
$keyCredentialsArray []= $keyCredentialsKeyCredentialConfiguration1;
$applicationRestrictions->setKeyCredentials($keyCredentialsArray);

$requestBody->setApplicationRestrictions($applicationRestrictions);

$result = $graphServiceClient->policies()->defaultAppManagementPolicy()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	isEnabled = $true
	applicationRestrictions = @{
		passwordCredentials = @(
			@{
				restrictionType = "passwordAddition"
				maxLifetime = $null
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2021-01-01T10:37:00Z")
			}
			@{
				restrictionType = "passwordLifetime"
				maxLifetime = "P4DT12H30M5S"
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2017-01-01T10:37:00Z")
			}
			@{
				restrictionType = "symmetricKeyAddition"
				maxLifetime = $null
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2021-01-01T10:37:00Z")
			}
			@{
				restrictionType = "customPasswordAddition"
				maxLifetime = $null
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2015-01-01T10:37:00Z")
			}
			@{
				restrictionType = "symmetricKeyLifetime"
				maxLifetime = "P40D"
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2015-01-01T10:37:00Z")
			}
		)
		keyCredentials = @(
			@{
				restrictionType = "asymmetricKeyLifetime"
				maxLifetime = "P30D"
				restrictForAppsCreatedAfterDateTime = [System.DateTime]::Parse("2015-01-01T10:37:00Z")
			}
		)
	}
}

Update-MgPolicyDefaultAppManagementPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.tenant_app_management_policy import TenantAppManagementPolicy
from msgraph.generated.models.app_management_application_configuration import AppManagementApplicationConfiguration
from msgraph.generated.models.password_credential_configuration import PasswordCredentialConfiguration
from msgraph.generated.models.app_credential_restriction_type import AppCredentialRestrictionType
from msgraph.generated.models.key_credential_configuration import KeyCredentialConfiguration
from msgraph.generated.models.app_key_credential_restriction_type import AppKeyCredentialRestrictionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TenantAppManagementPolicy(
	is_enabled = True,
	application_restrictions = AppManagementApplicationConfiguration(
		password_credentials = [
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.PasswordAddition,
				max_lifetime = None,
				restrict_for_apps_created_after_date_time = "2021-01-01T10:37:00Z",
			),
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.PasswordLifetime,
				max_lifetime = "P4DT12H30M5S",
				restrict_for_apps_created_after_date_time = "2017-01-01T10:37:00Z",
			),
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.SymmetricKeyAddition,
				max_lifetime = None,
				restrict_for_apps_created_after_date_time = "2021-01-01T10:37:00Z",
			),
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.CustomPasswordAddition,
				max_lifetime = None,
				restrict_for_apps_created_after_date_time = "2015-01-01T10:37:00Z",
			),
			PasswordCredentialConfiguration(
				restriction_type = AppCredentialRestrictionType.SymmetricKeyLifetime,
				max_lifetime = "P40D",
				restrict_for_apps_created_after_date_time = "2015-01-01T10:37:00Z",
			),
		],
		key_credentials = [
			KeyCredentialConfiguration(
				restriction_type = AppKeyCredentialRestrictionType.AsymmetricKeyLifetime,
				max_lifetime = "P30D",
				restrict_for_apps_created_after_date_time = "2015-01-01T10:37:00Z",
			),
		],
	),
)

result = await graph_client.policies.default_app_management_policy.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
