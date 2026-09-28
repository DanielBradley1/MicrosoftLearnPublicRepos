<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcprovisioningpolicy-schedulepolicyapplytask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudpcprovisioningpolicy: schedulePolicyApplyTask

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Set a scheduled auto-reprovision task to do automatic regular apply. `Frontline shared` only. Administrators only.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/provisioningPolicies/{id}/schedulePolicyApplyTask
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudpcpolicyscheduledapplyactiondetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpolicyscheduledapplyactiondetail?view=graph-rest-beta) object.

The following table shows the properties that can be supplied when you schedule a policy apply task.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| reservePercentage | Int32 | For `Frontline shared` only. The percentage of Cloud PCs to keep available. Administrators can set this property to a value from 0 to 99. Cloud PCs are reprovisioned only when there are no active and connected Cloud PC users. |
| cronScheduleExpression | String | Administrators can set a cron expression to define the scheduling rules for automatic regular apply. When auto provision is disabled, `cronScheduleExpression` is set to null, stopping the automatic task scheduling \(ex. "0 0 0 20 \* \*" means schedules a job to run at midnight on the 20th of every month\). Read-only. |
| startDateTime | String | Indicates IT Admins can set a start date to define the first scheduler run after this time. If not set, default is current time. There are no time zone information at this time, it needs to be coordinated with `timezone`, for example, "2025-01-01 00:00:00" with "China Standard Time" means the scheduling rule will take effect after Jan 01 2025 00:00:00 GMT+0800 \(China Standard Time\). |
| endDateTime | String | Indicates IT Admins can set an end date to define the last scheduler run before this time. If not set, the scheduler runs continuously. There are no time zone information at this time, it needs to be coordinated with `timezone`, for example, "2025-02-01 00:00:00" with "China Standard Time" means the scheduling rule will take effect before Feb 01 2025 00:00:00 GMT+0800 \(China Standard Time\). |
| timezone | cloudPcPolicyTimezone | Indicates IT Admins can set a timezone to define the timezone of `nextRunDateTime`, `startDateTime`, `endDateTime`, default is `gmt`. Possible values are `gmt`, `bit`, `nut`, `hst`, `mit`, `akst`, `pst`, `mst`, `east`, `est`, `ast`, `nst`, `art`, `gst`, `azot`, `cet`, `cat`, `eat`, `get`, `pkt`, `ist`, `bst`, `tha`, `cst`, `jst`, `acst`, `pgt`, `sbt`, `fjt`, `tot`, `lint`, and `unknownFutureValue`. |

## Response

If successful, this method returns a `202 ACCEPTED` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/provisioningPolicies/b0c2d35f-3385-46c8-a6f5-6c3dfad7708b/schedulePolicyApplyTask

{
  "reservePercentage": 50,
  "cronScheduleExpression": "0 0 0 20 * *",
  "startDateTime": "2025-03-12 00:00:00",
  "endDateTime": null,
  "timezone": "cst"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.ProvisioningPolicies.Item.SchedulePolicyApplyTask;

var requestBody = new SchedulePolicyApplyTaskPostRequestBody
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"reservePercentage" , 50
		},
		{
			"cronScheduleExpression" , "0 0 0 20 * *"
		},
		{
			"startDateTime" , "2025-03-12 00:00:00"
		},
		{
			"endDateTime" , null
		},
		{
			"timezone" , "cst"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.ProvisioningPolicies["{cloudPcProvisioningPolicy-id}"].SchedulePolicyApplyTask.PostAsync(requestBody);
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
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/devicemanagement"
	  //other-imports
)

requestBody := graphdevicemanagement.NewSchedulePolicyApplyTaskPostRequestBody()
additionalData := map[string]interface{}{
	"reservePercentage" : int32(50) , 
	"cronScheduleExpression" : "0 0 0 20 * *", 
	"startDateTime" : "2025-03-12 00:00:00", 
	endDateTime := null
requestBody.SetEndDateTime(&endDateTime) 
	"timezone" : "cst", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().ProvisioningPolicies().ByCloudPcProvisioningPolicyId("cloudPcProvisioningPolicy-id").SchedulePolicyApplyTask().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.provisioningpolicies.item.schedulepolicyapplytask.SchedulePolicyApplyTaskPostRequestBody schedulePolicyApplyTaskPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.provisioningpolicies.item.schedulepolicyapplytask.SchedulePolicyApplyTaskPostRequestBody();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("reservePercentage", 50);
additionalData.put("cronScheduleExpression", "0 0 0 20 * *");
additionalData.put("startDateTime", "2025-03-12 00:00:00");
additionalData.put("endDateTime", null);
additionalData.put("timezone", "cst");
schedulePolicyApplyTaskPostRequestBody.setAdditionalData(additionalData);
graphClient.deviceManagement().virtualEndpoint().provisioningPolicies().byCloudPcProvisioningPolicyId("{cloudPcProvisioningPolicy-id}").schedulePolicyApplyTask().post(schedulePolicyApplyTaskPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const schedulePolicyApplyTask = {
  reservePercentage: 50,
  cronScheduleExpression: '0 0 0 20 * *',
  startDateTime: '2025-03-12 00:00:00',
  endDateTime: null,
  timezone: 'cst'
};

await client.api('/deviceManagement/virtualEndpoint/provisioningPolicies/b0c2d35f-3385-46c8-a6f5-6c3dfad7708b/schedulePolicyApplyTask')
	.version('beta')
	.post(schedulePolicyApplyTask);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\ProvisioningPolicies\Item\SchedulePolicyApplyTask\SchedulePolicyApplyTaskPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SchedulePolicyApplyTaskPostRequestBody();
$additionalData = [
	'reservePercentage' => 50,
	'cronScheduleExpression' => '0 0 0 20 * *',
	'startDateTime' => '2025-03-12 00:00:00',
	'endDateTime' => null,
	'timezone' => 'cst',
];
$requestBody->setAdditionalData($additionalData);

$graphServiceClient->deviceManagement()->virtualEndpoint()->provisioningPolicies()->byCloudPcProvisioningPolicyId('cloudPcProvisioningPolicy-id')->schedulePolicyApplyTask()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.provisioningpolicies.item.schedule_policy_apply_task.schedule_policy_apply_task_post_request_body import SchedulePolicyApplyTaskPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SchedulePolicyApplyTaskPostRequestBody(
	additional_data = {
			"reserve_percentage" : 50,
			"cron_schedule_expression" : "0 0 0 20 * *",
			"start_date_time" : "2025-03-12 00:00:00",
			"end_date_time" : None,
			"timezone" : "cst",
	}
)

await graph_client.device_management.virtual_endpoint.provisioning_policies.by_cloud_pc_provisioning_policy_id('cloudPcProvisioningPolicy-id').schedule_policy_apply_task.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
