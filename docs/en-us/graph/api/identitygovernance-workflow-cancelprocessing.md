<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-cancelprocessing?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# workflow: cancelProcessing

Namespace: microsoft.graph.identityGovernance

Cancel one or more [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) runs that are currently in `queued` or `inProgress` status. Currently limited to canceling one run per request.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

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
POST /identityGovernance/lifecycleWorkflows/workflows/{workflow-id}/cancelProcessing
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that are required with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| scope | [microsoft.graph.identityGovernance.cancelScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-cancelscope?view=graph-rest-1.0) | Defines the scope of workflow runs to cancel. Currently only [cancelRunsScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-cancelrunsscope?view=graph-rest-1.0) is supported. Required. |

### cancelRunsScope properties

When using [cancelRunsScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-cancelrunsscope?view=graph-rest-1.0), the `@odata.type` property is required in the request body.

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | Must be `#microsoft.graph.identityGovernance.cancelRunsScope`. Required. |
| runs | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | The workflow runs to cancel. Currently limited to one run per request. Required. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Successfully cancel a workflow run

The following example shows a request that successfully cancels a single workflow run.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/cancelProcessing
Content-Type: application/json

{
  "scope": {
    "@odata.type": "#microsoft.graph.identityGovernance.cancelRunsScope",
    "runs": [
      {
        "id": "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceCancelProcessing;
using Microsoft.Graph.Models.IdentityGovernance;

var requestBody = new CancelProcessingPostRequestBody
{
	Scope = new CancelRunsScope
	{
		OdataType = "#microsoft.graph.identityGovernance.cancelRunsScope",
		Runs = new List<Run>
		{
			new Run
			{
				Id = "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceCancelProcessing.PostAsync(requestBody);
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

requestBody := graphidentitygovernance.NewCancelProcessingPostRequestBody()
scope := graphmodelsidentitygovernance.NewCancelRunsScope()


run := graphmodelsidentitygovernance.NewRun()
id := "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
run.SetId(&id) 

runs := []graphmodelsidentitygovernance.Runable {
	run,
}
scope.SetRuns(runs)
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernanceCancelProcessing().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecancelprocessing.CancelProcessingPostRequestBody cancelProcessingPostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancecancelprocessing.CancelProcessingPostRequestBody();
com.microsoft.graph.models.identitygovernance.CancelRunsScope scope = new com.microsoft.graph.models.identitygovernance.CancelRunsScope();
scope.setOdataType("#microsoft.graph.identityGovernance.cancelRunsScope");
LinkedList<com.microsoft.graph.models.identitygovernance.Run> runs = new LinkedList<com.microsoft.graph.models.identitygovernance.Run>();
com.microsoft.graph.models.identitygovernance.Run run = new com.microsoft.graph.models.identitygovernance.Run();
run.setId("8cdf25a8-c9d2-423e-a03d-3f39f03c3e97");
runs.add(run);
scope.setRuns(runs);
cancelProcessingPostRequestBody.setScope(scope);
graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceCancelProcessing().post(cancelProcessingPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cancelProcessing = {
  scope: {
    '@odata.type': '#microsoft.graph.identityGovernance.cancelRunsScope',
    runs: [
      {
        id: '8cdf25a8-c9d2-423e-a03d-3f39f03c3e97'
      }
    ]
  }
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/cancelProcessing')
	.post(cancelProcessing);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceCancelProcessing\CancelProcessingPostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\CancelRunsScope;
use Microsoft\Graph\Generated\Models\IdentityGovernance\Run;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CancelProcessingPostRequestBody();
$scope = new CancelRunsScope();
$scope->setOdataType('#microsoft.graph.identityGovernance.cancelRunsScope');
$runsRun1 = new Run();
$runsRun1->setId('8cdf25a8-c9d2-423e-a03d-3f39f03c3e97');
$runsArray []= $runsRun1;
$scope->setRuns($runsArray);

$requestBody->setScope($scope);

$graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceCancelProcessing()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	scope = @{
		"@odata.type" = "#microsoft.graph.identityGovernance.cancelRunsScope"
		runs = @(
			@{
				id = "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
			}
		)
	}
}

Stop-MgIdentityGovernanceLifecycleWorkflowProcessing -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_cancel_processing.cancel_processing_post_request_body import CancelProcessingPostRequestBody
from msgraph.generated.models.identity_governance.cancel_runs_scope import CancelRunsScope
from msgraph.generated.models.identity_governance.run import Run
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CancelProcessingPostRequestBody(
	scope = CancelRunsScope(
		odata_type = "#microsoft.graph.identityGovernance.cancelRunsScope",
		runs = [
			Run(
				id = "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97",
			),
		],
	),
)

await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_cancel_processing.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
