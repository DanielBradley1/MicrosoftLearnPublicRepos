<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcusersetting-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-13 -->

# Update cloudPcUserSetting

Namespace: microsoft.graph

Update the properties of a [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH /deviceManagement/virtualEndpoint/userSettings/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object.

The following table shows the properties that are required when you update the [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The setting name displayed in the user interface. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the setting was last modified. The timestamp type represents the date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| localAdminEnabled | Boolean | To turn on the local admin option, change this setting to `true`. |
| resetEnabled | Boolean | Indicates whether an end user is allowed to reset their Cloud PC. When `true`, the user is allowed to reset their Cloud PC. When `false`, end-user initiated reset isn't allowed. The default value is `false`. |
| restorePointSetting | [cloudPcRestorePointSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcrestorepointsetting?view=graph-rest-1.0) | Defines how frequently a restore point is created \(that is, a snapshot is taken\) for users' provisioned Cloud PCs \(default is 12 hours\), and whether the user is allowed to restore their own Cloud PCs to a backup made at a specific point in time. |

## Response

If successful, this method returns a `200 OK` response code and an updated [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/userSettings/b0c2d35f-3385-46c8-a6f5-6c3dfad7ffff
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcUserSetting",
  "displayName": "Example",
  "restorePointSetting": {
    "frequencyType": "sixteenHours",
    "userRestoreEnabled": true
  },
  "localAdminEnabled": false,
  "resetEnabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CloudPcUserSetting
{
	OdataType = "#microsoft.graph.cloudPcUserSetting",
	DisplayName = "Example",
	RestorePointSetting = new CloudPcRestorePointSetting
	{
		FrequencyType = CloudPcRestorePointFrequencyType.SixteenHours,
		UserRestoreEnabled = true,
	},
	LocalAdminEnabled = false,
	ResetEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.UserSettings["{cloudPcUserSetting-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcUserSetting()
displayName := "Example"
requestBody.SetDisplayName(&displayName) 
restorePointSetting := graphmodels.NewCloudPcRestorePointSetting()
frequencyType := graphmodels.SIXTEENHOURS_CLOUDPCRESTOREPOINTFREQUENCYTYPE 
restorePointSetting.SetFrequencyType(&frequencyType) 
userRestoreEnabled := true
restorePointSetting.SetUserRestoreEnabled(&userRestoreEnabled) 
requestBody.SetRestorePointSetting(restorePointSetting)
localAdminEnabled := false
requestBody.SetLocalAdminEnabled(&localAdminEnabled) 
resetEnabled := true
requestBody.SetResetEnabled(&resetEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
userSettings, err := graphClient.DeviceManagement().VirtualEndpoint().UserSettings().ByCloudPcUserSettingId("cloudPcUserSetting-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcUserSetting cloudPcUserSetting = new CloudPcUserSetting();
cloudPcUserSetting.setOdataType("#microsoft.graph.cloudPcUserSetting");
cloudPcUserSetting.setDisplayName("Example");
CloudPcRestorePointSetting restorePointSetting = new CloudPcRestorePointSetting();
restorePointSetting.setFrequencyType(CloudPcRestorePointFrequencyType.SixteenHours);
restorePointSetting.setUserRestoreEnabled(true);
cloudPcUserSetting.setRestorePointSetting(restorePointSetting);
cloudPcUserSetting.setLocalAdminEnabled(false);
cloudPcUserSetting.setResetEnabled(true);
CloudPcUserSetting result = graphClient.deviceManagement().virtualEndpoint().userSettings().byCloudPcUserSettingId("{cloudPcUserSetting-id}").patch(cloudPcUserSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcUserSetting = {
  '@odata.type': '#microsoft.graph.cloudPcUserSetting',
  displayName: 'Example',
  restorePointSetting: {
    frequencyType: 'sixteenHours',
    userRestoreEnabled: true
  },
  localAdminEnabled: false,
  resetEnabled: true
};

await client.api('/deviceManagement/virtualEndpoint/userSettings/b0c2d35f-3385-46c8-a6f5-6c3dfad7ffff')
	.update(cloudPcUserSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CloudPcUserSetting;
use Microsoft\Graph\Generated\Models\CloudPcRestorePointSetting;
use Microsoft\Graph\Generated\Models\CloudPcRestorePointFrequencyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcUserSetting();
$requestBody->setOdataType('#microsoft.graph.cloudPcUserSetting');
$requestBody->setDisplayName('Example');
$restorePointSetting = new CloudPcRestorePointSetting();
$restorePointSetting->setFrequencyType(new CloudPcRestorePointFrequencyType('sixteenHours'));
$restorePointSetting->setUserRestoreEnabled(true);
$requestBody->setRestorePointSetting($restorePointSetting);
$requestBody->setLocalAdminEnabled(false);
$requestBody->setResetEnabled(true);

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->userSettings()->byCloudPcUserSettingId('cloudPcUserSetting-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	"@odata.type" = "#microsoft.graph.cloudPcUserSetting"
	displayName = "Example"
	restorePointSetting = @{
		frequencyType = "sixteenHours"
		userRestoreEnabled = $true
	}
	localAdminEnabled = $false
	resetEnabled = $true
}

Update-MgDeviceManagementVirtualEndpointUserSetting -CloudPcUserSettingId $cloudPcUserSettingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cloud_pc_user_setting import CloudPcUserSetting
from msgraph.generated.models.cloud_pc_restore_point_setting import CloudPcRestorePointSetting
from msgraph.generated.models.cloud_pc_restore_point_frequency_type import CloudPcRestorePointFrequencyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcUserSetting(
	odata_type = "#microsoft.graph.cloudPcUserSetting",
	display_name = "Example",
	restore_point_setting = CloudPcRestorePointSetting(
		frequency_type = CloudPcRestorePointFrequencyType.SixteenHours,
		user_restore_enabled = True,
	),
	local_admin_enabled = False,
	reset_enabled = True,
)

result = await graph_client.device_management.virtual_endpoint.user_settings.by_cloud_pc_user_setting_id('cloudPcUserSetting-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
