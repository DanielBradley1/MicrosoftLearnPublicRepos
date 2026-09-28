<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringpolicylink-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Add policy to filteringProfile

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Add a Global Secure Access network policy to a [filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta). The policy can be one of the following types:

- [filteringPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringpolicy?view=graph-rest-beta)
- [threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta)
- [tlsInspectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionpolicy?view=graph-rest-beta)

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policy
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) object.

You can specify the following properties when creating a **policy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The display name of the policy. Required. |
| description | String | A description of the policy. Optional. |
| version | String | The version of the policy, used for tracking changes. Required. |

## Response

If successful, this method returns a `204 No Content` response code and a [microsoft.graph.networkaccess.policy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policy?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Add a filteringPolicy to a filteringProfile

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policy
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligencePolicy",
  "name": "Threat Intel Policy",
  "description": "",
  "version": "1.0.0",
  "settings": {
    "defaultAction": "allow"
  }
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
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

### Example 2: Add a tlsInspectionPolicy to a filteringProfile

#### Request

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
POST https://graph.microsoft.com/beta/networkAccess/filteringProfiles/d734d2de-f2df-4b4a-8c4c-5111f8878275/policies
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionPolicyLink",
  "state": "enabled",
  "policy": {
    "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionPolicy",
    "id": "b712c469-e7cd-e7cb-738f-94b199570b0d"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new TlsInspectionPolicyLink
{
	OdataType = "#microsoft.graph.networkaccess.tlsInspectionPolicyLink",
	State = Status.Enabled,
	Policy = new TlsInspectionPolicy
	{
		OdataType = "#microsoft.graph.networkaccess.tlsInspectionPolicy",
		Id = "b712c469-e7cd-e7cb-738f-94b199570b0d",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.FilteringProfiles["{filteringProfile-id}"].Policies.PostAsync(requestBody);
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

requestBody := graphmodelsnetworkaccess.NewPolicyLink()
state := graphmodels.ENABLED_STATUS 
requestBody.SetState(&state) 
policy := graphmodelsnetworkaccess.NewTlsInspectionPolicy()
id := "b712c469-e7cd-e7cb-738f-94b199570b0d"
policy.SetId(&id) 
requestBody.SetPolicy(policy)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policies, err := graphClient.NetworkAccess().FilteringProfiles().ByFilteringProfileId("filteringProfile-id").Policies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicyLink policyLink = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicyLink();
policyLink.setOdataType("#microsoft.graph.networkaccess.tlsInspectionPolicyLink");
policyLink.setState(com.microsoft.graph.beta.models.networkaccess.Status.Enabled);
com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicy policy = new com.microsoft.graph.beta.models.networkaccess.TlsInspectionPolicy();
policy.setOdataType("#microsoft.graph.networkaccess.tlsInspectionPolicy");
policy.setId("b712c469-e7cd-e7cb-738f-94b199570b0d");
policyLink.setPolicy(policy);
com.microsoft.graph.models.networkaccess.PolicyLink result = graphClient.networkAccess().filteringProfiles().byFilteringProfileId("{filteringProfile-id}").policies().post(policyLink);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const policyLink = {
  '@odata.type': '#microsoft.graph.networkaccess.tlsInspectionPolicyLink',
  state: 'enabled',
  policy: {
    '@odata.type': '#microsoft.graph.networkaccess.tlsInspectionPolicy',
    id: 'b712c469-e7cd-e7cb-738f-94b199570b0d'
  }
};

await client.api('/networkAccess/filteringProfiles/d734d2de-f2df-4b4a-8c4c-5111f8878275/policies')
	.version('beta')
	.post(policyLink);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionPolicyLink;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\Status;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TlsInspectionPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TlsInspectionPolicyLink();
$requestBody->setOdataType('#microsoft.graph.networkaccess.tlsInspectionPolicyLink');
$requestBody->setState(new Status('enabled'));
$policy = new TlsInspectionPolicy();
$policy->setOdataType('#microsoft.graph.networkaccess.tlsInspectionPolicy');
$policy->setId('b712c469-e7cd-e7cb-738f-94b199570b0d');
$requestBody->setPolicy($policy);

$result = $graphServiceClient->networkAccess()->filteringProfiles()->byFilteringProfileId('filteringProfile-id')->policies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	"@odata.type" = "#microsoft.graph.networkaccess.tlsInspectionPolicyLink"
	state = "enabled"
	policy = @{
		"@odata.type" = "#microsoft.graph.networkaccess.tlsInspectionPolicy"
		id = "b712c469-e7cd-e7cb-738f-94b199570b0d"
	}
}

New-MgBetaNetworkAccessFilteringProfilePolicy -FilteringProfileId $filteringProfileId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.tls_inspection_policy_link import TlsInspectionPolicyLink
from msgraph_beta.generated.models.status import Status
from msgraph_beta.generated.models.networkaccess.tls_inspection_policy import TlsInspectionPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TlsInspectionPolicyLink(
	odata_type = "#microsoft.graph.networkaccess.tlsInspectionPolicyLink",
	state = Status.Enabled,
	policy = TlsInspectionPolicy(
		odata_type = "#microsoft.graph.networkaccess.tlsInspectionPolicy",
		id = "b712c469-e7cd-e7cb-738f-94b199570b0d",
	),
)

result = await graph_client.network_access.filtering_profiles.by_filtering_profile_id('filteringProfile-id').policies.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionPolicyLink",
  "id": "70405a6c-b823-c521-c981-de9d08a21f8f",
  "state": "enabled",
  "version": "1.0",
  "policy": {
    "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionPolicy",
    "id": "b712c469-e7cd-e7cb-738f-94b199570b0d",
    "name": "Default TLS Inspection Policy",
    "description": "Policy for inspecting TLS traffic",
    "version": "1.0.0",
    "lastModifiedDateTime": "2025-06-02T20:54:19.146638Z",
    "settings": {
      "defaultAction": "bypass"
    }
  }
}
```
