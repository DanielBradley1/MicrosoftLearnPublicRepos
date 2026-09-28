<!-- Source: https://learn.microsoft.com/en-us/graph/api/template-post-devicetemplates?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-02-11 -->

# Create deviceTemplate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) used to identify attributes and manage a group of devices with similar characteristics.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DeviceTemplate.Create | DeviceTemplate.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DeviceTemplate.Create | DeviceTemplate.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Cloud Device Administrator
- IoT Device Administrator
- Users - owners of the device template object

## HTTP request

```http
POST /directory/templates/deviceTemplates
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) object.

You can specify the following properties when you create a **deviceTemplate**.

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceAuthority | String | A tenant-defined name for the party that's responsible for provisioning and managing devices on the Microsoft Entra tenant. For example, Tailwind Traders \(the manufacturer\) makes security cameras that are installed in customer buildings and managed by Lakeshore Retail \(the device authority\). This value is provided to the customer by the device authority \(manufacturer or reseller\). Required. |
| manufacturer | String | Manufacturer name. Required. |
| model | String | Model name. Required. |
| mutualTlsOauthConfigurationId | String | Object ID of the [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta). This value isn't required if self-signed certificates are used instead of trusted root certificates. Optional. |
| mutualTlsOauthConfigurationTenantId | String | ID \(tenant ID for device authority\) of the tenant that contains the [mutualTlsOauthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/mutualtlsoauthconfiguration?view=graph-rest-beta). This value isn't required if self-signed certificates are used instead of trusted root certificates. Optional. |
| operatingSystem | String | Operating system type. Optional. |
| owners@odata.bind | String collection | List of IDs for owners to add to the device template. Only the following [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) types are supported as owners: [service principals](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta), [users](https://learn.microsoft.com/en-us/graph/api/resources/users?view=graph-rest-beta), or [applications](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-beta). Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) object in the response body. If a validation failure occurs during the certificate validation steps, the method returns a `400 Bad Request` along with the message, "Unable to validate device certificate".

For more information, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Example 1: Create a new device template

The following example shows how to create a new [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta).

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
POST https://graph.microsoft.com/beta/directory/templates/deviceTemplates
Content-Type: application/json
Content-length: 106

{
  "mutualTlsOauthConfigurationId": "00001111-aaaa-2222-bbbb-3333cccc4444",
  "mutualTlsOauthConfigurationTenantId": "00001111-aaaa-2222-bbbb-3333cccc4445",
  "deviceAuthority": "Lakeshore Retail",
  "manufacturer": "Tailwind Traders",
  "model": "DeepFreezerModelAB",
  "operatingSystem": "WindowsIoT"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new DeviceTemplate
{
	MutualTlsOauthConfigurationId = "00001111-aaaa-2222-bbbb-3333cccc4444",
	MutualTlsOauthConfigurationTenantId = "00001111-aaaa-2222-bbbb-3333cccc4445",
	DeviceAuthority = "Lakeshore Retail",
	Manufacturer = "Tailwind Traders",
	Model = "DeepFreezerModelAB",
	OperatingSystem = "WindowsIoT",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.Templates.DeviceTemplates.PostAsync(requestBody);
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

requestBody := graphmodels.NewDeviceTemplate()
mutualTlsOauthConfigurationId := "00001111-aaaa-2222-bbbb-3333cccc4444"
requestBody.SetMutualTlsOauthConfigurationId(&mutualTlsOauthConfigurationId) 
mutualTlsOauthConfigurationTenantId := "00001111-aaaa-2222-bbbb-3333cccc4445"
requestBody.SetMutualTlsOauthConfigurationTenantId(&mutualTlsOauthConfigurationTenantId) 
deviceAuthority := "Lakeshore Retail"
requestBody.SetDeviceAuthority(&deviceAuthority) 
manufacturer := "Tailwind Traders"
requestBody.SetManufacturer(&manufacturer) 
model := "DeepFreezerModelAB"
requestBody.SetModel(&model) 
operatingSystem := "WindowsIoT"
requestBody.SetOperatingSystem(&operatingSystem) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
deviceTemplates, err := graphClient.Directory().Templates().DeviceTemplates().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DeviceTemplate deviceTemplate = new DeviceTemplate();
deviceTemplate.setMutualTlsOauthConfigurationId("00001111-aaaa-2222-bbbb-3333cccc4444");
deviceTemplate.setMutualTlsOauthConfigurationTenantId("00001111-aaaa-2222-bbbb-3333cccc4445");
deviceTemplate.setDeviceAuthority("Lakeshore Retail");
deviceTemplate.setManufacturer("Tailwind Traders");
deviceTemplate.setModel("DeepFreezerModelAB");
deviceTemplate.setOperatingSystem("WindowsIoT");
DeviceTemplate result = graphClient.directory().templates().deviceTemplates().post(deviceTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const deviceTemplate = {
  mutualTlsOauthConfigurationId: '00001111-aaaa-2222-bbbb-3333cccc4444',
  mutualTlsOauthConfigurationTenantId: '00001111-aaaa-2222-bbbb-3333cccc4445',
  deviceAuthority: 'Lakeshore Retail',
  manufacturer: 'Tailwind Traders',
  model: 'DeepFreezerModelAB',
  operatingSystem: 'WindowsIoT'
};

await client.api('/directory/templates/deviceTemplates')
	.version('beta')
	.post(deviceTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\DeviceTemplate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DeviceTemplate();
$requestBody->setMutualTlsOauthConfigurationId('00001111-aaaa-2222-bbbb-3333cccc4444');
$requestBody->setMutualTlsOauthConfigurationTenantId('00001111-aaaa-2222-bbbb-3333cccc4445');
$requestBody->setDeviceAuthority('Lakeshore Retail');
$requestBody->setManufacturer('Tailwind Traders');
$requestBody->setModel('DeepFreezerModelAB');
$requestBody->setOperatingSystem('WindowsIoT');

$result = $graphServiceClient->directory()->templates()->deviceTemplates()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	mutualTlsOauthConfigurationId = "00001111-aaaa-2222-bbbb-3333cccc4444"
	mutualTlsOauthConfigurationTenantId = "00001111-aaaa-2222-bbbb-3333cccc4445"
	deviceAuthority = "Lakeshore Retail"
	manufacturer = "Tailwind Traders"
	model = "DeepFreezerModelAB"
	operatingSystem = "WindowsIoT"
}

New-MgBetaDirectoryTemplateDeviceTemplate -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.device_template import DeviceTemplate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DeviceTemplate(
	mutual_tls_oauth_configuration_id = "00001111-aaaa-2222-bbbb-3333cccc4444",
	mutual_tls_oauth_configuration_tenant_id = "00001111-aaaa-2222-bbbb-3333cccc4445",
	device_authority = "Lakeshore Retail",
	manufacturer = "Tailwind Traders",
	model = "DeepFreezerModelAB",
	operating_system = "WindowsIoT",
)

result = await graph_client.directory.templates.device_templates.post(request_body)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directory/templates/deviceTemplates/$entity",
  "id": "c0ff9329-3596-4ece-8aa9-3dd23a925356",
  "mutualTlsOauthConfigurationId": "00001111-aaaa-2222-bbbb-3333cccc4444",
  "mutualTlsOauthConfigurationTenantId": "00001111-aaaa-2222-bbbb-3333cccc4445",
  "deletedDateTime": null,
  "deviceAuthority": "Lakeshore Retail",
  "manufacturer": "Tailwind Traders",
  "model": "DeepFreezerModelAB",
  "operatingSystem": "WindowsIoT"
}
```

