<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-workflows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Create workflow

Namespace: microsoft.graph.identityGovernance

Create a new [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. You can create up to 100 workflows in a tenant.

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
POST /identityGovernance/lifecycleWorkflows/workflows
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object.

You can specify the following properties when creating a **workflow**.

| Property | Type | Description |
| :--- | :--- | :--- |
| category | [microsoft.graph.identityGovernance.lifecycleWorkflowCategory](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | The category of the workflow. The possible values are: `joiner`, `leaver`, `unknownFutureValue`. Can be only one value. Required. |
| description | String | A string that describes the purpose of the workflow for administrative use. |
| displayName | String | A unique string that identifies the workflow. Required. |
| executionConditions | [microsoft.graph.identityGovernance.workflowExecutionConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) | Defines for who and when a workflow will run. Required. |
| id | String | Identifier used for individually addressing a specific workflow. |
| isEnabled | Boolean | A Boolean value that denotes whether the workflow is set to run or not. |
| isSchedulingEnabled | Boolean | A Boolean value that denotes whether scheduling is enabled or not. |
| tasks | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) collection | Represents the configured tasks to execute and their execution sequence within the workflow. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a new workflow

#### Request

The following example shows a request that creates a workflow with the following configuration:

- It's a "joiner" workflow that's enabled and schedule to run.
- It runs for new users that are based in Australia, on their employeeHireDate.
- Two tasks are carried out when the workflow runs: the user's account is enabled and a "Welcome" email is sent to the user.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows
Content-Type: application/json

{
    "category": "joiner",
    "description": "Configure new hire tasks for onboarding employees on their first day",
    "displayName": "Australia Onboard new hire employee",
    "isEnabled": true,
    "isSchedulingEnabled": true,
    "executionConditions": {
        "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
        "scope": {
            "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
            "rule": "(country eq 'Australia')"
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
            "arguments": []
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new Workflow
{
	Category = LifecycleWorkflowCategory.Joiner,
	Description = "Configure new hire tasks for onboarding employees on their first day",
	DisplayName = "Australia Onboard new hire employee",
	IsEnabled = true,
	IsSchedulingEnabled = true,
	ExecutionConditions = new TriggerAndScopeBasedConditions
	{
		OdataType = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
		Scope = new RuleBasedSubjectSet
		{
			OdataType = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
			Rule = "(country eq 'Australia')",
		},
		Trigger = new TimeBasedAttributeTrigger
		{
			OdataType = "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
			TimeBasedAttribute = WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
			OffsetInDays = 0,
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
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelsidentitygovernance.NewWorkflow()
category := graphmodels.JOINER_LIFECYCLEWORKFLOWCATEGORY 
requestBody.SetCategory(&category) 
description := "Configure new hire tasks for onboarding employees on their first day"
requestBody.SetDescription(&description) 
displayName := "Australia Onboard new hire employee"
requestBody.SetDisplayName(&displayName) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := true
requestBody.SetIsSchedulingEnabled(&isSchedulingEnabled) 
executionConditions := graphmodelsidentitygovernance.NewTriggerAndScopeBasedConditions()
scope := graphmodelsidentitygovernance.NewRuleBasedSubjectSet()
rule := "(country eq 'Australia')"
scope.SetRule(&rule) 
executionConditions.SetScope(scope)
trigger := graphmodelsidentitygovernance.NewTimeBasedAttributeTrigger()
timeBasedAttribute := graphmodels.EMPLOYEEHIREDATE_WORKFLOWTRIGGERTIMEBASEDATTRIBUTE 
trigger.SetTimeBasedAttribute(&timeBasedAttribute) 
offsetInDays := int32(0)
trigger.SetOffsetInDays(&offsetInDays) 
executionConditions.SetTrigger(trigger)
requestBody.SetExecutionConditions(executionConditions)


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
requestBody.SetTasks(tasks)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workflows, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setCategory(com.microsoft.graph.models.identitygovernance.LifecycleWorkflowCategory.Joiner);
workflow.setDescription("Configure new hire tasks for onboarding employees on their first day");
workflow.setDisplayName("Australia Onboard new hire employee");
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(true);
com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions executionConditions = new com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions();
executionConditions.setOdataType("#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions");
com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet scope = new com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet();
scope.setOdataType("#microsoft.graph.identityGovernance.ruleBasedSubjectSet");
scope.setRule("(country eq 'Australia')");
executionConditions.setScope(scope);
com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger trigger = new com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger();
trigger.setOdataType("#microsoft.graph.identityGovernance.timeBasedAttributeTrigger");
trigger.setTimeBasedAttribute(com.microsoft.graph.models.identitygovernance.WorkflowTriggerTimeBasedAttribute.EmployeeHireDate);
trigger.setOffsetInDays(0);
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
com.microsoft.graph.models.identitygovernance.Workflow result = graphClient.identityGovernance().lifecycleWorkflows().workflows().post(workflow);
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
    displayName: 'Australia Onboard new hire employee',
    isEnabled: true,
    isSchedulingEnabled: true,
    executionConditions: {
        '@odata.type': '#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions',
        scope: {
            '@odata.type': '#microsoft.graph.identityGovernance.ruleBasedSubjectSet',
            rule: '(country eq \'Australia\')'
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
            arguments: []
        }
    ]
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows')
	.post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleWorkflowCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TriggerAndScopeBasedConditions;
use Microsoft\Graph\Generated\Models\IdentityGovernance\RuleBasedSubjectSet;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TimeBasedAttributeTrigger;
use Microsoft\Graph\Generated\Models\IdentityGovernance\WorkflowTriggerTimeBasedAttribute;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workflow();
$requestBody->setCategory(new LifecycleWorkflowCategory('joiner'));
$requestBody->setDescription('Configure new hire tasks for onboarding employees on their first day');
$requestBody->setDisplayName('Australia Onboard new hire employee');
$requestBody->setIsEnabled(true);
$requestBody->setIsSchedulingEnabled(true);
$executionConditions = new TriggerAndScopeBasedConditions();
$executionConditions->setOdataType('#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions');
$executionConditionsScope = new RuleBasedSubjectSet();
$executionConditionsScope->setOdataType('#microsoft.graph.identityGovernance.ruleBasedSubjectSet');
$executionConditionsScope->setRule('(country eq \'Australia\')');
$executionConditions->setScope($executionConditionsScope);
$executionConditionsTrigger = new TimeBasedAttributeTrigger();
$executionConditionsTrigger->setOdataType('#microsoft.graph.identityGovernance.timeBasedAttributeTrigger');
$executionConditionsTrigger->setTimeBasedAttribute(new WorkflowTriggerTimeBasedAttribute('employeeHireDate'));
$executionConditionsTrigger->setOffsetInDays(0);
$executionConditions->setTrigger($executionConditionsTrigger);
$requestBody->setExecutionConditions($executionConditions);
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
$requestBody->setTasks($tasksArray);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	category = "joiner"
	description = "Configure new hire tasks for onboarding employees on their first day"
	displayName = "Australia Onboard new hire employee"
	isEnabled = $true
	isSchedulingEnabled = $true
	executionConditions = @{
		"@odata.type" = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions"
		scope = @{
			"@odata.type" = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet"
			rule = "(country eq 'Australia')"
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

New-MgIdentityGovernanceLifecycleWorkflow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_governance.workflow import Workflow
from msgraph.generated.models.lifecycle_workflow_category import LifecycleWorkflowCategory
from msgraph.generated.models.identity_governance.trigger_and_scope_based_conditions import TriggerAndScopeBasedConditions
from msgraph.generated.models.identity_governance.rule_based_subject_set import RuleBasedSubjectSet
from msgraph.generated.models.identity_governance.time_based_attribute_trigger import TimeBasedAttributeTrigger
from msgraph.generated.models.workflow_trigger_time_based_attribute import WorkflowTriggerTimeBasedAttribute
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workflow(
	category = LifecycleWorkflowCategory.Joiner,
	description = "Configure new hire tasks for onboarding employees on their first day",
	display_name = "Australia Onboard new hire employee",
	is_enabled = True,
	is_scheduling_enabled = True,
	execution_conditions = TriggerAndScopeBasedConditions(
		odata_type = "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
		scope = RuleBasedSubjectSet(
			odata_type = "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
			rule = "(country eq 'Australia')",
		),
		trigger = TimeBasedAttributeTrigger(
			odata_type = "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
			time_based_attribute = WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
			offset_in_days = 0,
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
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows/$entity",
    "category": "joiner",
    "description": "Configure new hire tasks for onboarding employees on their first day",
    "displayName": "New Zealand new hire",
    "lastModifiedDateTime": "2022-08-26T04:51:27.521792Z",
    "createdDateTime": "2022-08-26T04:51:27.5217824Z",
    "deletedDateTime": null,
    "id": "818cd47f-138c-4a83-b3f5-afa92bfcf391",
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "nextScheduleRunDateTime": null,
    "version": 1,
    "executionConditions": {
        "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
        "scope": {
            "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
            "rule": "(country eq 'New Zealand')"
        },
        "trigger": {
            "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
            "timeBasedAttribute": "employeeHireDate",
            "offsetInDays": 0
        }
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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows
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
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new Workflow
{
	Category = LifecycleWorkflowCategory.Joiner,
	Description = "Configure new hire tasks for onboarding employees on their first day",
	DisplayName = "custom email marketing API test",
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
			OffsetInDays = 0,
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
				new KeyValuePair
				{
					Name = "cc",
					Value = "1baa57fa-3c4e-4526-ba5a-db47a9df95f0",
				},
				new KeyValuePair
				{
					Name = "customSubject",
					Value = "Welcome to the organization {{userDisplayName}}!",
				},
				new KeyValuePair
				{
					Name = "customBody",
					Value = "Welcome to our organization {{userGivenName}}!",
				},
				new KeyValuePair
				{
					Name = "locale",
					Value = "en-us",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelsidentitygovernance.NewWorkflow()
category := graphmodels.JOINER_LIFECYCLEWORKFLOWCATEGORY 
requestBody.SetCategory(&category) 
description := "Configure new hire tasks for onboarding employees on their first day"
requestBody.SetDescription(&description) 
displayName := "custom email marketing API test"
requestBody.SetDisplayName(&displayName) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := false
requestBody.SetIsSchedulingEnabled(&isSchedulingEnabled) 
executionConditions := graphmodelsidentitygovernance.NewTriggerAndScopeBasedConditions()
scope := graphmodelsidentitygovernance.NewRuleBasedSubjectSet()
rule := "(department eq 'Marketing')"
scope.SetRule(&rule) 
executionConditions.SetScope(scope)
trigger := graphmodelsidentitygovernance.NewTimeBasedAttributeTrigger()
timeBasedAttribute := graphmodels.EMPLOYEEHIREDATE_WORKFLOWTRIGGERTIMEBASEDATTRIBUTE 
trigger.SetTimeBasedAttribute(&timeBasedAttribute) 
offsetInDays := int32(0)
trigger.SetOffsetInDays(&offsetInDays) 
executionConditions.SetTrigger(trigger)
requestBody.SetExecutionConditions(executionConditions)


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


keyValuePair := graphmodels.NewKeyValuePair()
name := "cc"
keyValuePair.SetName(&name) 
value := "1baa57fa-3c4e-4526-ba5a-db47a9df95f0"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodels.NewKeyValuePair()
name := "customSubject"
keyValuePair1.SetName(&name) 
value := "Welcome to the organization {{userDisplayName}}!"
keyValuePair1.SetValue(&value) 
keyValuePair2 := graphmodels.NewKeyValuePair()
name := "customBody"
keyValuePair2.SetName(&name) 
value := "Welcome to our organization {{userGivenName}}!"
keyValuePair2.SetValue(&value) 
keyValuePair3 := graphmodels.NewKeyValuePair()
name := "locale"
keyValuePair3.SetName(&name) 
value := "en-us"
keyValuePair3.SetValue(&value) 

arguments := []graphmodels.KeyValuePairable {
	keyValuePair,
	keyValuePair1,
	keyValuePair2,
	keyValuePair3,
}
task1.SetArguments(arguments)

tasks := []graphmodelsidentitygovernance.Taskable {
	task,
	task1,
}
requestBody.SetTasks(tasks)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workflows, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setCategory(com.microsoft.graph.models.identitygovernance.LifecycleWorkflowCategory.Joiner);
workflow.setDescription("Configure new hire tasks for onboarding employees on their first day");
workflow.setDisplayName("custom email marketing API test");
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
trigger.setOffsetInDays(0);
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
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("cc");
keyValuePair.setValue("1baa57fa-3c4e-4526-ba5a-db47a9df95f0");
arguments1.add(keyValuePair);
KeyValuePair keyValuePair1 = new KeyValuePair();
keyValuePair1.setName("customSubject");
keyValuePair1.setValue("Welcome to the organization {{userDisplayName}}!");
arguments1.add(keyValuePair1);
KeyValuePair keyValuePair2 = new KeyValuePair();
keyValuePair2.setName("customBody");
keyValuePair2.setValue("Welcome to our organization {{userGivenName}}!");
arguments1.add(keyValuePair2);
KeyValuePair keyValuePair3 = new KeyValuePair();
keyValuePair3.setName("locale");
keyValuePair3.setValue("en-us");
arguments1.add(keyValuePair3);
task1.setArguments(arguments1);
tasks.add(task1);
workflow.setTasks(tasks);
com.microsoft.graph.models.identitygovernance.Workflow result = graphClient.identityGovernance().lifecycleWorkflows().workflows().post(workflow);
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

await client.api('/identityGovernance/lifecycleWorkflows/workflows')
	.post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleWorkflowCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TriggerAndScopeBasedConditions;
use Microsoft\Graph\Generated\Models\IdentityGovernance\RuleBasedSubjectSet;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TimeBasedAttributeTrigger;
use Microsoft\Graph\Generated\Models\IdentityGovernance\WorkflowTriggerTimeBasedAttribute;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workflow();
$requestBody->setCategory(new LifecycleWorkflowCategory('joiner'));
$requestBody->setDescription('Configure new hire tasks for onboarding employees on their first day');
$requestBody->setDisplayName('custom email marketing API test');
$requestBody->setIsEnabled(true);
$requestBody->setIsSchedulingEnabled(false);
$executionConditions = new TriggerAndScopeBasedConditions();
$executionConditions->setOdataType('#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions');
$executionConditionsScope = new RuleBasedSubjectSet();
$executionConditionsScope->setOdataType('#microsoft.graph.identityGovernance.ruleBasedSubjectSet');
$executionConditionsScope->setRule('(department eq \'Marketing\')');
$executionConditions->setScope($executionConditionsScope);
$executionConditionsTrigger = new TimeBasedAttributeTrigger();
$executionConditionsTrigger->setOdataType('#microsoft.graph.identityGovernance.timeBasedAttributeTrigger');
$executionConditionsTrigger->setTimeBasedAttribute(new WorkflowTriggerTimeBasedAttribute('employeeHireDate'));
$executionConditionsTrigger->setOffsetInDays(0);
$executionConditions->setTrigger($executionConditionsTrigger);
$requestBody->setExecutionConditions($executionConditions);
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
$argumentsKeyValuePair1 = new KeyValuePair();
$argumentsKeyValuePair1->setName('cc');
$argumentsKeyValuePair1->setValue('1baa57fa-3c4e-4526-ba5a-db47a9df95f0');
$argumentsArray []= $argumentsKeyValuePair1;
$argumentsKeyValuePair2 = new KeyValuePair();
$argumentsKeyValuePair2->setName('customSubject');
$argumentsKeyValuePair2->setValue('Welcome to the organization {{userDisplayName}}!');
$argumentsArray []= $argumentsKeyValuePair2;
$argumentsKeyValuePair3 = new KeyValuePair();
$argumentsKeyValuePair3->setName('customBody');
$argumentsKeyValuePair3->setValue('Welcome to our organization {{userGivenName}}!');
$argumentsArray []= $argumentsKeyValuePair3;
$argumentsKeyValuePair4 = new KeyValuePair();
$argumentsKeyValuePair4->setName('locale');
$argumentsKeyValuePair4->setValue('en-us');
$argumentsArray []= $argumentsKeyValuePair4;
$tasksTask2->setArguments($argumentsArray);

$tasksArray []= $tasksTask2;
$requestBody->setTasks($tasksArray);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->post($requestBody)->wait();
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

New-MgIdentityGovernanceLifecycleWorkflow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_governance.workflow import Workflow
from msgraph.generated.models.lifecycle_workflow_category import LifecycleWorkflowCategory
from msgraph.generated.models.identity_governance.trigger_and_scope_based_conditions import TriggerAndScopeBasedConditions
from msgraph.generated.models.identity_governance.rule_based_subject_set import RuleBasedSubjectSet
from msgraph.generated.models.identity_governance.time_based_attribute_trigger import TimeBasedAttributeTrigger
from msgraph.generated.models.workflow_trigger_time_based_attribute import WorkflowTriggerTimeBasedAttribute
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workflow(
	category = LifecycleWorkflowCategory.Joiner,
	description = "Configure new hire tasks for onboarding employees on their first day",
	display_name = "custom email marketing API test",
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
			offset_in_days = 0,
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
				KeyValuePair(
					name = "cc",
					value = "1baa57fa-3c4e-4526-ba5a-db47a9df95f0",
				),
				KeyValuePair(
					name = "customSubject",
					value = "Welcome to the organization {{userDisplayName}}!",
				),
				KeyValuePair(
					name = "customBody",
					value = "Welcome to our organization {{userGivenName}}!",
				),
				KeyValuePair(
					name = "locale",
					value = "en-us",
				),
			],
		),
	],
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.post(request_body)
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

### Example 3: Create a mover workflow with a set target scope

#### Request

The following example shows a request that creates a workflow with the following configuration:

- It's a "mover" workflow-enabled and set to run on-demand only.
- It runs for users within the set target scope of the administrative units "4f9dc456-0574-4122-9e55-8b4cc494b27d" and "2c987843-e9b1-4b1a-b924-ff1d2a9b054d".
- One task is carried out, which is to send an email to notify the user's manager of the move.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows
Content-Type: application/json

{
  "category": "mover",
  "displayName": "On Demand workflow move",
  "description": "Execute real-time tasks for employee job changes",
  "tasks": [
    {
      "arguments": [],
      "description": "Send email to notify user's manager of user move",
      "displayName": "Send email to notify manager of user move",
      "isEnabled": true,
      "continueOnError": false,
      "taskDefinitionId": "aab41899-9972-422a-9d97-f626014578b7",
      "category": "mover"
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
      "id": "4f9dc456-0574-4122-9e55-8b4cc494b27d"
    },
    {
      "@odata.type": "#microsoft.graph.administrativeUnit",
      "id": "2c987843-e9b1-4b1a-b924-ff1d2a9b054d"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new Workflow
{
	Category = LifecycleWorkflowCategory.Mover,
	DisplayName = "On Demand workflow move",
	Description = "Execute real-time tasks for employee job changes",
	Tasks = new List<TaskObject>
	{
		new TaskObject
		{
			Arguments = new List<KeyValuePair>
			{
			},
			Description = "Send email to notify user's manager of user move",
			DisplayName = "Send email to notify manager of user move",
			IsEnabled = true,
			ContinueOnError = false,
			TaskDefinitionId = "aab41899-9972-422a-9d97-f626014578b7",
			Category = LifecycleTaskCategory.Mover,
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
			Id = "4f9dc456-0574-4122-9e55-8b4cc494b27d",
		},
		new AdministrativeUnit
		{
			OdataType = "#microsoft.graph.administrativeUnit",
			Id = "2c987843-e9b1-4b1a-b924-ff1d2a9b054d",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelsidentitygovernance.NewWorkflow()
category := graphmodels.MOVER_LIFECYCLEWORKFLOWCATEGORY 
requestBody.SetCategory(&category) 
displayName := "On Demand workflow move"
requestBody.SetDisplayName(&displayName) 
description := "Execute real-time tasks for employee job changes"
requestBody.SetDescription(&description) 


task := graphmodelsidentitygovernance.NewTask()
arguments := []graphmodels.KeyValuePairable {

}
task.SetArguments(arguments)
description := "Send email to notify user's manager of user move"
task.SetDescription(&description) 
displayName := "Send email to notify manager of user move"
task.SetDisplayName(&displayName) 
isEnabled := true
task.SetIsEnabled(&isEnabled) 
continueOnError := false
task.SetContinueOnError(&continueOnError) 
taskDefinitionId := "aab41899-9972-422a-9d97-f626014578b7"
task.SetTaskDefinitionId(&taskDefinitionId) 
category := graphmodels.MOVER_LIFECYCLETASKCATEGORY 
task.SetCategory(&category) 

tasks := []graphmodelsidentitygovernance.Taskable {
	task,
}
requestBody.SetTasks(tasks)
executionConditions := graphmodelsidentitygovernance.NewOnDemandExecutionOnly()
requestBody.SetExecutionConditions(executionConditions)
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := false
requestBody.SetIsSchedulingEnabled(&isSchedulingEnabled) 


directoryObject := graphmodels.NewAdministrativeUnit()
id := "4f9dc456-0574-4122-9e55-8b4cc494b27d"
directoryObject.SetId(&id) 
directoryObject1 := graphmodels.NewAdministrativeUnit()
id := "2c987843-e9b1-4b1a-b924-ff1d2a9b054d"
directoryObject1.SetId(&id) 

administrationScopeTargets := []graphmodels.DirectoryObjectable {
	directoryObject,
	directoryObject1,
}
requestBody.SetAdministrationScopeTargets(administrationScopeTargets)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workflows, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setCategory(com.microsoft.graph.models.identitygovernance.LifecycleWorkflowCategory.Mover);
workflow.setDisplayName("On Demand workflow move");
workflow.setDescription("Execute real-time tasks for employee job changes");
LinkedList<com.microsoft.graph.models.identitygovernance.Task> tasks = new LinkedList<com.microsoft.graph.models.identitygovernance.Task>();
com.microsoft.graph.models.identitygovernance.Task task = new com.microsoft.graph.models.identitygovernance.Task();
LinkedList<KeyValuePair> arguments = new LinkedList<KeyValuePair>();
task.setArguments(arguments);
task.setDescription("Send email to notify user's manager of user move");
task.setDisplayName("Send email to notify manager of user move");
task.setIsEnabled(true);
task.setContinueOnError(false);
task.setTaskDefinitionId("aab41899-9972-422a-9d97-f626014578b7");
task.setCategory(EnumSet.of(com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Mover));
tasks.add(task);
workflow.setTasks(tasks);
com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly executionConditions = new com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly();
executionConditions.setOdataType("#microsoft.graph.identityGovernance.onDemandExecutionOnly");
workflow.setExecutionConditions(executionConditions);
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(false);
LinkedList<DirectoryObject> administrationScopeTargets = new LinkedList<DirectoryObject>();
AdministrativeUnit directoryObject = new AdministrativeUnit();
directoryObject.setOdataType("#microsoft.graph.administrativeUnit");
directoryObject.setId("4f9dc456-0574-4122-9e55-8b4cc494b27d");
administrationScopeTargets.add(directoryObject);
AdministrativeUnit directoryObject1 = new AdministrativeUnit();
directoryObject1.setOdataType("#microsoft.graph.administrativeUnit");
directoryObject1.setId("2c987843-e9b1-4b1a-b924-ff1d2a9b054d");
administrationScopeTargets.add(directoryObject1);
workflow.setAdministrationScopeTargets(administrationScopeTargets);
com.microsoft.graph.models.identitygovernance.Workflow result = graphClient.identityGovernance().lifecycleWorkflows().workflows().post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workflow = {
  category: 'mover',
  displayName: 'On Demand workflow move',
  description: 'Execute real-time tasks for employee job changes',
  tasks: [
    {
      arguments: [],
      description: 'Send email to notify user\'s manager of user move',
      displayName: 'Send email to notify manager of user move',
      isEnabled: true,
      continueOnError: false,
      taskDefinitionId: 'aab41899-9972-422a-9d97-f626014578b7',
      category: 'mover'
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
      id: '4f9dc456-0574-4122-9e55-8b4cc494b27d'
    },
    {
      '@odata.type': '#microsoft.graph.administrativeUnit',
      id: '2c987843-e9b1-4b1a-b924-ff1d2a9b054d'
    }
  ]
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows')
	.post(workflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleWorkflowCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\KeyValuePair;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleTaskCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\OnDemandExecutionOnly;
use Microsoft\Graph\Generated\Models\DirectoryObject;
use Microsoft\Graph\Generated\Models\AdministrativeUnit;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workflow();
$requestBody->setCategory(new LifecycleWorkflowCategory('mover'));
$requestBody->setDisplayName('On Demand workflow move');
$requestBody->setDescription('Execute real-time tasks for employee job changes');
$tasksTask1 = new Task();
$tasksTask1->setArguments([	]);
$tasksTask1->setDescription('Send email to notify user\'s manager of user move');
$tasksTask1->setDisplayName('Send email to notify manager of user move');
$tasksTask1->setIsEnabled(true);
$tasksTask1->setContinueOnError(false);
$tasksTask1->setTaskDefinitionId('aab41899-9972-422a-9d97-f626014578b7');
$tasksTask1->setCategory(new LifecycleTaskCategory('mover'));
$tasksArray []= $tasksTask1;
$requestBody->setTasks($tasksArray);

$executionConditions = new OnDemandExecutionOnly();
$executionConditions->setOdataType('#microsoft.graph.identityGovernance.onDemandExecutionOnly');
$requestBody->setExecutionConditions($executionConditions);
$requestBody->setIsEnabled(true);
$requestBody->setIsSchedulingEnabled(false);
$administrationScopeTargetsDirectoryObject1 = new AdministrativeUnit();
$administrationScopeTargetsDirectoryObject1->setOdataType('#microsoft.graph.administrativeUnit');
$administrationScopeTargetsDirectoryObject1->setId('4f9dc456-0574-4122-9e55-8b4cc494b27d');
$administrationScopeTargetsArray []= $administrationScopeTargetsDirectoryObject1;
$administrationScopeTargetsDirectoryObject2 = new AdministrativeUnit();
$administrationScopeTargetsDirectoryObject2->setOdataType('#microsoft.graph.administrativeUnit');
$administrationScopeTargetsDirectoryObject2->setId('2c987843-e9b1-4b1a-b924-ff1d2a9b054d');
$administrationScopeTargetsArray []= $administrationScopeTargetsDirectoryObject2;
$requestBody->setAdministrationScopeTargets($administrationScopeTargetsArray);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	category = "mover"
	displayName = "On Demand workflow move"
	description = "Execute real-time tasks for employee job changes"
	tasks = @(
		@{
			arguments = @(
			)
			description = "Send email to notify user's manager of user move"
			displayName = "Send email to notify manager of user move"
			isEnabled = $true
			continueOnError = $false
			taskDefinitionId = "aab41899-9972-422a-9d97-f626014578b7"
			category = "mover"
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
			id = "4f9dc456-0574-4122-9e55-8b4cc494b27d"
		}
		@{
			"@odata.type" = "#microsoft.graph.administrativeUnit"
			id = "2c987843-e9b1-4b1a-b924-ff1d2a9b054d"
		}
	)
}

New-MgIdentityGovernanceLifecycleWorkflow -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_governance.workflow import Workflow
from msgraph.generated.models.lifecycle_workflow_category import LifecycleWorkflowCategory
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.key_value_pair import KeyValuePair
from msgraph.generated.models.lifecycle_task_category import LifecycleTaskCategory
from msgraph.generated.models.identity_governance.on_demand_execution_only import OnDemandExecutionOnly
from msgraph.generated.models.directory_object import DirectoryObject
from msgraph.generated.models.administrative_unit import AdministrativeUnit
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workflow(
	category = LifecycleWorkflowCategory.Mover,
	display_name = "On Demand workflow move",
	description = "Execute real-time tasks for employee job changes",
	tasks = [
		Task(
			arguments = [
			],
			description = "Send email to notify user's manager of user move",
			display_name = "Send email to notify manager of user move",
			is_enabled = True,
			continue_on_error = False,
			task_definition_id = "aab41899-9972-422a-9d97-f626014578b7",
			category = LifecycleTaskCategory.Mover,
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
			id = "4f9dc456-0574-4122-9e55-8b4cc494b27d",
		),
		AdministrativeUnit(
			odata_type = "#microsoft.graph.administrativeUnit",
			id = "2c987843-e9b1-4b1a-b924-ff1d2a9b054d",
		),
	],
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows/$entity",
  "category": "mover",
  "description": "Execute real-time tasks for employee job changes",
  "displayName": "On Demand workflow move",
  "isEnabled": true,
  "isSchedulingEnabled": false,
  "lastModifiedDateTime": "2025-01-09T15:28:24.0565594Z",
  "createdDateTime": "2025-01-09T15:28:24.0565526Z",
  "id": "465d0d08-3099-483f-9d93-16aad77bcd22",
  "version": 1,
  "administrationScopeTargets": [
    {
      "@odata.type": "#microsoft.graph.administrativeUnit",
      "id": "4f9dc456-0574-4122-9e55-8b4cc494b27d"
    },
    {
      "@odata.type": "#microsoft.graph.administrativeUnit",
      "id": "2c987843-e9b1-4b1a-b924-ff1d2a9b054d"
    }
  ]
}
```
