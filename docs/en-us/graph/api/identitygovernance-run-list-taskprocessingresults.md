<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-run-list-taskprocessingresults?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List taskProcessingResults \(from a run\)

Namespace: microsoft.graph.identityGovernance

Get the [taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) resources for a [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows-Reports.Read.All | LifecycleWorkflows.Read.All, LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows-Reports.Read.All | LifecycleWorkflows.Read.All, LifecycleWorkflows.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* and *Lifecycle Workflows Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/runs/{runId}/taskProcessingResults
```

## Optional query parameters

This method supports the `$select`, `$orderby`, `$expand`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.identityGovernance.taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Get the task processing results in a run report from a workflow

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/a977dbe8-0f3f-4ae6-b3a7-29e1010ac4cc/runs/33bf1a9c-2b26-49b6-996f-ca416c518341/taskProcessingResults
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].Runs["{run-id}"].TaskProcessingResults.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").Runs().ByRunId("run-id").TaskProcessingResults().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").runs().byRunId("{run-id}").taskProcessingResults().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskProcessingResults = await client.api('/identityGovernance/lifecycleWorkflows/workflows/a977dbe8-0f3f-4ae6-b3a7-29e1010ac4cc/runs/33bf1a9c-2b26-49b6-996f-ca416c518341/taskProcessingResults')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->runs()->byRunId('run-id')->taskProcessingResults()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowRunTaskProcessingResult -WorkflowId $workflowId -RunId $runId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').runs.by_run_id('run-id').task_processing_results.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('a977dbe8-0f3f-4ae6-b3a7-29e1010ac4cc')/runs('33bf1a9c-2b26-49b6-996f-ca416c518341')/taskProcessingResults",
    "value": [
        {
            "completedDateTime": "2023-01-20T17:16:03.4863553Z",
            "createdDateTime": "2023-01-20T17:16:00.9095011Z",
            "id": "7a21089f-ec13-4e9c-997e-b31f4e59d41e",
            "processingStatus": "completed",
            "startedDateTime": "2023-01-20T17:16:02.8025169Z",
            "failureReason": null,
            "processingInfo": "User was already a member of all requested groups",
            "subject": {
                "id": "1baa57fa-3c4e-4526-ba5a-db47a9df95f0"
            },
            "task": {
                "category": "joiner,leaver",
                "continueOnError": false,
                "description": "Add user to selected groups",
                "displayName": "Add User To Groups",
                "executionSequence": 3,
                "id": "c8dbaed8-3d23-4e5a-8f65-130767639667",
                "isEnabled": true,
                "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
                "arguments": [
                    {
                        "name": "groupID",
                        "value": "1624be55-d924-491e-ac72-401f6f961e4d"
                    }
                ]
            }
        }
    ]
}
```

### Example 2: Get the specific properties of task processing results in a run report for a workflow

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/a977dbe8-0f3f-4ae6-b3a7-29e1010ac4cc/runs/33bf1a9c-2b26-49b6-996f-ca416c518341/taskProcessingResults?$select=id,failureReason,processingStatus,subject,task
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].Runs["{run-id}"].TaskProcessingResults.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","failureReason","processingStatus","subject","task" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)

requestParameters := &graphidentitygovernance.LifecycleWorkflowsWorkflowsItemRunsItemTaskProcessingResultsRequestBuilderGetQueryParameters{
	Select: [] string {"id","failureReason","processingStatus","subject","task"},
}
configuration := &graphidentitygovernance.LifecycleWorkflowsWorkflowsItemRunsItemTaskProcessingResultsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").Runs().ByRunId("run-id").TaskProcessingResults().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").runs().byRunId("{run-id}").taskProcessingResults().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "failureReason", "processingStatus", "subject", "task"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskProcessingResults = await client.api('/identityGovernance/lifecycleWorkflows/workflows/a977dbe8-0f3f-4ae6-b3a7-29e1010ac4cc/runs/33bf1a9c-2b26-49b6-996f-ca416c518341/taskProcessingResults')
	.select('id,failureReason,processingStatus,subject,task')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\Runs\Item\TaskProcessingResults\TaskProcessingResultsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TaskProcessingResultsRequestBuilderGetRequestConfiguration();
$queryParameters = TaskProcessingResultsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","failureReason","processingStatus","subject","task"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->runs()->byRunId('run-id')->taskProcessingResults()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowRunTaskProcessingResult -WorkflowId $workflowId -RunId $runId -Property "id,failureReason,processingStatus,subject,task" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.lifecycle_workflows.workflows.item.runs.item.task_processing_results.task_processing_results_request_builder import TaskProcessingResultsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TaskProcessingResultsRequestBuilder.TaskProcessingResultsRequestBuilderGetQueryParameters(
		select = ["id","failureReason","processingStatus","subject","task"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').runs.by_run_id('run-id').task_processing_results.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('a977dbe8-0f3f-4ae6-b3a7-29e1010ac4cc')/runs('33bf1a9c-2b26-49b6-996f-ca416c518341')/taskProcessingResults(id,failureReason,processingStatus,subject,task)",
    "value": [
        {
            "id": "7a21089f-ec13-4e9c-997e-b31f4e59d41e",
            "processingStatus": "completed",
            "failureReason": null,
            "subject": {
                "id": "1baa57fa-3c4e-4526-ba5a-db47a9df95f0"
            },
            "task": {
                "category": "joiner,leaver",
                "continueOnError": false,
                "description": "Add user to selected groups",
                "displayName": "Add User To Groups",
                "executionSequence": 3,
                "id": "c8dbaed8-3d23-4e5a-8f65-130767639667",
                "isEnabled": true,
                "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
                "arguments": [
                    {
                        "name": "groupID",
                        "value": "1624be55-d924-491e-ac72-401f6f961e4d"
                    }
                ]
            }
        }
    ]
}
```
