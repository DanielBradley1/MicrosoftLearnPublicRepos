<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-post-customaccesspackageworkflowextensions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create customAccessPackageWorkflowExtensions

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) object and add it to an existing [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EntitlementManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Tip

For delegated access using work or school accounts, the signed-in user must be assigned an administrator role with supported role permissions through one of the following options:

- One of the following [Azure role](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) assignments are required either on the Logic App itself, or on a higher scope such as the resource group, subscription or management group:

  - Logic App contributor
  - Contributor
  - Owner

And one of the following:

- A [role in the Entitlement Management system](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) where the least privileged role is *Catalog owner*. **This is the least privileged option**.
- More privileged [Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation:

  - Identity Governance Administrator

In app-only scenarios, the calling app can be assigned one of the preceding supported roles instead of the `EntitlementManagement.ReadWrite.All` application permission. The *Catalog owner* role is less privileged than the `EntitlementManagement.Read.All` application permission.. If it's a delegated call without the `URL` property in [logicAppTriggerEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/logicapptriggerendpointconfiguration), the caller also needs to be authorized on the Logic App.

For more information, see [Delegation and roles in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate) and [how to delegate access governance to access package managers in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-delegate-managers).

## HTTP request

```http
POST /identityGovernance/entitlementManagement/accessPackageCatalogs/{catalogId}/customAccessPackageWorkflowExtensions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) object.

You can specify the following properties when creating a **customAccessPackageWorkflowExtension**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for the customAccessPackageWorkflowExtension object. |
| displayName | String | Display name for the customAccessPackageWorkflowExtension. |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-beta) | The type and details for configuring the endpoint to call the logic app's workflow. |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-beta) | Configuration for securing the API call to the logic app. For example, using OAuth client credentials flow. |

## Response

If successful, this method returns a `201 Created` response code and a [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) object in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/identityGovernance/entitlementManagement/accessPackageCatalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customAccessPackageWorkflowExtensions
Content-Type: application/json

{ 
    "displayName": "test_action_0124", 
    "description": "this is for graph testing only", 
    "endpointConfiguration": { 
        "@odata.type": "#microsoft.graph.logicAppTriggerEndpointConfiguration", 
        "subscriptionId": "38ab2ccc-3747-4567-b36b-9478f5602f0d", 
        "resourceGroupName": "EMLogicApp", 
        "logicAppWorkflowName": "customextension_test" 
    }, 
    "authenticationConfiguration": { 
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication", 
        "resourceId": "f604bd15-f785-4309-ad7c-6fad18ddb6cb" 
    } 
} 
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CustomAccessPackageWorkflowExtension
{
	DisplayName = "test_action_0124",
	Description = "this is for graph testing only",
	EndpointConfiguration = new LogicAppTriggerEndpointConfiguration
	{
		OdataType = "#microsoft.graph.logicAppTriggerEndpointConfiguration",
		SubscriptionId = "38ab2ccc-3747-4567-b36b-9478f5602f0d",
		ResourceGroupName = "EMLogicApp",
		LogicAppWorkflowName = "customextension_test",
	},
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "f604bd15-f785-4309-ad7c-6fad18ddb6cb",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.AccessPackageCatalogs["{accessPackageCatalog-id}"].CustomAccessPackageWorkflowExtensions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCustomAccessPackageWorkflowExtension()
displayName := "test_action_0124"
requestBody.SetDisplayName(&displayName) 
description := "this is for graph testing only"
requestBody.SetDescription(&description) 
endpointConfiguration := graphmodels.NewLogicAppTriggerEndpointConfiguration()
subscriptionId := "38ab2ccc-3747-4567-b36b-9478f5602f0d"
endpointConfiguration.SetSubscriptionId(&subscriptionId) 
resourceGroupName := "EMLogicApp"
endpointConfiguration.SetResourceGroupName(&resourceGroupName) 
logicAppWorkflowName := "customextension_test"
endpointConfiguration.SetLogicAppWorkflowName(&logicAppWorkflowName) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "f604bd15-f785-4309-ad7c-6fad18ddb6cb"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customAccessPackageWorkflowExtensions, err := graphClient.IdentityGovernance().EntitlementManagement().AccessPackageCatalogs().ByAccessPackageCatalogId("accessPackageCatalog-id").CustomAccessPackageWorkflowExtensions().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomAccessPackageWorkflowExtension customAccessPackageWorkflowExtension = new CustomAccessPackageWorkflowExtension();
customAccessPackageWorkflowExtension.setDisplayName("test_action_0124");
customAccessPackageWorkflowExtension.setDescription("this is for graph testing only");
LogicAppTriggerEndpointConfiguration endpointConfiguration = new LogicAppTriggerEndpointConfiguration();
endpointConfiguration.setOdataType("#microsoft.graph.logicAppTriggerEndpointConfiguration");
endpointConfiguration.setSubscriptionId("38ab2ccc-3747-4567-b36b-9478f5602f0d");
endpointConfiguration.setResourceGroupName("EMLogicApp");
endpointConfiguration.setLogicAppWorkflowName("customextension_test");
customAccessPackageWorkflowExtension.setEndpointConfiguration(endpointConfiguration);
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("f604bd15-f785-4309-ad7c-6fad18ddb6cb");
customAccessPackageWorkflowExtension.setAuthenticationConfiguration(authenticationConfiguration);
CustomAccessPackageWorkflowExtension result = graphClient.identityGovernance().entitlementManagement().accessPackageCatalogs().byAccessPackageCatalogId("{accessPackageCatalog-id}").customAccessPackageWorkflowExtensions().post(customAccessPackageWorkflowExtension);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customAccessPackageWorkflowExtension = {
    displayName: 'test_action_0124', 
    description: 'this is for graph testing only', 
    endpointConfiguration: { 
        '@odata.type': '#microsoft.graph.logicAppTriggerEndpointConfiguration', 
        subscriptionId: '38ab2ccc-3747-4567-b36b-9478f5602f0d', 
        resourceGroupName: 'EMLogicApp', 
        logicAppWorkflowName: 'customextension_test' 
    }, 
    authenticationConfiguration: { 
        '@odata.type': '#microsoft.graph.azureAdTokenAuthentication', 
        resourceId: 'f604bd15-f785-4309-ad7c-6fad18ddb6cb' 
    } 
};

await client.api('/identityGovernance/entitlementManagement/accessPackageCatalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customAccessPackageWorkflowExtensions')
	.version('beta')
	.post(customAccessPackageWorkflowExtension);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CustomAccessPackageWorkflowExtension;
use Microsoft\Graph\Beta\Generated\Models\LogicAppTriggerEndpointConfiguration;
use Microsoft\Graph\Beta\Generated\Models\AzureAdTokenAuthentication;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomAccessPackageWorkflowExtension();
$requestBody->setDisplayName('test_action_0124');
$requestBody->setDescription('this is for graph testing only');
$endpointConfiguration = new LogicAppTriggerEndpointConfiguration();
$endpointConfiguration->setOdataType('#microsoft.graph.logicAppTriggerEndpointConfiguration');
$endpointConfiguration->setSubscriptionId('38ab2ccc-3747-4567-b36b-9478f5602f0d');
$endpointConfiguration->setResourceGroupName('EMLogicApp');
$endpointConfiguration->setLogicAppWorkflowName('customextension_test');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('f604bd15-f785-4309-ad7c-6fad18ddb6cb');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->accessPackageCatalogs()->byAccessPackageCatalogId('accessPackageCatalog-id')->customAccessPackageWorkflowExtensions()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	displayName = "test_action_0124"
	description = "this is for graph testing only"
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.logicAppTriggerEndpointConfiguration"
		subscriptionId = "38ab2ccc-3747-4567-b36b-9478f5602f0d"
		resourceGroupName = "EMLogicApp"
		logicAppWorkflowName = "customextension_test"
	}
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "f604bd15-f785-4309-ad7c-6fad18ddb6cb"
	}
}

New-MgBetaEntitlementManagementAccessPackageCatalogCustomAccessPackageWorkflowExtension -AccessPackageCatalogId $accessPackageCatalogId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.custom_access_package_workflow_extension import CustomAccessPackageWorkflowExtension
from msgraph_beta.generated.models.logic_app_trigger_endpoint_configuration import LogicAppTriggerEndpointConfiguration
from msgraph_beta.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomAccessPackageWorkflowExtension(
	display_name = "test_action_0124",
	description = "this is for graph testing only",
	endpoint_configuration = LogicAppTriggerEndpointConfiguration(
		odata_type = "#microsoft.graph.logicAppTriggerEndpointConfiguration",
		subscription_id = "38ab2ccc-3747-4567-b36b-9478f5602f0d",
		resource_group_name = "EMLogicApp",
		logic_app_workflow_name = "customextension_test",
	),
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "f604bd15-f785-4309-ad7c-6fad18ddb6cb",
	),
)

result = await graph_client.identity_governance.entitlement_management.access_package_catalogs.by_access_package_catalog_id('accessPackageCatalog-id').custom_access_package_workflow_extensions.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{ 
    "id": "98ffaec5-ae8e-4902-a434-5ffc5d3d3cd0", 
    "displayName": "test_action_0124",
    "description": "this is for graph testing only", 
    "createdDateTime": "2022-01-24T21:48:57.1483656Z", 
    "lastModifiedDateTime": "2022-01-24T21:48:57.1483656Z", 
    "clientConfiguration": null, 
    "endpointConfiguration": { 
        "@odata.type": "#microsoft.graph.logicAppTriggerEndpointConfiguration", 
        "subscriptionId": "38ab2ccc-3747-4567-b36b-9478f5602f0d", 
        "resourceGroupName": "EMLogicApp", 
        "logicAppWorkflowName": "customextension_test" 
    },
    "authenticationConfiguration": { 
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication", 
        "resourceId": "f604bd15-f785-4309-ad7c-6fad18ddb6cb" 
    } 
} 
```
