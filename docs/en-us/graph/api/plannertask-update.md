<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannertask-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update plannerTask

Namespace: microsoft.graph

Update the properties of **plannerTask** object.

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
PATCH /planner/tasks/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | Last known ETag value for the **plannerTask** to be updated. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| appliedCategories | [plannerAppliedCategories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-1.0) | The categories to which the task has been applied. For possible values, see [appliedCategories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-1.0). |
| assigneePriority | String | Hint used to order items of this type in a list view. The format is defined in [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| assignments | [plannerAssignments](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignments?view=graph-rest-1.0) | The set of users the task is assigned to. |
| bucketId | String | Bucket ID to which the task belongs. The bucket needs to be in the plan that the task is in. The value is 28 characters long and case-sensitive. [Format validation](https://learn.microsoft.com/en-us/graph/api/resources/planner-identifiers-disclaimer?view=graph-rest-1.0) is done on the service. |
| conversationThreadId | String | Thread ID of the conversation on the task. This is the ID of the conversation thread object created in the group. |
| dueDateTime | DateTimeOffset | Date and time at which the task is due. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| orderHint | String | Hint used to order items of this type in a list view. The format is defined in [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-1.0). |
| priority | Int32 | Priority of the task. The valid range of values is between `0` and `10`, with the increasing value being lower priority \(`0` has the highest priority and `10` has the lowest priority\). Currently, Planner interprets values `0` and `1` as "urgent", `2`, `3` and `4` as "important", `5`, `6`, and `7` as "medium", and `8`, `9`, and `10` as "low". Additionally, Planner sets the value `1` for "urgent", `3` for "important", `5` for "medium", and `9` for "low". |
| percentComplete | Int32 | Percentage of task completion. When set to `100`, the task is considered completed. |
| startDateTime | DateTimeOffset | Date and time at which the task starts. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| title | String | Title of the task. |

Note

For Project tasks that are replicated to Planner, only the **percentComplete** property can be updated.

## Response

If successful, this method returns a `204 No Content` response code and an empty content. If the request specifies the `Prefer` header with a `return=representation` preference, then this method returns a `200 OK` response code and an updated [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/planner/tasks/{task-id}
Content-type: application/json
Prefer: return=representation
If-Match: W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="

{
  "assignments": {
    "fbab97d0-4932-4511-b675-204639209557": {
      "@odata.type": "#microsoft.graph.plannerAssignment",
      "orderHint": "N9917 U2883!"
    }
  },
  "appliedCategories": {
    "category3": true,
    "category4": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PlannerTask
{
	Assignments = new PlannerAssignments
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"fbab97d0-4932-4511-b675-204639209557" , new PlannerAssignment
				{
					OdataType = "#microsoft.graph.plannerAssignment",
					OrderHint = "N9917 U2883!",
				}
			},
		},
	},
	AppliedCategories = new PlannerAppliedCategories
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"category3" , true
			},
			{
				"category4" , false
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Tasks["{plannerTask-id}"].PatchAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphplanner.TasksItemRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewPlannerTask()
assignments := graphmodels.NewPlannerAssignments()
additionalData := map[string]interface{}{
"fbab97d0-4932-4511-b675-204639209557" := graphmodels.NewPlannerAssignment()
orderHint := "N9917 U2883!"
"fbab97d0-4932-4511-b675-204639209557".SetOrderHint(&orderHint) 
	assignments.Set"fbab97d0-4932-4511-b675-204639209557"("fbab97d0-4932-4511-b675-204639209557")
}
assignments.SetAdditionalData(additionalData)
requestBody.SetAssignments(assignments)
appliedCategories := graphmodels.NewPlannerAppliedCategories()
additionalData := map[string]interface{}{
	category3 := true
appliedCategories.SetCategory3(&category3) 
	category4 := false
appliedCategories.SetCategory4(&category4) 
}
appliedCategories.SetAdditionalData(additionalData)
requestBody.SetAppliedCategories(appliedCategories)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tasks, err := graphClient.Planner().Tasks().ByPlannerTaskId("plannerTask-id").Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerTask plannerTask = new PlannerTask();
PlannerAssignments assignments = new PlannerAssignments();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
PlannerAssignment fbab97d049324511B675204639209557 = new PlannerAssignment();
fbab97d049324511B675204639209557.setOdataType("#microsoft.graph.plannerAssignment");
fbab97d049324511B675204639209557.setOrderHint("N9917 U2883!");
additionalData.put("fbab97d0-4932-4511-b675-204639209557", fbab97d049324511B675204639209557);
assignments.setAdditionalData(additionalData);
plannerTask.setAssignments(assignments);
PlannerAppliedCategories appliedCategories = new PlannerAppliedCategories();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("category3", true);
additionalData1.put("category4", false);
appliedCategories.setAdditionalData(additionalData1);
plannerTask.setAppliedCategories(appliedCategories);
PlannerTask result = graphClient.planner().tasks().byPlannerTaskId("{plannerTask-id}").patch(plannerTask, requestConfiguration -> {
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

const plannerTask = {
  assignments: {
    'fbab97d0-4932-4511-b675-204639209557': {
      '@odata.type': '#microsoft.graph.plannerAssignment',
      orderHint: 'N9917 U2883!'
    }
  },
  appliedCategories: {
    category3: true,
    category4: false
  }
};

await client.api('/planner/tasks/{task-id}')
	.update(plannerTask);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Planner\Tasks\Item\PlannerTaskItemRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\PlannerTask;
use Microsoft\Graph\Generated\Models\PlannerAssignments;
use Microsoft\Graph\Generated\Models\PlannerAssignment;
use Microsoft\Graph\Generated\Models\PlannerAppliedCategories;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerTask();
$assignments = new PlannerAssignments();
$additionalData = [
	'fbab97d0-4932-4511-b675-204639209557' => [
		'@odata.type' => '#microsoft.graph.plannerAssignment',
		'orderHint' => 'N9917 U2883!',
	],
];
$assignments->setAdditionalData($additionalData);
$requestBody->setAssignments($assignments);
$appliedCategories = new PlannerAppliedCategories();
$additionalData = [
	'category3' => true,
	'category4' => false,
];
$appliedCategories->setAdditionalData($additionalData);
$requestBody->setAppliedCategories($appliedCategories);
$requestConfiguration = new PlannerTaskItemRequestBuilderPatchRequestConfiguration();
$headers = [
		'Prefer' => 'return=representation',
		'If-Match' => 'W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->planner()->tasks()->byPlannerTaskId('plannerTask-id')->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Planner

$params = @{
	assignments = @{
		"fbab97d0-4932-4511-b675-204639209557" = @{
			"@odata.type" = "#microsoft.graph.plannerAssignment"
			orderHint = "N9917 U2883!"
		}
	}
	appliedCategories = @{
		category3 = $true
		category4 = $false
	}
}

Update-MgPlannerTask -PlannerTaskId $plannerTaskId -BodyParameter $params -IfMatch W/'"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="' 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.planner.tasks.item.planner_task_item_request_builder import PlannerTaskItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.planner_task import PlannerTask
from msgraph.generated.models.planner_assignments import PlannerAssignments
from msgraph.generated.models.planner_assignment import PlannerAssignment
from msgraph.generated.models.planner_applied_categories import PlannerAppliedCategories
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerTask(
	assignments = PlannerAssignments(
		additional_data = {
				"fbab97d0-4932-4511-b675-204639209557" : {
						"@odata_type" : "#microsoft.graph.plannerAssignment",
						"order_hint" : "N9917 U2883!",
				},
		}
	),
	applied_categories = PlannerAppliedCategories(
		additional_data = {
				"category3" : True,
				"category4" : False,
		}
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "return=representation")
request_configuration.headers.add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"")


result = await graph_client.planner.tasks.by_planner_task_id('plannerTask-id').patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "createdBy": {
    "user": {
      "id": "6463a5ce-2119-4198-9f2a-628761df4a62"
    }
  },
  "planId": "xqQg5FS2LkCp935s-FIFm2QAFkHM",
  "bucketId": "gcrYAaAkgU2EQUvpkNNXLGQAGTtu",
  "title": "title-value",
  "orderHint": "9223370609546166567W",
  "assigneePriority": "90057581\"",
  "createdDateTime": "2015-03-24T18:36:49.2407981Z",
  "assignments": {
    "6463a5ce-2119-4198-9f2a-628761df4a62": {
      "@odata.type": "#microsoft.graph.plannerAssignment",
      "assignedBy": {
        "user": {
          "id": "6463a5ce-2119-4198-9f2a-628761df4a62"
        }
      },
      "assignedDateTime": "2015-03-25T18:38:21.956Z",
      "orderHint": "N9917"
    },
    "fbab97d0-4932-4511-b675-204639209557": {
      "@odata.type": "#microsoft.graph.plannerAssignment",
      "assignedBy": {
        "user": {
          "id": "1e9955d2-6acd-45bf-86d3-b546fdc795eb"
        }
      },
      "assignedDateTime": "2017-04-24T22:40:44.5665917",
      "orderHint": "RWk1"
    },
    "aaa27244-1db4-476a-a5cb-004607466324": {
      "@odata.type": "#microsoft.graph.plannerAssignment",
      "assignedBy": {
        "user": {
          "id": "6463a5ce-2119-4198-9f2a-628761df4a62"
        }
      },
      "assignedDateTime": "2015-03-25T18:38:21.956Z",
      "orderHint": "U2883"
    }
  },
  "appliedCategories": {
    "category3": true,
    "category5": true,
    "category6": true,
  },
  "id":"01gzSlKkIUSUl6DF_EilrmQAKDhh",
  "priority": 5
}
```
