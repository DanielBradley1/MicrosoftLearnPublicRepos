<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-createnewversion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# workflow: createNewVersion

Namespace: microsoft.graph.identityGovernance

Create a new version of the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows-Workflow.ReadWrite.All | LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows-Workflow.ReadWrite.All | LifecycleWorkflows.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Lifecycle Workflows Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| workflow | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | The workflow for which you want to create a new version. |

## Response

If successful, this action returns a `200 OK` response code and a [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) in the response body.

## Examples

### Example 1: Create a new version of a workflow

#### Request

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion
Content-Type: application/json
Content-length: 631

{
    "workflow":{
        "category": "joiner",
        "description": "Configure new hire tasks for onboarding employees on their first day",
        "displayName": "Global onboard new hire employee",
        "isEnabled": true,
        "isSchedulingEnabled": false,
        "executionConditions": {
            "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
            "scope": {
                "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                "rule": "(department eq 'Marketing')"
            },
            "trigger": {
                "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                "timeBasedAttribute": "employeeHireDate",
                "offsetInDays": 1
            }
        },
        "tasks": [
            {
                "continueOnError": false,
                "description": "Enable user account in the directory",
                "displayName": "Enable User Account",
                "isEnabled": true,
                "taskDefinitionId": "6fc52c9d-398b-4305-9763-15f42c1676fc",
                "arguments": []
            },
            {
                "continueOnError": false,
                "description": "Send welcome email to new hire",
                "displayName": "Send Welcome Email",
                "isEnabled": true,
                "taskDefinitionId": "70b29d51-b59a-4773-9280-8841dfd3f2ea",
                "arguments": []
            }
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceCreateNewVersion;
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new CreateNewVersionPostRequestBody
{
	Workflow = new Workflow
	{
		Category = LifecycleWorkflowCategory.Joiner,
		Description = "Configure new hire tasks for onboarding employees on their first day",
		DisplayName = "Global onboard new hire employee",
		IsEnabled = true,
		IsSchedulingEnabled = false,
		ExecutionConditions = new TriggerAndScopeBasedConditions
		{
			OdataType = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
			Scope = new RuleBasedSubjectSet
			{
				OdataType = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
				Rule = "(department eq 'Marketing')",
			},
			Trigger = new TimeBasedAttributeTrigger
			{
				OdataType = "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
				TimeBasedAttribute = WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
				OffsetInDays = 1,
			},
		},
		Tasks = new List<TaskObject>
		{
			new TaskObject
			{
				ContinueOnError = false,
				Description = "Enable user account in the directory",
				DisplayName = "Enable User Account",
				IsEnabled = true,
				TaskDefinitionId = "6fc52c9d-398b-4305-9763-15f42c1676fc",
				Arguments = new List<KeyValuePair>
				{
				},
			},
			new TaskObject
			{
				ContinueOnError = false,
				Description = "Send welcome email to new hire",
				DisplayName = "Send Welcome Email",
				IsEnabled = true,
				TaskDefinitionId = "70b29d51-b59a-4773-9280-8841dfd3f2ea",
				Arguments = new List<KeyValuePair>
				{
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceCreateNewVersion.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentitygovernance.NewCreateNewVersionPostRequestBody()
workflow := graphmodelsidentitygovernance.NewWorkflow()
category := graphmodels.JOINER_LIFECYCLEWORKFLOWCATEGORY 
workflow.SetCategory(&category) 
description := "Configure new hire tasks for onboarding employees on their first day"
workflow.SetDescription(&description) 
displayName := "Global onboard new hire employee"
workflow.SetDisplayName(&displayName) 
isEnabled := true
workflow.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := false
workflow.SetIsSchedulingEnabled(&isSchedulingEnabled) 
executionConditions := graphmodelsidentitygovernance.NewTriggerAndScopeBasedConditions()
scope := graphmodelsidentitygovernance.NewRuleBasedSubjectSet()
rule := "(department eq 'Marketing')"
scope.SetRule(&rule) 
executionConditions.SetScope(scope)
trigger := graphmodelsidentitygovernance.NewTimeBasedAttributeTrigger()
timeBasedAttribute := graphmodels.EMPLOYEEHIREDATE_WORKFLOWTRIGGERTIMEBASEDATTRIBUTE 
trigger.SetTimeBasedAttribute(&timeBasedAttribute) 
offsetInDays := int32(1)
trigger.SetOffsetInDays(&offsetInDays) 
executionConditions.SetTrigger(trigger)
workflow.SetExecutionConditions(executionConditions)


task := graphmodelsidentitygovernance.NewTask()
continueOnError := false
task.SetContinueOnError(&continueOnError) 
description := "Enable user account in the directory"
task.SetDescription(&description) 
displayName := "Enable User Account"
task.SetDisplayName(&displayName) 
isEnabled := true
task.SetIsEnabled(&isEnabled) 
taskDefinitionId := "6fc52c9d-398b-4305-9763-15f42c1676fc"
task.SetTaskDefinitionId(&taskDefinitionId) 
arguments := []graphmodels.KeyValuePairable {

}
task.SetArguments(arguments)
task1 := graphmodelsidentitygovernance.NewTask()
continueOnError := false
task1.SetContinueOnError(&continueOnError) 
description := "Send welcome email to new hire"
task1.SetDescription(&description) 
displayName := "Send Welcome Email"
task1.SetDisplayName(&displayName) 
isEnabled := true
task1.SetIsEnabled(&isEnabled) 
taskDefinitionId := "70b29d51-b59a-4773-9280-8841dfd3f2ea"
task1.SetTaskDefinitionId(&taskDefinitionId) 
arguments := []graphmodels.KeyValuePairable {

}
task1.SetArguments(arguments)

tasks := []graphmodelsidentitygovernance.Taskable {
	task,
	task1,
}
workflow.SetTasks(tasks)
requestBody.SetWorkflow(workflow)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphIdentityGovernanceCreateNewVersion, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernanceCreateNewVersion().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody createNewVersionPostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody();
com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setCategory(com.microsoft.graph.models.identitygovernance.LifecycleWorkflowCategory.Joiner);
workflow.setDescription("Configure new hire tasks for onboarding employees on their first day");
workflow.setDisplayName("Global onboard new hire employee");
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(false);
com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions executionConditions = new com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions();
executionConditions.setOdataType("#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions");
com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet scope = new com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet();
scope.setOdataType("#microsoft.graph.identityGovernance.ruleBasedSubjectSet");
scope.setRule("(department eq 'Marketing')");
executionConditions.setScope(scope);
com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger trigger = new com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger();
trigger.setOdataType("#microsoft.graph.identityGovernance.timeBasedAttributeTrigger");
trigger.setTimeBasedAttribute(com.microsoft.graph.models.identitygovernance.WorkflowTriggerTimeBasedAttribute.EmployeeHireDate);
trigger.setOffsetInDays(1);
executionConditions.setTrigger(trigger);
workflow.setExecutionConditions(executionConditions);
LinkedList<com.microsoft.graph.models.identitygovernance.Task> tasks = new LinkedList<com.microsoft.graph.models.identitygovernance.Task>();
com.microsoft.graph.models.identitygovernance.Task task = new com.microsoft.graph.models.identitygovernance.Task();
task.setContinueOnError(false);
task.setDescription("Enable user account in the directory");
task.setDisplayName("Enable User Account");
task.setIsEnabled(true);
task.setTaskDefinitionId("6fc52c9d-398b-4305-9763-15f42c1676fc");
LinkedList<KeyValuePair> arguments = new LinkedList<KeyValuePair>();
task.setArguments(arguments);
tasks.add(task);
com.microsoft.graph.models.identitygovernance.Task task1 = new com.microsoft.graph.models.identitygovernance.Task();
task1.setContinueOnError(false);
task1.setDescription("Send welcome email to new hire");
task1.setDisplayName("Send Welcome Email");
task1.setIsEnabled(true);
task1.setTaskDefinitionId("70b29d51-b59a-4773-9280-8841dfd3f2ea");
LinkedList<KeyValuePair> arguments1 = new LinkedList<KeyValuePair>();
task1.setArguments(arguments1);
tasks.add(task1);
workflow.setTasks(tasks);
createNewVersionPostRequestBody.setWorkflow(workflow);
var result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceCreateNewVersion().post(createNewVersionPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workflow = {
    workflow: {
        category: 'joiner',
        description: 'Configure new hire tasks for onboarding employees on their first day',
        displayName: 'Global onboard new hire employee',
        isEnabled: true,
        isSchedulingEnabled: false,
        executionConditions: {
            '@odata.type': '#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions',
            scope: {
                '@odata.type': '#microsoft.graph.identityGovernance.ruleBasedSubjectSet',
                rule: '(department eq \'Marketing\')'
            },
            trigger: {
                '@odata.type': '#microsoft.graph.identityGovernance.timeBasedAttributeTrigger',
                timeBasedAttribute: 'employeeHireDate',
                offsetInDays: 1
            }
        },
        tasks: [
            {
                continueOnError: false,
                description: 'Enable user account in the directory',
                displayName: 'Enable User Account',
                isEnabled: true,
                taskDefinitionId: '6fc52c9d-398b-4305-9763-15f42c1676fc',
                arguments: []
            },
            {
                continueOnError: false,
                description: 'Send welcome email to new hire',
                displayName: 'Send Welcome Email',
                isEnabled: true,
                taskDefinitionId: '70b29d51-b59a-4773-9280-8841dfd3f2ea',
                arguments: []
            }
        ]
    }
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion')
	.post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceCreateNewVersion\CreateNewVersionPostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleWorkflowCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TriggerAndScopeBasedConditions;
use Microsoft\Graph\Generated\Models\IdentityGovernance\RuleBasedSubjectSet;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TimeBasedAttributeTrigger;
use Microsoft\Graph\Generated\Models\IdentityGovernance\WorkflowTriggerTimeBasedAttribute;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateNewVersionPostRequestBody();
$workflow = new Workflow();
$workflow->setCategory(new LifecycleWorkflowCategory('joiner'));
$workflow->setDescription('Configure new hire tasks for onboarding employees on their first day');
$workflow->setDisplayName('Global onboard new hire employee');
$workflow->setIsEnabled(true);
$workflow->setIsSchedulingEnabled(false);
$workflowExecutionConditions = new TriggerAndScopeBasedConditions();
$workflowExecutionConditions->setOdataType('#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions');
$workflowExecutionConditionsScope = new RuleBasedSubjectSet();
$workflowExecutionConditionsScope->setOdataType('#microsoft.graph.identityGovernance.ruleBasedSubjectSet');
$workflowExecutionConditionsScope->setRule('(department eq \'Marketing\')');
$workflowExecutionConditions->setScope($workflowExecutionConditionsScope);
$workflowExecutionConditionsTrigger = new TimeBasedAttributeTrigger();
$workflowExecutionConditionsTrigger->setOdataType('#microsoft.graph.identityGovernance.timeBasedAttributeTrigger');
$workflowExecutionConditionsTrigger->setTimeBasedAttribute(new WorkflowTriggerTimeBasedAttribute('employeeHireDate'));
$workflowExecutionConditionsTrigger->setOffsetInDays(1);
$workflowExecutionConditions->setTrigger($workflowExecutionConditionsTrigger);
$workflow->setExecutionConditions($workflowExecutionConditions);
$tasksTask1 = new Task();
$tasksTask1->setContinueOnError(false);
$tasksTask1->setDescription('Enable user account in the directory');
$tasksTask1->setDisplayName('Enable User Account');
$tasksTask1->setIsEnabled(true);
$tasksTask1->setTaskDefinitionId('6fc52c9d-398b-4305-9763-15f42c1676fc');
$tasksTask1->setArguments([	]);
$tasksArray []= $tasksTask1;
$tasksTask2 = new Task();
$tasksTask2->setContinueOnError(false);
$tasksTask2->setDescription('Send welcome email to new hire');
$tasksTask2->setDisplayName('Send Welcome Email');
$tasksTask2->setIsEnabled(true);
$tasksTask2->setTaskDefinitionId('70b29d51-b59a-4773-9280-8841dfd3f2ea');
$tasksTask2->setArguments([	]);
$tasksArray []= $tasksTask2;
$workflow->setTasks($tasksArray);

$requestBody->setWorkflow($workflow);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceCreateNewVersion()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	workflow = @{
		category = "joiner"
		description = "Configure new hire tasks for onboarding employees on their first day"
		displayName = "Global onboard new hire employee"
		isEnabled = $true
		isSchedulingEnabled = $false
		executionConditions = @{
			"@odata.type" = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions"
			scope = @{
				"@odata.type" = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet"
				rule = "(department eq 'Marketing')"
			}
			trigger = @{
				"@odata.type" = "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger"
				timeBasedAttribute = "employeeHireDate"
				offsetInDays = 
			}
		}
		tasks = @(
			@{
				continueOnError = $false
				description = "Enable user account in the directory"
				displayName = "Enable User Account"
				isEnabled = $true
				taskDefinitionId = "6fc52c9d-398b-4305-9763-15f42c1676fc"
				arguments = @(
				)
			}
			@{
				continueOnError = $false
				description = "Send welcome email to new hire"
				displayName = "Send Welcome Email"
				isEnabled = $true
				taskDefinitionId = "70b29d51-b59a-4773-9280-8841dfd3f2ea"
				arguments = @(
				)
			}
		)
	}
}

New-MgIdentityGovernanceLifecycleWorkflowNewVersion -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_create_new_version.create_new_version_post_request_body import CreateNewVersionPostRequestBody
from msgraph.generated.models.identity_governance.workflow import Workflow
from msgraph.generated.models.lifecycle_workflow_category import LifecycleWorkflowCategory
from msgraph.generated.models.identity_governance.trigger_and_scope_based_conditions import TriggerAndScopeBasedConditions
from msgraph.generated.models.identity_governance.rule_based_subject_set import RuleBasedSubjectSet
from msgraph.generated.models.identity_governance.time_based_attribute_trigger import TimeBasedAttributeTrigger
from msgraph.generated.models.workflow_trigger_time_based_attribute import WorkflowTriggerTimeBasedAttribute
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateNewVersionPostRequestBody(
	workflow = Workflow(
		category = LifecycleWorkflowCategory.Joiner,
		description = "Configure new hire tasks for onboarding employees on their first day",
		display_name = "Global onboard new hire employee",
		is_enabled = True,
		is_scheduling_enabled = False,
		execution_conditions = TriggerAndScopeBasedConditions(
			odata_type = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
			scope = RuleBasedSubjectSet(
				odata_type = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
				rule = "(department eq 'Marketing')",
			),
			trigger = TimeBasedAttributeTrigger(
				odata_type = "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
				time_based_attribute = WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
				offset_in_days = 1,
			),
		),
		tasks = [
			Task(
				continue_on_error = False,
				description = "Enable user account in the directory",
				display_name = "Enable User Account",
				is_enabled = True,
				task_definition_id = "6fc52c9d-398b-4305-9763-15f42c1676fc",
				arguments = [
				],
			),
			Task(
				continue_on_error = False,
				description = "Send welcome email to new hire",
				display_name = "Send Welcome Email",
				is_enabled = True,
				task_definition_id = "70b29d51-b59a-4773-9280-8841dfd3f2ea",
				arguments = [
				],
			),
		],
	),
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_create_new_version.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json


{
    "workflow":{
        "category": "joiner",
        "description": "Configure new hire tasks for onboarding employees on their first day",
        "displayName": "Global onboard new hire employee",
        "isEnabled": true,
        "isSchedulingEnabled": false,
        "executionConditions": {
            "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
            "scope": {
                "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                "rule": "(department eq 'Marketing')"
            },
            "trigger": {
                "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                "timeBasedAttribute": "employeeHireDate",
                "offsetInDays": 1
            }
        },
        "tasks": [
            {
                "continueOnError": false,
                "description": "Enable user account in the directory",
                "displayName": "Enable User Account",
                "isEnabled": true,
                "taskDefinitionId": "6fc52c9d-398b-4305-9763-15f42c1676fc",
                "arguments": []
            },
            {
                "continueOnError": false,
                "description": "Send welcome email to new hire",
                "displayName": "Send Welcome Email",
                "isEnabled": true,
                "taskDefinitionId": "70b29d51-b59a-4773-9280-8841dfd3f2ea",
                "arguments": []
            }
        ]
    }
}
```

### Example 2: Create a new version of a task with customized email

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion
Content-Type: application/json
Content-length: 631

{
    "category": "joiner",
    "description": "Configure new hire tasks for onboarding employees on their first day",
    "displayName": "custom email marketing API test",
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "executionConditions": {
        "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
        "scope": {
            "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
            "rule": "(department eq 'Marketing')"
        },
        "trigger": {
            "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
            "timeBasedAttribute": "employeeHireDate",
            "offsetInDays": 0
        }
    },
    "tasks": [
        {
            "continueOnError": false,
            "description": "Enable user account in the directory",
            "displayName": "Enable User Account",
            "isEnabled": true,
            "taskDefinitionId": "6fc52c9d-398b-4305-9763-15f42c1676fc",
            "arguments": []
        },
        {
            "continueOnError": false,
            "description": "Send welcome email to new hire",
            "displayName": "Send Welcome Email",
            "isEnabled": true,
            "taskDefinitionId": "70b29d51-b59a-4773-9280-8841dfd3f2ea",
            "arguments": [
                {
                    "name": "cc",
                    "value": "1baa57fa-3c4e-4526-ba5a-db47a9df95f0"
                },
                {
                    "name": "customSubject",
                    "value": "Welcome to the organization {{userDisplayName}}!"
                },
                {
                    "name": "customBody",
                    "value": "Welcome to our organization {{userGivenName}}!"
                },
                {
                    "name": "locale",
                    "value": "en-us"
                }
            ]
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceCreateNewVersion;
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new CreateNewVersionPostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"category" , "joiner"
		},
		{
			"description" , "Configure new hire tasks for onboarding employees on their first day"
		},
		{
			"displayName" , "custom email marketing API test"
		},
		{
			"isEnabled" , true
		},
		{
			"isSchedulingEnabled" , false
		},
		{
			"executionConditions" , new TriggerAndScopeBasedConditions
			{
				OdataType = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
				Scope = new RuleBasedSubjectSet
				{
					OdataType = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
					Rule = "(department eq 'Marketing')",
				},
				Trigger = new TimeBasedAttributeTrigger
				{
					OdataType = "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
					TimeBasedAttribute = WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
					OffsetInDays = 0,
				},
			}
		},
		{
			"tasks" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"continueOnError", new UntypedBoolean(false)
					},
					{
						"description", new UntypedString("Enable user account in the directory")
					},
					{
						"displayName", new UntypedString("Enable User Account")
					},
					{
						"isEnabled", new UntypedBoolean(true)
					},
					{
						"taskDefinitionId", new UntypedString("6fc52c9d-398b-4305-9763-15f42c1676fc")
					},
					{
						"arguments", new UntypedArray(new List<UntypedNode>
						{
						})
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"continueOnError", new UntypedBoolean(false)
					},
					{
						"description", new UntypedString("Send welcome email to new hire")
					},
					{
						"displayName", new UntypedString("Send Welcome Email")
					},
					{
						"isEnabled", new UntypedBoolean(true)
					},
					{
						"taskDefinitionId", new UntypedString("70b29d51-b59a-4773-9280-8841dfd3f2ea")
					},
					{
						"arguments", new UntypedArray(new List<UntypedNode>
						{
							new UntypedObject(new Dictionary<string, UntypedNode>
							{
								{
									"name", new UntypedString("cc")
								},
								{
									"value", new UntypedString("1baa57fa-3c4e-4526-ba5a-db47a9df95f0")
								},
							}),
							new UntypedObject(new Dictionary<string, UntypedNode>
							{
								{
									"name", new UntypedString("customSubject")
								},
								{
									"value", new UntypedString("Welcome to the organization {{userDisplayName}}!")
								},
							}),
							new UntypedObject(new Dictionary<string, UntypedNode>
							{
								{
									"name", new UntypedString("customBody")
								},
								{
									"value", new UntypedString("Welcome to our organization {{userGivenName}}!")
								},
							}),
							new UntypedObject(new Dictionary<string, UntypedNode>
							{
								{
									"name", new UntypedString("locale")
								},
								{
									"value", new UntypedString("en-us")
								},
							}),
						})
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceCreateNewVersion.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody createNewVersionPostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("category", "joiner");
additionalData.put("description", "Configure new hire tasks for onboarding employees on their first day");
additionalData.put("displayName", "custom email marketing API test");
additionalData.put("isEnabled", true);
additionalData.put("isSchedulingEnabled", false);
com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions executionConditions = new com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions();
executionConditions.setOdataType("#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions");
com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet scope = new com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet();
scope.setOdataType("#microsoft.graph.identityGovernance.ruleBasedSubjectSet");
scope.setRule("(department eq 'Marketing')");
executionConditions.setScope(scope);
com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger trigger = new com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger();
trigger.setOdataType("#microsoft.graph.identityGovernance.timeBasedAttributeTrigger");
trigger.setTimeBasedAttribute(com.microsoft.graph.models.identitygovernance.WorkflowTriggerTimeBasedAttribute.EmployeeHireDate);
trigger.setOffsetInDays(0);
executionConditions.setTrigger(trigger);
additionalData.put("executionConditions", executionConditions);
LinkedList<Object> tasks = new LinkedList<Object>();
 property = new ();
property.setContinueOnError(false);
property.setDescription("Enable user account in the directory");
property.setDisplayName("Enable User Account");
property.setIsEnabled(true);
property.setTaskDefinitionId("6fc52c9d-398b-4305-9763-15f42c1676fc");
LinkedList<Object> arguments = new LinkedList<Object>();
property.setArguments(arguments);
tasks.add(property);
 property1 = new ();
property1.setContinueOnError(false);
property1.setDescription("Send welcome email to new hire");
property1.setDisplayName("Send Welcome Email");
property1.setIsEnabled(true);
property1.setTaskDefinitionId("70b29d51-b59a-4773-9280-8841dfd3f2ea");
LinkedList<Object> arguments1 = new LinkedList<Object>();
 property2 = new ();
property2.setName("cc");
property2.setValue("1baa57fa-3c4e-4526-ba5a-db47a9df95f0");
arguments1.add(property2);
 property3 = new ();
property3.setName("customSubject");
property3.setValue("Welcome to the organization {{userDisplayName}}!");
arguments1.add(property3);
 property4 = new ();
property4.setName("customBody");
property4.setValue("Welcome to our organization {{userGivenName}}!");
arguments1.add(property4);
 property5 = new ();
property5.setName("locale");
property5.setValue("en-us");
arguments1.add(property5);
property1.setArguments(arguments1);
tasks.add(property1);
additionalData.put("tasks", tasks);
createNewVersionPostRequestBody.setAdditionalData(additionalData);
var result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceCreateNewVersion().post(createNewVersionPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workflow = {
    category: 'joiner',
    description: 'Configure new hire tasks for onboarding employees on their first day',
    displayName: 'custom email marketing API test',
    isEnabled: true,
    isSchedulingEnabled: false,
    executionConditions: {
        '@odata.type': '#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions',
        scope: {
            '@odata.type': '#microsoft.graph.identityGovernance.ruleBasedSubjectSet',
            rule: '(department eq \'Marketing\')'
        },
        trigger: {
            '@odata.type': '#microsoft.graph.identityGovernance.timeBasedAttributeTrigger',
            timeBasedAttribute: 'employeeHireDate',
            offsetInDays: 0
        }
    },
    tasks: [
        {
            continueOnError: false,
            description: 'Enable user account in the directory',
            displayName: 'Enable User Account',
            isEnabled: true,
            taskDefinitionId: '6fc52c9d-398b-4305-9763-15f42c1676fc',
            arguments: []
        },
        {
            continueOnError: false,
            description: 'Send welcome email to new hire',
            displayName: 'Send Welcome Email',
            isEnabled: true,
            taskDefinitionId: '70b29d51-b59a-4773-9280-8841dfd3f2ea',
            arguments: [
                {
                    name: 'cc',
                    value: '1baa57fa-3c4e-4526-ba5a-db47a9df95f0'
                },
                {
                    name: 'customSubject',
                    value: 'Welcome to the organization {{userDisplayName}}!'
                },
                {
                    name: 'customBody',
                    value: 'Welcome to our organization {{userGivenName}}!'
                },
                {
                    name: 'locale',
                    value: 'en-us'
                }
            ]
        }
    ]
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion')
	.post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceCreateNewVersion\CreateNewVersionPostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TriggerAndScopeBasedConditions;
use Microsoft\Graph\Generated\Models\IdentityGovernance\RuleBasedSubjectSet;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TimeBasedAttributeTrigger;
use Microsoft\Graph\Generated\Models\IdentityGovernance\WorkflowTriggerTimeBasedAttribute;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateNewVersionPostRequestBody();
$additionalData = [
	'category' => 'joiner',
	'description' => 'Configure new hire tasks for onboarding employees on their first day',
	'displayName' => 'custom email marketing API test',
	'isEnabled' => true,
	'isSchedulingEnabled' => false,
	'executionConditions' => [
		'@odata.type' => '#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions',
		'scope' => [
			'@odata.type' => '#microsoft.graph.identityGovernance.ruleBasedSubjectSet',
			'rule' => '(department eq \'Marketing\')',
		],
		'trigger' => [
			'@odata.type' => '#microsoft.graph.identityGovernance.timeBasedAttributeTrigger',
			'timeBasedAttribute' => new WorkflowTriggerTimeBasedAttribute('employeeHireDate'),
			'offsetInDays' => 0,
		],
	],
	'tasks' => [
			[
				'continueOnError' => false,
				'description' => 'Enable user account in the directory',
				'displayName' => 'Enable User Account',
				'isEnabled' => true,
				'taskDefinitionId' => '6fc52c9d-398b-4305-9763-15f42c1676fc',
				'arguments' => [],
			],
			[
				'continueOnError' => false,
				'description' => 'Send welcome email to new hire',
				'displayName' => 'Send Welcome Email',
				'isEnabled' => true,
				'taskDefinitionId' => '70b29d51-b59a-4773-9280-8841dfd3f2ea',
				'arguments' => [
						[
							'name' => 'cc',
							'value' => '1baa57fa-3c4e-4526-ba5a-db47a9df95f0',
						],
						[
							'name' => 'customSubject',
							'value' => 'Welcome to the organization {{userDisplayName}}!',
						],
						[
							'name' => 'customBody',
							'value' => 'Welcome to our organization {{userGivenName}}!',
						],
						[
							'name' => 'locale',
							'value' => 'en-us',
						],
					],
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceCreateNewVersion()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	category = "joiner"
	description = "Configure new hire tasks for onboarding employees on their first day"
	displayName = "custom email marketing API test"
	isEnabled = $true
	isSchedulingEnabled = $false
	executionConditions = @{
		"@odata.type" = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions"
		scope = @{
			"@odata.type" = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet"
			rule = "(department eq 'Marketing')"
		}
		trigger = @{
			"@odata.type" = "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger"
			timeBasedAttribute = "employeeHireDate"
			offsetInDays = 
		}
	}
	tasks = @(
		@{
			continueOnError = $false
			description = "Enable user account in the directory"
			displayName = "Enable User Account"
			isEnabled = $true
			taskDefinitionId = "6fc52c9d-398b-4305-9763-15f42c1676fc"
			arguments = @(
			)
		}
		@{
			continueOnError = $false
			description = "Send welcome email to new hire"
			displayName = "Send Welcome Email"
			isEnabled = $true
			taskDefinitionId = "70b29d51-b59a-4773-9280-8841dfd3f2ea"
			arguments = @(
				@{
					name = "cc"
					value = "1baa57fa-3c4e-4526-ba5a-db47a9df95f0"
				}
				@{
					name = "customSubject"
					value = "Welcome to the organization {{userDisplayName}}!"
				}
				@{
					name = "customBody"
					value = "Welcome to our organization {{userGivenName}}!"
				}
				@{
					name = "locale"
					value = "en-us"
				}
			)
		}
	)
}

New-MgIdentityGovernanceLifecycleWorkflowNewVersion -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_create_new_version.create_new_version_post_request_body import CreateNewVersionPostRequestBody
from msgraph.generated.models.identity_governance.trigger_and_scope_based_conditions import TriggerAndScopeBasedConditions
from msgraph.generated.models.identity_governance.rule_based_subject_set import RuleBasedSubjectSet
from msgraph.generated.models.identity_governance.time_based_attribute_trigger import TimeBasedAttributeTrigger
from msgraph.generated.models.workflow_trigger_time_based_attribute import WorkflowTriggerTimeBasedAttribute
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateNewVersionPostRequestBody(
	additional_data = {
			"category" : "joiner",
			"description" : "Configure new hire tasks for onboarding employees on their first day",
			"display_name" : "custom email marketing API test",
			"is_enabled" : True,
			"is_scheduling_enabled" : False,
			"execution_conditions" : {
					"@odata_type" : "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
					"scope" : {
							"@odata_type" : "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
							"rule" : "(department eq 'Marketing')",
					},
					"trigger" : {
							"@odata_type" : "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
							"time_based_attribute" : WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
							"offset_in_days" : 0,
					},
			},
			"tasks" : [
				{
						"continue_on_error" : False,
						"description" : "Enable user account in the directory",
						"display_name" : "Enable User Account",
						"is_enabled" : True,
						"task_definition_id" : "6fc52c9d-398b-4305-9763-15f42c1676fc",
						"arguments" : [
						],
				},
				{
						"continue_on_error" : False,
						"description" : "Send welcome email to new hire",
						"display_name" : "Send Welcome Email",
						"is_enabled" : True,
						"task_definition_id" : "70b29d51-b59a-4773-9280-8841dfd3f2ea",
						"arguments" : [
							{
									"name" : "cc",
									"value" : "1baa57fa-3c4e-4526-ba5a-db47a9df95f0",
							},
							{
									"name" : "customSubject",
									"value" : "Welcome to the organization {{userDisplayName}}!",
							},
							{
									"name" : "customBody",
									"value" : "Welcome to our organization {{userGivenName}}!",
							},
							{
									"name" : "locale",
									"value" : "en-us",
							},
						],
				},
			],
	}
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_create_new_version.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "workflow":{
        "category": "joiner",
        "description": "Configure new hire tasks for onboarding employees on their first day",
        "displayName": "Global onboard new hire employee",
        "isEnabled": true,
        "isSchedulingEnabled": false,
        "executionConditions": {
            "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
            "scope": {
                "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                "rule": "(department eq 'Marketing')"
            },
            "trigger": {
                "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                "timeBasedAttribute": "employeeHireDate",
                "offsetInDays": 1
            }
        },
        "tasks": [
            {
                "continueOnError": false,
                "description": "Enable user account in the directory",
                "displayName": "Enable User Account",
                "isEnabled": true,
                "taskDefinitionId": "6fc52c9d-398b-4305-9763-15f42c1676fc",
                "arguments": []
            },
            {
                "continueOnError": false,
                "description": "Send welcome email to new hire",
                "displayName": "Send Welcome Email",
                "isEnabled": true,
                "taskDefinitionId": "70b29d51-b59a-4773-9280-8841dfd3f2ea",
                "arguments": [
                    {
                    "name": "cc",
                    "value": "b47471b9-af8f-4a5a-bfa2-b78e82398f6e, a7a23ce0-909b-40b9-82cf-95d31f0aaca2"
                },
                {
                "name": "customSubject",
                "value": "Welcome to the organization {{userDisplayName}}!"
                },
                {
                "name": "customBody",
                "value": "Welcome to our organization {{userGivenName}} {{userSurname}}. \nFor more information, reach out to your manager {{managerDisplayName}} at {{managerEmail}}."
                },
                {
                "name": "locale",
                "value": "en-us"
                }, 
    ]
            }
        ]
    }
}
```

### Example 3: Create a new version of a workflow with specific administrative scope

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion
Content-Type: application/json

{
  "workflow": {
    "category": "mover",
    "displayName": "On Demand mover workflow",
    "description": "Execute real-time tasks for employee job changes",
    "tasks": [
      {
        "category": "mover",
        "continueOnError": false,
        "description": "Send email to notify user's manager of user move",
        "displayName": "Send email to notify manager of user move",
        "executionSequence": 1,
        "id": "f09eb640-6c16-4f1a-8b48-6a295a307705",
        "isEnabled": true,
        "taskDefinitionId": "aab41899-9972-422a-9d97-f626014578b7",
        "arguments": []
      },
      {
        "arguments": [
          {
            "name": "groupID",
            "value": "8d1d1deb-2ef0-4f72-a460-729a1cc74e7e"
          }
        ],
        "description": "Add user to selected groups",
        "displayName": "Add user to groups",
        "isEnabled": true,
        "continueOnError": false,
        "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
        "category": "joiner,leaver,mover"
      }
    ],
    "executionConditions": {
      "@odata.type": "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
    },
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "administrationScopeTargets": [
      {
        "@odata.type": "#microsoft.graph.administrativeUnit",
        "id": "2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceCreateNewVersion;
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new CreateNewVersionPostRequestBody
{
	Workflow = new Workflow
	{
		Category = LifecycleWorkflowCategory.Mover,
		DisplayName = "On Demand mover workflow",
		Description = "Execute real-time tasks for employee job changes",
		Tasks = new List<TaskObject>
		{
			new TaskObject
			{
				Category = LifecycleTaskCategory.Mover,
				ContinueOnError = false,
				Description = "Send email to notify user's manager of user move",
				DisplayName = "Send email to notify manager of user move",
				ExecutionSequence = 1,
				Id = "f09eb640-6c16-4f1a-8b48-6a295a307705",
				IsEnabled = true,
				TaskDefinitionId = "aab41899-9972-422a-9d97-f626014578b7",
				Arguments = new List<KeyValuePair>
				{
				},
			},
			new TaskObject
			{
				Arguments = new List<KeyValuePair>
				{
					new KeyValuePair
					{
						Name = "groupID",
						Value = "8d1d1deb-2ef0-4f72-a460-729a1cc74e7e",
					},
				},
				Description = "Add user to selected groups",
				DisplayName = "Add user to groups",
				IsEnabled = true,
				ContinueOnError = false,
				TaskDefinitionId = "22085229-5809-45e8-97fd-270d28d66910",
				Category = LifecycleTaskCategory.Joiner | LifecycleTaskCategory.Leaver | LifecycleTaskCategory.Mover,
			},
		},
		ExecutionConditions = new OnDemandExecutionOnly
		{
			OdataType = "#microsoft.graph.identityGovernance.onDemandExecutionOnly",
		},
		IsEnabled = true,
		IsSchedulingEnabled = false,
		AdministrationScopeTargets = new List<DirectoryObject>
		{
			new AdministrativeUnit
			{
				OdataType = "#microsoft.graph.administrativeUnit",
				Id = "2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceCreateNewVersion.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentitygovernance.NewCreateNewVersionPostRequestBody()
workflow := graphmodelsidentitygovernance.NewWorkflow()
category := graphmodels.MOVER_LIFECYCLEWORKFLOWCATEGORY 
workflow.SetCategory(&category) 
displayName := "On Demand mover workflow"
workflow.SetDisplayName(&displayName) 
description := "Execute real-time tasks for employee job changes"
workflow.SetDescription(&description) 


task := graphmodelsidentitygovernance.NewTask()
category := graphmodels.MOVER_LIFECYCLETASKCATEGORY 
task.SetCategory(&category) 
continueOnError := false
task.SetContinueOnError(&continueOnError) 
description := "Send email to notify user's manager of user move"
task.SetDescription(&description) 
displayName := "Send email to notify manager of user move"
task.SetDisplayName(&displayName) 
executionSequence := int32(1)
task.SetExecutionSequence(&executionSequence) 
id := "f09eb640-6c16-4f1a-8b48-6a295a307705"
task.SetId(&id) 
isEnabled := true
task.SetIsEnabled(&isEnabled) 
taskDefinitionId := "aab41899-9972-422a-9d97-f626014578b7"
task.SetTaskDefinitionId(&taskDefinitionId) 
arguments := []graphmodels.KeyValuePairable {

}
task.SetArguments(arguments)
task1 := graphmodelsidentitygovernance.NewTask()


keyValuePair := graphmodels.NewKeyValuePair()
name := "groupID"
keyValuePair.SetName(&name) 
value := "8d1d1deb-2ef0-4f72-a460-729a1cc74e7e"
keyValuePair.SetValue(&value) 

arguments := []graphmodels.KeyValuePairable {
	keyValuePair,
}
task1.SetArguments(arguments)
description := "Add user to selected groups"
task1.SetDescription(&description) 
displayName := "Add user to groups"
task1.SetDisplayName(&displayName) 
isEnabled := true
task1.SetIsEnabled(&isEnabled) 
continueOnError := false
task1.SetContinueOnError(&continueOnError) 
taskDefinitionId := "22085229-5809-45e8-97fd-270d28d66910"
task1.SetTaskDefinitionId(&taskDefinitionId) 
category := graphmodels.JOINER,LEAVER,MOVER_LIFECYCLETASKCATEGORY 
task1.SetCategory(&category) 

tasks := []graphmodelsidentitygovernance.Taskable {
	task,
	task1,
}
workflow.SetTasks(tasks)
executionConditions := graphmodelsidentitygovernance.NewOnDemandExecutionOnly()
workflow.SetExecutionConditions(executionConditions)
isEnabled := true
workflow.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := false
workflow.SetIsSchedulingEnabled(&isSchedulingEnabled) 


directoryObject := graphmodels.NewAdministrativeUnit()
id := "2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7"
directoryObject.SetId(&id) 

administrationScopeTargets := []graphmodels.DirectoryObjectable {
	directoryObject,
}
workflow.SetAdministrationScopeTargets(administrationScopeTargets)
requestBody.SetWorkflow(workflow)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphIdentityGovernanceCreateNewVersion, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernanceCreateNewVersion().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody createNewVersionPostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody();
com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setCategory(com.microsoft.graph.models.identitygovernance.LifecycleWorkflowCategory.Mover);
workflow.setDisplayName("On Demand mover workflow");
workflow.setDescription("Execute real-time tasks for employee job changes");
LinkedList<com.microsoft.graph.models.identitygovernance.Task> tasks = new LinkedList<com.microsoft.graph.models.identitygovernance.Task>();
com.microsoft.graph.models.identitygovernance.Task task = new com.microsoft.graph.models.identitygovernance.Task();
task.setCategory(EnumSet.of(com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Mover));
task.setContinueOnError(false);
task.setDescription("Send email to notify user's manager of user move");
task.setDisplayName("Send email to notify manager of user move");
task.setExecutionSequence(1);
task.setId("f09eb640-6c16-4f1a-8b48-6a295a307705");
task.setIsEnabled(true);
task.setTaskDefinitionId("aab41899-9972-422a-9d97-f626014578b7");
LinkedList<KeyValuePair> arguments = new LinkedList<KeyValuePair>();
task.setArguments(arguments);
tasks.add(task);
com.microsoft.graph.models.identitygovernance.Task task1 = new com.microsoft.graph.models.identitygovernance.Task();
LinkedList<KeyValuePair> arguments1 = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("groupID");
keyValuePair.setValue("8d1d1deb-2ef0-4f72-a460-729a1cc74e7e");
arguments1.add(keyValuePair);
task1.setArguments(arguments1);
task1.setDescription("Add user to selected groups");
task1.setDisplayName("Add user to groups");
task1.setIsEnabled(true);
task1.setContinueOnError(false);
task1.setTaskDefinitionId("22085229-5809-45e8-97fd-270d28d66910");
task1.setCategory(EnumSet.of(com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Joiner, com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Leaver, com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Mover));
tasks.add(task1);
workflow.setTasks(tasks);
com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly executionConditions = new com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly();
executionConditions.setOdataType("#microsoft.graph.identityGovernance.onDemandExecutionOnly");
workflow.setExecutionConditions(executionConditions);
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(false);
LinkedList<DirectoryObject> administrationScopeTargets = new LinkedList<DirectoryObject>();
AdministrativeUnit directoryObject = new AdministrativeUnit();
directoryObject.setOdataType("#microsoft.graph.administrativeUnit");
directoryObject.setId("2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7");
administrationScopeTargets.add(directoryObject);
workflow.setAdministrationScopeTargets(administrationScopeTargets);
createNewVersionPostRequestBody.setWorkflow(workflow);
var result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceCreateNewVersion().post(createNewVersionPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workflow = {
  workflow: {
    category: 'mover',
    displayName: 'On Demand mover workflow',
    description: 'Execute real-time tasks for employee job changes',
    tasks: [
      {
        category: 'mover',
        continueOnError: false,
        description: 'Send email to notify user\'s manager of user move',
        displayName: 'Send email to notify manager of user move',
        executionSequence: 1,
        id: 'f09eb640-6c16-4f1a-8b48-6a295a307705',
        isEnabled: true,
        taskDefinitionId: 'aab41899-9972-422a-9d97-f626014578b7',
        arguments: []
      },
      {
        arguments: [
          {
            name: 'groupID',
            value: '8d1d1deb-2ef0-4f72-a460-729a1cc74e7e'
          }
        ],
        description: 'Add user to selected groups',
        displayName: 'Add user to groups',
        isEnabled: true,
        continueOnError: false,
        taskDefinitionId: '22085229-5809-45e8-97fd-270d28d66910',
        category: 'joiner,leaver,mover'
      }
    ],
    executionConditions: {
      '@odata.type': '#microsoft.graph.identityGovernance.onDemandExecutionOnly'
    },
    isEnabled: true,
    isSchedulingEnabled: false,
    administrationScopeTargets: [
      {
        '@odata.type': '#microsoft.graph.administrativeUnit',
        id: '2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7'
      }
    ]
  }
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion')
	.post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceCreateNewVersion\CreateNewVersionPostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleWorkflowCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleTaskCategory;
use Microsoft\Graph\Generated\Models\KeyValuePair;
use Microsoft\Graph\Generated\Models\IdentityGovernance\OnDemandExecutionOnly;
use Microsoft\Graph\Generated\Models\DirectoryObject;
use Microsoft\Graph\Generated\Models\AdministrativeUnit;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateNewVersionPostRequestBody();
$workflow = new Workflow();
$workflow->setCategory(new LifecycleWorkflowCategory('mover'));
$workflow->setDisplayName('On Demand mover workflow');
$workflow->setDescription('Execute real-time tasks for employee job changes');
$tasksTask1 = new Task();
$tasksTask1->setCategory(new LifecycleTaskCategory('mover'));
$tasksTask1->setContinueOnError(false);
$tasksTask1->setDescription('Send email to notify user\'s manager of user move');
$tasksTask1->setDisplayName('Send email to notify manager of user move');
$tasksTask1->setExecutionSequence(1);
$tasksTask1->setId('f09eb640-6c16-4f1a-8b48-6a295a307705');
$tasksTask1->setIsEnabled(true);
$tasksTask1->setTaskDefinitionId('aab41899-9972-422a-9d97-f626014578b7');
$tasksTask1->setArguments([	]);
$tasksArray []= $tasksTask1;
$tasksTask2 = new Task();
$argumentsKeyValuePair1 = new KeyValuePair();
$argumentsKeyValuePair1->setName('groupID');
$argumentsKeyValuePair1->setValue('8d1d1deb-2ef0-4f72-a460-729a1cc74e7e');
$argumentsArray []= $argumentsKeyValuePair1;
$tasksTask2->setArguments($argumentsArray);

$tasksTask2->setDescription('Add user to selected groups');
$tasksTask2->setDisplayName('Add user to groups');
$tasksTask2->setIsEnabled(true);
$tasksTask2->setContinueOnError(false);
$tasksTask2->setTaskDefinitionId('22085229-5809-45e8-97fd-270d28d66910');
$tasksTask2->setCategory(new LifecycleTaskCategory('joiner,leaver,mover'));
$tasksArray []= $tasksTask2;
$workflow->setTasks($tasksArray);

$workflowExecutionConditions = new OnDemandExecutionOnly();
$workflowExecutionConditions->setOdataType('#microsoft.graph.identityGovernance.onDemandExecutionOnly');
$workflow->setExecutionConditions($workflowExecutionConditions);
$workflow->setIsEnabled(true);
$workflow->setIsSchedulingEnabled(false);
$administrationScopeTargetsDirectoryObject1 = new AdministrativeUnit();
$administrationScopeTargetsDirectoryObject1->setOdataType('#microsoft.graph.administrativeUnit');
$administrationScopeTargetsDirectoryObject1->setId('2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7');
$administrationScopeTargetsArray []= $administrationScopeTargetsDirectoryObject1;
$workflow->setAdministrationScopeTargets($administrationScopeTargetsArray);

$requestBody->setWorkflow($workflow);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceCreateNewVersion()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	workflow = @{
		category = "mover"
		displayName = "On Demand mover workflow"
		description = "Execute real-time tasks for employee job changes"
		tasks = @(
			@{
				category = "mover"
				continueOnError = $false
				description = "Send email to notify user's manager of user move"
				displayName = "Send email to notify manager of user move"
				executionSequence = 1
				id = "f09eb640-6c16-4f1a-8b48-6a295a307705"
				isEnabled = $true
				taskDefinitionId = "aab41899-9972-422a-9d97-f626014578b7"
				arguments = @(
				)
			}
			@{
				arguments = @(
					@{
						name = "groupID"
						value = "8d1d1deb-2ef0-4f72-a460-729a1cc74e7e"
					}
				)
				description = "Add user to selected groups"
				displayName = "Add user to groups"
				isEnabled = $true
				continueOnError = $false
				taskDefinitionId = "22085229-5809-45e8-97fd-270d28d66910"
				category = "joiner,leaver,mover"
			}
		)
		executionConditions = @{
			"@odata.type" = "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
		}
		isEnabled = $true
		isSchedulingEnabled = $false
		administrationScopeTargets = @(
			@{
				"@odata.type" = "#microsoft.graph.administrativeUnit"
				id = "2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7"
			}
		)
	}
}

New-MgIdentityGovernanceLifecycleWorkflowNewVersion -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_create_new_version.create_new_version_post_request_body import CreateNewVersionPostRequestBody
from msgraph.generated.models.identity_governance.workflow import Workflow
from msgraph.generated.models.lifecycle_workflow_category import LifecycleWorkflowCategory
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.lifecycle_task_category import LifecycleTaskCategory
from msgraph.generated.models.key_value_pair import KeyValuePair
from msgraph.generated.models.identity_governance.on_demand_execution_only import OnDemandExecutionOnly
from msgraph.generated.models.directory_object import DirectoryObject
from msgraph.generated.models.administrative_unit import AdministrativeUnit
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateNewVersionPostRequestBody(
	workflow = Workflow(
		category = LifecycleWorkflowCategory.Mover,
		display_name = "On Demand mover workflow",
		description = "Execute real-time tasks for employee job changes",
		tasks = [
			Task(
				category = LifecycleTaskCategory.Mover,
				continue_on_error = False,
				description = "Send email to notify user's manager of user move",
				display_name = "Send email to notify manager of user move",
				execution_sequence = 1,
				id = "f09eb640-6c16-4f1a-8b48-6a295a307705",
				is_enabled = True,
				task_definition_id = "aab41899-9972-422a-9d97-f626014578b7",
				arguments = [
				],
			),
			Task(
				arguments = [
					KeyValuePair(
						name = "groupID",
						value = "8d1d1deb-2ef0-4f72-a460-729a1cc74e7e",
					),
				],
				description = "Add user to selected groups",
				display_name = "Add user to groups",
				is_enabled = True,
				continue_on_error = False,
				task_definition_id = "22085229-5809-45e8-97fd-270d28d66910",
				category = LifecycleTaskCategory.Joiner | LifecycleTaskCategory.Leaver | LifecycleTaskCategory.Mover,
			),
		],
		execution_conditions = OnDemandExecutionOnly(
			odata_type = "#microsoft.graph.identityGovernance.onDemandExecutionOnly",
		),
		is_enabled = True,
		is_scheduling_enabled = False,
		administration_scope_targets = [
			AdministrativeUnit(
				odata_type = "#microsoft.graph.administrativeUnit",
				id = "2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7",
			),
		],
	),
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_create_new_version.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.identityGovernance.workflow",
  "category": "mover",
  "description": "Execute real-time tasks for employee job changes",
  "displayName": "On Demand mover workflow",
  "isEnabled": true,
  "isSchedulingEnabled": false,
  "lastModifiedDateTime": "2025-01-09T15:40:14.4514101Z",
  "createdDateTime": "2025-01-09T15:28:24.0565526Z",
  "deletedDateTime": null,
  "id": "394f5831-b1c2-44b3-830d-bbcb88d4ebb0",
  "nextScheduleRunDateTime": null,
  "version": 2,
  "executionConditions": null,
  "lastModifiedBy": {
    "id": "03ad19ba-bf80-4900-bee0-7f6813ee6ecf"
  },
  "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('465d0d08-3099-483f-9d93-16aad77bcd22')('465d0d08-3099-483f-9d93-16aad77bcd22')/tasks",
  "tasks": [
    {
      "category": "mover",
      "continueOnError": false,
      "description": "Send email to notify user's manager of user move",
      "displayName": "Send email to notify manager of user move",
      "executionSequence": 1,
      "id": "c070b422-17e3-45a2-82a0-42b5a46c2421",
      "isEnabled": true,
      "taskDefinitionId": "aab41899-9972-422a-9d97-f626014578b7",
      "arguments": []
    },
    {
      "category": "joiner,leaver,mover",
      "continueOnError": false,
      "description": "Add user to selected groups",
      "displayName": "Add user to groups",
      "executionSequence": 2,
      "id": "71b576f8-da57-457f-a507-e7b978c56680",
      "isEnabled": true,
      "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
      "arguments": [
        {
          "name": "groupID",
          "value": "8d1d1deb-2ef0-4f72-a460-729a1cc74e7e"
        }
      ]
    }
  ],
  "createdBy": {
    "id": "03ad19ba-bf80-4900-bee0-7f6813ee6ecf"
  },
  "administrationScopeTargets": [
    {
      "@odata.type": "#microsoft.graph.administrativeUnit",
      "id": "2ae6f1b1-fcbf-4ad1-9f4f-8c5e48e364c7"
    }
  ]
}
```

### Example 4: Create a new version of a mover workflow removing a target scope

#### Request

The following example shows a request that updates a workflow with the following configuration:

- It's a "mover" workflow-enabled and set to run on-demand only.
- It runs for users without a set target scope as the adminsitration scope target argument is empty.
- Two tasks are carried out, which are to send an email to notify the user's manager of the move, and to add a user to a specific group.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion
Content-Type: application/json

{
  "workflow": {
    "category": "mover",
    "displayName": "Remove existing target scope of a workflow",
    "description": "On-demand removal of the target scope of a workflow.",
    "tasks": [
      {
        "category": "mover",
        "continueOnError": false,
        "description": "Send email to notify user's manager of user move",
        "displayName": "Send email to notify manager of user move",
        "executionSequence": 1,
        "id": "f09eb640-6c16-4f1a-8b48-6a295a307705",
        "isEnabled": true,
        "taskDefinitionId": "aab41899-9972-422a-9d97-f626014578b7",
        "arguments": []
      },
      {
        "arguments": [
          {
            "name": "groupID",
            "value": "5fa668df-a7b0-43fe-828d-48f7a1f7ca44"
          }
        ],
        "description": "Add user to selected groups",
        "displayName": "Add user to groups",
        "isEnabled": true,
        "continueOnError": false,
        "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
        "category": "joiner,leaver,mover"
      }
    ],
    "executionConditions": {
      "@odata.type": "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
    },
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "administrationScopeTargets": []
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceCreateNewVersion;
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new CreateNewVersionPostRequestBody
{
	Workflow = new Workflow
	{
		Category = LifecycleWorkflowCategory.Mover,
		DisplayName = "Remove existing target scope of a workflow",
		Description = "On-demand removal of the target scope of a workflow.",
		Tasks = new List<TaskObject>
		{
			new TaskObject
			{
				Category = LifecycleTaskCategory.Mover,
				ContinueOnError = false,
				Description = "Send email to notify user's manager of user move",
				DisplayName = "Send email to notify manager of user move",
				ExecutionSequence = 1,
				Id = "f09eb640-6c16-4f1a-8b48-6a295a307705",
				IsEnabled = true,
				TaskDefinitionId = "aab41899-9972-422a-9d97-f626014578b7",
				Arguments = new List<KeyValuePair>
				{
				},
			},
			new TaskObject
			{
				Arguments = new List<KeyValuePair>
				{
					new KeyValuePair
					{
						Name = "groupID",
						Value = "5fa668df-a7b0-43fe-828d-48f7a1f7ca44",
					},
				},
				Description = "Add user to selected groups",
				DisplayName = "Add user to groups",
				IsEnabled = true,
				ContinueOnError = false,
				TaskDefinitionId = "22085229-5809-45e8-97fd-270d28d66910",
				Category = LifecycleTaskCategory.Joiner | LifecycleTaskCategory.Leaver | LifecycleTaskCategory.Mover,
			},
		},
		ExecutionConditions = new OnDemandExecutionOnly
		{
			OdataType = "#microsoft.graph.identityGovernance.onDemandExecutionOnly",
		},
		IsEnabled = true,
		IsSchedulingEnabled = false,
		AdministrationScopeTargets = new List<DirectoryObject>
		{
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceCreateNewVersion.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentitygovernance.NewCreateNewVersionPostRequestBody()
workflow := graphmodelsidentitygovernance.NewWorkflow()
category := graphmodels.MOVER_LIFECYCLEWORKFLOWCATEGORY 
workflow.SetCategory(&category) 
displayName := "Remove existing target scope of a workflow"
workflow.SetDisplayName(&displayName) 
description := "On-demand removal of the target scope of a workflow."
workflow.SetDescription(&description) 


task := graphmodelsidentitygovernance.NewTask()
category := graphmodels.MOVER_LIFECYCLETASKCATEGORY 
task.SetCategory(&category) 
continueOnError := false
task.SetContinueOnError(&continueOnError) 
description := "Send email to notify user's manager of user move"
task.SetDescription(&description) 
displayName := "Send email to notify manager of user move"
task.SetDisplayName(&displayName) 
executionSequence := int32(1)
task.SetExecutionSequence(&executionSequence) 
id := "f09eb640-6c16-4f1a-8b48-6a295a307705"
task.SetId(&id) 
isEnabled := true
task.SetIsEnabled(&isEnabled) 
taskDefinitionId := "aab41899-9972-422a-9d97-f626014578b7"
task.SetTaskDefinitionId(&taskDefinitionId) 
arguments := []graphmodels.KeyValuePairable {

}
task.SetArguments(arguments)
task1 := graphmodelsidentitygovernance.NewTask()


keyValuePair := graphmodels.NewKeyValuePair()
name := "groupID"
keyValuePair.SetName(&name) 
value := "5fa668df-a7b0-43fe-828d-48f7a1f7ca44"
keyValuePair.SetValue(&value) 

arguments := []graphmodels.KeyValuePairable {
	keyValuePair,
}
task1.SetArguments(arguments)
description := "Add user to selected groups"
task1.SetDescription(&description) 
displayName := "Add user to groups"
task1.SetDisplayName(&displayName) 
isEnabled := true
task1.SetIsEnabled(&isEnabled) 
continueOnError := false
task1.SetContinueOnError(&continueOnError) 
taskDefinitionId := "22085229-5809-45e8-97fd-270d28d66910"
task1.SetTaskDefinitionId(&taskDefinitionId) 
category := graphmodels.JOINER,LEAVER,MOVER_LIFECYCLETASKCATEGORY 
task1.SetCategory(&category) 

tasks := []graphmodelsidentitygovernance.Taskable {
	task,
	task1,
}
workflow.SetTasks(tasks)
executionConditions := graphmodelsidentitygovernance.NewOnDemandExecutionOnly()
workflow.SetExecutionConditions(executionConditions)
isEnabled := true
workflow.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := false
workflow.SetIsSchedulingEnabled(&isSchedulingEnabled) 
administrationScopeTargets := []graphmodels.DirectoryObjectable {

}
workflow.SetAdministrationScopeTargets(administrationScopeTargets)
requestBody.SetWorkflow(workflow)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
microsoftGraphIdentityGovernanceCreateNewVersion, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernanceCreateNewVersion().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody createNewVersionPostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecreatenewversion.CreateNewVersionPostRequestBody();
com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setCategory(com.microsoft.graph.models.identitygovernance.LifecycleWorkflowCategory.Mover);
workflow.setDisplayName("Remove existing target scope of a workflow");
workflow.setDescription("On-demand removal of the target scope of a workflow.");
LinkedList<com.microsoft.graph.models.identitygovernance.Task> tasks = new LinkedList<com.microsoft.graph.models.identitygovernance.Task>();
com.microsoft.graph.models.identitygovernance.Task task = new com.microsoft.graph.models.identitygovernance.Task();
task.setCategory(EnumSet.of(com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Mover));
task.setContinueOnError(false);
task.setDescription("Send email to notify user's manager of user move");
task.setDisplayName("Send email to notify manager of user move");
task.setExecutionSequence(1);
task.setId("f09eb640-6c16-4f1a-8b48-6a295a307705");
task.setIsEnabled(true);
task.setTaskDefinitionId("aab41899-9972-422a-9d97-f626014578b7");
LinkedList<KeyValuePair> arguments = new LinkedList<KeyValuePair>();
task.setArguments(arguments);
tasks.add(task);
com.microsoft.graph.models.identitygovernance.Task task1 = new com.microsoft.graph.models.identitygovernance.Task();
LinkedList<KeyValuePair> arguments1 = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("groupID");
keyValuePair.setValue("5fa668df-a7b0-43fe-828d-48f7a1f7ca44");
arguments1.add(keyValuePair);
task1.setArguments(arguments1);
task1.setDescription("Add user to selected groups");
task1.setDisplayName("Add user to groups");
task1.setIsEnabled(true);
task1.setContinueOnError(false);
task1.setTaskDefinitionId("22085229-5809-45e8-97fd-270d28d66910");
task1.setCategory(EnumSet.of(com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Joiner, com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Leaver, com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Mover));
tasks.add(task1);
workflow.setTasks(tasks);
com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly executionConditions = new com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly();
executionConditions.setOdataType("#microsoft.graph.identityGovernance.onDemandExecutionOnly");
workflow.setExecutionConditions(executionConditions);
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(false);
LinkedList<DirectoryObject> administrationScopeTargets = new LinkedList<DirectoryObject>();
workflow.setAdministrationScopeTargets(administrationScopeTargets);
createNewVersionPostRequestBody.setWorkflow(workflow);
var result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceCreateNewVersion().post(createNewVersionPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workflow = {
  workflow: {
    category: 'mover',
    displayName: 'Remove existing target scope of a workflow',
    description: 'On-demand removal of the target scope of a workflow.',
    tasks: [
      {
        category: 'mover',
        continueOnError: false,
        description: 'Send email to notify user\'s manager of user move',
        displayName: 'Send email to notify manager of user move',
        executionSequence: 1,
        id: 'f09eb640-6c16-4f1a-8b48-6a295a307705',
        isEnabled: true,
        taskDefinitionId: 'aab41899-9972-422a-9d97-f626014578b7',
        arguments: []
      },
      {
        arguments: [
          {
            name: 'groupID',
            value: '5fa668df-a7b0-43fe-828d-48f7a1f7ca44'
          }
        ],
        description: 'Add user to selected groups',
        displayName: 'Add user to groups',
        isEnabled: true,
        continueOnError: false,
        taskDefinitionId: '22085229-5809-45e8-97fd-270d28d66910',
        category: 'joiner,leaver,mover'
      }
    ],
    executionConditions: {
      '@odata.type': '#microsoft.graph.identityGovernance.onDemandExecutionOnly'
    },
    isEnabled: true,
    isSchedulingEnabled: false,
    administrationScopeTargets: []
  }
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/{workflowId}/createNewVersion')
	.post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceCreateNewVersion\CreateNewVersionPostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleWorkflowCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleTaskCategory;
use Microsoft\Graph\Generated\Models\KeyValuePair;
use Microsoft\Graph\Generated\Models\IdentityGovernance\OnDemandExecutionOnly;
use Microsoft\Graph\Generated\Models\DirectoryObject;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateNewVersionPostRequestBody();
$workflow = new Workflow();
$workflow->setCategory(new LifecycleWorkflowCategory('mover'));
$workflow->setDisplayName('Remove existing target scope of a workflow');
$workflow->setDescription('On-demand removal of the target scope of a workflow.');
$tasksTask1 = new Task();
$tasksTask1->setCategory(new LifecycleTaskCategory('mover'));
$tasksTask1->setContinueOnError(false);
$tasksTask1->setDescription('Send email to notify user\'s manager of user move');
$tasksTask1->setDisplayName('Send email to notify manager of user move');
$tasksTask1->setExecutionSequence(1);
$tasksTask1->setId('f09eb640-6c16-4f1a-8b48-6a295a307705');
$tasksTask1->setIsEnabled(true);
$tasksTask1->setTaskDefinitionId('aab41899-9972-422a-9d97-f626014578b7');
$tasksTask1->setArguments([	]);
$tasksArray []= $tasksTask1;
$tasksTask2 = new Task();
$argumentsKeyValuePair1 = new KeyValuePair();
$argumentsKeyValuePair1->setName('groupID');
$argumentsKeyValuePair1->setValue('5fa668df-a7b0-43fe-828d-48f7a1f7ca44');
$argumentsArray []= $argumentsKeyValuePair1;
$tasksTask2->setArguments($argumentsArray);

$tasksTask2->setDescription('Add user to selected groups');
$tasksTask2->setDisplayName('Add user to groups');
$tasksTask2->setIsEnabled(true);
$tasksTask2->setContinueOnError(false);
$tasksTask2->setTaskDefinitionId('22085229-5809-45e8-97fd-270d28d66910');
$tasksTask2->setCategory(new LifecycleTaskCategory('joiner,leaver,mover'));
$tasksArray []= $tasksTask2;
$workflow->setTasks($tasksArray);

$workflowExecutionConditions = new OnDemandExecutionOnly();
$workflowExecutionConditions->setOdataType('#microsoft.graph.identityGovernance.onDemandExecutionOnly');
$workflow->setExecutionConditions($workflowExecutionConditions);
$workflow->setIsEnabled(true);
$workflow->setIsSchedulingEnabled(false);
$workflow->setAdministrationScopeTargets([]);
$requestBody->setWorkflow($workflow);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceCreateNewVersion()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	workflow = @{
		category = "mover"
		displayName = "Remove existing target scope of a workflow"
		description = "On-demand removal of the target scope of a workflow."
		tasks = @(
			@{
				category = "mover"
				continueOnError = $false
				description = "Send email to notify user's manager of user move"
				displayName = "Send email to notify manager of user move"
				executionSequence = 1
				id = "f09eb640-6c16-4f1a-8b48-6a295a307705"
				isEnabled = $true
				taskDefinitionId = "aab41899-9972-422a-9d97-f626014578b7"
				arguments = @(
				)
			}
			@{
				arguments = @(
					@{
						name = "groupID"
						value = "5fa668df-a7b0-43fe-828d-48f7a1f7ca44"
					}
				)
				description = "Add user to selected groups"
				displayName = "Add user to groups"
				isEnabled = $true
				continueOnError = $false
				taskDefinitionId = "22085229-5809-45e8-97fd-270d28d66910"
				category = "joiner,leaver,mover"
			}
		)
		executionConditions = @{
			"@odata.type" = "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
		}
		isEnabled = $true
		isSchedulingEnabled = $false
		administrationScopeTargets = @(
		)
	}
}

New-MgIdentityGovernanceLifecycleWorkflowNewVersion -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_create_new_version.create_new_version_post_request_body import CreateNewVersionPostRequestBody
from msgraph.generated.models.identity_governance.workflow import Workflow
from msgraph.generated.models.lifecycle_workflow_category import LifecycleWorkflowCategory
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.lifecycle_task_category import LifecycleTaskCategory
from msgraph.generated.models.key_value_pair import KeyValuePair
from msgraph.generated.models.identity_governance.on_demand_execution_only import OnDemandExecutionOnly
from msgraph.generated.models.directory_object import DirectoryObject
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateNewVersionPostRequestBody(
	workflow = Workflow(
		category = LifecycleWorkflowCategory.Mover,
		display_name = "Remove existing target scope of a workflow",
		description = "On-demand removal of the target scope of a workflow.",
		tasks = [
			Task(
				category = LifecycleTaskCategory.Mover,
				continue_on_error = False,
				description = "Send email to notify user's manager of user move",
				display_name = "Send email to notify manager of user move",
				execution_sequence = 1,
				id = "f09eb640-6c16-4f1a-8b48-6a295a307705",
				is_enabled = True,
				task_definition_id = "aab41899-9972-422a-9d97-f626014578b7",
				arguments = [
				],
			),
			Task(
				arguments = [
					KeyValuePair(
						name = "groupID",
						value = "5fa668df-a7b0-43fe-828d-48f7a1f7ca44",
					),
				],
				description = "Add user to selected groups",
				display_name = "Add user to groups",
				is_enabled = True,
				continue_on_error = False,
				task_definition_id = "22085229-5809-45e8-97fd-270d28d66910",
				category = LifecycleTaskCategory.Joiner | LifecycleTaskCategory.Leaver | LifecycleTaskCategory.Mover,
			),
		],
		execution_conditions = OnDemandExecutionOnly(
			odata_type = "#microsoft.graph.identityGovernance.onDemandExecutionOnly",
		),
		is_enabled = True,
		is_scheduling_enabled = False,
		administration_scope_targets = [
		],
	),
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_create_new_version.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.identityGovernance.workflow",
  "category": "mover",
  "description": "On-demand removal of the target scope of a workflow.",
  "displayName": "Remove existing target scope of a workflow",
  "isEnabled": true,
  "isSchedulingEnabled": false,
  "lastModifiedDateTime": "2025-01-09T15:40:14.4514101Z",
  "createdDateTime": "2025-01-09T15:28:24.0565526Z",
  "deletedDateTime": null,
  "id": "394f5831-b1c2-44b3-830d-bbcb88d4ebb0",
  "nextScheduleRunDateTime": null,
  "version": 2,
  "executionConditions": null,
  "lastModifiedBy": {
    "id": "2355df95-8fd8-499c-adcf-4b5f1acf713d"
  },
  "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('e64ec370-8b6c-4eb7-a692-a07ffa26dc1f')('e64ec370-8b6c-4eb7-a692-a07ffa26dc1f')/tasks",
  "tasks": [
    {
      "category": "mover",
      "continueOnError": false,
      "description": "Send email to notify user's manager of user move",
      "displayName": "Send email to notify manager of user move",
      "executionSequence": 1,
      "id": "c070b422-17e3-45a2-82a0-42b5a46c2421",
      "isEnabled": true,
      "taskDefinitionId": "aab41899-9972-422a-9d97-f626014578b7",
      "arguments": []
    },
    {
      "category": "joiner,leaver,mover",
      "continueOnError": false,
      "description": "Add user to selected groups",
      "displayName": "Add user to groups",
      "executionSequence": 2,
      "id": "71b576f8-da57-457f-a507-e7b978c56680",
      "isEnabled": true,
      "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
      "arguments": [
        {
          "name": "groupID",
          "value": "5fa668df-a7b0-43fe-828d-48f7a1f7ca44"
        }
      ]
    }
  ],
  "administrationScopeTargets": [],
  "createdBy": {
    "id": "2355df95-8fd8-499c-adcf-4b5f1acf713d"
  }
}
```
