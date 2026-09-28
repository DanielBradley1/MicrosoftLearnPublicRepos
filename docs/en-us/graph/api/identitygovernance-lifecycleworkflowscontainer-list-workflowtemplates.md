<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-workflowtemplates?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# List workflowTemplates

Namespace: microsoft.graph.identityGovernance

Get a list of the [workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows.Read.All | LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows.Read.All | LifecycleWorkflows.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* and *Lifecycle Workflows Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/workflowTemplates
```

## Optional query parameters

This method supports the `$select`, `$orderby`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.identityGovernance.workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve all Lifecycle Workflows workflow templates

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflowTemplates
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.WorkflowTemplates.GetAsync();
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
workflowTemplates, err := graphClient.IdentityGovernance().LifecycleWorkflows().WorkflowTemplates().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.WorkflowTemplateCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflowTemplates().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let workflowTemplates = await client.api('/identityGovernance/lifecycleWorkflows/workflowTemplates')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflowTemplates()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowTemplate
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflow_templates.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates",
    "value": [
        {
            "category": "joiner",
            "description": "Configure pre-hire tasks for onboarding employees before their first day",
            "displayName": "Onboard pre-hire employee",
            "id": "77179007-8114-41b5-922e-2e22109df41f",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeHireDate",
                    "offsetInDays": -7
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('77179007-8114-41b5-922e-2e22109df41f')/tasks",
            "tasks": [
                {
                    "category": "joiner",
                    "continueOnError": false,
                    "description": "Generate Temporary Access Pass and send via email to user's manager",
                    "displayName": "Generate TAP And Send Email",
                    "executionSequence": 1,
                    "id": "3e062c24-d219-483d-9258-288f2a039b94",
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
            ]
        },
        {
            "category": "joiner",
            "description": "Configure new hire tasks for onboarding employees on their first day",
            "displayName": "Onboard new hire employee",
            "id": "4e06785d-7c1d-4b24-b9e1-bba2b890c58b",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeHireDate",
                    "offsetInDays": 0
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('4e06785d-7c1d-4b24-b9e1-bba2b890c58b')/tasks",
            "tasks": [
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Enable user account in the directory",
                    "displayName": "Enable User Account",
                    "executionSequence": 1,
                    "id": "e18f3208-311c-46a3-a27b-d9c15cd595bc",
                    "isEnabled": true,
                    "taskDefinitionId": "6fc52c9d-398b-4305-9763-15f42c1676fc",
                    "arguments": []
                },
                {
                    "category": "joiner",
                    "continueOnError": false,
                    "description": "Send welcome email to new hire",
                    "displayName": "Send Welcome Email",
                    "executionSequence": 2,
                    "id": "e9551045-4302-499f-9108-60b9e23c067a",
                    "isEnabled": true,
                    "taskDefinitionId": "70b29d51-b59a-4773-9280-8841dfd3f2ea",
                    "arguments": []
                },
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Add user to selected groups",
                    "displayName": "Add User To Groups",
                    "executionSequence": 3,
                    "id": "560acd0c-321e-4e7e-9f31-ff8899c55878",
                    "isEnabled": true,
                    "taskDefinitionId": "22085229-5809-45e8-97fd-270d28d66910",
                    "arguments": [
                        {
                            "name": "groupID",
                            "value": ""
                        }
                    ]
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Execute real-time termination tasks for employees on their last day of work",
            "displayName": "Real-time employee termination",
            "id": "145735f1-57cc-48c2-81ec-727f07a10096",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('145735f1-57cc-48c2-81ec-727f07a10096')/tasks",
            "tasks": [
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Azure AD groups memberships",
                    "displayName": "Remove user from all groups",
                    "executionSequence": 1,
                    "id": "1b89bb69-a8cf-416b-a69e-4f6d8108834c",
                    "isEnabled": true,
                    "taskDefinitionId": "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Teams memberships",
                    "displayName": "Remove user from all Teams",
                    "executionSequence": 2,
                    "id": "d3cea676-ccce-4426-825c-63c63e9a64c7",
                    "isEnabled": true,
                    "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Delete user account in Azure AD",
                    "displayName": "Delete User Account",
                    "executionSequence": 3,
                    "id": "adbd4f05-99f0-4260-a155-7657623ca071",
                    "isEnabled": true,
                    "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
                    "arguments": []
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Configure pre-offboarding tasks for employees before their last day of work",
            "displayName": "Pre-Offboarding of an employee",
            "id": "25abd83d-3b5d-4d6f-bb9a-4ed366fd96b1",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeLeaveDateTime",
                    "offsetInDays": -7
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('25abd83d-3b5d-4d6f-bb9a-4ed366fd96b1')/tasks",
            "tasks": [
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Remove user from membership of selected Azure AD groups",
                    "displayName": "Remove user from selected groups",
                    "executionSequence": 1,
                    "id": "7e9aac8a-d239-4867-be60-b3c999c50ee7",
                    "isEnabled": true,
                    "taskDefinitionId": "1953a66c-751c-45e5-8bfe-01462c70da3c",
                    "arguments": [
                        {
                            "name": "groupID",
                            "value": ""
                        }
                    ]
                },
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Remove user from membership of selected Teams",
                    "displayName": "Remove user from selected Teams",
                    "executionSequence": 2,
                    "id": "40eab675-1aaf-432d-b17e-053d93b0fe2e",
                    "isEnabled": true,
                    "taskDefinitionId": "06aa7acb-01af-4824-8899-b14e5ed788d6",
                    "arguments": [
                        {
                            "name": "teamID",
                            "value": ""
                        }
                    ]
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Configure offboarding tasks for employees on their last day of work",
            "displayName": "Offboard an employee",
            "id": "e821c59e-d28c-44d7-902f-5fed05e926f1",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeLeaveDateTime",
                    "offsetInDays": 0
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('e821c59e-d28c-44d7-902f-5fed05e926f1')/tasks",
            "tasks": [
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Disable user account in the directory",
                    "displayName": "Disable User Account",
                    "executionSequence": 1,
                    "id": "8d9eab35-6c32-4b76-acbd-6a22cb07aa6a",
                    "isEnabled": true,
                    "taskDefinitionId": "1dfdfcc7-52fa-4c2e-bf3a-e3919cc12950",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Azure AD groups memberships",
                    "displayName": "Remove user from all groups",
                    "executionSequence": 2,
                    "id": "4f5d8835-5d38-4106-ac7e-ebc407749bd2",
                    "isEnabled": true,
                    "taskDefinitionId": "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Teams memberships",
                    "displayName": "Remove user from all Teams",
                    "executionSequence": 3,
                    "id": "8087b303-e7d5-492d-ab75-31d4aa34bd73",
                    "isEnabled": true,
                    "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                    "arguments": []
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Configure offboarding tasks for employees after their last day of work",
            "displayName": "Post-Offboarding of an employee",
            "id": "50149a4a-7c2d-4fd8-8018-761f4eb915cb",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeLeaveDateTime",
                    "offsetInDays": 7
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('50149a4a-7c2d-4fd8-8018-761f4eb915cb')/tasks",
            "tasks": [
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove all licenses assigned to the user",
                    "displayName": "Remove all licenses for user",
                    "executionSequence": 1,
                    "id": "760ab754-8249-4bce-9315-1ad06488e434",
                    "isEnabled": true,
                    "taskDefinitionId": "8fa97d28-3e52-4985-b3a9-a1126f9b8b4e",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Teams memberships",
                    "displayName": "Remove user from all Teams",
                    "executionSequence": 2,
                    "id": "17b4e37b-c50b-4e04-a11c-93479f487d1d",
                    "isEnabled": true,
                    "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Delete user account in Azure AD",
                    "displayName": "Delete User Account",
                    "executionSequence": 3,
                    "id": "46849618-30e7-4b67-abf0-f8c7f0d54b95",
                    "isEnabled": true,
                    "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
                    "arguments": []
                }
            ]
        }
    ]
}
```

### Example 2: Retrieve workflow templates supported for "leaver" workflows

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflowTemplates?$filter=category eq 'leaver'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.WorkflowTemplates.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "category eq 'leaver'";
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


requestFilter := "category eq 'leaver'"

requestParameters := &graphidentitygovernance.LifecycleWorkflowsWorkflowTemplatesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphidentitygovernance.LifecycleWorkflowsWorkflowTemplatesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workflowTemplates, err := graphClient.IdentityGovernance().LifecycleWorkflows().WorkflowTemplates().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.WorkflowTemplateCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflowTemplates().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "category eq 'leaver'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let workflowTemplates = await client.api('/identityGovernance/lifecycleWorkflows/workflowTemplates')
	.filter('category eq \'leaver\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\WorkflowTemplates\WorkflowTemplatesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new WorkflowTemplatesRequestBuilderGetRequestConfiguration();
$queryParameters = WorkflowTemplatesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "category eq 'leaver'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflowTemplates()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflowTemplate -Filter "category eq 'leaver'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.lifecycle_workflows.workflow_templates.workflow_templates_request_builder import WorkflowTemplatesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = WorkflowTemplatesRequestBuilder.WorkflowTemplatesRequestBuilderGetQueryParameters(
		filter = "category eq 'leaver'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.lifecycle_workflows.workflow_templates.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```json
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates",
    "value": [
        {
            "category": "leaver",
            "description": "Execute real-time termination tasks for employees on their last day of work",
            "displayName": "Real-time employee termination",
            "id": "145735f1-57cc-48c2-81ec-727f07a10096",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.onDemandExecutionOnly"
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('145735f1-57cc-48c2-81ec-727f07a10096')/tasks",
            "tasks": [
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Azure AD groups memberships",
                    "displayName": "Remove user from all groups",
                    "executionSequence": 1,
                    "id": "1b89bb69-a8cf-416b-a69e-4f6d8108834c",
                    "isEnabled": true,
                    "taskDefinitionId": "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Teams memberships",
                    "displayName": "Remove user from all Teams",
                    "executionSequence": 2,
                    "id": "d3cea676-ccce-4426-825c-63c63e9a64c7",
                    "isEnabled": true,
                    "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Delete user account in Azure AD",
                    "displayName": "Delete User Account",
                    "executionSequence": 3,
                    "id": "adbd4f05-99f0-4260-a155-7657623ca071",
                    "isEnabled": true,
                    "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
                    "arguments": []
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Configure pre-offboarding tasks for employees before their last day of work",
            "displayName": "Pre-Offboarding of an employee",
            "id": "25abd83d-3b5d-4d6f-bb9a-4ed366fd96b1",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeLeaveDateTime",
                    "offsetInDays": -7
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('25abd83d-3b5d-4d6f-bb9a-4ed366fd96b1')/tasks",
            "tasks": [
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Remove user from membership of selected Azure AD groups",
                    "displayName": "Remove user from selected groups",
                    "executionSequence": 1,
                    "id": "7e9aac8a-d239-4867-be60-b3c999c50ee7",
                    "isEnabled": true,
                    "taskDefinitionId": "1953a66c-751c-45e5-8bfe-01462c70da3c",
                    "arguments": [
                        {
                            "name": "groupID",
                            "value": ""
                        }
                    ]
                },
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Remove user from membership of selected Teams",
                    "displayName": "Remove user from selected Teams",
                    "executionSequence": 2,
                    "id": "40eab675-1aaf-432d-b17e-053d93b0fe2e",
                    "isEnabled": true,
                    "taskDefinitionId": "06aa7acb-01af-4824-8899-b14e5ed788d6",
                    "arguments": [
                        {
                            "name": "teamID",
                            "value": ""
                        }
                    ]
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Configure offboarding tasks for employees on their last day of work",
            "displayName": "Offboard an employee",
            "id": "e821c59e-d28c-44d7-902f-5fed05e926f1",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeLeaveDateTime",
                    "offsetInDays": 0
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('e821c59e-d28c-44d7-902f-5fed05e926f1')/tasks",
            "tasks": [
                {
                    "category": "joiner,leaver",
                    "continueOnError": false,
                    "description": "Disable user account in the directory",
                    "displayName": "Disable User Account",
                    "executionSequence": 1,
                    "id": "8d9eab35-6c32-4b76-acbd-6a22cb07aa6a",
                    "isEnabled": true,
                    "taskDefinitionId": "1dfdfcc7-52fa-4c2e-bf3a-e3919cc12950",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Azure AD groups memberships",
                    "displayName": "Remove user from all groups",
                    "executionSequence": 2,
                    "id": "4f5d8835-5d38-4106-ac7e-ebc407749bd2",
                    "isEnabled": true,
                    "taskDefinitionId": "b3a31406-2a15-4c9a-b25b-a658fa5f07fc",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Teams memberships",
                    "displayName": "Remove user from all Teams",
                    "executionSequence": 3,
                    "id": "8087b303-e7d5-492d-ab75-31d4aa34bd73",
                    "isEnabled": true,
                    "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                    "arguments": []
                }
            ]
        },
        {
            "category": "leaver",
            "description": "Configure offboarding tasks for employees after their last day of work",
            "displayName": "Post-Offboarding of an employee",
            "id": "50149a4a-7c2d-4fd8-8018-761f4eb915cb",
            "executionConditions": {
                "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
                "scope": {
                    "@odata.type": "#microsoft.graph.identityGovernance.ruleBasedSubjectSet",
                    "rule": "department eq 'Marketing'"
                },
                "trigger": {
                    "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
                    "timeBasedAttribute": "employeeLeaveDateTime",
                    "offsetInDays": 7
                }
            },
            "tasks@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflowTemplates('50149a4a-7c2d-4fd8-8018-761f4eb915cb')/tasks",
            "tasks": [
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove all licenses assigned to the user",
                    "displayName": "Remove all licenses for user",
                    "executionSequence": 1,
                    "id": "760ab754-8249-4bce-9315-1ad06488e434",
                    "isEnabled": true,
                    "taskDefinitionId": "8fa97d28-3e52-4985-b3a9-a1126f9b8b4e",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Remove user from all Teams memberships",
                    "displayName": "Remove user from all Teams",
                    "executionSequence": 2,
                    "id": "17b4e37b-c50b-4e04-a11c-93479f487d1d",
                    "isEnabled": true,
                    "taskDefinitionId": "81f7b200-2816-4b3b-8c5d-dc556f07b024",
                    "arguments": []
                },
                {
                    "category": "leaver",
                    "continueOnError": false,
                    "description": "Delete user account in Azure AD",
                    "displayName": "Delete User Account",
                    "executionSequence": 3,
                    "id": "46849618-30e7-4b67-abf0-f8c7f0d54b95",
                    "isEnabled": true,
                    "taskDefinitionId": "8d18588d-9ad3-4c0f-99d0-ec215f0e3dff",
                    "arguments": []
                }
            ]
        }
    ]
}
```
