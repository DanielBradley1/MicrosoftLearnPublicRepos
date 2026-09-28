<!-- Source: https://learn.microsoft.com/en-us/graph/api/planneruser-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-25 -->

# Update plannerUser

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [plannerUser](https://learn.microsoft.com/en-us/graph/api/resources/planneruser?view=graph-rest-beta) object. You can use this operation to add or remove plans from a user's favorite plans list, and to indicate which plans the user has recently viewed.

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
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/planner
```

## Optional request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |
| If-Match | Last known ETag value for the **plannerUser** to be updated. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

| Property | Type | Description |
| :--- | :--- | :--- |
| favoritePlanReferences | [plannerFavoritePlanReferenceCollection](https://learn.microsoft.com/en-us/graph/api/resources/plannerfavoriteplanreferencecollection?view=graph-rest-beta) | Changes to the collection containing the references to the plans that the user has marked as a favorite. |
| recentPlanReferences | [plannerRecentPlanReferenceCollection](https://learn.microsoft.com/en-us/graph/api/resources/plannerrecentplanreferencecollection?view=graph-rest-beta) | Changes to the collection containing the references to the plans that the user has recently viewed. |

## Response

If successful, this method returns `204 No Content` response and empty content. If the request specifies `Prefer` header with `return=representation` preference, then this method returns a `200 OK` response code and an updated [plannerUser](https://learn.microsoft.com/en-us/graph/api/resources/planneruser?view=graph-rest-beta) object in the response body.

This method can return any of the [HTTP status codes](https://learn.microsoft.com/en-us/graph/errors). The most common errors that apps should handle for this method are the 400, 403, 404, 409, and 412 responses. For more information about these errors, see [Common Planner error conditions](https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-beta#common-planner-error-conditions).

## Example

### Request

The following example shows a request. This request adds the plan "Next Release Discussion" with ID "jd8S5gOaFk2S8aWCIAJz42QAAxtD" as a favorite for the user, and removes plan with ID "7oTB5aMIAE2rVo-1N-L7RmQAGX2q" from the favorite plans list. It also updates the last view time of the plan "jd8S5gOaFk2S8aWCIAJz42QAAxtD".

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/me/planner
Content-type: application/json
Prefer: return=representation
If-Match: W/"JzEtVXNlckRldGFpbHMgQEBAQEBAQEBAQEBAQEBIWCc="

{
  "favoritePlanReferences": {
    "jd8S5gOaFk2S8aWCIAJz42QAAxtD": {
      "@odata.type": "#microsoft.graph.plannerFavoritePlanReference",
      "orderHint": " !",
      "planTitle": "Next Release Discussion"
    },
    "7oTB5aMIAE2rVo-1N-L7RmQAGX2q": null
  },
  "recentPlanReferences": {
    "jd8S5gOaFk2S8aWCIAJz42QAAxtD": {
      "@odata.type": "#microsoft.graph.plannerRecentPlanReference",
      "lastAccessedDateTime": "2018-01-02T22:49:46.155Z",
      "planTitle": "Next Release Discussion"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PlannerUser
{
	FavoritePlanReferences = new PlannerFavoritePlanReferenceCollection
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"jd8S5gOaFk2S8aWCIAJz42QAAxtD" , new PlannerFavoritePlanReference
				{
					OdataType = "#microsoft.graph.plannerFavoritePlanReference",
					OrderHint = " !",
					PlanTitle = "Next Release Discussion",
				}
			},
			{
				"7oTB5aMIAE2rVo-1N-L7RmQAGX2q" , null
			},
		},
	},
	RecentPlanReferences = new PlannerRecentPlanReferenceCollection
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"jd8S5gOaFk2S8aWCIAJz42QAAxtD" , new PlannerRecentPlanReference
				{
					OdataType = "#microsoft.graph.plannerRecentPlanReference",
					LastAccessedDateTime = DateTimeOffset.Parse("2018-01-02T22:49:46.155Z"),
					PlanTitle = "Next Release Discussion",
				}
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Planner.PatchAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "return=representation");
	requestConfiguration.Headers.Add("If-Match", "W/\"JzEtVXNlckRldGFpbHMgQEBAQEBAQEBAQEBAQEBIWCc=\"");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "return=representation")
headers.Add("If-Match", "W/\"JzEtVXNlckRldGFpbHMgQEBAQEBAQEBAQEBAQEBIWCc=\"")

configuration := &graphusers.ItemPlannerRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewPlannerUser()
favoritePlanReferences := graphmodels.NewPlannerFavoritePlanReferenceCollection()
additionalData := map[string]interface{}{
jd8S5gOaFk2S8aWCIAJz42QAAxtD := graphmodels.NewPlannerFavoritePlanReference()
orderHint := " !"
jd8S5gOaFk2S8aWCIAJz42QAAxtD.SetOrderHint(&orderHint) 
planTitle := "Next Release Discussion"
jd8S5gOaFk2S8aWCIAJz42QAAxtD.SetPlanTitle(&planTitle) 
	favoritePlanReferences.SetJd8S5gOaFk2S8aWCIAJz42QAAxtD(jd8S5gOaFk2S8aWCIAJz42QAAxtD)
	"7oTB5aMIAE2rVo-1N-L7RmQAGX2q" := null
favoritePlanReferences.Set"7oTB5aMIAE2rVo-1N-L7RmQAGX2q"(&"7oTB5aMIAE2rVo-1N-L7RmQAGX2q") 
}
favoritePlanReferences.SetAdditionalData(additionalData)
requestBody.SetFavoritePlanReferences(favoritePlanReferences)
recentPlanReferences := graphmodels.NewPlannerRecentPlanReferenceCollection()
additionalData := map[string]interface{}{
jd8S5gOaFk2S8aWCIAJz42QAAxtD := graphmodels.NewPlannerRecentPlanReference()
lastAccessedDateTime , err := time.Parse(time.RFC3339, "2018-01-02T22:49:46.155Z")
jd8S5gOaFk2S8aWCIAJz42QAAxtD.SetLastAccessedDateTime(&lastAccessedDateTime) 
planTitle := "Next Release Discussion"
jd8S5gOaFk2S8aWCIAJz42QAAxtD.SetPlanTitle(&planTitle) 
	recentPlanReferences.SetJd8S5gOaFk2S8aWCIAJz42QAAxtD(jd8S5gOaFk2S8aWCIAJz42QAAxtD)
}
recentPlanReferences.SetAdditionalData(additionalData)
requestBody.SetRecentPlanReferences(recentPlanReferences)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
planner, err := graphClient.Me().Planner().Patch(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerUser plannerUser = new PlannerUser();
PlannerFavoritePlanReferenceCollection favoritePlanReferences = new PlannerFavoritePlanReferenceCollection();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
PlannerFavoritePlanReference jd8S5gOaFk2S8aWCIAJz42QAAxtD = new PlannerFavoritePlanReference();
jd8S5gOaFk2S8aWCIAJz42QAAxtD.setOdataType("#microsoft.graph.plannerFavoritePlanReference");
jd8S5gOaFk2S8aWCIAJz42QAAxtD.setOrderHint(" !");
jd8S5gOaFk2S8aWCIAJz42QAAxtD.setPlanTitle("Next Release Discussion");
additionalData.put("jd8S5gOaFk2S8aWCIAJz42QAAxtD", jd8S5gOaFk2S8aWCIAJz42QAAxtD);
additionalData.put("7oTB5aMIAE2rVo-1N-L7RmQAGX2q", null);
favoritePlanReferences.setAdditionalData(additionalData);
plannerUser.setFavoritePlanReferences(favoritePlanReferences);
PlannerRecentPlanReferenceCollection recentPlanReferences = new PlannerRecentPlanReferenceCollection();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
PlannerRecentPlanReference jd8S5gOaFk2S8aWCIAJz42QAAxtD1 = new PlannerRecentPlanReference();
jd8S5gOaFk2S8aWCIAJz42QAAxtD1.setOdataType("#microsoft.graph.plannerRecentPlanReference");
OffsetDateTime lastAccessedDateTime = OffsetDateTime.parse("2018-01-02T22:49:46.155Z");
jd8S5gOaFk2S8aWCIAJz42QAAxtD1.setLastAccessedDateTime(lastAccessedDateTime);
jd8S5gOaFk2S8aWCIAJz42QAAxtD1.setPlanTitle("Next Release Discussion");
additionalData1.put("jd8S5gOaFk2S8aWCIAJz42QAAxtD", jd8S5gOaFk2S8aWCIAJz42QAAxtD1);
recentPlanReferences.setAdditionalData(additionalData1);
plannerUser.setRecentPlanReferences(recentPlanReferences);
PlannerUser result = graphClient.me().planner().patch(plannerUser, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "return=representation");
	requestConfiguration.headers.add("If-Match", "W/\"JzEtVXNlckRldGFpbHMgQEBAQEBAQEBAQEBAQEBIWCc=\"");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const plannerUser = {
  favoritePlanReferences: {
    jd8S5gOaFk2S8aWCIAJz42QAAxtD: {
      '@odata.type': '#microsoft.graph.plannerFavoritePlanReference',
      orderHint: ' !',
      planTitle: 'Next Release Discussion'
    },
    '7oTB5aMIAE2rVo-1N-L7RmQAGX2q': null
  },
  recentPlanReferences: {
    jd8S5gOaFk2S8aWCIAJz42QAAxtD: {
      '@odata.type': '#microsoft.graph.plannerRecentPlanReference',
      lastAccessedDateTime: '2018-01-02T22:49:46.155Z',
      planTitle: 'Next Release Discussion'
    }
  }
};

await client.api('/me/planner')
	.version('beta')
	.update(plannerUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Planner\PlannerRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\PlannerUser;
use Microsoft\Graph\Beta\Generated\Models\PlannerFavoritePlanReferenceCollection;
use Microsoft\Graph\Beta\Generated\Models\PlannerFavoritePlanReference;
use Microsoft\Graph\Beta\Generated\Models\PlannerRecentPlanReferenceCollection;
use Microsoft\Graph\Beta\Generated\Models\PlannerRecentPlanReference;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerUser();
$favoritePlanReferences = new PlannerFavoritePlanReferenceCollection();
$additionalData = [
	'jd8S5gOaFk2S8aWCIAJz42QAAxtD' => [
		'@odata.type' => '#microsoft.graph.plannerFavoritePlanReference',
		'orderHint' => ' !',
		'planTitle' => 'Next Release Discussion',
	],
	'7oTB5aMIAE2rVo-1N-L7RmQAGX2q' => null,
];
$favoritePlanReferences->setAdditionalData($additionalData);
$requestBody->setFavoritePlanReferences($favoritePlanReferences);
$recentPlanReferences = new PlannerRecentPlanReferenceCollection();
$additionalData = [
	'jd8S5gOaFk2S8aWCIAJz42QAAxtD' => [
		'@odata.type' => '#microsoft.graph.plannerRecentPlanReference',
		'lastAccessedDateTime' => new \DateTime('2018-01-02T22:49:46.155Z'),
		'planTitle' => 'Next Release Discussion',
	],
];
$recentPlanReferences->setAdditionalData($additionalData);
$requestBody->setRecentPlanReferences($recentPlanReferences);
$requestConfiguration = new PlannerRequestBuilderPatchRequestConfiguration();
$headers = [
		'Prefer' => 'return=representation',
		'If-Match' => 'W/"JzEtVXNlckRldGFpbHMgQEBAQEBAQEBAQEBAQEBIWCc="',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->me()->planner()->patch($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

$params = @{
	favoritePlanReferences = @{
		jd8S5gOaFk2S8aWCIAJz42QAAxtD = @{
			"@odata.type" = "#microsoft.graph.plannerFavoritePlanReference"
			orderHint = " !"
			planTitle = "Next Release Discussion"
		}
		"7oTB5aMIAE2rVo-1N-L7RmQAGX2q" = $null
	}
	recentPlanReferences = @{
		jd8S5gOaFk2S8aWCIAJz42QAAxtD = @{
			"@odata.type" = "#microsoft.graph.plannerRecentPlanReference"
			lastAccessedDateTime = "2018-01-02T22:49:46.155Z"
			planTitle = "Next Release Discussion"
		}
	}
}

# A UPN can also be used as -UserId.
Update-MgBetaUserPlanner -UserId $userId -BodyParameter $params -IfMatch W/'"JzEtVXNlckRldGFpbHMgQEBAQEBAQEBAQEBAQEBIWCc="' 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.planner.planner_request_builder import PlannerRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.planner_user import PlannerUser
from msgraph_beta.generated.models.planner_favorite_plan_reference_collection import PlannerFavoritePlanReferenceCollection
from msgraph_beta.generated.models.planner_favorite_plan_reference import PlannerFavoritePlanReference
from msgraph_beta.generated.models.planner_recent_plan_reference_collection import PlannerRecentPlanReferenceCollection
from msgraph_beta.generated.models.planner_recent_plan_reference import PlannerRecentPlanReference
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerUser(
	favorite_plan_references = PlannerFavoritePlanReferenceCollection(
		additional_data = {
				"jd8_s5g_oa_fk2_s8a_w_c_i_a_jz42_q_a_axt_d" : {
						"@odata_type" : "#microsoft.graph.plannerFavoritePlanReference",
						"order_hint" : " !",
						"plan_title" : "Next Release Discussion",
				},
				"7o_t_b5a_m_i_a_e2r_vo-1_n-_l7_rm_q_a_g_x2q" : None,
		}
	),
	recent_plan_references = PlannerRecentPlanReferenceCollection(
		additional_data = {
				"jd8_s5g_oa_fk2_s8a_w_c_i_a_jz42_q_a_axt_d" : {
						"@odata_type" : "#microsoft.graph.plannerRecentPlanReference",
						"last_accessed_date_time" : "2018-01-02T22:49:46.155Z",
						"plan_title" : "Next Release Discussion",
				},
		}
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "return=representation")
request_configuration.headers.add("If-Match", "W/\"JzEtVXNlckRldGFpbHMgQEBAQEBAQEBAQEBAQEBIWCc=\"")


result = await graph_client.me.planner.patch(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "favoritePlanReferences": {
    "jd8S5gOaFk2S8aWCIAJz42QAAxtD": {
      "@odata.type": "#microsoft.graph.plannerFavoritePlanReference",
      "orderHint": "8586866870001551087",
      "planTitle": "Next Release Discussion"
    },
    "uZWtCtli30CGoWLIWSat1mQAC0ai": {
      "@odata.type": "#microsoft.graph.plannerFavoritePlanReference",
      "orderHint": "8586888705198093378",
      "planTitle": "Product Support"
    }
  },
  "recentPlanReferences": {
    "jd8S5gOaFk2S8aWCIAJz42QAAxtD": {
      "@odata.type": "#microsoft.graph.plannerRecentPlanReference",
      "lastAccessedDateTime": "2018-01-02T22:49:46.155Z",
      "planTitle": "Next Release Discussion"
    },
    "XYE5pqNJu0uuRC2PM4ZQrmQAF2Pn": {
      "@odata.type": "#microsoft.graph.plannerRecentPlanReference",
      "lastAccessedDateTime": "2018-01-01T19:39:17.57Z",
      "planTitle": "Success Metrics"
    }
  },
  "id": "-YPnMJRiIUSKFyaVjYEkBWQAAc47"
}
```
