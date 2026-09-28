<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcexternalpartner-configureagent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# cloudPcExternalPartner: configureAgent

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Configure the [cloudPcExternalPartnerAgentSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartneragentsetting?view=graph-rest-beta) of the [cloudPcExternalPartner](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartner?view=graph-rest-beta) object. This setting is used for RMM partner agent installation. RMM partners must contact the Microsoft team to complete onboarding and add the agent URL prefix to the allow list before using this API. If `autoDeploymentEnabled` is enabled, the new provisioned Cloud PC is triggered agent deployment automatically. Currently supports only Windows 365 Business Cloud PC.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Global Administrator | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/externalPartners/{cloudPcExternalPartnerId}/configureAgent
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| agentSetting | [cloudPcExternalPartnerAgentSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcexternalpartneragentsetting?view=graph-rest-beta) | The agent settings associated with the external partner. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/externalPartners/b3548526-e615-3785-3118-be70b3968ec5/configureAgent
Content-Type: application/json

{
  "agentSetting": {
      "agentUrl": "https://rmmExample.microsoft.com/agent/rmmExampleAgent.msi",
      "agentSha256": "EC6AF1EA0367D16DDE6639A89A080A524CEBC4D4BEDFE00ED0CAC4B865A918D8",
      "installParameters": [
          "/quiet",
          "/norestart",
          "TOKENID=e69c1577-d465-4e57-af33-0ddea43feeb1"
      ],
      "autoDeploymentEnabled": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.ExternalPartners.Item.ConfigureAgent;
using Microsoft.Graph.Beta.Models;

var requestBody = new ConfigureAgentPostRequestBody
{
	AgentSetting = new CloudPcExternalPartnerAgentSetting
	{
		AgentUrl = "https://rmmExample.microsoft.com/agent/rmmExampleAgent.msi",
		AgentSha256 = "EC6AF1EA0367D16DDE6639A89A080A524CEBC4D4BEDFE00ED0CAC4B865A918D8",
		InstallParameters = new List<string>
		{
			"/quiet",
			"/norestart",
			"TOKENID=e69c1577-d465-4e57-af33-0ddea43feeb1",
		},
		AutoDeploymentEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.ExternalPartners["{cloudPcExternalPartner-id}"].ConfigureAgent.PostAsync(requestBody);
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

requestBody := graphdevicemanagement.NewConfigureAgentPostRequestBody()
agentSetting := graphmodels.NewCloudPcExternalPartnerAgentSetting()
agentUrl := "https://rmmExample.microsoft.com/agent/rmmExampleAgent.msi"
agentSetting.SetAgentUrl(&agentUrl) 
agentSha256 := "EC6AF1EA0367D16DDE6639A89A080A524CEBC4D4BEDFE00ED0CAC4B865A918D8"
agentSetting.SetAgentSha256(&agentSha256) 
installParameters := []string {
	"/quiet",
	"/norestart",
	"TOKENID=e69c1577-d465-4e57-af33-0ddea43feeb1",
}
agentSetting.SetInstallParameters(installParameters)
autoDeploymentEnabled := true
agentSetting.SetAutoDeploymentEnabled(&autoDeploymentEnabled) 
requestBody.SetAgentSetting(agentSetting)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().ExternalPartners().ByCloudPcExternalPartnerId("cloudPcExternalPartner-id").ConfigureAgent().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.externalpartners.item.configureagent.ConfigureAgentPostRequestBody configureAgentPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.externalpartners.item.configureagent.ConfigureAgentPostRequestBody();
CloudPcExternalPartnerAgentSetting agentSetting = new CloudPcExternalPartnerAgentSetting();
agentSetting.setAgentUrl("https://rmmExample.microsoft.com/agent/rmmExampleAgent.msi");
agentSetting.setAgentSha256("EC6AF1EA0367D16DDE6639A89A080A524CEBC4D4BEDFE00ED0CAC4B865A918D8");
LinkedList<String> installParameters = new LinkedList<String>();
installParameters.add("/quiet");
installParameters.add("/norestart");
installParameters.add("TOKENID=e69c1577-d465-4e57-af33-0ddea43feeb1");
agentSetting.setInstallParameters(installParameters);
agentSetting.setAutoDeploymentEnabled(true);
configureAgentPostRequestBody.setAgentSetting(agentSetting);
graphClient.deviceManagement().virtualEndpoint().externalPartners().byCloudPcExternalPartnerId("{cloudPcExternalPartner-id}").configureAgent().post(configureAgentPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const configureAgent = {
  agentSetting: {
      agentUrl: 'https://rmmExample.microsoft.com/agent/rmmExampleAgent.msi',
      agentSha256: 'EC6AF1EA0367D16DDE6639A89A080A524CEBC4D4BEDFE00ED0CAC4B865A918D8',
      installParameters: [
          '/quiet',
          '/norestart',
          'TOKENID=e69c1577-d465-4e57-af33-0ddea43feeb1'
      ],
      autoDeploymentEnabled: true
  }
};

await client.api('/deviceManagement/virtualEndpoint/externalPartners/b3548526-e615-3785-3118-be70b3968ec5/configureAgent')
	.version('beta')
	.post(configureAgent);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\ExternalPartners\Item\ConfigureAgent\ConfigureAgentPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcExternalPartnerAgentSetting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConfigureAgentPostRequestBody();
$agentSetting = new CloudPcExternalPartnerAgentSetting();
$agentSetting->setAgentUrl('https://rmmExample.microsoft.com/agent/rmmExampleAgent.msi');
$agentSetting->setAgentSha256('EC6AF1EA0367D16DDE6639A89A080A524CEBC4D4BEDFE00ED0CAC4B865A918D8');
$agentSetting->setInstallParameters(['/quiet', '/norestart', 'TOKENID=e69c1577-d465-4e57-af33-0ddea43feeb1', 	]);
$agentSetting->setAutoDeploymentEnabled(true);
$requestBody->setAgentSetting($agentSetting);

$graphServiceClient->deviceManagement()->virtualEndpoint()->externalPartners()->byCloudPcExternalPartnerId('cloudPcExternalPartner-id')->configureAgent()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.externalpartners.item.configure_agent.configure_agent_post_request_body import ConfigureAgentPostRequestBody
from msgraph_beta.generated.models.cloud_pc_external_partner_agent_setting import CloudPcExternalPartnerAgentSetting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConfigureAgentPostRequestBody(
	agent_setting = CloudPcExternalPartnerAgentSetting(
		agent_url = "https://rmmExample.microsoft.com/agent/rmmExampleAgent.msi",
		agent_sha256 = "EC6AF1EA0367D16DDE6639A89A080A524CEBC4D4BEDFE00ED0CAC4B865A918D8",
		install_parameters = [
			"/quiet",
			"/norestart",
			"TOKENID=e69c1577-d465-4e57-af33-0ddea43feeb1",
		],
		auto_deployment_enabled = True,
	),
)

await graph_client.device_management.virtual_endpoint.external_partners.by_cloud_pc_external_partner_id('cloudPcExternalPartner-id').configure_agent.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
