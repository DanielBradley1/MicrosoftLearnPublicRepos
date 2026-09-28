<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-taskprocessingresult-resume?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# taskProcessingResult: resume

Namespace: microsoft.graph.identityGovernance

Resume a [taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) that's `inProgress`. In the default case, an Azure Logic Apps system-assigned managed identity calls this API. For more information, see [Lifecycle Workflows extensibility approach](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-extensibility).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Lifecycle Workflows Administrator* is the least privileged role supported for this operation.

Important

The following applies to app-only access to better follow the principle of least privilege:

> - Apps specified in `authorizedApps` within the [customTaskExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackconfiguration?view=graph-rest-1.0) of the [custom task extension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) are allowed to resume the task processing result without application permissions or role assignments.
> - The app specified in `resourceId` within the [azureAdTokenAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackconfiguration?view=graph-rest-1.0) of the [custom task extension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) is allowed to resume the task processing result without an application permission or role assignment.

## HTTP request

```http
POST /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/tasks/{taskId}/taskProcessingResults/{taskProcessingResultsId}/resume
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a [custom extension callout response](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutresponse?view=graph-rest-1.0).

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| source | String | The source of the `taskProcessingResult`. |
| type | String | The type of the `taskProcessingResult`. |
| data | [microsoft.graph.identityGovernance.customTaskExtensionCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackdata?view=graph-rest-1.0) | The customtaskextensionCallbackData of the taskProcessingResult. The logic app returns an operation status of whether or not it successfully ran. The taskprocessingresult resumes based on how the task was designed in the workflow. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/4f36da05-5df8-457d-adb3-b132e7b59571/tasks/e07dcdb2-0a77-4ee3-8645-3801fbe1cf9f/taskProcessingResults/6e1ec336-8d06-4386-a377-79dbab1a2eb6/resume
Content-Type: application/json
Content-length: 155

{
  "data": {
    "operationStatus": "Completed"
  },
  "source": "sample",
  "type": "lifecycleEvent"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.Tasks.Item.TaskProcessingResults.Item.MicrosoftGraphIdentityGovernanceResume;
using Microsoft.Graph.Models.IdentityGovernance;

var requestBody = new ResumePostRequestBody
{
	Data = new CustomTaskExtensionCallbackData
	{
		OperationStatus = CustomTaskExtensionOperationStatus.Completed,
	},
	Source = "sample",
	Type = "lifecycleEvent",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].Tasks["{task-id}"].TaskProcessingResults["{taskProcessingResult-id}"].MicrosoftGraphIdentityGovernanceResume.PostAsync(requestBody);
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
	  //other-imports
)

requestBody := graphidentitygovernance.NewResumePostRequestBody()
data := graphmodelsidentitygovernance.NewCustomTaskExtensionCallbackData()
operationStatus := graphmodels.COMPLETED_CUSTOMTASKEXTENSIONOPERATIONSTATUS 
data.SetOperationStatus(&operationStatus) 
requestBody.SetData(data)
source := "sample"
requestBody.SetSource(&source) 
type := "lifecycleEvent"
requestBody.SetType(&type) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").Tasks().ByTaskId("task-id").TaskProcessingResults().ByTaskProcessingResultId("taskProcessingResult-id").MicrosoftGraphIdentityGovernanceResume().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.tasks.item.taskprocessingresults.item.microsoftgraphidentitygovernanceresume.ResumePostRequestBody resumePostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.tasks.item.taskprocessingresults.item.microsoftgraphidentitygovernanceresume.ResumePostRequestBody();
com.microsoft.graph.models.identitygovernance.CustomTaskExtensionCallbackData data = new com.microsoft.graph.models.identitygovernance.CustomTaskExtensionCallbackData();
data.setOperationStatus(com.microsoft.graph.models.identitygovernance.CustomTaskExtensionOperationStatus.Completed);
resumePostRequestBody.setData(data);
resumePostRequestBody.setSource("sample");
resumePostRequestBody.setType("lifecycleEvent");
graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").tasks().byTaskId("{task-id}").taskProcessingResults().byTaskProcessingResultId("{taskProcessingResult-id}").microsoftGraphIdentityGovernanceResume().post(resumePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const resume = {
  data: {
    operationStatus: 'Completed'
  },
  source: 'sample',
  type: 'lifecycleEvent'
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/4f36da05-5df8-457d-adb3-b132e7b59571/tasks/e07dcdb2-0a77-4ee3-8645-3801fbe1cf9f/taskProcessingResults/6e1ec336-8d06-4386-a377-79dbab1a2eb6/resume')
	.post(resume);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\Tasks\Item\TaskProcessingResults\Item\MicrosoftGraphIdentityGovernanceResume\ResumePostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\CustomTaskExtensionCallbackData;
use Microsoft\Graph\Generated\Models\IdentityGovernance\CustomTaskExtensionOperationStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ResumePostRequestBody();
$data = new CustomTaskExtensionCallbackData();
$data->setOperationStatus(new CustomTaskExtensionOperationStatus('completed'));
$requestBody->setData($data);
$requestBody->setSource('sample');
$requestBody->setType('lifecycleEvent');

$graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->tasks()->byTaskId('task-id')->taskProcessingResults()->byTaskProcessingResultId('taskProcessingResult-id')->microsoftGraphIdentityGovernanceResume()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	data = @{
		operationStatus = "Completed"
	}
	source = "sample"
	type = "lifecycleEvent"
}

Resume-MgIdentityGovernanceLifecycleWorkflowTaskProcessingResult -WorkflowId $workflowId -TaskId $taskId -TaskProcessingResultId $taskProcessingResultId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.tasks.item.taskprocessingresults.item.microsoft_graph_identity_governance_resume.resume_post_request_body import ResumePostRequestBody
from msgraph.generated.models.identity_governance.custom_task_extension_callback_data import CustomTaskExtensionCallbackData
from msgraph.generated.models.custom_task_extension_operation_status import CustomTaskExtensionOperationStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ResumePostRequestBody(
	data = CustomTaskExtensionCallbackData(
		operation_status = CustomTaskExtensionOperationStatus.Completed,
	),
	source = "sample",
	type = "lifecycleEvent",
)

await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').tasks.by_task_id('task-id').task_processing_results.by_task_processing_result_id('taskProcessingResult-id').microsoft_graph_identity_governance_resume.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
