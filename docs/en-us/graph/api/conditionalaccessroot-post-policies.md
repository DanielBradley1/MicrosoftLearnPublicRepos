<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-post-policies?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# Create conditionalAccessPolicy

Namespace: microsoft.graph

Create a new [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.Read.All and Policy.ReadWrite.ConditionalAccess | Application.Read.All and Policy.ReadWrite.ConditionalAccess |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.Read.All and Policy.ReadWrite.ConditionalAccess | Application.Read.All and Policy.ReadWrite.ConditionalAccess |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Administrator
- Conditional Access Administrator

Note

This method has a [known permissions issue](https://learn.microsoft.com/en-us/graph/known-issues#conditional-access-policy-requires-consent-to-additional-permission) and may require consent to multiple permissions.

## HTTP request

```http
POST /identity/conditionalAccess/policies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) object.

A valid policy should contain at least one of the following:

- [application](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessapplications?view=graph-rest-1.0) rule. For example, `'includeApplications': 'none'`.
- [user](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessusers?view=graph-rest-1.0) rule. For example, `'includeUsers': 'none'`.
- [grant](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessgrantcontrols?view=graph-rest-1.0)/[session](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrols?view=graph-rest-1.0) control.

## Response

If successful, this method returns a `201 Created` response code and a new [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Require MFA to access Exchange Online outside of trusted locations

#### Request

The following example shows a common request to require multifactor authentication for access to Exchange Online from modern authentication clients outside of trusted locations for a particular group.

> **Note:** You must set up your trusted locations before using this operation.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/policies
Content-type: application/json

{
    "displayName": "Access to EXO requires MFA",
    "state": "enabled",
    "conditions": {
        "clientAppTypes": [
            "mobileAppsAndDesktopClients",
            "browser"
        ],
        "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ]
        },
        "users": {
            "includeGroups": ["ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"]
        },
        "locations": {
            "includeLocations": [
                "All"
            ],
            "excludeLocations": [
                "AllTrusted"
            ]
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "mfa"
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConditionalAccessPolicy
{
	DisplayName = "Access to EXO requires MFA",
	State = ConditionalAccessPolicyState.Enabled,
	Conditions = new ConditionalAccessConditionSet
	{
		ClientAppTypes = new List<ConditionalAccessClientApp?>
		{
			ConditionalAccessClientApp.MobileAppsAndDesktopClients,
			ConditionalAccessClientApp.Browser,
		},
		Applications = new ConditionalAccessApplications
		{
			IncludeApplications = new List<string>
			{
				"00000002-0000-0ff1-ce00-000000000000",
			},
		},
		Users = new ConditionalAccessUsers
		{
			IncludeGroups = new List<string>
			{
				"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
			},
		},
		Locations = new ConditionalAccessLocations
		{
			IncludeLocations = new List<string>
			{
				"All",
			},
			ExcludeLocations = new List<string>
			{
				"AllTrusted",
			},
		},
	},
	GrantControls = new ConditionalAccessGrantControls
	{
		Operator = "OR",
		BuiltInControls = new List<ConditionalAccessGrantControl?>
		{
			ConditionalAccessGrantControl.Mfa,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Policies.PostAsync(requestBody);
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

requestBody := graphmodels.NewConditionalAccessPolicy()
displayName := "Access to EXO requires MFA"
requestBody.SetDisplayName(&displayName) 
state := graphmodels.ENABLED_CONDITIONALACCESSPOLICYSTATE 
requestBody.SetState(&state) 
conditions := graphmodels.NewConditionalAccessConditionSet()
clientAppTypes := []graphmodels.ConditionalAccessClientAppable {
	conditionalAccessClientApp := graphmodels.MOBILEAPPSANDDESKTOPCLIENTS_CONDITIONALACCESSCLIENTAPP 
	conditions.SetConditionalAccessClientApp(&conditionalAccessClientApp) 
	conditionalAccessClientApp := graphmodels.BROWSER_CONDITIONALACCESSCLIENTAPP 
	conditions.SetConditionalAccessClientApp(&conditionalAccessClientApp)
}
conditions.SetClientAppTypes(clientAppTypes)
applications := graphmodels.NewConditionalAccessApplications()
includeApplications := []string {
	"00000002-0000-0ff1-ce00-000000000000",
}
applications.SetIncludeApplications(includeApplications)
conditions.SetApplications(applications)
users := graphmodels.NewConditionalAccessUsers()
includeGroups := []string {
	"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
}
users.SetIncludeGroups(includeGroups)
conditions.SetUsers(users)
locations := graphmodels.NewConditionalAccessLocations()
includeLocations := []string {
	"All",
}
locations.SetIncludeLocations(includeLocations)
excludeLocations := []string {
	"AllTrusted",
}
locations.SetExcludeLocations(excludeLocations)
conditions.SetLocations(locations)
requestBody.SetConditions(conditions)
grantControls := graphmodels.NewConditionalAccessGrantControls()
operator := "OR"
grantControls.SetOperator(&operator) 
builtInControls := []graphmodels.ConditionalAccessGrantControlable {
	conditionalAccessGrantControl := graphmodels.MFA_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl)
}
grantControls.SetBuiltInControls(builtInControls)
requestBody.SetGrantControls(grantControls)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policies, err := graphClient.Identity().ConditionalAccess().Policies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessPolicy conditionalAccessPolicy = new ConditionalAccessPolicy();
conditionalAccessPolicy.setDisplayName("Access to EXO requires MFA");
conditionalAccessPolicy.setState(ConditionalAccessPolicyState.Enabled);
ConditionalAccessConditionSet conditions = new ConditionalAccessConditionSet();
LinkedList<ConditionalAccessClientApp> clientAppTypes = new LinkedList<ConditionalAccessClientApp>();
clientAppTypes.add(ConditionalAccessClientApp.MobileAppsAndDesktopClients);
clientAppTypes.add(ConditionalAccessClientApp.Browser);
conditions.setClientAppTypes(clientAppTypes);
ConditionalAccessApplications applications = new ConditionalAccessApplications();
LinkedList<String> includeApplications = new LinkedList<String>();
includeApplications.add("00000002-0000-0ff1-ce00-000000000000");
applications.setIncludeApplications(includeApplications);
conditions.setApplications(applications);
ConditionalAccessUsers users = new ConditionalAccessUsers();
LinkedList<String> includeGroups = new LinkedList<String>();
includeGroups.add("ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba");
users.setIncludeGroups(includeGroups);
conditions.setUsers(users);
ConditionalAccessLocations locations = new ConditionalAccessLocations();
LinkedList<String> includeLocations = new LinkedList<String>();
includeLocations.add("All");
locations.setIncludeLocations(includeLocations);
LinkedList<String> excludeLocations = new LinkedList<String>();
excludeLocations.add("AllTrusted");
locations.setExcludeLocations(excludeLocations);
conditions.setLocations(locations);
conditionalAccessPolicy.setConditions(conditions);
ConditionalAccessGrantControls grantControls = new ConditionalAccessGrantControls();
grantControls.setOperator("OR");
LinkedList<ConditionalAccessGrantControl> builtInControls = new LinkedList<ConditionalAccessGrantControl>();
builtInControls.add(ConditionalAccessGrantControl.Mfa);
grantControls.setBuiltInControls(builtInControls);
conditionalAccessPolicy.setGrantControls(grantControls);
ConditionalAccessPolicy result = graphClient.identity().conditionalAccess().policies().post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conditionalAccessPolicy = {
    displayName: 'Access to EXO requires MFA',
    state: 'enabled',
    conditions: {
        clientAppTypes: [
            'mobileAppsAndDesktopClients',
            'browser'
        ],
        applications: {
            includeApplications: [
                '00000002-0000-0ff1-ce00-000000000000'
            ]
        },
        users: {
            includeGroups: ['ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba']
        },
        locations: {
            includeLocations: [
                'All'
            ],
            excludeLocations: [
                'AllTrusted'
            ]
        }
    },
    grantControls: {
        operator: 'OR',
        builtInControls: [
            'mfa'
        ]
    }
};

await client.api('/identity/conditionalAccess/policies')
	.post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicy;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicyState;
use Microsoft\Graph\Generated\Models\ConditionalAccessConditionSet;
use Microsoft\Graph\Generated\Models\ConditionalAccessClientApp;
use Microsoft\Graph\Generated\Models\ConditionalAccessApplications;
use Microsoft\Graph\Generated\Models\ConditionalAccessUsers;
use Microsoft\Graph\Generated\Models\ConditionalAccessLocations;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControls;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControl;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConditionalAccessPolicy();
$requestBody->setDisplayName('Access to EXO requires MFA');
$requestBody->setState(new ConditionalAccessPolicyState('enabled'));
$conditions = new ConditionalAccessConditionSet();
$conditions->setClientAppTypes([new ConditionalAccessClientApp('mobileAppsAndDesktopClients'),new ConditionalAccessClientApp('browser'),	]);
$conditionsApplications = new ConditionalAccessApplications();
$conditionsApplications->setIncludeApplications(['00000002-0000-0ff1-ce00-000000000000', 	]);
$conditions->setApplications($conditionsApplications);
$conditionsUsers = new ConditionalAccessUsers();
$conditionsUsers->setIncludeGroups(['ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba', 	]);
$conditions->setUsers($conditionsUsers);
$conditionsLocations = new ConditionalAccessLocations();
$conditionsLocations->setIncludeLocations(['All', 	]);
$conditionsLocations->setExcludeLocations(['AllTrusted', 	]);
$conditions->setLocations($conditionsLocations);
$requestBody->setConditions($conditions);
$grantControls = new ConditionalAccessGrantControls();
$grantControls->setOperator('OR');
$grantControls->setBuiltInControls([new ConditionalAccessGrantControl('mfa'),	]);
$requestBody->setGrantControls($grantControls);

$result = $graphServiceClient->identity()->conditionalAccess()->policies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	displayName = "Access to EXO requires MFA"
	state = "enabled"
	conditions = @{
		clientAppTypes = @(
		"mobileAppsAndDesktopClients"
	"browser"
)
applications = @{
	includeApplications = @(
	"00000002-0000-0ff1-ce00-000000000000"
)
}
users = @{
includeGroups = @(
"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"
)
}
locations = @{
includeLocations = @(
"All"
)
excludeLocations = @(
"AllTrusted"
)
}
}
grantControls = @{
operator = "OR"
builtInControls = @(
"mfa"
)
}
}

New-MgIdentityConditionalAccessPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conditional_access_policy import ConditionalAccessPolicy
from msgraph.generated.models.conditional_access_policy_state import ConditionalAccessPolicyState
from msgraph.generated.models.conditional_access_condition_set import ConditionalAccessConditionSet
from msgraph.generated.models.conditional_access_client_app import ConditionalAccessClientApp
from msgraph.generated.models.conditional_access_applications import ConditionalAccessApplications
from msgraph.generated.models.conditional_access_users import ConditionalAccessUsers
from msgraph.generated.models.conditional_access_locations import ConditionalAccessLocations
from msgraph.generated.models.conditional_access_grant_controls import ConditionalAccessGrantControls
from msgraph.generated.models.conditional_access_grant_control import ConditionalAccessGrantControl
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConditionalAccessPolicy(
	display_name = "Access to EXO requires MFA",
	state = ConditionalAccessPolicyState.Enabled,
	conditions = ConditionalAccessConditionSet(
		client_app_types = [
			ConditionalAccessClientApp.MobileAppsAndDesktopClients,
			ConditionalAccessClientApp.Browser,
		],
		applications = ConditionalAccessApplications(
			include_applications = [
				"00000002-0000-0ff1-ce00-000000000000",
			],
		),
		users = ConditionalAccessUsers(
			include_groups = [
				"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
			],
		),
		locations = ConditionalAccessLocations(
			include_locations = [
				"All",
			],
			exclude_locations = [
				"AllTrusted",
			],
		),
	),
	grant_controls = ConditionalAccessGrantControls(
		operator = "OR",
		built_in_controls = [
			ConditionalAccessGrantControl.Mfa,
		],
	),
)

result = await graph_client.identity.conditional_access.policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#conditionalAccess/policies/$entity",
    "id": "7359d0e0-d8a9-4afa-8a93-e23e099d7be8",
    "displayName": "Access to EXO requires MFA",
    "createdDateTime": "2019-10-14T19:52:00.050958Z",
    "modifiedDateTime": null,
    "state": "enabled",
    "sessionControls": null,
    "conditions": {
        "signInRiskLevels": [],
        "clientAppTypes": [
            "mobileAppsAndDesktopClients",
            "browser"
        ],
        "platforms": null,
        "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ],
            "excludeApplications": [],
            "includeUserActions": []
        },
        "users": {
            "includeUsers": [],
            "excludeUsers": [],
            "includeGroups": [
                "ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"
            ],
            "excludeGroups": [],
            "includeRoles": [],
            "excludeRoles": []
        },
        "locations": {
            "includeLocations": [
                "All"
            ],
            "excludeLocations": [
                "AllTrusted"
            ]
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "mfa"
        ],
        "customAuthenticationFactors": [],
        "termsOfUse": []
    }
}
```

### Example 2: Block access to Exchange Online from nontrusted regions

#### Request

The following example shows a request to block access to Exchange Online from non-trusted/unknown regions. This example assumes that the named location with ID = 198ad66e-87b3-4157-85a3-8a7b51794ee9 corresponds to a list of non-trusted/unknown regions.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/policies
Content-type: application/json

{
    "displayName": "Block access to EXO non-trusted regions.",
    "state": "enabled",
    "conditions": {
        "clientAppTypes": [
            "all"
        ],
        "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ]
        },
        "users": {
            "includeGroups": ["ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"]
        },
        "locations": {
            "includeLocations": [
                "198ad66e-87b3-4157-85a3-8a7b51794ee9"
            ]
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "block"
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConditionalAccessPolicy
{
	DisplayName = "Block access to EXO non-trusted regions.",
	State = ConditionalAccessPolicyState.Enabled,
	Conditions = new ConditionalAccessConditionSet
	{
		ClientAppTypes = new List<ConditionalAccessClientApp?>
		{
			ConditionalAccessClientApp.All,
		},
		Applications = new ConditionalAccessApplications
		{
			IncludeApplications = new List<string>
			{
				"00000002-0000-0ff1-ce00-000000000000",
			},
		},
		Users = new ConditionalAccessUsers
		{
			IncludeGroups = new List<string>
			{
				"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
			},
		},
		Locations = new ConditionalAccessLocations
		{
			IncludeLocations = new List<string>
			{
				"198ad66e-87b3-4157-85a3-8a7b51794ee9",
			},
		},
	},
	GrantControls = new ConditionalAccessGrantControls
	{
		Operator = "OR",
		BuiltInControls = new List<ConditionalAccessGrantControl?>
		{
			ConditionalAccessGrantControl.Block,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Policies.PostAsync(requestBody);
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

requestBody := graphmodels.NewConditionalAccessPolicy()
displayName := "Block access to EXO non-trusted regions."
requestBody.SetDisplayName(&displayName) 
state := graphmodels.ENABLED_CONDITIONALACCESSPOLICYSTATE 
requestBody.SetState(&state) 
conditions := graphmodels.NewConditionalAccessConditionSet()
clientAppTypes := []graphmodels.ConditionalAccessClientAppable {
	conditionalAccessClientApp := graphmodels.ALL_CONDITIONALACCESSCLIENTAPP 
	conditions.SetConditionalAccessClientApp(&conditionalAccessClientApp)
}
conditions.SetClientAppTypes(clientAppTypes)
applications := graphmodels.NewConditionalAccessApplications()
includeApplications := []string {
	"00000002-0000-0ff1-ce00-000000000000",
}
applications.SetIncludeApplications(includeApplications)
conditions.SetApplications(applications)
users := graphmodels.NewConditionalAccessUsers()
includeGroups := []string {
	"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
}
users.SetIncludeGroups(includeGroups)
conditions.SetUsers(users)
locations := graphmodels.NewConditionalAccessLocations()
includeLocations := []string {
	"198ad66e-87b3-4157-85a3-8a7b51794ee9",
}
locations.SetIncludeLocations(includeLocations)
conditions.SetLocations(locations)
requestBody.SetConditions(conditions)
grantControls := graphmodels.NewConditionalAccessGrantControls()
operator := "OR"
grantControls.SetOperator(&operator) 
builtInControls := []graphmodels.ConditionalAccessGrantControlable {
	conditionalAccessGrantControl := graphmodels.BLOCK_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl)
}
grantControls.SetBuiltInControls(builtInControls)
requestBody.SetGrantControls(grantControls)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policies, err := graphClient.Identity().ConditionalAccess().Policies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessPolicy conditionalAccessPolicy = new ConditionalAccessPolicy();
conditionalAccessPolicy.setDisplayName("Block access to EXO non-trusted regions.");
conditionalAccessPolicy.setState(ConditionalAccessPolicyState.Enabled);
ConditionalAccessConditionSet conditions = new ConditionalAccessConditionSet();
LinkedList<ConditionalAccessClientApp> clientAppTypes = new LinkedList<ConditionalAccessClientApp>();
clientAppTypes.add(ConditionalAccessClientApp.All);
conditions.setClientAppTypes(clientAppTypes);
ConditionalAccessApplications applications = new ConditionalAccessApplications();
LinkedList<String> includeApplications = new LinkedList<String>();
includeApplications.add("00000002-0000-0ff1-ce00-000000000000");
applications.setIncludeApplications(includeApplications);
conditions.setApplications(applications);
ConditionalAccessUsers users = new ConditionalAccessUsers();
LinkedList<String> includeGroups = new LinkedList<String>();
includeGroups.add("ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba");
users.setIncludeGroups(includeGroups);
conditions.setUsers(users);
ConditionalAccessLocations locations = new ConditionalAccessLocations();
LinkedList<String> includeLocations = new LinkedList<String>();
includeLocations.add("198ad66e-87b3-4157-85a3-8a7b51794ee9");
locations.setIncludeLocations(includeLocations);
conditions.setLocations(locations);
conditionalAccessPolicy.setConditions(conditions);
ConditionalAccessGrantControls grantControls = new ConditionalAccessGrantControls();
grantControls.setOperator("OR");
LinkedList<ConditionalAccessGrantControl> builtInControls = new LinkedList<ConditionalAccessGrantControl>();
builtInControls.add(ConditionalAccessGrantControl.Block);
grantControls.setBuiltInControls(builtInControls);
conditionalAccessPolicy.setGrantControls(grantControls);
ConditionalAccessPolicy result = graphClient.identity().conditionalAccess().policies().post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conditionalAccessPolicy = {
    displayName: 'Block access to EXO non-trusted regions.',
    state: 'enabled',
    conditions: {
        clientAppTypes: [
            'all'
        ],
        applications: {
            includeApplications: [
                '00000002-0000-0ff1-ce00-000000000000'
            ]
        },
        users: {
            includeGroups: ['ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba']
        },
        locations: {
            includeLocations: [
                '198ad66e-87b3-4157-85a3-8a7b51794ee9'
            ]
        }
    },
    grantControls: {
        operator: 'OR',
        builtInControls: [
            'block'
        ]
    }
};

await client.api('/identity/conditionalAccess/policies')
	.post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicy;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicyState;
use Microsoft\Graph\Generated\Models\ConditionalAccessConditionSet;
use Microsoft\Graph\Generated\Models\ConditionalAccessClientApp;
use Microsoft\Graph\Generated\Models\ConditionalAccessApplications;
use Microsoft\Graph\Generated\Models\ConditionalAccessUsers;
use Microsoft\Graph\Generated\Models\ConditionalAccessLocations;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControls;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControl;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConditionalAccessPolicy();
$requestBody->setDisplayName('Block access to EXO non-trusted regions.');
$requestBody->setState(new ConditionalAccessPolicyState('enabled'));
$conditions = new ConditionalAccessConditionSet();
$conditions->setClientAppTypes([new ConditionalAccessClientApp('all'),	]);
$conditionsApplications = new ConditionalAccessApplications();
$conditionsApplications->setIncludeApplications(['00000002-0000-0ff1-ce00-000000000000', 	]);
$conditions->setApplications($conditionsApplications);
$conditionsUsers = new ConditionalAccessUsers();
$conditionsUsers->setIncludeGroups(['ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba', 	]);
$conditions->setUsers($conditionsUsers);
$conditionsLocations = new ConditionalAccessLocations();
$conditionsLocations->setIncludeLocations(['198ad66e-87b3-4157-85a3-8a7b51794ee9', 	]);
$conditions->setLocations($conditionsLocations);
$requestBody->setConditions($conditions);
$grantControls = new ConditionalAccessGrantControls();
$grantControls->setOperator('OR');
$grantControls->setBuiltInControls([new ConditionalAccessGrantControl('block'),	]);
$requestBody->setGrantControls($grantControls);

$result = $graphServiceClient->identity()->conditionalAccess()->policies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	displayName = "Block access to EXO non-trusted regions."
	state = "enabled"
	conditions = @{
		clientAppTypes = @(
		"all"
	)
	applications = @{
		includeApplications = @(
		"00000002-0000-0ff1-ce00-000000000000"
	)
}
users = @{
	includeGroups = @(
	"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"
)
}
locations = @{
includeLocations = @(
"198ad66e-87b3-4157-85a3-8a7b51794ee9"
)
}
}
grantControls = @{
operator = "OR"
builtInControls = @(
"block"
)
}
}

New-MgIdentityConditionalAccessPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conditional_access_policy import ConditionalAccessPolicy
from msgraph.generated.models.conditional_access_policy_state import ConditionalAccessPolicyState
from msgraph.generated.models.conditional_access_condition_set import ConditionalAccessConditionSet
from msgraph.generated.models.conditional_access_client_app import ConditionalAccessClientApp
from msgraph.generated.models.conditional_access_applications import ConditionalAccessApplications
from msgraph.generated.models.conditional_access_users import ConditionalAccessUsers
from msgraph.generated.models.conditional_access_locations import ConditionalAccessLocations
from msgraph.generated.models.conditional_access_grant_controls import ConditionalAccessGrantControls
from msgraph.generated.models.conditional_access_grant_control import ConditionalAccessGrantControl
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConditionalAccessPolicy(
	display_name = "Block access to EXO non-trusted regions.",
	state = ConditionalAccessPolicyState.Enabled,
	conditions = ConditionalAccessConditionSet(
		client_app_types = [
			ConditionalAccessClientApp.All,
		],
		applications = ConditionalAccessApplications(
			include_applications = [
				"00000002-0000-0ff1-ce00-000000000000",
			],
		),
		users = ConditionalAccessUsers(
			include_groups = [
				"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
			],
		),
		locations = ConditionalAccessLocations(
			include_locations = [
				"198ad66e-87b3-4157-85a3-8a7b51794ee9",
			],
		),
	),
	grant_controls = ConditionalAccessGrantControls(
		operator = "OR",
		built_in_controls = [
			ConditionalAccessGrantControl.Block,
		],
	),
)

result = await graph_client.identity.conditional_access.policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#conditionalAccess/policies/$entity",
    "id": "c98e6c3d-f6ca-42ea-a927-773b6f12a0c2",
    "displayName": "Block access to EXO non-trusted regions.",
    "createdDateTime": "2019-10-14T19:53:11.3705634Z",
    "modifiedDateTime": null,
    "state": "enabled",
    "sessionControls": null,
    "conditions": {
        "signInRiskLevels": [],
        "clientAppTypes": [
            "all"
        ],
        "platforms": null,
        "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ],
            "excludeApplications": [],
            "includeUserActions": []
        },
        "users": {
            "includeUsers": [],
            "excludeUsers": [],
            "includeGroups": [
                "ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"
            ],
            "excludeGroups": [],
            "includeRoles": [],
            "excludeRoles": []
        },
        "locations": {
            "includeLocations": [
                "198ad66e-87b3-4157-85a3-8a7b51794ee9"
            ],
            "excludeLocations": []
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "block"
        ],
        "customAuthenticationFactors": [],
        "termsOfUse": []
    }
}
```

### Example 3: Use all conditions and controls

#### Request

The following example shows a request to use all the conditions and controls.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/policies
Content-type: application/json

{
    "displayName": "Demo app for documentation",
    "state": "disabled",
    "conditions": {
        "signInRiskLevels": [
            "high",
            "medium"
        ],
        "clientAppTypes": [
            "mobileAppsAndDesktopClients",
            "exchangeActiveSync",
            "other"
        ],
        "applications": {
            "includeApplications": [
                "All"
            ],
            "excludeApplications": [
                "499b84ac-1321-427f-aa17-267ca6975798",
                "00000007-0000-0000-c000-000000000000",
                "de8bc8b5-d9f9-48b1-a8ad-b748da725064",
                "00000012-0000-0000-c000-000000000000",
                "797f4846-ba00-4fd7-ba43-dac1f8f63013",
                "05a65629-4c1b-48c1-a78b-804c4abdd4af",
                "7df0a125-d3be-4c96-aa54-591f83ff541c"
            ],
            "includeUserActions": []
        },
        "users": {
            "includeUsers": [
                "a702a13d-a437-4a07-8a7e-8c052de62dfd"
            ],
            "excludeUsers": [
                "124c5b6a-ffa5-483a-9b88-04c3fce5574a",
                "GuestsOrExternalUsers"
            ],
            "includeGroups": [],
            "excludeGroups": [],
            "includeRoles": [
                "9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
                "cf1c38e5-3621-4004-a7cb-879624dced7c",
                "c4e39bd9-1100-46d3-8c65-fb160da0071f"
            ],
            "excludeRoles": [
                "b0f54661-2d74-4c50-afa3-1ec803f12efe"
            ]
        },
        "platforms": {
            "includePlatforms": [
                "all"
            ],
            "excludePlatforms": [
                "iOS",
                "windowsPhone"
            ]
        },
        "locations": {
            "includeLocations": [
                "AllTrusted"
            ],
            "excludeLocations": [
                "00000000-0000-0000-0000-000000000000",
                "d2136c9c-b049-47ae-b9cf-316e04ef7198"
            ]
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "mfa",
            "compliantDevice",
            "domainJoinedDevice",
            "approvedApplication",
            "compliantApplication"
        ],
        "customAuthenticationFactors": [],
        "termsOfUse": [
            "ce580154-086a-40fd-91df-8a60abac81a0",
            "7f29d675-caff-43e1-8a53-1b8516ed2075"
        ]
    },
    "sessionControls": {
        "applicationEnforcedRestrictions": null,
        "persistentBrowser": null,
        "cloudAppSecurity": {
            "cloudAppSecurityType": "blockDownloads",
            "isEnabled": true
        },
        "signInFrequency": {
            "value": 4,
            "type": "hours",
            "isEnabled": true
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConditionalAccessPolicy
{
	DisplayName = "Demo app for documentation",
	State = ConditionalAccessPolicyState.Disabled,
	Conditions = new ConditionalAccessConditionSet
	{
		SignInRiskLevels = new List<RiskLevel?>
		{
			RiskLevel.High,
			RiskLevel.Medium,
		},
		ClientAppTypes = new List<ConditionalAccessClientApp?>
		{
			ConditionalAccessClientApp.MobileAppsAndDesktopClients,
			ConditionalAccessClientApp.ExchangeActiveSync,
			ConditionalAccessClientApp.Other,
		},
		Applications = new ConditionalAccessApplications
		{
			IncludeApplications = new List<string>
			{
				"All",
			},
			ExcludeApplications = new List<string>
			{
				"499b84ac-1321-427f-aa17-267ca6975798",
				"00000007-0000-0000-c000-000000000000",
				"de8bc8b5-d9f9-48b1-a8ad-b748da725064",
				"00000012-0000-0000-c000-000000000000",
				"797f4846-ba00-4fd7-ba43-dac1f8f63013",
				"05a65629-4c1b-48c1-a78b-804c4abdd4af",
				"7df0a125-d3be-4c96-aa54-591f83ff541c",
			},
			IncludeUserActions = new List<string>
			{
			},
		},
		Users = new ConditionalAccessUsers
		{
			IncludeUsers = new List<string>
			{
				"a702a13d-a437-4a07-8a7e-8c052de62dfd",
			},
			ExcludeUsers = new List<string>
			{
				"124c5b6a-ffa5-483a-9b88-04c3fce5574a",
				"GuestsOrExternalUsers",
			},
			IncludeGroups = new List<string>
			{
			},
			ExcludeGroups = new List<string>
			{
			},
			IncludeRoles = new List<string>
			{
				"9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
				"cf1c38e5-3621-4004-a7cb-879624dced7c",
				"c4e39bd9-1100-46d3-8c65-fb160da0071f",
			},
			ExcludeRoles = new List<string>
			{
				"b0f54661-2d74-4c50-afa3-1ec803f12efe",
			},
		},
		Platforms = new ConditionalAccessPlatforms
		{
			IncludePlatforms = new List<ConditionalAccessDevicePlatform?>
			{
				ConditionalAccessDevicePlatform.All,
			},
			ExcludePlatforms = new List<ConditionalAccessDevicePlatform?>
			{
				ConditionalAccessDevicePlatform.IOS,
				ConditionalAccessDevicePlatform.WindowsPhone,
			},
		},
		Locations = new ConditionalAccessLocations
		{
			IncludeLocations = new List<string>
			{
				"AllTrusted",
			},
			ExcludeLocations = new List<string>
			{
				"00000000-0000-0000-0000-000000000000",
				"d2136c9c-b049-47ae-b9cf-316e04ef7198",
			},
		},
	},
	GrantControls = new ConditionalAccessGrantControls
	{
		Operator = "OR",
		BuiltInControls = new List<ConditionalAccessGrantControl?>
		{
			ConditionalAccessGrantControl.Mfa,
			ConditionalAccessGrantControl.CompliantDevice,
			ConditionalAccessGrantControl.DomainJoinedDevice,
			ConditionalAccessGrantControl.ApprovedApplication,
			ConditionalAccessGrantControl.CompliantApplication,
		},
		CustomAuthenticationFactors = new List<string>
		{
		},
		TermsOfUse = new List<string>
		{
			"ce580154-086a-40fd-91df-8a60abac81a0",
			"7f29d675-caff-43e1-8a53-1b8516ed2075",
		},
	},
	SessionControls = new ConditionalAccessSessionControls
	{
		ApplicationEnforcedRestrictions = null,
		PersistentBrowser = null,
		CloudAppSecurity = new CloudAppSecuritySessionControl
		{
			CloudAppSecurityType = CloudAppSecuritySessionControlType.BlockDownloads,
			IsEnabled = true,
		},
		SignInFrequency = new SignInFrequencySessionControl
		{
			Value = 4,
			Type = SigninFrequencyType.Hours,
			IsEnabled = true,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Policies.PostAsync(requestBody);
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

requestBody := graphmodels.NewConditionalAccessPolicy()
displayName := "Demo app for documentation"
requestBody.SetDisplayName(&displayName) 
state := graphmodels.DISABLED_CONDITIONALACCESSPOLICYSTATE 
requestBody.SetState(&state) 
conditions := graphmodels.NewConditionalAccessConditionSet()
signInRiskLevels := []graphmodels.RiskLevelable {
	riskLevel := graphmodels.HIGH_RISKLEVEL 
	conditions.SetRiskLevel(&riskLevel) 
	riskLevel := graphmodels.MEDIUM_RISKLEVEL 
	conditions.SetRiskLevel(&riskLevel)
}
conditions.SetSignInRiskLevels(signInRiskLevels)
clientAppTypes := []graphmodels.ConditionalAccessClientAppable {
	conditionalAccessClientApp := graphmodels.MOBILEAPPSANDDESKTOPCLIENTS_CONDITIONALACCESSCLIENTAPP 
	conditions.SetConditionalAccessClientApp(&conditionalAccessClientApp) 
	conditionalAccessClientApp := graphmodels.EXCHANGEACTIVESYNC_CONDITIONALACCESSCLIENTAPP 
	conditions.SetConditionalAccessClientApp(&conditionalAccessClientApp) 
	conditionalAccessClientApp := graphmodels.OTHER_CONDITIONALACCESSCLIENTAPP 
	conditions.SetConditionalAccessClientApp(&conditionalAccessClientApp)
}
conditions.SetClientAppTypes(clientAppTypes)
applications := graphmodels.NewConditionalAccessApplications()
includeApplications := []string {
	"All",
}
applications.SetIncludeApplications(includeApplications)
excludeApplications := []string {
	"499b84ac-1321-427f-aa17-267ca6975798",
	"00000007-0000-0000-c000-000000000000",
	"de8bc8b5-d9f9-48b1-a8ad-b748da725064",
	"00000012-0000-0000-c000-000000000000",
	"797f4846-ba00-4fd7-ba43-dac1f8f63013",
	"05a65629-4c1b-48c1-a78b-804c4abdd4af",
	"7df0a125-d3be-4c96-aa54-591f83ff541c",
}
applications.SetExcludeApplications(excludeApplications)
includeUserActions := []string {

}
applications.SetIncludeUserActions(includeUserActions)
conditions.SetApplications(applications)
users := graphmodels.NewConditionalAccessUsers()
includeUsers := []string {
	"a702a13d-a437-4a07-8a7e-8c052de62dfd",
}
users.SetIncludeUsers(includeUsers)
excludeUsers := []string {
	"124c5b6a-ffa5-483a-9b88-04c3fce5574a",
	"GuestsOrExternalUsers",
}
users.SetExcludeUsers(excludeUsers)
includeGroups := []string {

}
users.SetIncludeGroups(includeGroups)
excludeGroups := []string {

}
users.SetExcludeGroups(excludeGroups)
includeRoles := []string {
	"9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
	"cf1c38e5-3621-4004-a7cb-879624dced7c",
	"c4e39bd9-1100-46d3-8c65-fb160da0071f",
}
users.SetIncludeRoles(includeRoles)
excludeRoles := []string {
	"b0f54661-2d74-4c50-afa3-1ec803f12efe",
}
users.SetExcludeRoles(excludeRoles)
conditions.SetUsers(users)
platforms := graphmodels.NewConditionalAccessPlatforms()
includePlatforms := []graphmodels.ConditionalAccessDevicePlatformable {
	conditionalAccessDevicePlatform := graphmodels.ALL_CONDITIONALACCESSDEVICEPLATFORM 
	platforms.SetConditionalAccessDevicePlatform(&conditionalAccessDevicePlatform)
}
platforms.SetIncludePlatforms(includePlatforms)
excludePlatforms := []graphmodels.ConditionalAccessDevicePlatformable {
	conditionalAccessDevicePlatform := graphmodels.IOS_CONDITIONALACCESSDEVICEPLATFORM 
	platforms.SetConditionalAccessDevicePlatform(&conditionalAccessDevicePlatform) 
	conditionalAccessDevicePlatform := graphmodels.WINDOWSPHONE_CONDITIONALACCESSDEVICEPLATFORM 
	platforms.SetConditionalAccessDevicePlatform(&conditionalAccessDevicePlatform)
}
platforms.SetExcludePlatforms(excludePlatforms)
conditions.SetPlatforms(platforms)
locations := graphmodels.NewConditionalAccessLocations()
includeLocations := []string {
	"AllTrusted",
}
locations.SetIncludeLocations(includeLocations)
excludeLocations := []string {
	"00000000-0000-0000-0000-000000000000",
	"d2136c9c-b049-47ae-b9cf-316e04ef7198",
}
locations.SetExcludeLocations(excludeLocations)
conditions.SetLocations(locations)
requestBody.SetConditions(conditions)
grantControls := graphmodels.NewConditionalAccessGrantControls()
operator := "OR"
grantControls.SetOperator(&operator) 
builtInControls := []graphmodels.ConditionalAccessGrantControlable {
	conditionalAccessGrantControl := graphmodels.MFA_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl) 
	conditionalAccessGrantControl := graphmodels.COMPLIANTDEVICE_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl) 
	conditionalAccessGrantControl := graphmodels.DOMAINJOINEDDEVICE_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl) 
	conditionalAccessGrantControl := graphmodels.APPROVEDAPPLICATION_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl) 
	conditionalAccessGrantControl := graphmodels.COMPLIANTAPPLICATION_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl)
}
grantControls.SetBuiltInControls(builtInControls)
customAuthenticationFactors := []string {

}
grantControls.SetCustomAuthenticationFactors(customAuthenticationFactors)
termsOfUse := []string {
	"ce580154-086a-40fd-91df-8a60abac81a0",
	"7f29d675-caff-43e1-8a53-1b8516ed2075",
}
grantControls.SetTermsOfUse(termsOfUse)
requestBody.SetGrantControls(grantControls)
sessionControls := graphmodels.NewConditionalAccessSessionControls()
applicationEnforcedRestrictions := null
sessionControls.SetApplicationEnforcedRestrictions(&applicationEnforcedRestrictions) 
persistentBrowser := null
sessionControls.SetPersistentBrowser(&persistentBrowser) 
cloudAppSecurity := graphmodels.NewCloudAppSecuritySessionControl()
cloudAppSecurityType := graphmodels.BLOCKDOWNLOADS_CLOUDAPPSECURITYSESSIONCONTROLTYPE 
cloudAppSecurity.SetCloudAppSecurityType(&cloudAppSecurityType) 
isEnabled := true
cloudAppSecurity.SetIsEnabled(&isEnabled) 
sessionControls.SetCloudAppSecurity(cloudAppSecurity)
signInFrequency := graphmodels.NewSignInFrequencySessionControl()
value := int32(4)
signInFrequency.SetValue(&value) 
type := graphmodels.HOURS_SIGNINFREQUENCYTYPE 
signInFrequency.SetType(&type) 
isEnabled := true
signInFrequency.SetIsEnabled(&isEnabled) 
sessionControls.SetSignInFrequency(signInFrequency)
requestBody.SetSessionControls(sessionControls)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policies, err := graphClient.Identity().ConditionalAccess().Policies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessPolicy conditionalAccessPolicy = new ConditionalAccessPolicy();
conditionalAccessPolicy.setDisplayName("Demo app for documentation");
conditionalAccessPolicy.setState(ConditionalAccessPolicyState.Disabled);
ConditionalAccessConditionSet conditions = new ConditionalAccessConditionSet();
LinkedList<RiskLevel> signInRiskLevels = new LinkedList<RiskLevel>();
signInRiskLevels.add(RiskLevel.High);
signInRiskLevels.add(RiskLevel.Medium);
conditions.setSignInRiskLevels(signInRiskLevels);
LinkedList<ConditionalAccessClientApp> clientAppTypes = new LinkedList<ConditionalAccessClientApp>();
clientAppTypes.add(ConditionalAccessClientApp.MobileAppsAndDesktopClients);
clientAppTypes.add(ConditionalAccessClientApp.ExchangeActiveSync);
clientAppTypes.add(ConditionalAccessClientApp.Other);
conditions.setClientAppTypes(clientAppTypes);
ConditionalAccessApplications applications = new ConditionalAccessApplications();
LinkedList<String> includeApplications = new LinkedList<String>();
includeApplications.add("All");
applications.setIncludeApplications(includeApplications);
LinkedList<String> excludeApplications = new LinkedList<String>();
excludeApplications.add("499b84ac-1321-427f-aa17-267ca6975798");
excludeApplications.add("00000007-0000-0000-c000-000000000000");
excludeApplications.add("de8bc8b5-d9f9-48b1-a8ad-b748da725064");
excludeApplications.add("00000012-0000-0000-c000-000000000000");
excludeApplications.add("797f4846-ba00-4fd7-ba43-dac1f8f63013");
excludeApplications.add("05a65629-4c1b-48c1-a78b-804c4abdd4af");
excludeApplications.add("7df0a125-d3be-4c96-aa54-591f83ff541c");
applications.setExcludeApplications(excludeApplications);
LinkedList<String> includeUserActions = new LinkedList<String>();
applications.setIncludeUserActions(includeUserActions);
conditions.setApplications(applications);
ConditionalAccessUsers users = new ConditionalAccessUsers();
LinkedList<String> includeUsers = new LinkedList<String>();
includeUsers.add("a702a13d-a437-4a07-8a7e-8c052de62dfd");
users.setIncludeUsers(includeUsers);
LinkedList<String> excludeUsers = new LinkedList<String>();
excludeUsers.add("124c5b6a-ffa5-483a-9b88-04c3fce5574a");
excludeUsers.add("GuestsOrExternalUsers");
users.setExcludeUsers(excludeUsers);
LinkedList<String> includeGroups = new LinkedList<String>();
users.setIncludeGroups(includeGroups);
LinkedList<String> excludeGroups = new LinkedList<String>();
users.setExcludeGroups(excludeGroups);
LinkedList<String> includeRoles = new LinkedList<String>();
includeRoles.add("9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3");
includeRoles.add("cf1c38e5-3621-4004-a7cb-879624dced7c");
includeRoles.add("c4e39bd9-1100-46d3-8c65-fb160da0071f");
users.setIncludeRoles(includeRoles);
LinkedList<String> excludeRoles = new LinkedList<String>();
excludeRoles.add("b0f54661-2d74-4c50-afa3-1ec803f12efe");
users.setExcludeRoles(excludeRoles);
conditions.setUsers(users);
ConditionalAccessPlatforms platforms = new ConditionalAccessPlatforms();
LinkedList<ConditionalAccessDevicePlatform> includePlatforms = new LinkedList<ConditionalAccessDevicePlatform>();
includePlatforms.add(ConditionalAccessDevicePlatform.All);
platforms.setIncludePlatforms(includePlatforms);
LinkedList<ConditionalAccessDevicePlatform> excludePlatforms = new LinkedList<ConditionalAccessDevicePlatform>();
excludePlatforms.add(ConditionalAccessDevicePlatform.IOS);
excludePlatforms.add(ConditionalAccessDevicePlatform.WindowsPhone);
platforms.setExcludePlatforms(excludePlatforms);
conditions.setPlatforms(platforms);
ConditionalAccessLocations locations = new ConditionalAccessLocations();
LinkedList<String> includeLocations = new LinkedList<String>();
includeLocations.add("AllTrusted");
locations.setIncludeLocations(includeLocations);
LinkedList<String> excludeLocations = new LinkedList<String>();
excludeLocations.add("00000000-0000-0000-0000-000000000000");
excludeLocations.add("d2136c9c-b049-47ae-b9cf-316e04ef7198");
locations.setExcludeLocations(excludeLocations);
conditions.setLocations(locations);
conditionalAccessPolicy.setConditions(conditions);
ConditionalAccessGrantControls grantControls = new ConditionalAccessGrantControls();
grantControls.setOperator("OR");
LinkedList<ConditionalAccessGrantControl> builtInControls = new LinkedList<ConditionalAccessGrantControl>();
builtInControls.add(ConditionalAccessGrantControl.Mfa);
builtInControls.add(ConditionalAccessGrantControl.CompliantDevice);
builtInControls.add(ConditionalAccessGrantControl.DomainJoinedDevice);
builtInControls.add(ConditionalAccessGrantControl.ApprovedApplication);
builtInControls.add(ConditionalAccessGrantControl.CompliantApplication);
grantControls.setBuiltInControls(builtInControls);
LinkedList<String> customAuthenticationFactors = new LinkedList<String>();
grantControls.setCustomAuthenticationFactors(customAuthenticationFactors);
LinkedList<String> termsOfUse = new LinkedList<String>();
termsOfUse.add("ce580154-086a-40fd-91df-8a60abac81a0");
termsOfUse.add("7f29d675-caff-43e1-8a53-1b8516ed2075");
grantControls.setTermsOfUse(termsOfUse);
conditionalAccessPolicy.setGrantControls(grantControls);
ConditionalAccessSessionControls sessionControls = new ConditionalAccessSessionControls();
sessionControls.setApplicationEnforcedRestrictions(null);
sessionControls.setPersistentBrowser(null);
CloudAppSecuritySessionControl cloudAppSecurity = new CloudAppSecuritySessionControl();
cloudAppSecurity.setCloudAppSecurityType(CloudAppSecuritySessionControlType.BlockDownloads);
cloudAppSecurity.setIsEnabled(true);
sessionControls.setCloudAppSecurity(cloudAppSecurity);
SignInFrequencySessionControl signInFrequency = new SignInFrequencySessionControl();
signInFrequency.setValue(4);
signInFrequency.setType(SigninFrequencyType.Hours);
signInFrequency.setIsEnabled(true);
sessionControls.setSignInFrequency(signInFrequency);
conditionalAccessPolicy.setSessionControls(sessionControls);
ConditionalAccessPolicy result = graphClient.identity().conditionalAccess().policies().post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conditionalAccessPolicy = {
    displayName: 'Demo app for documentation',
    state: 'disabled',
    conditions: {
        signInRiskLevels: [
            'high',
            'medium'
        ],
        clientAppTypes: [
            'mobileAppsAndDesktopClients',
            'exchangeActiveSync',
            'other'
        ],
        applications: {
            includeApplications: [
                'All'
            ],
            excludeApplications: [
                '499b84ac-1321-427f-aa17-267ca6975798',
                '00000007-0000-0000-c000-000000000000',
                'de8bc8b5-d9f9-48b1-a8ad-b748da725064',
                '00000012-0000-0000-c000-000000000000',
                '797f4846-ba00-4fd7-ba43-dac1f8f63013',
                '05a65629-4c1b-48c1-a78b-804c4abdd4af',
                '7df0a125-d3be-4c96-aa54-591f83ff541c'
            ],
            includeUserActions: []
        },
        users: {
            includeUsers: [
                'a702a13d-a437-4a07-8a7e-8c052de62dfd'
            ],
            excludeUsers: [
                '124c5b6a-ffa5-483a-9b88-04c3fce5574a',
                'GuestsOrExternalUsers'
            ],
            includeGroups: [],
            excludeGroups: [],
            includeRoles: [
                '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3',
                'cf1c38e5-3621-4004-a7cb-879624dced7c',
                'c4e39bd9-1100-46d3-8c65-fb160da0071f'
            ],
            excludeRoles: [
                'b0f54661-2d74-4c50-afa3-1ec803f12efe'
            ]
        },
        platforms: {
            includePlatforms: [
                'all'
            ],
            excludePlatforms: [
                'iOS',
                'windowsPhone'
            ]
        },
        locations: {
            includeLocations: [
                'AllTrusted'
            ],
            excludeLocations: [
                '00000000-0000-0000-0000-000000000000',
                'd2136c9c-b049-47ae-b9cf-316e04ef7198'
            ]
        }
    },
    grantControls: {
        operator: 'OR',
        builtInControls: [
            'mfa',
            'compliantDevice',
            'domainJoinedDevice',
            'approvedApplication',
            'compliantApplication'
        ],
        customAuthenticationFactors: [],
        termsOfUse: [
            'ce580154-086a-40fd-91df-8a60abac81a0',
            '7f29d675-caff-43e1-8a53-1b8516ed2075'
        ]
    },
    sessionControls: {
        applicationEnforcedRestrictions: null,
        persistentBrowser: null,
        cloudAppSecurity: {
            cloudAppSecurityType: 'blockDownloads',
            isEnabled: true
        },
        signInFrequency: {
            value: 4,
            type: 'hours',
            isEnabled: true
        }
    }
};

await client.api('/identity/conditionalAccess/policies')
	.post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicy;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicyState;
use Microsoft\Graph\Generated\Models\ConditionalAccessConditionSet;
use Microsoft\Graph\Generated\Models\RiskLevel;
use Microsoft\Graph\Generated\Models\ConditionalAccessClientApp;
use Microsoft\Graph\Generated\Models\ConditionalAccessApplications;
use Microsoft\Graph\Generated\Models\ConditionalAccessUsers;
use Microsoft\Graph\Generated\Models\ConditionalAccessPlatforms;
use Microsoft\Graph\Generated\Models\ConditionalAccessDevicePlatform;
use Microsoft\Graph\Generated\Models\ConditionalAccessLocations;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControls;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControl;
use Microsoft\Graph\Generated\Models\ConditionalAccessSessionControls;
use Microsoft\Graph\Generated\Models\CloudAppSecuritySessionControl;
use Microsoft\Graph\Generated\Models\CloudAppSecuritySessionControlType;
use Microsoft\Graph\Generated\Models\SignInFrequencySessionControl;
use Microsoft\Graph\Generated\Models\SigninFrequencyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConditionalAccessPolicy();
$requestBody->setDisplayName('Demo app for documentation');
$requestBody->setState(new ConditionalAccessPolicyState('disabled'));
$conditions = new ConditionalAccessConditionSet();
$conditions->setSignInRiskLevels([new RiskLevel('high'),new RiskLevel('medium'),	]);
$conditions->setClientAppTypes([new ConditionalAccessClientApp('mobileAppsAndDesktopClients'),new ConditionalAccessClientApp('exchangeActiveSync'),new ConditionalAccessClientApp('other'),	]);
$conditionsApplications = new ConditionalAccessApplications();
$conditionsApplications->setIncludeApplications(['All', 	]);
$conditionsApplications->setExcludeApplications(['499b84ac-1321-427f-aa17-267ca6975798', '00000007-0000-0000-c000-000000000000', 'de8bc8b5-d9f9-48b1-a8ad-b748da725064', '00000012-0000-0000-c000-000000000000', '797f4846-ba00-4fd7-ba43-dac1f8f63013', '05a65629-4c1b-48c1-a78b-804c4abdd4af', '7df0a125-d3be-4c96-aa54-591f83ff541c', 	]);
$conditionsApplications->setIncludeUserActions([	]);
$conditions->setApplications($conditionsApplications);
$conditionsUsers = new ConditionalAccessUsers();
$conditionsUsers->setIncludeUsers(['a702a13d-a437-4a07-8a7e-8c052de62dfd', 	]);
$conditionsUsers->setExcludeUsers(['124c5b6a-ffa5-483a-9b88-04c3fce5574a', 'GuestsOrExternalUsers', 	]);
$conditionsUsers->setIncludeGroups([	]);
$conditionsUsers->setExcludeGroups([	]);
$conditionsUsers->setIncludeRoles(['9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3', 'cf1c38e5-3621-4004-a7cb-879624dced7c', 'c4e39bd9-1100-46d3-8c65-fb160da0071f', 	]);
$conditionsUsers->setExcludeRoles(['b0f54661-2d74-4c50-afa3-1ec803f12efe', 	]);
$conditions->setUsers($conditionsUsers);
$conditionsPlatforms = new ConditionalAccessPlatforms();
$conditionsPlatforms->setIncludePlatforms([new ConditionalAccessDevicePlatform('all'),	]);
$conditionsPlatforms->setExcludePlatforms([new ConditionalAccessDevicePlatform('iOS'),new ConditionalAccessDevicePlatform('windowsPhone'),	]);
$conditions->setPlatforms($conditionsPlatforms);
$conditionsLocations = new ConditionalAccessLocations();
$conditionsLocations->setIncludeLocations(['AllTrusted', 	]);
$conditionsLocations->setExcludeLocations(['00000000-0000-0000-0000-000000000000', 'd2136c9c-b049-47ae-b9cf-316e04ef7198', 	]);
$conditions->setLocations($conditionsLocations);
$requestBody->setConditions($conditions);
$grantControls = new ConditionalAccessGrantControls();
$grantControls->setOperator('OR');
$grantControls->setBuiltInControls([new ConditionalAccessGrantControl('mfa'),new ConditionalAccessGrantControl('compliantDevice'),new ConditionalAccessGrantControl('domainJoinedDevice'),new ConditionalAccessGrantControl('approvedApplication'),new ConditionalAccessGrantControl('compliantApplication'),	]);
$grantControls->setCustomAuthenticationFactors([	]);
$grantControls->setTermsOfUse(['ce580154-086a-40fd-91df-8a60abac81a0', '7f29d675-caff-43e1-8a53-1b8516ed2075', 	]);
$requestBody->setGrantControls($grantControls);
$sessionControls = new ConditionalAccessSessionControls();
$sessionControls->setApplicationEnforcedRestrictions(null);
$sessionControls->setPersistentBrowser(null);
$sessionControlsCloudAppSecurity = new CloudAppSecuritySessionControl();
$sessionControlsCloudAppSecurity->setCloudAppSecurityType(new CloudAppSecuritySessionControlType('blockDownloads'));
$sessionControlsCloudAppSecurity->setIsEnabled(true);
$sessionControls->setCloudAppSecurity($sessionControlsCloudAppSecurity);
$sessionControlsSignInFrequency = new SignInFrequencySessionControl();
$sessionControlsSignInFrequency->setValue(4);
$sessionControlsSignInFrequency->setType(new SigninFrequencyType('hours'));
$sessionControlsSignInFrequency->setIsEnabled(true);
$sessionControls->setSignInFrequency($sessionControlsSignInFrequency);
$requestBody->setSessionControls($sessionControls);

$result = $graphServiceClient->identity()->conditionalAccess()->policies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	displayName = "Demo app for documentation"
	state = "disabled"
	conditions = @{
		signInRiskLevels = @(
		"high"
	"medium"
)
clientAppTypes = @(
"mobileAppsAndDesktopClients"
"exchangeActiveSync"
"other"
)
applications = @{
includeApplications = @(
"All"
)
excludeApplications = @(
"499b84ac-1321-427f-aa17-267ca6975798"
"00000007-0000-0000-c000-000000000000"
"de8bc8b5-d9f9-48b1-a8ad-b748da725064"
"00000012-0000-0000-c000-000000000000"
"797f4846-ba00-4fd7-ba43-dac1f8f63013"
"05a65629-4c1b-48c1-a78b-804c4abdd4af"
"7df0a125-d3be-4c96-aa54-591f83ff541c"
)
includeUserActions = @(
)
}
users = @{
includeUsers = @(
"a702a13d-a437-4a07-8a7e-8c052de62dfd"
)
excludeUsers = @(
"124c5b6a-ffa5-483a-9b88-04c3fce5574a"
"GuestsOrExternalUsers"
)
includeGroups = @(
)
excludeGroups = @(
)
includeRoles = @(
"9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3"
"cf1c38e5-3621-4004-a7cb-879624dced7c"
"c4e39bd9-1100-46d3-8c65-fb160da0071f"
)
excludeRoles = @(
"b0f54661-2d74-4c50-afa3-1ec803f12efe"
)
}
platforms = @{
includePlatforms = @(
"all"
)
excludePlatforms = @(
"iOS"
"windowsPhone"
)
}
locations = @{
includeLocations = @(
"AllTrusted"
)
excludeLocations = @(
"00000000-0000-0000-0000-000000000000"
"d2136c9c-b049-47ae-b9cf-316e04ef7198"
)
}
}
grantControls = @{
operator = "OR"
builtInControls = @(
"mfa"
"compliantDevice"
"domainJoinedDevice"
"approvedApplication"
"compliantApplication"
)
customAuthenticationFactors = @(
)
termsOfUse = @(
"ce580154-086a-40fd-91df-8a60abac81a0"
"7f29d675-caff-43e1-8a53-1b8516ed2075"
)
}
sessionControls = @{
applicationEnforcedRestrictions = $null
persistentBrowser = $null
cloudAppSecurity = @{
cloudAppSecurityType = "blockDownloads"
isEnabled = $true
}
signInFrequency = @{
value = 4
type = "hours"
isEnabled = $true
}
}
}

New-MgIdentityConditionalAccessPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conditional_access_policy import ConditionalAccessPolicy
from msgraph.generated.models.conditional_access_policy_state import ConditionalAccessPolicyState
from msgraph.generated.models.conditional_access_condition_set import ConditionalAccessConditionSet
from msgraph.generated.models.risk_level import RiskLevel
from msgraph.generated.models.conditional_access_client_app import ConditionalAccessClientApp
from msgraph.generated.models.conditional_access_applications import ConditionalAccessApplications
from msgraph.generated.models.conditional_access_users import ConditionalAccessUsers
from msgraph.generated.models.conditional_access_platforms import ConditionalAccessPlatforms
from msgraph.generated.models.conditional_access_device_platform import ConditionalAccessDevicePlatform
from msgraph.generated.models.conditional_access_locations import ConditionalAccessLocations
from msgraph.generated.models.conditional_access_grant_controls import ConditionalAccessGrantControls
from msgraph.generated.models.conditional_access_grant_control import ConditionalAccessGrantControl
from msgraph.generated.models.conditional_access_session_controls import ConditionalAccessSessionControls
from msgraph.generated.models.cloud_app_security_session_control import CloudAppSecuritySessionControl
from msgraph.generated.models.cloud_app_security_session_control_type import CloudAppSecuritySessionControlType
from msgraph.generated.models.sign_in_frequency_session_control import SignInFrequencySessionControl
from msgraph.generated.models.signin_frequency_type import SigninFrequencyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConditionalAccessPolicy(
	display_name = "Demo app for documentation",
	state = ConditionalAccessPolicyState.Disabled,
	conditions = ConditionalAccessConditionSet(
		sign_in_risk_levels = [
			RiskLevel.High,
			RiskLevel.Medium,
		],
		client_app_types = [
			ConditionalAccessClientApp.MobileAppsAndDesktopClients,
			ConditionalAccessClientApp.ExchangeActiveSync,
			ConditionalAccessClientApp.Other,
		],
		applications = ConditionalAccessApplications(
			include_applications = [
				"All",
			],
			exclude_applications = [
				"499b84ac-1321-427f-aa17-267ca6975798",
				"00000007-0000-0000-c000-000000000000",
				"de8bc8b5-d9f9-48b1-a8ad-b748da725064",
				"00000012-0000-0000-c000-000000000000",
				"797f4846-ba00-4fd7-ba43-dac1f8f63013",
				"05a65629-4c1b-48c1-a78b-804c4abdd4af",
				"7df0a125-d3be-4c96-aa54-591f83ff541c",
			],
			include_user_actions = [
			],
		),
		users = ConditionalAccessUsers(
			include_users = [
				"a702a13d-a437-4a07-8a7e-8c052de62dfd",
			],
			exclude_users = [
				"124c5b6a-ffa5-483a-9b88-04c3fce5574a",
				"GuestsOrExternalUsers",
			],
			include_groups = [
			],
			exclude_groups = [
			],
			include_roles = [
				"9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
				"cf1c38e5-3621-4004-a7cb-879624dced7c",
				"c4e39bd9-1100-46d3-8c65-fb160da0071f",
			],
			exclude_roles = [
				"b0f54661-2d74-4c50-afa3-1ec803f12efe",
			],
		),
		platforms = ConditionalAccessPlatforms(
			include_platforms = [
				ConditionalAccessDevicePlatform.All,
			],
			exclude_platforms = [
				ConditionalAccessDevicePlatform.IOS,
				ConditionalAccessDevicePlatform.WindowsPhone,
			],
		),
		locations = ConditionalAccessLocations(
			include_locations = [
				"AllTrusted",
			],
			exclude_locations = [
				"00000000-0000-0000-0000-000000000000",
				"d2136c9c-b049-47ae-b9cf-316e04ef7198",
			],
		),
	),
	grant_controls = ConditionalAccessGrantControls(
		operator = "OR",
		built_in_controls = [
			ConditionalAccessGrantControl.Mfa,
			ConditionalAccessGrantControl.CompliantDevice,
			ConditionalAccessGrantControl.DomainJoinedDevice,
			ConditionalAccessGrantControl.ApprovedApplication,
			ConditionalAccessGrantControl.CompliantApplication,
		],
		custom_authentication_factors = [
		],
		terms_of_use = [
			"ce580154-086a-40fd-91df-8a60abac81a0",
			"7f29d675-caff-43e1-8a53-1b8516ed2075",
		],
	),
	session_controls = ConditionalAccessSessionControls(
		application_enforced_restrictions = None,
		persistent_browser = None,
		cloud_app_security = CloudAppSecuritySessionControl(
			cloud_app_security_type = CloudAppSecuritySessionControlType.BlockDownloads,
			is_enabled = True,
		),
		sign_in_frequency = SignInFrequencySessionControl(
			value = 4,
			type = SigninFrequencyType.Hours,
			is_enabled = True,
		),
	),
)

result = await graph_client.identity.conditional_access.policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#conditionalAccess/policies/$entity",
    "id": "6b5e999b-0ba8-4186-a106-e0296c1c4358",
    "displayName": "Demo app for documentation",
    "createdDateTime": "2019-09-26T23:12:16.0792706Z",
    "modifiedDateTime": null,
    "state": "disabled",
    "conditions": {
        "signInRiskLevels": [
            "high",
            "medium"
        ],
        "clientAppTypes": [
            "mobileAppsAndDesktopClients",
            "exchangeActiveSync",
            "other"
        ],
        "applications": {
            "includeApplications": [
                "All"
            ],
            "excludeApplications": [
                "499b84ac-1321-427f-aa17-267ca6975798",
                "00000007-0000-0000-c000-000000000000",
                "de8bc8b5-d9f9-48b1-a8ad-b748da725064",
                "00000012-0000-0000-c000-000000000000",
                "797f4846-ba00-4fd7-ba43-dac1f8f63013",
                "05a65629-4c1b-48c1-a78b-804c4abdd4af",
                "7df0a125-d3be-4c96-aa54-591f83ff541c"
            ],
            "includeUserActions": []
        },
        "users": {
            "includeUsers": [
                "a702a13d-a437-4a07-8a7e-8c052de62dfd"
            ],
            "excludeUsers": [
                "124c5b6a-ffa5-483a-9b88-04c3fce5574a",
                "GuestsOrExternalUsers"
            ],
            "includeGroups": [],
            "excludeGroups": [],
            "includeRoles": [
                "9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
                "cf1c38e5-3621-4004-a7cb-879624dced7c",
                "c4e39bd9-1100-46d3-8c65-fb160da0071f"
            ],
            "excludeRoles": [
                "b0f54661-2d74-4c50-afa3-1ec803f12efe"
            ]
        },
        "platforms": {
            "includePlatforms": [
                "all"
            ],
            "excludePlatforms": [
                "iOS",
                "windowsPhone"
            ]
        },
        "locations": {
            "includeLocations": [
                "AllTrusted"
            ],
            "excludeLocations": [
                "00000000-0000-0000-0000-000000000000",
                "d2136c9c-b049-47ae-b9cf-316e04ef7198"
            ]
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "mfa",
            "compliantDevice",
            "domainJoinedDevice",
            "approvedApplication",
            "compliantApplication"
        ],
        "customAuthenticationFactors": [],
        "termsOfUse": [
            "ce580154-086a-40fd-91df-8a60abac81a0",
            "7f29d675-caff-43e1-8a53-1b8516ed2075"
        ]
    },
    "sessionControls": {
        "applicationEnforcedRestrictions": null,
        "persistentBrowser": null,
        "cloudAppSecurity": {
            "cloudAppSecurityType": "blockDownloads",
            "isEnabled": true
        },
        "signInFrequency": {
            "value": 4,
            "type": "hours",
            "isEnabled": true
        }
    }
}
```

### Example 4: Require MFA to Exchange Online from noncompliant devices

#### Request

The following example shows a request to require MFA to Exchange Online from noncompliant devices.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identity/conditionalAccess/policies
Content-type: application/json

{
    "displayName": "Require MFA to EXO from non-compliant devices.",
    "state": "enabled",
    "conditions": {
        "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ]
        },
        "users": {
            "includeGroups": ["ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"]
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "mfa"
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConditionalAccessPolicy
{
	DisplayName = "Require MFA to EXO from non-compliant devices.",
	State = ConditionalAccessPolicyState.Enabled,
	Conditions = new ConditionalAccessConditionSet
	{
		Applications = new ConditionalAccessApplications
		{
			IncludeApplications = new List<string>
			{
				"00000002-0000-0ff1-ce00-000000000000",
			},
		},
		Users = new ConditionalAccessUsers
		{
			IncludeGroups = new List<string>
			{
				"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
			},
		},
	},
	GrantControls = new ConditionalAccessGrantControls
	{
		Operator = "OR",
		BuiltInControls = new List<ConditionalAccessGrantControl?>
		{
			ConditionalAccessGrantControl.Mfa,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.ConditionalAccess.Policies.PostAsync(requestBody);
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

requestBody := graphmodels.NewConditionalAccessPolicy()
displayName := "Require MFA to EXO from non-compliant devices."
requestBody.SetDisplayName(&displayName) 
state := graphmodels.ENABLED_CONDITIONALACCESSPOLICYSTATE 
requestBody.SetState(&state) 
conditions := graphmodels.NewConditionalAccessConditionSet()
applications := graphmodels.NewConditionalAccessApplications()
includeApplications := []string {
	"00000002-0000-0ff1-ce00-000000000000",
}
applications.SetIncludeApplications(includeApplications)
conditions.SetApplications(applications)
users := graphmodels.NewConditionalAccessUsers()
includeGroups := []string {
	"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
}
users.SetIncludeGroups(includeGroups)
conditions.SetUsers(users)
requestBody.SetConditions(conditions)
grantControls := graphmodels.NewConditionalAccessGrantControls()
operator := "OR"
grantControls.SetOperator(&operator) 
builtInControls := []graphmodels.ConditionalAccessGrantControlable {
	conditionalAccessGrantControl := graphmodels.MFA_CONDITIONALACCESSGRANTCONTROL 
	grantControls.SetConditionalAccessGrantControl(&conditionalAccessGrantControl)
}
grantControls.SetBuiltInControls(builtInControls)
requestBody.SetGrantControls(grantControls)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policies, err := graphClient.Identity().ConditionalAccess().Policies().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConditionalAccessPolicy conditionalAccessPolicy = new ConditionalAccessPolicy();
conditionalAccessPolicy.setDisplayName("Require MFA to EXO from non-compliant devices.");
conditionalAccessPolicy.setState(ConditionalAccessPolicyState.Enabled);
ConditionalAccessConditionSet conditions = new ConditionalAccessConditionSet();
ConditionalAccessApplications applications = new ConditionalAccessApplications();
LinkedList<String> includeApplications = new LinkedList<String>();
includeApplications.add("00000002-0000-0ff1-ce00-000000000000");
applications.setIncludeApplications(includeApplications);
conditions.setApplications(applications);
ConditionalAccessUsers users = new ConditionalAccessUsers();
LinkedList<String> includeGroups = new LinkedList<String>();
includeGroups.add("ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba");
users.setIncludeGroups(includeGroups);
conditions.setUsers(users);
conditionalAccessPolicy.setConditions(conditions);
ConditionalAccessGrantControls grantControls = new ConditionalAccessGrantControls();
grantControls.setOperator("OR");
LinkedList<ConditionalAccessGrantControl> builtInControls = new LinkedList<ConditionalAccessGrantControl>();
builtInControls.add(ConditionalAccessGrantControl.Mfa);
grantControls.setBuiltInControls(builtInControls);
conditionalAccessPolicy.setGrantControls(grantControls);
ConditionalAccessPolicy result = graphClient.identity().conditionalAccess().policies().post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conditionalAccessPolicy = {
    displayName: 'Require MFA to EXO from non-compliant devices.',
    state: 'enabled',
    conditions: {
        applications: {
            includeApplications: [
                '00000002-0000-0ff1-ce00-000000000000'
            ]
        },
        users: {
            includeGroups: ['ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba']
        }
    },
    grantControls: {
        operator: 'OR',
        builtInControls: [
            'mfa'
        ]
    }
};

await client.api('/identity/conditionalAccess/policies')
	.post(conditionalAccessPolicy);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicy;
use Microsoft\Graph\Generated\Models\ConditionalAccessPolicyState;
use Microsoft\Graph\Generated\Models\ConditionalAccessConditionSet;
use Microsoft\Graph\Generated\Models\ConditionalAccessApplications;
use Microsoft\Graph\Generated\Models\ConditionalAccessUsers;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControls;
use Microsoft\Graph\Generated\Models\ConditionalAccessGrantControl;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConditionalAccessPolicy();
$requestBody->setDisplayName('Require MFA to EXO from non-compliant devices.');
$requestBody->setState(new ConditionalAccessPolicyState('enabled'));
$conditions = new ConditionalAccessConditionSet();
$conditionsApplications = new ConditionalAccessApplications();
$conditionsApplications->setIncludeApplications(['00000002-0000-0ff1-ce00-000000000000', 	]);
$conditions->setApplications($conditionsApplications);
$conditionsUsers = new ConditionalAccessUsers();
$conditionsUsers->setIncludeGroups(['ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba', 	]);
$conditions->setUsers($conditionsUsers);
$requestBody->setConditions($conditions);
$grantControls = new ConditionalAccessGrantControls();
$grantControls->setOperator('OR');
$grantControls->setBuiltInControls([new ConditionalAccessGrantControl('mfa'),	]);
$requestBody->setGrantControls($grantControls);

$result = $graphServiceClient->identity()->conditionalAccess()->policies()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	displayName = "Require MFA to EXO from non-compliant devices."
	state = "enabled"
	conditions = @{
		applications = @{
			includeApplications = @(
			"00000002-0000-0ff1-ce00-000000000000"
		)
	}
	users = @{
		includeGroups = @(
		"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"
	)
}
}
grantControls = @{
operator = "OR"
builtInControls = @(
"mfa"
)
}
}

New-MgIdentityConditionalAccessPolicy -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conditional_access_policy import ConditionalAccessPolicy
from msgraph.generated.models.conditional_access_policy_state import ConditionalAccessPolicyState
from msgraph.generated.models.conditional_access_condition_set import ConditionalAccessConditionSet
from msgraph.generated.models.conditional_access_applications import ConditionalAccessApplications
from msgraph.generated.models.conditional_access_users import ConditionalAccessUsers
from msgraph.generated.models.conditional_access_grant_controls import ConditionalAccessGrantControls
from msgraph.generated.models.conditional_access_grant_control import ConditionalAccessGrantControl
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConditionalAccessPolicy(
	display_name = "Require MFA to EXO from non-compliant devices.",
	state = ConditionalAccessPolicyState.Enabled,
	conditions = ConditionalAccessConditionSet(
		applications = ConditionalAccessApplications(
			include_applications = [
				"00000002-0000-0ff1-ce00-000000000000",
			],
		),
		users = ConditionalAccessUsers(
			include_groups = [
				"ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba",
			],
		),
	),
	grant_controls = ConditionalAccessGrantControls(
		operator = "OR",
		built_in_controls = [
			ConditionalAccessGrantControl.Mfa,
		],
	),
)

result = await graph_client.identity.conditional_access.policies.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#conditionalAccess/policies/$entity",
     "id": "b3f1298e-8e93-49af-bdbf-94cf7d453ca3",
    "displayName": "Require MFA to EXO from non-compliant devices.",
    "createdDateTime": "2020-04-01T00:55:12.9571747Z",
    "modifiedDateTime": null,
    "state": "enabled",
    "sessionControls": null,
    "conditions": {
        "userRiskLevels": [],
        "signInRiskLevels": [],
        "clientAppTypes": [
            "all"
        ],
        "platforms": null,
        "locations": null,
        "times": null,
        "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ],
            "excludeApplications": [],
            "includeUserActions": [],
            "includeProtectionLevels": []
        },
        "users": {
            "includeUsers": [],
            "excludeUsers": [],
            "includeGroups": [
                "ba8e7ded-8b0f-4836-ba06-8ff1ecc5c8ba"
            ],
            "excludeGroups": [],
            "includeRoles": [],
            "excludeRoles": []
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
            "mfa"
        ],
        "customAuthenticationFactors": [],
        "termsOfUse": []
    }
}
```
