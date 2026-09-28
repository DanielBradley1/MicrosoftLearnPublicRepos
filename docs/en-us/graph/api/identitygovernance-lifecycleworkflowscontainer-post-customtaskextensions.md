<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-customtaskextensions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# Create customTaskExtensions

Namespace: microsoft.graph.identityGovernance

Create a new [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecycleWorkflows-CustomExt.ReadWrite.All | LifecycleWorkflows.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecycleWorkflows-CustomExt.ReadWrite.All | LifecycleWorkflows.ReadWrite.All |

Important

The calling user also requires one of the following Azure Resource Manager roles for the specified Azure Logic App: **Logic App contributor**, **Contributor**, or **Owner**.

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Lifecycle Workflows Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
POST /identityGovernance/lifecycleWorkflows/customTaskExtensions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) object.

You can specify the following properties when creating a **customTaskExtension**.

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationConfiguration | [microsoft.graph.customExtensionAuthenticationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionauthenticationconfiguration?view=graph-rest-1.0) | The authentication configuration for the `customTaskExtension`. |
| clientConfiguration | [microsoft.graph.customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | The client configuration for a custom extension. |
| description | String | The description of the `customTaskExtension`. |
| displayName | String | A unique string that identifies the `customTaskExtension`. |
| endpointConfiguration | [microsoft.graph.customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) | The endpoint configuration for a custom extension. Optional. |
| callbackConfiguration | [microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackconfiguration?view=graph-rest-1.0) | The callback configuration for a custom extension. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.identityGovernance.customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/lifecycleWorkflows/customTaskExtensions
Content-Type: application/json
Content-length: 588

{
    "displayName": "Grant manager access to mailbox and OneDrive",
    "description": "Grant manager access to mailbox and OneDrive",
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.logicAppTriggerEndpointConfiguration",
        "subscriptionId": "c500b67c-e9b7-4ad2-a90d-77d41385ae55",
        "resourceGroupName": "RG-LCM",
        "logicAppWorkflowName": "ManagerAccess"
    },
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "542dc01a-0b5d-4edc-b3f9-5cfe6393f557"
    },
    "clientConfiguration": {
        "@odata.type": "#microsoft.graph.customExtensionClientConfiguration",
        "maximumRetries": 1,
        "timeoutInMilliseconds": 1000
    },
    "callbackConfiguration": {
        "@odata.type": "#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration",
        "timeoutDuration": "PT30M"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.IdentityGovernance;
using Microsoft.Graph.Models;

var requestBody = new CustomTaskExtension
{
	DisplayName = "Grant manager access to mailbox and OneDrive",
	Description = "Grant manager access to mailbox and OneDrive",
	EndpointConfiguration = new LogicAppTriggerEndpointConfiguration
	{
		OdataType = "#microsoft.graph.logicAppTriggerEndpointConfiguration",
		SubscriptionId = "c500b67c-e9b7-4ad2-a90d-77d41385ae55",
		ResourceGroupName = "RG-LCM",
		LogicAppWorkflowName = "ManagerAccess",
	},
	AuthenticationConfiguration = new AzureAdTokenAuthentication
	{
		OdataType = "#microsoft.graph.azureAdTokenAuthentication",
		ResourceId = "542dc01a-0b5d-4edc-b3f9-5cfe6393f557",
	},
	ClientConfiguration = new CustomExtensionClientConfiguration
	{
		OdataType = "#microsoft.graph.customExtensionClientConfiguration",
		MaximumRetries = 1,
		TimeoutInMilliseconds = 1000,
	},
	CallbackConfiguration = new CustomTaskExtensionCallbackConfiguration
	{
		OdataType = "#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration",
		TimeoutDuration = TimeSpan.Parse("PT30M"),
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.LifecycleWorkflows.CustomTaskExtensions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelsidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/models/identitygovernance"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodelsidentitygovernance.NewCustomTaskExtension()
displayName := "Grant manager access to mailbox and OneDrive"
requestBody.SetDisplayName(&displayName) 
description := "Grant manager access to mailbox and OneDrive"
requestBody.SetDescription(&description) 
endpointConfiguration := graphmodels.NewLogicAppTriggerEndpointConfiguration()
subscriptionId := "c500b67c-e9b7-4ad2-a90d-77d41385ae55"
endpointConfiguration.SetSubscriptionId(&subscriptionId) 
resourceGroupName := "RG-LCM"
endpointConfiguration.SetResourceGroupName(&resourceGroupName) 
logicAppWorkflowName := "ManagerAccess"
endpointConfiguration.SetLogicAppWorkflowName(&logicAppWorkflowName) 
requestBody.SetEndpointConfiguration(endpointConfiguration)
authenticationConfiguration := graphmodels.NewAzureAdTokenAuthentication()
resourceId := "542dc01a-0b5d-4edc-b3f9-5cfe6393f557"
authenticationConfiguration.SetResourceId(&resourceId) 
requestBody.SetAuthenticationConfiguration(authenticationConfiguration)
clientConfiguration := graphmodels.NewCustomExtensionClientConfiguration()
maximumRetries := int32(1)
clientConfiguration.SetMaximumRetries(&maximumRetries) 
timeoutInMilliseconds := int32(1000)
clientConfiguration.SetTimeoutInMilliseconds(&timeoutInMilliseconds) 
requestBody.SetClientConfiguration(clientConfiguration)
callbackConfiguration := graphmodelsidentitygovernance.NewCustomTaskExtensionCallbackConfiguration()
timeoutDuration , err := abstractions.ParseISODuration("PT30M")
callbackConfiguration.SetTimeoutDuration(&timeoutDuration) 
requestBody.SetCallbackConfiguration(callbackConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customTaskExtensions, err := graphClient.IdentityGovernance().LifecycleWorkflows().CustomTaskExtensions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.identitygovernance.CustomTaskExtension customTaskExtension = new com.microsoft.graph.models.identitygovernance.CustomTaskExtension();
customTaskExtension.setDisplayName("Grant manager access to mailbox and OneDrive");
customTaskExtension.setDescription("Grant manager access to mailbox and OneDrive");
LogicAppTriggerEndpointConfiguration endpointConfiguration = new LogicAppTriggerEndpointConfiguration();
endpointConfiguration.setOdataType("#microsoft.graph.logicAppTriggerEndpointConfiguration");
endpointConfiguration.setSubscriptionId("c500b67c-e9b7-4ad2-a90d-77d41385ae55");
endpointConfiguration.setResourceGroupName("RG-LCM");
endpointConfiguration.setLogicAppWorkflowName("ManagerAccess");
customTaskExtension.setEndpointConfiguration(endpointConfiguration);
AzureAdTokenAuthentication authenticationConfiguration = new AzureAdTokenAuthentication();
authenticationConfiguration.setOdataType("#microsoft.graph.azureAdTokenAuthentication");
authenticationConfiguration.setResourceId("542dc01a-0b5d-4edc-b3f9-5cfe6393f557");
customTaskExtension.setAuthenticationConfiguration(authenticationConfiguration);
CustomExtensionClientConfiguration clientConfiguration = new CustomExtensionClientConfiguration();
clientConfiguration.setOdataType("#microsoft.graph.customExtensionClientConfiguration");
clientConfiguration.setMaximumRetries(1);
clientConfiguration.setTimeoutInMilliseconds(1000);
customTaskExtension.setClientConfiguration(clientConfiguration);
com.microsoft.graph.models.identitygovernance.CustomTaskExtensionCallbackConfiguration callbackConfiguration = new com.microsoft.graph.models.identitygovernance.CustomTaskExtensionCallbackConfiguration();
callbackConfiguration.setOdataType("#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration");
PeriodAndDuration timeoutDuration = PeriodAndDuration.ofDuration(Duration.parse("PT30M"));
callbackConfiguration.setTimeoutDuration(timeoutDuration);
customTaskExtension.setCallbackConfiguration(callbackConfiguration);
com.microsoft.graph.models.identitygovernance.CustomTaskExtension result = graphClient.identityGovernance().lifecycleWorkflows().customTaskExtensions().post(customTaskExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const customTaskExtension = {
    displayName: 'Grant manager access to mailbox and OneDrive',
    description: 'Grant manager access to mailbox and OneDrive',
    endpointConfiguration: {
        '@odata.type': '#microsoft.graph.logicAppTriggerEndpointConfiguration',
        subscriptionId: 'c500b67c-e9b7-4ad2-a90d-77d41385ae55',
        resourceGroupName: 'RG-LCM',
        logicAppWorkflowName: 'ManagerAccess'
    },
    authenticationConfiguration: {
        '@odata.type': '#microsoft.graph.azureAdTokenAuthentication',
        resourceId: '542dc01a-0b5d-4edc-b3f9-5cfe6393f557'
    },
    clientConfiguration: {
        '@odata.type': '#microsoft.graph.customExtensionClientConfiguration',
        maximumRetries: 1,
        timeoutInMilliseconds: 1000
    },
    callbackConfiguration: {
        '@odata.type': '#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration',
        timeoutDuration: 'PT30M'
    }
};

await client.api('/identityGovernance/lifecycleWorkflows/customTaskExtensions')
	.post(customTaskExtension);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\IdentityGovernance\CustomTaskExtension;
use Microsoft\Graph\Generated\Models\LogicAppTriggerEndpointConfiguration;
use Microsoft\Graph\Generated\Models\AzureAdTokenAuthentication;
use Microsoft\Graph\Generated\Models\CustomExtensionClientConfiguration;
use Microsoft\Graph\Generated\Models\IdentityGovernance\CustomTaskExtensionCallbackConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CustomTaskExtension();
$requestBody->setDisplayName('Grant manager access to mailbox and OneDrive');
$requestBody->setDescription('Grant manager access to mailbox and OneDrive');
$endpointConfiguration = new LogicAppTriggerEndpointConfiguration();
$endpointConfiguration->setOdataType('#microsoft.graph.logicAppTriggerEndpointConfiguration');
$endpointConfiguration->setSubscriptionId('c500b67c-e9b7-4ad2-a90d-77d41385ae55');
$endpointConfiguration->setResourceGroupName('RG-LCM');
$endpointConfiguration->setLogicAppWorkflowName('ManagerAccess');
$requestBody->setEndpointConfiguration($endpointConfiguration);
$authenticationConfiguration = new AzureAdTokenAuthentication();
$authenticationConfiguration->setOdataType('#microsoft.graph.azureAdTokenAuthentication');
$authenticationConfiguration->setResourceId('542dc01a-0b5d-4edc-b3f9-5cfe6393f557');
$requestBody->setAuthenticationConfiguration($authenticationConfiguration);
$clientConfiguration = new CustomExtensionClientConfiguration();
$clientConfiguration->setOdataType('#microsoft.graph.customExtensionClientConfiguration');
$clientConfiguration->setMaximumRetries(1);
$clientConfiguration->setTimeoutInMilliseconds(1000);
$requestBody->setClientConfiguration($clientConfiguration);
$callbackConfiguration = new CustomTaskExtensionCallbackConfiguration();
$callbackConfiguration->setOdataType('#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration');
$callbackConfiguration->setTimeoutDuration(new \DateInterval('PT30M'));
$requestBody->setCallbackConfiguration($callbackConfiguration);

$result = $graphServiceClient->identityGovernance()->lifecycleWorkflows()->customTaskExtensions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Grant manager access to mailbox and OneDrive"
	description = "Grant manager access to mailbox and OneDrive"
	endpointConfiguration = @{
		"@odata.type" = "#microsoft.graph.logicAppTriggerEndpointConfiguration"
		subscriptionId = "c500b67c-e9b7-4ad2-a90d-77d41385ae55"
		resourceGroupName = "RG-LCM"
		logicAppWorkflowName = "ManagerAccess"
	}
	authenticationConfiguration = @{
		"@odata.type" = "#microsoft.graph.azureAdTokenAuthentication"
		resourceId = "542dc01a-0b5d-4edc-b3f9-5cfe6393f557"
	}
	clientConfiguration = @{
		"@odata.type" = "#microsoft.graph.customExtensionClientConfiguration"
		maximumRetries = 1
		timeoutInMilliseconds = 1000
	}
	callbackConfiguration = @{
		"@odata.type" = "#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration"
		timeoutDuration = "PT30M"
	}
}

New-MgIdentityGovernanceLifecycleWorkflowCustomTaskExtension -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.identity_governance.custom_task_extension import CustomTaskExtension
from msgraph.generated.models.logic_app_trigger_endpoint_configuration import LogicAppTriggerEndpointConfiguration
from msgraph.generated.models.azure_ad_token_authentication import AzureAdTokenAuthentication
from msgraph.generated.models.custom_extension_client_configuration import CustomExtensionClientConfiguration
from msgraph.generated.models.identity_governance.custom_task_extension_callback_configuration import CustomTaskExtensionCallbackConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CustomTaskExtension(
	display_name = "Grant manager access to mailbox and OneDrive",
	description = "Grant manager access to mailbox and OneDrive",
	endpoint_configuration = LogicAppTriggerEndpointConfiguration(
		odata_type = "#microsoft.graph.logicAppTriggerEndpointConfiguration",
		subscription_id = "c500b67c-e9b7-4ad2-a90d-77d41385ae55",
		resource_group_name = "RG-LCM",
		logic_app_workflow_name = "ManagerAccess",
	),
	authentication_configuration = AzureAdTokenAuthentication(
		odata_type = "#microsoft.graph.azureAdTokenAuthentication",
		resource_id = "542dc01a-0b5d-4edc-b3f9-5cfe6393f557",
	),
	client_configuration = CustomExtensionClientConfiguration(
		odata_type = "#microsoft.graph.customExtensionClientConfiguration",
		maximum_retries = 1,
		timeout_in_milliseconds = 1000,
	),
	callback_configuration = CustomTaskExtensionCallbackConfiguration(
		odata_type = "#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration",
		timeout_duration = "PT30M",
	),
)

result = await graph_client.identity_governance.lifecycle_workflows.custom_task_extensions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/lifecycleWorkflows/customTaskExtensions/$entity",
    "id": "ee2590e4-4572-4820-a397-969ecd7bd6a9",
    "displayName": "Grant manager access to mailbox and OneDrive",
    "description": "Grant manager access to mailbox and OneDrive",
    "createdDateTime": "2022-08-24T22:37:46.1790566Z",
    "lastModifiedDateTime": "2022-08-24T22:37:46.179062Z",
    "endpointConfiguration": {
        "@odata.type": "#microsoft.graph.logicAppTriggerEndpointConfiguration",
        "subscriptionId": "c500b67c-e9b7-4ad2-a90d-77d41385ae55",
        "resourceGroupName": "RG-LCM",
        "logicAppWorkflowName": "ManagerAccess"
    },
    "authenticationConfiguration": {
        "@odata.type": "#microsoft.graph.azureAdTokenAuthentication",
        "resourceId": "542dc01a-0b5d-4edc-b3f9-5cfe6393f557"
    },
    "clientConfiguration": {
        "@odata.type": "#microsoft.graph.customExtensionClientConfiguration",
        "maximumRetries": 1,
        "timeoutInMilliseconds": 1000
    },
    "callbackConfiguration": {
        "@odata.type": "#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration",
        "timeoutDuration": "PT30M"
    }
}
```
