<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-tlsinspectionpolicy-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# Update tlsInspectionPolicy

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta) object.

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
PATCH /networkAccess/tlsInspectionPolicies/{tlsInspectionPolicyId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Optional description of the policy. |
| name | String | The display name of the policy. |
| settings | [microsoft.graph.networkaccess.tlsInspectionPolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicysettings?view=graph-rest-beta) | Settings that configure the default behavior of the policy. |

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
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/networkAccess/tlsInspectionPolicies/b712c469-e7cd-e7cb-738f-94b199570b0d
Content-Type: application/json

{
  "name": "New name TLS Inspection Policy",
  "description": "New description policy for inspecting TLS traffic",
  "settings": {
        "defaultAction": "inspect"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new TlsInspectionPolicy
{
	Name = "New name TLS Inspection Policy",
	Description = "New description policy for inspecting TLS traffic",
	Settings = new TlsInspectionPolicySettings
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"defaultAction" , "inspect"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.TlsInspectionPolicies["{tlsInspectionPolicy-id}"].PatchAsync(requestBody);
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
name := "New name TLS Inspection Policy"
requestBody.SetName(&name) 
description := "New description policy for inspecting TLS traffic"
requestBody.SetDescription(&description) 
settings := graphmodelsnetworkaccess.NewTlsInspectionPolicySettings()
additionalData := map[string]interface{}{
	"defaultAction" : "inspect", 
}
settings.SetAdditionalData(additionalData)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tlsInspectionPolicies, err := graphClient.NetworkAccess().TlsInspectionPolicies().ByTlsInspectionPolicyId("tlsInspectionPolicy-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicy tlsInspectionPolicy = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicy();
tlsInspectionPolicy.setName("New name TLS Inspection Policy");
tlsInspectionPolicy.setDescription("New description policy for inspecting TLS traffic");
com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicySettings settings = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicySettings();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("defaultAction", "inspect");
settings.setAdditionalData(additionalData);
tlsInspectionPolicy.setSettings(settings);
com.microsoft.graph.models.networkaccess.TlsInspectionPolicy result = graphClient.networkAccess().tlsInspectionPolicies().byTlsInspectionPolicyId("{tlsInspectionPolicy-id}").patch(tlsInspectionPolicy);
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
  name: 'New name TLS Inspection Policy',
  description: 'New description policy for inspecting TLS traffic',
  settings: {
        defaultAction: 'inspect'
    }
};

await client.api('/networkAccess/tlsInspectionPolicies/b712c469-e7cd-e7cb-738f-94b199570b0d')
	.version('beta')
	.update(tlsInspectionPolicy);
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
$requestBody->setName('New name TLS Inspection Policy');
$requestBody->setDescription('New description policy for inspecting TLS traffic');
$settings = new TlsInspectionPolicySettings();
$additionalData = [
	'defaultAction' => 'inspect',
];
$settings->setAdditionalData($additionalData);
$requestBody->setSettings($settings);

$result = $graphServiceClient->networkAccess()->tlsInspectionPolicies()->byTlsInspectionPolicyId('tlsInspectionPolicy-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "New name TLS Inspection Policy"
	description = "New description policy for inspecting TLS traffic"
	settings = @{
		defaultAction = "inspect"
	}
}

Update-MgBetaNetworkAccessTlInspectionPolicy -TlsInspectionPolicyId $tlsInspectionPolicyId -BodyParameter $params
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
	name = "New name TLS Inspection Policy",
	description = "New description policy for inspecting TLS traffic",
	settings = TlsInspectionPolicySettings(
		additional_data = {
				"default_action" : "inspect",
		}
	),
)

result = await graph_client.network_access.tls_inspection_policies.by_tls_inspection_policy_id('tlsInspectionPolicy-id').patch(request_body)
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
