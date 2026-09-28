<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-cloudapps?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-27 -->

# Create cloudPcCloudApp

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object.

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
POST /deviceManagement/virtualEndpoint/cloudApps
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object.

The following table shows the properties available when you create a **cloudPcCloudApp**.

| Property | Type | Description |
| :--- | :--- | :--- |
| appDetail | [cloudPcCloudAppDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudappdetail?view=graph-rest-beta) | The details about the cloud app. This is a polymorphic type. Use **@odata.type** to specify the derived type: `#microsoft.graph.cloudPcFilePathAppDetail` for apps with a manually specified file path, or `#microsoft.graph.cloudPcAutomaticDiscoveredAppDetail` for automatically discovered apps. Required. |
| description | String | The description associated with the cloud app. The maximum allowed length for this property is 512 characters. Optional. |
| discoveredAppName | String | Name of the discovered app associated with the cloud app. Required. |
| displayName | String | The display name for the cloud app. Must be unique within a single provisioning policy. The maximum allowed length for this property is 64 characters. Required. |
| provisioningPolicyId | String | The ID of the provisioning policy associated with this cloud app. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudPcCloudApp](https://learn.microsoft.com/en-us/graph/api/resources/cloudpccloudapp?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows how to create a cloud app using the **cloudPcFilePathAppDetail** type.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudApps
Content-Type: application/json

{
  "displayName": "Remote Desktop Connection",
  "discoveredAppName": "Remote Desktop Connection",
  "provisioningPolicyId": "e31f75e9-25a8-41e9-a9d5-ce8fd484af15",
  "description": "",
  "appDetail": {
    "@odata.type": "#microsoft.graph.cloudPcFilePathAppDetail",
    "filePath": "C:\\Windows\\system32\\mstsc.exe",
    "commandLineArguments": "",
    "iconPath": "C:\\Windows\\system32\\mstsc.exe",
    "iconIndex": 0
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcCloudApp
{
	DisplayName = "Remote Desktop Connection",
	DiscoveredAppName = "Remote Desktop Connection",
	ProvisioningPolicyId = "e31f75e9-25a8-41e9-a9d5-ce8fd484af15",
	Description = "",
	AppDetail = new CloudPcFilePathAppDetail
	{
		OdataType = "#microsoft.graph.cloudPcFilePathAppDetail",
		FilePath = "C:\Windows\system32\mstsc.exe",
		CommandLineArguments = "",
		IconPath = "C:\Windows\system32\mstsc.exe",
		IconIndex = 0,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudApps.PostAsync(requestBody);
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
displayName := "Remote Desktop Connection"
requestBody.SetDisplayName(&displayName) 
discoveredAppName := "Remote Desktop Connection"
requestBody.SetDiscoveredAppName(&discoveredAppName) 
provisioningPolicyId := "e31f75e9-25a8-41e9-a9d5-ce8fd484af15"
requestBody.SetProvisioningPolicyId(&provisioningPolicyId) 
description := ""
requestBody.SetDescription(&description) 
appDetail := graphmodels.NewCloudPcFilePathAppDetail()
filePath := "C:\Windows\system32\mstsc.exe"
appDetail.SetFilePath(&filePath) 
commandLineArguments := ""
appDetail.SetCommandLineArguments(&commandLineArguments) 
iconPath := "C:\Windows\system32\mstsc.exe"
appDetail.SetIconPath(&iconPath) 
iconIndex := int32(0)
appDetail.SetIconIndex(&iconIndex) 
requestBody.SetAppDetail(appDetail)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cloudApps, err := graphClient.DeviceManagement().VirtualEndpoint().CloudApps().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcCloudApp cloudPcCloudApp = new CloudPcCloudApp();
cloudPcCloudApp.setDisplayName("Remote Desktop Connection");
cloudPcCloudApp.setDiscoveredAppName("Remote Desktop Connection");
cloudPcCloudApp.setProvisioningPolicyId("e31f75e9-25a8-41e9-a9d5-ce8fd484af15");
cloudPcCloudApp.setDescription("");
CloudPcFilePathAppDetail appDetail = new CloudPcFilePathAppDetail();
appDetail.setOdataType("#microsoft.graph.cloudPcFilePathAppDetail");
appDetail.setFilePath("C:\Windows\system32\mstsc.exe");
appDetail.setCommandLineArguments("");
appDetail.setIconPath("C:\Windows\system32\mstsc.exe");
appDetail.setIconIndex(0);
cloudPcCloudApp.setAppDetail(appDetail);
CloudPcCloudApp result = graphClient.deviceManagement().virtualEndpoint().cloudApps().post(cloudPcCloudApp);
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
  displayName: 'Remote Desktop Connection',
  discoveredAppName: 'Remote Desktop Connection',
  provisioningPolicyId: 'e31f75e9-25a8-41e9-a9d5-ce8fd484af15',
  description: '',
  appDetail: {
    '@odata.type': '#microsoft.graph.cloudPcFilePathAppDetail',
    filePath: 'C:\\Windows\\system32\\mstsc.exe',
    commandLineArguments: '',
    iconPath: 'C:\\Windows\\system32\\mstsc.exe',
    iconIndex: 0
  }
};

await client.api('/deviceManagement/virtualEndpoint/cloudApps')
	.version('beta')
	.post(cloudPcCloudApp);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcCloudApp;
use Microsoft\Graph\Beta\Generated\Models\CloudPcFilePathAppDetail;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcCloudApp();
$requestBody->setDisplayName('Remote Desktop Connection');
$requestBody->setDiscoveredAppName('Remote Desktop Connection');
$requestBody->setProvisioningPolicyId('e31f75e9-25a8-41e9-a9d5-ce8fd484af15');
$requestBody->setDescription('');
$appDetail = new CloudPcFilePathAppDetail();
$appDetail->setOdataType('#microsoft.graph.cloudPcFilePathAppDetail');
$appDetail->setFilePath('C:\Windows\system32\mstsc.exe');
$appDetail->setCommandLineArguments('');
$appDetail->setIconPath('C:\Windows\system32\mstsc.exe');
$appDetail->setIconIndex(0);
$requestBody->setAppDetail($appDetail);

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudApps()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_cloud_app import CloudPcCloudApp
from msgraph_beta.generated.models.cloud_pc_file_path_app_detail import CloudPcFilePathAppDetail
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcCloudApp(
	display_name = "Remote Desktop Connection",
	discovered_app_name = "Remote Desktop Connection",
	provisioning_policy_id = "e31f75e9-25a8-41e9-a9d5-ce8fd484af15",
	description = "",
	app_detail = CloudPcFilePathAppDetail(
		odata_type = "#microsoft.graph.cloudPcFilePathAppDetail",
		file_path = "C:\Windows\system32\mstsc.exe",
		command_line_arguments = "",
		icon_path = "C:\Windows\system32\mstsc.exe",
		icon_index = 0,
	),
)

result = await graph_client.device_management.virtual_endpoint.cloud_apps.post(request_body)
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#deviceManagement/virtualEndpoint/cloudApps/$entity",
  "id": "60a7bbf2-d831-4dc8-8375-1253403f7e74",
  "displayName": "Remote Desktop Connection",
  "discoveredAppName": "Remote Desktop Connection",
  "provisioningPolicyId": "e31f75e9-25a8-41e9-a9d5-ce8fd484af15",
  "description": "",
  "appDetail": {
    "@odata.type": "#microsoft.graph.cloudPcFilePathAppDetail",
    "filePath": "C:\\Windows\\system32\\mstsc.exe",
    "commandLineArguments": "",
    "iconPath": "C:\\Windows\\system32\\mstsc.exe",
    "iconIndex": 0
  },
  "addedDateTime": "2025-11-13T07:37:22.3049326Z",
  "lastPublishedDateTime": "0001-01-01T00:00:00Z",
  "appStatus": "preparing",
  "actionFailedErrorCode": null,
  "actionFailedErrorMessage": null,
  "availableToUser": false,
  "scopeIds": [
    "0"
  ]
}
```
