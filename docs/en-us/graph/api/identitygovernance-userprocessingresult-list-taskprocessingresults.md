<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-userprocessingresult-list-taskprocessingresults?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List taskProcessingResults \(for a user\)

Namespace: microsoft.graph.identityGovernance

Get the task processing result from a [userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) either directly or through a [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0).

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

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Lifecycle Workflows Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/userProcessingResults/{userProcessingResultId}/taskProcessingResults
GET /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/runs/{runId}/userProcessingResults/{userProcessingResultId}/taskProcessingResults
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

### Example 1: List the results of the tasks processed for a user in a workflow

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
GET https://graph.microsoft.com/v1.0/IdentityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/userProcessingResults/78b83505-6967-4168-a7ea-4921c0543ce9/taskProcessingResults
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].UserProcessingResults["{userProcessingResult-id}"].TaskProcessingResults.GetAsync();
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
taskProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").UserProcessingResults().ByUserProcessingResultId("userProcessingResult-id").TaskProcessingResults().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").userProcessingResults().byUserProcessingResultId("{userProcessingResult-id}").taskProcessingResults().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskProcessingResults = await client.api('/IdentityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/userProcessingResults/78b83505-6967-4168-a7ea-4921c0543ce9/taskProcessingResults')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->userProcessingResults()->byUserProcessingResultId('userProcessingResult-id')->taskProcessingResults()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowUserProcessingResultTaskProcessingResult -WorkflowId $workflowId -UserProcessingResultId $userProcessingResultId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').user_processing_results.by_user_processing_result_id('userProcessingResult-id').task_processing_results.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('14879e66-9ea9-48d0-804d-8fea672d0341')/userProcessingResults('78b83505-6967-4168-a7ea-4921c0543ce9')/taskProcessingResults",
    "value": [
        {
            "completedDateTime": "2022-08-24T23:28:05.3529197Z",
            "createdDateTime": "2022-08-24T23:28:04.5490995Z",
            "id": "05a96d7a-0e00-459c-b6c8-1870099e8275",
            "processingStatus": "completed",
            "startedDateTime": "2022-08-24T23:28:05.1234966Z",
            "failureReason": null,
            "processingInfo": null,
            "subject": {
                "id": "ea09ac2e-77e3-4134-85f2-25ccf3c33387"
            },
            "task": {
                "category": "joiner,leaver",
                "continueOnError": false,
                "description": "Enable user account in the directory",
                "displayName": "Enable User Account",
                "executionSequence": 1,
                "id": "917e9eab-415d-4e45-b39d-87eb5e30de38",
                "isEnabled": false,
                "taskDefinitionId": "6fc52c9d-398b-4305-9763-15f42c1676fc",
                "arguments": []
            }
        },
        {
            "completedDateTime": "2022-08-24T23:28:06.760333Z",
            "createdDateTime": "2022-08-24T23:28:04.5571759Z",
            "id": "e30b12e1-45fa-4463-8d54-48f43fd8942a",
            "processingStatus": "completed",
            "startedDateTime": "2022-08-24T23:28:06.3926865Z",
            "failureReason": null,
            "processingInfo": null,
            "subject": {
                "id": "ea09ac2e-77e3-4134-85f2-25ccf3c33387"
            },
            "task": {
                "category": "joiner,leaver",
                "continueOnError": false,
                "description": "Add user to selected groups",
                "displayName": "Add User To Groups",
                "executionSequence": 2,
                "id": "eedd8043-90a1-4e3c-9112-b2a8917ea3ae",
                "isEnabled": true,
                "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
                "arguments": [
                    {
                        "name": "groupID",
                        "value": "e5659cb0-bcbb-4a9f-9092-90f72bd19028"
                    }
                ]
            }
        }
    ]
}
```

### Example 2: List the results of the tasks processed for a user in a workflow and select specific properties

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/15239232-66ed-445b-8292-2f5bbb2eb833/userProcessingResults/40efc576-840f-47d0-ab95-5abca800f8a2/taskProcessingResults?$select=id,processingStatus,failureReason,subject,task
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].UserProcessingResults["{userProcessingResult-id}"].TaskProcessingResults.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","processingStatus","failureReason","subject","task" };
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

requestParameters := &graphidentitygovernance.LifecycleWorkflowsWorkflowsItemUserProcessingResultsItemTaskProcessingResultsRequestBuilderGetQueryParameters{
	Select: [] string {"id","processingStatus","failureReason","subject","task"},
}
configuration := &graphidentitygovernance.LifecycleWorkflowsWorkflowsItemUserProcessingResultsItemTaskProcessingResultsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").UserProcessingResults().ByUserProcessingResultId("userProcessingResult-id").TaskProcessingResults().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").userProcessingResults().byUserProcessingResultId("{userProcessingResult-id}").taskProcessingResults().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "processingStatus", "failureReason", "subject", "task"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskProcessingResults = await client.api('/identityGovernance/lifecycleWorkflows/workflows/15239232-66ed-445b-8292-2f5bbb2eb833/userProcessingResults/40efc576-840f-47d0-ab95-5abca800f8a2/taskProcessingResults')
	.select('id,processingStatus,failureReason,subject,task')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\UserProcessingResults\Item\TaskProcessingResults\TaskProcessingResultsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TaskProcessingResultsRequestBuilderGetRequestConfiguration();
$queryParameters = TaskProcessingResultsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","processingStatus","failureReason","subject","task"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->userProcessingResults()->byUserProcessingResultId('userProcessingResult-id')->taskProcessingResults()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowUserProcessingResultTaskProcessingResult -WorkflowId $workflowId -UserProcessingResultId $userProcessingResultId -Property "id,processingStatus,failureReason,subject,task" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.lifecycle_workflows.workflows.item.user_processing_results.item.task_processing_results.task_processing_results_request_builder import TaskProcessingResultsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TaskProcessingResultsRequestBuilder.TaskProcessingResultsRequestBuilderGetQueryParameters(
		select = ["id","processingStatus","failureReason","subject","task"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').user_processing_results.by_user_processing_result_id('userProcessingResult-id').task_processing_results.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('15239232-66ed-445b-8292-2f5bbb2eb833')/userProcessingResults('40efc576-840f-47d0-ab95-5abca800f8a2')/taskProcessingResults(id,processingStatus,failureReason,subject,task)",
    "value": [
        {
            "id": "78650318-7238-4e7e-852f-2c36cbeff340",
            "processingStatus": "completed",
            "failureReason": null,
            "subject": {
                "id": "df744d9e-2148-4922-88a8-633896c1e929"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Remove all licenses assigned to the user",
                "displayName": "Remove all licenses for user",
                "executionSequence": 1,
                "id": "f71246b2-269c-4ba6-ab8e-afc1a05114cb",
                "isEnabled": true,
                "taskDefinitionId": "8fa97d28-3e52-4985-b3a9-a1126f9b8b4e",
                "arguments": []
            }
        },
        {
            "id": "3d2e459d-5614-42e4-952b-0e917b5f6646",
            "processingStatus": "completed",
            "failureReason": null,
            "subject": {
                "id": "df744d9e-2148-4922-88a8-633896c1e929"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Remove user from all Teams memberships",
                "displayName": "Remove user from all Teams",
                "executionSequence": 2,
                "id": "ed545f03-e8d8-45fb-9cbd-15c937f2a866",
                "isEnabled": true,
                "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                "arguments": []
            }
        },
        {
            "id": "03359fa6-c63c-4573-92c2-4c9518ca98aa",
            "processingStatus": "completed",
            "failureReason": null,
            "subject": {
                "id": "df744d9e-2148-4922-88a8-633896c1e929"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Delete user account in Azure AD",
                "displayName": "Delete User Account",
                "executionSequence": 3,
                "id": "b4cefaa0-6ceb-461d-bbf5-ec69246463fd",
                "isEnabled": true,
                "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
                "arguments": []
            }
        }
    ]
}
```

