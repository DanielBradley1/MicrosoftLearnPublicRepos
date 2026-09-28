<!-- Source: https://learn.microsoft.com/en-us/graph/api/authenticationmethoddevice-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-03 -->

# Create one or more hardwareOathTokenAuthenticationMethodDevice objects

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create one or more [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) objects. This API supports two scenarios:

- Create the new hardware tokens without assigning to users. You can then [assign to a user](https://learn.microsoft.com/en-us/graph/api/authentication-post-hardwareoathmethods?view=graph-rest-beta).
- Create and assign any individual hardware tokens to users in the same request.

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
PATCH /directory/authenticationMethodDevices/hardwareOathDevices
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
| timeIntervalInSeconds | Int32 | Refresh interval of the 6-digit verification code, in seconds. The possible values are: 30 or 60. Required. |
| hashFunction | hardwareOathTokenHashFunction | Hash function of the hardrware token. The possible values are: `hmacsha1` or `hmacsha256`. Default value is: `hmacsha1`. Optional. |
| assignTo | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | User ID if you want to directly assign the token to a user. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/directory/authenticationMethodDevices/hardwareOathDevices
Content-Type: application/json

{
  "@context": "#$delta",
  "value": [
    {
      "@contentId": "1",
      "serialNumber": "TOTP123456",
      "manufacturer": "Contoso",
      "model": "Hardware Token 1000",
      "secretKey": "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
      "timeIntervalInSeconds": "30",
      "hashFunction": "hmacsha1"
      },
      {
        "@contentId": "2",
        "serialNumber": "TOTP654321",
        "manufacturer": "Contoso",
        "model": "Hardware Token 1000",
        "secretKey": "TXYZAE6PJ4UZF3NNKIW3HQNFUF7WFTFB",
        "timeIntervalInSeconds": "30",
        "hashFunction": "hmacsha1",
        "assignTo": {
          "id": "0cadbf92-####-####-####-############"
          }
      }
   ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new HardwareOathTokenAuthenticationMethodDevice
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@context" , "#$delta"
		},
		{
			"value" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@contentId", new UntypedString("1")
					},
					{
						"serialNumber", new UntypedString("TOTP123456")
					},
					{
						"manufacturer", new UntypedString("Contoso")
					},
					{
						"model", new UntypedString("Hardware Token 1000")
					},
					{
						"secretKey", new UntypedString("6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB")
					},
					{
						"timeIntervalInSeconds", new UntypedString("30")
					},
					{
						"hashFunction", new UntypedString("hmacsha1")
					},
				}),
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"@contentId", new UntypedString("2")
					},
					{
						"serialNumber", new UntypedString("TOTP654321")
					},
					{
						"manufacturer", new UntypedString("Contoso")
					},
					{
						"model", new UntypedString("Hardware Token 1000")
					},
					{
						"secretKey", new UntypedString("TXYZAE6PJ4UZF3NNKIW3HQNFUF7WFTFB")
					},
					{
						"timeIntervalInSeconds", new UntypedString("30")
					},
					{
						"hashFunction", new UntypedString("hmacsha1")
					},
					{
						"assignTo", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"id", new UntypedString("0cadbf92-####-####-####-############")
							},
						})
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Directory.AuthenticationMethodDevices.HardwareOathDevices.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

HardwareOathTokenAuthenticationMethodDevice hardwareOathTokenAuthenticationMethodDevice = new HardwareOathTokenAuthenticationMethodDevice();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@context", "#$delta");
LinkedList<Object> value = new LinkedList<Object>();
 property = new ();
property.setContentId("1");
property.setSerialNumber("TOTP123456");
property.setManufacturer("Contoso");
property.setModel("Hardware Token 1000");
property.setSecretKey("6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB");
property.setTimeIntervalInSeconds("30");
property.setHashFunction("hmacsha1");
value.add(property);
 property1 = new ();
property1.setContentId("2");
property1.setSerialNumber("TOTP654321");
property1.setManufacturer("Contoso");
property1.setModel("Hardware Token 1000");
property1.setSecretKey("TXYZAE6PJ4UZF3NNKIW3HQNFUF7WFTFB");
property1.setTimeIntervalInSeconds("30");
property1.setHashFunction("hmacsha1");
 assignTo = new ();
