<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcpool-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-27 -->

# Update cloudPcPool

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /deviceManagement/virtualEndpoint/cloudPcPools/{cloudPcPool-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

You must specify the **@odata.type** property and the value of the [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object type to update. For example, `"@odata.type": "#microsoft.graph.cloudPcAgentPool"`.

The following table lists the properties that can be updated for a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | The type of the cloud PC pool to update. Required. |
| billingConfiguration | [cloudPcAgentPoolBillingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolbillingconfiguration?view=graph-rest-beta) | The billing configuration for the agent pool, including billing type and billing plan identifier. |
| capabilities | [cloudPcPoolCapabilityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolcapabilityconfiguration?view=graph-rest-beta) | The capabilities configuration for the pool, including single sign-on settings. |
| cloudPcConfiguration | [cloudPcConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconfiguration?view=graph-rest-beta) | The Cloud PC specification, including image and operating system locale settings for provisioning. |
| description | String | The description of the pool. The maximum length is 512 characters. |
| displayName | String | The display name of the pool. The name is unique across Cloud PC pools in an organization. The maximum length is 60 characters. |
| scalingPolicy | [cloudPcAgentPoolScalingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolscalingpolicy?view=graph-rest-beta) | The scaling policy defining minimum and maximum Cloud PC counts for the pool. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPcPools/a1b2c3d4-e5f6-7890-abcd-ef1234567890
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcAgentPool",
  "displayName": "Contoso Development Pool Updated",
  "description": "Contoso Development Pool Description Updated"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcAgentPool
{
	OdataType = "#microsoft.graph.cloudPcAgentPool",
	DisplayName = "Contoso Development Pool Updated",
	Description = "Contoso Development Pool Description Updated",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudPcPools["{cloudPcPool-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcPool()
displayName := "Contoso Development Pool Updated"
requestBody.SetDisplayName(&displayName) 
description := "Contoso Development Pool Description Updated"
requestBody.SetDescription(&description) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cloudPcPools, err := graphClient.DeviceManagement().VirtualEndpoint().CloudPcPools().ByCloudPcPoolId("cloudPcPool-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcAgentPool cloudPcPool = new CloudPcAgentPool();
cloudPcPool.setOdataType("#microsoft.graph.cloudPcAgentPool");
cloudPcPool.setDisplayName("Contoso Development Pool Updated");
cloudPcPool.setDescription("Contoso Development Pool Description Updated");
CloudPcPool result = graphClient.deviceManagement().virtualEndpoint().cloudPcPools().byCloudPcPoolId("{cloudPcPool-id}").patch(cloudPcPool);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcPool = {
  '@odata.type': '#microsoft.graph.cloudPcAgentPool',
  displayName: 'Contoso Development Pool Updated',
  description: 'Contoso Development Pool Description Updated'
};

await client.api('/deviceManagement/virtualEndpoint/cloudPcPools/a1b2c3d4-e5f6-7890-abcd-ef1234567890')
	.version('beta')
	.update(cloudPcPool);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAgentPool;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcAgentPool();
$requestBody->setOdataType('#microsoft.graph.cloudPcAgentPool');
$requestBody->setDisplayName('Contoso Development Pool Updated');
$requestBody->setDescription('Contoso Development Pool Description Updated');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudPcPools()->byCloudPcPoolId('cloudPcPool-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_agent_pool import CloudPcAgentPool
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcAgentPool(
	odata_type = "#microsoft.graph.cloudPcAgentPool",
	display_name = "Contoso Development Pool Updated",
	description = "Contoso Development Pool Description Updated",
)

result = await graph_client.device_management.virtual_endpoint.cloud_pc_pools.by_cloud_pc_pool_id('cloudPcPool-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
