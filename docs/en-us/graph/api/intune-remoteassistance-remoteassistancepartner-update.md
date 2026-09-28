<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancepartner-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update remoteAssistancePartner

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/remoteAssistancePartners/{remoteAssistancePartnerId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the partner. |
| displayName | String | Display name of the partner. |
| onboardingUrl | String | URL of the partner's onboarding portal, where an administrator can configure their Remote Assistance service. |
| onboardingStatus | [remoteAssistanceOnboardingStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistanceonboardingstatus?view=graph-rest-1.0) | A friendly description of the current TeamViewer connector status. The possible values are: `notOnboarded`, `onboarding`, `onboarded`. |
| lastConnectionDateTime | DateTimeOffset | Timestamp of the last request sent to Intune by the TEM partner. |

## Response

If successful, this method returns a `200 OK` response code and an updated [remoteAssistancePartner](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancepartner?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/remoteAssistancePartners/{remoteAssistancePartnerId}
Content-type: application/json
Content-length: 266

{
  "@odata.type": "#microsoft.graph.remoteAssistancePartner",
  "displayName": "Display Name value",
  "onboardingUrl": "https://example.com/onboardingUrl/",
  "onboardingStatus": "onboarding",
  "lastConnectionDateTime": "2016-12-31T23:58:36.6670033-08:00"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new RemoteAssistancePartner
{
	OdataType = "#microsoft.graph.remoteAssistancePartner",
	DisplayName = "Display Name value",
	OnboardingUrl = "https://example.com/onboardingUrl/",
	OnboardingStatus = RemoteAssistanceOnboardingStatus.Onboarding,
	LastConnectionDateTime = DateTimeOffset.Parse("2016-12-31T23:58:36.6670033-08:00"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.RemoteAssistancePartners["{remoteAssistancePartner-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewRemoteAssistancePartner()
displayName := "Display Name value"
requestBody.SetDisplayName(&displayName) 
onboardingUrl := "https://example.com/onboardingUrl/"
requestBody.SetOnboardingUrl(&onboardingUrl) 
onboardingStatus := graphmodels.ONBOARDING_REMOTEASSISTANCEONBOARDINGSTATUS 
requestBody.SetOnboardingStatus(&onboardingStatus) 
lastConnectionDateTime , err := time.Parse(time.RFC3339, "2016-12-31T23:58:36.6670033-08:00")
requestBody.SetLastConnectionDateTime(&lastConnectionDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remoteAssistancePartners, err := graphClient.DeviceManagement().RemoteAssistancePartners().ByRemoteAssistancePartnerId("remoteAssistancePartner-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

RemoteAssistancePartner remoteAssistancePartner = new RemoteAssistancePartner();
remoteAssistancePartner.setOdataType("#microsoft.graph.remoteAssistancePartner");
remoteAssistancePartner.setDisplayName("Display Name value");
remoteAssistancePartner.setOnboardingUrl("https://example.com/onboardingUrl/");
remoteAssistancePartner.setOnboardingStatus(RemoteAssistanceOnboardingStatus.Onboarding);
OffsetDateTime lastConnectionDateTime = OffsetDateTime.parse("2016-12-31T23:58:36.6670033-08:00");
remoteAssistancePartner.setLastConnectionDateTime(lastConnectionDateTime);
RemoteAssistancePartner result = graphClient.deviceManagement().remoteAssistancePartners().byRemoteAssistancePartnerId("{remoteAssistancePartner-id}").patch(remoteAssistancePartner);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const remoteAssistancePartner = {
  '@odata.type': '#microsoft.graph.remoteAssistancePartner',
  displayName: 'Display Name value',
  onboardingUrl: 'https://example.com/onboardingUrl/',
  onboardingStatus: 'onboarding',
  lastConnectionDateTime: '2016-12-31T23:58:36.6670033-08:00'
};

await client.api('/deviceManagement/remoteAssistancePartners/{remoteAssistancePartnerId}')
	.update(remoteAssistancePartner);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\RemoteAssistancePartner;
use Microsoft\Graph\Generated\Models\RemoteAssistanceOnboardingStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemoteAssistancePartner();
$requestBody->setOdataType('#microsoft.graph.remoteAssistancePartner');
$requestBody->setDisplayName('Display Name value');
$requestBody->setOnboardingUrl('https://example.com/onboardingUrl/');
$requestBody->setOnboardingStatus(new RemoteAssistanceOnboardingStatus('onboarding'));
$requestBody->setLastConnectionDateTime(new \DateTime('2016-12-31T23:58:36.6670033-08:00'));

$result = $graphServiceClient->deviceManagement()->remoteAssistancePartners()->byRemoteAssistancePartnerId('remoteAssistancePartner-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	"@odata.type" = "#microsoft.graph.remoteAssistancePartner"
	displayName = "Display Name value"
	onboardingUrl = "https://example.com/onboardingUrl/"
	onboardingStatus = "onboarding"
	lastConnectionDateTime = [System.DateTime]::Parse("2016-12-31T23:58:36.6670033-08:00")
}

Update-MgDeviceManagementRemoteAssistancePartner -RemoteAssistancePartnerId $remoteAssistancePartnerId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.remote_assistance_partner import RemoteAssistancePartner
from msgraph.generated.models.remote_assistance_onboarding_status import RemoteAssistanceOnboardingStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemoteAssistancePartner(
	odata_type = "#microsoft.graph.remoteAssistancePartner",
	display_name = "Display Name value",
	onboarding_url = "https://example.com/onboardingUrl/",
	onboarding_status = RemoteAssistanceOnboardingStatus.Onboarding,
	last_connection_date_time = "2016-12-31T23:58:36.6670033-08:00",
)

result = await graph_client.device_management.remote_assistance_partners.by_remote_assistance_partner_id('remoteAssistancePartner-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 315

{
  "@odata.type": "#microsoft.graph.remoteAssistancePartner",
  "id": "7443c8b9-c8b9-7443-b9c8-4374b9c84374",
  "displayName": "Display Name value",
  "onboardingUrl": "https://example.com/onboardingUrl/",
  "onboardingStatus": "onboarding",
  "lastConnectionDateTime": "2016-12-31T23:58:36.6670033-08:00"
}
```
