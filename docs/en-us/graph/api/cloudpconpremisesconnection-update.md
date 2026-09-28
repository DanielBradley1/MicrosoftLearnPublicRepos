<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpconpremisesconnection-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update cloudPcOnPremisesConnection

Namespace: microsoft.graph

Update the properties of a [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object.

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
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /deviceManagement/virtualEndpoint/onPremisesConnections/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| adDomainName | String | The fully qualified domain name \(FQDN\) of the Active Directory domain you want to join. |
| adDomainPassword | String | The password associated with adDomainUsername. |
| adDomainUsername | String | The username of an Active Directory account \(user or service account\) that has permissions to create computer objects in Active Directory. Required format: username@contoso.com. |
| connectionType | cloudPcOnPremisesConnectionType | Specifies how the provisioned Cloud PC will be joined to Microsoft Entra ID. The default value is `hybridAzureADJoin`. The possible values are: `azureADJoin`, `hybridAzureADJoin`, `unknownFutureValue`. |
| displayName | String | The display name for the Azure network connection. |
| resourceGroupId | String | The ID of the target resource group. Required format: "/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}". |
| subnetId | String | The ID of the target subnet. Required format: "/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/virtualNetworks/{virtualNetworkId}/subnets/{subnetName}". |
| subscriptionId | String | The ID of the target Azure subscription that’s associated with your tenant. |
| virtualNetworkId | String | The ID of the target virtual network. Required format: "/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/virtualNetworks/{virtualNetworkName}". |

## Response

If successful, this method returns a `200 OK` response code and an updated [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/onPremisesConnections/{id}
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnection",
  "displayName": "Display Name value",
  "subscriptionId": "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
  "subscriptionName": "Subscription Name value",
  "adDomainName": "Active Directory Domain Name value",
  "adDomainUsername": "Active Directory Domain User Name value",
  "organizationalUnit": "Organization Unit value",
  "resourceGroupId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG",
  "virtualNetworkId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet",
  "subnetId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CloudPcOnPremisesConnection
{
	OdataType = "#microsoft.graph.cloudPcOnPremisesConnection",
	DisplayName = "Display Name value",
	SubscriptionId = "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
	SubscriptionName = "Subscription Name value",
	AdDomainName = "Active Directory Domain Name value",
	AdDomainUsername = "Active Directory Domain User Name value",
	OrganizationalUnit = "Organization Unit value",
	ResourceGroupId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG",
	VirtualNetworkId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet",
	SubnetId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.OnPremisesConnections["{cloudPcOnPremisesConnection-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcOnPremisesConnection()
displayName := "Display Name value"
requestBody.SetDisplayName(&displayName) 
subscriptionId := "0ac520ee-14c0-480f-b6c9-0a90c585ffff"
requestBody.SetSubscriptionId(&subscriptionId) 
subscriptionName := "Subscription Name value"
requestBody.SetSubscriptionName(&subscriptionName) 
adDomainName := "Active Directory Domain Name value"
requestBody.SetAdDomainName(&adDomainName) 
adDomainUsername := "Active Directory Domain User Name value"
requestBody.SetAdDomainUsername(&adDomainUsername) 
organizationalUnit := "Organization Unit value"
requestBody.SetOrganizationalUnit(&organizationalUnit) 
resourceGroupId := "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG"
requestBody.SetResourceGroupId(&resourceGroupId) 
virtualNetworkId := "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet"
requestBody.SetVirtualNetworkId(&virtualNetworkId) 
subnetId := "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default"
requestBody.SetSubnetId(&subnetId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onPremisesConnections, err := graphClient.DeviceManagement().VirtualEndpoint().OnPremisesConnections().ByCloudPcOnPremisesConnectionId("cloudPcOnPremisesConnection-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcOnPremisesConnection cloudPcOnPremisesConnection = new CloudPcOnPremisesConnection();
cloudPcOnPremisesConnection.setOdataType("#microsoft.graph.cloudPcOnPremisesConnection");
cloudPcOnPremisesConnection.setDisplayName("Display Name value");
cloudPcOnPremisesConnection.setSubscriptionId("0ac520ee-14c0-480f-b6c9-0a90c585ffff");
cloudPcOnPremisesConnection.setSubscriptionName("Subscription Name value");
cloudPcOnPremisesConnection.setAdDomainName("Active Directory Domain Name value");
cloudPcOnPremisesConnection.setAdDomainUsername("Active Directory Domain User Name value");
cloudPcOnPremisesConnection.setOrganizationalUnit("Organization Unit value");
cloudPcOnPremisesConnection.setResourceGroupId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG");
cloudPcOnPremisesConnection.setVirtualNetworkId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet");
cloudPcOnPremisesConnection.setSubnetId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default");
CloudPcOnPremisesConnection result = graphClient.deviceManagement().virtualEndpoint().onPremisesConnections().byCloudPcOnPremisesConnectionId("{cloudPcOnPremisesConnection-id}").patch(cloudPcOnPremisesConnection);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcOnPremisesConnection = {
  '@odata.type': '#microsoft.graph.cloudPcOnPremisesConnection',
  displayName: 'Display Name value',
  subscriptionId: '0ac520ee-14c0-480f-b6c9-0a90c585ffff',
  subscriptionName: 'Subscription Name value',
  adDomainName: 'Active Directory Domain Name value',
  adDomainUsername: 'Active Directory Domain User Name value',
  organizationalUnit: 'Organization Unit value',
  resourceGroupId: '/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG',
  virtualNetworkId: '/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet',
  subnetId: '/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default'
};

await client.api('/deviceManagement/virtualEndpoint/onPremisesConnections/{id}')
	.update(cloudPcOnPremisesConnection);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CloudPcOnPremisesConnection;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcOnPremisesConnection();
$requestBody->setOdataType('#microsoft.graph.cloudPcOnPremisesConnection');
$requestBody->setDisplayName('Display Name value');
$requestBody->setSubscriptionId('0ac520ee-14c0-480f-b6c9-0a90c585ffff');
$requestBody->setSubscriptionName('Subscription Name value');
$requestBody->setAdDomainName('Active Directory Domain Name value');
$requestBody->setAdDomainUsername('Active Directory Domain User Name value');
$requestBody->setOrganizationalUnit('Organization Unit value');
$requestBody->setResourceGroupId('/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG');
$requestBody->setVirtualNetworkId('/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet');
$requestBody->setSubnetId('/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->onPremisesConnections()->byCloudPcOnPremisesConnectionId('cloudPcOnPremisesConnection-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	"@odata.type" = "#microsoft.graph.cloudPcOnPremisesConnection"
	displayName = "Display Name value"
	subscriptionId = "0ac520ee-14c0-480f-b6c9-0a90c585ffff"
	subscriptionName = "Subscription Name value"
	adDomainName = "Active Directory Domain Name value"
	adDomainUsername = "Active Directory Domain User Name value"
	organizationalUnit = "Organization Unit value"
	resourceGroupId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG"
	virtualNetworkId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet"
	subnetId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default"
}

Update-MgDeviceManagementVirtualEndpointOnPremiseConnection -CloudPcOnPremisesConnectionId $cloudPcOnPremisesConnectionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cloud_pc_on_premises_connection import CloudPcOnPremisesConnection
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcOnPremisesConnection(
	odata_type = "#microsoft.graph.cloudPcOnPremisesConnection",
	display_name = "Display Name value",
	subscription_id = "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
	subscription_name = "Subscription Name value",
	ad_domain_name = "Active Directory Domain Name value",
	ad_domain_username = "Active Directory Domain User Name value",
	organizational_unit = "Organization Unit value",
	resource_group_id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG",
	virtual_network_id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet",
	subnet_id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default",
)

result = await graph_client.device_management.virtual_endpoint.on_premises_connections.by_cloud_pc_on_premises_connection_id('cloudPcOnPremisesConnection-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnection",
  "id": "9ec90ff8-fd63-4fb9-ab5a-aa4fdcc4ffff",
  "connectionType": "hybridAzureADJoin", 
  "displayName": "Display Name value",
  "subscriptionId": "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
  "subscriptionName": "Subscription Name value",
  "adDomainName": "Active Directory Domain Name value",
  "adDomainUsername": "Active Directory Domain User Name value",
  "organizationalUnit": "Organization Unit value",
  "resourceGroupId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG",
  "virtualNetworkId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c58ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet",
  "subnetId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ffff/resourceGroups/ExampleRG/providers/Microsoft.Network/virtualNetworks/ExampleVNet/subnets/default",
  "healthCheckStatus": "running",
  "virtualNetworkLocation": "westus2"
}
```
