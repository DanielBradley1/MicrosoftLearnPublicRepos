<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcorganizationsettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Update cloudPcOrganizationSettings

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of the [cloudPcOrganizationSettings](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcorganizationsettings?view=graph-rest-beta) object in a tenant.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | CloudPC.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | CloudPC.Read.All |

## HTTP request

```http
PATCH /deviceManagement/virtualEndpoint/organizationSettings
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
| enableMEMAutoEnroll | Boolean | Specifies whether new Cloud PCs will be automatically enrolled in Microsoft Endpoint Manager\(MEM\). The default value is `false`. Optional. |
| enableSingleSignOn | Boolean | `True` if the provisioned Cloud PC can be accessed by single sign-on. `False` indicates that the provisioned Cloud PC doesn't support this feature. Default value is `false`. Windows 365 users can use single sign-on to authenticate to Microsoft Entra ID with passwordless options \(for example, FIDO keys\) to access their Cloud PC. Optional. |
| osVersion | cloudPcOperatingSystem | The version of the operating system \(OS\) to provision on Cloud PCs. The possible values are: `windows10`, `windows11`, `unknownFutureValue`. Optional. |
| userAccountType | cloudPcUserAccountType | The account type of the user on provisioned Cloud PCs. The possible values are: `standardUser`, `administrator`, `unknownFutureValue`. Optional. |
| windowsSettings | cloudPcWindowsSettings | The settings to apply to Windows while creating Cloud PCs for this organization. The default language value is `en-US`. |

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
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/organizationSettings
Content-Type: application/json
Content-length: 127

{
  "@odata.type": "#microsoft.graph.cloudPcOrganizationSettings",
  "enableMEMAutoEnroll": true,
  "osVersion": "windows11",
  "userAccountType": "standardUser",
  "windowsSettings": {
    "language": "en-US"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcOrganizationSettings
{
	OdataType = "#microsoft.graph.cloudPcOrganizationSettings",
	EnableMEMAutoEnroll = true,
	OsVersion = CloudPcOperatingSystem.Windows11,
	UserAccountType = CloudPcUserAccountType.StandardUser,
	WindowsSettings = new CloudPcWindowsSettings
	{
		Language = "en-US",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.OrganizationSettings.PatchAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcOrganizationSettings()
enableMEMAutoEnroll := true
requestBody.SetEnableMEMAutoEnroll(&enableMEMAutoEnroll) 
osVersion := graphmodels.WINDOWS11_CLOUDPCOPERATINGSYSTEM 
requestBody.SetOsVersion(&osVersion) 
userAccountType := graphmodels.STANDARDUSER_CLOUDPCUSERACCOUNTTYPE 
requestBody.SetUserAccountType(&userAccountType) 
windowsSettings := graphmodels.NewCloudPcWindowsSettings()
language := "en-US"
windowsSettings.SetLanguage(&language) 
requestBody.SetWindowsSettings(windowsSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
organizationSettings, err := graphClient.DeviceManagement().VirtualEndpoint().OrganizationSettings().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcOrganizationSettings cloudPcOrganizationSettings = new CloudPcOrganizationSettings();
cloudPcOrganizationSettings.setOdataType("#microsoft.graph.cloudPcOrganizationSettings");
cloudPcOrganizationSettings.setEnableMEMAutoEnroll(true);
cloudPcOrganizationSettings.setOsVersion(CloudPcOperatingSystem.Windows11);
cloudPcOrganizationSettings.setUserAccountType(CloudPcUserAccountType.StandardUser);
CloudPcWindowsSettings windowsSettings = new CloudPcWindowsSettings();
windowsSettings.setLanguage("en-US");
cloudPcOrganizationSettings.setWindowsSettings(windowsSettings);
CloudPcOrganizationSettings result = graphClient.deviceManagement().virtualEndpoint().organizationSettings().patch(cloudPcOrganizationSettings);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcOrganizationSettings = {
  '@odata.type': '#microsoft.graph.cloudPcOrganizationSettings',
  enableMEMAutoEnroll: true,
  osVersion: 'windows11',
  userAccountType: 'standardUser',
  windowsSettings: {
    language: 'en-US'
  }
};

await client.api('/deviceManagement/virtualEndpoint/organizationSettings')
	.version('beta')
	.update(cloudPcOrganizationSettings);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcOrganizationSettings;
use Microsoft\Graph\Beta\Generated\Models\CloudPcOperatingSystem;
use Microsoft\Graph\Beta\Generated\Models\CloudPcUserAccountType;
use Microsoft\Graph\Beta\Generated\Models\CloudPcWindowsSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcOrganizationSettings();
$requestBody->setOdataType('#microsoft.graph.cloudPcOrganizationSettings');
$requestBody->setEnableMEMAutoEnroll(true);
$requestBody->setOsVersion(new CloudPcOperatingSystem('windows11'));
$requestBody->setUserAccountType(new CloudPcUserAccountType('standardUser'));
$windowsSettings = new CloudPcWindowsSettings();
$windowsSettings->setLanguage('en-US');
$requestBody->setWindowsSettings($windowsSettings);

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->organizationSettings()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Administration

$params = @{
	"@odata.type" = "#microsoft.graph.cloudPcOrganizationSettings"
	enableMEMAutoEnroll = $true
	osVersion = "windows11"
	userAccountType = "standardUser"
	windowsSettings = @{
		language = "en-US"
	}
}

Update-MgBetaDeviceManagementVirtualEndpointOrganizationSetting -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_organization_settings import CloudPcOrganizationSettings
from msgraph_beta.generated.models.cloud_pc_operating_system import CloudPcOperatingSystem
from msgraph_beta.generated.models.cloud_pc_user_account_type import CloudPcUserAccountType
from msgraph_beta.generated.models.cloud_pc_windows_settings import CloudPcWindowsSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcOrganizationSettings(
	odata_type = "#microsoft.graph.cloudPcOrganizationSettings",
	enable_m_e_m_auto_enroll = True,
	os_version = CloudPcOperatingSystem.Windows11,
	user_account_type = CloudPcUserAccountType.StandardUser,
	windows_settings = CloudPcWindowsSettings(
		language = "en-US",
	),
)

result = await graph_client.device_management.virtual_endpoint.organization_settings.patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
