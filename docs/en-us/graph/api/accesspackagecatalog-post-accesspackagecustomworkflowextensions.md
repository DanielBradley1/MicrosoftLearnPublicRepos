<!-- Source: https://learn.microsoft.com/en-us/graph/api/accesspackagecatalog-post-accesspackagecustomworkflowextensions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create accessPackageCustomWorkflowExtension

Namespace: microsoft.graph

Create a new [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0) or [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0) object in the **accessPackageCustomWorkflowExtensions** relationship of an [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0). You must explicitly provide an `@odata.type` property that indicates whether the object is an **accessPackageAssignmentRequestWorkflowExtension** or an **accessPackageAssignmentWorkflowExtension**.

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
| Application | EntitlementManagement.ReadWrite.All | Not available. |

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
POST /identityGovernance/entitlementManagement/catalogs/{catalogId}/customWorkflowExtensions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0) or [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0) object.

You can specify the following properties when creating a **accessPackageCustomWorkflowExtension**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description for the customAccessPackageWorkflowExtension object. |
| displayName | String | Required. Display name for the customAccessPackageWorkflowExtension. |
| endpointConfiguration | [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | Required. The type and details for configuring the endpoint to call the logic app's workflow. |
| authenticationConfiguration | [customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | Required. Configuration for securing the API call to the logic app. For example, using OAuth client credentials flow. |
| callbackConfiguration | [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0) | The callback configuration for a custom extension. This is supported for `accessPackageAssignmentRequestWorkflowExtension`. |

You must also supply an **@odata.type** property with a value of the specific access package workflow extension type. For example, `"@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension"`.

## Response

If successful, this method returns a `201 Created` response code and a [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0) or [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a custom extension for use with an access package assignment request

The following is an example of a access package assignment request custom workflow extension.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customWorkflowExtensions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
  "displayName": "test_action_0124_email",
  "description": "this is for graph testing only",
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.logicAppTriggerEndpointConfiguration",
    "subscriptionId": "38ab2ccc-3747-4567-b36b-9478f5602f0d",
    "resourceGroupName": "test",
    "logicAppWorkflowName": "elm-extension-email"
  },
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdPopTokenAuthentication"
  },
  "callbackConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionCallbackConfiguration",
    "durationBeforeTimeout": "PT1H"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessPackageAssignmentRequestWorkflowExtension
{
	OdataType = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
	DisplayName = "test_action_0124_email",
	Description = "this is for graph testing only",
	EndpointConfiguration = new LogicAppTriggerEndpointConfiguration
	{
		OdataType = "#microsoft.graph.logicAppTriggerEndpointConfiguration",
		SubscriptionId = "38ab2ccc-3747-4567-b36b-9478f5602f0d",
		ResourceGroupName = "test",
		LogicAppWorkflowName = "elm-extension-email",
	},
	AuthenticationConfiguration = new AzureAdPopTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdPopTokenAuthentication",
	},
	CallbackConfiguration = new CustomExtensionCallbackConfiguration
	{
		OdataType = "microsoft.graph.customExtensionCallbackConfiguration",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"durationBeforeTimeout" , "PT1H"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs["{accessPackageCatalog-id}"].CustomWorkflowExtensions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCustomCalloutExtension()
displayName := "test_action_0124_email"
requestBody.SetDisplayName(&displayName) 
description := "this is for graph testing only"
requestBody.SetDescription(&description) 
endpointConfiguration := graphmodels.NewLogicAppTriggerEndpointConfiguration()
subscriptionId := "38ab2ccc-3747-4567-b36b-9478f5602f0d"
endpointConfiguration.SetSubscriptionId(&subscriptionId) 
resourceGroupName := "test"
endpointConfiguration.SetResourceGroupName(&resourceGroupName) 
logicAppWorkflowName := "elm-extension-email"
endpointConfiguration.SetLogicAppWorkflowName(&logicAppWorkflowName) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
authenticationConfiguration := graphmodels.NewAzureAdPopTokenAuthentication()
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)
callbackConfiguration := graphmodels.NewCustomExtensionCallbackConfiguration()
additionalData := map[string]interface{}{
	"durationBeforeTimeout" : "PT1H", 
}
callbackConfiguration.SetAdditionalData(additionalData)
requestBody.SetCallbackConfiguration(callbackConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customWorkflowExtensions, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().ByAccessPackageCatalogId("accessPackageCatalog-id").CustomWorkflowExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessPackageAssignmentRequestWorkflowExtension customCalloutExtension = new AccessPackageAssignmentRequestWorkflowExtension();
customCalloutExtension.setOdataType("#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension");
customCalloutExtension.setDisplayName("test_action_0124_email");
customCalloutExtension.setDescription("this is for graph testing only");
LogicAppTriggerEndpointConfiguration endpointConfiguration = new LogicAppTriggerEndpointConfiguration();
endpointConfiguration.setOdataType("#microsoft.graph.logicAppTriggerEndpointConfiguration");
endpointConfiguration.setSubscriptionId("38ab2ccc-3747-4567-b36b-9478f5602f0d");
endpointConfiguration.setResourceGroupName("test");
endpointConfiguration.setLogicAppWorkflowName("elm-extension-email");
customCalloutExtension.setEndpointConfiguration(endpointConfiguration);
AzureAdPopTokenAuthentication authenticationConfiguration = new AzureAdPopTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdPopTokenAuthentication");
customCalloutExtension.setAuthenticationConfiguration(authenticationConfiguration);
CustomExtensionCallbackConfiguration callbackConfiguration = new CustomExtensionCallbackConfiguration();
callbackConfiguration.setOdataType("microsoft.graph.customExtensionCallbackConfiguration");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("durationBeforeTimeout", "PT1H");
callbackConfiguration.setAdditionalData(additionalData);
customCalloutExtension.setCallbackConfiguration(callbackConfiguration);
CustomCalloutExtension result = graphClient.identityGovernance().entitlementManagement().catalogs().byAccessPackageCatalogId("{accessPackageCatalog-id}").customWorkflowExtensions().post(customCalloutExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customCalloutExtension = {
  '@odata.type': '#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension',
  displayName: 'test_action_0124_email',
  description: 'this is for graph testing only',
  endpointConfiguration: {
    '@odata.type': '#microsoft.graph.logicAppTriggerEndpointConfiguration',
    subscriptionId: '38ab2ccc-3747-4567-b36b-9478f5602f0d',
    resourceGroupName: 'test',
    logicAppWorkflowName: 'elm-extension-email'
  },
  authenticationConfiguration: {
    '@odata.type': '#microsoft.graph.azureAdPopTokenAuthentication'
  },
  callbackConfiguration: {
    '@odata.type': 'microsoft.graph.customExtensionCallbackConfiguration',
    durationBeforeTimeout: 'PT1H'
  }
};

await client.api('/identityGovernance/entitlementManagement/catalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customWorkflowExtensions')
	.post(customCalloutExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentRequestWorkflowExtension;
use Microsoft\Graph\Generated\Models\LogicAppTriggerEndpointConfiguration;
use Microsoft\Graph\Generated\Models\AzureAdPopTokenAuthentication;
use Microsoft\Graph\Generated\Models\CustomExtensionCallbackConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessPackageAssignmentRequestWorkflowExtension();
$requestBody->setOdataType('#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension');
$requestBody->setDisplayName('test_action_0124_email');
$requestBody->setDescription('this is for graph testing only');
$endpointConfiguration = new LogicAppTriggerEndpointConfiguration();
$endpointConfiguration->setOdataType('#microsoft.graph.logicAppTriggerEndpointConfiguration');
$endpointConfiguration->setSubscriptionId('38ab2ccc-3747-4567-b36b-9478f5602f0d');
$endpointConfiguration->setResourceGroupName('test');
$endpointConfiguration->setLogicAppWorkflowName('elm-extension-email');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$authenticationConfiguration = new AzureAdPopTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdPopTokenAuthentication');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$callbackConfiguration = new CustomExtensionCallbackConfiguration();
$callbackConfiguration->setOdataType('microsoft.graph.customExtensionCallbackConfiguration');
$additionalData = [
	'durationBeforeTimeout' => 'PT1H',
];
$callbackConfiguration->setAdditionalData($additionalData);
$requestBody->setCallbackConfiguration($callbackConfiguration);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->byAccessPackageCatalogId('accessPackageCatalog-id')->customWorkflowExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension"
	displayName = "test_action_0124_email"
	description = "this is for graph testing only"
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.logicAppTriggerEndpointConfiguration"
		subscriptionId = "38ab2ccc-3747-4567-b36b-9478f5602f0d"
		resourceGroupName = "test"
		logicAppWorkflowName = "elm-extension-email"
	}
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdPopTokenAuthentication"
	}
	callbackConfiguration = @{
		"@odata.type" = "microsoft.graph.customExtensionCallbackConfiguration"
		durationBeforeTimeout = "PT1H"
	}
}

New-MgEntitlementManagementCatalogCustomWorkflowExtension -AccessPackageCatalogId $accessPackageCatalogId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_package_assignment_request_workflow_extension import AccessPackageAssignmentRequestWorkflowExtension
from msgraph.generated.models.logic_app_trigger_endpoint_configuration import LogicAppTriggerEndpointConfiguration
from msgraph.generated.models.azure_ad_pop_token_authentication import AzureAdPopTokenAuthentication
from msgraph.generated.models.custom_extension_callback_configuration import CustomExtensionCallbackConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessPackageAssignmentRequestWorkflowExtension(
	odata_type = "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
	display_name = "test_action_0124_email",
	description = "this is for graph testing only",
	endpoint_configuration = LogicAppTriggerEndpointConfiguration(
		odata_type = "#microsoft.graph.logicAppTriggerEndpointConfiguration",
		subscription_id = "38ab2ccc-3747-4567-b36b-9478f5602f0d",
		resource_group_name = "test",
		logic_app_workflow_name = "elm-extension-email",
	),
	authentication_configuration = AzureAdPopTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdPopTokenAuthentication",
	),
	callback_configuration = CustomExtensionCallbackConfiguration(
		odata_type = "microsoft.graph.customExtensionCallbackConfiguration",
		additional_data = {
				"duration_before_timeout" : "PT1H",
		}
	),
)

