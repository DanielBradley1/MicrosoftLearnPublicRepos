<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannerplan-movetocontainer?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# plannerPlan: moveToContainer

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Move a [planner plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) object from one [planner plan container](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontainer?view=graph-rest-beta) to another. Planner plans can only be moved from a user container to a group container.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Tasks.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.Read.All | Tasks.ReadWrite.All |

## HTTP request

```http
POST /planner/plans/{planId}/moveToContainer
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | Last known ETag value for the **plannerPlan** to be moved. Required. |

## Request body

In the request body, supply a JSON representation of the [plannerPlanContainer](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontainer?view=graph-rest-beta) object.

## Response

If successful, this API returns a `200 OK` response code and a [plannerPlan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta) object in the response body.

## Example

### Request

The following example shows a request to move a plan from a user container to a group container.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/planner/plans/{planId}/moveToContainer
Content-type: application/json
If-Match: "string"

{
    "container": {
        "containerId": "groupId",
        "type": "group"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Planner.Plans.Item.MoveToContainer;
using Microsoft.Graph.Beta.Models;

var requestBody = new MoveToContainerPostRequestBody
{
	Container = new PlannerPlanContainer
	{
		ContainerId = "groupId",
		Type = PlannerContainerType.Group,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Plans["{plannerPlan-id}"].MoveToContainer.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("If-Match", "\"string\"");
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
	  graphplanner "github.com/microsoftgraph/msgraph-beta-sdk-go/planner"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "\"string\"")

configuration := &graphplanner.PlansItemMoveToContainerRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphplanner.NewMoveToContainerPostRequestBody()
container := graphmodels.NewPlannerPlanContainer()
containerId := "groupId"
container.SetContainerId(&containerId) 
type := graphmodels.GROUP_PLANNERCONTAINERTYPE 
container.SetType(&type) 
requestBody.SetContainer(container)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
moveToContainer, err := graphClient.Planner().Plans().ByPlannerPlanId("plannerPlan-id").MoveToContainer().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.planner.plans.item.movetocontainer.MoveToContainerPostRequestBody moveToContainerPostRequestBody = new com.microsoft.graph.beta.planner.plans.item.movetocontainer.MoveToContainerPostRequestBody();
PlannerPlanContainer container = new PlannerPlanContainer();
container.setContainerId("groupId");
container.setType(PlannerContainerType.Group);
moveToContainerPostRequestBody.setContainer(container);
var result = graphClient.planner().plans().byPlannerPlanId("{plannerPlan-id}").moveToContainer().post(moveToContainerPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("If-Match", "\"string\"");
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

const plannerPlan = {
    container: {
        containerId: 'groupId',
        type: 'group'
    }
};

await client.api('/planner/plans/{planId}/moveToContainer')
	.version('beta')
	.post(plannerPlan);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Planner\Plans\Item\MoveToContainer\MoveToContainerRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Planner\Plans\Item\MoveToContainer\MoveToContainerPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\PlannerPlanContainer;
use Microsoft\Graph\Beta\Generated\Models\PlannerContainerType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MoveToContainerPostRequestBody();
$container = new PlannerPlanContainer();
$container->setContainerId('groupId');
$container->setType(new PlannerContainerType('group'));
$requestBody->setContainer($container);
$requestConfiguration = new MoveToContainerRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"string"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->planner()->plans()->byPlannerPlanId('plannerPlan-id')->moveToContainer()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

$params = @{
	container = @{
		containerId = "groupId"
		type = "group"
	}
}

Move-MgBetaPlannerPlanToContainer -PlannerPlanId $plannerPlanId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.planner.plans.item.move_to_container.move_to_container_request_builder import MoveToContainerRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.planner.plans.item.move_to_container.move_to_container_post_request_body import MoveToContainerPostRequestBody
from msgraph_beta.generated.models.planner_plan_container import PlannerPlanContainer
from msgraph_beta.generated.models.planner_container_type import PlannerContainerType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MoveToContainerPostRequestBody(
	container = PlannerPlanContainer(
		container_id = "groupId",
		type = PlannerContainerType.Group,
	),
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"string\"")


result = await graph_client.planner.plans.by_planner_plan_id('plannerPlan-id').move_to_container.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows a response to a request to move a plan from a user container to a group container.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#plans/$entity",
    "@odata.etag": "W/\"JzEtUGxhbiAgQEBAQEBAQEBAQEBAQEBARCc=\"",
    "title": "The Plan",
    "id": "planId",
    "container": {
        "containerId": "groupId",
        "type": "group",
        "url": "https://graph.microsoft.com/beta/groups/groupId"

    }
}
```
