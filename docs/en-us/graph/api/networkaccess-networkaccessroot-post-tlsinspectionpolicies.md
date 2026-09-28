<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-post-tlsinspectionpolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create tlsInspectionPolicy

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) object.

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
POST /networkAccess/tlsInspectionPolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) object.

You can specify the following properties when creating a **tlsInspectionPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Optional description of the policy. |
| name | String | The display name of the policy. Required. |
| settings | [microsoft.graph.networkaccess.tlsInspectionPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicysettings?view=graph-rest-beta) | Settings that configure the default behavior of the policy. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/networkAccess/tlsInspectionPolicies
Content-Type: application/json

{
  "name": "Default TLS Inspection Policy",
  "description": "Policy for inspecting TLS traffic",
  "settings": {
    "defaultAction": "bypass"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new TlsInspectionPolicy
{
	Name = "Default TLS Inspection Policy",
	Description = "Policy for inspecting TLS traffic",
	Settings = new TlsInspectionPolicySettings
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"defaultAction" , "bypass"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.TlsInspectionPolicies.PostAsync(requestBody);
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

requestBody := graphmodelsnetworkaccess.NewTlsInspectionPolicy()
name := "Default TLS Inspection Policy"
requestBody.SetName(&name) 
description := "Policy for inspecting TLS traffic"
requestBody.SetDescription(&description) 
settings := graphmodelsnetworkaccess.NewTlsInspectionPolicySettings()
additionalData := map[string]interface{}{
	"defaultAction" : "bypass", 
}
settings.SetAdditionalData(additionalData)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tlsInspectionPolicies, err := graphClient.NetworkAccess().TlsInspectionPolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicy tlsInspectionPolicy = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicy();
tlsInspectionPolicy.setName("Default TLS Inspection Policy");
tlsInspectionPolicy.setDescription("Policy for inspecting TLS traffic");
com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicySettings settings = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicySettings();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("defaultAction", "bypass");
settings.setAdditionalData(additionalData);
tlsInspectionPolicy.setSettings(settings);
com.microsoft.graph.models.networkaccess.TlsInspectionPolicy result = graphClient.networkAccess().tlsInspectionPolicies().post(tlsInspectionPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const tlsInspectionPolicy = {
  name: 'Default TLS Inspection Policy',
  description: 'Policy for inspecting TLS traffic',
  settings: {
    defaultAction: 'bypass'
  }
};

await client.api('/networkAccess/tlsInspectionPolicies')
	.version('beta')
	.post(tlsInspectionPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionPolicy;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionPolicySettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TlsInspectionPolicy();
$requestBody->setName('Default TLS Inspection Policy');
$requestBody->setDescription('Policy for inspecting TLS traffic');
$settings = new TlsInspectionPolicySettings();
$additionalData = [
	'defaultAction' => 'bypass',
];
$settings->setAdditionalData($additionalData);
$requestBody->setSettings($settings);

$result = $graphServiceClient->networkAccess()->tlsInspectionPolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "Default TLS Inspection Policy"
	description = "Policy for inspecting TLS traffic"
	settings = @{
		defaultAction = "bypass"
	}
}

New-MgBetaNetworkAccessTlInspectionPolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.tls_inspection_policy import TlsInspectionPolicy
from msgraph_beta.generated.models.networkaccess.tls_inspection_policy_settings import TlsInspectionPolicySettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TlsInspectionPolicy(
	name = "Default TLS Inspection Policy",
	description = "Policy for inspecting TLS traffic",
	settings = TlsInspectionPolicySettings(
		additional_data = {
				"default_action" : "bypass",
		}
	),
)

result = await graph_client.network_access.tls_inspection_policies.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/tlsInspectionPolicies/$entity",
    "id": "b712c469-e7cd-e7cb-738f-94b199570b0d",
    "name": "Default TLS Inspection Policy",
    "description": "Policy for inspecting TLS traffic",
    "version": "1.0.0",
    "lastModifiedDateTime": "2025-06-02T20:54:19.146638Z",
    "settings": {
        "defaultAction": "bypass"
    }
}
```
