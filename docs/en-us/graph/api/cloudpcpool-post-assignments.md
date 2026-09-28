<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcpool-post-assignments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-27 -->

# Create cloudPcPoolAssignment

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) for a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta).

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
POST /deviceManagement/virtualEndpoint/cloudPcPools/{cloudPcPool-id}/assignments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) object. Use `#microsoft.graph.cloudPcAgentPoolUserAssignment` as the **@odata.type**.

The following table lists the properties that are required when you create a [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | Required. The type of assignment. Use `#microsoft.graph.cloudPcAgentPoolUserAssignment`. |
| userPrincipalId | String | Required. The unique identifier of the user principal. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudPcPoolAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolassignment?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPcPools/a1b2c3d4-e5f6-7890-abcd-ef1234567890/assignments
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcAgentPoolUserAssignment",
  "userPrincipalId": "f6a7b8c9-d0e1-2345-f678-901234567890"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcAgentPoolUserAssignment
{
	OdataType = "#microsoft.graph.cloudPcAgentPoolUserAssignment",
	UserPrincipalId = "f6a7b8c9-d0e1-2345-f678-901234567890",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudPcPools["{cloudPcPool-id}"].Assignments.PostAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcPoolAssignment()
userPrincipalId := "f6a7b8c9-d0e1-2345-f678-901234567890"
requestBody.SetUserPrincipalId(&userPrincipalId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
assignments, err := graphClient.DeviceManagement().VirtualEndpoint().CloudPcPools().ByCloudPcPoolId("cloudPcPool-id").Assignments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcAgentPoolUserAssignment cloudPcPoolAssignment = new CloudPcAgentPoolUserAssignment();
cloudPcPoolAssignment.setOdataType("#microsoft.graph.cloudPcAgentPoolUserAssignment");
cloudPcPoolAssignment.setUserPrincipalId("f6a7b8c9-d0e1-2345-f678-901234567890");
CloudPcPoolAssignment result = graphClient.deviceManagement().virtualEndpoint().cloudPcPools().byCloudPcPoolId("{cloudPcPool-id}").assignments().post(cloudPcPoolAssignment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcPoolAssignment = {
  '@odata.type': '#microsoft.graph.cloudPcAgentPoolUserAssignment',
  userPrincipalId: 'f6a7b8c9-d0e1-2345-f678-901234567890'
};

await client.api('/deviceManagement/virtualEndpoint/cloudPcPools/a1b2c3d4-e5f6-7890-abcd-ef1234567890/assignments')
	.version('beta')
	.post(cloudPcPoolAssignment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAgentPoolUserAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcAgentPoolUserAssignment();
$requestBody->setOdataType('#microsoft.graph.cloudPcAgentPoolUserAssignment');
$requestBody->setUserPrincipalId('f6a7b8c9-d0e1-2345-f678-901234567890');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudPcPools()->byCloudPcPoolId('cloudPcPool-id')->assignments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_agent_pool_user_assignment import CloudPcAgentPoolUserAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcAgentPoolUserAssignment(
	odata_type = "#microsoft.graph.cloudPcAgentPoolUserAssignment",
	user_principal_id = "f6a7b8c9-d0e1-2345-f678-901234567890",
)

result = await graph_client.device_management.virtual_endpoint.cloud_pc_pools.by_cloud_pc_pool_id('cloudPcPool-id').assignments.post(request_body)
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
  "@odata.type": "#microsoft.graph.cloudPcAgentPoolUserAssignment",
  "id": "cloudPcPoolAssignmentId",
  "userPrincipalId": "f6a7b8c9-d0e1-2345-f678-901234567890"
}
```
