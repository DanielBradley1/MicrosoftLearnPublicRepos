<!-- Source: https://learn.microsoft.com/en-us/graph/api/printtaskdefinition-update-task?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update printTask

Namespace: microsoft.graph

Update a print task.

For details about how to use this API to add pull printing support to Universal Print, see [Extending Universal Print to support pull printing](https://learn.microsoft.com/en-us/graph/universal-print-concept-overview#extending-universal-print-to-support-pull-printing).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrintTaskDefinition.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /print/taskDefinitions/{taskDefinitionId}/tasks/{taskId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for the relevant [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| status | String | Include `state` and `description` values that describe the current state of the task. |

## Response

If successful, this method returns a `200 OK` response code and an updated [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/print/taskDefinitions/{taskDefinitionId}/tasks/{taskId}
Content-Type: application/json

{
  "status": {
    "state": "completed",
    "description": "completed"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PrintTask
{
	Status = new PrintTaskStatus
	{
		State = PrintTaskProcessingState.Completed,
		Description = "completed",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Print.TaskDefinitions["{printTaskDefinition-id}"].Tasks["{printTask-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewPrintTask()
status := graphmodels.NewPrintTaskStatus()
state := graphmodels.COMPLETED_PRINTTASKPROCESSINGSTATE 
status.SetState(&state) 
description := "completed"
status.SetDescription(&description) 
requestBody.SetStatus(status)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tasks, err := graphClient.Print().TaskDefinitions().ByPrintTaskDefinitionId("printTaskDefinition-id").Tasks().ByPrintTaskId("printTask-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PrintTask printTask = new PrintTask();
PrintTaskStatus status = new PrintTaskStatus();
status.setState(PrintTaskProcessingState.Completed);
status.setDescription("completed");
printTask.setStatus(status);
PrintTask result = graphClient.print().taskDefinitions().byPrintTaskDefinitionId("{printTaskDefinition-id}").tasks().byPrintTaskId("{printTask-id}").patch(printTask);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const printTask = {
  status: {
    state: 'completed',
    description: 'completed'
  }
};

await client.api('/print/taskDefinitions/{taskDefinitionId}/tasks/{taskId}')
	.update(printTask);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\PrintTask;
use Microsoft\Graph\Generated\Models\PrintTaskStatus;
use Microsoft\Graph\Generated\Models\PrintTaskProcessingState;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PrintTask();
$status = new PrintTaskStatus();
$status->setState(new PrintTaskProcessingState('completed'));
$status->setDescription('completed');
$requestBody->setStatus($status);

$result = $graphServiceClient->escapedPrint()->taskDefinitions()->byPrintTaskDefinitionId('printTaskDefinition-id')->tasks()->byPrintTaskId('printTask-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Devices.CloudPrint

$params = @{
	status = @{
		state = "completed"
		description = "completed"
	}
}

Update-MgPrintTaskDefinitionTask -PrintTaskDefinitionId $printTaskDefinitionId -PrintTaskId $printTaskId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.print_task import PrintTask
from msgraph.generated.models.print_task_status import PrintTaskStatus
from msgraph.generated.models.print_task_processing_state import PrintTaskProcessingState
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PrintTask(
	status = PrintTaskStatus(
		state = PrintTaskProcessingState.Completed,
		description = "completed",
	),
)

result = await graph_client.print.task_definitions.by_print_task_definition_id('printTaskDefinition-id').tasks.by_print_task_id('printTask-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "d036638b-1272-4bba-9227-732463823ed3",
  "parentUrl": "https://graph.microsoft.com/v1.0/print/printers/d5ef6ec4-07ca-4212-baf9-d45be126bfbb/jobs/44353",
  "status": {
    "state": "completed",
    "description": "Task execution is completed."
  }
}
```
