<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-customauthenticationextensions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Create customAuthenticationExtension

Namespace: microsoft.graph

Create a new [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) object. The following derived types are currently supported.

- [onTokenIssuanceStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionstartcustomextension?view=graph-rest-1.0) resource type.
- [onAttributeCollectionSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onattributecollectionsubmitcustomextension?view=graph-rest-1.0) resource type.
- [onOtpSendCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onotpsendcustomextension?view=graph-rest-1.0) resource type.
- [onPasswordSubmitCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/onpasswordsubmitcustomextension?view=graph-rest-1.0) resource type.

Note

You can have a maximum of 100 custom extension policies.

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
POST /identity/customAuthenticationExtensions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) object.

You can specify the following properties when creating a **customAuthenticationExtension**. You must specify the **@odata.type** property with a value of the customAuthenticationExtension object type that you want to create. For example, to create an **onTokenIssuanceStartCustomExtension** object, set **@odata.type** to `#microsoft.graph.onTokenIssuanceStartCustomExtension`.

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | The authentication configuration for this custom extension. Required. |
| behaviorOnError | [customExtensionBehaviorOnError](https://learn.microsoft.com/en-us/graph/api/resources/customextensionbehavioronerror?view=graph-rest-1.0) | Lets you to configure behavior if the call to custom authentication extension returns an error. Optional. |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | The connection settings for the custom extension. Optional. |
| description | String | Description for the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| displayName | String | Display name for the custom extension. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | Configuration for the API endpoint that the custom extension will call. Inherited from [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0). Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an onTokenIssuanceStartCustomExtension object

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
POST https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions
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
    "clientConfiguration": {
        "timeoutInMilliseconds": 2000,
        "maximumRetries": 1
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
	ClientConfiguration = new CustomExtensionClientConfiguration
	{
		TimeoutInMilliseconds = 2000,
		MaximumRetries = 1,
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
var result = await graphClient.Identity.CustomAuthenticationExtensions.PostAsync(requestBody);
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
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
timeoutInMilliseconds := int32(2000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
requestBody.SetClientConfiguration(clientConfiguration)


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
customAuthenticationExtensions, err := graphClient.Identity().CustomAuthenticationExtensions().Post(context.Background(), requestBody, nil)
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
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setTimeoutInMilliseconds(2000);
clientConfiguration.setMaximumRetries(1);
customAuthenticationExtension.setClientConfiguration(clientConfiguration);
LinkedList<OnTokenIssuanceStartReturnClaim> claimsForTokenConfiguration = new LinkedList<OnTokenIssuanceStartReturnClaim>();
OnTokenIssuanceStartReturnClaim onTokenIssuanceStartReturnClaim = new OnTokenIssuanceStartReturnClaim();
onTokenIssuanceStartReturnClaim.setClaimIdInApiResponse("DateOfBirth");
claimsForTokenConfiguration.add(onTokenIssuanceStartReturnClaim);
OnTokenIssuanceStartReturnClaim onTokenIssuanceStartReturnClaim1 = new OnTokenIssuanceStartReturnClaim();
onTokenIssuanceStartReturnClaim1.setClaimIdInApiResponse("CustomRoles");
claimsForTokenConfiguration.add(onTokenIssuanceStartReturnClaim1);
customAuthenticationExtension.setClaimsForTokenConfiguration(claimsForTokenConfiguration);
CustomAuthenticationExtension result = graphClient.identity().customAuthenticationExtensions().post(customAuthenticationExtension);
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
    clientConfiguration: {
        timeoutInMilliseconds: 2000,
        maximumRetries: 1
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

await client.api('/identity/customAuthenticationExtensions')
	.post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnTokenIssuanceStartCustomExtension;
use Microsoft\Graph\Generated\Models\HttpRequestEndpoint;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;
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
$clientConfiguration = new CustomExtensionClientConfiguration();
$clientConfiguration->setTimeoutInMilliseconds(2000);
$clientConfiguration->setMaximumRetries(1);
$requestBody->setClientConfiguration($clientConfiguration);
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim1 = new OnTokenIssuanceStartReturnClaim();
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim1->setClaimIdInApiResponse('DateOfBirth');
$claimsForTokenConfigurationArray []= $claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim1;
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim2 = new OnTokenIssuanceStartReturnClaim();
$claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim2->setClaimIdInApiResponse('CustomRoles');
$claimsForTokenConfigurationArray []= $claimsForTokenConfigurationOnTokenIssuanceStartReturnClaim2;
$requestBody->setClaimsForTokenConfiguration($claimsForTokenConfigurationArray);


$result = $graphServiceClient->identity()->customAuthenticationExtensions()->post($requestBody)->wait();
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
	clientConfiguration = @{
		timeoutInMilliseconds = 2000
		maximumRetries = 1
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

New-MgIdentityCustomAuthenticationExtension -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_token_issuance_start_custom_extension import OnTokenIssuanceStartCustomExtension
from msgraph.generated.models.http_request_endpoint import HttpRequestEndpoint
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
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
	client_configuration = CustomExtensionClientConfiguration(
		timeout_in_milliseconds = 2000,
		maximum_retries = 1,
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

result = await graph_client.identity.custom_authentication_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/customAuthenticationExtensions/$entity",
    "@odata.type": "#microsoft.graph.onTokenIssuanceStartCustomExtension",
    "id": "6fc5012e-7665-43d6-9708-4370863f4e6e",
    "displayName": "onTokenIssuanceStartCustomExtension",
    "description": "Fetch additional claims from custom user store",
    "clientConfiguration": null,
    "behaviorOnError": null,
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://authenticationeventsAPI.contoso.com/a13d0fc1-04ab-4ede-b215-63de0174cbb4"
    },
    "clientConfiguration": {
        "timeoutInMilliseconds": 2000,
        "maximumRetries": 1
    },
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://authenticationeventsAPI.contoso.com"
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

### Example 2: Create an onAttributeCollectionStartCustomExtension object

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onAttributeCollectionStartCustomExtension",
  "displayName": "attributeCollectionStartName",
  "description": "example description",
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
  },
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.httpRequestEndpoint",
    "targetUrl": "https://contoso.com"
  },
  "clientConfiguration": {
    "timeoutInMilliseconds": 2000,
    "maximumRetries": 1
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnAttributeCollectionStartCustomExtension
{
	OdataType = "#microsoft.graph.onAttributeCollectionStartCustomExtension",
	DisplayName = "attributeCollectionStartName",
	Description = "example description",
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e",
	},
	EndpointConfiguration = new HttpRequestEndpoint
	{
		OdataType = "#microsoft.graph.httpRequestEndpoint",
		TargetUrl = "https://contoso.com",
	},
	ClientConfiguration = new CustomExtensionClientConfiguration
	{
		TimeoutInMilliseconds = 2000,
		MaximumRetries = 1,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.CustomAuthenticationExtensions.PostAsync(requestBody);
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
displayName := "attributeCollectionStartName"
requestBody.SetDisplayName(&displayName) 
description := "example description"
requestBody.SetDescription(&description) 
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)
endpointConfiguration := graphmodels.NewHttpRequestEndpoint()
targetUrl := "https://contoso.com"
endpointConfiguration.SetTargetUrl(&targetUrl) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
timeoutInMilliseconds := int32(2000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
requestBody.SetClientConfiguration(clientConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAuthenticationExtensions, err := graphClient.Identity().CustomAuthenticationExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnAttributeCollectionStartCustomExtension customAuthenticationExtension = new OnAttributeCollectionStartCustomExtension();
customAuthenticationExtension.setOdataType("#microsoft.graph.onAttributeCollectionStartCustomExtension");
customAuthenticationExtension.setDisplayName("attributeCollectionStartName");
customAuthenticationExtension.setDescription("example description");
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e");
customAuthenticationExtension.setAuthenticationConfiguration(authenticationConfiguration);
HttpRequestEndpoint endpointConfiguration = new HttpRequestEndpoint();
endpointConfiguration.setOdataType("#microsoft.graph.httpRequestEndpoint");
endpointConfiguration.setTargetUrl("https://contoso.com");
customAuthenticationExtension.setEndpointConfiguration(endpointConfiguration);
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setTimeoutInMilliseconds(2000);
clientConfiguration.setMaximumRetries(1);
customAuthenticationExtension.setClientConfiguration(clientConfiguration);
CustomAuthenticationExtension result = graphClient.identity().customAuthenticationExtensions().post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAuthenticationExtension = {
  '@odata.type': '#microsoft.graph.onAttributeCollectionStartCustomExtension',
  displayName: 'attributeCollectionStartName',
  description: 'example description',
  authenticationConfiguration: {
    '@odata.type': '#microsoft.graph.azureAdTokenAuthentication',
    resourceId: 'api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e'
  },
  endpointConfiguration: {
    '@odata.type': '#microsoft.graph.httpRequestEndpoint',
    targetUrl: 'https://contoso.com'
  },
  clientConfiguration: {
    timeoutInMilliseconds: 2000,
    maximumRetries: 1
  }
};

await client.api('/identity/customAuthenticationExtensions')
	.post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnAttributeCollectionStartCustomExtension;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\HttpRequestEndpoint;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnAttributeCollectionStartCustomExtension();
$requestBody->setOdataType('#microsoft.graph.onAttributeCollectionStartCustomExtension');
$requestBody->setDisplayName('attributeCollectionStartName');
$requestBody->setDescription('example description');
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$endpointConfiguration = new HttpRequestEndpoint();
$endpointConfiguration->setOdataType('#microsoft.graph.httpRequestEndpoint');
$endpointConfiguration->setTargetUrl('https://contoso.com');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$clientConfiguration = new CustomExtensionClientConfiguration();
$clientConfiguration->setTimeoutInMilliseconds(2000);
$clientConfiguration->setMaximumRetries(1);
$requestBody->setClientConfiguration($clientConfiguration);

$result = $graphServiceClient->identity()->customAuthenticationExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onAttributeCollectionStartCustomExtension"
	displayName = "attributeCollectionStartName"
	description = "example description"
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
	}
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.httpRequestEndpoint"
		targetUrl = "https://contoso.com"
	}
	clientConfiguration = @{
		timeoutInMilliseconds = 2000
		maximumRetries = 1
	}
}

New-MgIdentityCustomAuthenticationExtension -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_attribute_collection_start_custom_extension import OnAttributeCollectionStartCustomExtension
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.http_request_endpoint import HttpRequestEndpoint
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnAttributeCollectionStartCustomExtension(
	odata_type = "#microsoft.graph.onAttributeCollectionStartCustomExtension",
	display_name = "attributeCollectionStartName",
	description = "example description",
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e",
	),
	endpoint_configuration = HttpRequestEndpoint(
		odata_type = "#microsoft.graph.httpRequestEndpoint",
		target_url = "https://contoso.com",
	),
	client_configuration = CustomExtensionClientConfiguration(
		timeout_in_milliseconds = 2000,
		maximum_retries = 1,
	),
)

result = await graph_client.identity.custom_authentication_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/customAuthenticationExtensions/$entity",
    "@odata.type": "#microsoft.graph.onAttributeCollectionStartCustomExtension",
    "id": "2d9c3e8d-88a9-444e-8c4c-f0c6c4fe1c02",
    "displayName": "attributeCollectionStartName",
    "description": "example description",
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
    },
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://contoso.com"
    },
    "clientConfiguration": {
        "timeoutInMilliseconds": 2000,
        "maximumRetries": 1
    }
}
```

### Example 3: Create an onAttributeCollectionSubmitCustomExtension object

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.onAttributeCollectionSubmitCustomExtension",
    "displayName": "attributeCollectionSubmitName",
    "description": "example description",
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
    },
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://contoso.com"
    },
    "clientConfiguration": {
        "timeoutInMilliseconds": 2000,
        "maximumRetries": 1
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnAttributeCollectionSubmitCustomExtension
{
	OdataType = "#microsoft.graph.onAttributeCollectionSubmitCustomExtension",
	DisplayName = "attributeCollectionSubmitName",
	Description = "example description",
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e",
	},
	EndpointConfiguration = new HttpRequestEndpoint
	{
		OdataType = "#microsoft.graph.httpRequestEndpoint",
		TargetUrl = "https://contoso.com",
	},
	ClientConfiguration = new CustomExtensionClientConfiguration
	{
		TimeoutInMilliseconds = 2000,
		MaximumRetries = 1,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.CustomAuthenticationExtensions.PostAsync(requestBody);
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
displayName := "attributeCollectionSubmitName"
requestBody.SetDisplayName(&displayName) 
description := "example description"
requestBody.SetDescription(&description) 
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)
endpointConfiguration := graphmodels.NewHttpRequestEndpoint()
targetUrl := "https://contoso.com"
endpointConfiguration.SetTargetUrl(&targetUrl) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
timeoutInMilliseconds := int32(2000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
requestBody.SetClientConfiguration(clientConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAuthenticationExtensions, err := graphClient.Identity().CustomAuthenticationExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnAttributeCollectionSubmitCustomExtension customAuthenticationExtension = new OnAttributeCollectionSubmitCustomExtension();
customAuthenticationExtension.setOdataType("#microsoft.graph.onAttributeCollectionSubmitCustomExtension");
customAuthenticationExtension.setDisplayName("attributeCollectionSubmitName");
customAuthenticationExtension.setDescription("example description");
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e");
customAuthenticationExtension.setAuthenticationConfiguration(authenticationConfiguration);
HttpRequestEndpoint endpointConfiguration = new HttpRequestEndpoint();
endpointConfiguration.setOdataType("#microsoft.graph.httpRequestEndpoint");
endpointConfiguration.setTargetUrl("https://contoso.com");
customAuthenticationExtension.setEndpointConfiguration(endpointConfiguration);
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setTimeoutInMilliseconds(2000);
clientConfiguration.setMaximumRetries(1);
customAuthenticationExtension.setClientConfiguration(clientConfiguration);
CustomAuthenticationExtension result = graphClient.identity().customAuthenticationExtensions().post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAuthenticationExtension = {
    '@odata.type': '#microsoft.graph.onAttributeCollectionSubmitCustomExtension',
    displayName: 'attributeCollectionSubmitName',
    description: 'example description',
    authenticationConfiguration: {
        '@odata.type': '#microsoft.graph.azureAdTokenAuthentication',
        resourceId: 'api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e'
    },
    endpointConfiguration: {
        '@odata.type': '#microsoft.graph.httpRequestEndpoint',
        targetUrl: 'https://contoso.com'
    },
    clientConfiguration: {
        timeoutInMilliseconds: 2000,
        maximumRetries: 1
    }
};

await client.api('/identity/customAuthenticationExtensions')
	.post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnAttributeCollectionSubmitCustomExtension;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\HttpRequestEndpoint;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnAttributeCollectionSubmitCustomExtension();
$requestBody->setOdataType('#microsoft.graph.onAttributeCollectionSubmitCustomExtension');
$requestBody->setDisplayName('attributeCollectionSubmitName');
$requestBody->setDescription('example description');
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$endpointConfiguration = new HttpRequestEndpoint();
$endpointConfiguration->setOdataType('#microsoft.graph.httpRequestEndpoint');
$endpointConfiguration->setTargetUrl('https://contoso.com');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$clientConfiguration = new CustomExtensionClientConfiguration();
$clientConfiguration->setTimeoutInMilliseconds(2000);
$clientConfiguration->setMaximumRetries(1);
$requestBody->setClientConfiguration($clientConfiguration);

$result = $graphServiceClient->identity()->customAuthenticationExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onAttributeCollectionSubmitCustomExtension"
	displayName = "attributeCollectionSubmitName"
	description = "example description"
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
	}
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.httpRequestEndpoint"
		targetUrl = "https://contoso.com"
	}
	clientConfiguration = @{
		timeoutInMilliseconds = 2000
		maximumRetries = 1
	}
}

New-MgIdentityCustomAuthenticationExtension -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_attribute_collection_submit_custom_extension import OnAttributeCollectionSubmitCustomExtension
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.http_request_endpoint import HttpRequestEndpoint
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnAttributeCollectionSubmitCustomExtension(
	odata_type = "#microsoft.graph.onAttributeCollectionSubmitCustomExtension",
	display_name = "attributeCollectionSubmitName",
	description = "example description",
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e",
	),
	endpoint_configuration = HttpRequestEndpoint(
		odata_type = "#microsoft.graph.httpRequestEndpoint",
		target_url = "https://contoso.com",
	),
	client_configuration = CustomExtensionClientConfiguration(
		timeout_in_milliseconds = 2000,
		maximum_retries = 1,
	),
)

result = await graph_client.identity.custom_authentication_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/customAuthenticationExtensions/$entity",
    "@odata.type": "#microsoft.graph.onAttributeCollectionSubmitCustomExtension",
    "id": "66867d1f-7824-4f38-aad1-75da1ad09ee2",
    "displayName": "attributeCollectionSubmitName",
    "description": "example description",
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://contoso.com/fb96de85-2abe-4b02-b45f-64ba122c509e"
    },
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://contoso.com"
    },
    "clientConfiguration": {
        "timeoutInMilliseconds": 2000,
        "maximumRetries": 1
    }
}
```

