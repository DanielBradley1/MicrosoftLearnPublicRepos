<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcprovisioningpolicy-applyconfig?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPcProvisioningPolicy: applyConfig

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the [provisioning policy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-beta) configuration for a set of Cloud PC devices by their IDs. This method supports retry and allows you to apply the configuration to a subset of Cloud PCs initially to test.

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
POST /deviceManagement/virtualEndpoint/provisioningPolicies/applyConfig
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| cloudPcIds | String collection | A collection of Cloud PC IDs. |
| policySettings | cloudPcPolicySettingType | The target property of this apply action. The possible values are: `region`, `singleSignOn`, `unknownFutureValue`. The default value is `region`. This action applies `region` as a value if this parameter is `null`. |

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/provisioningPolicies/applyConfig
Content-Type: application/json

{
  "cloudPcIds": [
    "52aa2645-36ee-47d2-9eb3-b8fbb17c3fc4",
    "ff117b6c-e3e6-41be-9cae-eb6743249a30"
  ],
  "policySettings": "region"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.ProvisioningPolicies.ApplyConfig;
using Microsoft.Graph.Beta.Models;

var requestBody = new ApplyConfigPostRequestBody
{
	CloudPcIds = new List<string>
	{
		"52aa2645-36ee-47d2-9eb3-b8fbb17c3fc4",
		"ff117b6c-e3e6-41be-9cae-eb6743249a30",
	},
	PolicySettings = CloudPcPolicySettingType.Region,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.ProvisioningPolicies.ApplyConfig.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphdevicemanagement.NewApplyConfigPostRequestBody()
cloudPcIds := []string {
	"52aa2645-36ee-47d2-9eb3-b8fbb17c3fc4",
	"ff117b6c-e3e6-41be-9cae-eb6743249a30",
}
requestBody.SetCloudPcIds(cloudPcIds)
policySettings := graphmodels.REGION_CLOUDPCPOLICYSETTINGTYPE 
requestBody.SetPolicySettings(&policySettings) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().ProvisioningPolicies().ApplyConfig().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.provisioningpolicies.applyconfig.ApplyConfigPostRequestBody applyConfigPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.provisioningpolicies.applyconfig.ApplyConfigPostRequestBody();
LinkedList<String> cloudPcIds = new LinkedList<String>();
cloudPcIds.add("52aa2645-36ee-47d2-9eb3-b8fbb17c3fc4");
cloudPcIds.add("ff117b6c-e3e6-41be-9cae-eb6743249a30");
applyConfigPostRequestBody.setCloudPcIds(cloudPcIds);
applyConfigPostRequestBody.setPolicySettings(EnumSet.of(CloudPcPolicySettingType.Region));
graphClient.deviceManagement().virtualEndpoint().provisioningPolicies().applyConfig().post(applyConfigPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const applyConfig = {
  cloudPcIds: [
    '52aa2645-36ee-47d2-9eb3-b8fbb17c3fc4',
    'ff117b6c-e3e6-41be-9cae-eb6743249a30'
  ],
  policySettings: 'region'
};

await client.api('/deviceManagement/virtualEndpoint/provisioningPolicies/applyConfig')
	.version('beta')
	.post(applyConfig);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\ProvisioningPolicies\ApplyConfig\ApplyConfigPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcPolicySettingType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ApplyConfigPostRequestBody();
$requestBody->setCloudPcIds(['52aa2645-36ee-47d2-9eb3-b8fbb17c3fc4', 'ff117b6c-e3e6-41be-9cae-eb6743249a30', 	]);
$requestBody->setPolicySettings(new CloudPcPolicySettingType('region'));

$graphServiceClient->deviceManagement()->virtualEndpoint()->provisioningPolicies()->applyConfig()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.provisioningpolicies.apply_config.apply_config_post_request_body import ApplyConfigPostRequestBody
from msgraph_beta.generated.models.cloud_pc_policy_setting_type import CloudPcPolicySettingType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ApplyConfigPostRequestBody(
	cloud_pc_ids = [
		"52aa2645-36ee-47d2-9eb3-b8fbb17c3fc4",
		"ff117b6c-e3e6-41be-9cae-eb6743249a30",
	],
	policy_settings = CloudPcPolicySettingType.Region,
)

await graph_client.device_management.virtual_endpoint.provisioning_policies.apply_config.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
