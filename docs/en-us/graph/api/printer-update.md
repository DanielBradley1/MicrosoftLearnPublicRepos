<!-- Source: https://learn.microsoft.com/en-us/graph/api/printer-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update printer

Namespace: microsoft.graph

Update the properties of a [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Printer.ReadWrite.All | Printer.FullControl.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Printer.ReadWrite.All | Not available. |

> **Note:** Right now, only printers that don't have physical devices can be updated using application permissions.

## HTTP request

```http
PATCH /print/printers/{printerId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | `application/json` when using delegated permissions, `application/ipp` or `application/json` when using application permissions. Required. |

## Request body

### Delegated permissions and JSON payload

If using delegated permissions, in the request body, supply the values for the relevant [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) fields that should be updated. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

The following properties can be updated using delegated permissions.

| Property | Type | Description |
| :--- | :--- | :--- |
| defaults | [printerDefaults](https://learn.microsoft.com/en-us/graph/api/resources/printerdefaults?view=graph-rest-1.0) | The printer's default print settings. |
| location | [printerLocation](https://learn.microsoft.com/en-us/graph/api/resources/printerlocation?view=graph-rest-1.0) | The physical and/or organizational location of the printer. |
| displayName | String | The name of the printer. |

### Application permissions and JSON payload

In the request body, supply the values for the relevant [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) fields that should be updated. Existing properties that aren't included in the request body maintain their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

The following properties can be updated using application permissions.

| Property | Type | Description |
| :--- | :--- | :--- |
| defaults | [printerDefaults](https://learn.microsoft.com/en-us/graph/api/resources/printerdefaults?view=graph-rest-1.0) | The printer's default print settings. |
| capabilities | [printerCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/printercapabilities?view=graph-rest-1.0) | The capabilities of the printer associated with this printer share. |
| displayName | String | The name of the printer. |
| manufacturer | String | The manufacturer of the printer. |
| model | String | The model name of the printer. |
| status | [printerStatus](https://learn.microsoft.com/en-us/graph/api/resources/printerstatus?view=graph-rest-1.0) | The processing status of the printer, including any errors. |
| isAcceptingJobs | Boolean | Whether the printer is currently accepting new print jobs. |

### Application permissions and IPP payload

With application permissions, a printer can also be updated using an Internet Printing Protocol \(IPP\) payload. In this case, the request body contains a binary stream that represents the Printer Attributes group in [IPP encoding](https://tools.ietf.org/html/rfc8010).

The client MUST supply a set of Printer attributes with one or more values \(including explicitly allowed out-of-band values\) as defined in [RFC8011 section 5.2](https://tools.ietf.org/html/rfc8011#section-5.2) Job Template Attributes \("xxx-default", "xxx-supported", and "xxx-ready" attributes\), [Section 5.4](https://tools.ietf.org/html/rfc8011#section-5.4) Printer Description Attributes. The client must also supply any attribute extensions supported by the Printer. The value\(s\) of each Printer attribute supplied replaces the value\(s\) of the corresponding Printer attribute on the target Printer object. For attributes that can have multiple values \(1setOf\), all values supplied by the client replace all values of the corresponding Printer object attribute.

> **Note:** Don't pass operation attributes in the request body. The request body should only contain printer attributes.

> **Note:** For printers to work with a particular platform, it should meet the requirements of that platform. For example, on the Windows client, it is expected that the printer specifies all attributes that are considered mandatory as per [MOPRIA](https://mopria.org) specs. Please note MOPRIA specs are available to only the paid members of MOPRIA.

## Response

### Delegated permissions and JSON payload

If using delegated permissions, if successful, this method returns a `200 OK` response code and an updated [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) object in the response body.

### Application permissions and JSON payload

If using delegated permissions, if successful, this method returns a `200 OK` response code and an updated [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) object in the response body.

### Application permissions and IPP payload

If using application permissions, if successful, this method returns a `204 No content` response code. It doesn't return anything in the response body.

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
PATCH https://graph.microsoft.com/v1.0/print/printers/{printerId}
Content-Type: application/json

{
  "name": "PrinterName",
  "location": {
    "latitude": 1.1,
    "longitude": 2.2,
    "altitudeInMeters": 3
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Printer
{
	Location = new PrinterLocation
	{
		Latitude = 1.1d,
		Longitude = 2.2d,
		AltitudeInMeters = 3,
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"name" , "PrinterName"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Print.Printers["{printer-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewPrinter()
location := graphmodels.NewPrinterLocation()
latitude := float64(1.1)
location.SetLatitude(&latitude) 
longitude := float64(2.2)
location.SetLongitude(&longitude) 
altitudeInMeters := int32(3)
location.SetAltitudeInMeters(&altitudeInMeters) 
requestBody.SetLocation(location)
additionalData := map[string]interface{}{
	"name" : "PrinterName", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
printers, err := graphClient.Print().Printers().ByPrinterId("printer-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Printer printer = new Printer();
PrinterLocation location = new PrinterLocation();
location.setLatitude(1.1d);
location.setLongitude(2.2d);
location.setAltitudeInMeters(3);
printer.setLocation(location);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("name", "PrinterName");
printer.setAdditionalData(additionalData);
Printer result = graphClient.print().printers().byPrinterId("{printer-id}").patch(printer);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const printer = {
  name: 'PrinterName',
  location: {
    latitude: 1.1,
    longitude: 2.2,
    altitudeInMeters: 3
  }
};

await client.api('/print/printers/{printerId}')
	.update(printer);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Printer;
use Microsoft\Graph\Generated\Models\PrinterLocation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Printer();
$location = new PrinterLocation();
$location->setLatitude(1.1);
$location->setLongitude(2.2);
$location->setAltitudeInMeters(3);
$requestBody->setLocation($location);
$additionalData = [
	'name' => 'PrinterName',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->escapedPrint()->printers()->byPrinterId('printer-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.printer import Printer
from msgraph.generated.models.printer_location import PrinterLocation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Printer(
	location = PrinterLocation(
		latitude = 1.1,
		longitude = 2.2,
		altitude_in_meters = 3,
	),
	additional_data = {
			"name" : "PrinterName",
	}
)

result = await graph_client.print.printers.by_printer_id('printer-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response. **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#print/printers/$entity",
  "id": "016b5565-3bbf-4067-b9ff-4d68167eb1a6",
  "displayName": "PrinterName",
  "manufacturer": "PrinterManufacturer",
  "model": "PrinterModel",
  "isShared": true,
  "registeredDateTime": "2020-02-04T00:00:00.0000000Z",
  "isAcceptingJobs": true,
  "status": {
    "state": "idle",
    "details": [],
    "description": ""
  },
  "defaults": {
    "copiesPerJob":1,
    "contentType": "application/oxps",
    "finishings": ["none"],
    "mediaType": "stationery"
  },
  "location": {
    "latitude": 1.1,
    "longitude": 2.2,
    "altitudeInMeters": 3,
    "streetAddress": "One Microsoft Way",
    "subUnit": [
        "Main Plaza",
        "Unit 400"
    ],
    "city": "Redmond",
    "postalCode": "98052",
    "countryOrRegion": "USA",
    "site": "Puget Sound",
    "building": "Studio E",
    "floor": "1",
    "floorDescription": "First Floor",
    "roomName": "1234",
    "roomDescription": "First floor copy room",
    "organization": [
        "C+AI",
        "Microsoft Graph"
    ],
    "subdivision": [
        "King County",
        "Red West"
    ],
    "stateOrProvince": "Washington"
  }
}
```
