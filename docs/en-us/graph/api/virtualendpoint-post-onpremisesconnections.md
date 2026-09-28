<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-onpremisesconnections?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create cloudPcOnPremisesConnection

Namespace: microsoft.graph

Create a new [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object for provisioning Cloud PCs.

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
POST /deviceManagement/virtualEndpoint/onPremisesConnections
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
| adDomainUsername | String | The username of an Active Directory account \(user or service account\) that has permissions to create computer objects in Active Directory. Required format: admin@contoso.com. |
| connectionType | cloudPcOnPremisesConnectionType | Specifies how the provisioned Cloud PC will be joined to Microsoft Entra ID. The default value is `hybridAzureADJoin`. The possible values are: `azureADJoin`, `hybridAzureADJoin`, `unknownFutureValue`. |
| displayName | String | The display name for the Azure network connection. |
| resourceGroupId | String | The ID of the target resource group. Required format: "/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}". |
| subnetId | String | The ID of the target subnet. Required format: "/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/virtualNetworks/{virtualNetworkId}/subnets/{subnetName}". |
| subscriptionId | String | The ID of the target Azure subscription that’s associated with your tenant. |
| virtualNetworkId | String | The ID of the target virtual network. Required format: "/subscriptions/{subscription-id}/resourceGroups/{resourceGroupName}/providers/Microsoft.Network/virtualNetworks/{virtualNetworkName}". |

## Response

If successful, this method returns a `201 Created` response code and a [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/onPremisesConnections
Content-Type: application/json

{
  "displayName": "test-canary-02",
  "connectionType": "hybridAzureADJoin",
  "subscriptionId": "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
  "adDomainName": "contoso001.com",
  "adDomainUsername": "dcadmin",
  "organizationalUnit": "OU=Domain Controllers, DC=contoso001, DC=com",
  "resourceGroupId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG",
  "virtualNetworkId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET",
  "subnetId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CloudPcOnPremisesConnection
{
	DisplayName = "test-canary-02",
	ConnectionType = CloudPcOnPremisesConnectionType.HybridAzureADJoin,
	SubscriptionId = "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
	AdDomainName = "contoso001.com",
	AdDomainUsername = "dcadmin",
	OrganizationalUnit = "OU=Domain Controllers, DC=contoso001, DC=com",
	ResourceGroupId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG",
	VirtualNetworkId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET",
	SubnetId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.OnPremisesConnections.PostAsync(requestBody);
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
displayName := "test-canary-02"
requestBody.SetDisplayName(&displayName) 
connectionType := graphmodels.HYBRIDAZUREADJOIN_CLOUDPCONPREMISESCONNECTIONTYPE 
requestBody.SetConnectionType(&connectionType) 
subscriptionId := "0ac520ee-14c0-480f-b6c9-0a90c585ffff"
requestBody.SetSubscriptionId(&subscriptionId) 
adDomainName := "contoso001.com"
requestBody.SetAdDomainName(&adDomainName) 
adDomainUsername := "dcadmin"
requestBody.SetAdDomainUsername(&adDomainUsername) 
organizationalUnit := "OU=Domain Controllers, DC=contoso001, DC=com"
requestBody.SetOrganizationalUnit(&organizationalUnit) 
resourceGroupId := "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG"
requestBody.SetResourceGroupId(&resourceGroupId) 
virtualNetworkId := "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET"
requestBody.SetVirtualNetworkId(&virtualNetworkId) 
subnetId := "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet"
requestBody.SetSubnetId(&subnetId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onPremisesConnections, err := graphClient.DeviceManagement().VirtualEndpoint().OnPremisesConnections().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcOnPremisesConnection cloudPcOnPremisesConnection = new CloudPcOnPremisesConnection();
cloudPcOnPremisesConnection.setDisplayName("test-canary-02");
cloudPcOnPremisesConnection.setConnectionType(CloudPcOnPremisesConnectionType.HybridAzureADJoin);
cloudPcOnPremisesConnection.setSubscriptionId("0ac520ee-14c0-480f-b6c9-0a90c585ffff");
cloudPcOnPremisesConnection.setAdDomainName("contoso001.com");
cloudPcOnPremisesConnection.setAdDomainUsername("dcadmin");
cloudPcOnPremisesConnection.setOrganizationalUnit("OU=Domain Controllers, DC=contoso001, DC=com");
cloudPcOnPremisesConnection.setResourceGroupId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG");
cloudPcOnPremisesConnection.setVirtualNetworkId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET");
cloudPcOnPremisesConnection.setSubnetId("/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet");
CloudPcOnPremisesConnection result = graphClient.deviceManagement().virtualEndpoint().onPremisesConnections().post(cloudPcOnPremisesConnection);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcOnPremisesConnection = {
  displayName: 'test-canary-02',
  connectionType: 'hybridAzureADJoin',
  subscriptionId: '0ac520ee-14c0-480f-b6c9-0a90c585ffff',
  adDomainName: 'contoso001.com',
  adDomainUsername: 'dcadmin',
  organizationalUnit: 'OU=Domain Controllers, DC=contoso001, DC=com',
  resourceGroupId: '/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG',
  virtualNetworkId: '/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET',
  subnetId: '/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet'
};

await client.api('/deviceManagement/virtualEndpoint/onPremisesConnections')
	.post(cloudPcOnPremisesConnection);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CloudPcOnPremisesConnection;
use Microsoft\Graph\Generated\Models\CloudPcOnPremisesConnectionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcOnPremisesConnection();
$requestBody->setDisplayName('test-canary-02');
$requestBody->setConnectionType(new CloudPcOnPremisesConnectionType('hybridAzureADJoin'));
$requestBody->setSubscriptionId('0ac520ee-14c0-480f-b6c9-0a90c585ffff');
$requestBody->setAdDomainName('contoso001.com');
$requestBody->setAdDomainUsername('dcadmin');
$requestBody->setOrganizationalUnit('OU=Domain Controllers, DC=contoso001, DC=com');
$requestBody->setResourceGroupId('/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG');
$requestBody->setVirtualNetworkId('/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET');
$requestBody->setSubnetId('/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->onPremisesConnections()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	displayName = "test-canary-02"
	connectionType = "hybridAzureADJoin"
	subscriptionId = "0ac520ee-14c0-480f-b6c9-0a90c585ffff"
	adDomainName = "contoso001.com"
	adDomainUsername = "dcadmin"
	organizationalUnit = "OU=Domain Controllers, DC=contoso001, DC=com"
	resourceGroupId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG"
	virtualNetworkId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET"
	subnetId = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet"
}

New-MgDeviceManagementVirtualEndpointOnPremiseConnection -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.cloud_pc_on_premises_connection import CloudPcOnPremisesConnection
from msgraph.generated.models.cloud_pc_on_premises_connection_type import CloudPcOnPremisesConnectionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcOnPremisesConnection(
	display_name = "test-canary-02",
	connection_type = CloudPcOnPremisesConnectionType.HybridAzureADJoin,
	subscription_id = "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
	ad_domain_name = "contoso001.com",
	ad_domain_username = "dcadmin",
	organizational_unit = "OU=Domain Controllers, DC=contoso001, DC=com",
	resource_group_id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG",
	virtual_network_id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET",
	subnet_id = "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet",
)

result = await graph_client.device_management.virtual_endpoint.on_premises_connections.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnection",
  "id": "ac2ad805-167e-49ee-9bef-196c4ce7ffff",
  "displayName": "test-canary-02",
  "connectionType": "hybridAzureADJoin",
  "subscriptionId": "0ac520ee-14c0-480f-b6c9-0a90c585ffff",
  "subscriptionName": "CPC customer 001 test subscription",
  "adDomainName": "contoso001.com",
  "adDomainUsername": "dcadmin",
  "organizationalUnit": "OU=Domain Controllers, DC=contoso001, DC=com",
  "resourceGroupId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG",
  "virtualNetworkId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET",
  "subnetId": "/subscriptions/0ac520ee-14c0-480f-b6c9-0a90c585ad47/resourceGroups/CustomerRG/providers/Microsoft.Network/virtualNetworks/canary01-MyVNET/subnets/canary01-Subnet",
  "healthCheckStatus": "pending"
}
```