### Example 4: Create an onOtpSendCustomExtension object

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onOtpSendCustomExtension",
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e"
  },
  "clientConfiguration": {
    "timeoutInMilliseconds": 2000,
    "maximumRetries": 1
  },
  "description": "Use an external Email provider to send OTP Codes.",
  "displayName": "onEmailOtpSendCustomExtension",
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.httpRequestEndpoint",
    "targetUrl": "https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo"
  },
  "behaviorOnError": {
    "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnOtpSendCustomExtension
{
	OdataType = "#microsoft.graph.onOtpSendCustomExtension",
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e",
	},
	ClientConfiguration = new CustomExtensionClientConfiguration
	{
		TimeoutInMilliseconds = 2000,
		MaximumRetries = 1,
	},
	Description = "Use an external Email provider to send OTP Codes.",
	DisplayName = "onEmailOtpSendCustomExtension",
	EndpointConfiguration = new HttpRequestEndpoint
	{
		OdataType = "#microsoft.graph.httpRequestEndpoint",
		TargetUrl = "https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo",
	},
	BehaviorOnError = new CustomExtensionBehaviorOnError
	{
		OdataType = "microsoft.graph.customExtensionBehaviorOnError",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.CustomAuthenticationExtensions.PostAsync(requestBody);
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
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
timeoutInMilliseconds := int32(2000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
requestBody.SetClientConfiguration(clientConfiguration)
description := "Use an external Email provider to send OTP Codes."
requestBody.SetDescription(&description) 
displayName := "onEmailOtpSendCustomExtension"
requestBody.SetDisplayName(&displayName) 
endpointConfiguration := graphmodels.NewHttpRequestEndpoint()
targetUrl := "https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo"
endpointConfiguration.SetTargetUrl(&targetUrl) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
behaviorOnError := graphmodels.NewCustomExtensionBehaviorOnError()
requestBody.SetBehaviorOnError(behaviorOnError)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAuthenticationExtensions, err := graphClient.Identity().CustomAuthenticationExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnOtpSendCustomExtension customAuthenticationExtension = new OnOtpSendCustomExtension();
customAuthenticationExtension.setOdataType("#microsoft.graph.onOtpSendCustomExtension");
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e");
customAuthenticationExtension.setAuthenticationConfiguration(authenticationConfiguration);
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setTimeoutInMilliseconds(2000);
clientConfiguration.setMaximumRetries(1);
customAuthenticationExtension.setClientConfiguration(clientConfiguration);
customAuthenticationExtension.setDescription("Use an external Email provider to send OTP Codes.");
customAuthenticationExtension.setDisplayName("onEmailOtpSendCustomExtension");
HttpRequestEndpoint endpointConfiguration = new HttpRequestEndpoint();
endpointConfiguration.setOdataType("#microsoft.graph.httpRequestEndpoint");
endpointConfiguration.setTargetUrl("https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo");
customAuthenticationExtension.setEndpointConfiguration(endpointConfiguration);
CustomExtensionBehaviorOnError behaviorOnError = new CustomExtensionBehaviorOnError();
behaviorOnError.setOdataType("microsoft.graph.customExtensionBehaviorOnError");
customAuthenticationExtension.setBehaviorOnError(behaviorOnError);
CustomAuthenticationExtension result = graphClient.identity().customAuthenticationExtensions().post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAuthenticationExtension = {
  '@odata.type': '#microsoft.graph.onOtpSendCustomExtension',
  authenticationConfiguration: {
    '@odata.type': '#microsoft.graph.azureAdTokenAuthentication',
    resourceId: 'api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e'
  },
  clientConfiguration: {
    timeoutInMilliseconds: 2000,
    maximumRetries: 1
  },
  description: 'Use an external Email provider to send OTP Codes.',
  displayName: 'onEmailOtpSendCustomExtension',
  endpointConfiguration: {
    '@odata.type': '#microsoft.graph.httpRequestEndpoint',
    targetUrl: 'https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo'
  },
  behaviorOnError: {
    '@odata.type': 'microsoft.graph.customExtensionBehaviorOnError'
  }
};

await client.api('/identity/customAuthenticationExtensions')
	.post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnOtpSendCustomExtension;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;
use Microsoft\Graph\Generated\Models\HttpRequestEndpoint;
use Microsoft\Graph\Generated\Models\CustomExtensionBehaviorOnError;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnOtpSendCustomExtension();
$requestBody->setOdataType('#microsoft.graph.onOtpSendCustomExtension');
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$clientConfiguration = new CustomExtensionClientConfiguration();
$clientConfiguration->setTimeoutInMilliseconds(2000);
$clientConfiguration->setMaximumRetries(1);
$requestBody->setClientConfiguration($clientConfiguration);
$requestBody->setDescription('Use an external Email provider to send OTP Codes.');
$requestBody->setDisplayName('onEmailOtpSendCustomExtension');
$endpointConfiguration = new HttpRequestEndpoint();
$endpointConfiguration->setOdataType('#microsoft.graph.httpRequestEndpoint');
$endpointConfiguration->setTargetUrl('https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$behaviorOnError = new CustomExtensionBehaviorOnError();
$behaviorOnError->setOdataType('microsoft.graph.customExtensionBehaviorOnError');
$requestBody->setBehaviorOnError($behaviorOnError);

$result = $graphServiceClient->identity()->customAuthenticationExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onOtpSendCustomExtension"
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e"
	}
	clientConfiguration = @{
		timeoutInMilliseconds = 2000
		maximumRetries = 1
	}
	description = "Use an external Email provider to send OTP Codes."
	displayName = "onEmailOtpSendCustomExtension"
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.httpRequestEndpoint"
		targetUrl = "https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo"
	}
	behaviorOnError = @{
		"@odata.type" = "microsoft.graph.customExtensionBehaviorOnError"
	}
}

New-MgIdentityCustomAuthenticationExtension -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_otp_send_custom_extension import OnOtpSendCustomExtension
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
from msgraph.generated.models.http_request_endpoint import HttpRequestEndpoint
from msgraph.generated.models.custom_extension_behavior_on_error import CustomExtensionBehaviorOnError
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnOtpSendCustomExtension(
	odata_type = "#microsoft.graph.onOtpSendCustomExtension",
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e",
	),
	client_configuration = CustomExtensionClientConfiguration(
		timeout_in_milliseconds = 2000,
		maximum_retries = 1,
	),
	description = "Use an external Email provider to send OTP Codes.",
	display_name = "onEmailOtpSendCustomExtension",
	endpoint_configuration = HttpRequestEndpoint(
		odata_type = "#microsoft.graph.httpRequestEndpoint",
		target_url = "https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo",
	),
	behavior_on_error = CustomExtensionBehaviorOnError(
		odata_type = "microsoft.graph.customExtensionBehaviorOnError",
	),
)

