<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannertaskconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-28 -->

# Update plannerTaskConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BusinessScenarioConfig.ReadWrite.OwnedBy | BusinessScenarioConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BusinessScenarioConfig.ReadWrite.OwnedBy | Not available. |

## HTTP request

```http
PATCH /solutions/businessScenarios/{businessScenarioId}/planner/taskConfiguration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | Last known `@odata-etag` value for the **plannerTaskConfiguration** to be updated. Required. Learn more about [etags](https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-1.0#planner-resource-versioning). |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| editPolicy | [plannerTaskPolicy](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskpolicy?view=graph-rest-beta) | Policy configuration for tasks created for a [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta) when they are being changed outside of the scenario. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [plannerTaskConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskconfiguration?view=graph-rest-beta) object in the response body.

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
PATCH https://graph.microsoft.com/beta/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/taskConfiguration
Content-Type: application/json
If-Match: W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="

{
    "editPolicy": {
        "rules": [
            {
                "userType": {
                    "@odata.type": "#microsoft.graph.plannerRelationshipBasedUserType",
                    "selectionKind": "relationship",
                    "role": "defaultRules"
                },
                "defaultRule": "block",
                "propertyRule": {
                    "ruleKind": "taskRule",
                    "references": {
                        "defaultRules": [ "allow" ],
                        "overrides": []
                    },
                    "checkLists": {
                        "defaultRules": [ "allow" ],
                        "overrides": []
                    },
                    "assignments": {
                        "defaultRules": [ "allow" ],
                        "overrides": [
                            {
                                "name": "userCreated",
                                "rules": [ "allow" ]
                            },
                            {
                                "name": "applicationCreated",
                                "rules": [ "allow" ]
                            }
                        ]
                    },
                    "appliedCategories": {
                        "defaultRules": [ "allow" ],
                        "overrides": []
                    }
                }
            }
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PlannerTaskConfiguration
{
	EditPolicy = new PlannerTaskPolicy
	{
		Rules = new List<PlannerTaskRoleBasedRule>
		{
			new PlannerTaskRoleBasedRule
			{
				DefaultRule = "block",
				PropertyRule = new PlannerTaskPropertyRule
				{
					RuleKind = PlannerRuleKind.TaskRule,
					References = new PlannerFieldRules
					{
						DefaultRules = new List<string>
						{
							"allow",
						},
						Overrides = new List<PlannerRuleOverride>
						{
						},
					},
					CheckLists = new PlannerFieldRules
					{
						DefaultRules = new List<string>
						{
							"allow",
						},
						Overrides = new List<PlannerRuleOverride>
						{
						},
					},
					Assignments = new PlannerFieldRules
					{
						DefaultRules = new List<string>
						{
							"allow",
						},
						Overrides = new List<PlannerRuleOverride>
						{
							new PlannerRuleOverride
							{
								Name = "userCreated",
								Rules = new List<string>
								{
									"allow",
								},
							},
							new PlannerRuleOverride
							{
								Name = "applicationCreated",
								Rules = new List<string>
								{
									"allow",
								},
							},
						},
					},
					AppliedCategories = new PlannerFieldRules
					{
						DefaultRules = new List<string>
						{
							"allow",
						},
						Overrides = new List<PlannerRuleOverride>
						{
						},
					},
				},
				AdditionalData = new Dictionary<string, object>
				{
					{
						"userType" , new PlannerRelationshipBasedUserType
						{
							OdataType = "#microsoft.graph.plannerRelationshipBasedUserType",
							Role = PlannerRelationshipUserRoles.DefaultRules,
							AdditionalData = new Dictionary<string, object>
							{
								{
									"selectionKind" , "relationship"
								},
							},
						}
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BusinessScenarios["{businessScenario-id}"].Planner.TaskConfiguration.PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  graphsolutions "github.com/microsoftgraph/msgraph-beta-sdk-go/solutions"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"")

configuration := &graphsolutions.BusinessScenariosItemPlannerTaskConfigurationRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewPlannerTaskConfiguration()
editPolicy := graphmodels.NewPlannerTaskPolicy()


plannerTaskRoleBasedRule := graphmodels.NewPlannerTaskRoleBasedRule()
defaultRule := "block"
plannerTaskRoleBasedRule.SetDefaultRule(&defaultRule) 
propertyRule := graphmodels.NewPlannerTaskPropertyRule()
ruleKind := graphmodels.TASKRULE_PLANNERRULEKIND 
propertyRule.SetRuleKind(&ruleKind) 
references := graphmodels.NewPlannerFieldRules()
defaultRules := []string {
	"allow",
}
references.SetDefaultRules(defaultRules)
overrides := []graphmodels.PlannerRuleOverrideable {

}
references.SetOverrides(overrides)
propertyRule.SetReferences(references)
checkLists := graphmodels.NewPlannerFieldRules()
defaultRules := []string {
	"allow",
}
checkLists.SetDefaultRules(defaultRules)
overrides := []graphmodels.PlannerRuleOverrideable {

}
checkLists.SetOverrides(overrides)
propertyRule.SetCheckLists(checkLists)
assignments := graphmodels.NewPlannerFieldRules()
defaultRules := []string {
	"allow",
}
assignments.SetDefaultRules(defaultRules)


plannerRuleOverride := graphmodels.NewPlannerRuleOverride()
name := "userCreated"
plannerRuleOverride.SetName(&name) 
rules := []string {
	"allow",
}
plannerRuleOverride.SetRules(rules)
plannerRuleOverride1 := graphmodels.NewPlannerRuleOverride()
name := "applicationCreated"
plannerRuleOverride1.SetName(&name) 
rules := []string {
	"allow",
}
plannerRuleOverride1.SetRules(rules)

overrides := []graphmodels.PlannerRuleOverrideable {
	plannerRuleOverride,
	plannerRuleOverride1,
}
assignments.SetOverrides(overrides)
propertyRule.SetAssignments(assignments)
appliedCategories := graphmodels.NewPlannerFieldRules()
defaultRules := []string {
	"allow",
}
appliedCategories.SetDefaultRules(defaultRules)
overrides := []graphmodels.PlannerRuleOverrideable {

}
appliedCategories.SetOverrides(overrides)
propertyRule.SetAppliedCategories(appliedCategories)
plannerTaskRoleBasedRule.SetPropertyRule(propertyRule)
additionalData := map[string]interface{}{
userType := graphmodels.NewPlannerRelationshipBasedUserType()
	role := graphmodels.DEFAULTRULES_PLANNERRELATIONSHIPUSERROLES 
	userType.SetRole(&role) 
additionalData := map[string]interface{}{
		"selectionKind" : "relationship", 
}
	userType.SetAdditionalData(additionalData)
	plannerTaskRoleBasedRule.SetUserType(userType)
}
plannerTaskRoleBasedRule.SetAdditionalData(additionalData)

rules := []graphmodels.PlannerTaskRoleBasedRuleable {
	plannerTaskRoleBasedRule,
}
editPolicy.SetRules(rules)
requestBody.SetEditPolicy(editPolicy)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskConfiguration, err := graphClient.Solutions().BusinessScenarios().ByBusinessScenarioId("businessScenario-id").Planner().TaskConfiguration().Patch(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerTaskConfiguration plannerTaskConfiguration = new PlannerTaskConfiguration();
PlannerTaskPolicy editPolicy = new PlannerTaskPolicy();
LinkedList<PlannerTaskRoleBasedRule> rules = new LinkedList<PlannerTaskRoleBasedRule>();
PlannerTaskRoleBasedRule plannerTaskRoleBasedRule = new PlannerTaskRoleBasedRule();
plannerTaskRoleBasedRule.setDefaultRule("block");
PlannerTaskPropertyRule propertyRule = new PlannerTaskPropertyRule();
propertyRule.setRuleKind(PlannerRuleKind.TaskRule);
PlannerFieldRules references = new PlannerFieldRules();
LinkedList<String> defaultRules = new LinkedList<String>();
defaultRules.add("allow");
references.setDefaultRules(defaultRules);
LinkedList<PlannerRuleOverride> overrides = new LinkedList<PlannerRuleOverride>();
references.setOverrides(overrides);
propertyRule.setReferences(references);
PlannerFieldRules checkLists = new PlannerFieldRules();
LinkedList<String> defaultRules1 = new LinkedList<String>();
defaultRules1.add("allow");
checkLists.setDefaultRules(defaultRules1);
LinkedList<PlannerRuleOverride> overrides1 = new LinkedList<PlannerRuleOverride>();
checkLists.setOverrides(overrides1);
propertyRule.setCheckLists(checkLists);
PlannerFieldRules assignments = new PlannerFieldRules();
LinkedList<String> defaultRules2 = new LinkedList<String>();
defaultRules2.add("allow");
assignments.setDefaultRules(defaultRules2);
LinkedList<PlannerRuleOverride> overrides2 = new LinkedList<PlannerRuleOverride>();
PlannerRuleOverride plannerRuleOverride = new PlannerRuleOverride();
plannerRuleOverride.setName("userCreated");
LinkedList<String> rules1 = new LinkedList<String>();
rules1.add("allow");
plannerRuleOverride.setRules(rules1);
overrides2.add(plannerRuleOverride);
PlannerRuleOverride plannerRuleOverride1 = new PlannerRuleOverride();
plannerRuleOverride1.setName("applicationCreated");
LinkedList<String> rules2 = new LinkedList<String>();
rules2.add("allow");
plannerRuleOverride1.setRules(rules2);
overrides2.add(plannerRuleOverride1);
assignments.setOverrides(overrides2);
propertyRule.setAssignments(assignments);
PlannerFieldRules appliedCategories = new PlannerFieldRules();
LinkedList<String> defaultRules3 = new LinkedList<String>();
defaultRules3.add("allow");
appliedCategories.setDefaultRules(defaultRules3);
LinkedList<PlannerRuleOverride> overrides3 = new LinkedList<PlannerRuleOverride>();
appliedCategories.setOverrides(overrides3);
propertyRule.setAppliedCategories(appliedCategories);
plannerTaskRoleBasedRule.setPropertyRule(propertyRule);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
PlannerRelationshipBasedUserType userType = new PlannerRelationshipBasedUserType();
userType.setOdataType("#microsoft.graph.plannerRelationshipBasedUserType");
userType.setRole(PlannerRelationshipUserRoles.DefaultRules);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("selectionKind", "relationship");
userType.setAdditionalData(additionalData1);
additionalData.put("userType", userType);
plannerTaskRoleBasedRule.setAdditionalData(additionalData);
rules.add(plannerTaskRoleBasedRule);
editPolicy.setRules(rules);
plannerTaskConfiguration.setEditPolicy(editPolicy);
PlannerTaskConfiguration result = graphClient.solutions().businessScenarios().byBusinessScenarioId("{businessScenario-id}").planner().taskConfiguration().patch(plannerTaskConfiguration, requestConfiguration -> {
	requestConfiguration.headers.add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const plannerTaskConfiguration = {
    editPolicy: {
        rules: [
            {
                userType: {
                    '@odata.type': '#microsoft.graph.plannerRelationshipBasedUserType',
                    selectionKind: 'relationship',
                    role: 'defaultRules'
                },
                defaultRule: 'block',
                propertyRule: {
                    ruleKind: 'taskRule',
                    references: {
                        defaultRules: [ 'allow' ],
                        overrides: []
                    },
                    checkLists: {
                        defaultRules: [ 'allow' ],
                        overrides: []
                    },
                    assignments: {
                        defaultRules: [ 'allow' ],
                        overrides: [
                            {
                                name: 'userCreated',
                                rules: [ 'allow' ]
                            },
                            {
                                name: 'applicationCreated',
                                rules: [ 'allow' ]
                            }
                        ]
                    },
                    appliedCategories: {
                        defaultRules: [ 'allow' ],
                        overrides: []
                    }
                }
            }
        ]
    }
};

await client.api('/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/taskConfiguration')
	.version('beta')
	.update(plannerTaskConfiguration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Solutions\BusinessScenarios\Item\Planner\TaskConfiguration\TaskConfigurationRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskConfiguration;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskPolicy;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskRoleBasedRule;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskPropertyRule;
use Microsoft\Graph\Beta\Generated\Models\PlannerRuleKind;
use Microsoft\Graph\Beta\Generated\Models\PlannerFieldRules;
use Microsoft\Graph\Beta\Generated\Models\PlannerRuleOverride;
use Microsoft\Graph\Beta\Generated\Models\PlannerRelationshipBasedUserType;
use Microsoft\Graph\Beta\Generated\Models\PlannerRelationshipUserRoles;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerTaskConfiguration();
$editPolicy = new PlannerTaskPolicy();
$rulesPlannerTaskRoleBasedRule1 = new PlannerTaskRoleBasedRule();
$rulesPlannerTaskRoleBasedRule1->setDefaultRule('block');
$rulesPlannerTaskRoleBasedRule1PropertyRule = new PlannerTaskPropertyRule();
$rulesPlannerTaskRoleBasedRule1PropertyRule->setRuleKind(new PlannerRuleKind('taskRule'));
$rulesPlannerTaskRoleBasedRule1PropertyRuleReferences = new PlannerFieldRules();
$rulesPlannerTaskRoleBasedRule1PropertyRuleReferences->setDefaultRules(['allow', 	]);
$rulesPlannerTaskRoleBasedRule1PropertyRuleReferences->setOverrides([	]);
$rulesPlannerTaskRoleBasedRule1PropertyRule->setReferences($rulesPlannerTaskRoleBasedRule1PropertyRuleReferences);
$rulesPlannerTaskRoleBasedRule1PropertyRuleCheckLists = new PlannerFieldRules();
$rulesPlannerTaskRoleBasedRule1PropertyRuleCheckLists->setDefaultRules(['allow', 	]);
$rulesPlannerTaskRoleBasedRule1PropertyRuleCheckLists->setOverrides([	]);
$rulesPlannerTaskRoleBasedRule1PropertyRule->setCheckLists($rulesPlannerTaskRoleBasedRule1PropertyRuleCheckLists);
$rulesPlannerTaskRoleBasedRule1PropertyRuleAssignments = new PlannerFieldRules();
$rulesPlannerTaskRoleBasedRule1PropertyRuleAssignments->setDefaultRules(['allow', 	]);
$overridesPlannerRuleOverride1 = new PlannerRuleOverride();
$overridesPlannerRuleOverride1->setName('userCreated');
$overridesPlannerRuleOverride1->setRules(['allow', 	]);
$overridesArray []= $overridesPlannerRuleOverride1;
$overridesPlannerRuleOverride2 = new PlannerRuleOverride();
$overridesPlannerRuleOverride2->setName('applicationCreated');
$overridesPlannerRuleOverride2->setRules(['allow', 	]);
$overridesArray []= $overridesPlannerRuleOverride2;
$rulesPlannerTaskRoleBasedRule1PropertyRuleAssignments->setOverrides($overridesArray);

$rulesPlannerTaskRoleBasedRule1PropertyRule->setAssignments($rulesPlannerTaskRoleBasedRule1PropertyRuleAssignments);
$rulesPlannerTaskRoleBasedRule1PropertyRuleAppliedCategories = new PlannerFieldRules();
$rulesPlannerTaskRoleBasedRule1PropertyRuleAppliedCategories->setDefaultRules(['allow', ]);
$rulesPlannerTaskRoleBasedRule1PropertyRuleAppliedCategories->setOverrides([]);
$rulesPlannerTaskRoleBasedRule1PropertyRule->setAppliedCategories($rulesPlannerTaskRoleBasedRule1PropertyRuleAppliedCategories);
$rulesPlannerTaskRoleBasedRule1->setPropertyRule($rulesPlannerTaskRoleBasedRule1PropertyRule);
$additionalData = [
'userType' => [
	'@odata.type' => '#microsoft.graph.plannerRelationshipBasedUserType',
	'role' => new PlannerRelationshipUserRoles('defaultRules'),
	'additionalData' => [
		'selectionKind' => 'relationship',
	],
],
];
$rulesPlannerTaskRoleBasedRule1->setAdditionalData($additionalData);
$rulesArray []= $rulesPlannerTaskRoleBasedRule1;
$editPolicy->setRules($rulesArray);

$requestBody->setEditPolicy($editPolicy);
$requestConfiguration = new TaskConfigurationRequestBuilderPatchRequestConfiguration();
$headers = [
'If-Match' => 'W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->solutions()->businessScenarios()->byBusinessScenarioId('businessScenario-id')->planner()->taskConfiguration()->patch($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.BusinessScenario

$params = @{
	editPolicy = @{
		rules = @(
			@{
				userType = @{
					"@odata.type" = "#microsoft.graph.plannerRelationshipBasedUserType"
					selectionKind = "relationship"
					role = "defaultRules"
				}
				defaultRule = "block"
				propertyRule = @{
					ruleKind = "taskRule"
					references = @{
						defaultRules = @(
						"allow"
					)
					overrides = @(
					)
				}
				checkLists = @{
					defaultRules = @(
					"allow"
				)
				overrides = @(
				)
			}
			assignments = @{
				defaultRules = @(
				"allow"
			)
			overrides = @(
				@{
					name = "userCreated"
					rules = @(
					"allow"
				)
			}
			@{
				name = "applicationCreated"
				rules = @(
				"allow"
			)
		}
	)
}
appliedCategories = @{
	defaultRules = @(
	"allow"
)
overrides = @(
)
}
}
}
)
}
}

Update-MgBetaSolutionBusinessScenarioPlannerTaskConfiguration -BusinessScenarioId $businessScenarioId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.solutions.business_scenarios.item.planner.task_configuration.task_configuration_request_builder import TaskConfigurationRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.planner_task_configuration import PlannerTaskConfiguration
from msgraph_beta.generated.models.planner_task_policy import PlannerTaskPolicy
from msgraph_beta.generated.models.planner_task_role_based_rule import PlannerTaskRoleBasedRule
from msgraph_beta.generated.models.planner_task_property_rule import PlannerTaskPropertyRule
from msgraph_beta.generated.models.planner_rule_kind import PlannerRuleKind
from msgraph_beta.generated.models.planner_field_rules import PlannerFieldRules
from msgraph_beta.generated.models.planner_rule_override import PlannerRuleOverride
from msgraph_beta.generated.models.planner_relationship_based_user_type import PlannerRelationshipBasedUserType
from msgraph_beta.generated.models.planner_relationship_user_roles import PlannerRelationshipUserRoles
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerTaskConfiguration(
	edit_policy = PlannerTaskPolicy(
		rules = [
			PlannerTaskRoleBasedRule(
				default_rule = "block",
				property_rule = PlannerTaskPropertyRule(
					rule_kind = PlannerRuleKind.TaskRule,
					references = PlannerFieldRules(
						default_rules = [
							"allow",
						],
						overrides = [
						],
					),
					check_lists = PlannerFieldRules(
						default_rules = [
							"allow",
						],
						overrides = [
						],
					),
					assignments = PlannerFieldRules(
						default_rules = [
							"allow",
						],
						overrides = [
							PlannerRuleOverride(
								name = "userCreated",
								rules = [
									"allow",
								],
							),
							PlannerRuleOverride(
								name = "applicationCreated",
								rules = [
									"allow",
								],
							),
						],
					),
					applied_categories = PlannerFieldRules(
						default_rules = [
							"allow",
						],
						overrides = [
						],
					),
				),
				additional_data = {
						"user_type" : {
								"@odata_type" : "#microsoft.graph.plannerRelationshipBasedUserType",
								"role" : PlannerRelationshipUserRoles.DefaultRules,
								"additional_data" : {
										"selection_kind" : "relationship",
								},
						},
				}
			),
		],
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"")


result = await graph_client.solutions.business_scenarios.by_business_scenario_id('businessScenario-id').planner.task_configuration.patch(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
