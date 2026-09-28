<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpc-validatebulkresize?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPC: validateBulkResize

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Validate that a set of [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta) devices meet the requirements to be bulk resized.

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
POST /deviceManagement/virtualEndpoint/cloudPCs/validateBulkResize
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudPcIds | String collection | The selected Cloud PC ID list to be validated. The max count is 2000. |
| targetServicePlanId | String | The target service plan ID of the resize configuration with the new vCPU and storage size. |

## Response

If successful, this method returns a `200 OK` response code and the requested [cloudPcResizeValidateResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcresizevalidationresult?view=graph-rest-beta) object collection in the response body.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/validateBulkResize
Content-Type: application/json

{
  "cloudPcIds": [
    "30d0e128-de93-41dc-89ec-33d84bb662a0", 
    "7c82a3e3-9459-44e4-94d9-b92f93bf78dd"
  ],
  "targetServicePlanId": "662009bc-7732-4f6f-8726-25883518b33e"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.CloudPCs.ValidateBulkResize;

var requestBody = new ValidateBulkResizePostRequestBody
{
	CloudPcIds = new List<string>
	{
		"30d0e128-de93-41dc-89ec-33d84bb662a0",
		"7c82a3e3-9459-44e4-94d9-b92f93bf78dd",
	},
	TargetServicePlanId = "662009bc-7732-4f6f-8726-25883518b33e",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudPCs.ValidateBulkResize.PostAsValidateBulkResizePostResponseAsync(requestBody);
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

requestBody := graphdevicemanagement.NewValidateBulkResizePostRequestBody()
cloudPcIds := []string {
	"30d0e128-de93-41dc-89ec-33d84bb662a0",
	"7c82a3e3-9459-44e4-94d9-b92f93bf78dd",
}
requestBody.SetCloudPcIds(cloudPcIds)
targetServicePlanId := "662009bc-7732-4f6f-8726-25883518b33e"
requestBody.SetTargetServicePlanId(&targetServicePlanId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
validateBulkResize, err := graphClient.DeviceManagement().VirtualEndpoint().CloudPCs().ValidateBulkResize().PostAsValidateBulkResizePostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.cloudpcs.validatebulkresize.ValidateBulkResizePostRequestBody validateBulkResizePostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.cloudpcs.validatebulkresize.ValidateBulkResizePostRequestBody();
LinkedList<String> cloudPcIds = new LinkedList<String>();
cloudPcIds.add("30d0e128-de93-41dc-89ec-33d84bb662a0");
cloudPcIds.add("7c82a3e3-9459-44e4-94d9-b92f93bf78dd");
validateBulkResizePostRequestBody.setCloudPcIds(cloudPcIds);
validateBulkResizePostRequestBody.setTargetServicePlanId("662009bc-7732-4f6f-8726-25883518b33e");
var result = graphClient.deviceManagement().virtualEndpoint().cloudPCs().validateBulkResize().post(validateBulkResizePostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcResizeValidationResult = {
  cloudPcIds: [
    '30d0e128-de93-41dc-89ec-33d84bb662a0', 
    '7c82a3e3-9459-44e4-94d9-b92f93bf78dd'
  ],
  targetServicePlanId: '662009bc-7732-4f6f-8726-25883518b33e'
};

await client.api('/deviceManagement/virtualEndpoint/cloudPCs/validateBulkResize')
	.version('beta')
	.post(cloudPcResizeValidationResult);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\CloudPCs\ValidateBulkResize\ValidateBulkResizePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ValidateBulkResizePostRequestBody();
$requestBody->setCloudPcIds(['30d0e128-de93-41dc-89ec-33d84bb662a0', '7c82a3e3-9459-44e4-94d9-b92f93bf78dd', 	]);
$requestBody->setTargetServicePlanId('662009bc-7732-4f6f-8726-25883518b33e');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudPCs()->validateBulkResize()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.cloudpcs.validate_bulk_resize.validate_bulk_resize_post_request_body import ValidateBulkResizePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ValidateBulkResizePostRequestBody(
	cloud_pc_ids = [
		"30d0e128-de93-41dc-89ec-33d84bb662a0",
		"7c82a3e3-9459-44e4-94d9-b92f93bf78dd",
	],
	target_service_plan_id = "662009bc-7732-4f6f-8726-25883518b33e",
)

result = await graph_client.device_management.virtual_endpoint.cloud_p_cs.validate_bulk_resize.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value": [
        {
            "@odata.type": "#microsoft.graph.cloudPcResizeValidationResult",
            "cloudPcId": "30d0e128-de93-41dc-89ec-33d84bb662a0",
            "validationResult": "success"
        },
        {
            "@odata.type": "#microsoft.graph.cloudPcResizeValidationResult",
            "cloudPcId": "7c82a3e3-9459-44e4-94d9-b92f93bf78dd",
            "validationResult": "operationNotSupported"
        }
    ]
}
```
