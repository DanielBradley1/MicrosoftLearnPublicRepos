<!-- Source: https://learn.microsoft.com/en-us/graph/api/devicemanagement-alertrecord-changealertrecordsportalnotificationassent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# alertRecord: changeAlertRecordsPortalNotificationAsSent

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Set the **isPortalNotificationSent** property of all [portal notification](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-portalnotification?view=graph-rest-beta) resources associated with the specified [alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) to `true`, marking them as sent. A maximum of 100 [alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) IDs can be received at one time, and a maximum of 100 **portal notification** resources can be changed in the **isPortalNotificationSent** property status.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
POST /deviceManagement/monitoring/alertRecords/changeAlertRecordsPortalNotificationAsSent
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
| alertRecordIds | String collection | A list of up to 100 [alertRecord](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrecord?view=graph-rest-beta) IDs. |

## Response

If successful, this action returns a `202 Accepted` response code.

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
POST https://graph.microsoft.com/beta/deviceManagement/monitoring/alertRecords/changeAlertRecordsPortalNotificationAsSent

{
  "alertRecordIds": [
    "1d2b92e3-539a-481f-b38a-c2c050b422ad",
    "4bf624c4-a801-4631-989c-7f1a3a0d1d83",
  ]

}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.Monitoring.AlertRecords.MicrosoftGraphDeviceManagementChangeAlertRecordsPortalNotificationAsSent;

var requestBody = new ChangeAlertRecordsPortalNotificationAsSentPostRequestBody
{
	AlertRecordIds = new List<string>
	{
		"1d2b92e3-539a-481f-b38a-c2c050b422ad",
		"4bf624c4-a801-4631-989c-7f1a3a0d1d83",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.Monitoring.AlertRecords.MicrosoftGraphDeviceManagementChangeAlertRecordsPortalNotificationAsSent.PostAsync(requestBody);
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
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/devicemanagement"
	  //other-imports
)

requestBody := graphdevicemanagement.NewChangeAlertRecordsPortalNotificationAsSentPostRequestBody()
alertRecordIds := []string {
	"1d2b92e3-539a-481f-b38a-c2c050b422ad",
	"4bf624c4-a801-4631-989c-7f1a3a0d1d83",
}
requestBody.SetAlertRecordIds(alertRecordIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().Monitoring().AlertRecords().MicrosoftGraphDeviceManagementChangeAlertRecordsPortalNotificationAsSent().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.monitoring.alertrecords.microsoftgraphdevicemanagementchangealertrecordsportalnotificationassent.ChangeAlertRecordsPortalNotificationAsSentPostRequestBody changeAlertRecordsPortalNotificationAsSentPostRequestBody = new com.microsoft.graph.beta.devicemanagement.monitoring.alertrecords.microsoftgraphdevicemanagementchangealertrecordsportalnotificationassent.ChangeAlertRecordsPortalNotificationAsSentPostRequestBody();
LinkedList<String> alertRecordIds = new LinkedList<String>();
alertRecordIds.add("1d2b92e3-539a-481f-b38a-c2c050b422ad");
alertRecordIds.add("4bf624c4-a801-4631-989c-7f1a3a0d1d83");
changeAlertRecordsPortalNotificationAsSentPostRequestBody.setAlertRecordIds(alertRecordIds);
graphClient.deviceManagement().monitoring().alertRecords().microsoftGraphDeviceManagementChangeAlertRecordsPortalNotificationAsSent().post(changeAlertRecordsPortalNotificationAsSentPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const changeAlertRecordsPortalNotificationAsSent = {
  alertRecordIds: [
    '1d2b92e3-539a-481f-b38a-c2c050b422ad',
    '4bf624c4-a801-4631-989c-7f1a3a0d1d83',
  ]

};

await client.api('/deviceManagement/monitoring/alertRecords/changeAlertRecordsPortalNotificationAsSent')
	.version('beta')
	.post(changeAlertRecordsPortalNotificationAsSent);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\Monitoring\AlertRecords\MicrosoftGraphDeviceManagementChangeAlertRecordsPortalNotificationAsSent\ChangeAlertRecordsPortalNotificationAsSentPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChangeAlertRecordsPortalNotificationAsSentPostRequestBody();
$requestBody->setAlertRecordIds(['1d2b92e3-539a-481f-b38a-c2c050b422ad', '4bf624c4-a801-4631-989c-7f1a3a0d1d83', 	]);

$graphServiceClient->deviceManagement()->monitoring()->alertRecords()->microsoftGraphDeviceManagementChangeAlertRecordsPortalNotificationAsSent()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement

$params = @{
	alertRecordIds = @(
	"1d2b92e3-539a-481f-b38a-c2c050b422ad"
"4bf624c4-a801-4631-989c-7f1a3a0d1d83"
)
}

Rename-MgBetaDeviceManagementMonitoringAlertRecordPortalNotificationAsSent -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.monitoring.alertrecords.microsoft_graph_device_management_change_alert_records_portal_notification_as_sent.change_alert_records_portal_notification_as_sent_post_request_body import ChangeAlertRecordsPortalNotificationAsSentPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChangeAlertRecordsPortalNotificationAsSentPostRequestBody(
	alert_record_ids = [
		"1d2b92e3-539a-481f-b38a-c2c050b422ad",
		"4bf624c4-a801-4631-989c-7f1a3a0d1d83",
	],
)

await graph_client.device_management.monitoring.alert_records.microsoft_graph_device_management_change_alert_records_portal_notification_as_sent.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

```http
HTTP/1.1 202 ACCEPTED
```
