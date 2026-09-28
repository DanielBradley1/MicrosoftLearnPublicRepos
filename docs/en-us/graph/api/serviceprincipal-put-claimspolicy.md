<!-- Source: https://learn.microsoft.com/en-us/graph/api/serviceprincipal-put-claimspolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-05 -->

# Create or replace claimsPolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [customClaimsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/customclaimspolicy?view=graph-rest-beta) object if it doesn't exist, or replace an existing one.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ApplicationConfiguration | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ApplicationConfiguration | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Application Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
PUT /servicePrincipals/{servicePrincipalsId}/claimsPolicy
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [customClaimsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/customclaimspolicy?view=graph-rest-beta) object.

You can specify the following properties when creating a **customClaimsPolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| includeBasicClaimSet | Boolean | Determines whether the basic claim set is included in tokens affected by this policy. If set to `true`, all claims in the basic claim set are emitted in tokens affected by the policy. By default the basic claim set isn't in the tokens, unless they're explicitly configured in this policy. Optional. |
| includeApplicationIdInIssuer | Boolean | Indicates whether the application ID is added to the claim. It is relevant only for SAML2.0 and if a custom signing key is used. the default value is `true`. Optional. |
| audienceOverride | String | If specified, it overrides the content of the audience claim for WS-Federation and SAML2 protocols. A custom signing key must be used for audienceOverride to be applied, otherwise audienceOverride value is ignored. The value provided must be in the format of an absolute URI. Optional. |
| claims | [customClaimBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimbase?view=graph-rest-beta) collection | Defines which claims are present in the tokens affected by the policy, in addition to the basic claim and the core claim set. Optional. |

## Response

If successful, this method returns a `204` response code and a [customClaimsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/customclaimspolicy?view=graph-rest-beta) object in the response body.

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
PUT https://graph.microsoft.com/beta/servicePrincipals/{servicePrincipalsId}/claimsPolicy
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.customClaimsPolicy",
  "includeBasicClaimSet": "Boolean",
  "includeApplicationIdInIssuer": "Boolean",
  "audienceOverride": "String",
  "claims": [
    {
      "@odata.type": "microsoft.graph.customClaim"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CustomClaimsPolicy
{
	OdataType = "#microsoft.graph.customClaimsPolicy",
	IncludeBasicClaimSet = boolean,
	IncludeApplicationIdInIssuer = boolean,
	AudienceOverride = "String",
	Claims = new List<CustomClaimBase>
	{
		new CustomClaim
		{
			OdataType = "microsoft.graph.customClaim",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].ClaimsPolicy.PutAsync(requestBody);
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

requestBody := graphmodels.NewCustomClaimsPolicy()
includeBasicClaimSet := boolean
requestBody.SetIncludeBasicClaimSet(&includeBasicClaimSet) 
includeApplicationIdInIssuer := boolean
requestBody.SetIncludeApplicationIdInIssuer(&includeApplicationIdInIssuer) 
audienceOverride := "String"
requestBody.SetAudienceOverride(&audienceOverride) 


customClaimBase := graphmodels.NewCustomClaim()

claims := []graphmodels.CustomClaimBaseable {
	customClaimBase,
}
requestBody.SetClaims(claims)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
claimsPolicy, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").ClaimsPolicy().Put(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomClaimsPolicy customClaimsPolicy = new CustomClaimsPolicy();
customClaimsPolicy.setOdataType("#microsoft.graph.customClaimsPolicy");
customClaimsPolicy.setIncludeBasicClaimSet(boolean);
customClaimsPolicy.setIncludeApplicationIdInIssuer(boolean);
customClaimsPolicy.setAudienceOverride("String");
LinkedList<CustomClaimBase> claims = new LinkedList<CustomClaimBase>();
CustomClaim customClaimBase = new CustomClaim();
customClaimBase.setOdataType("microsoft.graph.customClaim");
claims.add(customClaimBase);
customClaimsPolicy.setClaims(claims);
CustomClaimsPolicy result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").claimsPolicy().put(customClaimsPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customClaimsPolicy = {
  '@odata.type': '#microsoft.graph.customClaimsPolicy',
  includeBasicClaimSet: 'Boolean',
  includeApplicationIdInIssuer: 'Boolean',
  audienceOverride: 'String',
  claims: [
    {
      '@odata.type': 'microsoft.graph.customClaim'
    }
  ]
};

await client.api('/servicePrincipals/{servicePrincipalsId}/claimsPolicy')
	.version('beta')
	.put(customClaimsPolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CustomClaimsPolicy;
use Microsoft\Graph\Beta\Generated\Models\CustomClaimBase;
use Microsoft\Graph\Beta\Generated\Models\CustomClaim;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomClaimsPolicy();
$requestBody->setOdataType('#microsoft.graph.customClaimsPolicy');
$requestBody->setIncludeBasicClaimSet(boolean);
$requestBody->setIncludeApplicationIdInIssuer(boolean);
$requestBody->setAudienceOverride('String');
$claimsCustomClaimBase1 = new CustomClaim();
$claimsCustomClaimBase1->setOdataType('microsoft.graph.customClaim');
$claimsArray []= $claimsCustomClaimBase1;
$requestBody->setClaims($claimsArray);


$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->claimsPolicy()->put($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Applications

$params = @{
	"@odata.type" = "#microsoft.graph.customClaimsPolicy"
	includeBasicClaimSet = "Boolean"
	includeApplicationIdInIssuer = "Boolean"
	audienceOverride = "String"
	claims = @(
		@{
			"@odata.type" = "microsoft.graph.customClaim"
		}
	)
}

Set-MgBetaServicePrincipalClaimPolicy -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.custom_claims_policy import CustomClaimsPolicy
from msgraph_beta.generated.models.custom_claim_base import CustomClaimBase
from msgraph_beta.generated.models.custom_claim import CustomClaim
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomClaimsPolicy(
	odata_type = "#microsoft.graph.customClaimsPolicy",
	include_basic_claim_set = Boolean,
	include_application_id_in_issuer = Boolean,
	audience_override = "String",
	claims = [
		CustomClaim(
			odata_type = "microsoft.graph.customClaim",
		),
	],
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').claims_policy.put(request_body)
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
  "@odata.type": "#microsoft.graph.customClaimsPolicy",
  "id": "f914f36d-167e-3fa7-cfa2-355cc5a36689",
  "includeBasicClaimSet": "Boolean",
  "includeApplicationIdInIssuer": "Boolean",
  "audienceOverride": "String",
  "claims": [
    {
      "@odata.type": "microsoft.graph.customClaim"
    }
  ]
}
```