result = await graph_client.identity_governance.entitlement_management.catalogs.by_access_package_catalog_id('accessPackageCatalog-id').custom_workflow_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
   "value":{
      "@odata.type":"#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
      "id":"98ffaec5-ae8e-4902-a434-5ffc5d3d3cd0",
      "displayName":"test_action_0124_email",
      "description":"this is for graph testing only",
      "createdDateTime":"2022-01-24T21:48:57.15Z",
      "lastModifiedDateTime":"2022-01-24T21:55:44.953Z",
      "clientConfiguration":null,
      "endpointConfiguration":{
         "@odata.type":"#microsoft.graph.logicAppTriggerEndpointConfiguration",
         "subscriptionId":"38ab2ccc-3747-4567-b36b-9478f5602f0d",
         "resourceGroupName":"test",
         "logicAppWorkflowName":"elm-extension-email",
         "url":"https://prod-31.eastus.logic.azure.com:443/workflows/8ccffea766ae48e680gd9a22d1549bbc/triggers/manual/paths/invoke?api-version=2016-10-01"
      },
      "authenticationConfiguration":{
         "@odata.type":"#microsoft.graph.azureAdPopTokenAuthentication"
      },
      "callbackConfiguration":{
         "@odata.type":"microsoft.graph.customExtensionCallbackConfiguration",
         "durationBeforeTimeout":"PT1H"
      }
   }
}
```

### Example 2: Create a custom extension for use with an access package assignment

The following is an example of a access package assignment custom workflow extension.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/catalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customWorkflowExtensions
Content-Type: application/json

{
   "value":{
      "@odata.type":"#microsoft.graph.accessPackageAssignmentWorkflowExtension",
      "displayName":"test_action_0127_email",
      "description":"this is for graph testing only",
      "endpointConfiguration":{
         "@odata.type":"#microsoft.graph.logicAppTriggerEndpointConfiguration",
         "subscriptionId":"38ab2ccc-3747-4567-b36b-9478f5602f0d",
         "resourceGroupName":"test",
         "logicAppWorkflowName":"elm-extension-email"
      },
      "authenticationConfiguration":{
         "@odata.type":"#microsoft.graph.azureAdPopTokenAuthentication"
      }
   }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CustomCalloutExtension
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"value" , new AccessPackageAssignmentWorkflowExtension
			{
				OdataType = "#microsoft.graph.accessPackageAssignmentWorkflowExtension",
				DisplayName = "test_action_0127_email",
				Description = "this is for graph testing only",
				EndpointConfiguration = new LogicAppTriggerEndpointConfiguration
				{
					OdataType = "#microsoft.graph.logicAppTriggerEndpointConfiguration",
					SubscriptionId = "38ab2ccc-3747-4567-b36b-9478f5602f0d",
					ResourceGroupName = "test",
					LogicAppWorkflowName = "elm-extension-email",
				},
				AuthenticationConfiguration = new AzureAdPopTokenAuthentication
				{
					OdataType = "#microsoft.graph.azureAdPopTokenAuthentication",
				},
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.EntitlementManagement.Catalogs["{accessPackageCatalog-id}"].CustomWorkflowExtensions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCustomCalloutExtension()
additionalData := map[string]interface{}{
value := graphmodels.NewAccessPackageAssignmentWorkflowExtension()
displayName := "test_action_0127_email"
value.SetDisplayName(&displayName) 
description := "this is for graph testing only"
value.SetDescription(&description) 
endpointConfiguration := graphmodels.NewLogicAppTriggerEndpointConfiguration()
subscriptionId := "38ab2ccc-3747-4567-b36b-9478f5602f0d"
endpointConfiguration.SetSubscriptionId(&subscriptionId) 
resourceGroupName := "test"
endpointConfiguration.SetResourceGroupName(&resourceGroupName) 
logicAppWorkflowName := "elm-extension-email"
endpointConfiguration.SetLogicAppWorkflowName(&logicAppWorkflowName) 
	value.SetEndpointConfiguration(endpointConfiguration)
authenticationConfiguration := graphmodels.NewAzureAdPopTokenAuthentication()
	value.SetAuthenticationConfiguration(authenticationConfiguration)
	requestBody.SetValue(value)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customWorkflowExtensions, err := graphClient.IdentityGovernance().EntitlementManagement().Catalogs().ByAccessPackageCatalogId("accessPackageCatalog-id").CustomWorkflowExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CustomCalloutExtension customCalloutExtension = new CustomCalloutExtension();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
AccessPackageAssignmentWorkflowExtension value = new AccessPackageAssignmentWorkflowExtension();
value.setOdataType("#microsoft.graph.accessPackageAssignmentWorkflowExtension");
value.setDisplayName("test_action_0127_email");
value.setDescription("this is for graph testing only");
LogicAppTriggerEndpointConfiguration endpointConfiguration = new LogicAppTriggerEndpointConfiguration();
endpointConfiguration.setOdataType("#microsoft.graph.logicAppTriggerEndpointConfiguration");
endpointConfiguration.setSubscriptionId("38ab2ccc-3747-4567-b36b-9478f5602f0d");
endpointConfiguration.setResourceGroupName("test");
endpointConfiguration.setLogicAppWorkflowName("elm-extension-email");
value.setEndpointConfiguration(endpointConfiguration);
AzureAdPopTokenAuthentication authenticationConfiguration = new AzureAdPopTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdPopTokenAuthentication");
value.setAuthenticationConfiguration(authenticationConfiguration);
additionalData.put("value", value);
customCalloutExtension.setAdditionalData(additionalData);
CustomCalloutExtension result = graphClient.identityGovernance().entitlementManagement().catalogs().byAccessPackageCatalogId("{accessPackageCatalog-id}").customWorkflowExtensions().post(customCalloutExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customCalloutExtension = {
   value: {
      '@odata.type':'#microsoft.graph.accessPackageAssignmentWorkflowExtension',
      displayName: 'test_action_0127_email',
      description: 'this is for graph testing only',
      endpointConfiguration: {
         '@odata.type':'#microsoft.graph.logicAppTriggerEndpointConfiguration',
         subscriptionId: '38ab2ccc-3747-4567-b36b-9478f5602f0d',
         resourceGroupName: 'test',
         logicAppWorkflowName: 'elm-extension-email'
      },
      authenticationConfiguration: {
         '@odata.type':'#microsoft.graph.azureAdPopTokenAuthentication'
      }
   }
};

await client.api('/identityGovernance/entitlementManagement/catalogs/32efb28c-9a7a-446c-986b-ca6528c6669d/customWorkflowExtensions')
	.post(customCalloutExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CustomCalloutExtension;
use Microsoft\Graph\Generated\Models\AccessPackageAssignmentWorkflowExtension;
use Microsoft\Graph\Generated\Models\LogicAppTriggerEndpointConfiguration;
use Microsoft\Graph\Generated\Models\AzureAdPopTokenAuthentication;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomCalloutExtension();
$additionalData = [
	'value' => [
		'@odata.type' => '#microsoft.graph.accessPackageAssignmentWorkflowExtension',
		'displayName' => 'test_action_0127_email',
		'description' => 'this is for graph testing only',
		'endpointConfiguration' => [
			'@odata.type' => '#microsoft.graph.logicAppTriggerEndpointConfiguration',
			'subscriptionId' => '38ab2ccc-3747-4567-b36b-9478f5602f0d',
			'resourceGroupName' => 'test',
			'logicAppWorkflowName' => 'elm-extension-email',
		],
		'authenticationConfiguration' => [
			'@odata.type' => '#microsoft.graph.azureAdPopTokenAuthentication',
		],
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->entitlementManagement()->catalogs()->byAccessPackageCatalogId('accessPackageCatalog-id')->customWorkflowExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	value = @{
		"@odata.type" = "#microsoft.graph.accessPackageAssignmentWorkflowExtension"
		displayName = "test_action_0127_email"
		description = "this is for graph testing only"
		endpointConfiguration = @{
			"@odata.type" = "#microsoft.graph.logicAppTriggerEndpointConfiguration"
			subscriptionId = "38ab2ccc-3747-4567-b36b-9478f5602f0d"
			resourceGroupName = "test"
			logicAppWorkflowName = "elm-extension-email"
		}
		authenticationConfiguration = @{
			"@odata.type" = "#microsoft.graph.azureAdPopTokenAuthentication"
		}
	}
}

New-MgEntitlementManagementCatalogCustomWorkflowExtension -AccessPackageCatalogId $accessPackageCatalogId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.custom_callout_extension import CustomCalloutExtension
from msgraph.generated.models.access_package_assignment_workflow_extension import AccessPackageAssignmentWorkflowExtension
from msgraph.generated.models.logic_app_trigger_endpoint_configuration import LogicAppTriggerEndpointConfiguration
from msgraph.generated.models.azure_ad_pop_token_authentication import AzureAdPopTokenAuthentication
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomCalloutExtension(
	additional_data = {
			"value" : {
					"@odata_type" : "#microsoft.graph.accessPackageAssignmentWorkflowExtension",
					"display_name" : "test_action_0127_email",
					"description" : "this is for graph testing only",
					"endpoint_configuration" : {
							"@odata_type" : "#microsoft.graph.logicAppTriggerEndpointConfiguration",
							"subscription_id" : "38ab2ccc-3747-4567-b36b-9478f5602f0d",
							"resource_group_name" : "test",
							"logic_app_workflow_name" : "elm-extension-email",
					},
					"authentication_configuration" : {
							"@odata_type" : "#microsoft.graph.azureAdPopTokenAuthentication",
					},
			},
	}
)

result = await graph_client.identity_governance.entitlement_management.catalogs.by_access_package_catalog_id('accessPackageCatalog-id').custom_workflow_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
   "value":{
      "@odata.type":"#microsoft.graph.accessPackageAssignmentWorkflowExtension",
      "id":"78ffaec5-ae8e-4902-a434-5ffc5d3d3cd0",
      "displayName":"test_action_0127_email",
      "description":"this is for graph testing only",
      "createdDateTime":"2022-01-24T21:48:57.15Z",
      "lastModifiedDateTime":"2022-01-24T21:55:44.953Z",
      "clientConfiguration":null,
      "endpointConfiguration":{
         "@odata.type":"#microsoft.graph.logicAppTriggerEndpointConfiguration",
         "subscriptionId":"38ab2ccc-3747-4567-b36b-9478f5602f0d",
         "resourceGroupName":"test",
         "logicAppWorkflowName":"elm-extension-email",
         "url":"https://prod-31.eastus.logic.azure.com:443/workflows/7ccffea766ae48e680gd9a22d1549bbc/triggers/manual/paths/invoke?api-version=2016-10-01"
      },
      "authenticationConfiguration":{
         "@odata.type":"#microsoft.graph.azureAdPopTokenAuthentication"
      }
   }
}
```

