<!-- Source: https://learn.microsoft.com/en-us/graph/api/devicetemplate-createdevicefromtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# deviceTemplate: createDeviceFromTemplate

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) from a [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Device.CreateFromOwnedTemplate | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Cloud Device Administrator
- IoT Device Administrator
- Users - owners of the device template object

> **Note:** Users must be owner of the object.

## HTTP request

```http
POST /directory/templates/deviceTemplates/{deviceTemplateId}/createDeviceFromTemplate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that you can use when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | `true` if the account is enabled; otherwise, `false`. The default value is `true`. A disabled device can't authenticate with Microsoft Entra ID. Optional. |
| alternativeNames | String collection | A collection of ARM resource IDs associated with the device, if any. Optional. |
| externalDeviceId | String | ID of the device in IoT registry. Must be unique within a tenant. Required. |
| externalSourceName | String | Identifies the source name of the device. Optional. |
| keyCredential | [keyCredential](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-beta) | The key credential when you use self-signed certificates. Optional. |
| operatingSystemVersion | String | The operating system version of the device specified. Optional. |

## Response

If successful, this action returns a `200 OK` response code and a [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-beta) object in the response body.

For more information, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/templates/deviceTemplates/2d62b12a-0163-457d-9796-9602e9807e1/createDeviceFromTemplate
Content-Type: application/json

{
  "externalDeviceId": "2fa9424e-7ab0-4a22-8c90-2a20d15d8183",
  "operatingSystemVersion": "Ubuntu 18.04",
  "externalSourceName": "unknown",
  "accountEnabled": false,
  "alternativeNames": [
    "/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Templates.DeviceTemplates.Item.CreateDeviceFromTemplate;

var requestBody = new CreateDeviceFromTemplatePostRequestBody
{
	ExternalDeviceId = "2fa9424e-7ab0-4a22-8c90-2a20d15d8183",
	OperatingSystemVersion = "Ubuntu 18.04",
	ExternalSourceName = "unknown",
	AccountEnabled = false,
	AlternativeNames = new List<string>
	{
		"/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Templates.DeviceTemplates["{deviceTemplate-id}"].CreateDeviceFromTemplate.PostAsync(requestBody);
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
	  graphtemplates "github.com/microsoftgraph/msgraph-beta-sdk-go/templates"
	  //other-imports
)

requestBody := graphtemplates.NewCreateDeviceFromTemplatePostRequestBody()
externalDeviceId := "2fa9424e-7ab0-4a22-8c90-2a20d15d8183"
requestBody.SetExternalDeviceId(&externalDeviceId) 
operatingSystemVersion := "Ubuntu 18.04"
requestBody.SetOperatingSystemVersion(&operatingSystemVersion) 
externalSourceName := "unknown"
requestBody.SetExternalSourceName(&externalSourceName) 
accountEnabled := false
requestBody.SetAccountEnabled(&accountEnabled) 
alternativeNames := []string {
	"/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1",
}
requestBody.SetAlternativeNames(alternativeNames)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createDeviceFromTemplate, err := graphClient.Templates().DeviceTemplates().ByDeviceTemplateId("deviceTemplate-id").CreateDeviceFromTemplate().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.templates.devicetemplates.item.createdevicefromtemplate.CreateDeviceFromTemplatePostRequestBody createDeviceFromTemplatePostRequestBody = new com.microsoft.graph.beta.templates.devicetemplates.item.createdevicefromtemplate.CreateDeviceFromTemplatePostRequestBody();
createDeviceFromTemplatePostRequestBody.setExternalDeviceId("2fa9424e-7ab0-4a22-8c90-2a20d15d8183");
createDeviceFromTemplatePostRequestBody.setOperatingSystemVersion("Ubuntu 18.04");
createDeviceFromTemplatePostRequestBody.setExternalSourceName("unknown");
createDeviceFromTemplatePostRequestBody.setAccountEnabled(false);
LinkedList<String> alternativeNames = new LinkedList<String>();
alternativeNames.add("/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1");
createDeviceFromTemplatePostRequestBody.setAlternativeNames(alternativeNames);
Device result = graphClient.templates().deviceTemplates().byDeviceTemplateId("{deviceTemplate-id}").createDeviceFromTemplate().post(createDeviceFromTemplatePostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const device = {
  externalDeviceId: '2fa9424e-7ab0-4a22-8c90-2a20d15d8183',
  operatingSystemVersion: 'Ubuntu 18.04',
  externalSourceName: 'unknown',
  accountEnabled: false,
  alternativeNames: [
    '/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1'
  ]
};

await client.api('/templates/deviceTemplates/2d62b12a-0163-457d-9796-9602e9807e1/createDeviceFromTemplate')
	.version('beta')
	.post(device);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Templates\DeviceTemplates\Item\CreateDeviceFromTemplate\CreateDeviceFromTemplatePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateDeviceFromTemplatePostRequestBody();
$requestBody->setExternalDeviceId('2fa9424e-7ab0-4a22-8c90-2a20d15d8183');
$requestBody->setOperatingSystemVersion('Ubuntu 18.04');
$requestBody->setExternalSourceName('unknown');
$requestBody->setAccountEnabled(false);
$requestBody->setAlternativeNames(['/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1', 	]);

$result = $graphServiceClient->templates()->deviceTemplates()->byDeviceTemplateId('deviceTemplate-id')->createDeviceFromTemplate()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.templates.devicetemplates.item.create_device_from_template.create_device_from_template_post_request_body import CreateDeviceFromTemplatePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateDeviceFromTemplatePostRequestBody(
	external_device_id = "2fa9424e-7ab0-4a22-8c90-2a20d15d8183",
	operating_system_version = "Ubuntu 18.04",
	external_source_name = "unknown",
	account_enabled = False,
	alternative_names = [
		"/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1",
	],
)

result = await graph_client.templates.device_templates.by_device_template_id('deviceTemplate-id').create_device_from_template.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "06d59f74-dbf3-432a-9971-c5f60374e4f0",
  "accountEnabled": false,
  "alternativeNames": [
    "/subscriptions/00001111-aaaa-2222-bbbb-3333cccc4444/resourcegroups/testrg/providers/microsoft.deviceregistry/assets/asset1"
  ],
  "deviceId": "c6ca2657-8685-4398-9edc-a6a603f177b3",
  "displayName": "2fa9424e-7ab0-4a22-8c90-2a20d15d8183",
  "externalSourceName": "unknown",
  "manufacturer": "IoT Device Template Manufacturer",
  "model": "IoT Device Template Model",
  "operatingSystem": "WindowsIoT",
  "operatingSystemVersion": "Ubuntu 18.04",
  "physicalIds": [
    "[EXTID]:2fa9424e-7ab0-4a22-8c90-2a20d15d8183"
  ],
  "profileType": "IoT",
  "sourceType": "External",
  "alternativeSecurityIds": [
    {
      "type": 2,
      "identityProvider": null,
      "key": "WAA1ADAAOQA6ADwAVQB..."
    }
  ]
}
```
