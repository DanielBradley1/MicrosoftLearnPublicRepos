<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-deviceimages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Create cloudPcDeviceImage

Namespace: microsoft.graph

Create a new [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) object. Upload a custom OS image that you can later provision on Cloud PCs.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

> **Note:** When using application-only authentication, you need to grant the `Subscriptions.Read` permission to Windows 365 in advance. For more information, see [Customer permissions](https://learn.microsoft.com/en-us/windows-365/enterprise/customer-permissions).

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/deviceImages
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create a [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of this image. |
| sourceImageResourceId | String | The ID of the source image resource on Azure. The required ID format is: "/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Compute/images/{imageName}". |
| version | String | The image version. For example, `0.0.1` and `1.5.13`. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudPcDeviceImage](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdeviceimage?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/deviceImages
Content-Type: application/json

{
  "displayName": "ImageForDev",
  "version": "0.0.1",
  "sourceImageResourceId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CloudPcDeviceImage
{
	DisplayName = "ImageForDev",
	Version = "0.0.1",
	SourceImageResourceId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.DeviceImages.PostAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcDeviceImage()
displayName := "ImageForDev"
requestBody.SetDisplayName(&displayName) 
version := "0.0.1"
requestBody.SetVersion(&version) 
sourceImageResourceId := "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage"
requestBody.SetSourceImageResourceId(&sourceImageResourceId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
deviceImages, err := graphClient.DeviceManagement().VirtualEndpoint().DeviceImages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcDeviceImage cloudPcDeviceImage = new CloudPcDeviceImage();
cloudPcDeviceImage.setDisplayName("ImageForDev");
cloudPcDeviceImage.setVersion("0.0.1");
cloudPcDeviceImage.setSourceImageResourceId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage");
CloudPcDeviceImage result = graphClient.deviceManagement().virtualEndpoint().deviceImages().post(cloudPcDeviceImage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcDeviceImage = {
  displayName: 'ImageForDev',
  version: '0.0.1',
  sourceImageResourceId: '/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage'
};

await client.api('/deviceManagement/virtualEndpoint/deviceImages')
	.post(cloudPcDeviceImage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CloudPcDeviceImage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcDeviceImage();
$requestBody->setDisplayName('ImageForDev');
$requestBody->setVersion('0.0.1');
$requestBody->setSourceImageResourceId('/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->deviceImages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	displayName = "ImageForDev"
	version = "0.0.1"
	sourceImageResourceId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage"
}

New-MgDeviceManagementVirtualEndpointDeviceImage -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cloud_pc_device_image import CloudPcDeviceImage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcDeviceImage(
	display_name = "ImageForDev",
	version = "0.0.1",
	source_image_resource_id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImage",
)

result = await graph_client.device_management.virtual_endpoint.device_images.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#deviceManagement/virtualEndpoint/deviceImages/$entity",
  "id": "eda7ed64-7705-4079-9d08-c2bd883fffff",
  "displayName": "ImageForDev",
  "osBuildNumber": null,
  "operatingSystem": null,
  "version": "0.0.1",
  "sourceImageResourceId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/Example/providers/Microsoft.Compute/images/exampleImageForDev",
  "lastModifiedDateTime": "2023-11-03T07:03:44.97Z",
  "status": "pending",
  "errorCode": null,
  "osStatus": null,
  "expirationDate": null,
  "osVersionNumber": null,
  "sizeInGB": 64
}
```
