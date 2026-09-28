<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationmethoddevice-post-hardwareoathdevices?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-03 -->

# Create hardwareOathTokenAuthenticationMethodDevice

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) object. This API supports two scenarios:

- Create the new hardware token without assigning to a user. You can then [assign to a user](https://learn.microsoft.com/en-us/graph/api/authentication-post-hardwareoathmethods?view=graph-rest-beta).
- Create and assign a hardware token to a user in the same request.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.AuthenticationMethod | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.AuthenticationMethod | Not available. |

Important

When using delegated permissions with work or school accounts, the signed-in user must have an appropriate [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with the necessary permissions. The least privileged built-in role required for this operation is *Authentication Policy Administrator*.

To create and assign a hardware OATH token to a user in a single request, the signed-in user must also have:

- The *UserAuthenticationMethod.ReadWrite.All* delegated permission.
- Either *Authentication Administrator* \(least privileged role for assigning hardware tokens to nonadmin users\) or *Privileged Authentication Administrator* \(least privileged role for assigning hardware tokens to admin users\) role.

## HTTP request

```http
POST /directory/authenticationMethodDevices/hardwareOathDevices
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) object.

You can specify the following properties when creating a **hardwareOathTokenAuthenticationMethodDevice**.

| Property | Type | Description |
| :--- | :--- | :--- |
| serialNumber | String | Serial number of the specific hardware token, often found on the back of the device. Required. |
| manufacturer | String | Manufacturer name of the hardware token. Required. |
| model | String | Model name of the hardware token. Required. |
| secretKey | String | Secret key of the specific hardware token, provided by the vendor. Required. |
| timeIntervalInSeconds | Int32 | Refresh interval of the six-digit verification code, in seconds. The possible values are: 30 or 60. Required. |
| hashFunction | hardwareOathTokenHashFunction | Hash function of the hardware token. The possible values are: `hmacsha1` or `hmacsha256`. Default value is: `hmacsha1`. Optional. |
| assignTo | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | User ID if you want to directly assign the token to a user. Optional. |
| displayName | String | Name that can be provided to the Hardware OATH token. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) object in the response body.

## Examples

### Example 1: Create a token without user assignment

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
POST https://graph.microsoft.com/beta/directory/authenticationMethodDevices/hardwareOathDevices
Content-Type: application/json

{
  "displayName": "Token 1",
  "serialNumber": "TOTP123456",
  "manufacturer": "Contoso",
  "model": "Hardware Token 1000",
  "secretKey": "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
  "timeIntervalInSeconds": 30,
  "hashFunction": "hmacsha1"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new HardwareOathTokenAuthenticationMethodDevice
{
	DisplayName = "Token 1",
	SerialNumber = "TOTP123456",
	Manufacturer = "Contoso",
	Model = "Hardware Token 1000",
	SecretKey = "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
	TimeIntervalInSeconds = 30,
	HashFunction = HardwareOathTokenHashFunction.Hmacsha1,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.AuthenticationMethodDevices.HardwareOathDevices.PostAsync(requestBody);
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

requestBody := graphmodels.NewHardwareOathTokenAuthenticationMethodDevice()
displayName := "Token 1"
requestBody.SetDisplayName(&displayName) 
serialNumber := "TOTP123456"
requestBody.SetSerialNumber(&serialNumber) 
manufacturer := "Contoso"
requestBody.SetManufacturer(&manufacturer) 
model := "Hardware Token 1000"
requestBody.SetModel(&model) 
secretKey := "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB"
requestBody.SetSecretKey(&secretKey) 
timeIntervalInSeconds := int32(30)
requestBody.SetTimeIntervalInSeconds(&timeIntervalInSeconds) 
hashFunction := graphmodels.HMACSHA1_HARDWAREOATHTOKENHASHFUNCTION 
requestBody.SetHashFunction(&hashFunction) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
hardwareOathDevices, err := graphClient.Directory().AuthenticationMethodDevices().HardwareOathDevices().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

HardwareOathTokenAuthenticationMethodDevice hardwareOathTokenAuthenticationMethodDevice = new HardwareOathTokenAuthenticationMethodDevice();
hardwareOathTokenAuthenticationMethodDevice.setDisplayName("Token 1");
hardwareOathTokenAuthenticationMethodDevice.setSerialNumber("TOTP123456");
hardwareOathTokenAuthenticationMethodDevice.setManufacturer("Contoso");
hardwareOathTokenAuthenticationMethodDevice.setModel("Hardware Token 1000");
hardwareOathTokenAuthenticationMethodDevice.setSecretKey("6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB");
hardwareOathTokenAuthenticationMethodDevice.setTimeIntervalInSeconds(30);
hardwareOathTokenAuthenticationMethodDevice.setHashFunction(HardwareOathTokenHashFunction.Hmacsha1);
HardwareOathTokenAuthenticationMethodDevice result = graphClient.directory().authenticationMethodDevices().hardwareOathDevices().post(hardwareOathTokenAuthenticationMethodDevice);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const hardwareOathTokenAuthenticationMethodDevice = {
  displayName: 'Token 1',
  serialNumber: 'TOTP123456',
  manufacturer: 'Contoso',
  model: 'Hardware Token 1000',
  secretKey: '6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB',
  timeIntervalInSeconds: 30,
  hashFunction: 'hmacsha1'
};

await client.api('/directory/authenticationMethodDevices/hardwareOathDevices')
	.version('beta')
	.post(hardwareOathTokenAuthenticationMethodDevice);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\HardwareOathTokenAuthenticationMethodDevice;
use Microsoft\Graph\Beta\Generated\Models\HardwareOathTokenHashFunction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new HardwareOathTokenAuthenticationMethodDevice();
$requestBody->setDisplayName('Token 1');
$requestBody->setSerialNumber('TOTP123456');
$requestBody->setManufacturer('Contoso');
$requestBody->setModel('Hardware Token 1000');
$requestBody->setSecretKey('6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB');
$requestBody->setTimeIntervalInSeconds(30);
$requestBody->setHashFunction(new HardwareOathTokenHashFunction('hmacsha1'));

$result = $graphServiceClient->directory()->authenticationMethodDevices()->hardwareOathDevices()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	displayName = "Token 1"
	serialNumber = "TOTP123456"
	manufacturer = "Contoso"
	model = "Hardware Token 1000"
	secretKey = "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB"
	timeIntervalInSeconds = 30
	hashFunction = "hmacsha1"
}

New-MgBetaDirectoryAuthenticationMethodDeviceHardwareOathDevice -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.hardware_oath_token_authentication_method_device import HardwareOathTokenAuthenticationMethodDevice
from msgraph_beta.generated.models.hardware_oath_token_hash_function import HardwareOathTokenHashFunction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = HardwareOathTokenAuthenticationMethodDevice(
	display_name = "Token 1",
	serial_number = "TOTP123456",
	manufacturer = "Contoso",
	model = "Hardware Token 1000",
	secret_key = "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
	time_interval_in_seconds = 30,
	hash_function = HardwareOathTokenHashFunction.Hmacsha1,
)

result = await graph_client.directory.authentication_method_devices.hardware_oath_devices.post(request_body)
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
  "@odata.type": "#microsoft.graph.hardwareOathTokenAuthenticationMethodDevice",
  "id": "9b037532-f999-1ed9-13fd-849ffb995e11",
  "displayName": "Token 1",
  "serialNumber": "TOTP123456",
  "manufacturer": "Contoso",
  "model": "Hardware Token 1000",
  "secretKey": null,
  "timeIntervalInSeconds": 30,
  "status": "available",
  "lastUsedDateTime": null,
  "assignedTo": null,
  "hashFunction": "hmacsha1"
}
```

### Example 2: Create a token and assign it to a user

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
POST https://graph.microsoft.com/beta/directory/authenticationMethodDevices/hardwareOathDevices
Content-Type: application/json

{
  "displayName": "Token 1",
  "serialNumber": "TOTP123456",
  "manufacturer": "Contoso",
  "model": "Hardware Token 1000",
  "secretKey": "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
  "timeIntervalInSeconds": 30,
  "hashFunction": "hmacsha1",
  "assignTo": {
    "id": "0cadbf92-####-####-####-############"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new HardwareOathTokenAuthenticationMethodDevice
{
	DisplayName = "Token 1",
	SerialNumber = "TOTP123456",
	Manufacturer = "Contoso",
	Model = "Hardware Token 1000",
	SecretKey = "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
	TimeIntervalInSeconds = 30,
	HashFunction = HardwareOathTokenHashFunction.Hmacsha1,
	AssignTo = new User
	{
		Id = "0cadbf92-####-####-####-############",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.AuthenticationMethodDevices.HardwareOathDevices.PostAsync(requestBody);
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

requestBody := graphmodels.NewHardwareOathTokenAuthenticationMethodDevice()
displayName := "Token 1"
requestBody.SetDisplayName(&displayName) 
serialNumber := "TOTP123456"
requestBody.SetSerialNumber(&serialNumber) 
manufacturer := "Contoso"
requestBody.SetManufacturer(&manufacturer) 
model := "Hardware Token 1000"
requestBody.SetModel(&model) 
secretKey := "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB"
requestBody.SetSecretKey(&secretKey) 
timeIntervalInSeconds := int32(30)
requestBody.SetTimeIntervalInSeconds(&timeIntervalInSeconds) 
hashFunction := graphmodels.HMACSHA1_HARDWAREOATHTOKENHASHFUNCTION 
requestBody.SetHashFunction(&hashFunction) 
assignTo := graphmodels.NewUser()
id := "0cadbf92-####-####-####-############"
assignTo.SetId(&id) 
requestBody.SetAssignTo(assignTo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
hardwareOathDevices, err := graphClient.Directory().AuthenticationMethodDevices().HardwareOathDevices().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

HardwareOathTokenAuthenticationMethodDevice hardwareOathTokenAuthenticationMethodDevice = new HardwareOathTokenAuthenticationMethodDevice();
hardwareOathTokenAuthenticationMethodDevice.setDisplayName("Token 1");
hardwareOathTokenAuthenticationMethodDevice.setSerialNumber("TOTP123456");
hardwareOathTokenAuthenticationMethodDevice.setManufacturer("Contoso");
hardwareOathTokenAuthenticationMethodDevice.setModel("Hardware Token 1000");
hardwareOathTokenAuthenticationMethodDevice.setSecretKey("6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB");
hardwareOathTokenAuthenticationMethodDevice.setTimeIntervalInSeconds(30);
hardwareOathTokenAuthenticationMethodDevice.setHashFunction(HardwareOathTokenHashFunction.Hmacsha1);
User assignTo = new User();
assignTo.setId("0cadbf92-####-####-####-############");
hardwareOathTokenAuthenticationMethodDevice.setAssignTo(assignTo);
HardwareOathTokenAuthenticationMethodDevice result = graphClient.directory().authenticationMethodDevices().hardwareOathDevices().post(hardwareOathTokenAuthenticationMethodDevice);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const hardwareOathTokenAuthenticationMethodDevice = {
  displayName: 'Token 1',
  serialNumber: 'TOTP123456',
  manufacturer: 'Contoso',
  model: 'Hardware Token 1000',
  secretKey: '6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB',
  timeIntervalInSeconds: 30,
  hashFunction: 'hmacsha1',
  assignTo: {
    id: '0cadbf92-####-####-####-############'
    }
};

await client.api('/directory/authenticationMethodDevices/hardwareOathDevices')
	.version('beta')
	.post(hardwareOathTokenAuthenticationMethodDevice);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\HardwareOathTokenAuthenticationMethodDevice;
use Microsoft\Graph\Beta\Generated\Models\HardwareOathTokenHashFunction;
use Microsoft\Graph\Beta\Generated\Models\User;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new HardwareOathTokenAuthenticationMethodDevice();
$requestBody->setDisplayName('Token 1');
$requestBody->setSerialNumber('TOTP123456');
$requestBody->setManufacturer('Contoso');
$requestBody->setModel('Hardware Token 1000');
$requestBody->setSecretKey('6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB');
$requestBody->setTimeIntervalInSeconds(30);
$requestBody->setHashFunction(new HardwareOathTokenHashFunction('hmacsha1'));
$assignTo = new User();
$assignTo->setId('0cadbf92-####-####-####-############');
$requestBody->setAssignTo($assignTo);

$result = $graphServiceClient->directory()->authenticationMethodDevices()->hardwareOathDevices()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	displayName = "Token 1"
	serialNumber = "TOTP123456"
	manufacturer = "Contoso"
	model = "Hardware Token 1000"
	secretKey = "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB"
	timeIntervalInSeconds = 30
	hashFunction = "hmacsha1"
	assignTo = @{
		id = "0cadbf92-####-####-####-############"
	}
}

New-MgBetaDirectoryAuthenticationMethodDeviceHardwareOathDevice -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.hardware_oath_token_authentication_method_device import HardwareOathTokenAuthenticationMethodDevice
from msgraph_beta.generated.models.hardware_oath_token_hash_function import HardwareOathTokenHashFunction
from msgraph_beta.generated.models.user import User
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = HardwareOathTokenAuthenticationMethodDevice(
	display_name = "Token 1",
	serial_number = "TOTP123456",
	manufacturer = "Contoso",
	model = "Hardware Token 1000",
	secret_key = "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
	time_interval_in_seconds = 30,
	hash_function = HardwareOathTokenHashFunction.Hmacsha1,
	assign_to = User(
		id = "0cadbf92-####-####-####-############",
	),
)

result = await graph_client.directory.authentication_method_devices.hardware_oath_devices.post(request_body)
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
  "@odata.type": "#microsoft.graph.hardwareOathTokenAuthenticationMethodDevice",
  "id": "9b037532-f999-1ed9-13fd-849ffb995e11",
  "displayName": "Token 1",
  "serialNumber": "TOTP123456",
  "manufacturer": "Contoso",
  "model": "Hardware Token 1000",
  "secretKey": null,
  "timeIntervalInSeconds": 30,
  "status": "assigned",
  "lastUsedDateTime": null,
  "assignedTo": null,
  "hashFunction": "hmacsha1",
  "assignedTo": {
    "id": "0cadbf92-####-####-####-############",
    "displayName": "Amy Masters"
    }
}
```