### Example 3: Create a custom extension for use with an approval stage callback

The following is an example of a access package assignment request custom workflow extension.

#### Request

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/entitlementManagement/accessPackageCatalogs/a9286c9c-7659-4b2e-ba44-4d1f2ce07746/accessPackagecustomWorkflowExtensions
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
  "displayName": "test_action_0124_email",
  "description": "this is for graph testing only",
  "endpointConfiguration": {
    "@odata.type": "#microsoft.graph.logicAppTriggerEndpointConfiguration",
    "subscriptionId": "38ab2ccc-3747-4567-b36b-9478f5602f0d",
    "resourceGroupName": "test",
    "logicAppWorkflowName": "elm-extension-email"
  },
  "authenticationConfiguration": {
    "@odata.type": "#microsoft.graph.azureAdPopTokenAuthentication"
  },
  "callbackConfiguration": {
    "@odata.type": "microsoft.graph.accessPackageRequestApprovalStageCallbackConfiguration",
    "durationBeforeTimeout": "PT1H"
  }
}
```

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
   "value":{
      "@odata.type":"#microsoft.graph.accessPackageAssignmentRequestWorkflowExtension",
      "id":"5afcb385-d500-450c-bbf6-3b74a44403da",
      "displayName":"test_action_0124_email",
      "description":"this is for graph testing only",
      "createdDateTime":"2022-01-24T21:48:57.15Z",
      "lastModifiedDateTime":"2022-01-24T21:55:44.953Z",
      "clientConfiguration":null,
      "endpointConfiguration":{
         "@odata.type":"#microsoft.graph.logicAppTriggerEndpointConfiguration",
         "subscriptionId":"e8eb46ab-626d-451f-8668-9434e73cf43b",
         "resourceGroupName":"test",
         "logicAppWorkflowName":"elm-extension-email",
         "url":"https://prod-31.eastus.logic.azure.com:443/workflows/8ccffea766ae48e680gd9a22d1549bbc/triggers/manual/paths/invoke?api-version=2016-10-01"
      },
      "authenticationConfiguration":{
         "@odata.type":"#microsoft.graph.azureAdPopTokenAuthentication"
      },
      "callbackConfiguration":{
         "@odata.type":"microsoft.graph.accessPackageRequestApprovalStageCallbackConfiguration",
         "durationBeforeTimeout":"PT1H"
      }
   }
} 
```
