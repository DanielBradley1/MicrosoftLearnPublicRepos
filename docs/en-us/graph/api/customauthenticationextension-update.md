<!-- Source: https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Update customAuthenticationExtension

Namespace: microsoft.graph

Update the properties of a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) object. The following derived types are currently supported.

- [onTokenIssuanceStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitcustomextension?view=graph-rest-1.0) resource type.
- [onOtpSendCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextension?view=graph-rest-1.0) resource type.
- [onVerifiedIdClaimValidationCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onverifiedidclaimvalidationcustomextension?view=graph-rest-1.0) resource type.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CustomAuthenticationExtension.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CustomAuthenticationExtension.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the admin must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Authentication Extensibility Administrator
- Application Administrator

## HTTP request

```http
PATCH /identity/customAuthenticationExtensions/{customAuthenticationExtensionId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the `@odata.type` property when updating a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) object. For example, to update an [onTokenIssuanceStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension?view=graph-rest-1.0) object type, set the `@odata.type` property to `#microsoft.graph.onTokenIssuanceStartCustomExtension`.

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | The authentication configuration for this custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| description | String | Description for the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| displayName | String | Display name for the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| handler | [onAttributeCollectionStartCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextensionhandler?view=graph-rest-1.0) | The handler to invoke when conditions are met. Can be updated for the **onAttributeCollectionStartCustomExtensionListener** listener type. |
| handler | [onAttributeCollectionSubmitCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitcustomextensionhandler?view=graph-rest-1.0) | The handler to invoke when conditions are met. Can be updated for the **onAttributeCollectionSubmitCustomExtensionListener** listener type. |
| handler | [onOtpSendCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextensionhandler?view=graph-rest-1.0) | The handler to invoke when conditions are met. Can be updated for the **onOtpSendCustomExtensionListener** listener type. |
| handler | [onTokenIssuanceStartCustomExtensionHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextensionhandler?view=graph-rest-1.0) | The handler to invoke when conditions are met. Can be updated for the **onTokenIssuanceStartCustomExtensionListener** listener type. |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | Configuration for the API endpoint that the custom extension will call. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| behaviorOnError | [customExtensionBehaviorOnError](https://learn.microsoft.com/en-us/graph/api/resources/customextensionbehavioronerror?view=graph-rest-1.0) | Let to configure behavior if the call to custom authentication extension returns error. Optional. |

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
PATCH https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions/6fc5012e-7665-43d6-9708-4370863f4e6e
Content-Type: application/json
Content-length: 468

{
    "@odata.type": "#microsoft.graph.onTokenIssuanceStartCustomExtension",
    "displayName": "onTokenIssuanceStartCustomExtension",
    "description": "Fetch additional claims from custom user store",
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://authenticationeventsAPI.contoso.com"
    },
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4"
    },
    "claimsForTokenConfiguration": [
        {
            "claimIdInApiResponse": "DateOfBirth"
        },
        {
            "claimIdInApiResponse": "CustomRoles"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnTokenIssuanceStartCustomExtension
{
	OdataType = "#microsoft.graph.onTokenIssuanceStartCustomExtension",
	DisplayName = "onTokenIssuanceStartCustomExtension",
	Description = "Fetch additional claims from custom user store",
	EndpointConfiguration = new HttpRequestEndpoint
	{
		OdataType = "#microsoft.graph.httpRequestEndpoint",
		TargetUrl = "https://authenticationeventsAPI.contoso.com",
	},
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4",
	},
	ClaimsForTokenConfiguration = new List<OnTokenIssuanceStartReturnClaim>
	{
		new OnTokenIssuanceStartReturnClaim
		{
			ClaimIdInApiResponse = "DateOfBirth",
		},
		new OnTokenIssuanceStartReturnClaim
		{
			ClaimIdInApiResponse = "CustomRoles",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.CustomAuthenticationExtensions["{customAuthenticationExtension-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewCustomAuthenticationExtension()
displayName := "onTokenIssuanceStartCustomExtension"
requestBody.SetDisplayName(&displayName) 
description := "Fetch additional claims from custom user store"
requestBody.SetDescription(&description) 
endpointConfiguration := graphmodels.NewHttpRequestEndpoint()
targetUrl := "https://authenticationeventsAPI.contoso.com"
endpointConfiguration.SetTargetUrl(&targetUrl) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)


onTokenIssuanceStartReturnClaim := graphmodels.NewOnTokenIssuanceStartReturnClaim()
claimIdInApiResponse := "DateOfBirth"
onTokenIssuanceStartReturnClaim.SetClaimIdInApiResponse(&claimIdInApiResponse) 
onTokenIssuanceStartReturnClaim1 := graphmodels.NewOnTokenIssuanceStartReturnClaim()
claimIdInApiResponse := "CustomRoles"
onTokenIssuanceStartReturnClaim1.SetClaimIdInApiResponse(&claimIdInApiResponse) 

claimsForTokenConfiguration := []graphmodels.OnTokenIssuanceStartReturnClaimable {
	onTokenIssuanceStartReturnClaim,
	onTokenIssuanceStartReturnClaim1,
}
requestBody.SetClaimsForTokenConfiguration(claimsForTokenConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAuthenticationExtensions, err := graphClient.Identity().CustomAuthenticationExtensions().ByCustomAuthenticationExtensionId("customAuthenticationExtension-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnTokenIssuanceStartCustomExtension customAuthenticationExtension = new OnTokenIssuanceStartCustomExtension();
customAuthenticationExtension.setOdataType("#microsoft.graph.onTokenIssuanceStartCustomExtension");
customAuthenticationExtension.setDisplayName("onTokenIssuanceStartCustomExtension");
customAuthenticationExtension.setDescription("Fetch additional claims from custom user store");
HttpRequestEndpoint endpointConfiguration = new HttpRequestEndpoint();
endpointConfiguration.setOdataType("#microsoft.graph.httpRequestEndpoint");
endpointConfiguration.setTargetUrl("https://authenticationeventsAPI.contoso.com");
customAuthenticationExtension.setEndpointConfiguration(endpointConfiguration);
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4");
customAuthenticationExtension.setAuthenticationConfiguration(authenticationConfiguration);
LinkedList<OnTokenIssuanceStartReturnClaim> claimsForTokenConfiguration = new LinkedList<OnTokenIssuanceStartReturnClaim>();
OnTokenIssuanceStartReturnClaim onTokenIssuanceStartReturnClaim = new OnTokenIssuanceStartReturnClaim();
onTokenIssuanceStartReturnClaim.setClaimIdInApiResponse("DateOfBirth");
claimsForTokenConfiguration.add(onTokenIssuanceStartReturnClaim);
OnTokenIssuanceStartReturnClaim onTokenIssuanceStartReturnClaim1 = new OnTokenIssuanceStartReturnClaim();
onTokenIssuanceStartReturnClaim1.setClaimIdInApiResponse("CustomRoles");
claimsForTokenConfiguration.add(onTokenIssuanceStartReturnClaim1);
customAuthenticationExtension.setClaimsForTokenConfiguration(claimsForTokenConfiguration);
CustomAuthenticationExtension result = graphClient.identity().customAuthenticationExtensions().byCustomAuthenticationExtensionId("{customAuthenticationExtension-id}").patch(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAuthenticationExtension = {
    '@odata.type': '#microsoft.graph.onTokenIssuanceStartCustomExtension',
    displayName: 'onTokenIssuanceStartCustomExtension',
    description: 'Fetch additional claims from custom user store',
    endpointConfiguration: {
        '@odata.type': '#microsoft.graph.httpRequestEndpoint',
        targetUrl: 'https://authenticationeventsAPI.contoso.com'
    },
    authenticationConfiguration: {
        '@odata.type': '#microsoft.graph.azureAdTokenAuthentication',
        resourceId: 'api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4'
    },
    claimsForTokenConfiguration: [
        {
            claimIdInApiResponse: 'DateOfBirth'
        },
        {
            claimIdInApiResponse: 'CustomRoles'
        }
    ]
};

await client.api('/identity/customAuthenticationExtensions/6fc5012e-7665-43d6-9708-4370863f4e6e')
	.update(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnTokenIssuanceStartCustomExtension;
use Microsoft\Graph\Generated\Models\HttpRequestEndpoint;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\OnTokenIssuanceStartReturnClaim;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnTokenIssuanceStartCustomExtension();
$requestBody->setOdataType('#microsoft.graph.onTokenIssuanceStartCustomExtension');
$requestBody->setDisplayName('onTokenIssuanceStartCustomExtension');
$requestBody->setDescription('Fetch additional claims from custom user store');
$endpointConfiguration = new HttpRequestEndpoint();
$endpointConfiguration->setOdataType('#microsoft.graph.httpRequestEndpoint');
$endpointConfiguration->setTargetUrl('https://authenticationeventsAPI.contoso.com');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim1 = new OnTokenIssuanceStartReturnClaim();
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim1->setClaimIdInApiResponse('DateOfBirth');
$claimsForTokenConfigurationArray []= $claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim1;
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim2 = new OnTokenIssuanceStartReturnClaim();
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim2->setClaimIdInApiResponse('CustomRoles');
$claimsForTokenConfigurationArray []= $claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim2;
$requestBody->setClaimsForTokenConfiguration($claimsForTokenConfigurationArray);


$result = $graphServiceClient->identity()->customAuthenticationExtensions()->byCustomAuthenticationExtensionId('customAuthenticationExtension-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onTokenIssuanceStartCustomExtension"
	displayName = "onTokenIssuanceStartCustomExtension"
	description = "Fetch additional claims from custom user store"
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.httpRequestEndpoint"
		targetUrl = "https://authenticationeventsAPI.contoso.com"
	}
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4"
	}
	claimsForTokenConfiguration = @(
		@{
			claimIdInApiResponse = "DateOfBirth"
		}
		@{
			claimIdInApiResponse = "CustomRoles"
		}
	)
}

Update-MgIdentityCustomAuthenticationExtension -CustomAuthenticationExtensionId $customAuthenticationExtensionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_token_issuance_start_custom_extension import OnTokenIssuanceStartCustomExtension
from msgraph.generated.models.http_request_endpoint import HttpRequestEndpoint
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.on_token_issuance_start_return_claim import OnTokenIssuanceStartReturnClaim
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnTokenIssuanceStartCustomExtension(
	odata_type = "#microsoft.graph.onTokenIssuanceStartCustomExtension",
	display_name = "onTokenIssuanceStartCustomExtension",
	description = "Fetch additional claims from custom user store",
	endpoint_configuration = HttpRequestEndpoint(
		odata_type = "#microsoft.graph.httpRequestEndpoint",
		target_url = "https://authenticationeventsAPI.contoso.com",
	),
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4",
	),
	claims_for_token_configuration = [
		OnTokenIssuanceStartReturnClaim(
			claim_id_in_api_response = "DateOfBirth",
		),
		OnTokenIssuanceStartReturnClaim(
			claim_id_in_api_response = "CustomRoles",
		),
	],
)

result = await graph_client.identity.custom_authentication_extensions.by_custom_authentication_extension_id('customAuthenticationExtension-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
