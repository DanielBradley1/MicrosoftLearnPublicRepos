<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpccloudapp-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Update cloudPcCloudApp

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object, such as the display name or icon path.

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
PATCH /deviceManagement/virtualEndpoint/cloudApps/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object.

The following table shows the properties that you can use when you update a **cloudPcCloudApp**.

| Property | Type | Description |
| :--- | :--- | :--- |
| appDetail | [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta) | The details about the cloud app. This is a polymorphic type. Use **@odata.type** to specify the derived type: `#microsoft.graph.cloudPcFilePathAppDetail` for apps with a manually specified file path, or `#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail` for automatically discovered apps. These values come initially from the **appDetail** property of the associated discovered app. The **iconPath**, **iconIndex**, and **commandLineArguments** properties can be changed as needed when you update the cloud app. Supports `$select`. Optional. |
| description | String | The description associated with the cloud app. The maximum allowed length for this property is 512 characters. Supports `$filter`, `$select`, and `$orderBy`. Optional. |
| displayName | String | The display name for the cloud app that appears on the end-user portal and must be unique within a single provisioning policy. It uses the discovered app name as the default value. The maximum allowed length for this property is 64 characters. For example, `Paint`. Supports `$filter`, `$select`, and `$orderBy`. Optional. |

## Response

If successful, this method returns a `204 No Content` response code.

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
PATCH https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudApps/40d0e128-de93-41dc-89ec-33d84bb662a0
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcCloudApp",
  "displayName": "Cloud App example3",
  "appDetail": {
    "@odata.type": "#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail",
    "iconPath": "C:\\Windows\\system32\\WindowsPowerShell\\v1.0\\powershell_ise.exe"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcCloudApp
{
	OdataType = "#microsoft.graph.cloudPcCloudApp",
	DisplayName = "Cloud App example3",
	AppDetail = new CloudPcAutomaticDiscoveredAppDetail
	{
		OdataType = "#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail",
		IconPath = "C:\Windows\system32\WindowsPowerShell\v1.0\powershell_ise.exe",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudApps["{cloudPcCloudApp-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcCloudApp()
displayName := "Cloud App example3"
requestBody.SetDisplayName(&displayName) 
appDetail := graphmodels.NewCloudPcAutomaticDiscoveredAppDetail()
iconPath := "C:\Windows\system32\WindowsPowerShell\v1.0\powershell_ise.exe"
appDetail.SetIconPath(&iconPath) 
requestBody.SetAppDetail(appDetail)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cloudApps, err := graphClient.DeviceManagement().VirtualEndpoint().CloudApps().ByCloudPcCloudAppId("cloudPcCloudApp-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcCloudApp cloudPcCloudApp = new CloudPcCloudApp();
cloudPcCloudApp.setOdataType("#microsoft.graph.cloudPcCloudApp");
cloudPcCloudApp.setDisplayName("Cloud App example3");
CloudPcAutomaticDiscoveredAppDetail appDetail = new CloudPcAutomaticDiscoveredAppDetail();
appDetail.setOdataType("#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail");
appDetail.setIconPath("C:\Windows\system32\WindowsPowerShell\v1.0\powershell_ise.exe");
cloudPcCloudApp.setAppDetail(appDetail);
CloudPcCloudApp result = graphClient.deviceManagement().virtualEndpoint().cloudApps().byCloudPcCloudAppId("{cloudPcCloudApp-id}").patch(cloudPcCloudApp);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcCloudApp = {
  '@odata.type': '#microsoft.graph.cloudPcCloudApp',
  displayName: 'Cloud App example3',
  appDetail: {
    '@odata.type': '#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail',
    iconPath: 'C:\\Windows\\system32\\WindowsPowerShell\\v1.0\\powershell_ise.exe'
  }
};

await client.api('/deviceManagement/virtualEndpoint/cloudApps/40d0e128-de93-41dc-89ec-33d84bb662a0')
	.version('beta')
	.update(cloudPcCloudApp);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcCloudApp;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAutomaticDiscoveredAppDetail;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcCloudApp();
$requestBody->setOdataType('#microsoft.graph.cloudPcCloudApp');
$requestBody->setDisplayName('Cloud App example3');
$appDetail = new CloudPcAutomaticDiscoveredAppDetail();
$appDetail->setOdataType('#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail');
$appDetail->setIconPath('C:\Windows\system32\WindowsPowerShell\v1.0\powershell_ise.exe');
$requestBody->setAppDetail($appDetail);

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudApps()->byCloudPcCloudAppId('cloudPcCloudApp-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_cloud_app import CloudPcCloudApp
from msgraph_beta.generated.models.cloud_pc_automatic_discovered_app_detail import CloudPcAutomaticDiscoveredAppDetail
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcCloudApp(
	odata_type = "#microsoft.graph.cloudPcCloudApp",
	display_name = "Cloud App example3",
	app_detail = CloudPcAutomaticDiscoveredAppDetail(
		odata_type = "#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail",
		icon_path = "C:\Windows\system32\WindowsPowerShell\v1.0\powershell_ise.exe",
	),
)

result = await graph_client.device_management.virtual_endpoint.cloud_apps.by_cloud_pc_cloud_app_id('cloudPcCloudApp-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
