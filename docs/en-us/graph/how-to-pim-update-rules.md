<!-- Source: https://learn.microsoft.com/en-us/graph/how-to-pim-update-rules -->
<!-- Sitemap-Last-Modified: 2025-08-29 -->

# Update rules in PIM by using Microsoft Graph

This article provides examples for using Microsoft Graph APIs to update different rules that are assigned to Microsoft Entra roles or groups through Privileged Identity Management \(PIM\). To understand the structure of rules in PIM, see [Working with rules in PIM using Microsoft Graph](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview).

When updating the rules, you must include the `@odata.type` for the derived type in the request body. For example, to update an activation rule with the ID `Enablement_EndUser_Assignment`, you must include `"@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule"`.

If successful, all requests return `204 No Content` response codes.

Note

PIM for groups APIs are currently available on the `beta` endpoint only.

## Prerequisites

- Understand [PIM for Microsoft Entra roles APIs](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview) or [PIM for groups APIs](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagement-for-groups-api-overview).

  - Understand the [mapping of the rules to the different categories of rules in PIM](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview).

- In this article, you call the APIs in a [delegated scenario](https://learn.microsoft.com/en-us/graph/auth-v2-user).

  - Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) with administrative privileges to manage PIM rules. The *Privileged Role Administrator* role is the least privileged role sufficient to manage PIM rules.
  - Depending on operations you want to carry out, grant yourself one of the following delegated permissions:

    - To manage the rules for Microsoft Entra roles: *RoleManagementPolicy.ReadWrite.Directory*
    - To manage the rules for groups: *RoleManagementPolicy.ReadWrite.AzureADGroup*

## How to find the settings for a Microsoft Entra role

Consider a Microsoft Entra role like *Application Administrator*. The permanent immutable template ID for the role in Microsoft Entra ID is `9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3`.

To use the PIM APIs to discover the settings for the *Application Administrator* role, query the role management policy that Microsoft Entra ID assigned to the role by using the [unifiedRoleManagementPolicyAssignment resource type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment) as follows:

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/policies/roleManagementPolicyAssignments?$filter=scopeId eq '/' and scopeType eq 'DirectoryRole' and roleDefinitionId eq '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicyAssignments.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "scopeId eq '/' and scopeType eq 'DirectoryRole' and roleDefinitionId eq '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphpolicies "github.com/microsoftgraph/msgraph-sdk-go/policies"
	  //other-imports
)


requestFilter := "scopeId eq '/' and scopeType eq 'DirectoryRole' and roleDefinitionId eq '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3'"

requestParameters := &graphpolicies.PoliciesRoleManagementPolicyAssignmentsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphpolicies.PoliciesRoleManagementPolicyAssignmentsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
roleManagementPolicyAssignments, err := graphClient.Policies().RoleManagementPolicyAssignments().Get(context.Background(), configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyAssignmentCollectionResponse result = graphClient.policies().roleManagementPolicyAssignments().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "scopeId eq '/' and scopeType eq 'DirectoryRole' and roleDefinitionId eq '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3'";
});
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roleManagementPolicyAssignments = await client.api('/policies/roleManagementPolicyAssignments')
	.filter('scopeId eq \'/\' and scopeType eq \'DirectoryRole\' and roleDefinitionId eq \'9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3\'')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Policies\RoleManagementPolicyAssignments\RoleManagementPolicyAssignmentsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new RoleManagementPolicyAssignmentsRequestBuilderGetRequestConfiguration();
$queryParameters = RoleManagementPolicyAssignmentsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "scopeId eq '/' and scopeType eq 'DirectoryRole' and roleDefinitionId eq '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->policies()->roleManagementPolicyAssignments()->get($requestConfiguration)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

