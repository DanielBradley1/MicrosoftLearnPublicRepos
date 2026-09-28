<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-post-cloudfirewallpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Create cloudFirewallPolicy

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/cloudFirewallPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) object.

You can specify the following properties when creating a **cloudFirewallPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | A unique display name for the policy. Required. |
| description | String | A description of the policy. Optional. |
| settings | [microsoft.graph.networkaccess.cloudFirewallPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicysettings?view=graph-rest-beta) | Configuration settings for the policy, including the default action. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudFirewallPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-cloudfirewallpolicy?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/networkAccess/cloudFirewallPolicies
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicy",
  "name": "Block unauthorized egress",
  "description": "Policy to block unauthorized outbound connections",
  "settings": {
    "defaultAction": "allow"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new CloudFirewallPolicy
{
	OdataType = "#microsoft.graph.networkaccess.cloudFirewallPolicy",
	Name = "Block unauthorized egress",
	Description = "Policy to block unauthorized outbound connections",
	Settings = new CloudFirewallPolicySettings
	{
		DefaultAction = CloudFirewallAction.Allow,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.CloudFirewallPolicies.PostAsync(requestBody);
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
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewCloudFirewallPolicy()
name := "Block unauthorized egress"
requestBody.SetName(&name) 
description := "Policy to block unauthorized outbound connections"
requestBody.SetDescription(&description) 
settings := graphmodelsnetworkaccess.NewCloudFirewallPolicySettings()
defaultAction := graphmodels.ALLOW_CLOUDFIREWALLACTION 
settings.SetDefaultAction(&defaultAction) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cloudFirewallPolicies, err := graphClient.NetworkAccess().CloudFirewallPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.CloudFirewallPolicy cloudFirewallPolicy = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallPolicy();
cloudFirewallPolicy.setOdataType("#microsoft.graph.networkaccess.cloudFirewallPolicy");
cloudFirewallPolicy.setName("Block unauthorized egress");
cloudFirewallPolicy.setDescription("Policy to block unauthorized outbound connections");
com.microsoft.graph.beta.models.networkaccess.CloudFirewallPolicySettings settings = new com.microsoft.graph.beta.models.networkaccess.CloudFirewallPolicySettings();
settings.setDefaultAction(com.microsoft.graph.beta.models.networkaccess.CloudFirewallAction.Allow);
cloudFirewallPolicy.setSettings(settings);
com.microsoft.graph.models.networkaccess.CloudFirewallPolicy result = graphClient.networkAccess().cloudFirewallPolicies().post(cloudFirewallPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudFirewallPolicy = {
  '@odata.type': '#microsoft.graph.networkaccess.cloudFirewallPolicy',
  name: 'Block unauthorized egress',
  description: 'Policy to block unauthorized outbound connections',
  settings: {
    defaultAction: 'allow'
  }
};

await client.api('/networkAccess/cloudFirewallPolicies')
	.version('beta')
	.post(cloudFirewallPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallPolicy;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallPolicySettings;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\CloudFirewallAction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudFirewallPolicy();
$requestBody->setOdataType('#microsoft.graph.networkaccess.cloudFirewallPolicy');
$requestBody->setName('Block unauthorized egress');
$requestBody->setDescription('Policy to block unauthorized outbound connections');
$settings = new CloudFirewallPolicySettings();
$settings->setDefaultAction(new CloudFirewallAction('allow'));
$requestBody->setSettings($settings);

$result = $graphServiceClient->networkAccess()->cloudFirewallPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.cloudFirewallPolicy"
	name = "Block unauthorized egress"
	description = "Policy to block unauthorized outbound connections"
	settings = @{
		defaultAction = "allow"
	}
}

New-MgBetaNetworkAccessCloudFirewallPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.cloud_firewall_policy import CloudFirewallPolicy
from msgraph_beta.generated.models.networkaccess.cloud_firewall_policy_settings import CloudFirewallPolicySettings
from msgraph_beta.generated.models.cloud_firewall_action import CloudFirewallAction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudFirewallPolicy(
	odata_type = "#microsoft.graph.networkaccess.cloudFirewallPolicy",
	name = "Block unauthorized egress",
	description = "Policy to block unauthorized outbound connections",
	settings = CloudFirewallPolicySettings(
		default_action = CloudFirewallAction.Allow,
	),
)

result = await graph_client.network_access.cloud_firewall_policies.post(request_body)
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
  "@odata.type": "#microsoft.graph.networkaccess.cloudFirewallPolicy",
  "id": "e3692831-a554-4507-8a60-681a8066eb39",
  "name": "Block unauthorized egress",
  "description": "Policy to block unauthorized outbound connections",
  "version": "1.0.0",
  "lastModifiedDateTime": "2025-02-11T16:11:41Z",
  "settings": {
    "defaultAction": "allow"
  }
}
```
