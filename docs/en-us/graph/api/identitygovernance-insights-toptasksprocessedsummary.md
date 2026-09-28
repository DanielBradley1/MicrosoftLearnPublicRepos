<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-toptasksprocessedsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# insights: topTasksProcessedSummary

Namespace: microsoft.graph.identityGovernance

Provide a summary from the [insights](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-insights?view=graph-rest-1.0) resource of the most processed [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) objects, known as top tasks, for a specified time period in a tenant. The task definition is provided, along with numerical counts of total, successful, and failed runs. For information about workflows processed, see [insights: topWorkflowsProcessedSummary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-topworkflowsprocessedsummary?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows.Read.All | LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows.Read.All | LifecycleWorkflows.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Global Reader* and *Lifecycle Workflows Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/insights/topTasksProcessedSummary(startDateTime={startDateTime},endDateTime={endDateTime})
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table lists the parameters that are required when you call this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The start date, and time, of the insight summary for most tasks processed in a tenant. |
| endDateTime | DateTimeOffset | The end date, and time, of the insight summary for most tasks processed in a tenant. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.identityGovernance.topTasksInsightsSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-toptasksinsightssummary?view=graph-rest-1.0) collection in the response body.

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/insights/topTasksProcessedSummary(startDateTime=2023-01-01T00:00:00Z,endDateTime=2023-01-31T00:00:00Z)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Insights.MicrosoftGraphIdentityGovernanceTopTasksProcessedSummaryWithStartDateTimeWithEndDateTime(DateTimeOffset.Parse("{endDateTime}"),DateTimeOffset.Parse("{startDateTime}")).GetAsTopTasksProcessedSummaryWithStartDateTimeWithEndDateTimeGetResponseAsync();
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
startDateTime , err := time.Parse(time.RFC3339, "{startDateTime}")
endDateTime , err := time.Parse(time.RFC3339, "{endDateTime}")
microsoftGraphIdentityGovernanceTopTasksProcessedSummary, err := graphClient.IdentityGovernance().LifecycleWorkflows().Insights().MicrosoftGraphIdentityGovernanceTopTasksProcessedSummaryWithStartDateTimeWithEndDateTime(&startDateTime, &endDateTime).GetAsTopTasksProcessedSummaryWithStartDateTimeWithEndDateTimeGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.identityGovernance().lifecycleWorkflows().insights().microsoftGraphIdentityGovernanceTopTasksProcessedSummaryWithStartDateTimeWithEndDateTime(OffsetDateTime.parse("{endDateTime}"), OffsetDateTime.parse("{startDateTime}")).get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let topTasksProcessedSummary = await client.api('/identityGovernance/lifecycleWorkflows/insights/topTasksProcessedSummary(startDateTime=2023-01-01T00:00:00Z,endDateTime=2023-01-31T00:00:00Z)')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->insights()->microsoftGraphIdentityGovernanceTopTasksProcessedSummaryWithStartDateTimeWithEndDateTime(new \DateTime('{endDateTime}'),new \DateTime('{startDateTime}'))->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Invoke-MgTopIdentityGovernanceLifecycleWorkflowInsightTaskProcessedSummary
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.insights.microsoft_graph_identity_governance_top_tasks_processed_summary_with_start_date_time_with_end_date_time("{endDateTime}","{startDateTime}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.identityGovernance.topTasksInsightsSummary)",
"value": [
     { 
       "taskDefinitionId" : "gbc28c8e-f522-43b1-9d30-ee62b4ee941c", 
       "taskDefinitionDisplayName" : "Disable User Account",  
       "totalTasks" : 32, 
       "successfulTasks" : 15, 
       "failedTasks" : 17, 
       "totalUsers" : 46 , 
       "successfulUsers" : 25 ,
       "failedUsers" : 21
     },
     { 
       "taskDefinitionId" : "afg23h8e-a522-53b1-5d30-ft62b4ee941d", 
       "taskDefinitionDisplayName" : "Add user to groups", 
       "totalProcessedTasks" : 30, 
       "successfulTasks" : 14, 
       "failedTasks" : 16, 
       "totalUsers" : 36  ,
       "successfulUsers" : 25 ,
       "failedUsers" : 11
     },   
     { 
       "taskDefinitionId" : "mcd28c8e-t523-83b1-3d70-jl62b4hh944g", 
       "taskDefinitionDisplayName" : "Send onboarding reminder email", 
       "totalProcessedTasks" : 28, 
       "successfulTasks" : 13, 
       "failedTasks" : 15, 
       "totalUsers" : 37 ,
       "successfulUsers" : 23 ,
       "failedUsers" : 14
     }, 
     { 
       "taskDefinitionId" : "beg28c8e-h23-53b1-8f60-kv62b4ee941c", 
       "taskDefinitionDisplayName" : "Generate TAP and Send Email", 
       "totalProcessedTasks" : 30, 
       "successfulTasks" : 18, 
       "failedTasks" : 12, 
       "totalUsers" : 35  ,
       "successfulUsers" : 24 ,
       "failedUsers" : 11
     }, 
     { 
       "taskDefinitionId" : "efc28c8e-j322-73b1-9e30-fh62b4ee941d", 
       "taskDefinitionDisplayName" : "Run a custom task extension", 
       "totalProcessedTasks" : 25, 
       "successfulTasks" : 15, 
       "failedTasks" : 10, 
       "totalUsers" : 26  ,
       "successfulUsers" : 17 ,
       "failedUsers" : 9
     }, 
     { 
       "taskDefinitionId" : "nmd28c8e-k822-53b1-3d30-ee62b4ee941e", 
       "taskDefinitionDisplayName" : "Request user access package assignment", 
       "totalProcessedTasks" : 26, 
       "successfulTasks" : 18, 
       "failedTasks" : 8, 
       "totalUsers" : 32,  
       "successfulUsers" : 24 ,
       "failedUsers" : 8
     }, 
     { 
       "taskDefinitionId" : "qbc28c8e-f522-43b1-9d30-ee62b4ee941c", 
       "taskDefinitionDisplayName" : "Send Welcome Email",  
       "totalProcessedTasks" : 25, 
       "successfulTasks" : 20, 
       "failedTasks" : 5, 
       "totalUsers" : 28  ,
       "successfulUsers" : 22 ,
       "failedUsers" : 6
     }, 
  ] 
}
```
