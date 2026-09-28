<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activatewithscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# workflow: activateWithScope

Namespace: microsoft.graph.identityGovernance

Run a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object on-demand with a specific scope. You can run any workflow on-demand, including scheduled workflows. Workflows created from the "Real-time employee termination" template are run on-demand only. When you run a workflow on demand, the tasks are executed regardless of whether the user state matches the scope and trigger execution conditions.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Lifecycle Workflows Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/activatewithscope
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
| subjects | [microsoft.graph.user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | The subjects for whom the workflow is activated. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Activate a workflow with a specific scope of 2 users

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/activatewithscope
Content-Type: application/json

{
    "subjects": [ 
        { "id": "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"},
        { "id": "ea09ac2e-77e3-4134-85f2-25ccf3c33387"}
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceActivateWithScope;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ActivateWithScopePostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"subjects" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"id", new UntypedString("8cdf25a8-c9d2-423e-a03d-3f39f03c3e97")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"id", new UntypedString("ea09ac2e-77e3-4134-85f2-25ccf3c33387")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceActivateWithScope.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivatewithscope.ActivateWithScopePostRequestBody activateWithScopePostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivatewithscope.ActivateWithScopePostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> subjects = new LinkedList<Object>();
 property = new ();
property.setId("8cdf25a8-c9d2-423e-a03d-3f39f03c3e97");
subjects.add(property);
 property1 = new ();
property1.setId("ea09ac2e-77e3-4134-85f2-25ccf3c33387");
subjects.add(property1);
additionalData.put("subjects", subjects);
activateWithScopePostRequestBody.setAdditionalData(additionalData);
graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceActivateWithScope().post(activateWithScopePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const activatewithscope = {
    subjects: [ 
        { id: '8cdf25a8-c9d2-423e-a03d-3f39f03c3e97'},
        { id: 'ea09ac2e-77e3-4134-85f2-25ccf3c33387'}
    ]
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/activatewithscope')
	.post(activatewithscope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceActivateWithScope\ActivateWithScopePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ActivateWithScopePostRequestBody();
$additionalData = [
	'subjects' => [
			[
				'id' => '8cdf25a8-c9d2-423e-a03d-3f39f03c3e97',
			],
			[
				'id' => 'ea09ac2e-77e3-4134-85f2-25ccf3c33387',
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceActivateWithScope()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	subjects = @(
		@{
			id = "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97"
		}
		@{
			id = "ea09ac2e-77e3-4134-85f2-25ccf3c33387"
		}
	)
}

Initialize-MgIdentityGovernanceLifecycleWorkflowWithScope -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_activate_with_scope.activate_with_scope_post_request_body import ActivateWithScopePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ActivateWithScopePostRequestBody(
	additional_data = {
			"subjects" : [
				{
						"id" : "8cdf25a8-c9d2-423e-a03d-3f39f03c3e97",
				},
				{
						"id" : "ea09ac2e-77e3-4134-85f2-25ccf3c33387",
				},
			],
	}
)

await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_activate_with_scope.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Activate a workflow with a specific scope of 2 users who don't exist

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/2f0dcb02-65d9-4369-bad5-a3174538c5ff/activatewithscope
Content-Type: application/json

{
    "subjects": [ 
        { "id": "2ea4c363-4b85-4529-b2ec-53b64308f39f"},
        { "id": "44fc5392-9485-4348-871e-2ea17cc0a1b8"}
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceActivateWithScope;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ActivateWithScopePostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"subjects" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"id", new UntypedString("2ea4c363-4b85-4529-b2ec-53b64308f39f")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"id", new UntypedString("44fc5392-9485-4348-871e-2ea17cc0a1b8")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceActivateWithScope.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivatewithscope.ActivateWithScopePostRequestBody activateWithScopePostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivatewithscope.ActivateWithScopePostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> subjects = new LinkedList<Object>();
 property = new ();
property.setId("2ea4c363-4b85-4529-b2ec-53b64308f39f");
subjects.add(property);
 property1 = new ();
property1.setId("44fc5392-9485-4348-871e-2ea17cc0a1b8");
subjects.add(property1);
additionalData.put("subjects", subjects);
activateWithScopePostRequestBody.setAdditionalData(additionalData);
graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceActivateWithScope().post(activateWithScopePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const activatewithscope = {
    subjects: [ 
        { id: '2ea4c363-4b85-4529-b2ec-53b64308f39f'},
        { id: '44fc5392-9485-4348-871e-2ea17cc0a1b8'}
    ]
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/2f0dcb02-65d9-4369-bad5-a3174538c5ff/activatewithscope')
	.post(activatewithscope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceActivateWithScope\ActivateWithScopePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ActivateWithScopePostRequestBody();
$additionalData = [
	'subjects' => [
			[
				'id' => '2ea4c363-4b85-4529-b2ec-53b64308f39f',
			],
			[
				'id' => '44fc5392-9485-4348-871e-2ea17cc0a1b8',
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceActivateWithScope()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	subjects = @(
		@{
			id = "2ea4c363-4b85-4529-b2ec-53b64308f39f"
		}
		@{
			id = "44fc5392-9485-4348-871e-2ea17cc0a1b8"
		}
	)
}

Initialize-MgIdentityGovernanceLifecycleWorkflowWithScope -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_activate_with_scope.activate_with_scope_post_request_body import ActivateWithScopePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ActivateWithScopePostRequestBody(
	additional_data = {
			"subjects" : [
				{
						"id" : "2ea4c363-4b85-4529-b2ec-53b64308f39f",
				},
				{
						"id" : "44fc5392-9485-4348-871e-2ea17cc0a1b8",
				},
			],
	}
)

await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_activate_with_scope.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 406 NOT Acceptable
```

### Example 3: Activate a workflow with a specific processing result scope

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/2f0dcb02-65d9-4369-bad5-a3174538c5ff/activatewithscope
Content-Type: application/json

{
 "scope": {
  "@odata.type": "microsoft.graph.identityGovernance.activateProcessingResultScope",
  "processingResults": [
   {
    "id": "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa"
   },
   {
    "id": "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb"
   }
  ],
  "taskScope": "allTasks"
 }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.LifecycleWorkflows.Workflows.Item.MicrosoftGraphIdentityGovernanceActivateWithScope;
using Microsoft.Graph.Models.IdentityGovernance;

var requestBody = new ActivateWithScopePostRequestBody
{
	Scope = new ActivateProcessingResultScope
	{
		OdataType = "microsoft.graph.identityGovernance.activateProcessingResultScope",
		ProcessingResults = new List<UserProcessingResult>
		{
			new UserProcessingResult
			{
				Id = "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa",
			},
			new UserProcessingResult
			{
				Id = "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb",
			},
		},
		TaskScope = ActivationTaskScopeType.AllTasks,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].MicrosoftGraphIdentityGovernanceActivateWithScope.PostAsync(requestBody);
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

requestBody := graphidentitygovernance.NewActivateWithScopePostRequestBody()
scope := graphmodelsidentitygovernance.NewActivateProcessingResultScope()


userProcessingResult := graphmodelsidentitygovernance.NewUserProcessingResult()
id := "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa"
userProcessingResult.SetId(&id) 
userProcessingResult1 := graphmodelsidentitygovernance.NewUserProcessingResult()
id := "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb"
userProcessingResult1.SetId(&id) 

processingResults := []graphmodelsidentitygovernance.UserProcessingResultable {
	userProcessingResult,
	userProcessingResult1,
}
scope.SetProcessingResults(processingResults)
taskScope := graphmodels.ALLTASKS_ACTIVATIONTASKSCOPETYPE 
scope.SetTaskScope(&taskScope) 
requestBody.SetScope(scope)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").MicrosoftGraphIdentityGovernanceActivateWithScope().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivatewithscope.ActivateWithScopePostRequestBody activateWithScopePostRequestBody = new com.microsoft.graph.identitygovernance.lifecycleworkflows.workflows.item.microsoftgraphidentitygovernanceactivatewithscope.ActivateWithScopePostRequestBody();
com.microsoft.graph.models.identitygovernance.ActivateProcessingResultScope scope = new com.microsoft.graph.models.identitygovernance.ActivateProcessingResultScope();
scope.setOdataType("microsoft.graph.identityGovernance.activateProcessingResultScope");
LinkedList<com.microsoft.graph.models.identitygovernance.UserProcessingResult> processingResults = new LinkedList<com.microsoft.graph.models.identitygovernance.UserProcessingResult>();
com.microsoft.graph.models.identitygovernance.UserProcessingResult userProcessingResult = new com.microsoft.graph.models.identitygovernance.UserProcessingResult();
userProcessingResult.setId("abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa");
processingResults.add(userProcessingResult);
com.microsoft.graph.models.identitygovernance.UserProcessingResult userProcessingResult1 = new com.microsoft.graph.models.identitygovernance.UserProcessingResult();
userProcessingResult1.setId("abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb");
processingResults.add(userProcessingResult1);
scope.setProcessingResults(processingResults);
scope.setTaskScope(com.microsoft.graph.models.identitygovernance.ActivationTaskScopeType.AllTasks);
activateWithScopePostRequestBody.setScope(scope);
graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").microsoftGraphIdentityGovernanceActivateWithScope().post(activateWithScopePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const activatewithscope = {
 scope: {
  '@odata.type': 'microsoft.graph.identityGovernance.activateProcessingResultScope',
  processingResults: [
   {
    id: 'abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa'
   },
   {
    id: 'abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb'
   }
  ],
  taskScope: 'allTasks'
 }
};

await client.api('/identityGovernance/lifecycleWorkflows/workflows/2f0dcb02-65d9-4369-bad5-a3174538c5ff/activatewithscope')
	.post(activatewithscope);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\Item\MicrosoftGraphIdentityGovernanceActivateWithScope\ActivateWithScopePostRequestBody;
use Microsoft\Graph\Generated\Models\IdentityGovernance\ActivateProcessingResultScope;
use Microsoft\Graph\Generated\Models\IdentityGovernance\UserProcessingResult;
use Microsoft\Graph\Generated\Models\IdentityGovernance\ActivationTaskScopeType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ActivateWithScopePostRequestBody();
$scope = new ActivateProcessingResultScope();
$scope->setOdataType('microsoft.graph.identityGovernance.activateProcessingResultScope');
$processingResultsUserProcessingResult1 = new UserProcessingResult();
$processingResultsUserProcessingResult1->setId('abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa');
$processingResultsArray []= $processingResultsUserProcessingResult1;
$processingResultsUserProcessingResult2 = new UserProcessingResult();
$processingResultsUserProcessingResult2->setId('abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb');
$processingResultsArray []= $processingResultsUserProcessingResult2;
$scope->setProcessingResults($processingResultsArray);

$scope->setTaskScope(new ActivationTaskScopeType('allTasks'));
$requestBody->setScope($scope);

$graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->microsoftGraphIdentityGovernanceActivateWithScope()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	scope = @{
		"@odata.type" = "microsoft.graph.identityGovernance.activateProcessingResultScope"
		processingResults = @(
			@{
				id = "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa"
			}
			@{
				id = "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb"
			}
		)
		taskScope = "allTasks"
	}
}

Initialize-MgIdentityGovernanceLifecycleWorkflowWithScope -WorkflowId $workflowId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.lifecycleworkflows.workflows.item.microsoft_graph_identity_governance_activate_with_scope.activate_with_scope_post_request_body import ActivateWithScopePostRequestBody
from msgraph.generated.models.identity_governance.activate_processing_result_scope import ActivateProcessingResultScope
from msgraph.generated.models.identity_governance.user_processing_result import UserProcessingResult
from msgraph.generated.models.activation_task_scope_type import ActivationTaskScopeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ActivateWithScopePostRequestBody(
	scope = ActivateProcessingResultScope(
		odata_type = "microsoft.graph.identityGovernance.activateProcessingResultScope",
		processing_results = [
			UserProcessingResult(
				id = "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_638927021459371237_0cdd8963-aaaa-4632-a1f2-aaaa7230aaaa",
			),
			UserProcessingResult(
				id = "abc12345-265a-4e8f-8d61-94a2dcd2d395_1_78799042-265a-4e8f-8d61-94a2dcd2d395_388131231459357126_aaaa8963-1c30-4632-aaaa-ac96723069cb",
			),
		],
		task_scope = ActivationTaskScopeType.AllTasks,
	),
)

await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').microsoft_graph_identity_governance_activate_with_scope.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
