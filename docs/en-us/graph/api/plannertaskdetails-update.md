<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannertaskdetails-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Update plannertaskdetails

Namespace: microsoft.graph

Update the properties of **plannerTaskDetails** object.

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
PATCH /planner/tasks/{id}/details
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| If-Match | Last known ETag value for the **plannerTaskDetails** to be updated. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| checklist | [plannerChecklistItems](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitems?view=graph-rest-1.0) | The collection of checklist items on the task. |
| description | String | The description of the task. |
| previewType | string | This sets the type of preview that shows up on the task. The possible values are: `automatic`, `noPreview`, `checklist`, `description`, `reference`. When set to `automatic` the displayed preview is chosen by the app viewing the task. |
| references | [plannerExternalReferences](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreferences?view=graph-rest-1.0) | The collection of references on the task. |

## Response

If successful, this method returns a `204 No Content` response code and empty content. If the request specifies the `Prefer` header with `return=representation` preference, then this method returns a `200 OK` response code and an updated [plannerTaskDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/planner/tasks/{task-id}/details
Content-type: application/json
Prefer: return=representation
If-Match: W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="

{
  "previewType": "noPreview",
  "references": {
    "http%3A//developer%2Emicrosoft%2Ecom":{
      "@odata.type": "microsoft.graph.plannerExternalReference",
      "alias": "Documentation",
      "previewPriority": " !",
      "type": "Other"
    },
    "https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer":{
      "@odata.type": "microsoft.graph.plannerExternalReference",
      "previewPriority": "  !!",
    },
    "http%3A//www%2Ebing%2Ecom": null
  },
  "checklist": {
    "95e27074-6c4a-447a-aa24-9d718a0b86fa":{
      "@odata.type": "microsoft.graph.plannerChecklistItem",
      "title": "Update task details",
      "isChecked": true
    },
    "d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff":{
      "@odata.type": "microsoft.graph.plannerChecklistItem",
      "isChecked": true,
    },
    "a93c93c5-10a6-4167-9551-8bafa09967a7": null
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PlannerTaskDetails
{
	PreviewType = PlannerPreviewType.NoPreview,
	References = new PlannerExternalReferences
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"http%3A//developer%2Emicrosoft%2Ecom" , new PlannerExternalReference
				{
					OdataType = "microsoft.graph.plannerExternalReference",
					Alias = "Documentation",
					PreviewPriority = " !",
					Type = "Other",
				}
			},
			{
				"https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer" , new PlannerExternalReference
				{
					OdataType = "microsoft.graph.plannerExternalReference",
					PreviewPriority = "  !!",
				}
			},
			{
				"http%3A//www%2Ebing%2Ecom" , null
			},
		},
	},
	Checklist = new PlannerChecklistItems
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"95e27074-6c4a-447a-aa24-9d718a0b86fa" , new PlannerChecklistItem
				{
					OdataType = "microsoft.graph.plannerChecklistItem",
					Title = "Update task details",
					IsChecked = true,
				}
			},
			{
				"d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff" , new PlannerChecklistItem
				{
					OdataType = "microsoft.graph.plannerChecklistItem",
					IsChecked = true,
				}
			},
			{
				"a93c93c5-10a6-4167-9551-8bafa09967a7" , null
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Tasks["{plannerTask-id}"].Details.PatchAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphplanner.TasksItemDetailsRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewPlannerTaskDetails()
previewType := graphmodels.NOPREVIEW_PLANNERPREVIEWTYPE 
requestBody.SetPreviewType(&previewType) 
references := graphmodels.NewPlannerExternalReferences()
additionalData := map[string]interface{}{
http%3A//developer%2Emicrosoft%2Ecom := graphmodels.NewPlannerExternalReference()
alias := "Documentation"
http%3A//developer%2Emicrosoft%2Ecom.SetAlias(&alias) 
previewPriority := " !"
http%3A//developer%2Emicrosoft%2Ecom.SetPreviewPriority(&previewPriority) 
type := "Other"
http%3A//developer%2Emicrosoft%2Ecom.SetType(&type) 
	references.SetHttp%3A//developer%2Emicrosoft%2Ecom(http%3A//developer%2Emicrosoft%2Ecom)
"https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer" := graphmodels.NewPlannerExternalReference()
previewPriority := "  !!"
"https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer".SetPreviewPriority(&previewPriority) 
	references.Set"https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer"("https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer")
	http%3A//www%2Ebing%2Ecom := null
references.SetHttp%3A//www%2Ebing%2Ecom(&http%3A//www%2Ebing%2Ecom) 
}
references.SetAdditionalData(additionalData)
requestBody.SetReferences(references)
checklist := graphmodels.NewPlannerChecklistItems()
additionalData := map[string]interface{}{
"95e27074-6c4a-447a-aa24-9d718a0b86fa" := graphmodels.NewPlannerChecklistItem()
title := "Update task details"
"95e27074-6c4a-447a-aa24-9d718a0b86fa".SetTitle(&title) 
	isChecked := true
"95e27074-6c4a-447a-aa24-9d718a0b86fa".SetIsChecked(&isChecked) 
	checklist.Set"95e27074-6c4a-447a-aa24-9d718a0b86fa"("95e27074-6c4a-447a-aa24-9d718a0b86fa")
"d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff" := graphmodels.NewPlannerChecklistItem()
	isChecked := true
"d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff".SetIsChecked(&isChecked) 
	checklist.Set"d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff"("d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff")
	"a93c93c5-10a6-4167-9551-8bafa09967a7" := null
checklist.Set"a93c93c5-10a6-4167-9551-8bafa09967a7"(&"a93c93c5-10a6-4167-9551-8bafa09967a7") 
}
checklist.SetAdditionalData(additionalData)
requestBody.SetChecklist(checklist)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
details, err := graphClient.Planner().Tasks().ByPlannerTaskId("plannerTask-id").Details().Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerTaskDetails plannerTaskDetails = new PlannerTaskDetails();
plannerTaskDetails.setPreviewType(PlannerPreviewType.NoPreview);
PlannerExternalReferences references = new PlannerExternalReferences();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
PlannerExternalReference http3ADeveloper2Emicrosoft2Ecom = new PlannerExternalReference();
http3ADeveloper2Emicrosoft2Ecom.setOdataType("microsoft.graph.plannerExternalReference");
http3ADeveloper2Emicrosoft2Ecom.setAlias("Documentation");
http3ADeveloper2Emicrosoft2Ecom.setPreviewPriority(" !");
http3ADeveloper2Emicrosoft2Ecom.setType("Other");
additionalData.put("http%3A//developer%2Emicrosoft%2Ecom", http3ADeveloper2Emicrosoft2Ecom);
PlannerExternalReference https3ADeveloper2Emicrosoft2EcomEnUsGraphGraphExplorer = new PlannerExternalReference();
https3ADeveloper2Emicrosoft2EcomEnUsGraphGraphExplorer.setOdataType("microsoft.graph.plannerExternalReference");
https3ADeveloper2Emicrosoft2EcomEnUsGraphGraphExplorer.setPreviewPriority("  !!");
additionalData.put("https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer", https3ADeveloper2Emicrosoft2EcomEnUsGraphGraphExplorer);
additionalData.put("http%3A//www%2Ebing%2Ecom", null);
references.setAdditionalData(additionalData);
plannerTaskDetails.setReferences(references);
PlannerChecklistItems checklist = new PlannerChecklistItems();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
PlannerChecklistItem 95e270746c4a447aAa249d718a0b86fa = new PlannerChecklistItem();
95e270746c4a447aAa249d718a0b86fa.setOdataType("microsoft.graph.plannerChecklistItem");
95e270746c4a447aAa249d718a0b86fa.setTitle("Update task details");
95e270746c4a447aAa249d718a0b86fa.setIsChecked(true);
additionalData1.put("95e27074-6c4a-447a-aa24-9d718a0b86fa", 95e270746c4a447aAa249d718a0b86fa);
PlannerChecklistItem d280ed1a9f6b4f9cA962Fb4d00dc50ff = new PlannerChecklistItem();
d280ed1a9f6b4f9cA962Fb4d00dc50ff.setOdataType("microsoft.graph.plannerChecklistItem");
d280ed1a9f6b4f9cA962Fb4d00dc50ff.setIsChecked(true);
additionalData1.put("d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff", d280ed1a9f6b4f9cA962Fb4d00dc50ff);
additionalData1.put("a93c93c5-10a6-4167-9551-8bafa09967a7", null);
checklist.setAdditionalData(additionalData1);
plannerTaskDetails.setChecklist(checklist);
PlannerTaskDetails result = graphClient.planner().tasks().byPlannerTaskId("{plannerTask-id}").details().patch(plannerTaskDetails, requestConfiguration -> {
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

const plannerTaskDetails = {
  previewType: 'noPreview',
  references: {
    'http%3A//developer%2Emicrosoft%2Ecom':{
      '@odata.type': 'microsoft.graph.plannerExternalReference',
      alias: 'Documentation',
      previewPriority: ' !',
      type: 'Other'
    },
    'https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer':{
      '@odata.type': 'microsoft.graph.plannerExternalReference',
      previewPriority: '  !!',
    },
    'http%3A//www%2Ebing%2Ecom': null
  },
  checklist: {
    '95e27074-6c4a-447a-aa24-9d718a0b86fa':{
      '@odata.type': 'microsoft.graph.plannerChecklistItem',
      title: 'Update task details',
      isChecked: true
    },
    'd280ed1a-9f6b-4f9c-a962-fb4d00dc50ff':{
      '@odata.type': 'microsoft.graph.plannerChecklistItem',
      isChecked: true,
    },
    'a93c93c5-10a6-4167-9551-8bafa09967a7': null
  }
};

await client.api('/planner/tasks/{task-id}/details')
	.update(plannerTaskDetails);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Planner\Tasks\Item\Details\DetailsRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\PlannerTaskDetails;
use Microsoft\Graph\Generated\Models\PlannerPreviewType;
use Microsoft\Graph\Generated\Models\PlannerExternalReferences;
use Microsoft\Graph\Generated\Models\PlannerExternalReference;
use Microsoft\Graph\Generated\Models\PlannerChecklistItems;
use Microsoft\Graph\Generated\Models\PlannerChecklistItem;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerTaskDetails();
$requestBody->setPreviewType(new PlannerPreviewType('noPreview'));
$references = new PlannerExternalReferences();
$additionalData = [
	'http%3A//developer%2Emicrosoft%2Ecom' => [
		'@odata.type' => 'microsoft.graph.plannerExternalReference',
		'alias' => 'Documentation',
		'previewPriority' => ' !',
		'type' => 'Other',
	],
	'https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer' => [
		'@odata.type' => 'microsoft.graph.plannerExternalReference',
		'previewPriority' => '  !!',
	],
	'http%3A//www%2Ebing%2Ecom' => null,
];
$references->setAdditionalData($additionalData);
$requestBody->setReferences($references);
$checklist = new PlannerChecklistItems();
$additionalData = [
	'95e27074-6c4a-447a-aa24-9d718a0b86fa' => [
		'@odata.type' => 'microsoft.graph.plannerChecklistItem',
		'title' => 'Update task details',
		'isChecked' => true,
	],
	'd280ed1a-9f6b-4f9c-a962-fb4d00dc50ff' => [
		'@odata.type' => 'microsoft.graph.plannerChecklistItem',
		'isChecked' => true,
	],
	'a93c93c5-10a6-4167-9551-8bafa09967a7' => null,
];
$checklist->setAdditionalData($additionalData);
$requestBody->setChecklist($checklist);
$requestConfiguration = new DetailsRequestBuilderPatchRequestConfiguration();
$headers = [
		'Prefer' => 'return=representation',
		'If-Match' => 'W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->planner()->tasks()->byPlannerTaskId('plannerTask-id')->details()->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Planner

$params = @{
	previewType = "noPreview"
	references = @{
		"http%3A//developer%2Emicrosoft%2Ecom" = @{
			"@odata.type" = "microsoft.graph.plannerExternalReference"
			alias = "Documentation"
			previewPriority = " !"
			type = "Other"
		}
		"https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer" = @{
			"@odata.type" = "microsoft.graph.plannerExternalReference"
			previewPriority = "  !!"
		}
		"http%3A//www%2Ebing%2Ecom" = $null
	}
	checklist = @{
		"95e27074-6c4a-447a-aa24-9d718a0b86fa" = @{
			"@odata.type" = "microsoft.graph.plannerChecklistItem"
			title = "Update task details"
			isChecked = $true
		}
		"d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff" = @{
			"@odata.type" = "microsoft.graph.plannerChecklistItem"
			isChecked = $true
		}
		"a93c93c5-10a6-4167-9551-8bafa09967a7" = $null
	}
}

Update-MgPlannerTaskDetail -PlannerTaskId $plannerTaskId -BodyParameter $params -IfMatch W/'"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="' 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.planner.tasks.item.details.details_request_builder import DetailsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.planner_task_details import PlannerTaskDetails
from msgraph.generated.models.planner_preview_type import PlannerPreviewType
from msgraph.generated.models.planner_external_references import PlannerExternalReferences
from msgraph.generated.models.planner_external_reference import PlannerExternalReference
from msgraph.generated.models.planner_checklist_items import PlannerChecklistItems
from msgraph.generated.models.planner_checklist_item import PlannerChecklistItem
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerTaskDetails(
	preview_type = PlannerPreviewType.NoPreview,
	references = PlannerExternalReferences(
		additional_data = {
				"http%3_a//developer%2_emicrosoft%2_ecom" : {
						"@odata_type" : "microsoft.graph.plannerExternalReference",
						"alias" : "Documentation",
						"preview_priority" : " !",
						"type" : "Other",
				},
				"https%3_a//developer%2_emicrosoft%2_ecom/en-us/graph/graph-explorer" : {
						"@odata_type" : "microsoft.graph.plannerExternalReference",
						"preview_priority" : "  !!",
				},
				"http%3_a//www%2_ebing%2_ecom" : None,
		}
	),
	checklist = PlannerChecklistItems(
		additional_data = {
				"95e27074-6c4a-447a-aa24-9d718a0b86fa" : {
						"@odata_type" : "microsoft.graph.plannerChecklistItem",
						"title" : "Update task details",
						"is_checked" : True,
				},
				"d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff" : {
						"@odata_type" : "microsoft.graph.plannerChecklistItem",
						"is_checked" : True,
				},
				"a93c93c5-10a6-4167-9551-8bafa09967a7" : None,
		}
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "return=representation")
request_configuration.headers.add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"")


result = await graph_client.planner.tasks.by_planner_task_id('plannerTask-id').details.patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "description": "Task details properties:\nchecklist:Sub items\nreferences:Related links",
  "previewType": "automatic",
  "references": {
    "https%3A//developer%2Emicrosoft%2Ecom/en-us/graph/graph-explorer": {
      "@odata.type": "#microsoft.graph.plannerExternalReference",
      "alias": "Graph Explorer",
      "type": "Other",
      "previewPriority": "8599273",
      "lastModifiedBy": {
        "user": {
          "id": "fbab97d0-4932-4511-b675-204639209557"
        }
      },
      "lastModifiedDateTime": "2017-04-24T22:52:29.814Z"
    },
    "http%3A//developer%2Emicrosoft%2Ecom": {
      "@odata.type": "#microsoft.graph.plannerExternalReference",
      "alias": "Documentation",
      "type": "Other",
      "previewPriority": "90727736",
      "lastModifiedBy": {
        "user": {
          "id": "fbab97d0-4932-4511-b675-204639209557"
        }
      },
      "lastModifiedDateTime": "2017-04-24T22:52:29.814Z"
    }
  },
  "checklist": {
    "d280ed1a-9f6b-4f9c-a962-fb4d00dc50ff": {
      "@odata.type": "#microsoft.graph.plannerChecklistItem",
      "isChecked": true,
      "title": "Try reading task details",
      "orderHint": "a93c93c5^",
      "lastModifiedBy": {
        "user": {
          "id": "fbab97d0-4932-4511-b675-204639209557"
        }
      },
      "lastModifiedDateTime": "2017-04-24T22:52:29.814Z"
    },
    "95e27074-6c4a-447a-aa24-9d718a0b86f": {
      "@odata.type": "#microsoft.graph.plannerChecklistItem",
      "isChecked": true,
      "title": "Update task details",
      "orderHint": "8587094707721254251P]",
      "lastModifiedBy": {
        "user": {
          "id": "fbab97d0-4932-4511-b675-204639209557"
        }
      },
      "lastModifiedDateTime": "2017-04-24T22:52:29.814Z"
    }
  },
  "id": "gcrYAaAkgU2EQUvpkNNXLGQAGTtu"
}
```