### Example 2: Create a device template with an owner

The following example shows how to create a new [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta) with an owner.

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
POST https://graph.microsoft.com/beta/directory/templates/deviceTemplates
Content-Type: application/json
Content-length: 106

{
  "mutualTlsOauthConfigurationId": "00001111-aaaa-2222-bbbb-3333cccc4444",
  "mutualTlsOauthConfigurationTenantId": "00001111-aaaa-2222-bbbb-3333cccc4445",
  "deviceAuthority": "Lakeshore Retail",
  "manufacturer": "Tailwind Traders",
  "model": "DeepFreezerModelAB",
  "operatingSystem": "WindowsIoT",
  "owners@odata.bind": [
    "https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new DeviceTemplate
{
	MutualTlsOauthConfigurationId = "00001111-aaaa-2222-bbbb-3333cccc4444",
	MutualTlsOauthConfigurationTenantId = "00001111-aaaa-2222-bbbb-3333cccc4445",
	DeviceAuthority = "Lakeshore Retail",
	Manufacturer = "Tailwind Traders",
	Model = "DeepFreezerModelAB",
	OperatingSystem = "WindowsIoT",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"owners@odata.bind" , new List<string>
			{
				"https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.Templates.DeviceTemplates.PostAsync(requestBody);
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

requestBody := graphmodels.NewDeviceTemplate()
mutualTlsOauthConfigurationId := "00001111-aaaa-2222-bbbb-3333cccc4444"
requestBody.SetMutualTlsOauthConfigurationId(&mutualTlsOauthConfigurationId) 
mutualTlsOauthConfigurationTenantId := "00001111-aaaa-2222-bbbb-3333cccc4445"
requestBody.SetMutualTlsOauthConfigurationTenantId(&mutualTlsOauthConfigurationTenantId) 
deviceAuthority := "Lakeshore Retail"
requestBody.SetDeviceAuthority(&deviceAuthority) 
manufacturer := "Tailwind Traders"
requestBody.SetManufacturer(&manufacturer) 
model := "DeepFreezerModelAB"
requestBody.SetModel(&model) 
operatingSystem := "WindowsIoT"
requestBody.SetOperatingSystem(&operatingSystem) 
additionalData := map[string]interface{}{
	odataBind := []string {
		"https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222",
	}
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
deviceTemplates, err := graphClient.Directory().Templates().DeviceTemplates().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DeviceTemplate deviceTemplate = new DeviceTemplate();
deviceTemplate.setMutualTlsOauthConfigurationId("00001111-aaaa-2222-bbbb-3333cccc4444");
deviceTemplate.setMutualTlsOauthConfigurationTenantId("00001111-aaaa-2222-bbbb-3333cccc4445");
deviceTemplate.setDeviceAuthority("Lakeshore Retail");
deviceTemplate.setManufacturer("Tailwind Traders");
deviceTemplate.setModel("DeepFreezerModelAB");
deviceTemplate.setOperatingSystem("WindowsIoT");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> ownersOdataBind = new LinkedList<String>();
ownersOdataBind.add("https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222");
additionalData.put("owners@odata.bind", ownersOdataBind);
deviceTemplate.setAdditionalData(additionalData);
DeviceTemplate result = graphClient.directory().templates().deviceTemplates().post(deviceTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const deviceTemplate = {
  mutualTlsOauthConfigurationId: '00001111-aaaa-2222-bbbb-3333cccc4444',
  mutualTlsOauthConfigurationTenantId: '00001111-aaaa-2222-bbbb-3333cccc4445',
  deviceAuthority: 'Lakeshore Retail',
  manufacturer: 'Tailwind Traders',
  model: 'DeepFreezerModelAB',
  operatingSystem: 'WindowsIoT',
  'owners@odata.bind': [
    'https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222'
  ]
};

await client.api('/directory/templates/deviceTemplates')
	.version('beta')
	.post(deviceTemplate);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\DeviceTemplate;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DeviceTemplate();
$requestBody->setMutualTlsOauthConfigurationId('00001111-aaaa-2222-bbbb-3333cccc4444');
$requestBody->setMutualTlsOauthConfigurationTenantId('00001111-aaaa-2222-bbbb-3333cccc4445');
$requestBody->setDeviceAuthority('Lakeshore Retail');
$requestBody->setManufacturer('Tailwind Traders');
$requestBody->setModel('DeepFreezerModelAB');
$requestBody->setOperatingSystem('WindowsIoT');
$additionalData = [
	'owners@odata.bind' => [
'https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222', ],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->directory()->templates()->deviceTemplates()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	mutualTlsOauthConfigurationId = "00001111-aaaa-2222-bbbb-3333cccc4444"
	mutualTlsOauthConfigurationTenantId = "00001111-aaaa-2222-bbbb-3333cccc4445"
	deviceAuthority = "Lakeshore Retail"
	manufacturer = "Tailwind Traders"
	model = "DeepFreezerModelAB"
	operatingSystem = "WindowsIoT"
	"owners@odata.bind" = @(
	"https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222"
)
}

New-MgBetaDirectoryTemplateDeviceTemplate -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.device_template import DeviceTemplate
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DeviceTemplate(
	mutual_tls_oauth_configuration_id = "00001111-aaaa-2222-bbbb-3333cccc4444",
	mutual_tls_oauth_configuration_tenant_id = "00001111-aaaa-2222-bbbb-3333cccc4445",
	device_authority = "Lakeshore Retail",
	manufacturer = "Tailwind Traders",
	model = "DeepFreezerModelAB",
	operating_system = "WindowsIoT",
	additional_data = {
			"owners@odata_bind" : [
				"https://graph.microsoft.com/beta/users/aaaaaaaa-bbbb-cccc-1111-222222222222",
			],
	}
)

result = await graph_client.directory.templates.device_templates.post(request_body)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#directory/templates/deviceTemplates/$entity",
  "id": "c0ff9329-3596-4ece-8aa9-3dd23a925356",
  "mutualTlsOauthConfigurationId": "00001111-aaaa-2222-bbbb-3333cccc4444",
  "mutualTlsOauthConfigurationTenantId": "00001111-aaaa-2222-bbbb-3333cccc4445",
  "deletedDateTime": null,
  "deviceAuthority": "Lakeshore Retail",
  "manufacturer": "Tailwind Traders",
  "model": "DeepFreezerModelAB",
  "operatingSystem": "WindowsIoT"
}
```
