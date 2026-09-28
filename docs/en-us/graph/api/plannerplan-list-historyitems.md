<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannerplan-list-historyitems?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# List historyItems

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [history](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta) of changes made to tasks within a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plannerplan?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.Read | Tasks.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Tasks.Read.All | Tasks.ReadWrite.All |

## HTTP request

```http
GET /planner/plans/{plan-id}/historyItems
```

## Optional query parameters

This method supports the `$filter` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

Use `$filter` on the **occurredDateTime** property to retrieve history items within a specific time range.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [plannerHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows how to get task [history items](https://learn.microsoft.com/en-us/graph/api/resources/plannerhistoryitem?view=graph-rest-beta) for a plan with a date filter.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/beta/planner/plans/nETqF5FS2LkCp935s-FIFm2QAFkHM/historyItems?$filter=occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Plans["{plannerPlan-id}"].HistoryItems.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z";
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
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphplanner "github.com/microsoftgraph/msgraph-beta-sdk-go/planner"
	  //other-imports
)


requestFilter := "occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z"

requestParameters := &graphplanner.PlansItemHistoryItemsRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphplanner.PlansItemHistoryItemsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
historyItems, err := graphClient.Planner().Plans().ByPlannerPlanId("plannerPlan-id").HistoryItems().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerHistoryItemCollectionResponse result = graphClient.planner().plans().byPlannerPlanId("{plannerPlan-id}").historyItems().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z";
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

let historyItems = await client.api('/planner/plans/nETqF5FS2LkCp935s-FIFm2QAFkHM/historyItems')
	.version('beta')
	.filter('occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Planner\Plans\Item\HistoryItems\HistoryItemsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new HistoryItemsRequestBuilderGetRequestConfiguration();
$queryParameters = HistoryItemsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->planner()->plans()->byPlannerPlanId('plannerPlan-id')->historyItems()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

Get-MgBetaPlannerPlanHistoryItem -PlannerPlanId $plannerPlanId -Filter "occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.planner.plans.item.history_items.history_items_request_builder import HistoryItemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = HistoryItemsRequestBuilder.HistoryItemsRequestBuilderGetQueryParameters(
		filter = "occurredDateTime gt 2025-11-01T00:00:00Z and occurredDateTime lt 2025-12-01T00:00:00Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.planner.plans.by_planner_plan_id('plannerPlan-id').history_items.get(request_configuration = request_configuration)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#planner/plans('nETqF5FS2LkCp935s-FIFm2QAFkHM')/historyItems",
  "value": [
    {
      "@odata.type": "#microsoft.graph.taskHistoryItem",
      "id": "historyItem-id-1",
      "planId": "nETqF5FS2LkCp935s-FIFm2QAFkHM",
      "entityId": "dYsWHy7-WEGMQsMaPBv_9ZUAOzQz",
      "entityType": "task",
      "eventType": "created",
      "occurredDateTime": "2026-01-12T14:16:26.5896957Z",
      "actor": {
        "user": {
          "displayName": null,
          "id": "6699294c-9300-4ad8-a768-af3407b5e0fe"
        },
        "application": {
          "displayName": null,
          "id": "09abbdfd-ed23-44ee-a2d9-a627a41c90f3"
        }
      },
      "oldData": null,
      "newData": {
        "createdBy": {
          "user": {
            "displayName": null,
            "id": "6699294c-9300-4ad8-a768-af3407b5e0fe"
          },
          "application": {
            "displayName": null,
            "id": "09abbdfd-ed23-44ee-a2d9-a627a41c90f3"
          }
        },
        "bucketId": "0LHuWF3PrUqKYzq-TcR3oJUADFn8",
        "isArchived": false,
        "title": "Initial Task Title",
        "orderHint": "8584333795589189673P,",
        "percentComplete": 0,
        "priority": 5
      }
    },
    {
      "@odata.type": "#microsoft.graph.taskHistoryItem",
      "id": "historyItem-id-2",
      "planId": "nETqF5FS2LkCp935s-FIFm2QAFkHM",
      "entityId": "dYsWHy7-WEGMQsMaPBv_9ZUAOzQz",
      "entityType": "task",
      "eventType": "updated",
      "occurredDateTime": "2026-01-12T15:16:26.5896957Z",
      "actor": {
        "user": {
          "displayName": null,
          "id": "6699294c-9300-4ad8-a768-af3407b5e0fe"
        },
        "application": {
          "displayName": null,
          "id": "09abbdfd-ed23-44ee-a2d9-a627a41c90f3"
        }
      },
      "oldData": {
        "title": "Initial Task Title",
        "percentComplete": 0
      },
      "newData": {
        "title": "Updated Task Title",
        "percentComplete": 50
      }
    }
  ]
}
```