result = await graph_client.identity.custom_authentication_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onOtpSendCustomExtension",
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "api://onotpsendcustomextension.b2c.expert/fb96de85-2abe-4b02-b45f-64ba122c509e"
  },
  "clientConfiguration": {
    "timeoutInMilliseconds": 2000,
    "maximumRetries": 1
  },
  "description": "Use an external Email provider to send OTP Codes.",
  "displayName": "onEmailOtpSendCustomExtension",
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.httpRequestEndpoint",
    "targetUrl": "https://onotpsendcustomextension.b2c.expert/api/OnOTPCodeSendToTeamsDemo"
  },
  "behaviorOnError": {
    "@odata.type": "microsoft.graph.customExtensionBehaviorOnError"
  }
}
```

### Example 5: Create an onPasswordSubmitCustomExtension object

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
POST https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onPasswordSubmitCustomExtension",
  "displayName": "Legacy password validator",
  "description": "Validates passwords against a legacy authentication system for JIT migration",
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.httpRequestEndpoint",
    "targetUrl": "https://api.contoso.com/passwordvalidation"
  },
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "api://api.contoso.com/passwordvalidation"
  },
  "clientConfiguration": {
    "timeoutInMilliseconds": 2000,
    "maximumRetries": 1
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnPasswordSubmitCustomExtension
{
	OdataType = "#microsoft.graph.onPasswordSubmitCustomExtension",
	DisplayName = "Legacy password validator",
	Description = "Validates passwords against a legacy authentication system for JIT migration",
	EndpointConfiguration = new HttpRequestEndpoint
	{
		OdataType = "#microsoft.graph.httpRequestEndpoint",
		TargetUrl = "https://api.contoso.com/passwordvalidation",
	},
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "api://api.contoso.com/passwordvalidation",
	},
	ClientConfiguration = new CustomExtensionClientConfiguration
	{
		TimeoutInMilliseconds = 2000,
		MaximumRetries = 1,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.CustomAuthenticationExtensions.PostAsync(requestBody);
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
displayName := "Legacy password validator"
requestBody.SetDisplayName(&displayName) 
description := "Validates passwords against a legacy authentication system for JIT migration"
requestBody.SetDescription(&description) 
endpointConfiguration := graphmodels.NewHttpRequestEndpoint()
targetUrl := "https://api.contoso.com/passwordvalidation"
endpointConfiguration.SetTargetUrl(&targetUrl) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "api://api.contoso.com/passwordvalidation"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
timeoutInMilliseconds := int32(2000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
requestBody.SetClientConfiguration(clientConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAuthenticationExtensions, err := graphClient.Identity().CustomAuthenticationExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnPasswordSubmitCustomExtension customAuthenticationExtension = new OnPasswordSubmitCustomExtension();
customAuthenticationExtension.setOdataType("#microsoft.graph.onPasswordSubmitCustomExtension");
customAuthenticationExtension.setDisplayName("Legacy password validator");
customAuthenticationExtension.setDescription("Validates passwords against a legacy authentication system for JIT migration");
HttpRequestEndpoint endpointConfiguration = new HttpRequestEndpoint();
endpointConfiguration.setOdataType("#microsoft.graph.httpRequestEndpoint");
endpointConfiguration.setTargetUrl("https://api.contoso.com/passwordvalidation");
customAuthenticationExtension.setEndpointConfiguration(endpointConfiguration);
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("api://api.contoso.com/passwordvalidation");
customAuthenticationExtension.setAuthenticationConfiguration(authenticationConfiguration);
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setTimeoutInMilliseconds(2000);
clientConfiguration.setMaximumRetries(1);
customAuthenticationExtension.setClientConfiguration(clientConfiguration);
CustomAuthenticationExtension result = graphClient.identity().customAuthenticationExtensions().post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAuthenticationExtension = {
  '@odata.type': '#microsoft.graph.onPasswordSubmitCustomExtension',
  displayName: 'Legacy password validator',
  description: 'Validates passwords against a legacy authentication system for JIT migration',
  endpointConfiguration: {
    '@odata.type': '#microsoft.graph.httpRequestEndpoint',
    targetUrl: 'https://api.contoso.com/passwordvalidation'
  },
  authenticationConfiguration: {
    '@odata.type': '#microsoft.graph.azureAdTokenAuthentication',
    resourceId: 'api://api.contoso.com/passwordvalidation'
  },
  clientConfiguration: {
    timeoutInMilliseconds: 2000,
    maximumRetries: 1
  }
};

await client.api('/identity/customAuthenticationExtensions')
	.post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnPasswordSubmitCustomExtension;
use Microsoft\Graph\Generated\Models\HttpRequestEndpoint;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnPasswordSubmitCustomExtension();
$requestBody->setOdataType('#microsoft.graph.onPasswordSubmitCustomExtension');
$requestBody->setDisplayName('Legacy password validator');
$requestBody->setDescription('Validates passwords against a legacy authentication system for JIT migration');
$endpointConfiguration = new HttpRequestEndpoint();
$endpointConfiguration->setOdataType('#microsoft.graph.httpRequestEndpoint');
$endpointConfiguration->setTargetUrl('https://api.contoso.com/passwordvalidation');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('api://api.contoso.com/passwordvalidation');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$clientConfiguration = new CustomExtensionClientConfiguration();
$clientConfiguration->setTimeoutInMilliseconds(2000);
$clientConfiguration->setMaximumRetries(1);
$requestBody->setClientConfiguration($clientConfiguration);

$result = $graphServiceClient->identity()->customAuthenticationExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onPasswordSubmitCustomExtension"
	displayName = "Legacy password validator"
	description = "Validates passwords against a legacy authentication system for JIT migration"
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.httpRequestEndpoint"
		targetUrl = "https://api.contoso.com/passwordvalidation"
	}
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "api://api.contoso.com/passwordvalidation"
	}
	clientConfiguration = @{
		timeoutInMilliseconds = 2000
		maximumRetries = 1
	}
}

New-MgIdentityCustomAuthenticationExtension -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_password_submit_custom_extension import OnPasswordSubmitCustomExtension
from msgraph.generated.models.http_request_endpoint import HttpRequestEndpoint
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnPasswordSubmitCustomExtension(
	odata_type = "#microsoft.graph.onPasswordSubmitCustomExtension",
	display_name = "Legacy password validator",
	description = "Validates passwords against a legacy authentication system for JIT migration",
	endpoint_configuration = HttpRequestEndpoint(
		odata_type = "#microsoft.graph.httpRequestEndpoint",
		target_url = "https://api.contoso.com/passwordvalidation",
	),
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "api://api.contoso.com/passwordvalidation",
	),
	client_configuration = CustomExtensionClientConfiguration(
		timeout_in_milliseconds = 2000,
		maximum_retries = 1,
	),
)

result = await graph_client.identity.custom_authentication_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/customAuthenticationExtensions/$entity",
  "@odata.type": "#microsoft.graph.onPasswordSubmitCustomExtension",
  "id": "6fc5012e-7665-43d6-9708-4370863f4e6e",
  "displayName": "Legacy password validator",
  "description": "Validates passwords against a legacy authentication system for JIT migration",
  "behaviorOnError": null,
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "api://api.contoso.com/passwordvalidation"
  },
  "clientConfiguration": {
    "timeoutInMilliseconds": 2000,
    "maximumRetries": 1
  },
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.httpRequestEndpoint",
    "targetUrl": "https://api.contoso.com/passwordvalidation"
  }
}
```

