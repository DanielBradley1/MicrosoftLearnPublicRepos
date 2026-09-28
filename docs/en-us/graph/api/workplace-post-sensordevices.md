<!-- Source: https://learn.microsoft.com/en-us/graph/api/workplace-post-sensordevices?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-17 -->

# Create workplaceSensorDevice

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new workplace sensor device.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

For an app with delegated permissions to write workplace devices, the signed-in user must be a member of the **TenantPlacesManagement** Exchange Online administrator role.

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PlaceDevice.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PlaceDevice.ReadWrite.All | Not available. |

## HTTP request

```http
POST /workplace/sensorDevices
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) object.

You can specify the following properties when you create a **workplaceSensorDevice**.

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the device. Optional. |
| deviceId | String | The user-defined unique identifier of the device provided at the time of creation. Required. |
| displayName | String | The display name of the device. Optional. |
| ipV4Address | String | The IPv4 address of the device. Optional. |
| ipV6Address | String | The IPv6 address of the device. Optional. |
| macAddress | String | The MAC address of the device. Optional. |
| manufacturer | String | The manufacturer of the device. Required. |
| placeId | String | The unique identifier of the place where the device is located. If the device is installed in a room equipped with a mailbox, this property should match the **ExternalDirectoryObjectId** or Microsoft Entra object ID of the room mailbox. Optional. |
| sensors | [workplaceSensor](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensor?view=graph-rest-beta) collection | A list of sensors associated with the device that collect and report data about physical or environmental conditions, such as occupancy, people count, inferred occupancy, temperature, and more. Required. |
| tags | String collection | A list of custom tags associated with the device. Supports `$filter`. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevice?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/workplace/sensorDevices
Content-Type: application/json

{
    "deviceId": "contoso_9D6816",
    "displayName": "Contoso 9D6816 Device",
    "description": "Contoso 9D6816 Device",
    "macAddress": "00:0A:95:9D:68:16",
    "manufacturer": "Contoso",
    "ipV4Address": "192.168.1.100",
    "ipV6Address": "2001:db8::ff00:42:8329",
    "placeId": "acfa3bc0-2b83-425b-8910-84a0250e9671",
    "tags": [
        "Building A",
        "Floor 3",
        "Room 301",
        "Conference Room"
    ],
    "sensors": [
        {
            "sensorType": "occupancy"
        },
        {
            "sensorType": "peopleCount"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new WorkplaceSensorDevice
{
	DeviceId = "contoso_9D6816",
	DisplayName = "Contoso 9D6816 Device",
	Description = "Contoso 9D6816 Device",
	MacAddress = "00:0A:95:9D:68:16",
	Manufacturer = "Contoso",
	IpV4Address = "192.168.1.100",
	IpV6Address = "2001:db8::ff00:42:8329",
	PlaceId = "acfa3bc0-2b83-425b-8910-84a0250e9671",
	Tags = new List<string>
	{
		"Building A",
		"Floor 3",
		"Room 301",
		"Conference Room",
	},
	Sensors = new List<WorkplaceSensor>
	{
		new WorkplaceSensor
		{
			SensorType = WorkplaceSensorType.Occupancy,
		},
		new WorkplaceSensor
		{
			SensorType = WorkplaceSensorType.PeopleCount,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Workplace.SensorDevices.PostAsync(requestBody);
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

requestBody := graphmodels.NewWorkplaceSensorDevice()
deviceId := "contoso_9D6816"
requestBody.SetDeviceId(&deviceId) 
displayName := "Contoso 9D6816 Device"
requestBody.SetDisplayName(&displayName) 
description := "Contoso 9D6816 Device"
requestBody.SetDescription(&description) 
macAddress := "00:0A:95:9D:68:16"
requestBody.SetMacAddress(&macAddress) 
manufacturer := "Contoso"
requestBody.SetManufacturer(&manufacturer) 
ipV4Address := "192.168.1.100"
requestBody.SetIpV4Address(&ipV4Address) 
ipV6Address := "2001:db8::ff00:42:8329"
requestBody.SetIpV6Address(&ipV6Address) 
placeId := "acfa3bc0-2b83-425b-8910-84a0250e9671"
requestBody.SetPlaceId(&placeId) 
tags := []string {
	"Building A",
	"Floor 3",
	"Room 301",
	"Conference Room",
}
requestBody.SetTags(tags)


workplaceSensor := graphmodels.NewWorkplaceSensor()
sensorType := graphmodels.OCCUPANCY_WORKPLACESENSORTYPE 
workplaceSensor.SetSensorType(&sensorType) 
workplaceSensor1 := graphmodels.NewWorkplaceSensor()
sensorType := graphmodels.PEOPLECOUNT_WORKPLACESENSORTYPE 
workplaceSensor1.SetSensorType(&sensorType) 

sensors := []graphmodels.WorkplaceSensorable {
	workplaceSensor,
	workplaceSensor1,
}
requestBody.SetSensors(sensors)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sensorDevices, err := graphClient.Workplace().SensorDevices().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkplaceSensorDevice workplaceSensorDevice = new WorkplaceSensorDevice();
workplaceSensorDevice.setDeviceId("contoso_9D6816");
workplaceSensorDevice.setDisplayName("Contoso 9D6816 Device");
workplaceSensorDevice.setDescription("Contoso 9D6816 Device");
workplaceSensorDevice.setMacAddress("00:0A:95:9D:68:16");
workplaceSensorDevice.setManufacturer("Contoso");
workplaceSensorDevice.setIpV4Address("192.168.1.100");
workplaceSensorDevice.setIpV6Address("2001:db8::ff00:42:8329");
workplaceSensorDevice.setPlaceId("acfa3bc0-2b83-425b-8910-84a0250e9671");
LinkedList<String> tags = new LinkedList<String>();
tags.add("Building A");
tags.add("Floor 3");
tags.add("Room 301");
tags.add("Conference Room");
workplaceSensorDevice.setTags(tags);
LinkedList<WorkplaceSensor> sensors = new LinkedList<WorkplaceSensor>();
WorkplaceSensor workplaceSensor = new WorkplaceSensor();
workplaceSensor.setSensorType(WorkplaceSensorType.Occupancy);
sensors.add(workplaceSensor);
WorkplaceSensor workplaceSensor1 = new WorkplaceSensor();
workplaceSensor1.setSensorType(WorkplaceSensorType.PeopleCount);
sensors.add(workplaceSensor1);
workplaceSensorDevice.setSensors(sensors);
WorkplaceSensorDevice result = graphClient.workplace().sensorDevices().post(workplaceSensorDevice);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workplaceSensorDevice = {
    deviceId: 'contoso_9D6816',
    displayName: 'Contoso 9D6816 Device',
    description: 'Contoso 9D6816 Device',
    macAddress: '00:0A:95:9D:68:16',
    manufacturer: 'Contoso',
    ipV4Address: '192.168.1.100',
    ipV6Address: '2001:db8::ff00:42:8329',
    placeId: 'acfa3bc0-2b83-425b-8910-84a0250e9671',
    tags: [
        'Building A',
        'Floor 3',
        'Room 301',
        'Conference Room'
    ],
    sensors: [
        {
            sensorType: 'occupancy'
        },
        {
            sensorType: 'peopleCount'
        }
    ]
};

await client.api('/workplace/sensorDevices')
	.version('beta')
	.post(workplaceSensorDevice);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorDevice;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensor;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkplaceSensorDevice();
$requestBody->setDeviceId('contoso_9D6816');
$requestBody->setDisplayName('Contoso 9D6816 Device');
$requestBody->setDescription('Contoso 9D6816 Device');
$requestBody->setMacAddress('00:0A:95:9D:68:16');
$requestBody->setManufacturer('Contoso');
$requestBody->setIpV4Address('192.168.1.100');
$requestBody->setIpV6Address('2001:db8::ff00:42:8329');
$requestBody->setPlaceId('acfa3bc0-2b83-425b-8910-84a0250e9671');
$requestBody->setTags(['Building A', 'Floor 3', 'Room 301', 'Conference Room', 	]);
$sensorsWorkplaceSensor1 = new WorkplaceSensor();
$sensorsWorkplaceSensor1->setSensorType(new WorkplaceSensorType('occupancy'));
$sensorsArray []= $sensorsWorkplaceSensor1;
$sensorsWorkplaceSensor2 = new WorkplaceSensor();
$sensorsWorkplaceSensor2->setSensorType(new WorkplaceSensorType('peopleCount'));
$sensorsArray []= $sensorsWorkplaceSensor2;
$requestBody->setSensors($sensorsArray);


$result = $graphServiceClient->workplace()->sensorDevices()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.workplace_sensor_device import WorkplaceSensorDevice
from msgraph_beta.generated.models.workplace_sensor import WorkplaceSensor
from msgraph_beta.generated.models.workplace_sensor_type import WorkplaceSensorType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkplaceSensorDevice(
	device_id = "contoso_9D6816",
	display_name = "Contoso 9D6816 Device",
	description = "Contoso 9D6816 Device",
	mac_address = "00:0A:95:9D:68:16",
	manufacturer = "Contoso",
	ip_v4_address = "192.168.1.100",
	ip_v6_address = "2001:db8::ff00:42:8329",
	place_id = "acfa3bc0-2b83-425b-8910-84a0250e9671",
	tags = [
		"Building A",
		"Floor 3",
		"Room 301",
		"Conference Room",
	],
	sensors = [
		WorkplaceSensor(
			sensor_type = WorkplaceSensorType.Occupancy,
		),
		WorkplaceSensor(
			sensor_type = WorkplaceSensorType.PeopleCount,
		),
	],
)

result = await graph_client.workplace.sensor_devices.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#workplace/sensorDevices/$entity",
    "id": "ade7078f-4bf5-4239-bfde-95a7c4225df7",
    "deviceId": "contoso_9D6816",
    "displayName": "Contoso 9D6816 Device",
    "description": "Contoso 9D6816 Device",
    "macAddress": "00:0A:95:9D:68:16",
    "manufacturer": "Contoso",
    "ipV4Address": "192.168.1.100",
    "ipV6Address": "2001:db8::ff00:42:8329",
    "placeId": "acfa3bc0-2b83-425b-8910-84a0250e9671",
    "tags": [
        "Building A",
        "Floor 3",
        "Room 301",
        "Conference Room"
    ],
    "sensors": [
        {
            "sensorId": "Occupancy",
            "displayName": null,
            "sensorType": "occupancy",
            "placeId": "acfa3bc0-2b83-425b-8910-84a0250e9671"
        },
        {
            "sensorId": "PeopleCount",
            "displayName": null,
            "sensorType": "peopleCount",
            "placeId": "acfa3bc0-2b83-425b-8910-84a0250e9671"
        }
    ]
}
```
