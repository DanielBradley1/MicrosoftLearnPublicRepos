<!-- Source: https://learn.microsoft.com/en-us/graph/api/remotedesktopsecurityconfiguration-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Update remoteDesktopSecurityConfiguration

Namespace: microsoft.graph

Update the properties of a [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object on the servicePrincipal. Use this configuration to enable or disable the Microsoft Entra ID [Remote Desktop Services \(RDS\) authentication protocol](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/dc43f040-d75d-49a9-90c6-0c9999281136) to authenticate a user to [Microsoft Entra joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-directory-join) or [Microsoft Entra hybrid joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-hybrid-join) devices.

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
| Application | Application-RemoteDesktopConfig.ReadWrite.All | Application.ReadWrite.All, Directory.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Application Administrator
- Cloud Application Administrator

## HTTP request

```http
PATCH /servicePrincipals/{servicePrincipalsId}/remoteDesktopSecurityConfiguration
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
| isRemoteDesktopProtocolEnabled | Boolean | Whether new Microsoft Entra ID [Remote Desktop Services \(RDS\) authentication protocol](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-rdpbcgr/dc43f040-d75d-49a9-90c6-0c9999281136) to authenticate a user to [Microsoft Entra joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-directory-join) or [Microsoft Entra hybrid joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-hybrid-join) devices.over RDP is enabled or not. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/servicePrincipals/00af5dfb-85da-4b41-a677-0c6b86dd34f8/remoteDesktopSecurityConfiguration
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.remoteDesktopSecurityConfiguration",
  "isRemoteDesktopProtocolEnabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new RemoteDesktopSecurityConfiguration
{
	OdataType = "#microsoft.graph.remoteDesktopSecurityConfiguration",
	IsRemoteDesktopProtocolEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.ServicePrincipals["{servicePrincipal-id}"].RemoteDesktopSecurityConfiguration.PatchAsync(requestBody);
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

requestBody := graphmodels.NewRemoteDesktopSecurityConfiguration()
isRemoteDesktopProtocolEnabled := true
requestBody.SetIsRemoteDesktopProtocolEnabled(&isRemoteDesktopProtocolEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remoteDesktopSecurityConfiguration, err := graphClient.ServicePrincipals().ByServicePrincipalId("servicePrincipal-id").RemoteDesktopSecurityConfiguration().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

RemoteDesktopSecurityConfiguration remoteDesktopSecurityConfiguration = new RemoteDesktopSecurityConfiguration();
remoteDesktopSecurityConfiguration.setOdataType("#microsoft.graph.remoteDesktopSecurityConfiguration");
remoteDesktopSecurityConfiguration.setIsRemoteDesktopProtocolEnabled(true);
RemoteDesktopSecurityConfiguration result = graphClient.servicePrincipals().byServicePrincipalId("{servicePrincipal-id}").remoteDesktopSecurityConfiguration().patch(remoteDesktopSecurityConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const remoteDesktopSecurityConfiguration = {
  '@odata.type': '#microsoft.graph.remoteDesktopSecurityConfiguration',
  isRemoteDesktopProtocolEnabled: true
};

await client.api('/servicePrincipals/00af5dfb-85da-4b41-a677-0c6b86dd34f8/remoteDesktopSecurityConfiguration')
	.update(remoteDesktopSecurityConfiguration);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\RemoteDesktopSecurityConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemoteDesktopSecurityConfiguration();
$requestBody->setOdataType('#microsoft.graph.remoteDesktopSecurityConfiguration');
$requestBody->setIsRemoteDesktopProtocolEnabled(true);

$result = $graphServiceClient->servicePrincipals()->byServicePrincipalId('servicePrincipal-id')->remoteDesktopSecurityConfiguration()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Applications

$params = @{
	"@odata.type" = "#microsoft.graph.remoteDesktopSecurityConfiguration"
	isRemoteDesktopProtocolEnabled = $true
}

Update-MgServicePrincipalRemoteDesktopSecurityConfiguration -ServicePrincipalId $servicePrincipalId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.remote_desktop_security_configuration import RemoteDesktopSecurityConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemoteDesktopSecurityConfiguration(
	odata_type = "#microsoft.graph.remoteDesktopSecurityConfiguration",
	is_remote_desktop_protocol_enabled = True,
)

result = await graph_client.service_principals.by_service_principal_id('servicePrincipal-id').remote_desktop_security_configuration.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.remoteDesktopSecurityConfiguration",
  "id": "ca738153-c98a-f822-a7d1-5a6e1058462b",
  "isRemoteDesktopProtocolEnabled": true
}
```
