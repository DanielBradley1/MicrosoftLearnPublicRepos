<!-- Source: https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-getplan?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# businessScenarioPlanner: getPlan

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get information about the [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) mapped to a given target. If a **plannerPlan** doesn't exist for the specified target at the time of the request, a new plan will be created for the [businessScenario](https://learn.microsoft.com/en-us/graph/api/resources/businessscenario?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BusinessScenarioData.Read.OwnedBy | BusinessScenarioData.ReadWrite.OwnedBy |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BusinessScenarioData.Read.OwnedBy | BusinessScenarioData.ReadWrite.OwnedBy |

## HTTP request

```http
POST /solutions/businessScenarios/{businessScenarioId}/planner/getPlan
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameter that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| target | [businessScenarioTaskTargetBase](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotasktargetbase?view=graph-rest-beta) | Target for which to get the plan information. |

## Response

If successful, this action returns a `200 OK` response code and a [businessScenarioPlanReference](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioplanreference?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/getPlan
Content-Type: application/json

{
  "target": {
      "@odata.type": "microsoft.graph.businessScenarioGroupTarget",
      "taskTargetKind": "group",
      "groupId": "7a339254-4b2b-4410-b295-c890a16776ee"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Solutions.BusinessScenarios.Item.Planner.GetPlan;
using Microsoft.Graph.Beta.Models;

var requestBody = new GetPlanPostRequestBody
{
	Target = new BusinessScenarioGroupTarget
	{
		OdataType = "microsoft.graph.businessScenarioGroupTarget",
		TaskTargetKind = PlannerTaskTargetKind.Group,
		GroupId = "7a339254-4b2b-4410-b295-c890a16776ee",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BusinessScenarios["{businessScenario-id}"].Planner.GetPlan.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphsolutions "github.com/microsoftgraph/msgraph-beta-sdk-go/solutions"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphsolutions.NewGetPlanPostRequestBody()
target := graphmodels.NewBusinessScenarioGroupTarget()
taskTargetKind := graphmodels.GROUP_PLANNERTASKTARGETKIND 
target.SetTaskTargetKind(&taskTargetKind) 
groupId := "7a339254-4b2b-4410-b295-c890a16776ee"
target.SetGroupId(&groupId) 
requestBody.SetTarget(target)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getPlan, err := graphClient.Solutions().BusinessScenarios().ByBusinessScenarioId("businessScenario-id").Planner().GetPlan().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.solutions.businessscenarios.item.planner.getplan.GetPlanPostRequestBody getPlanPostRequestBody = new com.microsoft.graph.beta.solutions.businessscenarios.item.planner.getplan.GetPlanPostRequestBody();
BusinessScenarioGroupTarget target = new BusinessScenarioGroupTarget();
target.setOdataType("microsoft.graph.businessScenarioGroupTarget");
target.setTaskTargetKind(PlannerTaskTargetKind.Group);
target.setGroupId("7a339254-4b2b-4410-b295-c890a16776ee");
getPlanPostRequestBody.setTarget(target);
var result = graphClient.solutions().businessScenarios().byBusinessScenarioId("{businessScenario-id}").planner().getPlan().post(getPlanPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const businessScenarioPlanReference = {
  target: {
      '@odata.type': 'microsoft.graph.businessScenarioGroupTarget',
      taskTargetKind: 'group',
      groupId: '7a339254-4b2b-4410-b295-c890a16776ee'
  }
};

await client.api('/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/getPlan')
	.version('beta')
	.post(businessScenarioPlanReference);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Solutions\BusinessScenarios\Item\Planner\GetPlan\GetPlanPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\BusinessScenarioGroupTarget;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskTargetKind;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetPlanPostRequestBody();
$target = new BusinessScenarioGroupTarget();
$target->setOdataType('microsoft.graph.businessScenarioGroupTarget');
$target->setTaskTargetKind(new PlannerTaskTargetKind('group'));
$target->setGroupId('7a339254-4b2b-4410-b295-c890a16776ee');
$requestBody->setTarget($target);

$result = $graphServiceClient->solutions()->businessScenarios()->byBusinessScenarioId('businessScenario-id')->planner()->getPlan()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.BusinessScenario

$params = @{
	target = @{
		"@odata.type" = "microsoft.graph.businessScenarioGroupTarget"
		taskTargetKind = "group"
		groupId = "7a339254-4b2b-4410-b295-c890a16776ee"
	}
}

Get-MgBetaSolutionBusinessScenarioPlannerPlan -BusinessScenarioId $businessScenarioId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.solutions.businessscenarios.item.planner.get_plan.get_plan_post_request_body import GetPlanPostRequestBody
from msgraph_beta.generated.models.business_scenario_group_target import BusinessScenarioGroupTarget
from msgraph_beta.generated.models.planner_task_target_kind import PlannerTaskTargetKind
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetPlanPostRequestBody(
	target = BusinessScenarioGroupTarget(
		odata_type = "microsoft.graph.businessScenarioGroupTarget",
		task_target_kind = PlannerTaskTargetKind.Group,
		group_id = "7a339254-4b2b-4410-b295-c890a16776ee",
	),
)

result = await graph_client.solutions.business_scenarios.by_business_scenario_id('businessScenario-id').planner.get_plan.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.businessScenarioPlanReference",
  "id": "pmc1rS1Io0C3rXQhyXIsNmUAOeIi",
  "title": "Order Tracking"
}
```
