<!-- Source: https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-post-targetdevicegroups?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Create targetDeviceGroup

Namespace: microsoft.graph

Create a new [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) object for the remoteDesktopSecurityConfiguration object on the servicePrincipal. You can configure a maximum of 10 target device groups for the remoteDesktopSecurityConfiguration object on the servicePrincipal.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Application-RemoteDesktopConfig.ReadWrite.All | Application.ReadWrite.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Application-RemoteDesktopConfig.ReadWrite.All | Application.ReadWrite.All, Application.ReadWrite.OwnedBy, Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
POST /servicePrincipals/{servicePrincipalsId}/remoteDesktopSecurityConfiguration/targetDeviceGroups
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) object.

You can specify the following properties when creating a **targetDeviceGroup**.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Object identifier of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). Required. |
| displayName | String | Display name of the group. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [targetDeviceGroup](https://learn.microsoft.com/en-us/graph/api/resources/targetdevicegroup?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/servicePrincipals/00af5dfb-85da-4b41-a677-0c6b86dd34f8/remoteDesktopSecurityConfiguration/targetDeviceGroups
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.targetDeviceGroup",
  "id": "b9e4eae4-b781-45a1-ce65-f2dd8ac3b696",
  "displayName": "Device Group A"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TargetDeviceGroup
{
	OdataType = "#microsoft.graph.targetDeviceGroup",
	Id = "b9e4eae4-b781-45a1-ce65-f2dd8ac3b696",
	DisplayName = "Device Group A",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].RemoteDesktopSecurityConfiguration.TargetDeviceGroups.PostAsync(requestBody);
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

requestBody := graphmodels.NewTargetDeviceGroup()
id := "b9e4eae4-b781-45a1-ce65-f2dd8ac3b696"
requestBody.SetId(&id) 
displayName := "Device Group A"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
targetDeviceGroups, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").RemoteDesktopSecurityConfiguration().TargetDeviceGroups().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TargetDeviceGroup targetDeviceGroup = new TargetDeviceGroup();
targetDeviceGroup.setOdataType("#microsoft.graph.targetDeviceGroup");
targetDeviceGroup.setId("b9e4eae4-b781-45a1-ce65-f2dd8ac3b696");
targetDeviceGroup.setDisplayName("Device Group A");
TargetDeviceGroup result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").remoteDesktopSecurityConfiguration().targetDeviceGroups().post(targetDeviceGroup);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const targetDeviceGroup = {
  '@odata.type': '#microsoft.graph.targetDeviceGroup',
  id: 'b9e4eae4-b781-45a1-ce65-f2dd8ac3b696',
  displayName: 'Device Group A'
};

await client.api('/servicePrincipals/00af5dfb-85da-4b41-a677-0c6b86dd34f8/remoteDesktopSecurityConfiguration/targetDeviceGroups')
	.post(targetDeviceGroup);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TargetDeviceGroup;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TargetDeviceGroup();
$requestBody->setOdataType('#microsoft.graph.targetDeviceGroup');
$requestBody->setId('b9e4eae4-b781-45a1-ce65-f2dd8ac3b696');
$requestBody->setDisplayName('Device Group A');

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->remoteDesktopSecurityConfiguration()->targetDeviceGroups()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	"@odata.type" = "#microsoft.graph.targetDeviceGroup"
	id = "b9e4eae4-b781-45a1-ce65-f2dd8ac3b696"
	displayName = "Device Group A"
}

New-MgServicePrincipalRemoteDesktopSecurityConfigurationTargetDeviceGroup -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.target_device_group import TargetDeviceGroup
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TargetDeviceGroup(
	odata_type = "#microsoft.graph.targetDeviceGroup",
	id = "b9e4eae4-b781-45a1-ce65-f2dd8ac3b696",
	display_name = "Device Group A",
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').remote_desktop_security_configuration.target_device_groups.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.targetDeviceGroup",
  "id": "b9e4eae4-b781-45a1-ce65-f2dd8ac3b696",
  "displayName": "Device Group A"
}
```