Get-MgPolicyRoleManagementPolicyAssignment -Filter "scopeId eq '/' and scopeType eq 'DirectoryRole' and roleDefinitionId eq '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3'" 
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.policies.role_management_policy_assignments.role_management_policy_assignments_request_builder import RoleManagementPolicyAssignmentsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = RoleManagementPolicyAssignmentsRequestBuilder.RoleManagementPolicyAssignmentsRequestBuilderGetQueryParameters(
		filter = "scopeId eq '/' and scopeType eq 'DirectoryRole' and roleDefinitionId eq '9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.policies.role_management_policy_assignments.get(request_configuration = request_configuration)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The response returns an object similar to the following response that contains a policy assignment ID and a policy ID.

```http
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicyAssignments",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET policies/roleManagementPolicyAssignments?$select=policyId,roleDefinitionId",
    "value": [
        {
            "id": "DirectoryRole_714a5b9b-97d1-45af-937f-6a998297bc52_0653a6f0-2dca-4655-88fe-b43a086fb66a_9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3",
            "policyId": "DirectoryRole_714a5b9b-97d1-45af-937f-6a998297bc52_0653a6f0-2dca-4655-88fe-b43a086fb66a",
            "scopeId": "/",
            "scopeType": "DirectoryRole",
            "roleDefinitionId": "9b895d92-2cd3-44c7-9d02-a6ac2d5ea5c3"
        }
    ]
}
```

Use the **policyId** object to query and manage the corresponding rules for the role.

## Example 1: Update the activation maximum duration

- Category of rule: Activation rule
- Microsoft Graph [rule type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule): [unifiedRoleManagementPolicyExpirationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyexpirationrule)
- Microsoft Graph rule ID: `Expiration_EndUser_Assignment`

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Expiration_EndUser_Assignment
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
    "id": "Expiration_EndUser_Assignment",
    "isExpirationRequired": true,
    "maximumDuration": "PT1H45M",
    "target": {
        "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
        "caller": "EndUser",
        "operations": [
            "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicyExpirationRule
{
	OdataType = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
	Id = "Expiration_EndUser_Assignment",
	IsExpirationRequired = true,
	MaximumDuration = TimeSpan.Parse("PT1H45M"),
	Target = new UnifiedRoleManagementPolicyRuleTarget
	{
		OdataType = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		Caller = "EndUser",
		Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
		{
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		},
		Level = "Assignment",
		InheritableSettings = new List<string>
		{
		},
		EnforcedSettings = new List<string>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].Rules["{unifiedRoleManagementPolicyRule-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleManagementPolicyRule()
id := "Expiration_EndUser_Assignment"
requestBody.SetId(&id) 
isExpirationRequired := true
requestBody.SetIsExpirationRequired(&isExpirationRequired) 
maximumDuration , err := abstractions.ParseISODuration("PT1H45M")
requestBody.SetMaximumDuration(&maximumDuration) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "EndUser"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
requestBody.SetTarget(target)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rules, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Rules().ByUnifiedRoleManagementPolicyRuleId("unifiedRoleManagementPolicyRule-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyExpirationRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyExpirationRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyExpirationRule");
unifiedRoleManagementPolicyRule.setId("Expiration_EndUser_Assignment");
unifiedRoleManagementPolicyRule.setIsExpirationRequired(true);
PeriodAndDuration maximumDuration = PeriodAndDuration.ofDuration(Duration.parse("PT1H45M"));
unifiedRoleManagementPolicyRule.setMaximumDuration(maximumDuration);
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setOdataType("microsoft.graph.unifiedRoleManagementPolicyRuleTarget");
target.setCaller("EndUser");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Assignment");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
UnifiedRoleManagementPolicyRule result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").rules().byUnifiedRoleManagementPolicyRuleId("{unifiedRoleManagementPolicyRule-id}").patch(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicyRule = {
    '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyExpirationRule',
    id: 'Expiration_EndUser_Assignment',
    isExpirationRequired: true,
    maximumDuration: 'PT1H45M',
    target: {
        '@odata.type': 'microsoft.graph.unifiedRoleManagementPolicyRuleTarget',
        caller: 'EndUser',
        operations: [
            'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
    }
};

await client.api('/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Expiration_EndUser_Assignment')
	.update(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyExpirationRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicyExpirationRule();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyExpirationRule');
$requestBody->setId('Expiration_EndUser_Assignment');
$requestBody->setIsExpirationRequired(true);
$requestBody->setMaximumDuration(new \DateInterval('PT1H45M'));
$target = new UnifiedRoleManagementPolicyRuleTarget();
$target->setOdataType('microsoft.graph.unifiedRoleManagementPolicyRuleTarget');
$target->setCaller('EndUser');
$target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$target->setLevel('Assignment');
$target->setInheritableSettings([	]);
$target->setEnforcedSettings([	]);
$requestBody->setTarget($target);

$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->rules()->byUnifiedRoleManagementPolicyRuleId('unifiedRoleManagementPolicyRule-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule"
	id = "Expiration_EndUser_Assignment"
	isExpirationRequired = $true
	maximumDuration = "PT1H45M"
	target = @{
		"@odata.type" = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
		caller = "EndUser"
		operations = @(
		"All"
	)
	level = "Assignment"
	inheritableSettings = @(
	)
	enforcedSettings = @(
	)
}
}

Update-MgPolicyRoleManagementPolicyRule -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -UnifiedRoleManagementPolicyRuleId $unifiedRoleManagementPolicyRuleId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy_expiration_rule import UnifiedRoleManagementPolicyExpirationRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicyExpirationRule(
	odata_type = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
	id = "Expiration_EndUser_Assignment",
	is_expiration_required = True,
	maximum_duration = "PT1H45M",
	target = UnifiedRoleManagementPolicyRuleTarget(
		odata_type = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		caller = "EndUser",
		operations = [
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		],
		level = "Assignment",
		inheritable_settings = [
		],
		enforced_settings = [
		],
	),
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').rules.by_unified_role_management_policy_rule_id('unifiedRoleManagementPolicyRule-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Example 2: Update the justification, MFA, and ticketing rules required on activation

- Category of rule: Activation rule
- Microsoft Graph [rule type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule): [unifiedRoleManagementPolicyEnablementRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyenablementrule)
- Microsoft Graph rule ID: `Enablement_EndUser_Assignment`

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Enablement_EndUser_Assignment
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
    "id": "Enablement_EndUser_Assignment",
    "enabledRules": [
        "Justification",
        "MultiFactorAuthentication",
        "Ticketing"
    ],
    "target": {
        "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
        "caller": "EndUser",
        "operations": [
            "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicyEnablementRule
{
	OdataType = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
	Id = "Enablement_EndUser_Assignment",
	EnabledRules = new List<string>
	{
		"Justification",
		"MultiFactorAuthentication",
		"Ticketing",
	},
	Target = new UnifiedRoleManagementPolicyRuleTarget
	{
		OdataType = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		Caller = "EndUser",
		Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
		{
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		},
		Level = "Assignment",
		InheritableSettings = new List<string>
		{
		},
		EnforcedSettings = new List<string>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].Rules["{unifiedRoleManagementPolicyRule-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleManagementPolicyRule()
id := "Enablement_EndUser_Assignment"
requestBody.SetId(&id) 
enabledRules := []string {
	"Justification",
	"MultiFactorAuthentication",
	"Ticketing",
}
requestBody.SetEnabledRules(enabledRules)
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "EndUser"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
requestBody.SetTarget(target)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rules, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Rules().ByUnifiedRoleManagementPolicyRuleId("unifiedRoleManagementPolicyRule-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyEnablementRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyEnablementRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyEnablementRule");
unifiedRoleManagementPolicyRule.setId("Enablement_EndUser_Assignment");
LinkedList<String> enabledRules = new LinkedList<String>();
enabledRules.add("Justification");
enabledRules.add("MultiFactorAuthentication");
enabledRules.add("Ticketing");
unifiedRoleManagementPolicyRule.setEnabledRules(enabledRules);
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setOdataType("microsoft.graph.unifiedRoleManagementPolicyRuleTarget");
target.setCaller("EndUser");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Assignment");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
UnifiedRoleManagementPolicyRule result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").rules().byUnifiedRoleManagementPolicyRuleId("{unifiedRoleManagementPolicyRule-id}").patch(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicyRule = {
    '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyEnablementRule',
    id: 'Enablement_EndUser_Assignment',
    enabledRules: [
        'Justification',
        'MultiFactorAuthentication',
        'Ticketing'
    ],
    target: {
        '@odata.type': 'microsoft.graph.unifiedRoleManagementPolicyRuleTarget',
        caller: 'EndUser',
        operations: [
            'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
    }
};

await client.api('/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Enablement_EndUser_Assignment')
	.update(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyEnablementRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicyEnablementRule();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyEnablementRule');
$requestBody->setId('Enablement_EndUser_Assignment');
$requestBody->setEnabledRules(['Justification', 'MultiFactorAuthentication', 'Ticketing', 	]);
$target = new UnifiedRoleManagementPolicyRuleTarget();
$target->setOdataType('microsoft.graph.unifiedRoleManagementPolicyRuleTarget');
$target->setCaller('EndUser');
$target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$target->setLevel('Assignment');
$target->setInheritableSettings([	]);
$target->setEnforcedSettings([	]);
$requestBody->setTarget($target);

$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->rules()->byUnifiedRoleManagementPolicyRuleId('unifiedRoleManagementPolicyRule-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule"
	id = "Enablement_EndUser_Assignment"
	enabledRules = @(
	"Justification"
"MultiFactorAuthentication"
"Ticketing"
)
target = @{
"@odata.type" = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
caller = "EndUser"
operations = @(
"All"
)
level = "Assignment"
inheritableSettings = @(
)
enforcedSettings = @(
)
}
}

Update-MgPolicyRoleManagementPolicyRule -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -UnifiedRoleManagementPolicyRuleId $unifiedRoleManagementPolicyRuleId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy_enablement_rule import UnifiedRoleManagementPolicyEnablementRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicyEnablementRule(
	odata_type = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
	id = "Enablement_EndUser_Assignment",
	enabled_rules = [
		"Justification",
		"MultiFactorAuthentication",
		"Ticketing",
	],
	target = UnifiedRoleManagementPolicyRuleTarget(
		odata_type = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		caller = "EndUser",
		operations = [
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		],
		level = "Assignment",
		inheritable_settings = [
		],
		enforced_settings = [
		],
	),
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').rules.by_unified_role_management_policy_rule_id('unifiedRoleManagementPolicyRule-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Example 3: Require approval to activate

- Category of rule: Activation rule
- Microsoft Graph [rule type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule): [unifiedRoleManagementPolicyApprovalRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyapprovalrule)
- Microsoft Graph rule ID: `Approval_EndUser_Assignment`

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Approval_EndUser_Assignment
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
    "id": "Approval_EndUser_Assignment",
    "target": {
        "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
        "caller": "EndUser",
        "operations": [
            "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
    },
    "setting": {
        "@odata.type": "microsoft.graph.approvalSettings",
        "isApprovalRequired": true,
        "isApprovalRequiredForExtension": false,
        "isRequestorJustificationRequired": true,
        "approvalMode": "SingleStage",
        "approvalStages": [
            {
                "approvalStageTimeOutInDays": 1,
                "isApproverJustificationRequired": true,
                "escalationTimeInMinutes": 0,
                "primaryApprovers": [
                    {
                        "@odata.type": "#microsoft.graph.singleUser",
                        "userId": "10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6"
                    },
                    {
                        "@odata.type": "#microsoft.graph.groupMembers",
                        "groupId": "14f2746d-7d6f-4ac6-acd8-8cac318b041b"
                    }
                ],
                "isEscalationEnabled": false,
                "escalationApprovers": []
            }
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicyApprovalRule
{
	OdataType = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
	Id = "Approval_EndUser_Assignment",
	Target = new UnifiedRoleManagementPolicyRuleTarget
	{
		OdataType = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		Caller = "EndUser",
		Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
		{
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		},
		Level = "Assignment",
		InheritableSettings = new List<string>
		{
		},
		EnforcedSettings = new List<string>
		{
		},
	},
	Setting = new ApprovalSettings
	{
		OdataType = "microsoft.graph.approvalSettings",
		IsApprovalRequired = true,
		IsApprovalRequiredForExtension = false,
		IsRequestorJustificationRequired = true,
		ApprovalMode = "SingleStage",
		ApprovalStages = new List<UnifiedApprovalStage>
		{
			new UnifiedApprovalStage
			{
				ApprovalStageTimeOutInDays = 1,
				IsApproverJustificationRequired = true,
				EscalationTimeInMinutes = 0,
				PrimaryApprovers = new List<SubjectSet>
				{
					new SingleUser
					{
						OdataType = "#microsoft.graph.singleUser",
						UserId = "10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6",
					},
					new GroupMembers
					{
						OdataType = "#microsoft.graph.groupMembers",
						GroupId = "14f2746d-7d6f-4ac6-acd8-8cac318b041b",
					},
				},
				IsEscalationEnabled = false,
				EscalationApprovers = new List<SubjectSet>
				{
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].Rules["{unifiedRoleManagementPolicyRule-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleManagementPolicyRule()
id := "Approval_EndUser_Assignment"
requestBody.SetId(&id) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "EndUser"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
requestBody.SetTarget(target)
setting := graphmodels.NewApprovalSettings()
isApprovalRequired := true
setting.SetIsApprovalRequired(&isApprovalRequired) 
isApprovalRequiredForExtension := false
setting.SetIsApprovalRequiredForExtension(&isApprovalRequiredForExtension) 
isRequestorJustificationRequired := true
setting.SetIsRequestorJustificationRequired(&isRequestorJustificationRequired) 
approvalMode := "SingleStage"
setting.SetApprovalMode(&approvalMode) 


unifiedApprovalStage := graphmodels.NewUnifiedApprovalStage()
approvalStageTimeOutInDays := int32(1)
unifiedApprovalStage.SetApprovalStageTimeOutInDays(&approvalStageTimeOutInDays) 
isApproverJustificationRequired := true
unifiedApprovalStage.SetIsApproverJustificationRequired(&isApproverJustificationRequired) 
escalationTimeInMinutes := int32(0)
unifiedApprovalStage.SetEscalationTimeInMinutes(&escalationTimeInMinutes) 


subjectSet := graphmodels.NewSingleUser()
userId := "10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6"
subjectSet.SetUserId(&userId) 
subjectSet1 := graphmodels.NewGroupMembers()
groupId := "14f2746d-7d6f-4ac6-acd8-8cac318b041b"
subjectSet1.SetGroupId(&groupId) 

primaryApprovers := []graphmodels.SubjectSetable {
	subjectSet,
	subjectSet1,
}
unifiedApprovalStage.SetPrimaryApprovers(primaryApprovers)
isEscalationEnabled := false
unifiedApprovalStage.SetIsEscalationEnabled(&isEscalationEnabled) 
escalationApprovers := []graphmodels.SubjectSetable {

}
unifiedApprovalStage.SetEscalationApprovers(escalationApprovers)

approvalStages := []graphmodels.UnifiedApprovalStageable {
	unifiedApprovalStage,
}
setting.SetApprovalStages(approvalStages)
requestBody.SetSetting(setting)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rules, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Rules().ByUnifiedRoleManagementPolicyRuleId("unifiedRoleManagementPolicyRule-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyApprovalRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyApprovalRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyApprovalRule");
unifiedRoleManagementPolicyRule.setId("Approval_EndUser_Assignment");
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setOdataType("microsoft.graph.unifiedRoleManagementPolicyRuleTarget");
target.setCaller("EndUser");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Assignment");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
ApprovalSettings setting = new ApprovalSettings();
setting.setOdataType("microsoft.graph.approvalSettings");
setting.setIsApprovalRequired(true);
setting.setIsApprovalRequiredForExtension(false);
setting.setIsRequestorJustificationRequired(true);
setting.setApprovalMode("SingleStage");
LinkedList<UnifiedApprovalStage> approvalStages = new LinkedList<UnifiedApprovalStage>();
UnifiedApprovalStage unifiedApprovalStage = new UnifiedApprovalStage();
unifiedApprovalStage.setApprovalStageTimeOutInDays(1);
unifiedApprovalStage.setIsApproverJustificationRequired(true);
unifiedApprovalStage.setEscalationTimeInMinutes(0);
LinkedList<SubjectSet> primaryApprovers = new LinkedList<SubjectSet>();
SingleUser subjectSet = new SingleUser();
subjectSet.setOdataType("#microsoft.graph.singleUser");
subjectSet.setUserId("10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6");
primaryApprovers.add(subjectSet);
GroupMembers subjectSet1 = new GroupMembers();
subjectSet1.setOdataType("#microsoft.graph.groupMembers");
subjectSet1.setGroupId("14f2746d-7d6f-4ac6-acd8-8cac318b041b");
primaryApprovers.add(subjectSet1);
unifiedApprovalStage.setPrimaryApprovers(primaryApprovers);
unifiedApprovalStage.setIsEscalationEnabled(false);
LinkedList<SubjectSet> escalationApprovers = new LinkedList<SubjectSet>();
unifiedApprovalStage.setEscalationApprovers(escalationApprovers);
approvalStages.add(unifiedApprovalStage);
setting.setApprovalStages(approvalStages);
unifiedRoleManagementPolicyRule.setSetting(setting);
UnifiedRoleManagementPolicyRule result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").rules().byUnifiedRoleManagementPolicyRuleId("{unifiedRoleManagementPolicyRule-id}").patch(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicyRule = {
    '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyApprovalRule',
    id: 'Approval_EndUser_Assignment',
    target: {
        '@odata.type': 'microsoft.graph.unifiedRoleManagementPolicyRuleTarget',
        caller: 'EndUser',
        operations: [
            'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
    },
    setting: {
        '@odata.type': 'microsoft.graph.approvalSettings',
        isApprovalRequired: true,
        isApprovalRequiredForExtension: false,
        isRequestorJustificationRequired: true,
        approvalMode: 'SingleStage',
        approvalStages: [
            {
                approvalStageTimeOutInDays: 1,
                isApproverJustificationRequired: true,
                escalationTimeInMinutes: 0,
                primaryApprovers: [
                    {
                        '@odata.type': '#microsoft.graph.singleUser',
                        userId: '10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6'
                    },
                    {
                        '@odata.type': '#microsoft.graph.groupMembers',
                        groupId: '14f2746d-7d6f-4ac6-acd8-8cac318b041b'
                    }
                ],
                isEscalationEnabled: false,
                escalationApprovers: []
            }
        ]
    }
};

await client.api('/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Approval_EndUser_Assignment')
	.update(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyApprovalRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;
use Microsoft\Graph\Generated\Models\ApprovalSettings;
use Microsoft\Graph\Generated\Models\UnifiedApprovalStage;
use Microsoft\Graph\Generated\Models\SubjectSet;
use Microsoft\Graph\Generated\Models\SingleUser;
use Microsoft\Graph\Generated\Models\GroupMembers;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicyApprovalRule();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyApprovalRule');
$requestBody->setId('Approval_EndUser_Assignment');
$target = new UnifiedRoleManagementPolicyRuleTarget();
$target->setOdataType('microsoft.graph.unifiedRoleManagementPolicyRuleTarget');
$target->setCaller('EndUser');
$target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$target->setLevel('Assignment');
$target->setInheritableSettings([	]);
$target->setEnforcedSettings([	]);
$requestBody->setTarget($target);
$setting = new ApprovalSettings();
$setting->setOdataType('microsoft.graph.approvalSettings');
$setting->setIsApprovalRequired(true);
$setting->setIsApprovalRequiredForExtension(false);
$setting->setIsRequestorJustificationRequired(true);
$setting->setApprovalMode('SingleStage');
$approvalStagesUnifiedApprovalStage1 = new UnifiedApprovalStage();
$approvalStagesUnifiedApprovalStage1->setApprovalStageTimeOutInDays(1);
$approvalStagesUnifiedApprovalStage1->setIsApproverJustificationRequired(true);
$approvalStagesUnifiedApprovalStage1->setEscalationTimeInMinutes(0);
$primaryApproversSubjectSet1 = new SingleUser();
$primaryApproversSubjectSet1->setOdataType('#microsoft.graph.singleUser');
$primaryApproversSubjectSet1->setUserId('10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6');
$primaryApproversArray []= $primaryApproversSubjectSet1;
$primaryApproversSubjectSet2 = new GroupMembers();
$primaryApproversSubjectSet2->setOdataType('#microsoft.graph.groupMembers');
$primaryApproversSubjectSet2->setGroupId('14f2746d-7d6f-4ac6-acd8-8cac318b041b');
$primaryApproversArray []= $primaryApproversSubjectSet2;
$approvalStagesUnifiedApprovalStage1->setPrimaryApprovers($primaryApproversArray);

$approvalStagesUnifiedApprovalStage1->setIsEscalationEnabled(false);
$approvalStagesUnifiedApprovalStage1->setEscalationApprovers([]);
$approvalStagesArray []= $approvalStagesUnifiedApprovalStage1;
$setting->setApprovalStages($approvalStagesArray);

$requestBody->setSetting($setting);

$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->rules()->byUnifiedRoleManagementPolicyRuleId('unifiedRoleManagementPolicyRule-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule"
	id = "Approval_EndUser_Assignment"
	target = @{
		"@odata.type" = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
		caller = "EndUser"
		operations = @(
		"All"
	)
	level = "Assignment"
	inheritableSettings = @(
	)
	enforcedSettings = @(
	)
}
setting = @{
	"@odata.type" = "microsoft.graph.approvalSettings"
	isApprovalRequired = $true
	isApprovalRequiredForExtension = $false
	isRequestorJustificationRequired = $true
	approvalMode = "SingleStage"
	approvalStages = @(
		@{
			approvalStageTimeOutInDays = 
			isApproverJustificationRequired = $true
			escalationTimeInMinutes = 
			primaryApprovers = @(
				@{
					"@odata.type" = "#microsoft.graph.singleUser"
					userId = "10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6"
				}
				@{
					"@odata.type" = "#microsoft.graph.groupMembers"
					groupId = "14f2746d-7d6f-4ac6-acd8-8cac318b041b"
				}
			)
			isEscalationEnabled = $false
			escalationApprovers = @(
			)
		}
	)
}
}

Update-MgPolicyRoleManagementPolicyRule -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -UnifiedRoleManagementPolicyRuleId $unifiedRoleManagementPolicyRuleId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy_approval_rule import UnifiedRoleManagementPolicyApprovalRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
from msgraph.generated.models.approval_settings import ApprovalSettings
from msgraph.generated.models.unified_approval_stage import UnifiedApprovalStage
from msgraph.generated.models.subject_set import SubjectSet
from msgraph.generated.models.single_user import SingleUser
from msgraph.generated.models.group_members import GroupMembers
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicyApprovalRule(
	odata_type = "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule",
	id = "Approval_EndUser_Assignment",
	target = UnifiedRoleManagementPolicyRuleTarget(
		odata_type = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		caller = "EndUser",
		operations = [
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		],
		level = "Assignment",
		inheritable_settings = [
		],
		enforced_settings = [
		],
	),
	setting = ApprovalSettings(
		odata_type = "microsoft.graph.approvalSettings",
		is_approval_required = True,
		is_approval_required_for_extension = False,
		is_requestor_justification_required = True,
		approval_mode = "SingleStage",
		approval_stages = [
			UnifiedApprovalStage(
				approval_stage_time_out_in_days = 1,
				is_approver_justification_required = True,
				escalation_time_in_minutes = 0,
				primary_approvers = [
					SingleUser(
						odata_type = "#microsoft.graph.singleUser",
						user_id = "10a08e2e-3ea2-4ce0-80cb-d5fdd4b05ea6",
					),
					GroupMembers(
						odata_type = "#microsoft.graph.groupMembers",
						group_id = "14f2746d-7d6f-4ac6-acd8-8cac318b041b",
					),
				],
				is_escalation_enabled = False,
				escalation_approvers = [
				],
			),
		],
	),
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').rules.by_unified_role_management_policy_rule_id('unifiedRoleManagementPolicyRule-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Example 4: Set expiration of eligible assignment

- Category of rule: Activation rule
- Microsoft Graph [rule type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule): [unifiedRoleManagementPolicyExpirationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyexpirationrule)
- Microsoft Graph rule ID: `Expiration_Admin_Eligibility`

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Expiration_Admin_Eligibility
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
    "id": "Expiration_Admin_Eligibility",
    "isExpirationRequired": true,
    "maximumDuration": "P90D",
    "target": {
        "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
        "caller": "Admin",
        "operations": [
            "All"
        ],
        "level": "Eligibility",
        "inheritableSettings": [],
        "enforcedSettings": []
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicyExpirationRule
{
	OdataType = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
	Id = "Expiration_Admin_Eligibility",
	IsExpirationRequired = true,
	MaximumDuration = TimeSpan.Parse("P90D"),
	Target = new UnifiedRoleManagementPolicyRuleTarget
	{
		OdataType = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		Caller = "Admin",
		Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
		{
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		},
		Level = "Eligibility",
		InheritableSettings = new List<string>
		{
		},
		EnforcedSettings = new List<string>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].Rules["{unifiedRoleManagementPolicyRule-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleManagementPolicyRule()
id := "Expiration_Admin_Eligibility"
requestBody.SetId(&id) 
isExpirationRequired := true
requestBody.SetIsExpirationRequired(&isExpirationRequired) 
maximumDuration , err := abstractions.ParseISODuration("P90D")
requestBody.SetMaximumDuration(&maximumDuration) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Eligibility"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
requestBody.SetTarget(target)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rules, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Rules().ByUnifiedRoleManagementPolicyRuleId("unifiedRoleManagementPolicyRule-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyExpirationRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyExpirationRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyExpirationRule");
unifiedRoleManagementPolicyRule.setId("Expiration_Admin_Eligibility");
unifiedRoleManagementPolicyRule.setIsExpirationRequired(true);
PeriodAndDuration maximumDuration = PeriodAndDuration.ofDuration(Duration.parse("P90D"));
unifiedRoleManagementPolicyRule.setMaximumDuration(maximumDuration);
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setOdataType("microsoft.graph.unifiedRoleManagementPolicyRuleTarget");
target.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Eligibility");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
UnifiedRoleManagementPolicyRule result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").rules().byUnifiedRoleManagementPolicyRuleId("{unifiedRoleManagementPolicyRule-id}").patch(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicyRule = {
    '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyExpirationRule',
    id: 'Expiration_Admin_Eligibility',
    isExpirationRequired: true,
    maximumDuration: 'P90D',
    target: {
        '@odata.type': 'microsoft.graph.unifiedRoleManagementPolicyRuleTarget',
        caller: 'Admin',
        operations: [
            'All'
        ],
        level: 'Eligibility',
        inheritableSettings: [],
        enforcedSettings: []
    }
};

await client.api('/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Expiration_Admin_Eligibility')
	.update(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyExpirationRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicyExpirationRule();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyExpirationRule');
$requestBody->setId('Expiration_Admin_Eligibility');
$requestBody->setIsExpirationRequired(true);
$requestBody->setMaximumDuration(new \DateInterval('P90D'));
$target = new UnifiedRoleManagementPolicyRuleTarget();
$target->setOdataType('microsoft.graph.unifiedRoleManagementPolicyRuleTarget');
$target->setCaller('Admin');
$target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$target->setLevel('Eligibility');
$target->setInheritableSettings([	]);
$target->setEnforcedSettings([	]);
$requestBody->setTarget($target);

$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->rules()->byUnifiedRoleManagementPolicyRuleId('unifiedRoleManagementPolicyRule-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule"
	id = "Expiration_Admin_Eligibility"
	isExpirationRequired = $true
	maximumDuration = "P90D"
	target = @{
		"@odata.type" = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
		caller = "Admin"
		operations = @(
		"All"
	)
	level = "Eligibility"
	inheritableSettings = @(
	)
	enforcedSettings = @(
	)
}
}

Update-MgPolicyRoleManagementPolicyRule -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -UnifiedRoleManagementPolicyRuleId $unifiedRoleManagementPolicyRuleId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy_expiration_rule import UnifiedRoleManagementPolicyExpirationRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicyExpirationRule(
	odata_type = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
	id = "Expiration_Admin_Eligibility",
	is_expiration_required = True,
	maximum_duration = "P90D",
	target = UnifiedRoleManagementPolicyRuleTarget(
		odata_type = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		caller = "Admin",
		operations = [
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		],
		level = "Eligibility",
		inheritable_settings = [
		],
		enforced_settings = [
		],
	),
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').rules.by_unified_role_management_policy_rule_id('unifiedRoleManagementPolicyRule-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Example 5: Set expiration of active assignment

- Category of rule: Assignment rule
- Microsoft Graph [rule type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule): [unifiedRoleManagementPolicyExpirationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyexpirationrule)
- Microsoft Graph rule ID: `Expiration_Admin_Assignment`

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Expiration_Admin_Assignment
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
    "id": "Expiration_Admin_Assignment",
    "isExpirationRequired": true,
    "maximumDuration": "P90D",
    "target": {
        "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
        "caller": "Admin",
        "operations": [
            "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicyExpirationRule
{
	OdataType = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
	Id = "Expiration_Admin_Assignment",
	IsExpirationRequired = true,
	MaximumDuration = TimeSpan.Parse("P90D"),
	Target = new UnifiedRoleManagementPolicyRuleTarget
	{
		OdataType = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		Caller = "Admin",
		Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
		{
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		},
		Level = "Assignment",
		InheritableSettings = new List<string>
		{
		},
		EnforcedSettings = new List<string>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].Rules["{unifiedRoleManagementPolicyRule-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleManagementPolicyRule()
id := "Expiration_Admin_Assignment"
requestBody.SetId(&id) 
isExpirationRequired := true
requestBody.SetIsExpirationRequired(&isExpirationRequired) 
maximumDuration , err := abstractions.ParseISODuration("P90D")
requestBody.SetMaximumDuration(&maximumDuration) 
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
requestBody.SetTarget(target)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rules, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Rules().ByUnifiedRoleManagementPolicyRuleId("unifiedRoleManagementPolicyRule-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyExpirationRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyExpirationRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyExpirationRule");
unifiedRoleManagementPolicyRule.setId("Expiration_Admin_Assignment");
unifiedRoleManagementPolicyRule.setIsExpirationRequired(true);
PeriodAndDuration maximumDuration = PeriodAndDuration.ofDuration(Duration.parse("P90D"));
unifiedRoleManagementPolicyRule.setMaximumDuration(maximumDuration);
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setOdataType("microsoft.graph.unifiedRoleManagementPolicyRuleTarget");
target.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Assignment");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
UnifiedRoleManagementPolicyRule result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").rules().byUnifiedRoleManagementPolicyRuleId("{unifiedRoleManagementPolicyRule-id}").patch(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicyRule = {
    '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyExpirationRule',
    id: 'Expiration_Admin_Assignment',
    isExpirationRequired: true,
    maximumDuration: 'P90D',
    target: {
        '@odata.type': 'microsoft.graph.unifiedRoleManagementPolicyRuleTarget',
        caller: 'Admin',
        operations: [
            'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
    }
};

await client.api('/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Expiration_Admin_Assignment')
	.update(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyExpirationRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicyExpirationRule();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyExpirationRule');
$requestBody->setId('Expiration_Admin_Assignment');
$requestBody->setIsExpirationRequired(true);
$requestBody->setMaximumDuration(new \DateInterval('P90D'));
$target = new UnifiedRoleManagementPolicyRuleTarget();
$target->setOdataType('microsoft.graph.unifiedRoleManagementPolicyRuleTarget');
$target->setCaller('Admin');
$target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$target->setLevel('Assignment');
$target->setInheritableSettings([	]);
$target->setEnforcedSettings([	]);
$requestBody->setTarget($target);

$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->rules()->byUnifiedRoleManagementPolicyRuleId('unifiedRoleManagementPolicyRule-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule"
	id = "Expiration_Admin_Assignment"
	isExpirationRequired = $true
	maximumDuration = "P90D"
	target = @{
		"@odata.type" = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
		caller = "Admin"
		operations = @(
		"All"
	)
	level = "Assignment"
	inheritableSettings = @(
	)
	enforcedSettings = @(
	)
}
}

Update-MgPolicyRoleManagementPolicyRule -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -UnifiedRoleManagementPolicyRuleId $unifiedRoleManagementPolicyRuleId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy_expiration_rule import UnifiedRoleManagementPolicyExpirationRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicyExpirationRule(
	odata_type = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
	id = "Expiration_Admin_Assignment",
	is_expiration_required = True,
	maximum_duration = "P90D",
	target = UnifiedRoleManagementPolicyRuleTarget(
		odata_type = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		caller = "Admin",
		operations = [
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		],
		level = "Assignment",
		inheritable_settings = [
		],
		enforced_settings = [
		],
	),
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').rules.by_unified_role_management_policy_rule_id('unifiedRoleManagementPolicyRule-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Example 6: Set the justification and MFA requirements for active assignment

- Category of rule: Assignment rule
- Microsoft Graph [rule type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule): [unifiedRoleManagementPolicyExpirationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyexpirationrule)
- Microsoft Graph rule ID: `Enablement_Admin_Assignment`

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Enablement_Admin_Assignment
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
    "id": "Enablement_Admin_Assignment",
    "enabledRules": [
        "Justification",
        "MultiFactorAuthentication"
    ],
    "target": {
        "@odata.type": "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
        "caller": "Admin",
        "operations": [
            "All"
        ],
        "level": "Assignment",
        "inheritableSettings": [],
        "enforcedSettings": []
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new UnifiedRoleManagementPolicyEnablementRule
{
	OdataType = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
	Id = "Enablement_Admin_Assignment",
	EnabledRules = new List<string>
	{
		"Justification",
		"MultiFactorAuthentication",
	},
	Target = new UnifiedRoleManagementPolicyRuleTarget
	{
		OdataType = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		Caller = "Admin",
		Operations = new List<UnifiedRoleManagementPolicyRuleTargetOperations?>
		{
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		},
		Level = "Assignment",
		InheritableSettings = new List<string>
		{
		},
		EnforcedSettings = new List<string>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Policies.RoleManagementPolicies["{unifiedRoleManagementPolicy-id}"].Rules["{unifiedRoleManagementPolicyRule-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewUnifiedRoleManagementPolicyRule()
id := "Enablement_Admin_Assignment"
requestBody.SetId(&id) 
enabledRules := []string {
	"Justification",
	"MultiFactorAuthentication",
}
requestBody.SetEnabledRules(enabledRules)
target := graphmodels.NewUnifiedRoleManagementPolicyRuleTarget()
caller := "Admin"
target.SetCaller(&caller) 
operations := []graphmodels.UnifiedRoleManagementPolicyRuleTargetOperationsable {
	unifiedRoleManagementPolicyRuleTargetOperations := graphmodels.ALL_UNIFIEDROLEMANAGEMENTPOLICYRULETARGETOPERATIONS 
	target.SetUnifiedRoleManagementPolicyRuleTargetOperations(&unifiedRoleManagementPolicyRuleTargetOperations)
}
target.SetOperations(operations)
level := "Assignment"
target.SetLevel(&level) 
inheritableSettings := []string {

}
target.SetInheritableSettings(inheritableSettings)
enforcedSettings := []string {

}
target.SetEnforcedSettings(enforcedSettings)
requestBody.SetTarget(target)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rules, err := graphClient.Policies().RoleManagementPolicies().ByUnifiedRoleManagementPolicyId("unifiedRoleManagementPolicy-id").Rules().ByUnifiedRoleManagementPolicyRuleId("unifiedRoleManagementPolicyRule-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

UnifiedRoleManagementPolicyEnablementRule unifiedRoleManagementPolicyRule = new UnifiedRoleManagementPolicyEnablementRule();
unifiedRoleManagementPolicyRule.setOdataType("#microsoft.graph.unifiedRoleManagementPolicyEnablementRule");
unifiedRoleManagementPolicyRule.setId("Enablement_Admin_Assignment");
LinkedList<String> enabledRules = new LinkedList<String>();
enabledRules.add("Justification");
enabledRules.add("MultiFactorAuthentication");
unifiedRoleManagementPolicyRule.setEnabledRules(enabledRules);
UnifiedRoleManagementPolicyRuleTarget target = new UnifiedRoleManagementPolicyRuleTarget();
target.setOdataType("microsoft.graph.unifiedRoleManagementPolicyRuleTarget");
target.setCaller("Admin");
LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations> operations = new LinkedList<UnifiedRoleManagementPolicyRuleTargetOperations>();
operations.add(UnifiedRoleManagementPolicyRuleTargetOperations.All);
target.setOperations(operations);
target.setLevel("Assignment");
LinkedList<String> inheritableSettings = new LinkedList<String>();
target.setInheritableSettings(inheritableSettings);
LinkedList<String> enforcedSettings = new LinkedList<String>();
target.setEnforcedSettings(enforcedSettings);
unifiedRoleManagementPolicyRule.setTarget(target);
UnifiedRoleManagementPolicyRule result = graphClient.policies().roleManagementPolicies().byUnifiedRoleManagementPolicyId("{unifiedRoleManagementPolicy-id}").rules().byUnifiedRoleManagementPolicyRuleId("{unifiedRoleManagementPolicyRule-id}").patch(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unifiedRoleManagementPolicyRule = {
    '@odata.type': '#microsoft.graph.unifiedRoleManagementPolicyEnablementRule',
    id: 'Enablement_Admin_Assignment',
    enabledRules: [
        'Justification',
        'MultiFactorAuthentication'
    ],
    target: {
        '@odata.type': 'microsoft.graph.unifiedRoleManagementPolicyRuleTarget',
        caller: 'Admin',
        operations: [
            'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
    }
};

await client.api('/policies/roleManagementPolicies/DirectoryRole_38d49456-54d4-455d-a8d6-c383c71e0a6d_59d351b1-e819-4262-b298-236f5f9b1a67/rules/Enablement_Admin_Assignment')
	.update(unifiedRoleManagementPolicyRule);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyEnablementRule;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTarget;
use Microsoft\Graph\Generated\Models\UnifiedRoleManagementPolicyRuleTargetOperations;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UnifiedRoleManagementPolicyEnablementRule();
$requestBody->setOdataType('#microsoft.graph.unifiedRoleManagementPolicyEnablementRule');
$requestBody->setId('Enablement_Admin_Assignment');
$requestBody->setEnabledRules(['Justification', 'MultiFactorAuthentication', 	]);
$target = new UnifiedRoleManagementPolicyRuleTarget();
$target->setOdataType('microsoft.graph.unifiedRoleManagementPolicyRuleTarget');
$target->setCaller('Admin');
$target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$target->setLevel('Assignment');
$target->setInheritableSettings([	]);
$target->setEnforcedSettings([	]);
$requestBody->setTarget($target);

$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->rules()->byUnifiedRoleManagementPolicyRuleId('unifiedRoleManagementPolicyRule-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule"
	id = "Enablement_Admin_Assignment"
	enabledRules = @(
	"Justification"
"MultiFactorAuthentication"
)
target = @{
"@odata.type" = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget"
caller = "Admin"
operations = @(
"All"
)
level = "Assignment"
inheritableSettings = @(
)
enforcedSettings = @(
)
}
}

Update-MgPolicyRoleManagementPolicyRule -UnifiedRoleManagementPolicyId $unifiedRoleManagementPolicyId -UnifiedRoleManagementPolicyRuleId $unifiedRoleManagementPolicyRuleId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.unified_role_management_policy_enablement_rule import UnifiedRoleManagementPolicyEnablementRule
from msgraph.generated.models.unified_role_management_policy_rule_target import UnifiedRoleManagementPolicyRuleTarget
from msgraph.generated.models.unified_role_management_policy_rule_target_operations import UnifiedRoleManagementPolicyRuleTargetOperations
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UnifiedRoleManagementPolicyEnablementRule(
	odata_type = "#microsoft.graph.unifiedRoleManagementPolicyEnablementRule",
	id = "Enablement_Admin_Assignment",
	enabled_rules = [
		"Justification",
		"MultiFactorAuthentication",
	],
	target = UnifiedRoleManagementPolicyRuleTarget(
		odata_type = "microsoft.graph.unifiedRoleManagementPolicyRuleTarget",
		caller = "Admin",
		operations = [
			UnifiedRoleManagementPolicyRuleTargetOperations.All,
		],
		level = "Assignment",
		inheritable_settings = [
		],
		enforced_settings = [
		],
	),
)

result = await graph_client.policies.role_management_policies.by_unified_role_management_policy_id('unifiedRoleManagementPolicy-id').rules.by_unified_role_management_policy_rule_id('unifiedRoleManagementPolicyRule-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Related content

- [Overview of role management through the privileged identity management \(PIM\) API](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview)
- [Overview of rules for Microsoft Entra roles in privileged identity management \(PIM\) APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview)
- [Configure Microsoft Entra role settings using the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-change-default-settings)
