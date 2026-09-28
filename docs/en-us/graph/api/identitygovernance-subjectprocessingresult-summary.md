<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-subjectprocessingresult-summary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# subjectProcessingResult: summary

Namespace: microsoft.graph.identityGovernance

Provide a [subjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectsummary?view=graph-rest-1.0) for [subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0) objects over a specified time period. Because the number of subject processing results returned by the list API can be overwhelming, this summary allows administrators to get a quick overview based on counts.

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
GET /identityGovernance/lifecycleWorkflows/workflows/{workflowId}/runs/{runId}/subjectProcessingResults/summary(startDateTime={TimeStamp},endDateTime={TimeStamp})
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The start date and time of the subject processing result summary. Required. |
| endDateTime | DateTimeOffset | The end date and time of the subject processing result summary. Required. |

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | \*\*\*\*\*\* Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.identityGovernance.subjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectsummary?view=graph-rest-1.0) in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/runs/40efc576-8100-46eb-92c1-73eb43bb09a4/subjectProcessingResults/summary(startDateTime=2026-05-06T00:00:00Z,endDateTime=2026-05-13T00:00:00Z)
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.Workflows["{workflow-id}"].Runs["{run-id}"].SubjectProcessingResults.MicrosoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(DateTimeOffset.Parse("{endDateTime}"),DateTimeOffset.Parse("{startDateTime}")).GetAsync();
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
microsoftGraphIdentityGovernanceSummary, err := graphClient.IdentityGovernance().LifecycleWorkflows().Workflows().ByWorkflowId("workflow-id").Runs().ByRunId("run-id").SubjectProcessingResults().MicrosoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(&startDateTime, &endDateTime).Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.identityGovernance().lifecycleWorkflows().workflows().byWorkflowId("{workflow-id}").runs().byRunId("{run-id}").subjectProcessingResults().microsoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(OffsetDateTime.parse("{endDateTime}"), OffsetDateTime.parse("{startDateTime}")).get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let subjectSummary = await client.api('/identityGovernance/lifecycleWorkflows/workflows/14879e66-9ea9-48d0-804d-8fea672d0341/runs/40efc576-8100-46eb-92c1-73eb43bb09a4/subjectProcessingResults/summary(startDateTime=2026-05-06T00:00:00Z,endDateTime=2026-05-13T00:00:00Z)')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->workflows()->byWorkflowId('workflow-id')->runs()->byRunId('run-id')->subjectProcessingResults()->microsoftGraphIdentityGovernanceSummaryWithStartDateTimeWithEndDateTime(new \DateTime('{endDateTime}'),new \DateTime('{startDateTime}'))->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.lifecycle_workflows.workflows.by_workflow_id('workflow-id').runs.by_run_id('run-id').subject_processing_results.microsoft_graph_identity_governance_summary_with_start_date_time_with_end_date_time("{endDateTime}","{startDateTime}").get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.identityGovernance.subjectSummary",
    "failedTasks": 3,
    "failedSubjects": 2,
    "successfulSubjects": 48,
    "totalTasks": 150,
    "totalSubjects": 50
}
```
