<!-- Source: https://learn.microsoft.com/en-us/graph/tutorial-lifecycle-workflows-onboard-custom-workflow -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Automate employee onboarding tasks before their first day of work using Lifecycle Workflows APIs

This tutorial explains how to automate prehire tasks with Lifecycle Workflows APIs.

[![Screenshot of the Lifecycle Workflows scenario.](https://learn.microsoft.com/en-us/graph/images/tutorial-lifecycle-workflows/arch-2.png)](https://learn.microsoft.com/en-us/graph/images/tutorial-lifecycle-workflows/arch-2.png#lightbox)

In this tutorial, you learn how to:

- Configure a lifecycle workflow to check for new employees in a specific department, two days before their hire date.
- Configure a task to generate a temporary access pass \(TAP\) for the new employee and send it to the new employee's manager.
- Monitor the status of the workflow and its associated tasks.

## Prerequisites

To complete this tutorial, you need these resources and privileges:

- This feature requires Microsoft Entra ID Governance licenses. See [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals) to find the right license for your requirements.
- Sign in to an API client like [Graph Explorer](https://aka.ms/ge) to call Microsoft Graph with an account that has at least the *Lifecycle Administrator* Microsoft Entra role.
- Grant yourself the *LifecycleWorkflows.ReadWrite.All* Microsoft Graph delegated permission.
- Create two user accounts for this tutorial: one for the new hire and another for their manager. Configure the following settings as applicable.
  | User property | Description | Set on |
  | :--- | :--- | :--- |
  | mail | Used to notify manager of the new employee's temporary access pass \(TAP\). Both the manager and employee should have active mailboxes to receive emails. | Employee, Manager |
  | manager | This attribute that is used by the lifecycle workflow. | Employee |
  | employeeHireDate | Used to trigger the workflow. Set to today's date. | Employee |
  | department | Used to provide the scope for the workflow. Set to `Sales`. | Employee, Manager |
- Enable the [Temporary Access Pass \(TAP\) policy](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-temporary-access-pass#enable-the-temporary-access-pass-policy) in your tenant and ensure the new user is enabled to use the authentication method.

## Create a "joiner" workflow

### Request

This request creates a prehire workflow with these settings:

- It can be run on-demand but not on schedule.
- The workflow runs two days before the employee's hire date, and if they are in the "Sales" department.
- Only one built-in task runs in this workflow: to generate the TAP and send it to the new hire's manager. This task is identified in Lifecycle Workflows by the **taskDefinitionId** `1b555e50-7f65-41d5-b514-5894a026d10d`.

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
Content-type: application/json

{
   "displayName":"Onboard pre-hire employee", 
   "description":"Configure pre-hire tasks for onboarding employees before their first day", 
   "isEnabled":true, 
   "isSchedulingEnabled": false,
   "executionConditions": {
       "@odata.type": "microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
        "scope": {
            "@odata.type": "microsoft.graph.identityGovernance.ruleBasedSubjectSet",
            "rule": "(department eq 'Sales')"
        },
        "trigger": {
            "@odata.type": "microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
            "timeBasedAttribute": "employeeHireDate",
            "offsetInDays": -2
        }
    }, 
   "tasks":[ 
      {
         "isEnabled":true, 
         "category": "Joiner",
         "taskDefinitionId":"1b555e50-7f65-41d5-b514-5894a026d10d", 
         "displayName":"Generate TAP And Send Email", 
         "description":"Generate Temporary Access Pass and send via email to user's manager", 
         "arguments":[ 
            { 
                "name": "tapLifetimeMinutes", 
                "value": "480" 
            }, 
            { 
                "name": "tapIsUsableOnce", 
                "value": "true" 
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
	DisplayName = "Onboard pre-hire employee",
	Description = "Configure pre-hire tasks for onboarding employees before their first day",
	IsEnabled = true,
	IsSchedulingEnabled = false,
	ExecutionConditions = new TriggerAndScopeBasedConditions
	{
		OdataType = "microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
		Scope = new RuleBasedSubjectSet
		{
			OdataType = "microsoft.graph.identityGovernance.ruleBasedSubjectSet",
			Rule = "(department eq 'Sales')",
		},
		Trigger = new TimeBasedAttributeTrigger
		{
			OdataType = "microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
			TimeBasedAttribute = WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
			OffsetInDays = -2,
		},
	},
	Tasks = new List<TaskObject>
	{
		new TaskObject
		{
			IsEnabled = true,
			Category = LifecycleTaskCategory.Joiner,
			TaskDefinitionId = "1b555e50-7f65-41d5-b514-5894a026d10d",
			DisplayName = "Generate TAP And Send Email",
			Description = "Generate Temporary Access Pass and send via email to user's manager",
			Arguments = new List<KeyValuePair>
			{
				new KeyValuePair
				{
					Name = "tapLifetimeMinutes",
					Value = "480",
				},
				new KeyValuePair
				{
					Name = "tapIsUsableOnce",
					Value = "true",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
displayName := "Onboard pre-hire employee"
requestBody.SetDisplayName(&displayName) 
description := "Configure pre-hire tasks for onboarding employees before their first day"
requestBody.SetDescription(&description) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := false
requestBody.SetIsSchedulingEnabled(&isSchedulingEnabled) 
executionConditions := graphmodelsidentitygovernance.NewTriggerAndScopeBasedConditions()
scope := graphmodelsidentitygovernance.NewRuleBasedSubjectSet()
rule := "(department eq 'Sales')"
scope.SetRule(&rule) 
executionConditions.SetScope(scope)
trigger := graphmodelsidentitygovernance.NewTimeBasedAttributeTrigger()
timeBasedAttribute := graphmodels.EMPLOYEEHIREDATE_WORKFLOWTRIGGERTIMEBASEDATTRIBUTE 
trigger.SetTimeBasedAttribute(&timeBasedAttribute) 
offsetInDays := int32(-2)
trigger.SetOffsetInDays(&offsetInDays) 
executionConditions.SetTrigger(trigger)
requestBody.SetExecutionConditions(executionConditions)


task := graphmodelsidentitygovernance.NewTask()
isEnabled := true
task.SetIsEnabled(&isEnabled) 
category := graphmodels.JOINER_LIFECYCLETASKCATEGORY 
task.SetCategory(&category) 
taskDefinitionId := "1b555e50-7f65-41d5-b514-5894a026d10d"
task.SetTaskDefinitionId(&taskDefinitionId) 
displayName := "Generate TAP And Send Email"
task.SetDisplayName(&displayName) 
description := "Generate Temporary Access Pass and send via email to user's manager"
task.SetDescription(&description) 


keyValuePair := graphmodels.NewKeyValuePair()
name := "tapLifetimeMinutes"
keyValuePair.SetName(&name) 
value := "480"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodels.NewKeyValuePair()
name := "tapIsUsableOnce"
keyValuePair1.SetName(&name) 
value := "true"
keyValuePair1.SetValue(&value) 

arguments := []graphmodels.KeyValuePairable {
	keyValuePair,
	keyValuePair1,
}
task.SetArguments(arguments)

tasks := []graphmodelsidentitygovernance.Taskable {
	task,
}
requestBody.SetTasks(tasks)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workflows, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setDisplayName("Onboard pre-hire employee");
workflow.setDescription("Configure pre-hire tasks for onboarding employees before their first day");
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(false);
com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions executionConditions = new com.microsoft.graph.models.identitygovernance.TriggerAndScopeBasedConditions();
executionConditions.setOdataType("microsoft.graph.identityGovernance.triggerAndScopeBasedConditions");
com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet scope = new com.microsoft.graph.models.identitygovernance.RuleBasedSubjectSet();
scope.setOdataType("microsoft.graph.identityGovernance.ruleBasedSubjectSet");
scope.setRule("(department eq 'Sales')");
executionConditions.setScope(scope);
com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger trigger = new com.microsoft.graph.models.identitygovernance.TimeBasedAttributeTrigger();
trigger.setOdataType("microsoft.graph.identityGovernance.timeBasedAttributeTrigger");
trigger.setTimeBasedAttribute(com.microsoft.graph.models.identitygovernance.WorkflowTriggerTimeBasedAttribute.EmployeeHireDate);
trigger.setOffsetInDays(-2);
executionConditions.setTrigger(trigger);
workflow.setExecutionConditions(executionConditions);
LinkedList<com.microsoft.graph.models.identitygovernance.Task> tasks = new LinkedList<com.microsoft.graph.models.identitygovernance.Task>();
com.microsoft.graph.models.identitygovernance.Task task = new com.microsoft.graph.models.identitygovernance.Task();
task.setIsEnabled(true);
task.setCategory(EnumSet.of(com.microsoft.graph.models.identitygovernance.LifecycleTaskCategory.Joiner));
task.setTaskDefinitionId("1b555e50-7f65-41d5-b514-5894a026d10d");
task.setDisplayName("Generate TAP And Send Email");
task.setDescription("Generate Temporary Access Pass and send via email to user's manager");
LinkedList<KeyValuePair> arguments = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("tapLifetimeMinutes");
keyValuePair.setValue("480");
arguments.add(keyValuePair);
KeyValuePair keyValuePair1 = new KeyValuePair();
keyValuePair1.setName("tapIsUsableOnce");
keyValuePair1.setValue("true");
arguments.add(keyValuePair1);
task.setArguments(arguments);
tasks.add(task);
workflow.setTasks(tasks);
com.microsoft.graph.models.identitygovernance.Workflow result = graphClient.identityGovernance().lifecycleWorkflows().workflows().post(workflow);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workflow = {
   displayName: 'Onboard pre-hire employee', 
   description: 'Configure pre-hire tasks for onboarding employees before their first day', 
   isEnabled: true, 
   isSchedulingEnabled: false,
   executionConditions: {
       '@odata.type': 'microsoft.graph.identityGovernance.triggerAndScopeBasedConditions',
        scope: {
            '@odata.type': 'microsoft.graph.identityGovernance.ruleBasedSubjectSet',
            rule: '(department eq \'Sales\')'
        },
        trigger: {
            '@odata.type': 'microsoft.graph.identityGovernance.timeBasedAttributeTrigger',
            timeBasedAttribute: 'employeeHireDate',
            offsetInDays: -2
        }
    }, 
   tasks: [ 
      {
         isEnabled: true, 
         category: 'Joiner',
         taskDefinitionId: '1b555e50-7f65-41d5-b514-5894a026d10d', 
         displayName: 'Generate TAP And Send Email', 
         description: 'Generate Temporary Access Pass and send via email to user\'s manager', 
         arguments: [ 
            { 
                name: 'tapLifetimeMinutes', 
                value: '480' 
            }, 
            { 
                name: 'tapIsUsableOnce', 
                value: 'true' 
            }
          ]
       }  
    ]     
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows')
	.post(workflow);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TriggerAndScopeBasedConditions;
use Microsoft\Graph\Generated\Models\IdentityGovernance\RuleBasedSubjectSet;
use Microsoft\Graph\Generated\Models\IdentityGovernance\TimeBasedAttributeTrigger;
use Microsoft\Graph\Generated\Models\IdentityGovernance\WorkflowTriggerTimeBasedAttribute;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleTaskCategory;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workflow();
$requestBody->setDisplayName('Onboard pre-hire employee');
$requestBody->setDescription('Configure pre-hire tasks for onboarding employees before their first day');
$requestBody->setIsEnabled(true);
$requestBody->setIsSchedulingEnabled(false);
$executionConditions = new TriggerAndScopeBasedConditions();
$executionConditions->setOdataType('microsoft.graph.identityGovernance.triggerAndScopeBasedConditions');
$executionConditionsScope = new RuleBasedSubjectSet();
$executionConditionsScope->setOdataType('microsoft.graph.identityGovernance.ruleBasedSubjectSet');
$executionConditionsScope->setRule('(department eq \'Sales\')');
$executionConditions->setScope($executionConditionsScope);
$executionConditionsTrigger = new TimeBasedAttributeTrigger();
$executionConditionsTrigger->setOdataType('microsoft.graph.identityGovernance.timeBasedAttributeTrigger');
$executionConditionsTrigger->setTimeBasedAttribute(new WorkflowTriggerTimeBasedAttribute('employeeHireDate'));
$executionConditionsTrigger->setOffsetInDays(-2);
$executionConditions->setTrigger($executionConditionsTrigger);
$requestBody->setExecutionConditions($executionConditions);
$tasksTask1 = new Task();
$tasksTask1->setIsEnabled(true);
$tasksTask1->setCategory(new LifecycleTaskCategory('joiner'));
$tasksTask1->setTaskDefinitionId('1b555e50-7f65-41d5-b514-5894a026d10d');
$tasksTask1->setDisplayName('Generate TAP And Send Email');
$tasksTask1->setDescription('Generate Temporary Access Pass and send via email to user\'s manager');
$argumentsKeyValuePair1 = new KeyValuePair();
$argumentsKeyValuePair1->setName('tapLifetimeMinutes');
$argumentsKeyValuePair1->setValue('480');
$argumentsArray []= $argumentsKeyValuePair1;
$argumentsKeyValuePair2 = new KeyValuePair();
$argumentsKeyValuePair2->setName('tapIsUsableOnce');
$argumentsKeyValuePair2->setValue('true');
$argumentsArray []= $argumentsKeyValuePair2;
$tasksTask1->setArguments($argumentsArray);

$tasksArray []= $tasksTask1;
$requestBody->setTasks($tasksArray);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Onboard pre-hire employee"
	description = "Configure pre-hire tasks for onboarding employees before their first day"
	isEnabled = $true
	isSchedulingEnabled = $false
	executionConditions = @{
		"@odata.type" = "microsoft.graph.identityGovernance.triggerAndScopeBasedConditions"
		scope = @{
			"@odata.type" = "microsoft.graph.identityGovernance.ruleBasedSubjectSet"
			rule = "(department eq 'Sales')"
		}
		trigger = @{
			"@odata.type" = "microsoft.graph.identityGovernance.timeBasedAttributeTrigger"
			timeBasedAttribute = "employeeHireDate"
			offsetInDays = 
		}
	}
	tasks = @(
		@{
			isEnabled = $true
			category = "Joiner"
			taskDefinitionId = "1b555e50-7f65-41d5-b514-5894a026d10d"
			displayName = "Generate TAP And Send Email"
			description = "Generate Temporary Access Pass and send via email to user's manager"
			arguments = @(
				@{
					name = "tapLifetimeMinutes"
					value = "480"
				}
				@{
					name = "tapIsUsableOnce"
					value = "true"
				}
			)
		}
	)
}

New-MgIdentityGovernanceLifecycleWorkflow -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_governance.workflow import Workflow
from msgraph.generated.models.identity_governance.trigger_and_scope_based_conditions import TriggerAndScopeBasedConditions
from msgraph.generated.models.identity_governance.rule_based_subject_set import RuleBasedSubjectSet
from msgraph.generated.models.identity_governance.time_based_attribute_trigger import TimeBasedAttributeTrigger
from msgraph.generated.models.workflow_trigger_time_based_attribute import WorkflowTriggerTimeBasedAttribute
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.lifecycle_task_category import LifecycleTaskCategory
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workflow(
	display_name = "Onboard pre-hire employee",
	description = "Configure pre-hire tasks for onboarding employees before their first day",
	is_enabled = True,
	is_scheduling_enabled = False,
	execution_conditions = TriggerAndScopeBasedConditions(
		odata_type = "microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
		scope = RuleBasedSubjectSet(
			odata_type = "microsoft.graph.identityGovernance.ruleBasedSubjectSet",
			rule = "(department eq 'Sales')",
		),
		trigger = TimeBasedAttributeTrigger(
			odata_type = "microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
			time_based_attribute = WorkflowTriggerTimeBasedAttribute.EmployeeHireDate,
			offset_in_days = -2,
		),
	),
	tasks = [
		Task(
			is_enabled = True,
			category = LifecycleTaskCategory.Joiner,
			task_definition_id = "1b555e50-7f65-41d5-b514-5894a026d10d",
			display_name = "Generate TAP And Send Email",
			description = "Generate Temporary Access Pass and send via email to user's manager",
			arguments = [
				KeyValuePair(
					name = "tapLifetimeMinutes",
					value = "480",
				),
				KeyValuePair(
					name = "tapIsUsableOnce",
					value = "true",
				),
			],
		),
	],
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows/$entity",
    "category": "joiner",
    "description": "Configure pre-hire tasks for onboarding employees before their first day",
    "displayName": "Onboard pre-hire employee",
    "lastModifiedDateTime": "2024-03-04T07:45:14.3410141Z",
    "createdDateTime": "2024-03-04T07:45:14.3410017Z",
    "deletedDateTime": null,
    "id": "ea71190c-075a-4ae7-9bca-34abf3b7b056",
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "nextScheduleRunDateTime": null,
    "version": 1,
    "executionConditions": {
        "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
        "scope": {
            "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
            "rule": "(department eq 'Sales')"
        },
        "trigger": {
            "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
            "timeBasedAttribute": "employeeHireDate",
            "offsetInDays": -2
        }
    }
}
```

## Run the workflow

Because the workflow isn't scheduled, you must run it manually. In the following request, the user that's the target of the workflow is identified by ID `8930f0c7-cdd7-4885-9260-3b4a8111de5c`. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/activate

{
    "subjects": [
        {
            "id": "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceActivate;
using Microsoft.Graph.Models;

var requestBody = new ActivatePostRequestBody
{
	Subjects = new List<User>
	{
		new User
		{
			Id = "8930f0c7-cdd7-4885-9260-3b4a8111de5c",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceActivate.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphidentitygovernance.NewActivatePostRequestBody()


user := graphmodels.NewUser()
id := "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
user.SetId(&id) 

subjects := []graphmodels.Userable {
	user,
}
requestBody.SetSubjects(subjects)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernanceActivate().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivate.ActivatePostRequestBody activatePostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivate.ActivatePostRequestBody();
LinkedList<User> subjects = new LinkedList<User>();
User user = new User();
user.setId("8930f0c7-cdd7-4885-9260-3b4a8111de5c");
subjects.add(user);
activatePostRequestBody.setSubjects(subjects);
graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceActivate().post(activatePostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const activate = {
    subjects: [
        {
            id: '8930f0c7-cdd7-4885-9260-3b4a8111de5c'
        }
    ]
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/activate')
	.post(activate);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceActivate\ActivatePostRequestBody;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ActivatePostRequestBody();
$subjectsUser1 = new User();
$subjectsUser1->setId('8930f0c7-cdd7-4885-9260-3b4a8111de5c');
$subjectsArray []= $subjectsUser1;
$requestBody->setSubjects($subjectsArray);


$graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceActivate()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	subjects = @(
		@{
			id = "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
		}
	)
}

Initialize-MgIdentityGovernanceLifecycleWorkflow -WorkflowId $workflowId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_activate.activate_post_request_body import ActivatePostRequestBody
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ActivatePostRequestBody(
	subjects = [
		User(
			id = "8930f0c7-cdd7-4885-9260-3b4a8111de5c",
		),
	],
)

await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_activate.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Check tasks and workflow status

You can monitor the status of workflows and their associated tasks at three levels.

- Monitor tasks at the user level.
- Monitor the high-level summary of user-level results for a workflow within a specified period.
- Retrieve the detailed log of all tasks executed for a specific user in the workflow.

### Option 1: Monitor tasks for a workflow at the user level

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/userProcessingResults
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].UserProcessingResults.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
userProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").UserProcessingResults().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.UserProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").userProcessingResults().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let userProcessingResults = await client.api('/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/userProcessingResults')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->userProcessingResults()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowUserProcessingResult -WorkflowId $workflowId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').user_processing_results.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('ea71190c-075a-4ae7-9bca-34abf3b7b056')/userProcessingResults",
    "value": [
        {
            "id": "5772d894-3bcf-4d1c-9cfc-8c182331215b",
            "completedDateTime": "2024-03-04T08:07:23.2591226Z",
            "failedTasksCount": 0,
            "processingStatus": "completed",
            "scheduledDateTime": "2024-03-04T08:07:03.8706523Z",
            "startedDateTime": "2024-03-04T08:07:09.4670969Z",
            "totalTasksCount": 1,
            "totalUnprocessedTasksCount": 0,
            "workflowExecutionType": "onDemand",
            "workflowVersion": 1,
            "subject": {
                "id": "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
            }
        }
    ]
}
```

### Option 2: Get the aggregate high-level summary of the user-level results for a workflow, within a specified period

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/userProcessingResults/summary(startDateTime=2024-03-01T00:00:00Z,endDateTime=2024-03-30T00:00:00Z)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].UserProcessingResults.MicrosoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(DateTimeOffset.Parse("{endDateTime}"),DateTimeOffset.Parse("{startDateTime}")).GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
startDateTime , err := time.Parse(time.RFC3339, "{startDateTime}")
endDateTime , err := time.Parse(time.RFC3339, "{endDateTime}")
microsoftGraphIdentityGovernanceSummary, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").UserProcessingResults().MicrosoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(&startDateTime, &endDateTime).Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").userProcessingResults().microsoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(OffsetDateTime.parse("{endDateTime}"), OffsetDateTime.parse("{startDateTime}")).get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let userSummary = await client.api('/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/userProcessingResults/summary(startDateTime=2024-03-01T00:00:00Z,endDateTime=2024-03-30T00:00:00Z)')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->userProcessingResults()->microsoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(new \DateTime('{endDateTime}'),new \DateTime('{startDateTime}'))->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Invoke-MgSummaryIdentityGovernanceLifecycleWorkflowUserProcessingResult -WorkflowId $workflowId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').user_processing_results.microsoft_graph_identity_governance_summary_with_start_date_time_with_end_date_time("{endDateTime}","{startDateTime}").get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.identityGovernance.userSummary",
    "failedTasks": 0,
    "failedUsers": 0,
    "successfulUsers": 1,
    "totalTasks": 1,
    "totalUsers": 1
}
```

### Option 3: Retrieve the detailed log of all tasks that were executed for a specific user in the workflow

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/userProcessingResults/5772d894-3bcf-4d1c-9cfc-8c182331215b/taskProcessingResults
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].UserProcessingResults["{userProcessingResult-id}"].TaskProcessingResults.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").UserProcessingResults().ByUserProcessingResultId("userProcessingResult-id").TaskProcessingResults().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").userProcessingResults().byUserProcessingResultId("{userProcessingResult-id}").taskProcessingResults().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskProcessingResults = await client.api('/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056/userProcessingResults/5772d894-3bcf-4d1c-9cfc-8c182331215b/taskProcessingResults')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->userProcessingResults()->byUserProcessingResultId('userProcessingResult-id')->taskProcessingResults()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowUserProcessingResultTaskProcessingResult -WorkflowId $workflowId -UserProcessingResultId $userProcessingResultId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').user_processing_results.by_user_processing_result_id('userProcessingResult-id').task_processing_results.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('ea71190c-075a-4ae7-9bca-34abf3b7b056')/userProcessingResults('5772d894-3bcf-4d1c-9cfc-8c182331215b')/taskProcessingResults",
    "value": [
        {
            "completedDateTime": "2024-03-04T08:07:15.9906441Z",
            "createdDateTime": "2024-03-04T08:07:09.8072395Z",
            "id": "227c85e4-7b84-461f-8df5-c347c2435eb2",
            "processingStatus": "completed",
            "startedDateTime": "2024-03-04T08:07:11.1595421Z",
            "failureReason": null,
            "subject": {
                "id": "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
            },
            "task": {
                "category": "joiner",
                "continueOnError": false,
                "description": "Generate Temporary Access Pass and send via email to user's manager",
                "displayName": "Generate TAP And Send Email",
                "executionSequence": 1,
                "id": "8b9b47c0-957b-4a52-8f2d-816e59c40fd2",
                "isEnabled": true,
                "taskDefinitionId": "1b555e50-7f65-41d5-b514-5894a026d10d",
                "arguments": [
                    {
                        "name": "tapLifetimeMinutes",
                        "value": "480"
                    },
                    {
                        "name": "tapIsUsableOnce",
                        "value": "true"
                    }
                ]
            }
        }
    ]
}
```

## \[Optional\] Schedule the workflow to run automatically

After running your workflow on-demand and confirming it works, enable the workflow to run automatically on a tenant-defined schedule. Run the following request.

The request returns a `204 No Content` response. When a workflow is scheduled, the Lifecycle Workflows engine checks every three hours for user objects that match the execution condition and executes the configured tasks. You can customize this recurrence from one to 24 hours.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
PATCH https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056
Content-type: application/json

{
    "isEnabled": true,
    "isSchedulingEnabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.IdentityGovernance;

var requestBody = new Workflow
{
	IsEnabled = true,
	IsSchedulingEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  //other-imports
)

requestBody := graphmodelsidentitygovernance.NewWorkflow()
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := true
requestBody.SetIsSchedulingEnabled(&isSchedulingEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workflows, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.Workflow workflow = new com.microsoft.graph.models.identitygovernance.Workflow();
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(true);
com.microsoft.graph.models.identitygovernance.Workflow result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").patch(workflow);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workflow = {
    isEnabled: true,
    isSchedulingEnabled: true
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/ea71190c-075a-4ae7-9bca-34abf3b7b056')
	.update(workflow);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workflow();
$requestBody->setIsEnabled(true);
$requestBody->setIsSchedulingEnabled(true);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	isEnabled = $true
	isSchedulingEnabled = $true
}

Update-MgIdentityGovernanceLifecycleWorkflow -WorkflowId $workflowId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_governance.workflow import Workflow
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workflow(
	is_enabled = True,
	is_scheduling_enabled = True,
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Related content

- [Automate employee onboarding tasks before their first day of work by using the Microsoft Entra admin center](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-onboard-custom-workflow-portal)
- [Overview of Microsoft Entra Lifecycle Workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-overview)
- [Overview of reporting in Microsoft Entra Lifecycle Workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-reporting-overview)