assignTo.setId("0cadbf92-####-####-####-############");
property1.setAssignTo(assignTo);
value.add(property1);
additionalData.put("value", value);
hardwareOathTokenAuthenticationMethodDevice.setAdditionalData(additionalData);
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
  '@context': '#$delta',
  value: [
    {
      '@contentId': '1',
      serialNumber: 'TOTP123456',
      manufacturer: 'Contoso',
      model: 'Hardware Token 1000',
      secretKey: '6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB',
      timeIntervalInSeconds: '30',
      hashFunction: 'hmacsha1'
      },
      {
        '@contentId': '2',
        serialNumber: 'TOTP654321',
        manufacturer: 'Contoso',
        model: 'Hardware Token 1000',
        secretKey: 'TXYZAE6PJ4UZF3NNKIW3HQNFUF7WFTFB',
        timeIntervalInSeconds: '30',
        hashFunction: 'hmacsha1',
        assignTo: {
          id: '0cadbf92-####-####-####-############'
          }
      }
   ]
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


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new HardwareOathTokenAuthenticationMethodDevice();
$additionalData = [
	'@context' => '#$delta',
	'value' => [
			[
				'@contentId' => '1',
				'serialNumber' => 'TOTP123456',
				'manufacturer' => 'Contoso',
				'model' => 'Hardware Token 1000',
				'secretKey' => '6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB',
				'timeIntervalInSeconds' => '30',
				'hashFunction' => 'hmacsha1',
			],
			[
				'@contentId' => '2',
				'serialNumber' => 'TOTP654321',
				'manufacturer' => 'Contoso',
				'model' => 'Hardware Token 1000',
				'secretKey' => 'TXYZAE6PJ4UZF3NNKIW3HQNFUF7WFTFB',
				'timeIntervalInSeconds' => '30',
				'hashFunction' => 'hmacsha1',
				'assignTo' => [
					'id' => '0cadbf92-####-####-####-############',
				],
			],
		],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->directory()->authenticationMethodDevices()->hardwareOathDevices()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.DirectoryManagement

$params = @{
	"@context" = "#$delta"
	value = @(
		@{
			"@contentId" = "1"
			serialNumber = "TOTP123456"
			manufacturer = "Contoso"
			model = "Hardware Token 1000"
			secretKey = "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB"
			timeIntervalInSeconds = "30"
			hashFunction = "hmacsha1"
		}
		@{
			"@contentId" = "2"
			serialNumber = "TOTP654321"
			manufacturer = "Contoso"
			model = "Hardware Token 1000"
			secretKey = "TXYZAE6PJ4UZF3NNKIW3HQNFUF7WFTFB"
			timeIntervalInSeconds = "30"
			hashFunction = "hmacsha1"
			assignTo = @{
				id = "0cadbf92-####-####-####-############"
			}
		}
	)
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
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = HardwareOathTokenAuthenticationMethodDevice(
	additional_data = {
			"@context" : "#$delta",
			"value" : [
				{
						"@content_id" : "1",
						"serial_number" : "TOTP123456",
						"manufacturer" : "Contoso",
						"model" : "Hardware Token 1000",
						"secret_key" : "6PJ4UKIW33NNXYZAEHQNFUFTZF7WFTFB",
						"time_interval_in_seconds" : "30",
						"hash_function" : "hmacsha1",
				},
				{
						"@content_id" : "2",
						"serial_number" : "TOTP654321",
						"manufacturer" : "Contoso",
						"model" : "Hardware Token 1000",
						"secret_key" : "TXYZAE6PJ4UZF3NNKIW3HQNFUF7WFTFB",
						"time_interval_in_seconds" : "30",
						"hash_function" : "hmacsha1",
						"assign_to" : {
								"id" : "0cadbf92-####-####-####-############",
						},
				},
			],
	}
)

result = await graph_client.directory.authentication_method_devices.hardware_oath_devices.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.hardwareOathAuthenticationMethod",
      "id": "aad49556-####-####-####-############",
      "device": {
        "id": "aad49556-####-####-####-############",
        "displayName": null,
        "serialNumber": "TOTP123456",
        "manufacturer": "Contoso",
        "model": "Hardware Token 1000",
        "secretKey": null,
        "timeIntervalInSeconds": 30,
        "status": "available",
        "hashFunction": "hmacsha1",
        "assignedTo": null
      }
    },
    {
      "@odata.type": "#microsoft.graph.hardwareOathAuthenticationMethod",
      "id": "3dee0e53-####-####-####-############",
      "device": {
        "id": "3dee0e53-####-####-####-############",
        "displayName": null,
        "serialNumber": "TOTP654321",
        "manufacturer": "Contoso",
        "model": "Hardware Token 1000",
        "secretKey": null,
        "timeIntervalInSeconds": 30,
        "status": "assigned",
        "hashFunction": "hmacsha1",
        "assignedTo": {
            "id": "0cadbf92-####-####-####-############",
            "displayName": "Amy Masters"
        }
      }
    }
  ]
}
```
