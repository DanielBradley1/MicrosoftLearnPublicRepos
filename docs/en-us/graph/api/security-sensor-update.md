<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-sensor-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-07 -->

# Update sensor

Namespace: microsoft.graph.security

Update the properties of a [sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SecurityIdentitiesSensors.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | SecurityIdentitiesSensors.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /security/identities/sensors/{sensorId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| settings | [microsoft.graph.security.sensorSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorsettings?view=graph-rest-1.0) | Sensor settings information. The **description** property can be updated for all sensor types. The **isDelayedUpdateEnabled** property can be updated for all sensors with version < 3.X. The **domainControllerDnsNames** property can be updated for all sensors with version < 3.X except for domain controller sensors. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.security.sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/security/identities/sensors/d31dd827-92cd-4cd6-b269-c151a0eec55d
Content-Type: application/json

{
  "settings": {
    "description": "dc1 settings new description",
    "domainControllerDnsNames": [
        "DC1.domain1.test.local"
    ],
    "isDelayedDeploymentEnabled": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new Sensor
{
	Settings = new SensorSettings
	{
		Description = "dc1 settings new description",
		DomainControllerDnsNames = new List<string>
		{
			"DC1.domain1.test.local",
		},
		IsDelayedDeploymentEnabled = false,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Identities.Sensors["{sensor-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewSensor()
settings := graphmodelssecurity.NewSensorSettings()
description := "dc1 settings new description"
settings.SetDescription(&description) 
domainControllerDnsNames := []string {
	"DC1.domain1.test.local",
}
settings.SetDomainControllerDnsNames(domainControllerDnsNames)
isDelayedDeploymentEnabled := false
settings.SetIsDelayedDeploymentEnabled(&isDelayedDeploymentEnabled) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sensors, err := graphClient.Security().Identities().Sensors().BySensorId("sensor-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.Sensor sensor = new com.microsoft.graph.models.security.Sensor();
com.microsoft.graph.models.security.SensorSettings settings = new com.microsoft.graph.models.security.SensorSettings();
settings.setDescription("dc1 settings new description");
LinkedList<String> domainControllerDnsNames = new LinkedList<String>();
domainControllerDnsNames.add("DC1.domain1.test.local");
settings.setDomainControllerDnsNames(domainControllerDnsNames);
settings.setIsDelayedDeploymentEnabled(false);
sensor.setSettings(settings);
com.microsoft.graph.models.security.Sensor result = graphClient.security().identities().sensors().bySensorId("{sensor-id}").patch(sensor);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sensor = {
  settings: {
    description: 'dc1 settings new description',
    domainControllerDnsNames: [
        'DC1.domain1.test.local'
    ],
    isDelayedDeploymentEnabled: false
  }
};

await client.api('/security/identities/sensors/d31dd827-92cd-4cd6-b269-c151a0eec55d')
	.update(sensor);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\Sensor;
use Microsoft\Graph\Generated\Models\Security\SensorSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Sensor();
$settings = new SensorSettings();
$settings->setDescription('dc1 settings new description');
$settings->setDomainControllerDnsNames(['DC1.domain1.test.local', 	]);
$settings->setIsDelayedDeploymentEnabled(false);
$requestBody->setSettings($settings);

$result = $graphServiceClient->security()->identities()->sensors()->bySensorId('sensor-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	settings = @{
		description = "dc1 settings new description"
		domainControllerDnsNames = @(
		"DC1.domain1.test.local"
	)
	isDelayedDeploymentEnabled = $false
}
}

Update-MgSecurityIdentitySensor -SensorId $sensorId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.sensor import Sensor
from msgraph.generated.models.security.sensor_settings import SensorSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Sensor(
	settings = SensorSettings(
		description = "dc1 settings new description",
		domain_controller_dns_names = [
			"DC1.domain1.test.local",
		],
		is_delayed_deployment_enabled = False,
	),
)

result = await graph_client.security.identities.sensors.by_sensor_id('sensor-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.security.sensor",
    "id": "b3c1b5fc-828c-45fa-a1e1-10d74f6d6e9c",
    "displayName": "DC1",
    "sensorType": "domainControllerIntegrated",
    "version": "2.239.18124.58593",
    "deploymentStatus": "upToDate",
    "createdDateTime": "2023-11-16T09:41:24.2585071Z",
    "domainName": "domain1.test.local",
    "healthStatus": "healthy",
    "openHealthIssuesCount": 0,
    "settings": {
        "@odata.type": "microsoft.graph.security.sensorSettings",
        "description": "dc1 settings new description",
        "domainControllerDnsNames": [
            "DC1.domain1.test.local"
        ],
        "isDelayedDeploymentEnabled": false
    },
    "serviceStatus": "running"
}
```
