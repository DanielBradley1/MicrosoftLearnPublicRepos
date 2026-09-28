<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannerassignedtotaskboardtaskformat-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update plannerAssignedToTaskBoardTaskFormat

Namespace: microsoft.graph

Update the properties of **plannerAssignedToTaskBoardTaskFormat** object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.ReadWrite | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /planner/tasks/{id}/assignedToTaskBoardFormat
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | Last known ETag value for **plannerAssignedToTaskBoardTaskFormat** to be updated. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| orderHintsByAssignee | [plannerOrderHintsByAssignee](https://learn.microsoft.com/en-us/graph/api/resources/plannerorderhintsbyassignee?view=graph-rest-1.0) | Dictionary of hints used to order tasks on the AssignedTo view of the Task Board. The key of each entry is one of the users the task is assigned to and the value is the order hint. The format of each value is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| unassignedOrderHint | String | Hint value used to order the task on the AssignedTo view of the Task Board when the task is not assigned to anyone, or if the orderHintsByAssignee dictionary doesn't provide an order hint for the user the task is assigned to. The format is defined as outlined [here](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |

## Response

If successful, this method returns `204 No Content` response and empty content. If the request specifies `Prefer` header with `return=representation` preference, then this method returns a `200 OK` response code and updated [plannerAssignedToTaskBoardTaskFormat](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignedtotaskboardtaskformat?view=graph-rest-1.0) object in the response body.

This method can return any of the [HTTP status codes](https://learn.microsoft.com/en-us/graph/errors). The most common errors that apps should handle for this method are the 400, 403, 404, 409, and 412 responses. For more information about these errors, see [Common Planner error conditions](https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-1.0#common-planner-error-conditions).

## Example

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
PATCH https://graph.microsoft.com/v1.0/planner/tasks/{task-id}/assignedToTaskBoardFormat
Content-type: application/json
Prefer: return=representation
If-Match: W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="

{
  "orderHintsByAssignee": {
    "aaa27244-1db4-476a-a5cb-004607466324": "8566473P 957764Jk!"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PlannerAssignedToTaskBoardTaskFormat
{
	OrderHintsByAssignee = new PlannerOrderHintsByAssignee
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"aaa27244-1db4-476a-a5cb-004607466324" , "8566473P 957764Jk!"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Tasks["{plannerTask-id}"].AssignedToTaskBoardFormat.PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "return=representation");
	requestConfiguration.Headers.Add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphplanner "github.com/microsoftgraph/msgraph-sdk-go/planner"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "return=representation")
headers.Add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"")

configuration := &graphplanner.TasksItemAssignedToTaskBoardFormatRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewPlannerAssignedToTaskBoardTaskFormat()
orderHintsByAssignee := graphmodels.NewPlannerOrderHintsByAssignee()
additionalData := map[string]interface{}{
	"aaa27244-1db4-476a-a5cb-004607466324" : "8566473P 957764Jk!", 
}
orderHintsByAssignee.SetAdditionalData(additionalData)
requestBody.SetOrderHintsByAssignee(orderHintsByAssignee)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignedToTaskBoardFormat, err := graphClient.Planner().Tasks().ByPlannerTaskId("plannerTask-id").AssignedToTaskBoardFormat().Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerAssignedToTaskBoardTaskFormat plannerAssignedToTaskBoardTaskFormat = new PlannerAssignedToTaskBoardTaskFormat();
PlannerOrderHintsByAssignee orderHintsByAssignee = new PlannerOrderHintsByAssignee();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("aaa27244-1db4-476a-a5cb-004607466324", "8566473P 957764Jk!");
orderHintsByAssignee.setAdditionalData(additionalData);
plannerAssignedToTaskBoardTaskFormat.setOrderHintsByAssignee(orderHintsByAssignee);
PlannerAssignedToTaskBoardTaskFormat result = graphClient.planner().tasks().byPlannerTaskId("{plannerTask-id}").assignedToTaskBoardFormat().patch(plannerAssignedToTaskBoardTaskFormat, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "return=representation");
	requestConfiguration.headers.add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const plannerAssignedToTaskBoardTaskFormat = {
  orderHintsByAssignee: {
    'aaa27244-1db4-476a-a5cb-004607466324': '8566473P 957764Jk!'
  }
};

await client.api('/planner/tasks/{task-id}/assignedToTaskBoardFormat')
	.update(plannerAssignedToTaskBoardTaskFormat);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Planner\Tasks\Item\AssignedToTaskBoardFormat\AssignedToTaskBoardFormatRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\PlannerAssignedToTaskBoardTaskFormat;
use Microsoft\Graph\Generated\Models\PlannerOrderHintsByAssignee;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerAssignedToTaskBoardTaskFormat();
$orderHintsByAssignee = new PlannerOrderHintsByAssignee();
$additionalData = [
	'aaa27244-1db4-476a-a5cb-004607466324' => '8566473P 957764Jk!',
];
$orderHintsByAssignee->setAdditionalData($additionalData);
$requestBody->setOrderHintsByAssignee($orderHintsByAssignee);
$requestConfiguration = new AssignedToTaskBoardFormatRequestBuilderPatchRequestConfiguration();
$headers = [
		'Prefer' => 'return=representation',
		'If-Match' => 'W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->planner()->tasks()->byPlannerTaskId('plannerTask-id')->assignedToTaskBoardFormat()->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Planner

$params = @{
	orderHintsByAssignee = @{
		"aaa27244-1db4-476a-a5cb-004607466324" = "8566473P 957764Jk!"
	}
}

Update-MgPlannerTaskAssignedToTaskBoardFormat -PlannerTaskId $plannerTaskId -BodyParameter $params -IfMatch W/'"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="' 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.planner.tasks.item.assigned_to_task_board_format.assigned_to_task_board_format_request_builder import AssignedToTaskBoardFormatRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.planner_assigned_to_task_board_task_format import PlannerAssignedToTaskBoardTaskFormat
from msgraph.generated.models.planner_order_hints_by_assignee import PlannerOrderHintsByAssignee
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerAssignedToTaskBoardTaskFormat(
	order_hints_by_assignee = PlannerOrderHintsByAssignee(
		additional_data = {
				"aaa27244-1db4-476a-a5cb-004607466324" : "8566473P 957764Jk!",
		}
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "return=representation")
request_configuration.headers.add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"")


result = await graph_client.planner.tasks.by_planner_task_id('plannerTask-id').assigned_to_task_board_format.patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "unassignedOrderHint": "RWk1",
  "orderHintsByAssignee": {
    "6463a5ce-2119-4198-9f2a-628761df4a62":"85752723360752+",
    "aaa27244-1db4-476a-a5cb-004607466324":"90057581;"
  },
  "id": "01gzSlKkIUSUl6DF_EilrmQAKDhh"
}
```
