<!-- Source: https://learn.microsoft.com/en-us/graph/api/m365appsinstallationoptions-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-19 -->

# Update m365AppsInstallationOptions

Namespace: microsoft.graph

Update the properties of an [m365AppsInstallationOptions](https://learn.microsoft.com/en-us/graph/api/resources/m365appsinstallationoptions?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OrgSettings-Microsoft365Install.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OrgSettings-Microsoft365Install.ReadWrite.All | Not available. |

When calling on behalf of a user, the user needs to belong to the Office apps administrator role.

## HTTP request

```http
PATCH /admin/microsoft365Apps/installationOptions
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
| updateChannel | [appsUpdateChannelType](https://learn.microsoft.com/en-us/graph/api/resources/m365appsinstallationoptions?view=graph-rest-1.0#appsupdatechanneltype-values) | Specifies how often users get feature updates for Microsoft 365 apps installed on devices running Windows. The possible values are: `current`, `monthlyEnterprise`, or `semiAnnual`, with corresponding update frequencies of `As soon as they're ready`, `Once a month`, and `Every six months`. Include the `Prefer: include-unknown-enum-members` header to explicitly request for enum values beyond `unknownFutureValue`. |
| appsForWindows | [appsInstallationOptionsForWindows](https://learn.microsoft.com/en-us/graph/api/resources/appsinstallationoptionsforwindows?view=graph-rest-1.0) | The Microsoft 365 apps installation options container object for a Windows platform. |
| appsForMac | [appsInstallationOptionsForMac](https://learn.microsoft.com/en-us/graph/api/resources/appsinstallationoptionsformac?view=graph-rest-1.0) | The Microsoft 365 apps installation options container object for a MAC platform. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Set the Microsoft 365 update channel

#### Request

The following examples show a requet to set the Microsoft 365 update channel.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/admin/microsoft365Apps/installationOptions
Content-Type: application/json

{
  "updateChannel": "current"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new M365AppsInstallationOptions
{
	UpdateChannel = AppsUpdateChannelType.Current,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Microsoft365Apps.InstallationOptions.PatchAsync(requestBody);
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

requestBody := graphmodels.NewM365AppsInstallationOptions()
updateChannel := graphmodels.CURRENT_APPSUPDATECHANNELTYPE 
requestBody.SetUpdateChannel(&updateChannel) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
installationOptions, err := graphClient.Admin().Microsoft365Apps().InstallationOptions().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

M365AppsInstallationOptions m365AppsInstallationOptions = new M365AppsInstallationOptions();
m365AppsInstallationOptions.setUpdateChannel(AppsUpdateChannelType.Current);
M365AppsInstallationOptions result = graphClient.admin().microsoft365Apps().installationOptions().patch(m365AppsInstallationOptions);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const m365AppsInstallationOptions = {
  updateChannel: 'current'
};

await client.api('/admin/microsoft365Apps/installationOptions')
	.update(m365AppsInstallationOptions);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\M365AppsInstallationOptions;
use Microsoft\Graph\Generated\Models\AppsUpdateChannelType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new M365AppsInstallationOptions();
$requestBody->setUpdateChannel(new AppsUpdateChannelType('current'));

$result = $graphServiceClient->admin()->microsoft365Apps()->installationOptions()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.m365_apps_installation_options import M365AppsInstallationOptions
from msgraph.generated.models.apps_update_channel_type import AppsUpdateChannelType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = M365AppsInstallationOptions(
	update_channel = AppsUpdateChannelType.Current,
)

result = await graph_client.admin.microsoft365_apps.installation_options.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Set the Microsoft 365 apps installation options

#### Request

The following example shows a request to set the Microsoft 365 apps installation options for a platform.

```http
PATCH https://graph.microsoft.com/v1.0/admin/microsoft365Apps/installationOptions
Content-Type: application/json

{
  "appsForWindows": {
    "isMicrosoft365AppsEnabled": true,
    "isVisioEnabled": false
  }
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Update channel and installation options

#### Request

The following example shows a request to set Microsoft 365 apps update channel and installation options simutaneously.

```http
PATCH https://graph.microsoft.com/v1.0/admin/microsoft365Apps/installationOptions
Content-Type: application/json

{
  "updateChannel": "monthlyEnterprise",
  "appsForWindows": {
    "isMicrosoft365AppsEnabled": true,
    "isProjectEnabled": false,
    "isSkypeForBusinessEnabled": true,
    "isVisioEnabled": false
  },
  "appsForMac": {
    "isMicrosoft365AppsEnabled": true,
    "isSkypeForBusinessEnabled": false
  }
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
