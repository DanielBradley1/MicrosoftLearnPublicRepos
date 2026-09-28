<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-topworkflowsprocessedsummary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# insights: topWorkflowsProcessedSummary

Namespace: microsoft.graph.identityGovernance

Provide a summary from the [insights](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-insights?view=graph-rest-1.0) resource of the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) objects processed the most, known as top workflows, for a specified period in a tenant. Workflow basic details are given, along with run information. For information about tasks processed, see [insights: topTasksProcessedSummary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-insights-toptasksprocessedsummary?view=graph-rest-1.0).

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
GET /identityGovernance/lifecycleWorkflows/insights/topWorkflowsProcessedSummary(startDateTime={startDateTime},endDateTime={endDateTime})
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table lists the parameters that are required when you call this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The start date, and time, of the summary of the most workflows processed in a tenant. |
| endDateTime | DateTimeOffset | The end date, and time, of the summary of the most workflows processed in a tenant. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.identityGovernance.topWorkflowsInsightsSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-topworkflowsinsightssummary?view=graph-rest-1.0) collection in the response body.

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
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/insights/topWorkflowsProcessedSummary(startDateTime=2023-01-01T00:00:00Z,endDateTime=2023-01-31T00:00:00Z)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Insights.MicrosoftGraphIdentityGovernanceTopWorkflowsProcessedSummaryWithStartDateTimeWithEndDateTime(DateTimeOffset.Parse("{endDateTime}"),DateTimeOffset.Parse("{startDateTime}")).GetAsTopWorkflowsProcessedSummaryWithStartDateTimeWithEndDateTimeGetResponseAsync();
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
microsoftGraphIdentityGovernanceTopWorkflowsProcessedSummary, err := graphClient.IdentityGovernance().LifecycleWorkflows().Insights().MicrosoftGraphIdentityGovernanceTopWorkflowsProcessedSummaryWithStartDateTimeWithEndDateTime(&startDateTime, &endDateTime).GetAsTopWorkflowsProcessedSummaryWithStartDateTimeWithEndDateTimeGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.identityGovernance().lifecycleWorkflows().insights().microsoftGraphIdentityGovernanceTopWorkflowsProcessedSummaryWithStartDateTimeWithEndDateTime(OffsetDateTime.parse("{endDateTime}"), OffsetDateTime.parse("{startDateTime}")).get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let topWorkflowsProcessedSummary = await client.api('/identityGovernance/lifecycleWorkflows/insights/topWorkflowsProcessedSummary(startDateTime=2023-01-01T00:00:00Z,endDateTime=2023-01-31T00:00:00Z)')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->insights()->microsoftGraphIdentityGovernanceTopWorkflowsProcessedSummaryWithStartDateTimeWithEndDateTime(new \DateTime('{endDateTime}'),new \DateTime('{startDateTime}'))->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Invoke-MgTopIdentityGovernanceLifecycleWorkflowInsightWorkflowProcessedSummary
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.insights.microsoft_graph_identity_governance_top_workflows_processed_summary_with_start_date_time_with_end_date_time("{endDateTime}","{startDateTime}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.identityGovernance.topWorkflowsInsightsSummary)",
 "value": [
   { 
      "workflowId" : "6a98cceb-503b-709c-996c-3cg0f24481eb", 
      "workflowDisplayName" : "Pre-hire workflow", 
      "workflowCategory" : "Joiner", 
      "totalRuns" : 30 , 
      "successfulRuns" : 28 ,
      "failedRuns" : 2 , 
      "scheduledRuns" : 26, 
      "onDemandRuns" : 4, 
      "totalUsers" : 45, 
      "successfulUsers" : 38, 
      "failedUsers": 7,
      "workflowVersion" : 3 
   }, 
   { 
      "workflowId" : "8b67ddeb-603b-609c-293f-4dg0f28481ek", 
      "workflowDisplayName" : "Pre-Hire workflow", 
      "workflowCategory" : "Joiner", 
      "totalRuns" : 35 ,
      "successfulRuns" : 26 ,
      "failedUsers" : 9, 
      "scheduledRuns" : 30, 
      "onDemandRuns" : 5,  
      "totalUsers" : 56, 
      "successfulUsers" : 47 , 
      "failedUsers": 9,
      "workflowVersion" : 1  
   }, 
   { 
      "workflowId" : "1f67cceb-203b-909c-096f-6cg0f28481fg", 
      "workflowDisplayName" : "Post-Hire Workflow", 
      "workflowCategory" : "Jeaver", 
      "totalRuns" : 32  ,
      "successfulRuns" : 25 ,
      "failedRuns" : 7 , 
      "scheduldedRuns" : 15, 
      "onDemandRuns" :  17, 
      "totalUsers": 53, 
      "successfulUsers" : 45, 
      "failedUsers" : 8,
      "workflowVersion" : 2 
   }, 
   { 
      "workflowId" : "2s67ddeb-303b-709c-896f-4cg0f28481ed", 
      "workflowDisplayName" : "Pre-Hire Workflow", 
      "workflowCategory" :"Joiner" , 
      "totalRuns" : 28 ,
      "successfulRuns" : 23, 
      "failedRuns" : 5, 
      "scheduldedRuns" : 20, 
      "onDemandRuns" : 8, 
      "totalUsers" : 40, 
      "successfulUsers" : 32 , 
      "failedUsers" : 8,
      "workflowVersion" : 2  
   }, 
   { 
      "workflowId" : "7a67ddeb-503b-909d-995f-3cg0f26481eh", 
      "workflowDisplayName" : "Post-Hire Workflow", 
      "workflowCategory" : "Leaver", 
      "totalRuns" : 26 ,
      "successfulRuns" : 20 , 
      "failedRuns" : 6 , 
      "scheduldedRuns" : 12, 
      "onDemandRuns" : 14, 
      "totalUsers" : 34, 
      "successfulUsers" : 23, 
      "failedUsers" : 11,
      "workflowVersion" : 1 
   }, 
  ] 
}
```
