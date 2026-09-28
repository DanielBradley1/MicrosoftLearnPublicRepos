<!-- Source: https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-ingesttelemetry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# workplaceSensorDevice: ingestTelemetry

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Ingest sensor telemetry for a workplace sensor device.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PlaceDevice.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PlaceDeviceTelemetry.ReadWrite.All | PlaceDevice.ReadWrite.All |

## HTTP request

```http
POST /workplace/sensorDevices/ingestTelemetry
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The **sensorId** property may be omitted within the [workplaceSensorDeviceTelemetry](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevicetelemetry?view=graph-rest-beta) object for devices with unique sensor types. When this property is omitted, the [sensorType](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensor?view=graph-rest-beta#workplacesensortype-values) value serves as the default identifier, consistent with the behavior when you create a device without a specified **sensorId**.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| telemetry | [workplaceSensorDeviceTelemetry](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevicetelemetry?view=graph-rest-beta) collection | A collection of the telemetry data collected and reported by a sensor on a device, such as occupancy, people count, inferred occupancy, temperature, and more. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Send sensor telemetry for a device with unique sensor types

The following example shows how to send sensor telemetry for a device with unique sensor types.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/workplace/sensorDevices/ingestTelemetry
Content-Type: application/json

{
    "telemetry": [
        {
            "deviceId": "contoso_9D6816",
            "sensorType": "occupancy",
            "boolValue": false,
            "timestamp": "2021-03-31T09:36:05.144Z"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Workplace.SensorDevices.IngestTelemetry;
using Microsoft.Graph.Beta.Models;

var requestBody = new IngestTelemetryPostRequestBody
{
	Telemetry = new List<WorkplaceSensorDeviceTelemetry>
	{
		new WorkplaceSensorDeviceTelemetry
		{
			DeviceId = "contoso_9D6816",
			SensorType = WorkplaceSensorType.Occupancy,
			BoolValue = false,
			Timestamp = DateTimeOffset.Parse("2021-03-31T09:36:05.144Z"),
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Workplace.SensorDevices.IngestTelemetry.PostAsync(requestBody);
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
	  graphworkplace "github.com/microsoftgraph/msgraph-beta-sdk-go/workplace"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphworkplace.NewIngestTelemetryPostRequestBody()


workplaceSensorDeviceTelemetry := graphmodels.NewWorkplaceSensorDeviceTelemetry()
deviceId := "contoso_9D6816"
workplaceSensorDeviceTelemetry.SetDeviceId(&deviceId) 
sensorType := graphmodels.OCCUPANCY_WORKPLACESENSORTYPE 
workplaceSensorDeviceTelemetry.SetSensorType(&sensorType) 
boolValue := false
workplaceSensorDeviceTelemetry.SetBoolValue(&boolValue) 
timestamp , err := time.Parse(time.RFC3339, "2021-03-31T09:36:05.144Z")
workplaceSensorDeviceTelemetry.SetTimestamp(&timestamp) 

telemetry := []graphmodels.WorkplaceSensorDeviceTelemetryable {
	workplaceSensorDeviceTelemetry,
}
requestBody.SetTelemetry(telemetry)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Workplace().SensorDevices().IngestTelemetry().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.workplace.sensordevices.ingesttelemetry.IngestTelemetryPostRequestBody ingestTelemetryPostRequestBody = new com.microsoft.graph.beta.workplace.sensordevices.ingesttelemetry.IngestTelemetryPostRequestBody();
LinkedList<WorkplaceSensorDeviceTelemetry> telemetry = new LinkedList<WorkplaceSensorDeviceTelemetry>();
WorkplaceSensorDeviceTelemetry workplaceSensorDeviceTelemetry = new WorkplaceSensorDeviceTelemetry();
workplaceSensorDeviceTelemetry.setDeviceId("contoso_9D6816");
workplaceSensorDeviceTelemetry.setSensorType(WorkplaceSensorType.Occupancy);
workplaceSensorDeviceTelemetry.setBoolValue(false);
OffsetDateTime timestamp = OffsetDateTime.parse("2021-03-31T09:36:05.144Z");
workplaceSensorDeviceTelemetry.setTimestamp(timestamp);
telemetry.add(workplaceSensorDeviceTelemetry);
ingestTelemetryPostRequestBody.setTelemetry(telemetry);
graphClient.workplace().sensorDevices().ingestTelemetry().post(ingestTelemetryPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ingestTelemetry = {
    telemetry: [
        {
            deviceId: 'contoso_9D6816',
            sensorType: 'occupancy',
            boolValue: false,
            timestamp: '2021-03-31T09:36:05.144Z'
        }
    ]
};

await client.api('/workplace/sensorDevices/ingestTelemetry')
	.version('beta')
	.post(ingestTelemetry);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Workplace\SensorDevices\IngestTelemetry\IngestTelemetryPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorDeviceTelemetry;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IngestTelemetryPostRequestBody();
$telemetryWorkplaceSensorDeviceTelemetry1 = new WorkplaceSensorDeviceTelemetry();
$telemetryWorkplaceSensorDeviceTelemetry1->setDeviceId('contoso_9D6816');
$telemetryWorkplaceSensorDeviceTelemetry1->setSensorType(new WorkplaceSensorType('occupancy'));
$telemetryWorkplaceSensorDeviceTelemetry1->setBoolValue(false);
$telemetryWorkplaceSensorDeviceTelemetry1->setTimestamp(new \DateTime('2021-03-31T09:36:05.144Z'));
$telemetryArray []= $telemetryWorkplaceSensorDeviceTelemetry1;
$requestBody->setTelemetry($telemetryArray);


$graphServiceClient->workplace()->sensorDevices()->ingestTelemetry()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.workplace.sensordevices.ingest_telemetry.ingest_telemetry_post_request_body import IngestTelemetryPostRequestBody
from msgraph_beta.generated.models.workplace_sensor_device_telemetry import WorkplaceSensorDeviceTelemetry
from msgraph_beta.generated.models.workplace_sensor_type import WorkplaceSensorType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IngestTelemetryPostRequestBody(
	telemetry = [
		WorkplaceSensorDeviceTelemetry(
			device_id = "contoso_9D6816",
			sensor_type = WorkplaceSensorType.Occupancy,
			bool_value = False,
			timestamp = "2021-03-31T09:36:05.144Z",
		),
	],
)

await graph_client.workplace.sensor_devices.ingest_telemetry.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Send sensor telemetry for a device that has multiple sensors of the same type

The following example shows how to send sensor telemetry for a device that has multiple sensors of the same type.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/workplace/sensorDevices/ingestTelemetry
Content-Type: application/json

{
    "telemetry": [
        {
            "deviceId": "contoso_9D6816",
            "sensorId": "occupancy_1",
            "sensorType": "occupancy",
            "boolValue": false,
            "timestamp": "2021-03-31T09:36:05.144Z"
        },
        {
            "deviceId": "contoso_9D6816",
            "sensorId": "occupancy_2",
            "sensorType": "occupancy",
            "boolValue": false,
            "timestamp": "2021-03-31T09:36:05.144Z"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Workplace.SensorDevices.IngestTelemetry;
using Microsoft.Graph.Beta.Models;

var requestBody = new IngestTelemetryPostRequestBody
{
	Telemetry = new List<WorkplaceSensorDeviceTelemetry>
	{
		new WorkplaceSensorDeviceTelemetry
		{
			DeviceId = "contoso_9D6816",
			SensorId = "occupancy_1",
			SensorType = WorkplaceSensorType.Occupancy,
			BoolValue = false,
			Timestamp = DateTimeOffset.Parse("2021-03-31T09:36:05.144Z"),
		},
		new WorkplaceSensorDeviceTelemetry
		{
			DeviceId = "contoso_9D6816",
			SensorId = "occupancy_2",
			SensorType = WorkplaceSensorType.Occupancy,
			BoolValue = false,
			Timestamp = DateTimeOffset.Parse("2021-03-31T09:36:05.144Z"),
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Workplace.SensorDevices.IngestTelemetry.PostAsync(requestBody);
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
	  graphworkplace "github.com/microsoftgraph/msgraph-beta-sdk-go/workplace"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphworkplace.NewIngestTelemetryPostRequestBody()


workplaceSensorDeviceTelemetry := graphmodels.NewWorkplaceSensorDeviceTelemetry()
deviceId := "contoso_9D6816"
workplaceSensorDeviceTelemetry.SetDeviceId(&deviceId) 
sensorId := "occupancy_1"
workplaceSensorDeviceTelemetry.SetSensorId(&sensorId) 
sensorType := graphmodels.OCCUPANCY_WORKPLACESENSORTYPE 
workplaceSensorDeviceTelemetry.SetSensorType(&sensorType) 
boolValue := false
workplaceSensorDeviceTelemetry.SetBoolValue(&boolValue) 
timestamp , err := time.Parse(time.RFC3339, "2021-03-31T09:36:05.144Z")
workplaceSensorDeviceTelemetry.SetTimestamp(&timestamp) 
workplaceSensorDeviceTelemetry1 := graphmodels.NewWorkplaceSensorDeviceTelemetry()
deviceId := "contoso_9D6816"
workplaceSensorDeviceTelemetry1.SetDeviceId(&deviceId) 
sensorId := "occupancy_2"
workplaceSensorDeviceTelemetry1.SetSensorId(&sensorId) 
sensorType := graphmodels.OCCUPANCY_WORKPLACESENSORTYPE 
workplaceSensorDeviceTelemetry1.SetSensorType(&sensorType) 
boolValue := false
workplaceSensorDeviceTelemetry1.SetBoolValue(&boolValue) 
timestamp , err := time.Parse(time.RFC3339, "2021-03-31T09:36:05.144Z")
workplaceSensorDeviceTelemetry1.SetTimestamp(&timestamp) 

telemetry := []graphmodels.WorkplaceSensorDeviceTelemetryable {
	workplaceSensorDeviceTelemetry,
	workplaceSensorDeviceTelemetry1,
}
requestBody.SetTelemetry(telemetry)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Workplace().SensorDevices().IngestTelemetry().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.workplace.sensordevices.ingesttelemetry.IngestTelemetryPostRequestBody ingestTelemetryPostRequestBody = new com.microsoft.graph.beta.workplace.sensordevices.ingesttelemetry.IngestTelemetryPostRequestBody();
LinkedList<WorkplaceSensorDeviceTelemetry> telemetry = new LinkedList<WorkplaceSensorDeviceTelemetry>();
WorkplaceSensorDeviceTelemetry workplaceSensorDeviceTelemetry = new WorkplaceSensorDeviceTelemetry();
workplaceSensorDeviceTelemetry.setDeviceId("contoso_9D6816");
workplaceSensorDeviceTelemetry.setSensorId("occupancy_1");
workplaceSensorDeviceTelemetry.setSensorType(WorkplaceSensorType.Occupancy);
workplaceSensorDeviceTelemetry.setBoolValue(false);
OffsetDateTime timestamp = OffsetDateTime.parse("2021-03-31T09:36:05.144Z");
workplaceSensorDeviceTelemetry.setTimestamp(timestamp);
telemetry.add(workplaceSensorDeviceTelemetry);
WorkplaceSensorDeviceTelemetry workplaceSensorDeviceTelemetry1 = new WorkplaceSensorDeviceTelemetry();
workplaceSensorDeviceTelemetry1.setDeviceId("contoso_9D6816");
workplaceSensorDeviceTelemetry1.setSensorId("occupancy_2");
workplaceSensorDeviceTelemetry1.setSensorType(WorkplaceSensorType.Occupancy);
workplaceSensorDeviceTelemetry1.setBoolValue(false);
OffsetDateTime timestamp1 = OffsetDateTime.parse("2021-03-31T09:36:05.144Z");
workplaceSensorDeviceTelemetry1.setTimestamp(timestamp1);
telemetry.add(workplaceSensorDeviceTelemetry1);
ingestTelemetryPostRequestBody.setTelemetry(telemetry);
graphClient.workplace().sensorDevices().ingestTelemetry().post(ingestTelemetryPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ingestTelemetry = {
    telemetry: [
        {
            deviceId: 'contoso_9D6816',
            sensorId: 'occupancy_1',
            sensorType: 'occupancy',
            boolValue: false,
            timestamp: '2021-03-31T09:36:05.144Z'
        },
        {
            deviceId: 'contoso_9D6816',
            sensorId: 'occupancy_2',
            sensorType: 'occupancy',
            boolValue: false,
            timestamp: '2021-03-31T09:36:05.144Z'
        }
    ]
};

await client.api('/workplace/sensorDevices/ingestTelemetry')
	.version('beta')
	.post(ingestTelemetry);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Workplace\SensorDevices\IngestTelemetry\IngestTelemetryPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorDeviceTelemetry;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IngestTelemetryPostRequestBody();
$telemetryWorkplaceSensorDeviceTelemetry1 = new WorkplaceSensorDeviceTelemetry();
$telemetryWorkplaceSensorDeviceTelemetry1->setDeviceId('contoso_9D6816');
$telemetryWorkplaceSensorDeviceTelemetry1->setSensorId('occupancy_1');
$telemetryWorkplaceSensorDeviceTelemetry1->setSensorType(new WorkplaceSensorType('occupancy'));
$telemetryWorkplaceSensorDeviceTelemetry1->setBoolValue(false);
$telemetryWorkplaceSensorDeviceTelemetry1->setTimestamp(new \DateTime('2021-03-31T09:36:05.144Z'));
$telemetryArray []= $telemetryWorkplaceSensorDeviceTelemetry1;
$telemetryWorkplaceSensorDeviceTelemetry2 = new WorkplaceSensorDeviceTelemetry();
$telemetryWorkplaceSensorDeviceTelemetry2->setDeviceId('contoso_9D6816');
$telemetryWorkplaceSensorDeviceTelemetry2->setSensorId('occupancy_2');
$telemetryWorkplaceSensorDeviceTelemetry2->setSensorType(new WorkplaceSensorType('occupancy'));
$telemetryWorkplaceSensorDeviceTelemetry2->setBoolValue(false);
$telemetryWorkplaceSensorDeviceTelemetry2->setTimestamp(new \DateTime('2021-03-31T09:36:05.144Z'));
$telemetryArray []= $telemetryWorkplaceSensorDeviceTelemetry2;
$requestBody->setTelemetry($telemetryArray);


$graphServiceClient->workplace()->sensorDevices()->ingestTelemetry()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.workplace.sensordevices.ingest_telemetry.ingest_telemetry_post_request_body import IngestTelemetryPostRequestBody
from msgraph_beta.generated.models.workplace_sensor_device_telemetry import WorkplaceSensorDeviceTelemetry
from msgraph_beta.generated.models.workplace_sensor_type import WorkplaceSensorType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IngestTelemetryPostRequestBody(
	telemetry = [
		WorkplaceSensorDeviceTelemetry(
			device_id = "contoso_9D6816",
			sensor_id = "occupancy_1",
			sensor_type = WorkplaceSensorType.Occupancy,
			bool_value = False,
			timestamp = "2021-03-31T09:36:05.144Z",
		),
		WorkplaceSensorDeviceTelemetry(
			device_id = "contoso_9D6816",
			sensor_id = "occupancy_2",
			sensor_type = WorkplaceSensorType.Occupancy,
			bool_value = False,
			timestamp = "2021-03-31T09:36:05.144Z",
		),
	],
)

await graph_client.workplace.sensor_devices.ingest_telemetry.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Ingest telemetry for multiple devices

The following example shows how to ingest telemetry for multiple devices.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/workplace/sensorDevices/ingestTelemetry
Content-Type: application/json

{
    "telemetry": [
        {
            "deviceId": "contoso_9D6816",
            "sensorType": "occupancy",
            "boolValue": false,
            "timestamp": "2021-03-31T09:36:05.144Z"
        },
        {
            "deviceId": "contoso_9D6817",
            "sensorType": "occupancy",
            "boolValue": false,
            "timestamp": "2021-03-31T09:36:05.144Z"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Workplace.SensorDevices.IngestTelemetry;
using Microsoft.Graph.Beta.Models;

var requestBody = new IngestTelemetryPostRequestBody
{
	Telemetry = new List<WorkplaceSensorDeviceTelemetry>
	{
		new WorkplaceSensorDeviceTelemetry
		{
			DeviceId = "contoso_9D6816",
			SensorType = WorkplaceSensorType.Occupancy,
			BoolValue = false,
			Timestamp = DateTimeOffset.Parse("2021-03-31T09:36:05.144Z"),
		},
		new WorkplaceSensorDeviceTelemetry
		{
			DeviceId = "contoso_9D6817",
			SensorType = WorkplaceSensorType.Occupancy,
			BoolValue = false,
			Timestamp = DateTimeOffset.Parse("2021-03-31T09:36:05.144Z"),
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Workplace.SensorDevices.IngestTelemetry.PostAsync(requestBody);
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
	  graphworkplace "github.com/microsoftgraph/msgraph-beta-sdk-go/workplace"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphworkplace.NewIngestTelemetryPostRequestBody()


workplaceSensorDeviceTelemetry := graphmodels.NewWorkplaceSensorDeviceTelemetry()
deviceId := "contoso_9D6816"
workplaceSensorDeviceTelemetry.SetDeviceId(&deviceId) 
sensorType := graphmodels.OCCUPANCY_WORKPLACESENSORTYPE 
workplaceSensorDeviceTelemetry.SetSensorType(&sensorType) 
boolValue := false
workplaceSensorDeviceTelemetry.SetBoolValue(&boolValue) 
timestamp , err := time.Parse(time.RFC3339, "2021-03-31T09:36:05.144Z")
workplaceSensorDeviceTelemetry.SetTimestamp(&timestamp) 
workplaceSensorDeviceTelemetry1 := graphmodels.NewWorkplaceSensorDeviceTelemetry()
deviceId := "contoso_9D6817"
workplaceSensorDeviceTelemetry1.SetDeviceId(&deviceId) 
sensorType := graphmodels.OCCUPANCY_WORKPLACESENSORTYPE 
workplaceSensorDeviceTelemetry1.SetSensorType(&sensorType) 
boolValue := false
workplaceSensorDeviceTelemetry1.SetBoolValue(&boolValue) 
timestamp , err := time.Parse(time.RFC3339, "2021-03-31T09:36:05.144Z")
workplaceSensorDeviceTelemetry1.SetTimestamp(&timestamp) 

telemetry := []graphmodels.WorkplaceSensorDeviceTelemetryable {
	workplaceSensorDeviceTelemetry,
	workplaceSensorDeviceTelemetry1,
}
requestBody.SetTelemetry(telemetry)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Workplace().SensorDevices().IngestTelemetry().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.workplace.sensordevices.ingesttelemetry.IngestTelemetryPostRequestBody ingestTelemetryPostRequestBody = new com.microsoft.graph.beta.workplace.sensordevices.ingesttelemetry.IngestTelemetryPostRequestBody();
LinkedList<WorkplaceSensorDeviceTelemetry> telemetry = new LinkedList<WorkplaceSensorDeviceTelemetry>();
WorkplaceSensorDeviceTelemetry workplaceSensorDeviceTelemetry = new WorkplaceSensorDeviceTelemetry();
workplaceSensorDeviceTelemetry.setDeviceId("contoso_9D6816");
workplaceSensorDeviceTelemetry.setSensorType(WorkplaceSensorType.Occupancy);
workplaceSensorDeviceTelemetry.setBoolValue(false);
OffsetDateTime timestamp = OffsetDateTime.parse("2021-03-31T09:36:05.144Z");
workplaceSensorDeviceTelemetry.setTimestamp(timestamp);
telemetry.add(workplaceSensorDeviceTelemetry);
WorkplaceSensorDeviceTelemetry workplaceSensorDeviceTelemetry1 = new WorkplaceSensorDeviceTelemetry();
workplaceSensorDeviceTelemetry1.setDeviceId("contoso_9D6817");
workplaceSensorDeviceTelemetry1.setSensorType(WorkplaceSensorType.Occupancy);
workplaceSensorDeviceTelemetry1.setBoolValue(false);
OffsetDateTime timestamp1 = OffsetDateTime.parse("2021-03-31T09:36:05.144Z");
workplaceSensorDeviceTelemetry1.setTimestamp(timestamp1);
telemetry.add(workplaceSensorDeviceTelemetry1);
ingestTelemetryPostRequestBody.setTelemetry(telemetry);
graphClient.workplace().sensorDevices().ingestTelemetry().post(ingestTelemetryPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ingestTelemetry = {
    telemetry: [
        {
            deviceId: 'contoso_9D6816',
            sensorType: 'occupancy',
            boolValue: false,
            timestamp: '2021-03-31T09:36:05.144Z'
        },
        {
            deviceId: 'contoso_9D6817',
            sensorType: 'occupancy',
            boolValue: false,
            timestamp: '2021-03-31T09:36:05.144Z'
        }
    ]
};

await client.api('/workplace/sensorDevices/ingestTelemetry')
	.version('beta')
	.post(ingestTelemetry);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Workplace\SensorDevices\IngestTelemetry\IngestTelemetryPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorDeviceTelemetry;
use Microsoft\Graph\Beta\Generated\Models\WorkplaceSensorType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new IngestTelemetryPostRequestBody();
$telemetryWorkplaceSensorDeviceTelemetry1 = new WorkplaceSensorDeviceTelemetry();
$telemetryWorkplaceSensorDeviceTelemetry1->setDeviceId('contoso_9D6816');
$telemetryWorkplaceSensorDeviceTelemetry1->setSensorType(new WorkplaceSensorType('occupancy'));
$telemetryWorkplaceSensorDeviceTelemetry1->setBoolValue(false);
$telemetryWorkplaceSensorDeviceTelemetry1->setTimestamp(new \DateTime('2021-03-31T09:36:05.144Z'));
$telemetryArray []= $telemetryWorkplaceSensorDeviceTelemetry1;
$telemetryWorkplaceSensorDeviceTelemetry2 = new WorkplaceSensorDeviceTelemetry();
$telemetryWorkplaceSensorDeviceTelemetry2->setDeviceId('contoso_9D6817');
$telemetryWorkplaceSensorDeviceTelemetry2->setSensorType(new WorkplaceSensorType('occupancy'));
$telemetryWorkplaceSensorDeviceTelemetry2->setBoolValue(false);
$telemetryWorkplaceSensorDeviceTelemetry2->setTimestamp(new \DateTime('2021-03-31T09:36:05.144Z'));
$telemetryArray []= $telemetryWorkplaceSensorDeviceTelemetry2;
$requestBody->setTelemetry($telemetryArray);


$graphServiceClient->workplace()->sensorDevices()->ingestTelemetry()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.workplace.sensordevices.ingest_telemetry.ingest_telemetry_post_request_body import IngestTelemetryPostRequestBody
from msgraph_beta.generated.models.workplace_sensor_device_telemetry import WorkplaceSensorDeviceTelemetry
from msgraph_beta.generated.models.workplace_sensor_type import WorkplaceSensorType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = IngestTelemetryPostRequestBody(
	telemetry = [
		WorkplaceSensorDeviceTelemetry(
			device_id = "contoso_9D6816",
			sensor_type = WorkplaceSensorType.Occupancy,
			bool_value = False,
			timestamp = "2021-03-31T09:36:05.144Z",
		),
		WorkplaceSensorDeviceTelemetry(
			device_id = "contoso_9D6817",
			sensor_type = WorkplaceSensorType.Occupancy,
			bool_value = False,
			timestamp = "2021-03-31T09:36:05.144Z",
		),
	],
)

await graph_client.workplace.sensor_devices.ingest_telemetry.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