### Example 6: Create an onVerifiedIdClaimValidationCustomExtension object

#### Request

The following example shows a request.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/identity/customAuthenticationExtensions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationCustomExtension",
  "displayName": "Verified ID Claim Validation",
  "description": "Validate claims from a Verified ID presentation",
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.httpRequestEndpoint",
    "targetUrl": "https://contoso.azurewebsites.net/api/verifiedIdClaimValidation"
  },
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
    "resourceId": "api://contoso.azurewebsites.net/verifiedIdClaimValidation"
  },
  "clientConfiguration": {
    "timeoutInMilliseconds": 2000,
    "maximumRetries": 1
  },
  "behaviorOnError": {
    "@odata.type": "#microsoft.graph.customExtensionBehaviorOnError"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnVerifiedIdClaimValidationCustomExtension
{
	OdataType = "#microsoft.graph.onVerifiedIdClaimValidationCustomExtension",
	DisplayName = "Verified ID Claim Validation",
	Description = "Validate claims from a Verified ID presentation",
	EndpointConfiguration = new HttpRequestEndpoint
	{
		OdataType = "#microsoft.graph.httpRequestEndpoint",
		TargetUrl = "https://contoso.azurewebsites.net/api/verifiedIdClaimValidation",
	},
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "api://contoso.azurewebsites.net/verifiedIdClaimValidation",
	},
	ClientConfiguration = new CustomExtensionClientConfiguration
	{
		TimeoutInMilliseconds = 2000,
		MaximumRetries = 1,
	},
	BehaviorOnError = new CustomExtensionBehaviorOnError
	{
		OdataType = "#microsoft.graph.customExtensionBehaviorOnError",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Identity.CustomAuthenticationExtensions.PostAsync(requestBody);
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
displayName := "Verified ID Claim Validation"
requestBody.SetDisplayName(&displayName) 
description := "Validate claims from a Verified ID presentation"
requestBody.SetDescription(&description) 
endpointConfiguration := graphmodels.NewHttpRequestEndpoint()
targetUrl := "https://contoso.azurewebsites.net/api/verifiedIdClaimValidation"
endpointConfiguration.SetTargetUrl(&targetUrl) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "api://contoso.azurewebsites.net/verifiedIdClaimValidation"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
timeoutInMilliseconds := int32(2000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
requestBody.SetClientConfiguration(clientConfiguration)
behaviorOnError := graphmodels.NewCustomExtensionBehaviorOnError()
requestBody.SetBehaviorOnError(behaviorOnError)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAuthenticationExtensions, err := graphClient.Identity().CustomAuthenticationExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnVerifiedIdClaimValidationCustomExtension customAuthenticationExtension = new OnVerifiedIdClaimValidationCustomExtension();
customAuthenticationExtension.setOdataType("#microsoft.graph.onVerifiedIdClaimValidationCustomExtension");
customAuthenticationExtension.setDisplayName("Verified ID Claim Validation");
customAuthenticationExtension.setDescription("Validate claims from a Verified ID presentation");
HttpRequestEndpoint endpointConfiguration = new HttpRequestEndpoint();
endpointConfiguration.setOdataType("#microsoft.graph.httpRequestEndpoint");
endpointConfiguration.setTargetUrl("https://contoso.azurewebsites.net/api/verifiedIdClaimValidation");
customAuthenticationExtension.setEndpointConfiguration(endpointConfiguration);
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("api://contoso.azurewebsites.net/verifiedIdClaimValidation");
customAuthenticationExtension.setAuthenticationConfiguration(authenticationConfiguration);
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setTimeoutInMilliseconds(2000);
clientConfiguration.setMaximumRetries(1);
customAuthenticationExtension.setClientConfiguration(clientConfiguration);
CustomExtensionBehaviorOnError behaviorOnError = new CustomExtensionBehaviorOnError();
behaviorOnError.setOdataType("#microsoft.graph.customExtensionBehaviorOnError");
customAuthenticationExtension.setBehaviorOnError(behaviorOnError);
CustomAuthenticationExtension result = graphClient.identity().customAuthenticationExtensions().post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAuthenticationExtension = {
  '@odata.type': '#microsoft.graph.onVerifiedIdClaimValidationCustomExtension',
  displayName: 'Verified ID Claim Validation',
  description: 'Validate claims from a Verified ID presentation',
  endpointConfiguration: {
    '@odata.type': '#microsoft.graph.httpRequestEndpoint',
    targetUrl: 'https://contoso.azurewebsites.net/api/verifiedIdClaimValidation'
  },
  authenticationConfiguration: {
    '@odata.type': '#microsoft.graph.azureAdTokenAuthentication',
    resourceId: 'api://contoso.azurewebsites.net/verifiedIdClaimValidation'
  },
  clientConfiguration: {
    timeoutInMilliseconds: 2000,
    maximumRetries: 1
  },
  behaviorOnError: {
    '@odata.type': '#microsoft.graph.customExtensionBehaviorOnError'
  }
};

await client.api('/identity/customAuthenticationExtensions')
	.post(customAuthenticationExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnVerifiedIdClaimValidationCustomExtension;
use Microsoft\Graph\Generated\Models\HttpRequestEndpoint;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;
use Microsoft\Graph\Generated\Models\CustomExtensionBehaviorOnError;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnVerifiedIdClaimValidationCustomExtension();
$requestBody->setOdataType('#microsoft.graph.onVerifiedIdClaimValidationCustomExtension');
$requestBody->setDisplayName('Verified ID Claim Validation');
$requestBody->setDescription('Validate claims from a Verified ID presentation');
$endpointConfiguration = new HttpRequestEndpoint();
$endpointConfiguration->setOdataType('#microsoft.graph.httpRequestEndpoint');
$endpointConfiguration->setTargetUrl('https://contoso.azurewebsites.net/api/verifiedIdClaimValidation');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('api://contoso.azurewebsites.net/verifiedIdClaimValidation');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$clientConfiguration = new CustomExtensionClientConfiguration();
$clientConfiguration->setTimeoutInMilliseconds(2000);
$clientConfiguration->setMaximumRetries(1);
$requestBody->setClientConfiguration($clientConfiguration);
$behaviorOnError = new CustomExtensionBehaviorOnError();
$behaviorOnError->setOdataType('#microsoft.graph.customExtensionBehaviorOnError');
$requestBody->setBehaviorOnError($behaviorOnError);

$result = $graphServiceClient->identity()->customAuthenticationExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.SignIns

$params = @{
	"@odata.type" = "#microsoft.graph.onVerifiedIdClaimValidationCustomExtension"
	displayName = "Verified ID Claim Validation"
	description = "Validate claims from a Verified ID presentation"
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.httpRequestEndpoint"
		targetUrl = "https://contoso.azurewebsites.net/api/verifiedIdClaimValidation"
	}
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "api://contoso.azurewebsites.net/verifiedIdClaimValidation"
	}
	clientConfiguration = @{
		timeoutInMilliseconds = 2000
		maximumRetries = 1
	}
	behaviorOnError = @{
		"@odata.type" = "#microsoft.graph.customExtensionBehaviorOnError"
	}
}

New-MgIdentityCustomAuthenticationExtension -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.on_verified_id_claim_validation_custom_extension import OnVerifiedIdClaimValidationCustomExtension
from msgraph.generated.models.http_request_endpoint import HttpRequestEndpoint
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
from msgraph.generated.models.custom_extension_behavior_on_error import CustomExtensionBehaviorOnError
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnVerifiedIdClaimValidationCustomExtension(
	odata_type = "#microsoft.graph.onVerifiedIdClaimValidationCustomExtension",
	display_name = "Verified ID Claim Validation",
	description = "Validate claims from a Verified ID presentation",
	endpoint_configuration = HttpRequestEndpoint(
		odata_type = "#microsoft.graph.httpRequestEndpoint",
		target_url = "https://contoso.azurewebsites.net/api/verifiedIdClaimValidation",
	),
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "api://contoso.azurewebsites.net/verifiedIdClaimValidation",
	),
	client_configuration = CustomExtensionClientConfiguration(
		timeout_in_milliseconds = 2000,
		maximum_retries = 1,
	),
	behavior_on_error = CustomExtensionBehaviorOnError(
		odata_type = "#microsoft.graph.customExtensionBehaviorOnError",
	),
)

result = await graph_client.identity.custom_authentication_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identity/customAuthenticationExtensions/$entity",
    "@odata.type": "#microsoft.graph.onVerifiedIdClaimValidationCustomExtension",
    "id": "6a0a3429-be77-0aed-951e-1c8aed62bf8a",
    "displayName": "Verified ID Claim Validation",
    "description": "Validate claims from a Verified ID presentation",
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "api://contoso.azurewebsites.net/verifiedIdClaimValidation"
    },
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.httpRequestEndpoint",
        "targetUrl": "https://contoso.azurewebsites.net/api/verifiedIdClaimValidation"
    },
    "clientConfiguration": {
        "timeoutInMilliseconds": 2000,
        "maximumRetries": 1
    },
    "behaviorOnError": {
        "@odata.type": "#microsoft.graph.customExtensionBehaviorOnError"
    }
}
```
