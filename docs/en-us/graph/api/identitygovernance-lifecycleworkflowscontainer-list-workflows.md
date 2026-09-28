<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-workflows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# List workflows

Namespace: microsoft.graph.identityGovernance

Get a list of [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) resources that are associated with Lifecycle Workflows.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows-Workflow.ReadBasic.All | LifecycleWorkflows-Workflow.Read.All, LifecycleWorkflows-Workflow.ReadWrite.All, LifecycleWorkflows.Read.All, LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows-Workflow.ReadBasic.All | LifecycleWorkflows-Workflow.Read.All, LifecycleWorkflows-Workflow.ReadWrite.All, LifecycleWorkflows.Read.All, LifecycleWorkflows.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* and *Lifecycle Workflows Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/workflows
```

## Optional query parameters

This method supports the `$search`, `$orderby`, and `$filter` OData query parameters to help customize the response. `$expand` is supported by the **createdBy** and **lastModifiedBy** relationships only. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: Retrieve all workflows created in the tenant

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows.GetAsync();
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
workflows, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.WorkflowCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let workflows = await client.api('/identityGovernance/lifecycleWorkflows/workflows')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflow
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows",
    "value": [
        {
            "category": "joiner",
            "description": "Configure pre-hire tasks for onboarding employees before their first day",
            "displayName": "Global pre hire",
            "lastModifiedDateTime": "2022-08-16T20:05:51.4618603Z",
            "createdDateTime": "2022-01-10T20:04:30.619368Z",
            "id": "c007a148-5bf1-4f38-82b4-377fb23b1711",
            "isEnabled": true,
            "isSchedulingEnabled": true,
            "version": 12
        },
        {
            "category": "joiner",
            "description": "Configure new hire tasks for onboarding employees on their first day",
            "displayName": "Global new hire",
            "lastModifiedDateTime": "2022-08-18T17:24:42.6051254Z",
            "createdDateTime": "2022-05-06T14:10:39.9700268Z",
            "id": "559d8339-ab4e-4c41-a517-ed5d8dd9fbf5",
            "isEnabled": true,
            "isSchedulingEnabled": true,
            "version": 5
        },
        {
            "category": "joiner",
            "description": "Configure pre-hire tasks for onboarding employees before their first day",
            "displayName": "Onboard pre-hire employee",
            "lastModifiedDateTime": "2022-08-16T20:01:28.3589067Z",
            "createdDateTime": "2022-08-16T17:48:55.2262907Z",
            "id": "d0454160-b8e9-432f-8a85-790021e64c9e",
            "isEnabled": false,
            "isSchedulingEnabled": false,
            "version": 1
        },
        {
            "category": "leaver",
            "description": "Configure offboarding tasks for employees after their last day of work",
            "displayName": "Post-Offboarding of an employee",
            "lastModifiedDateTime": "2022-08-17T18:57:30.5091553Z",
            "createdDateTime": "2022-08-17T18:57:07.1840042Z",
            "id": "15f9c6db-ada8-4417-927f-17ac24b54b9b",
            "isEnabled": true,
            "isSchedulingEnabled": false,
            "version": 1
        },
        {
            "category": "leaver",
            "description": "Execute real-time termination tasks for employees on their last day of work",
            "displayName": "Real-time employee termination",
            "lastModifiedDateTime": "2022-08-19T20:34:15.4212506Z",
            "createdDateTime": "2022-08-19T20:34:15.4212481Z",
            "id": "57bc6612-2c20-4141-9dab-aa11a95b8fbc",
            "isEnabled": true,
            "isSchedulingEnabled": false,
            "version": 1
        },
        {
            "category": "joiner",
            "description": "Configure new hire tasks for onboarding employees on their first day",
            "displayName": "Onboard new hire employee",
            "lastModifiedDateTime": "2022-08-24T15:39:17.6496744Z",
            "createdDateTime": "2022-08-24T15:39:17.6496704Z",
            "id": "156ce798-1eb6-4e0a-8515-e79f54d04390",
            "isEnabled": true,
            "isSchedulingEnabled": false,
            "version": 1
        }
    ]
}
```

### Example 2: Retrieve only specific properties of "leaver" workflows

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows?$filter=category eq 'leaver'&$select=id,category,displayName,isEnabled,isSchedulingEnabled
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "category eq 'leaver'";
	requestConfiguration.QueryParameters.Select = new string []{ "id","category","displayName","isEnabled","isSchedulingEnabled" };
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

requestParameters := &graphidentitygovernance.LifecycleWorkflowsWorkflowsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
	Select: [] string {"id","category","displayName","isEnabled","isSchedulingEnabled"},
}
configuration := &graphidentitygovernance.LifecycleWorkflowsWorkflowsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workflows, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.WorkflowCollectionResponse result = graphClient.identityGovernance().lifecycleWorkflows().workflows().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "category eq 'leaver'";
	requestConfiguration.queryParameters.select = new String []{"id", "category", "displayName", "isEnabled", "isSchedulingEnabled"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let workflows = await client.api('/identityGovernance/lifecycleWorkflows/workflows')
	.filter('category eq \'leaver\'')
	.select('id,category,displayName,isEnabled,isSchedulingEnabled')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\LifecycleWorkflows\Workflows\WorkflowsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new WorkflowsRequestBuilderGetRequestConfiguration();
$queryParameters = WorkflowsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "category eq 'leaver'";
$queryParameters->select = ["id","category","displayName","isEnabled","isSchedulingEnabled"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceLifecycleWorkflow -Filter "category eq 'leaver'" -Property "id,category,displayName,isEnabled,isSchedulingEnabled" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identity_governance.lifecycle_workflows.workflows.workflows_request_builder import WorkflowsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = WorkflowsRequestBuilder.WorkflowsRequestBuilderGetQueryParameters(
		filter = "category eq 'leaver'",
		select = ["id","category","displayName","isEnabled","isSchedulingEnabled"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.identity_governance.lifecycle_workflows.workflows.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/workflows(category,displayName,isEnabled,isSchedulingEnabled)",
    "value": [
        {
            "category": "leaver",
            "displayName": "Pre-Offboarding employees in the R&D department",
            "id": "c0548e6c-8849-46e8-be14-8b6d2b04957e",
            "isEnabled": true,
            "isSchedulingEnabled": true
        }
    ]
}
```
