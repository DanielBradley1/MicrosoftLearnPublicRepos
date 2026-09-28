<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannerplandetails-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update plannerplandetails

Namespace: microsoft.graph

Update the properties of **plannerplandetails** object.

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
PATCH /planner/plans/{id}/details
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | Last known ETag value for the plannerPlanDetails to be updated. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| categoryDescriptions | [plannerCategoryDescriptions](https://learn.microsoft.com/en-us/graph/api/resources/plannercategorydescriptions?view=graph-rest-1.0) | An object that specifies the descriptions of the six categories that can be associated with tasks in the plan |
| sharedWith | [plannerUserIds](https://learn.microsoft.com/en-us/graph/api/resources/planneruserids?view=graph-rest-1.0) | Set of user ids that this plan is shared with. If you're using Microsoft 365 groups, use the Groups API to manage group membership to share the [group's](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) plan. You can also add existing members of the group to this collection though it isn't required for them to access the plan owned by the group. |

## Response

If successful, this method returns `204 No Content` response and empty content. If the request specifies `Prefer` header with `return=representation` preference, then this method returns a `200 OK` response code and updated [plannerPlanDetails](https://learn.microsoft.com/en-us/graph/api/resources/plannerplandetails?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/planner/plans/{plan-id}/details
Content-type: application/json
Prefer: return=representation
If-Match: W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="

{
  "sharedWith": {
    "6463a5ce-2119-4198-9f2a-628761df4a62" : true,
    "d95e6152-f683-4d78-9ff5-67ad180fea4a" : false,
  },
  "categoryDescriptions": {
    "category1": "Indoors",
    "category3": null,
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new PlannerPlanDetails
{
	SharedWith = new PlannerUserIds
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"6463a5ce-2119-4198-9f2a-628761df4a62" , true
			},
			{
				"d95e6152-f683-4d78-9ff5-67ad180fea4a" , false
			},
		},
	},
	CategoryDescriptions = new PlannerCategoryDescriptions
	{
		Category1 = "Indoors",
		Category3 = null,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Plans["{plannerPlan-id}"].Details.PatchAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphplanner.PlansItemDetailsRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewPlannerPlanDetails()
sharedWith := graphmodels.NewPlannerUserIds()
additionalData := map[string]interface{}{
	"6463a5ce-2119-4198-9f2a-628761df4a62" := true
sharedWith.Set"6463a5ce-2119-4198-9f2a-628761df4a62"(&"6463a5ce-2119-4198-9f2a-628761df4a62") 
	"d95e6152-f683-4d78-9ff5-67ad180fea4a" := false
sharedWith.Set"d95e6152-f683-4d78-9ff5-67ad180fea4a"(&"d95e6152-f683-4d78-9ff5-67ad180fea4a") 
}
sharedWith.SetAdditionalData(additionalData)
requestBody.SetSharedWith(sharedWith)
categoryDescriptions := graphmodels.NewPlannerCategoryDescriptions()
category1 := "Indoors"
categoryDescriptions.SetCategory1(&category1) 
category3 := null
categoryDescriptions.SetCategory3(&category3) 
requestBody.SetCategoryDescriptions(categoryDescriptions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
details, err := graphClient.Planner().Plans().ByPlannerPlanId("plannerPlan-id").Details().Patch(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerPlanDetails plannerPlanDetails = new PlannerPlanDetails();
PlannerUserIds sharedWith = new PlannerUserIds();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("6463a5ce-2119-4198-9f2a-628761df4a62", true);
additionalData.put("d95e6152-f683-4d78-9ff5-67ad180fea4a", false);
sharedWith.setAdditionalData(additionalData);
plannerPlanDetails.setSharedWith(sharedWith);
PlannerCategoryDescriptions categoryDescriptions = new PlannerCategoryDescriptions();
categoryDescriptions.setCategory1("Indoors");
categoryDescriptions.setCategory3(null);
plannerPlanDetails.setCategoryDescriptions(categoryDescriptions);
PlannerPlanDetails result = graphClient.planner().plans().byPlannerPlanId("{plannerPlan-id}").details().patch(plannerPlanDetails, requestConfiguration -> {
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

const plannerPlanDetails = {
  sharedWith: {
    '6463a5ce-2119-4198-9f2a-628761df4a62': true,
    'd95e6152-f683-4d78-9ff5-67ad180fea4a': false,
  },
  categoryDescriptions: {
    category1: 'Indoors',
    category3: null,
  }
};

await client.api('/planner/plans/{plan-id}/details')
	.update(plannerPlanDetails);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Planner\Plans\Item\Details\DetailsRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Generated\Models\PlannerPlanDetails;
use Microsoft\Graph\Generated\Models\PlannerUserIds;
use Microsoft\Graph\Generated\Models\PlannerCategoryDescriptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerPlanDetails();
$sharedWith = new PlannerUserIds();
$additionalData = [
	'6463a5ce-2119-4198-9f2a-628761df4a62' => true,
	'd95e6152-f683-4d78-9ff5-67ad180fea4a' => false,
];
$sharedWith->setAdditionalData($additionalData);
$requestBody->setSharedWith($sharedWith);
$categoryDescriptions = new PlannerCategoryDescriptions();
$categoryDescriptions->setCategory1('Indoors');
$categoryDescriptions->setCategory3(null);
$requestBody->setCategoryDescriptions($categoryDescriptions);
$requestConfiguration = new DetailsRequestBuilderPatchRequestConfiguration();
$headers = [
		'Prefer' => 'return=representation',
		'If-Match' => 'W/"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->planner()->plans()->byPlannerPlanId('plannerPlan-id')->details()->patch($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Planner

$params = @{
	sharedWith = @{
		"6463a5ce-2119-4198-9f2a-628761df4a62" = $true
		"d95e6152-f683-4d78-9ff5-67ad180fea4a" = $false
	}
	categoryDescriptions = @{
		category1 = "Indoors"
		category3 = $null
	}
}

Update-MgPlannerPlanDetail -PlannerPlanId $plannerPlanId -BodyParameter $params -IfMatch W/'"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc="' 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.planner.plans.item.details.details_request_builder import DetailsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.planner_plan_details import PlannerPlanDetails
from msgraph.generated.models.planner_user_ids import PlannerUserIds
from msgraph.generated.models.planner_category_descriptions import PlannerCategoryDescriptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerPlanDetails(
	shared_with = PlannerUserIds(
		additional_data = {
				"6463a5ce-2119-4198-9f2a-628761df4a62" : True,
				"d95e6152-f683-4d78-9ff5-67ad180fea4a" : False,
		}
	),
	category_descriptions = PlannerCategoryDescriptions(
		category1 = "Indoors",
		category3 = None,
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "return=representation")
request_configuration.headers.add("If-Match", "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBAWCc=\"")


result = await graph_client.planner.plans.by_planner_plan_id('plannerPlan-id').details.patch(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "sharedWith": {
    "aaa27244-1db4-476a-a5cb-004607466324" : true,
    "6463a5ce-2119-4198-9f2a-628761df4a62" : true
  },
  "categoryDescriptions": {
    "category1": "Indoors",
    "category2": "Outdoors",
    "category3": null,
    "category4": null,
    "category5": "Needs materials",
    "category6": "Needs equipment",
    "category7": "Description of category 7",
    "category8": "Description of category 8",
    "category9": "Description of category 9",
    "category10": "Description of category 10",
    "category11": "Description of category 11",
    "category12": "Description of category 12",
    "category13": "Description of category 13",
    "category14": "Description of category 14",
    "category15": "Description of category 15",
    "category16": "Description of category 16",
    "category17": "Description of category 17",
    "category18": "Description of category 18",
    "category19": "Description of category 19",
    "category20": "Description of category 20",
    "category21": "Description of category 21",
    "category22": "Description of category 22",
    "category23": "Description of category 23",
    "category24": "Description of category 24",
    "category25": "Description of category 25"
  },
  "id": "xqQg5FS2LkCp935s-FIFm2QAFkHM"
}
```
