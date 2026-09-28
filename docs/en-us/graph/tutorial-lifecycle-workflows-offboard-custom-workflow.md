<!-- Source: https://learn.microsoft.com/en-us/graph/tutorial-lifecycle-workflows-offboard-custom-workflow -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Complete employee offboarding tasks in real time on their last day of work using Lifecycle Workflows APIs

This tutorial provides step-by-step guidance for completing a real time employee termination with Lifecycle Workflows APIs in Microsoft Graph. In this scenario, the employee termination isn't scheduled. See [Schedule employee offboarding tasks with Lifecycle Workflows APIs](https://learn.microsoft.com/en-us/graph/tutorial-lifecycle-workflows-scheduled-leaver) for a scheduled scenario.

In this tutorial, you learn how to:

- Configure a lifecycle workflow to run the following tasks in sequence:

  - Remove the user from all groups
  - Remove user from all Teams
  - Delete user account

- Monitor the status of the workflow and its associated tasks.

## Prerequisites

To complete this tutorial, you need these resources and privileges:

- This feature requires Microsoft Entra ID Governance licenses. To find the right license for your requirements, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals).
- Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) to call Microsoft Graph with an account that has at least the *Lifecycle Administrator* Microsoft Entra role.
- Grant yourself the *LifecycleWorkflows.ReadWrite.All* Microsoft Graph delegated permission.
- Create a test user account that you use to represent an employee leaving your organization. This test user account is deleted when the workflow runs. Assign licenses and Teams memberships to the test user account.

## Create a "leaver" workflow

### Request

The following request creates an offboarding workflow with these settings:

- It can be run on-demand but not on schedule.
- The workflow doesn't include execution conditions. Execution conditions, even when defined, are bypassed for workflows that are run on-demand.
- Three workflow tasks are enabled to run in sequence: the user is removed from all groups, then removed from all teams, then their user account is deleted.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/LifecycleWorkflows/workflows
Content-type: application/json

