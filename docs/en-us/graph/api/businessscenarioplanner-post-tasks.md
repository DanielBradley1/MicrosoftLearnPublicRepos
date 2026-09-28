<!-- Source: https://learn.microsoft.com/en-us/graph/api/businessscenarioplanner-post-tasks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-15 -->

# Create businessScenarioTask

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BusinessScenarioData.ReadWrite.OwnedBy | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BusinessScenarioData.ReadWrite.OwnedBy | Not available. |

## HTTP request

```http
POST /solutions/businessScenarios/{businessScenarioId}/planner/tasks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object.

You can specify the following properties when you create a **businessScenarioTask**.

| Property | Type | Description |
| :--- | :--- | :--- |
| appliedCategories | [plannerAppliedCategories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-beta) | The categories to which the task has been applied. For possible values, see [plannerAppliedCategories](https://learn.microsoft.com/en-us/graph/api/resources/plannerappliedcategories?view=graph-rest-beta). Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| assigneePriority | String | Hint used to order items of this type in a list view. For details about the supported format, see [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-beta). Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| assignments | [plannerAssignments](https://learn.microsoft.com/en-us/graph/api/resources/plannerassignments?view=graph-rest-beta) | The set of assignees the task is assigned to. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| bucketId | String | Bucket ID to which the task belongs. The bucket needs to be in the plan that the task is in. It's 28 characters long and case-sensitive. The [format validation](https://learn.microsoft.com/en-us/graph/api/resources/tasks-identifiers-disclaimer?view=graph-rest-beta) is done on the service. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| businessScenarioProperties | [businessScenarioProperties](https://learn.microsoft.com/en-us/graph/api/resources/businessscenarioproperties?view=graph-rest-beta) | Scenario-specific properties of the task. **externalObjectId** and **externalBucketId** properties must be specified when creating a task. Required. |
| conversationThreadId | String | Thread ID of the conversation on the task. This ID references the conversation thread object created in the **group**. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| dueDateTime | DateTimeOffset | Date and time at which the task is due. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| orderHint | String | Hint used to order items of this type in a list view. For details about the supported format, see [Using order hints in Planner](https://learn.microsoft.com/en-us/graph/api/resources/planner-order-hint-format?view=graph-rest-beta). Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| percentComplete | Int32 | Percentage of task completion. When set to `100`, the task is considered completed. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| planId | String | Identifier of the plan to which the task belongs. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| priority | Int32 | Priority of the task. Valid range of values is between `0` and `10` \(inclusive\), with increasing value being lower priority \(`0` has the highest priority and `10` has the lowest priority\). Currently, Planner interprets values `0` and `1` as "urgent"; `2`, `3`, and `4` as "important"; `5`, `6`, and `7` as "medium"; and `8`, `9`, and `10` as "low". Currently, Planner sets the value `1` for "urgent", `3` for "important", `5` for "medium", and `9` for "low". Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| startDateTime | DateTimeOffset | Date and time at which the task starts. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |
| target | [businessScenarioTaskTargetBase](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotasktargetbase?view=graph-rest-beta) | Target of the task that specifies where the task should be placed. Required. |
| title | String | Title of the task. Inherited from [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). |

## Response

If successful, this method returns a `201 Created` response code and a [businessScenarioTask](https://learn.microsoft.com/en-us/graph/api/resources/businessscenariotask?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/tasks
Content-Type: application/json

{
  "title": "Customer order #12010",
  "percentComplete": 0,
  "priority": 5,
  "target": {
    "@odata.type": "microsoft.graph.businessScenarioGroupTarget",
    "taskTargetKind": "group",
    "groupId": "7a339254-4b2b-4410-b295-c890a16776ee"
  },
  "businessScenarioProperties": {
    "externalObjectId": "Order#12010",
    "externalContextId": "Warehouse-CA-36",
    "externalObjectVersion": "000001",
    "webUrl": "https://ordertracking.contoso.com/view?id=12010",
    "externalBucketId": "deliveryBucket"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new BusinessScenarioTask
{
	Title = "Customer order #12010",
	PercentComplete = 0,
	Priority = 5,
	Target = new BusinessScenarioGroupTarget
	{
		OdataType = "microsoft.graph.businessScenarioGroupTarget",
		TaskTargetKind = PlannerTaskTargetKind.Group,
		GroupId = "7a339254-4b2b-4410-b295-c890a16776ee",
	},
	BusinessScenarioProperties = new BusinessScenarioProperties
	{
		ExternalObjectId = "Order#12010",
		ExternalContextId = "Warehouse-CA-36",
		ExternalObjectVersion = "000001",
		WebUrl = "https://ordertracking.contoso.com/view?id=12010",
		ExternalBucketId = "deliveryBucket",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BusinessScenarios["{businessScenario-id}"].Planner.Tasks.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewBusinessScenarioTask()
title := "Customer order #12010"
requestBody.SetTitle(&title) 
percentComplete := int32(0)
requestBody.SetPercentComplete(&percentComplete) 
priority := int32(5)
requestBody.SetPriority(&priority) 
target := graphmodels.NewBusinessScenarioGroupTarget()
taskTargetKind := graphmodels.GROUP_PLANNERTASKTARGETKIND 
target.SetTaskTargetKind(&taskTargetKind) 
groupId := "7a339254-4b2b-4410-b295-c890a16776ee"
target.SetGroupId(&groupId) 
requestBody.SetTarget(target)
businessScenarioProperties := graphmodels.NewBusinessScenarioProperties()
externalObjectId := "Order#12010"
businessScenarioProperties.SetExternalObjectId(&externalObjectId) 
externalContextId := "Warehouse-CA-36"
businessScenarioProperties.SetExternalContextId(&externalContextId) 
externalObjectVersion := "000001"
businessScenarioProperties.SetExternalObjectVersion(&externalObjectVersion) 
webUrl := "https://ordertracking.contoso.com/view?id=12010"
businessScenarioProperties.SetWebUrl(&webUrl) 
externalBucketId := "deliveryBucket"
businessScenarioProperties.SetExternalBucketId(&externalBucketId) 
requestBody.SetBusinessScenarioProperties(businessScenarioProperties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tasks, err := graphClient.Solutions().BusinessScenarios().ByBusinessScenarioId("businessScenario-id").Planner().Tasks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BusinessScenarioTask businessScenarioTask = new BusinessScenarioTask();
businessScenarioTask.setTitle("Customer order #12010");
businessScenarioTask.setPercentComplete(0);
businessScenarioTask.setPriority(5);
BusinessScenarioGroupTarget target = new BusinessScenarioGroupTarget();
target.setOdataType("microsoft.graph.businessScenarioGroupTarget");
target.setTaskTargetKind(PlannerTaskTargetKind.Group);
target.setGroupId("7a339254-4b2b-4410-b295-c890a16776ee");
businessScenarioTask.setTarget(target);
BusinessScenarioProperties businessScenarioProperties = new BusinessScenarioProperties();
businessScenarioProperties.setExternalObjectId("Order#12010");
businessScenarioProperties.setExternalContextId("Warehouse-CA-36");
businessScenarioProperties.setExternalObjectVersion("000001");
businessScenarioProperties.setWebUrl("https://ordertracking.contoso.com/view?id=12010");
businessScenarioProperties.setExternalBucketId("deliveryBucket");
businessScenarioTask.setBusinessScenarioProperties(businessScenarioProperties);
BusinessScenarioTask result = graphClient.solutions().businessScenarios().byBusinessScenarioId("{businessScenario-id}").planner().tasks().post(businessScenarioTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const businessScenarioTask = {
  title: 'Customer order #12010',
  percentComplete: 0,
  priority: 5,
  target: {
    '@odata.type': 'microsoft.graph.businessScenarioGroupTarget',
    taskTargetKind: 'group',
    groupId: '7a339254-4b2b-4410-b295-c890a16776ee'
  },
  businessScenarioProperties: {
    externalObjectId: 'Order#12010',
    externalContextId: 'Warehouse-CA-36',
    externalObjectVersion: '000001',
    webUrl: 'https://ordertracking.contoso.com/view?id=12010',
    externalBucketId: 'deliveryBucket'
  }
};

await client.api('/solutions/businessScenarios/c5d514e6c6864911ac46c720affb6e4d/planner/tasks')
	.version('beta')
	.post(businessScenarioTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\BusinessScenarioTask;
use Microsoft\Graph\Beta\Generated\Models\BusinessScenarioGroupTarget;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskTargetKind;
use Microsoft\Graph\Beta\Generated\Models\BusinessScenarioProperties;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BusinessScenarioTask();
$requestBody->setTitle('Customer order #12010');
$requestBody->setPercentComplete(0);
$requestBody->setPriority(5);
$target = new BusinessScenarioGroupTarget();
$target->setOdataType('microsoft.graph.businessScenarioGroupTarget');
$target->setTaskTargetKind(new PlannerTaskTargetKind('group'));
$target->setGroupId('7a339254-4b2b-4410-b295-c890a16776ee');
$requestBody->setTarget($target);
$businessScenarioProperties = new BusinessScenarioProperties();
$businessScenarioProperties->setExternalObjectId('Order#12010');
$businessScenarioProperties->setExternalContextId('Warehouse-CA-36');
$businessScenarioProperties->setExternalObjectVersion('000001');
$businessScenarioProperties->setWebUrl('https://ordertracking.contoso.com/view?id=12010');
$businessScenarioProperties->setExternalBucketId('deliveryBucket');
$requestBody->setBusinessScenarioProperties($businessScenarioProperties);

$result = $graphServiceClient->solutions()->businessScenarios()->byBusinessScenarioId('businessScenario-id')->planner()->tasks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.BusinessScenario

$params = @{
	title = "Customer order #12010"
	percentComplete = 0
	priority = 5
	target = @{
		"@odata.type" = "microsoft.graph.businessScenarioGroupTarget"
		taskTargetKind = "group"
		groupId = "7a339254-4b2b-4410-b295-c890a16776ee"
	}
	businessScenarioProperties = @{
		externalObjectId = "Order#12010"
		externalContextId = "Warehouse-CA-36"
		externalObjectVersion = "000001"
		webUrl = "https://ordertracking.contoso.com/view?id=12010"
		externalBucketId = "deliveryBucket"
	}
}

New-MgBetaSolutionBusinessScenarioPlannerTask -BusinessScenarioId $businessScenarioId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.business_scenario_task import BusinessScenarioTask
from msgraph_beta.generated.models.business_scenario_group_target import BusinessScenarioGroupTarget
from msgraph_beta.generated.models.planner_task_target_kind import PlannerTaskTargetKind
from msgraph_beta.generated.models.business_scenario_properties import BusinessScenarioProperties
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BusinessScenarioTask(
	title = "Customer order #12010",
	percent_complete = 0,
	priority = 5,
	target = BusinessScenarioGroupTarget(
		odata_type = "microsoft.graph.businessScenarioGroupTarget",
		task_target_kind = PlannerTaskTargetKind.Group,
		group_id = "7a339254-4b2b-4410-b295-c890a16776ee",
	),
	business_scenario_properties = BusinessScenarioProperties(
		external_object_id = "Order#12010",
		external_context_id = "Warehouse-CA-36",
		external_object_version = "000001",
		web_url = "https://ordertracking.contoso.com/view?id=12010",
		external_bucket_id = "deliveryBucket",
	),
)

result = await graph_client.solutions.business_scenarios.by_business_scenario_id('businessScenario-id').planner.tasks.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.businessScenarioTask",
  "title": "Customer order #12010",
  "percentComplete": 0,
  "priority": 5,
  "id": "pmc1rS1Io0C3rXQhyXIsNmUAOeIi",
  "target": {
    "@odata.type": "microsoft.graph.businessScenarioGroupTarget",
    "taskTargetKind": "group",
    "groupId": "7a339254-4b2b-4410-b295-c890a16776ee"
  },
  "businessScenarioProperties": {
    "externalObjectId": "Order#12010",
    "externalContextId": "Warehouse-CA-36",
    "externalObjectVersion": "000001",
    "webUrl": "https://ordertracking.contoso.com/view?id=12010",
    "externalBucketId": "deliveryBucket"
  }
}
```
