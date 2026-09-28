<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-publish?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# cloudPcCloudApp: publish

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Publish a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object to make it available to end users through their portal, such as the Windows App.

Note

An admin can publish up to 500 cloud apps under a single provisioning policy

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/cloudApps/publish
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameter that you can use with this action.

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudAppIds | String collection | The selected app ID list to be published. The maximum number of apps an admin can publish under a single provisioning policy is 500. |

## Response

If successful, this method returns a `202 Accepted` response code.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudApps/publish
Content-Type: application/json

{
   "cloudAppIds": ["30d0e128-de93-41dc-89ec-33d84bb662a0", "40d0e128-de93-41dc-89ec-33d84bb662a0"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.CloudApps.Publish;

var requestBody = new PublishPostRequestBody
{
	CloudAppIds = new List<string>
	{
		"30d0e128-de93-41dc-89ec-33d84bb662a0",
		"40d0e128-de93-41dc-89ec-33d84bb662a0",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.CloudApps.Publish.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewPublishPostRequestBody()
cloudAppIds := []string {
	"30d0e128-de93-41dc-89ec-33d84bb662a0",
	"40d0e128-de93-41dc-89ec-33d84bb662a0",
}
requestBody.SetCloudAppIds(cloudAppIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().CloudApps().Publish().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.cloudapps.publish.PublishPostRequestBody publishPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.cloudapps.publish.PublishPostRequestBody();
LinkedList<String> cloudAppIds = new LinkedList<String>();
cloudAppIds.add("30d0e128-de93-41dc-89ec-33d84bb662a0");
cloudAppIds.add("40d0e128-de93-41dc-89ec-33d84bb662a0");
publishPostRequestBody.setCloudAppIds(cloudAppIds);
graphClient.deviceManagement().virtualEndpoint().cloudApps().publish().post(publishPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const publish = {
   cloudAppIds: ['30d0e128-de93-41dc-89ec-33d84bb662a0', '40d0e128-de93-41dc-89ec-33d84bb662a0']
};

await client.api('/deviceManagement/virtualEndpoint/cloudApps/publish')
	.version('beta')
	.post(publish);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\CloudApps\Publish\PublishPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PublishPostRequestBody();
$requestBody->setCloudAppIds(['30d0e128-de93-41dc-89ec-33d84bb662a0', '40d0e128-de93-41dc-89ec-33d84bb662a0', 	]);

$graphServiceClient->deviceManagement()->virtualEndpoint()->cloudApps()->publish()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.cloudapps.publish.publish_post_request_body import PublishPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PublishPostRequestBody(
	cloud_app_ids = [
		"30d0e128-de93-41dc-89ec-33d84bb662a0",
		"40d0e128-de93-41dc-89ec-33d84bb662a0",
	],
)

await graph_client.device_management.virtual_endpoint.cloud_apps.publish.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