{
    "category": "Leaver",
    "displayName": "Real-time employee termination",
    "description": "Execute real-time termination tasks for employees on their last day of work",
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "executionConditions":{
        "@odata.type":"#microsoft.graph.identityGovernance.onDemandExecutionOnly"
    },
    "tasks": [
        {
            "continueOnError": false,
            "description": "Remove user from all Azure AD groups memberships",
            "displayName": "Remove user from all groups",
            "executionSequence": 1,
            "isEnabled": true,
            "taskDefinitionId": "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
            "arguments": []
        },
        {
            "continueOnError": false,
            "description": "Remove user from all Teams memberships",
            "displayName": "Remove user from all Teams",
            "executionSequence": 2,
            "isEnabled": true,
            "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
            "arguments": []
        },
        {
            "continueOnError": false,
            "description": "Delete user account in Azure AD",
            "displayName": "Delete User Account",
            "executionSequence": 3,
            "isEnabled": true,
            "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
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
	Category = LifecycleWorkflowCategory.Leaver,
	DisplayName = "Real-time employee termination",
	Description = "Execute real-time termination tasks for employees on their last day of work",
	IsEnabled = true,
	IsSchedulingEnabled = false,
	ExecutionConditions = new OnDemandExecutionOnly
	{
		OdataType = "#microsoft.graph.identityGovernance.onDemandExecutionOnly",
	},
	Tasks = new List<TaskObject>
	{
		new TaskObject
		{
			ContinueOnError = false,
			Description = "Remove user from all Azure AD groups memberships",
			DisplayName = "Remove user from all groups",
			ExecutionSequence = 1,
			IsEnabled = true,
			TaskDefinitionId = "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
			Arguments = new List<KeyValuePair>
			{
			},
		},
		new TaskObject
		{
			ContinueOnError = false,
			Description = "Remove user from all Teams memberships",
			DisplayName = "Remove user from all Teams",
			ExecutionSequence = 2,
			IsEnabled = true,
			TaskDefinitionId = "81f7b200-2816-4b3b-8c5d-dc556f07b024",
			Arguments = new List<KeyValuePair>
			{
			},
		},
		new TaskObject
		{
			ContinueOnError = false,
			Description = "Delete user account in Azure AD",
			DisplayName = "Delete User Account",
			ExecutionSequence = 3,
			IsEnabled = true,
			TaskDefinitionId = "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
			Arguments = new List<KeyValuePair>
			{
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
category := graphmodels.LEAVER_LIFECYCLEWORKFLOWCATEGORY 
requestBody.SetCategory(&category) 
displayName := "Real-time employee termination"
requestBody.SetDisplayName(&displayName) 
description := "Execute real-time termination tasks for employees on their last day of work"
requestBody.SetDescription(&description) 
isEnabled := true
requestBody.SetIsEnabled(&isEnabled) 
isSchedulingEnabled := false
requestBody.SetIsSchedulingEnabled(&isSchedulingEnabled) 
executionConditions := graphmodelsidentitygovernance.NewOnDemandExecutionOnly()
requestBody.SetExecutionConditions(executionConditions)


task := graphmodelsidentitygovernance.NewTask()
continueOnError := false
task.SetContinueOnError(&continueOnError) 
description := "Remove user from all Azure AD groups memberships"
task.SetDescription(&description) 
displayName := "Remove user from all groups"
task.SetDisplayName(&displayName) 
executionSequence := int32(1)
task.SetExecutionSequence(&executionSequence) 
isEnabled := true
task.SetIsEnabled(&isEnabled) 
taskDefinitionId := "b3a31406-2a15-4c9a-b25b-a658fa5f07fc"
task.SetTaskDefinitionId(&taskDefinitionId) 
arguments := []graphmodels.KeyValuePairable {

}
task.SetArguments(arguments)
task1 := graphmodelsidentitygovernance.NewTask()
continueOnError := false
task1.SetContinueOnError(&continueOnError) 
description := "Remove user from all Teams memberships"
task1.SetDescription(&description) 
displayName := "Remove user from all Teams"
task1.SetDisplayName(&displayName) 
executionSequence := int32(2)
task1.SetExecutionSequence(&executionSequence) 
isEnabled := true
task1.SetIsEnabled(&isEnabled) 
taskDefinitionId := "81f7b200-2816-4b3b-8c5d-dc556f07b024"
task1.SetTaskDefinitionId(&taskDefinitionId) 
arguments := []graphmodels.KeyValuePairable {

}
task1.SetArguments(arguments)
task2 := graphmodelsidentitygovernance.NewTask()
continueOnError := false
task2.SetContinueOnError(&continueOnError) 
description := "Delete user account in Azure AD"
task2.SetDescription(&description) 
displayName := "Delete User Account"
task2.SetDisplayName(&displayName) 
executionSequence := int32(3)
task2.SetExecutionSequence(&executionSequence) 
isEnabled := true
task2.SetIsEnabled(&isEnabled) 
taskDefinitionId := "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff"
task2.SetTaskDefinitionId(&taskDefinitionId) 
arguments := []graphmodels.KeyValuePairable {

}
task2.SetArguments(arguments)

tasks := []graphmodelsidentitygovernance.Taskable {
	task,
	task1,
	task2,
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
workflow.setCategory(com.microsoft.graph.models.identitygovernance.LifecycleWorkflowCategory.Leaver);
workflow.setDisplayName("Real-time employee termination");
workflow.setDescription("Execute real-time termination tasks for employees on their last day of work");
workflow.setIsEnabled(true);
workflow.setIsSchedulingEnabled(false);
com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly executionConditions = new com.microsoft.graph.models.identitygovernance.OnDemandExecutionOnly();
executionConditions.setOdataType("#microsoft.graph.identityGovernance.onDemandExecutionOnly");
workflow.setExecutionConditions(executionConditions);
LinkedList<com.microsoft.graph.models.identitygovernance.Task> tasks = new LinkedList<com.microsoft.graph.models.identitygovernance.Task>();
com.microsoft.graph.models.identitygovernance.Task task = new com.microsoft.graph.models.identitygovernance.Task();
task.setContinueOnError(false);
task.setDescription("Remove user from all Azure AD groups memberships");
task.setDisplayName("Remove user from all groups");
task.setExecutionSequence(1);
task.setIsEnabled(true);
task.setTaskDefinitionId("b3a31406-2a15-4c9a-b25b-a658fa5f07fc");
LinkedList<KeyValuePair> arguments = new LinkedList<KeyValuePair>();
task.setArguments(arguments);
tasks.add(task);
com.microsoft.graph.models.identitygovernance.Task task1 = new com.microsoft.graph.models.identitygovernance.Task();
task1.setContinueOnError(false);
task1.setDescription("Remove user from all Teams memberships");
task1.setDisplayName("Remove user from all Teams");
task1.setExecutionSequence(2);
task1.setIsEnabled(true);
task1.setTaskDefinitionId("81f7b200-2816-4b3b-8c5d-dc556f07b024");
LinkedList<KeyValuePair> arguments1 = new LinkedList<KeyValuePair>();
task1.setArguments(arguments1);
tasks.add(task1);
com.microsoft.graph.models.identitygovernance.Task task2 = new com.microsoft.graph.models.identitygovernance.Task();
task2.setContinueOnError(false);
task2.setDescription("Delete user account in Azure AD");
task2.setDisplayName("Delete User Account");
task2.setExecutionSequence(3);
task2.setIsEnabled(true);
task2.setTaskDefinitionId("8d18588d-9ad3-4c0f-99d0-ec215f0e3dff");
LinkedList<KeyValuePair> arguments2 = new LinkedList<KeyValuePair>();
task2.setArguments(arguments2);
tasks.add(task2);
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
    category: 'Leaver',
    displayName: 'Real-time employee termination',
    description: 'Execute real-time termination tasks for employees on their last day of work',
    isEnabled: true,
    isSchedulingEnabled: false,
    executionConditions: {
        '@odata.type':'#microsoft.graph.identityGovernance.onDemandExecutionOnly'
    },
    tasks: [
        {
            continueOnError: false,
            description: 'Remove user from all Azure AD groups memberships',
            displayName: 'Remove user from all groups',
            executionSequence: 1,
            isEnabled: true,
            taskDefinitionId: 'b3a31406-2a15-4c9a-b25b-a658fa5f07fc',
            arguments: []
        },
        {
            continueOnError: false,
            description: 'Remove user from all Teams memberships',
            displayName: 'Remove user from all Teams',
            executionSequence: 2,
            isEnabled: true,
            taskDefinitionId: '81f7b200-2816-4b3b-8c5d-dc556f07b024',
            arguments: []
        },
        {
            continueOnError: false,
            description: 'Delete user account in Azure AD',
            displayName: 'Delete User Account',
            executionSequence: 3,
            isEnabled: true,
            taskDefinitionId: '8d18588d-9ad3-4c0f-99d0-ec215f0e3dff',
            arguments: []
        }
    ]
};

await client.api('/identityGovernance/LifecycleWorkflows/workflows')
	.post(workflow);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Workflow;
use Microsoft\Graph\Generated\Models\IdentityGovernance\LifecycleWorkflowCategory;
use Microsoft\Graph\Generated\Models\IdentityGovernance\OnDemandExecutionOnly;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Task;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Workflow();
$requestBody->setCategory(new LifecycleWorkflowCategory('leaver'));
$requestBody->setDisplayName('Real-time employee termination');
$requestBody->setDescription('Execute real-time termination tasks for employees on their last day of work');
$requestBody->setIsEnabled(true);
$requestBody->setIsSchedulingEnabled(false);
$executionConditions = new OnDemandExecutionOnly();
$executionConditions->setOdataType('#microsoft.graph.identityGovernance.onDemandExecutionOnly');
$requestBody->setExecutionConditions($executionConditions);
$tasksTask1 = new Task();
$tasksTask1->setContinueOnError(false);
$tasksTask1->setDescription('Remove user from all Azure AD groups memberships');
$tasksTask1->setDisplayName('Remove user from all groups');
$tasksTask1->setExecutionSequence(1);
$tasksTask1->setIsEnabled(true);
$tasksTask1->setTaskDefinitionId('b3a31406-2a15-4c9a-b25b-a658fa5f07fc');
$tasksTask1->setArguments([	]);
$tasksArray []= $tasksTask1;
$tasksTask2 = new Task();
$tasksTask2->setContinueOnError(false);
$tasksTask2->setDescription('Remove user from all Teams memberships');
$tasksTask2->setDisplayName('Remove user from all Teams');
$tasksTask2->setExecutionSequence(2);
$tasksTask2->setIsEnabled(true);
$tasksTask2->setTaskDefinitionId('81f7b200-2816-4b3b-8c5d-dc556f07b024');
$tasksTask2->setArguments([	]);
$tasksArray []= $tasksTask2;
$tasksTask3 = new Task();
$tasksTask3->setContinueOnError(false);
$tasksTask3->setDescription('Delete user account in Azure AD');
$tasksTask3->setDisplayName('Delete User Account');
$tasksTask3->setExecutionSequence(3);
$tasksTask3->setIsEnabled(true);
$tasksTask3->setTaskDefinitionId('8d18588d-9ad3-4c0f-99d0-ec215f0e3dff');
$tasksTask3->setArguments([	]);
$tasksArray []= $tasksTask3;
$requestBody->setTasks($tasksArray);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	category = "Leaver"
	displayName = "Real-time employee termination"
	description = "Execute real-time termination tasks for employees on their last day of work"
	isEnabled = $true
	isSchedulingEnabled = $false
	executionConditions = @{
		"@odata.type" = "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
	}
	tasks = @(
		@{
			continueOnError = $false
			description = "Remove user from all Azure AD groups memberships"
			displayName = "Remove user from all groups"
			executionSequence = 1
			isEnabled = $true
			taskDefinitionId = "b3a31406-2a15-4c9a-b25b-a658fa5f07fc"
			arguments = @(
			)
		}
		@{
			continueOnError = $false
			description = "Remove user from all Teams memberships"
			displayName = "Remove user from all Teams"
			executionSequence = 2
			isEnabled = $true
			taskDefinitionId = "81f7b200-2816-4b3b-8c5d-dc556f07b024"
			arguments = @(
			)
		}
		@{
			continueOnError = $false
			description = "Delete user account in Azure AD"
			displayName = "Delete User Account"
			executionSequence = 3
			isEnabled = $true
			taskDefinitionId = "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff"
			arguments = @(
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
from msgraph.generated.models.lifecycle_workflow_category import LifecycleWorkflowCategory
from msgraph.generated.models.identity_governance.on_demand_execution_only import OnDemandExecutionOnly
from msgraph.generated.models.identity_governance.task import Task
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Workflow(
	category = LifecycleWorkflowCategory.Leaver,
	display_name = "Real-time employee termination",
	description = "Execute real-time termination tasks for employees on their last day of work",
	is_enabled = True,
	is_scheduling_enabled = False,
	execution_conditions = OnDemandExecutionOnly(
		odata_type = "#microsoft.graph.identityGovernance.onDemandExecutionOnly",
	),
	tasks = [
		Task(
			continue_on_error = False,
			description = "Remove user from all Azure AD groups memberships",
			display_name = "Remove user from all groups",
			execution_sequence = 1,
			is_enabled = True,
			task_definition_id = "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
			arguments = [
			],
		),
		Task(
			continue_on_error = False,
			description = "Remove user from all Teams memberships",
			display_name = "Remove user from all Teams",
			execution_sequence = 2,
			is_enabled = True,
			task_definition_id = "81f7b200-2816-4b3b-8c5d-dc556f07b024",
			arguments = [
			],
		),
		Task(
			continue_on_error = False,
			description = "Delete user account in Azure AD",
			display_name = "Delete User Account",
			execution_sequence = 3,
			is_enabled = True,
			task_definition_id = "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
			arguments = [
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/lifecycleWorkflows/workflows/$entity",
    "category": "leaver",
    "description": "Execute real-time termination tasks for employees on their last day of work",
    "displayName": "Real-time employee termination",
    "lastModifiedDateTime": "2024-03-03T08:33:01.0619748Z",
    "createdDateTime": "2024-03-03T08:33:01.0619653Z",
    "deletedDateTime": null,
    "id": "368dfba3-2303-4e02-b258-87d742187e1b",
    "isEnabled": true,
    "isSchedulingEnabled": false,
    "nextScheduleRunDateTime": null,
    "version": 1,
    "executionConditions": {
        "@odata.type": "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
    }
}
```

## Run the workflow

In the following request, the user that's the target of the workflow is identified by ID `8930f0c7-cdd7-4885-9260-3b4a8111de5c`.

The request returns a `204 No Content` response.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/activate

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

await client.api('/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/activate')
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

Monitor the status of the workflows and tasks at three levels:

- Monitor tasks at the user level.
- Monitor the aggregate high-level summary of the user-level results for a workflow, within a specified period.
- Retrieve the detailed log of all tasks that were executed for a specific user in the workflow.

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
GET https://graph.microsoft.com/v1.0/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/userProcessingResults
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

let userProcessingResults = await client.api('/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/userProcessingResults')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/lifecycleWorkflows/workflows('368dfba3-2303-4e02-b258-87d742187e1b')/userProcessingResults",
    "value": [
        {
            "id": "bc5b9d36-55fb-4036-8551-582668a6b78e",
            "completedDateTime": "2024-03-03T08:37:47.3197648Z",
            "failedTasksCount": 0,
            "processingStatus": "completed",
            "scheduledDateTime": "2024-03-03T08:37:28.3040665Z",
            "startedDateTime": "2024-03-03T08:37:32.1018797Z",
            "totalTasksCount": 3,
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
GET https://graph.microsoft.com/v1.0/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/userProcessingResults/summary(startDateTime=2022-10-01T00:00:00Z,endDateTime=2022-10-30T00:00:00Z)
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

let userSummary = await client.api('/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/userProcessingResults/summary(startDateTime=2022-10-01T00:00:00Z,endDateTime=2022-10-30T00:00:00Z)')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.identityGovernance.userSummary",
    "failedTasks": 0,
    "failedUsers": 0,
    "successfulUsers": 1,
    "totalTasks": 3,
    "totalUsers": 1
}
```

### Option 3: Retrieve the detailed log of all tasks that were executed for a specific user in the workflow

#### Request

Retrieve the detailed log of all tasks executed for a specific user in the workflow.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/userProcessingResults/bc5b9d36-55fb-4036-8551-582668a6b78e/taskProcessingResults
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

let taskProcessingResults = await client.api('/identityGovernance/LifecycleWorkflows/workflows/368dfba3-2303-4e02-b258-87d742187e1b/userProcessingResults/bc5b9d36-55fb-4036-8551-582668a6b78e/taskProcessingResults')
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#identityGovernance/lifecycleWorkflows/workflows('368dfba3-2303-4e02-b258-87d742187e1b')/userProcessingResults('bc5b9d36-55fb-4036-8551-582668a6b78e')/taskProcessingResults",
    "value": [
        {
            "completedDateTime": "2024-03-03T08:37:37.1440809Z",
            "createdDateTime": "2024-03-03T08:37:32.6985496Z",
            "id": "0819ee66-f85c-49a2-bdbd-3bbdbb3c1797",
            "processingStatus": "completed",
            "startedDateTime": "2024-03-03T08:37:36.2260254Z",
            "failureReason": null,
            "subject": {
                "id": "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Remove user from all Azure AD groups memberships",
                "displayName": "Remove user from all groups",
                "executionSequence": 1,
                "id": "ab400768-ff1e-4a2f-ac0e-bae5d8419613",
                "isEnabled": true,
                "taskDefinitionId": "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
                "arguments": []
            }
        },
        {
            "completedDateTime": "2024-03-03T08:37:42.8173083Z",
            "createdDateTime": "2024-03-03T08:37:32.76041Z",
            "id": "f1e16080-0117-41ba-9632-74eb60a4b005",
            "processingStatus": "completed",
            "startedDateTime": "2024-03-03T08:37:38.383087Z",
            "failureReason": null,
            "subject": {
                "id": "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Remove user from all Teams memberships",
                "displayName": "Remove user from all Teams",
                "executionSequence": 2,
                "id": "b49e306a-17ad-4bed-89cb-f312b9d30eb3",
                "isEnabled": true,
                "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                "arguments": []
            }
        },
        {
            "completedDateTime": "2024-03-03T08:37:46.8305324Z",
            "createdDateTime": "2024-03-03T08:37:33.0279549Z",
            "id": "21d40600-259a-4581-a011-0a56d2ee6e7a",
            "processingStatus": "completed",
            "startedDateTime": "2024-03-03T08:37:46.3131624Z",
            "failureReason": null,
            "subject": {
                "id": "8930f0c7-cdd7-4885-9260-3b4a8111de5c"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Delete user account in Azure AD",
                "displayName": "Delete User Account",
                "executionSequence": 3,
                "id": "ce568616-5615-4783-a519-6bec9f13514e",
                "isEnabled": true,
                "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
                "arguments": []
            }
        }
    ]
}
```

## Related content

- [Execute employee offboarding tasks in real-time on their last day of work with the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/id-governance/tutorial-offboard-custom-workflow-portal)
- [Overview of Microsoft Entra Lifecycle Workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-overview)
- [Overview of reporting in Microsoft Entra Lifecycle Workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-reporting-overview)
