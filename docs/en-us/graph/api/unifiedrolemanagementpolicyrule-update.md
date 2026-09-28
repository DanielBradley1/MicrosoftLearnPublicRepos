<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedrolemanagementpolicyrule-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update unifiedRoleManagementPolicyRule

Namespace: microsoft.graph

Update a rule defined for a role management policy. The rule can be one of the following types that are derived from the [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) object:

- [unifiedRoleManagementPolicyApprovalRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyapprovalrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyAuthenticationContextRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyauthenticationcontextrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyEnablementRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyenablementrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyExpirationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyexpirationrule?view=graph-rest-1.0)
- [unifiedRoleManagementPolicyNotificationRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicynotificationrule?view=graph-rest-1.0)

For more information about rules for Microsoft Entra roles and examples of updating rules, see the following articles:

- [Overview of rules for Microsoft Entra roles in PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview)
- [Use PIM APIs in Microsoft Graph to update Microsoft Entra ID rules](https://learn.microsoft.com/en-us/graph/how-to-pim-update-rules)

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

### For PIM for Microsoft Entra roles

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | RoleManagementPolicy.ReadWrite.Directory, RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | RoleManagementPolicy.ReadWrite.Directory, RoleManagement.ReadWrite.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- For read operations: *Global Reader*, *Security Operator*, *Security Reader*, *Security Administrator*, or *Privileged Role Administrator*
- For write operations: *Privileged Role Administrator*

### For PIM for Groups

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | RoleManagementPolicy.ReadWrite.AzureADGroup |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | RoleManagementPolicy.ReadWrite.AzureADGroup |

## HTTP request

To update a rule defined for a policy for either Microsoft Entra roles or groups in PIM:

```http
PATCH /policies/roleManagementPolicies/{unifiedRoleManagementPolicyId}/rules/{unifiedRoleManagementPolicyRuleId}
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
| claimValue | String | The value of the authentication context claim.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyAuthenticationContextRule** rule type. |
| enabledRules | String collection | The collection of rules that are enabled for this policy rule. For example, `MultiFactorAuthentication`, `Ticketing`, and `Justification`.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyEnablementRule** rule type. |
| isDefaultRecipientsEnabled | Boolean | Indicates whether a default recipient will receive the notification email.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyNotificationRule** rule type. |
| isEnabled | Boolean | Whether this rule is enabled.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyAuthenticationContextRule** rule type. |
| isExpirationRequired | Boolean | Indicates whether expiration is required or if it's a permanently active assignment or eligibility.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyExpirationRule** rule type. |
| maximumDuration | Duration | The maximum duration allowed for eligibility or assignment which is not permanent. Required when **isExpirationRequired** is `true`.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyExpirationRule** rule type. |
| notificationLevel | String | The level of notification. The possible values are `None`, `Critical`, `All`.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyNotificationRule** rule type. |
| notificationRecipients | String collection | The list of recipients of the email notifications.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyNotificationRule** rule type. |
| notificationType | String | The type of notification. Only `Email` is supported.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyNotificationRule** rule type. |
| recipientType | String | The type of recipient of the notification. The possible values are `Requestor`, `Approver`, `Admin`.  <br>Can be updated for the **unifiedRoleManagementPolicyNotificationRule** rule type. |
| setting | [approvalSettings](https://learn.microsoft.com/en-us/graph/api/resources/approvalsettings?view=graph-rest-1.0) | The settings for approval of the role assignment.  <br>  <br>Can be updated for the **unifiedRoleManagementPolicyApprovalRule** rule type. |
| target | [unifiedRoleManagementPolicyRuleTarget](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyruletarget?view=graph-rest-1.0) | Defines details of the scope that's targeted by role management policy rule. The details can include the principal type, the role assignment type, and actions affecting a role.  <br>  <br>Can be updated for all rule types. |

> **Note:** The `@odata.type` property with a value of the specific rule type must be included in the body. For example, `"@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyApprovalRule"`.

## Response

If successful, this method returns a `200 OK` response code and an [unifiedRoleManagementPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyrule?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update a rule defined for a policy in PIM for Microsoft Entra roles

#### Request

The following example updates a role management policy rule of type **unifiedRoleManagementPolicyExpirationRule** and with ID is `Expiration_EndUser_Assignment`.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/DirectoryRole_84841066-274d-4ec0-a5c1-276be684bdd3_200ec19a-09e7-4e7a-9515-cf1ee64b96f9/rules/Expiration_EndUser_Assignment
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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

await client.api('/policies/roleManagementPolicies/DirectoryRole_84841066-274d-4ec0-a5c1-276be684bdd3_200ec19a-09e7-4e7a-9515-cf1ee64b96f9/rules/Expiration_EndUser_Assignment')
	.update(unifiedRoleManagementPolicyRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies('DirectoryRole_84841066-274d-4ec0-a5c1-276be684bdd3_200ec19a-09e7-4e7a-9515-cf1ee64b96f9')/rules/$entity",
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
    "id": "Expiration_EndUser_Assignment",
    "isExpirationRequired": true,
    "maximumDuration": "PT1H45M",
    "target": {
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

### Example 2: Update a rule defined for a policy in PIM for Groups

#### Request

The following example updates a role management policy rule with ID `Expiration_EndUser_Assignment`.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/policies/roleManagementPolicies/Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369/rules/Expiration_EndUser_Assignment
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
    "id": "Expiration_EndUser_Assignment",
    "isExpirationRequired": true,
    "maximumDuration": "PT1H45M",
    "target": {
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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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
        caller: 'EndUser',
        operations: [
            'All'
        ],
        level: 'Assignment',
        inheritableSettings: [],
        enforcedSettings: []
    }
};

await client.api('/policies/roleManagementPolicies/Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369/rules/Expiration_EndUser_Assignment')
	.update(unifiedRoleManagementPolicyRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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
$target->setCaller('EndUser');
$target->setOperations([new UnifiedRoleManagementPolicyRuleTargetOperations('all'),	]);
$target->setLevel('Assignment');
$target->setInheritableSettings([	]);
$target->setEnforcedSettings([	]);
$requestBody->setTarget($target);

$result = $graphServiceClient->policies()->roleManagementPolicies()->byUnifiedRoleManagementPolicyId('unifiedRoleManagementPolicy-id')->rules()->byUnifiedRoleManagementPolicyRuleId('unifiedRoleManagementPolicyRule-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule"
	id = "Expiration_EndUser_Assignment"
	isExpirationRequired = $true
	maximumDuration = "PT1H45M"
	target = @{
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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/roleManagementPolicies('Group_60bba733-f09d-49b7-8445-32369aa066b3_f21b26d9-9ff9-4af1-b1d4-bddf28591369')/rules/$entity",
    "@odata.type": "#microsoft.graph.unifiedRoleManagementPolicyExpirationRule",
    "id": "Expiration_EndUser_Assignment",
    "isExpirationRequired": true,
    "maximumDuration": "PT1H45M",
    "target": {
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

## Related content

- [Overview of rules for Microsoft Entra roles in PIM APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/identity-governance-pim-rules-overview)
- [Use PIM APIs in Microsoft Graph to update Microsoft Entra ID rules](https://learn.microsoft.com/en-us/graph/how-to-pim-update-rules)
