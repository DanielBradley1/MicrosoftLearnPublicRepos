<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-previewworkflow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# workflow: previewWorkflow

Namespace: microsoft.graph.identityGovernance

Run a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) in preview mode for selected directory objects without affecting production users. This action triggers workflow processing in preview mode, and results can be retrieved by using the [List userProcessingResults](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-userprocessingresults?view=graph-rest-1.0) operation with `$filter=workflowExecutionType eq 'previewMode'`.

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
POST /identityGovernance/lifecycleWorkflows/workflows/{workflow-id}/previewWorkflow
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
| subjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | A collection of directory objects \(typically users\) to include in the preview run. Maximum of 10 subjects per request. Required. |

## Response

If successful, this action returns a `204 No Content` response code.

To retrieve the results of the preview run, use the [List userProcessingResults](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-userprocessingresults?view=graph-rest-1.0) operation with `$filter=workflowExecutionType eq 'preview'`. Results may not be immediately available; timing depends on workflow complexity. Results may include users from previous preview runs for the same workflow.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/previewWorkflow
Content-Type: application/json

{
  "subjects": [
    {
      "@odata.type": "#microsoft.graph.user",
      "id": "b59552b8-fa7b-4f68-8496-0a529aace8c0"
    },
    {
      "@odata.type": "#microsoft.graph.user",
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernancePreviewWorkflow;
using Microsoft.Graph.Models;

var requestBody = new PreviewWorkflowPostRequestBody
{
	Subjects = new List<DirectoryObject>
	{
		new User
		{
			OdataType = "#microsoft.graph.user",
			Id = "b59552b8-fa7b-4f68-8496-0a529aace8c0",
		},
		new User
		{
			OdataType = "#microsoft.graph.user",
			Id = "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernancePreviewWorkflow.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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

requestBody := graphidentitygovernance.NewPreviewWorkflowPostRequestBody()


directoryObject := graphmodels.NewUser()
id := "b59552b8-fa7b-4f68-8496-0a529aace8c0"
directoryObject.SetId(&id) 
directoryObject1 := graphmodels.NewUser()
id := "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
directoryObject1.SetId(&id) 

subjects := []graphmodels.DirectoryObjectable {
	directoryObject,
	directoryObject1,
}
requestBody.SetSubjects(subjects)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernancePreviewWorkflow().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancepreviewworkflow.PreviewWorkflowPostRequestBody previewWorkflowPostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernancepreviewworkflow.PreviewWorkflowPostRequestBody();
LinkedList<DirectoryObject> subjects = new LinkedList<DirectoryObject>();
User directoryObject = new User();
directoryObject.setOdataType("#microsoft.graph.user");
directoryObject.setId("b59552b8-fa7b-4f68-8496-0a529aace8c0");
subjects.add(directoryObject);
User directoryObject1 = new User();
directoryObject1.setOdataType("#microsoft.graph.user");
directoryObject1.setId("a1b2c3d4-e5f6-7890-abcd-ef1234567890");
subjects.add(directoryObject1);
previewWorkflowPostRequestBody.setSubjects(subjects);
graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernancePreviewWorkflow().post(previewWorkflowPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const previewWorkflow = {
  subjects: [
    {
      '@odata.type': '#microsoft.graph.user',
      id: 'b59552b8-fa7b-4f68-8496-0a529aace8c0'
    },
    {
      '@odata.type': '#microsoft.graph.user',
      id: 'a1b2c3d4-e5f6-7890-abcd-ef1234567890'
    }
  ]
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/previewWorkflow')
	.post(previewWorkflow);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernancePreviewWorkflow\PreviewWorkflowPostRequestBody;
use Microsoft\Graph\Generated\Models\DirectoryObject;
use Microsoft\Graph\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PreviewWorkflowPostRequestBody();
$subjectsDirectoryObject1 = new User();
$subjectsDirectoryObject1->setOdataType('#microsoft.graph.user');
$subjectsDirectoryObject1->setId('b59552b8-fa7b-4f68-8496-0a529aace8c0');
$subjectsArray []= $subjectsDirectoryObject1;
$subjectsDirectoryObject2 = new User();
$subjectsDirectoryObject2->setOdataType('#microsoft.graph.user');
$subjectsDirectoryObject2->setId('a1b2c3d4-e5f6-7890-abcd-ef1234567890');
$subjectsArray []= $subjectsDirectoryObject2;
$requestBody->setSubjects($subjectsArray);


$graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernancePreviewWorkflow()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	subjects = @(
		@{
			"@odata.type" = "#microsoft.graph.user"
			id = "b59552b8-fa7b-4f68-8496-0a529aace8c0"
		}
		@{
			"@odata.type" = "#microsoft.graph.user"
			id = "a1b2c3d4-e5f6-7890-abcd-ef1234567890"
		}
	)
}

Invoke-MgPreviewIdentityGovernanceLifecycleWorkflow -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_preview_workflow.preview_workflow_post_request_body import PreviewWorkflowPostRequestBody
from msgraph.generated.models.directory_object import DirectoryObject
from msgraph.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PreviewWorkflowPostRequestBody(
	subjects = [
		User(
			odata_type = "#microsoft.graph.user",
			id = "b59552b8-fa7b-4f68-8496-0a529aace8c0",
		),
		User(
			odata_type = "#microsoft.graph.user",
			id = "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
		),
	],
)

await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_preview_workflow.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