### Example 3: Get the task processing results for a user processing result in a run report for a workflow

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/runs/72885f91-2cf0-44b1-b3ed-bd145af0192c/userProcessingResults/78b83505-6967-4168-a7ea-4921c0543ce9/taskProcessingResults
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].Runs["{run-id}"].UserProcessingResults["{userProcessingResult-id}"].TaskProcessingResults.GetAsync();
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
taskProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").Runs().ByRunId("run-id").UserProcessingResults().ByUserProcessingResultId("userProcessingResult-id").TaskProcessingResults().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").runs().byRunId("{run-id}").userProcessingResults().byUserProcessingResultId("{userProcessingResult-id}").taskProcessingResults().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskProcessingResults = await client.api('/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/runs/72885f91-2cf0-44b1-b3ed-bd145af0192c/userProcessingResults/78b83505-6967-4168-a7ea-4921c0543ce9/taskProcessingResults')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->runs()->byRunId('run-id')->userProcessingResults()->byUserProcessingResultId('userProcessingResult-id')->taskProcessingResults()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowRunUserProcessingResultTaskProcessingResult -WorkflowId $workflowId -RunId $runId -UserProcessingResultId $userProcessingResultId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').runs.by_run_id('run-id').user_processing_results.by_user_processing_result_id('userProcessingResult-id').task_processing_results.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('14879e66-9ea9-48d0-804d-8fea672d0341')/runs('dad77a47-6eda-4de7-bc37-fe8eb5aaf17d')/userProcessingResults('78b83505-6967-4168-a7ea-4921c0543ce9')/taskProcessingResults",
    "value": [
        {
            "completedDateTime": "2022-08-24T23:28:05.3529197Z",
            "createdDateTime": "2022-08-24T23:28:04.5490995Z",
            "id": "05a96d7a-0e00-459c-b6c8-1870099e8275",
            "processingStatus": "completed",
            "startedDateTime": "2022-08-24T23:28:05.1234966Z",
            "failureReason": null,
            "processingInfo": null,
            "subject": {
                "id": "ea09ac2e-77e3-4134-85f2-25ccf3c33387"
            },
            "task": {
                "category": "joiner,leaver",
                "continueOnError": false,
                "description": "Enable user account in the directory",
                "displayName": "Enable User Account",
                "executionSequence": 1,
                "id": "917e9eab-415d-4e45-b39d-87eb5e30de38",
                "isEnabled": false,
                "taskDefinitionId": "6fc52c9d-398b-4305-9763-15f42c1676fc",
                "arguments": []
            }
        },
        {
            "completedDateTime": "2022-08-24T23:28:06.760333Z",
            "createdDateTime": "2022-08-24T23:28:04.5571759Z",
            "id": "e30b12e1-45fa-4463-8d54-48f43fd8942a",
            "processingStatus": "completed",
            "startedDateTime": "2022-08-24T23:28:06.3926865Z",
            "failureReason": null,
            "processingInfo": "User was already a member of all requested groups",
            "subject": {
                "id": "ea09ac2e-77e3-4134-85f2-25ccf3c33387"
            },
            "task": {
                "category": "joiner,leaver",
                "continueOnError": false,
                "description": "Add user to selected groups",
                "displayName": "Add User To Groups",
                "executionSequence": 2,
                "id": "eedd8043-90a1-4e3c-9112-b2a8917ea3ae",
                "isEnabled": true,
                "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
                "arguments": [
                    {
                        "name": "groupID",
                        "value": "e5659cb0-bcbb-4a9f-9092-90f72bd19028"
                    }
                ]
            }
        }
    ]
}
```

### Example 4: Get the specific properties of task processing results for a user processing result in a run report for a workflow

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/15239232-66ed-445b-8292-2f5bbb2eb833/runs/e65e08a0-d68d-41dc-915b-8c4019af5cc2/userProcessingResults/40efc576-840f-47d0-ab95-5abca800f8a2/taskProcessingResults?$select=id,failureReason,processingStatus,subject,task
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].Runs["{run-id}"].UserProcessingResults["{userProcessingResult-id}"].TaskProcessingResults.GetAsync((requestConfiguration) =>
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

requestParameters := &graphidentitygovernance.LifecycleWorkflowsWorkflowsItemRunsItemUserProcessingResultsItemTaskProcessingResultsRequestBuilderGetQueryParameters{
	Select: [] string {"id","failureReason","processingStatus","subject","task"},
}
configuration := &graphidentitygovernance.LifecycleWorkflowsWorkflowsItemRunsItemUserProcessingResultsItemTaskProcessingResultsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
taskProcessingResults, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").Runs().ByRunId("run-id").UserProcessingResults().ByUserProcessingResultId("userProcessingResult-id").TaskProcessingResults().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.TaskProcessingResultCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").runs().byRunId("{run-id}").userProcessingResults().byUserProcessingResultId("{userProcessingResult-id}").taskProcessingResults().get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "failureReason", "processingStatus", "subject", "task"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let taskProcessingResults = await client.api('/identityGovernance/lifecycleWorkflows/workflows/15239232-66ed-445b-8292-2f5bbb2eb833/runs/e65e08a0-d68d-41dc-915b-8c4019af5cc2/userProcessingResults/40efc576-840f-47d0-ab95-5abca800f8a2/taskProcessingResults')
	.select('id,failureReason,processingStatus,subject,task')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\Runs\Item\UserProcessingResults\Item\TaskProcessingResults\TaskProcessingResultsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new TaskProcessingResultsRequestBuilderGetRequestConfiguration();
$queryParameters = TaskProcessingResultsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","failureReason","processingStatus","subject","task"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->runs()->byRunId('run-id')->userProcessingResults()->byUserProcessingResultId('userProcessingResult-id')->taskProcessingResults()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowRunUserProcessingResultTaskProcessingResult -WorkflowId $workflowId -RunId $runId -UserProcessingResultId $userProcessingResultId -Property "id,failureReason,processingStatus,subject,task" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.lifecycle_workflows.workflows.item.runs.item.user_processing_results.item.task_processing_results.task_processing_results_request_builder import TaskProcessingResultsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = TaskProcessingResultsRequestBuilder.TaskProcessingResultsRequestBuilderGetQueryParameters(
		select = ["id","failureReason","processingStatus","subject","task"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').runs.by_run_id('run-id').user_processing_results.by_user_processing_result_id('userProcessingResult-id').task_processing_results.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows('15239232-66ed-445b-8292-2f5bbb2eb833')/runs('e65e08a0-d68d-41dc-915b-8c4019af5cc2')/userProcessingResults('40efc576-840f-47d0-ab95-5abca800f8a2')/taskProcessingResults(id,failureReason,processingStatus,subject,task)",
    "value": [
        {
            "id": "78650318-7238-4e7e-852f-2c36cbeff340",
            "processingStatus": "completed",
            "failureReason": null,
            "subject": {
                "id": "df744d9e-2148-4922-88a8-633896c1e929"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Remove all licenses assigned to the user",
                "displayName": "Remove all licenses for user",
                "executionSequence": 1,
                "id": "f71246b2-269c-4ba6-ab8e-afc1a05114cb",
                "isEnabled": true,
                "taskDefinitionId": "8fa97d28-3e52-4985-b3a9-a1126f9b8b4e",
                "arguments": []
            }
        },
        {
            "id": "3d2e459d-5614-42e4-952b-0e917b5f6646",
            "processingStatus": "completed",
            "failureReason": null,
            "subject": {
                "id": "df744d9e-2148-4922-88a8-633896c1e929"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Remove user from all Teams memberships",
                "displayName": "Remove user from all Teams",
                "executionSequence": 2,
                "id": "ed545f03-e8d8-45fb-9cbd-15c937f2a866",
                "isEnabled": true,
                "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                "arguments": []
            }
        },
        {
            "id": "03359fa6-c63c-4573-92c2-4c9518ca98aa",
            "processingStatus": "completed",
            "failureReason": null,
            "subject": {
                "id": "df744d9e-2148-4922-88a8-633896c1e929"
            },
            "task": {
                "category": "leaver",
                "continueOnError": false,
                "description": "Delete user account in Azure AD",
                "displayName": "Delete User Account",
                "executionSequence": 3,
                "id": "b4cefaa0-6ceb-461d-bbf5-ec69246463fd",
                "isEnabled": true,
                "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
                "arguments": []
            }
        }
    ]
}
```
