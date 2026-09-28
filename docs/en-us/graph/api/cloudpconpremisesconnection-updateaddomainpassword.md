<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-updateaddomainpassword?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# cloudPcOnPremisesConnection: updateAdDomainPassword

Namespace: microsoft.graph

Update the Active Directory domain password for a successful [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0). This API is supported when the type of the **cloudPcOnPremisesConnection** object is `hybridAzureADJoin`.

Important

**On-premises network connection** has been renamed as **Azure network connection**. **cloudPcOnPremisesConnection** objects here are equivalent to **Azure network connection** for the Cloud PC product.

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
POST /deviceManagement/virtualEndpoint/onPremisesConnections/{id}/updateAdDomainPassword
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameter that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| adDomainPassword | String | The password associated with the **adDomainUsername**. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/onPremisesConnections/07f12770-a225-4957-9127-0d247cf4ffff/updateAdDomainPassword
Content-Type: application/json

{
  "adDomainPassword": "AdDomainPassword_XXXX"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DeviceManagement.VirtualEndpoint.OnPremisesConnections.Item.UpdateAdDomainPassword;

var requestBody = new UpdateAdDomainPasswordPostRequestBody
{
	AdDomainPassword = "AdDomainPassword_XXXX",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.OnPremisesConnections["{cloudPcOnPremisesConnection-id}"].UpdateAdDomainPassword.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-sdk-go/devicemanagement"
	  //other-imports
)

requestBody := graphdevicemanagement.NewUpdateAdDomainPasswordPostRequestBody()
adDomainPassword := "AdDomainPassword_XXXX"
requestBody.SetAdDomainPassword(&adDomainPassword) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().OnPremisesConnections().ByCloudPcOnPremisesConnectionId("cloudPcOnPremisesConnection-id").UpdateAdDomainPassword().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.devicemanagement.virtualendpoint.onpremisesconnections.item.updateaddomainpassword.UpdateAdDomainPasswordPostRequestBody updateAdDomainPasswordPostRequestBody = new com.microsoft.graph.devicemanagement.virtualendpoint.onpremisesconnections.item.updateaddomainpassword.UpdateAdDomainPasswordPostRequestBody();
updateAdDomainPasswordPostRequestBody.setAdDomainPassword("AdDomainPassword_XXXX");
graphClient.deviceManagement().virtualEndpoint().onPremisesConnections().byCloudPcOnPremisesConnectionId("{cloudPcOnPremisesConnection-id}").updateAdDomainPassword().post(updateAdDomainPasswordPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateAdDomainPassword = {
  adDomainPassword: 'AdDomainPassword_XXXX'
};

await client.api('/deviceManagement/virtualEndpoint/onPremisesConnections/07f12770-a225-4957-9127-0d247cf4ffff/updateAdDomainPassword')
	.post(updateAdDomainPassword);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DeviceManagement\VirtualEndpoint\OnPremisesConnections\Item\UpdateAdDomainPassword\UpdateAdDomainPasswordPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateAdDomainPasswordPostRequestBody();
$requestBody->setAdDomainPassword('AdDomainPassword_XXXX');

$graphServiceClient->deviceManagement()->virtualEndpoint()->onPremisesConnections()->byCloudPcOnPremisesConnectionId('cloudPcOnPremisesConnection-id')->updateAdDomainPassword()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	adDomainPassword = "AdDomainPassword_XXXX"
}

Update-MgDeviceManagementVirtualEndpointOnPremiseConnectionAdDomainPassword -CloudPcOnPremisesConnectionId $cloudPcOnPremisesConnectionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.devicemanagement.virtualendpoint.onpremisesconnections.item.update_ad_domain_password.update_ad_domain_password_post_request_body import UpdateAdDomainPasswordPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateAdDomainPasswordPostRequestBody(
	ad_domain_password = "AdDomainPassword_XXXX",
)

await graph_client.device_management.virtual_endpoint.on_premises_connections.by_cloud_pc_on_premises_connection_id('cloudPcOnPremisesConnection-id').update_ad_domain_password.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
