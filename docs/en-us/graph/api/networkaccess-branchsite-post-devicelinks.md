<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-branchsite-post-devicelinks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create deviceLink \(deprecated\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

Deprecated and to be retired soon. Use the [remoteNetwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) and its associated methods instead.

Create a branch site with associated device links.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/connectivity/branches/{branchSiteId}/deviceLinks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object.

You can specify the following properties when creating a **deviceLink**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name or identifier associated with a device link. Required. |
| ipAddress | String | The IP address associated with a device link. Required. |
| deviceVendor | microsoft.graph.networkaccess.deviceVendor | The vendor or manufacturer of the device associated with a device link. The possible values are: `barracudaNetworks`, `checkPoint`, `ciscoMeraki`, `citrix`, `fortinet`, `hpeAruba`, `netFoundry`, `nuage`, `openSystems`, `paloAltoNetworks`, `riverbedTechnology`, `silverPeak`, `vmWareSdWan`, `versa`, `other`. Required. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the device link was last modified. Required. |
| tunnelConfiguration | [microsoft.graph.networkaccess.tunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfiguration?view=graph-rest-beta) | The tunnel configuration settings associated with a device link. Required. |
| bgpConfiguration | [microsoft.graph.networkaccess.bgpConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-bgpconfiguration?view=graph-rest-beta) | The Border Gateway Protocol \(BGP\) configuration settings associated with a device link. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/networkAccess/connectivity/branches/19a92090-c14e-4cea-a933-27d38f72c4d1/deviceLinks
Content-Type: application/json

{
    "name": "device link 1",
    "ipAddress": "24.123.22.168",
    "deviceVendor": "intel",
    "bandwidthCapacityInMbps": "mbps250",
    "bgpConfiguration":
    {
        "localIpAddress": "1.128.24.22",
        "peerIpAddress": "1.128.24.28",
        "asn": 4
    },
    "redundancyConfiguration":
    {
        "zoneLocalIpAddress": "1.128.23.20",
        "redundancyTier": "zoneRedundancy"
    },
    "tunnelConfiguration":
    {
        "@odata.type": "microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default",
        "preSharedKey": "/microsoft/keyVault/placeholder"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new DeviceLink
{
	Name = "device link 1",
	IpAddress = "24.123.22.168",
	DeviceVendor = DeviceVendor.BarracudaNetworks,
	BandwidthCapacityInMbps = BandwidthCapacityInMbps.Mbps250,
	BgpConfiguration = new BgpConfiguration
	{
		LocalIpAddress = "1.128.24.22",
		PeerIpAddress = "1.128.24.28",
		Asn = 4,
	},
	RedundancyConfiguration = new RedundancyConfiguration
	{
		ZoneLocalIpAddress = "1.128.23.20",
		RedundancyTier = RedundancyTier.ZoneRedundancy,
	},
	TunnelConfiguration = new TunnelConfiguration
	{
		OdataType = "microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default",
		PreSharedKey = "/microsoft/keyVault/placeholder",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Connectivity.Branches["{branchSite-id}"].DeviceLinks.PostAsync(requestBody);
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
	  graphmodelsnetworkaccess "github.com/microsoftgraph/msgraph-beta-sdk-go/models/networkaccess"
	  //other-imports
)

requestBody := graphmodelsnetworkaccess.NewDeviceLink()
name := "device link 1"
requestBody.SetName(&name) 
ipAddress := "24.123.22.168"
requestBody.SetIpAddress(&ipAddress) 
deviceVendor := graphmodels.INTEL_DEVICEVENDOR 
requestBody.SetDeviceVendor(&deviceVendor) 
bandwidthCapacityInMbps := graphmodels.MBPS250_BANDWIDTHCAPACITYINMBPS 
requestBody.SetBandwidthCapacityInMbps(&bandwidthCapacityInMbps) 
bgpConfiguration := graphmodelsnetworkaccess.NewBgpConfiguration()
localIpAddress := "1.128.24.22"
bgpConfiguration.SetLocalIpAddress(&localIpAddress) 
peerIpAddress := "1.128.24.28"
bgpConfiguration.SetPeerIpAddress(&peerIpAddress) 
asn := int32(4)
bgpConfiguration.SetAsn(&asn) 
requestBody.SetBgpConfiguration(bgpConfiguration)
redundancyConfiguration := graphmodelsnetworkaccess.NewRedundancyConfiguration()
zoneLocalIpAddress := "1.128.23.20"
redundancyConfiguration.SetZoneLocalIpAddress(&zoneLocalIpAddress) 
redundancyTier := graphmodels.ZONEREDUNDANCY_REDUNDANCYTIER 
redundancyConfiguration.SetRedundancyTier(&redundancyTier) 
requestBody.SetRedundancyConfiguration(redundancyConfiguration)
tunnelConfiguration := graphmodelsnetworkaccess.NewTunnelConfiguration()
preSharedKey := "/microsoft/keyVault/placeholder"
tunnelConfiguration.SetPreSharedKey(&preSharedKey) 
requestBody.SetTunnelConfiguration(tunnelConfiguration)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
deviceLinks, err := graphClient.NetworkAccess().Connectivity().Branches().ByBranchSiteId("branchSite-id").DeviceLinks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.DeviceLink deviceLink = new com.microsoft.graph.beta.models.networkaccess.DeviceLink();
deviceLink.setName("device link 1");
deviceLink.setIpAddress("24.123.22.168");
deviceLink.setDeviceVendor(com.microsoft.graph.beta.models.networkaccess.DeviceVendor.BarracudaNetworks);
deviceLink.setBandwidthCapacityInMbps(com.microsoft.graph.beta.models.networkaccess.BandwidthCapacityInMbps.Mbps250);
com.microsoft.graph.beta.models.networkaccess.BgpConfiguration bgpConfiguration = new com.microsoft.graph.beta.models.networkaccess.BgpConfiguration();
bgpConfiguration.setLocalIpAddress("1.128.24.22");
bgpConfiguration.setPeerIpAddress("1.128.24.28");
bgpConfiguration.setAsn(4);
deviceLink.setBgpConfiguration(bgpConfiguration);
com.microsoft.graph.beta.models.networkaccess.RedundancyConfiguration redundancyConfiguration = new com.microsoft.graph.beta.models.networkaccess.RedundancyConfiguration();
redundancyConfiguration.setZoneLocalIpAddress("1.128.23.20");
redundancyConfiguration.setRedundancyTier(com.microsoft.graph.beta.models.networkaccess.RedundancyTier.ZoneRedundancy);
deviceLink.setRedundancyConfiguration(redundancyConfiguration);
com.microsoft.graph.beta.models.networkaccess.TunnelConfiguration tunnelConfiguration = new com.microsoft.graph.beta.models.networkaccess.TunnelConfiguration();
tunnelConfiguration.setOdataType("microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default");
tunnelConfiguration.setPreSharedKey("/microsoft/keyVault/placeholder");
deviceLink.setTunnelConfiguration(tunnelConfiguration);
com.microsoft.graph.models.networkaccess.DeviceLink result = graphClient.networkAccess().connectivity().branches().byBranchSiteId("{branchSite-id}").deviceLinks().post(deviceLink);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const deviceLink = {
    name: 'device link 1',
    ipAddress: '24.123.22.168',
    deviceVendor: 'intel',
    bandwidthCapacityInMbps: 'mbps250',
    bgpConfiguration: 
    {
        localIpAddress: '1.128.24.22',
        peerIpAddress: '1.128.24.28',
        asn: 4
    },
    redundancyConfiguration: 
    {
        zoneLocalIpAddress: '1.128.23.20',
        redundancyTier: 'zoneRedundancy'
    },
    tunnelConfiguration: 
    {
        '@odata.type': 'microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default',
        preSharedKey: '/microsoft/keyVault/placeholder'
    }
};

await client.api('/networkAccess/connectivity/branches/19a92090-c14e-4cea-a933-27d38f72c4d1/deviceLinks')
	.version('beta')
	.post(deviceLink);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\DeviceLink;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\DeviceVendor;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\BandwidthCapacityInMbps;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\BgpConfiguration;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RedundancyConfiguration;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RedundancyTier;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TunnelConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DeviceLink();
$requestBody->setName('device link 1');
$requestBody->setIpAddress('24.123.22.168');
$requestBody->setDeviceVendor(new DeviceVendor('intel'));
$requestBody->setBandwidthCapacityInMbps(new BandwidthCapacityInMbps('mbps250'));
$bgpConfiguration = new BgpConfiguration();
$bgpConfiguration->setLocalIpAddress('1.128.24.22');
$bgpConfiguration->setPeerIpAddress('1.128.24.28');
$bgpConfiguration->setAsn(4);
$requestBody->setBgpConfiguration($bgpConfiguration);
$redundancyConfiguration = new RedundancyConfiguration();
$redundancyConfiguration->setZoneLocalIpAddress('1.128.23.20');
$redundancyConfiguration->setRedundancyTier(new RedundancyTier('zoneRedundancy'));
$requestBody->setRedundancyConfiguration($redundancyConfiguration);
$tunnelConfiguration = new TunnelConfiguration();
$tunnelConfiguration->setOdataType('microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default');
$tunnelConfiguration->setPreSharedKey('/microsoft/keyVault/placeholder');
$requestBody->setTunnelConfiguration($tunnelConfiguration);

$result = $graphServiceClient->networkAccess()->connectivity()->branches()->byBranchSiteId('branchSite-id')->deviceLinks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "device link 1"
	ipAddress = "24.123.22.168"
	deviceVendor = "intel"
	bandwidthCapacityInMbps = "mbps250"
	bgpConfiguration = @{
		localIpAddress = "1.128.24.22"
		peerIpAddress = "1.128.24.28"
		asn = 4
	}
	redundancyConfiguration = @{
		zoneLocalIpAddress = "1.128.23.20"
		redundancyTier = "zoneRedundancy"
	}
	tunnelConfiguration = @{
		"@odata.type" = "microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default"
		preSharedKey = "/microsoft/keyVault/placeholder"
	}
}

New-MgBetaNetworkAccessConnectivityBranchDeviceLink -BranchSiteId $branchSiteId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.device_link import DeviceLink
from msgraph_beta.generated.models.device_vendor import DeviceVendor
from msgraph_beta.generated.models.bandwidth_capacity_in_mbps import BandwidthCapacityInMbps
from msgraph_beta.generated.models.networkaccess.bgp_configuration import BgpConfiguration
from msgraph_beta.generated.models.networkaccess.redundancy_configuration import RedundancyConfiguration
from msgraph_beta.generated.models.redundancy_tier import RedundancyTier
from msgraph_beta.generated.models.networkaccess.tunnel_configuration import TunnelConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DeviceLink(
	name = "device link 1",
	ip_address = "24.123.22.168",
	device_vendor = DeviceVendor.BarracudaNetworks,
	bandwidth_capacity_in_mbps = BandwidthCapacityInMbps.Mbps250,
	bgp_configuration = BgpConfiguration(
		local_ip_address = "1.128.24.22",
		peer_ip_address = "1.128.24.28",
		asn = 4,
	),
	redundancy_configuration = RedundancyConfiguration(
		zone_local_ip_address = "1.128.23.20",
		redundancy_tier = RedundancyTier.ZoneRedundancy,
	),
	tunnel_configuration = TunnelConfiguration(
		odata_type = "microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default",
		pre_shared_key = "/microsoft/keyVault/placeholder",
	),
)

result = await graph_client.network_access.connectivity.branches.by_branch_site_id('branchSite-id').device_links.post(request_body)
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
  "@odata.type": "#microsoft.graph.networkaccess.deviceLink",
  "id": "2f183529-b8d9-c6f1-0373-3a6beee36e38",
  "name": "device link 1",
  "ipAddress": "24.123.22.168",
  "deviceVendor": "intel",
  "bandwidthCapacityInMbps": "mbps250",
  "redundancyConfiguration_redundancyTier": "zoneRedundancy",
  "tunnelConfiguration_type": "microsoft.graph.networkAccess.tunnelConfigurationIKEv2Default",
  "tunnelConfiguration_preSharedKey": "/microsoft/keyVault/placeholder"
}
```
