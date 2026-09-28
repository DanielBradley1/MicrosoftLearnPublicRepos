<!-- Source: https://learn.microsoft.com/en-us/graph/api/printer-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# printer: create

Namespace: microsoft.graph

Create \(register\) a printer with the Universal Print service. This is a long-running operation and as such, it returns a [printerCreateOperation](https://learn.microsoft.com/en-us/graph/api/resources/printercreateoperation?view=graph-rest-1.0) that can be used to track and verify the registration of the printer.

For help creating the required Certificate Signing Request \(CSR\) for creating printer, see the [CSR generation code sample](https://learn.microsoft.com/en-us/universal-print/hardware/universal-print-oem-certificate-signing-request).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Printer.Create | Printer.FullControl.All, Printer.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /print/printers/create
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description | Required? |
| :--- | :--- | :--- | :--- |
| displayName | String | The display name to assign to the printer. | Yes |
| manufacturer | String | The manufacturer of the printer. | Yes |
| model | String | The model of the printer. | Yes |
| physicalDeviceId | String | The physical device UUID of the printer. Required if the `hasPhysicalDevice` property is true. | No |
| hasPhysicalDevice | Boolean | True if the printer has physical output device, false otherwise. If omitted, the default value is true. | No |
| certificateSigningRequest | [printCertificateSigningRequest](https://learn.microsoft.com/en-us/graph/api/resources/printcertificatesigningrequest?view=graph-rest-1.0) | The X.509 Certificate Signing Request \(CSR\) for the certificate created and used by the printer to identify itself. | Yes |
| connectorId | String | ID of the connector acting as proxy to the printer. | No |

## Response

If successful, this method returns a `202 Accepted` response code and a link to the associated [printerCreateOperation](https://learn.microsoft.com/en-us/graph/api/resources/printercreateoperation?view=graph-rest-1.0) in the `Operation-Location` header.

You make a GET request to the linked URL to get the status of an ongoing printer registration. After printer registration has completed successfully, a GET request to the linked URL will contain the created printer object and registered certificate.

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
POST https://graph.microsoft.com/v1.0/print/printers/create
Content-Type: application/json

{
  "displayName": "Test Printer",
  "manufacturer": "Test Printer Manufacturer",
  "model": "Test Printer Model",
  "physicalDeviceId": null,
  "hasPhysicalDevice": false,
  "certificateSigningRequest": { 
    "content": "{content}",
    "transportKey": "{sampleTransportKey}"
  },
  "connectorId": null
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Print.Printers.Create;
using Microsoft.Graph.Models;

var requestBody = new CreatePostRequestBody
{
	DisplayName = "Test Printer",
	Manufacturer = "Test Printer Manufacturer",
	Model = "Test Printer Model",
	PhysicalDeviceId = null,
	HasPhysicalDevice = false,
	CertificateSigningRequest = new PrintCertificateSigningRequest
	{
		Content = "{content}",
		TransportKey = "{sampleTransportKey}",
	},
	ConnectorId = null,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Print.Printers.Create.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphprint "github.com/microsoftgraph/msgraph-sdk-go/print"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphprint.NewCreatePostRequestBody()
displayName := "Test Printer"
requestBody.SetDisplayName(&displayName) 
manufacturer := "Test Printer Manufacturer"
requestBody.SetManufacturer(&manufacturer) 
model := "Test Printer Model"
requestBody.SetModel(&model) 
physicalDeviceId := null
requestBody.SetPhysicalDeviceId(&physicalDeviceId) 
hasPhysicalDevice := false
requestBody.SetHasPhysicalDevice(&hasPhysicalDevice) 
certificateSigningRequest := graphmodels.NewPrintCertificateSigningRequest()
content := "{content}"
certificateSigningRequest.SetContent(&content) 
transportKey := "{sampleTransportKey}"
certificateSigningRequest.SetTransportKey(&transportKey) 
requestBody.SetCertificateSigningRequest(certificateSigningRequest)
connectorId := null
requestBody.SetConnectorId(&connectorId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Print().Printers().Create().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.print.printers.create.CreatePostRequestBody createPostRequestBody = new com.microsoft.graph.print.printers.create.CreatePostRequestBody();
createPostRequestBody.setDisplayName("Test Printer");
createPostRequestBody.setManufacturer("Test Printer Manufacturer");
createPostRequestBody.setModel("Test Printer Model");
createPostRequestBody.setPhysicalDeviceId(null);
createPostRequestBody.setHasPhysicalDevice(false);
PrintCertificateSigningRequest certificateSigningRequest = new PrintCertificateSigningRequest();
certificateSigningRequest.setContent("{content}");
certificateSigningRequest.setTransportKey("{sampleTransportKey}");
createPostRequestBody.setCertificateSigningRequest(certificateSigningRequest);
createPostRequestBody.setConnectorId(null);
graphClient.print().printers().create().post(createPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const create = {
  displayName: 'Test Printer',
  manufacturer: 'Test Printer Manufacturer',
  model: 'Test Printer Model',
  physicalDeviceId: null,
  hasPhysicalDevice: false,
  certificateSigningRequest: { 
    content: '{content}',
    transportKey: '{sampleTransportKey}'
  },
  connectorId: null
};

await client.api('/print/printers/create')
	.post(create);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Print\Printers\Create\CreatePostRequestBody;
use Microsoft\Graph\Generated\Models\PrintCertificateSigningRequest;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreatePostRequestBody();
$requestBody->setDisplayName('Test Printer');
$requestBody->setManufacturer('Test Printer Manufacturer');
$requestBody->setModel('Test Printer Model');
$requestBody->setPhysicalDeviceId(null);
$requestBody->setHasPhysicalDevice(false);
$certificateSigningRequest = new PrintCertificateSigningRequest();
$certificateSigningRequest->setContent('{content}');
$certificateSigningRequest->setTransportKey('{sampleTransportKey}');
$requestBody->setCertificateSigningRequest($certificateSigningRequest);
$requestBody->setConnectorId(null);

$graphServiceClient->escapedPrint()->printers()->create()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Devices.CloudPrint

$params = @{
	displayName = "Test Printer"
	manufacturer = "Test Printer Manufacturer"
	model = "Test Printer Model"
	physicalDeviceId = $null
	hasPhysicalDevice = $false
	certificateSigningRequest = @{
		content = '{content}'
		transportKey = '{sampleTransportKey}'
	}
	connectorId = $null
}

New-MgPrintPrinter -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.print.printers.create.create_post_request_body import CreatePostRequestBody
from msgraph.generated.models.print_certificate_signing_request import PrintCertificateSigningRequest
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreatePostRequestBody(
	display_name = "Test Printer",
	manufacturer = "Test Printer Manufacturer",
	model = "Test Printer Model",
	physical_device_id = None,
	has_physical_device = False,
	certificate_signing_request = PrintCertificateSigningRequest(
		content = "{content}",
		transport_key = "{sampleTransportKey}",
	),
	connector_id = None,
)

await graph_client.print.printers.create.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 202 Accepted
Operation-Location: https://graph.microsoft.com/v1.0/print/operations/f221760a-52e8-4c11-b8c5-5dfaef3a49db
Retry-After: 5
```
