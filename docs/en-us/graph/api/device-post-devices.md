<!-- Source: https://learn.microsoft.com/en-us/graph/api/device-post-devices?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create device

Namespace: microsoft.graph

Create and register a new device in the organization.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Directory.AccessAsUser.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Intune Administrator
- Windows 365 Administrator

## HTTP request

```http
POST /devices
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json |

## Request body

In the request body, supply a JSON representation of [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) object.

## Response

If successful, this method returns `201 Created` response code and [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) object in the response body.

## Example

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
POST https://graph.microsoft.com/v1.0/devices
Content-type: application/json

{
  "accountEnabled":false,
  "alternativeSecurityIds":
  [
    {
      "type":2,
      "key":"base64Y3YxN2E1MWFlYw=="
    }
  ],
  "deviceId":"4c299165-6e8f-4b45-a5ba-c5d250a707ff",
  "displayName":"Test device",
  "operatingSystem":"linux",
  "operatingSystemVersion":"1"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Device
{
	AccountEnabled = false,
	AlternativeSecurityIds = new List<AlternativeSecurityId>
	{
		new AlternativeSecurityId
		{
			Type = 2,
			Key = Convert.FromBase64String("base64Y3YxN2E1MWFlYw=="),
		},
	},
	DeviceId = "4c299165-6e8f-4b45-a5ba-c5d250a707ff",
	DisplayName = "Test device",
	OperatingSystem = "linux",
	OperatingSystemVersion = "1",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Devices.PostAsync(requestBody);
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

requestBody := graphmodels.NewDevice()
accountEnabled := false
requestBody.SetAccountEnabled(&accountEnabled) 


alternativeSecurityId := graphmodels.NewAlternativeSecurityId()
type := int32(2)
alternativeSecurityId.SetType(&type) 
key := []byte("base64Y3YxN2E1MWFlYw==")
alternativeSecurityId.SetKey(&key) 

alternativeSecurityIds := []graphmodels.AlternativeSecurityIdable {
	alternativeSecurityId,
}
requestBody.SetAlternativeSecurityIds(alternativeSecurityIds)
deviceId := "4c299165-6e8f-4b45-a5ba-c5d250a707ff"
requestBody.SetDeviceId(&deviceId) 
displayName := "Test device"
requestBody.SetDisplayName(&displayName) 
operatingSystem := "linux"
requestBody.SetOperatingSystem(&operatingSystem) 
operatingSystemVersion := "1"
requestBody.SetOperatingSystemVersion(&operatingSystemVersion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
devices, err := graphClient.Devices().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Device device = new Device();
device.setAccountEnabled(false);
LinkedList<AlternativeSecurityId> alternativeSecurityIds = new LinkedList<AlternativeSecurityId>();
AlternativeSecurityId alternativeSecurityId = new AlternativeSecurityId();
alternativeSecurityId.setType(2);
byte[] key = Base64.getDecoder().decode("base64Y3YxN2E1MWFlYw==");
alternativeSecurityId.setKey(key);
alternativeSecurityIds.add(alternativeSecurityId);
device.setAlternativeSecurityIds(alternativeSecurityIds);
device.setDeviceId("4c299165-6e8f-4b45-a5ba-c5d250a707ff");
device.setDisplayName("Test device");
device.setOperatingSystem("linux");
device.setOperatingSystemVersion("1");
Device result = graphClient.devices().post(device);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const device = {
  accountEnabled: false,
  alternativeSecurityIds: 
  [
    {
      type: 2,
      key: 'base64Y3YxN2E1MWFlYw=='
    }
  ],
  deviceId: '4c299165-6e8f-4b45-a5ba-c5d250a707ff',
  displayName: 'Test device',
  operatingSystem: 'linux',
  operatingSystemVersion: '1'
};

await client.api('/devices')
	.post(device);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Device;
use Microsoft\Graph\Generated\Models\AlternativeSecurityId;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Device();
$requestBody->setAccountEnabled(false);
$alternativeSecurityIdsAlternativeSecurityId1 = new AlternativeSecurityId();
$alternativeSecurityIdsAlternativeSecurityId1->setType(2);
$alternativeSecurityIdsAlternativeSecurityId1->setKey(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('base64Y3YxN2E1MWFlYw==')));
$alternativeSecurityIdsArray []= $alternativeSecurityIdsAlternativeSecurityId1;
$requestBody->setAlternativeSecurityIds($alternativeSecurityIdsArray);

$requestBody->setDeviceId('4c299165-6e8f-4b45-a5ba-c5d250a707ff');
$requestBody->setDisplayName('Test device');
$requestBody->setOperatingSystem('linux');
$requestBody->setOperatingSystemVersion('1');

$result = $graphServiceClient->devices()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

$params = @{
	accountEnabled = $false
	alternativeSecurityIds = @(
		@{
			type = 2
			key = [System.Text.Encoding]::ASCII.GetBytes("base64Y3YxN2E1MWFlYw==")
		}
	)
	deviceId = "4c299165-6e8f-4b45-a5ba-c5d250a707ff"
	displayName = "Test device"
	operatingSystem = "linux"
	operatingSystemVersion = "1"
}

New-MgDevice -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.device import Device
from msgraph.generated.models.alternative_security_id import AlternativeSecurityId
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Device(
	account_enabled = False,
	alternative_security_ids = [
		AlternativeSecurityId(
			type = 2,
			key = base64.urlsafe_b64decode("base64Y3YxN2E1MWFlYw=="),
		),
	],
	device_id = "4c299165-6e8f-4b45-a5ba-c5d250a707ff",
	display_name = "Test device",
	operating_system = "linux",
	operating_system_version = "1",
)

result = await graph_client.devices.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) object.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "accountEnabled":false,
  "alternativeSecurityIds":
  [
    {
      "type":2,
      "key":"base64Y3YxN2E1MWFlYw=="
    }
  ],
  "deviceId":"4c299165-6e8f-4b45-a5ba-c5d250a707ff",
  "displayName":"Test device",
  "id": "id-value",
  "operatingSystem":"linux",
  "operatingSystemVersion":"1"
}
```
