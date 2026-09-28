<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update threatIntelligencePolicy

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta) object.

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
PATCH /networkAccess/threatIntelligencePolicies/{threatIntelligencePolicyId}
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
| name | String | The display name of the threat intelligence policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| description | String | A description of the threat intelligence policy. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| version | String | The version of the policy, used for tracking changes. Inherited from [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta). |
| settings | [microsoft.graph.networkaccess.threatIntelligencePolicySettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicysettings?view=graph-rest-beta) | Settings that define how the threat intelligence policy operates and evaluates threats. |

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
PATCH https://graph.microsoft.com/beta/networkAccess/threatIntelligencePolicies/{threatIntelligencePolicyId}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligencePolicy",
  "id": "a8352c78-90c6-4edd-aaca-9dc4292e7750",
  "name": "Threat Intel Policy",
  "description": "",
  "version": "1.0.0",
  "lastModifiedDateTime": "2025-06-18T17:34:25.8207682Z",
  "settings": {
    "defaultAction": "allow"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new ThreatIntelligencePolicy
{
	OdataType = "#microsoft.graph.networkaccess.threatIntelligencePolicy",
	Id = "a8352c78-90c6-4edd-aaca-9dc4292e7750",
	Name = "Threat Intel Policy",
	Description = "",
	Version = "1.0.0",
	LastModifiedDateTime = DateTimeOffset.Parse("2025-06-18T17:34:25.8207682Z"),
	Settings = new ThreatIntelligencePolicySettings
	{
		DefaultAction = ThreatIntelligenceAction.Allow,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.ThreatIntelligencePolicies["{threatIntelligencePolicy-id}"].PatchAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewThreatIntelligencePolicy()
id := "a8352c78-90c6-4edd-aaca-9dc4292e7750"
requestBody.SetId(&id) 
name := "Threat Intel Policy"
requestBody.SetName(&name) 
description := ""
requestBody.SetDescription(&description) 
version := "1.0.0"
requestBody.SetVersion(&version) 
lastModifiedDateTime , err := time.Parse(time.RFC3339, "2025-06-18T17:34:25.8207682Z")
requestBody.SetLastModifiedDateTime(&lastModifiedDateTime) 
settings := graphmodelsnetworkaccess.NewThreatIntelligencePolicySettings()
defaultAction := graphmodels.ALLOW_THREATINTELLIGENCEACTION 
settings.SetDefaultAction(&defaultAction) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
threatIntelligencePolicies, err := graphClient.NetworkAccess().ThreatIntelligencePolicies().ByThreatIntelligencePolicyId("threatIntelligencePolicy-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.ThreatIntelligencePolicy threatIntelligencePolicy = new com.microsoft.graph.beta.models.networkaccess.ThreatIntelligencePolicy();
threatIntelligencePolicy.setOdataType("#microsoft.graph.networkaccess.threatIntelligencePolicy");
threatIntelligencePolicy.setId("a8352c78-90c6-4edd-aaca-9dc4292e7750");
threatIntelligencePolicy.setName("Threat Intel Policy");
threatIntelligencePolicy.setDescription("");
threatIntelligencePolicy.setVersion("1.0.0");
OffsetDateTime lastModifiedDateTime = OffsetDateTime.parse("2025-06-18T17:34:25.8207682Z");
threatIntelligencePolicy.setLastModifiedDateTime(lastModifiedDateTime);
com.microsoft.graph.beta.models.networkaccess.ThreatIntelligencePolicySettings settings = new com.microsoft.graph.beta.models.networkaccess.ThreatIntelligencePolicySettings();
settings.setDefaultAction(com.microsoft.graph.beta.models.networkaccess.ThreatIntelligenceAction.Allow);
threatIntelligencePolicy.setSettings(settings);
com.microsoft.graph.models.networkaccess.ThreatIntelligencePolicy result = graphClient.networkAccess().threatIntelligencePolicies().byThreatIntelligencePolicyId("{threatIntelligencePolicy-id}").patch(threatIntelligencePolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const threatIntelligencePolicy = {
  '@odata.type': '#microsoft.graph.networkaccess.threatIntelligencePolicy',
  id: 'a8352c78-90c6-4edd-aaca-9dc4292e7750',
  name: 'Threat Intel Policy',
  description: '',
  version: '1.0.0',
  lastModifiedDateTime: '2025-06-18T17:34:25.8207682Z',
  settings: {
    defaultAction: 'allow'
  }
};

await client.api('/networkAccess/threatIntelligencePolicies/{threatIntelligencePolicyId}')
	.version('beta')
	.update(threatIntelligencePolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\ThreatIntelligencePolicy;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\ThreatIntelligencePolicySettings;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\ThreatIntelligenceAction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ThreatIntelligencePolicy();
$requestBody->setOdataType('#microsoft.graph.networkaccess.threatIntelligencePolicy');
$requestBody->setId('a8352c78-90c6-4edd-aaca-9dc4292e7750');
$requestBody->setName('Threat Intel Policy');
$requestBody->setDescription('');
$requestBody->setVersion('1.0.0');
$requestBody->setLastModifiedDateTime(new \DateTime('2025-06-18T17:34:25.8207682Z'));
$settings = new ThreatIntelligencePolicySettings();
$settings->setDefaultAction(new ThreatIntelligenceAction('allow'));
$requestBody->setSettings($settings);

$result = $graphServiceClient->networkAccess()->threatIntelligencePolicies()->byThreatIntelligencePolicyId('threatIntelligencePolicy-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.threatIntelligencePolicy"
	id = "a8352c78-90c6-4edd-aaca-9dc4292e7750"
	name = "Threat Intel Policy"
	description = ""
	version = "1.0.0"
	lastModifiedDateTime = [System.DateTime]::Parse("2025-06-18T17:34:25.8207682Z")
	settings = @{
		defaultAction = "allow"
	}
}

Update-MgBetaNetworkAccessThreatIntelligencePolicy -ThreatIntelligencePolicyId $threatIntelligencePolicyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.threat_intelligence_policy import ThreatIntelligencePolicy
from msgraph_beta.generated.models.networkaccess.threat_intelligence_policy_settings import ThreatIntelligencePolicySettings
from msgraph_beta.generated.models.threat_intelligence_action import ThreatIntelligenceAction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ThreatIntelligencePolicy(
	odata_type = "#microsoft.graph.networkaccess.threatIntelligencePolicy",
	id = "a8352c78-90c6-4edd-aaca-9dc4292e7750",
	name = "Threat Intel Policy",
	description = "",
	version = "1.0.0",
	last_modified_date_time = "2025-06-18T17:34:25.8207682Z",
	settings = ThreatIntelligencePolicySettings(
		default_action = ThreatIntelligenceAction.Allow,
	),
)

result = await graph_client.network_access.threat_intelligence_policies.by_threat_intelligence_policy_id('threatIntelligencePolicy-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
