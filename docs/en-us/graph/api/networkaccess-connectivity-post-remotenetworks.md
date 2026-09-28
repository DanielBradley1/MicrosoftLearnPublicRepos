<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-connectivity-post-remotenetworks?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create remoteNetwork

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new remote network.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
POST /networkAccess/connectivity/remoteNetworks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object.

You can specify the following properties when creating a **remote network**.

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name of the remote network. Required. |
| region | String | Specify the region closest to the remote network location. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.networkaccess.remoteNetwork](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetwork?view=graph-rest-beta) object in the response body.

## Example 1: Create a remote network with just name and region

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
POST https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks
Content-Type: application/json

{
    "name": "Bellevue branch",
    "region": "canadaEast"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new RemoteNetwork
{
	Name = "Bellevue branch",
	Region = Region.CanadaEast,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Connectivity.RemoteNetworks.PostAsync(requestBody);
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

requestBody := graphmodelsnetworkaccess.NewRemoteNetwork()
name := "Bellevue branch"
requestBody.SetName(&name) 
region := graphmodels.CANADAEAST_REGION 
requestBody.SetRegion(&region) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remoteNetworks, err := graphClient.NetworkAccess().Connectivity().RemoteNetworks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.RemoteNetwork remoteNetwork = new com.microsoft.graph.beta.models.networkaccess.RemoteNetwork();
remoteNetwork.setName("Bellevue branch");
remoteNetwork.setRegion(com.microsoft.graph.beta.models.networkaccess.Region.CanadaEast);
com.microsoft.graph.models.networkaccess.RemoteNetwork result = graphClient.networkAccess().connectivity().remoteNetworks().post(remoteNetwork);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const remoteNetwork = {
    name: 'Bellevue branch',
    region: 'canadaEast'
};

await client.api('/networkAccess/connectivity/remoteNetworks')
	.version('beta')
	.post(remoteNetwork);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RemoteNetwork;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\Region;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemoteNetwork();
$requestBody->setName('Bellevue branch');
$requestBody->setRegion(new Region('canadaEast'));

$result = $graphServiceClient->networkAccess()->connectivity()->remoteNetworks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "Bellevue branch"
	region = "canadaEast"
}

New-MgBetaNetworkAccessConnectivityRemoteNetwork -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.remote_network import RemoteNetwork
from msgraph_beta.generated.models.region import Region
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemoteNetwork(
	name = "Bellevue branch",
	region = Region.CanadaEast,
)

result = await graph_client.network_access.connectivity.remote_networks.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks/$entity",
    "id": "8a273997-b84d-422f-8dec-e1dd82a4035b",
    "name": "Bellevue branch",
    "region": "canadaEast",
    "version": "1.0.0",
    "lastModifiedDateTime": "2024-02-01T00:41:48Z"
}
```

## Example 2: Create a remote network with forwarding profile

To get the ID of forwarding profiles of your organization, refer to this article - [List forwardingProfiles](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingprofiles?view=graph-rest-beta).

### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks
Content-Type: application/json

{
    "name": "Bellevue branch w/ fwd profile",
    "region": "canadaEast",
    "forwardingProfiles": [
        {
            "id": "1adaf535-1e31-4e14-983f-2270408162bf"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new RemoteNetwork
{
	Name = "Bellevue branch w/ fwd profile",
	Region = Region.CanadaEast,
	ForwardingProfiles = new List<ForwardingProfile>
	{
		new ForwardingProfile
		{
			Id = "1adaf535-1e31-4e14-983f-2270408162bf",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Connectivity.RemoteNetworks.PostAsync(requestBody);
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

requestBody := graphmodelsnetworkaccess.NewRemoteNetwork()
name := "Bellevue branch w/ fwd profile"
requestBody.SetName(&name) 
region := graphmodels.CANADAEAST_REGION 
requestBody.SetRegion(&region) 


forwardingProfile := graphmodelsnetworkaccess.NewForwardingProfile()
id := "1adaf535-1e31-4e14-983f-2270408162bf"
forwardingProfile.SetId(&id) 

forwardingProfiles := []graphmodelsnetworkaccess.ForwardingProfileable {
	forwardingProfile,
}
requestBody.SetForwardingProfiles(forwardingProfiles)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remoteNetworks, err := graphClient.NetworkAccess().Connectivity().RemoteNetworks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.RemoteNetwork remoteNetwork = new com.microsoft.graph.beta.models.networkaccess.RemoteNetwork();
remoteNetwork.setName("Bellevue branch w/ fwd profile");
remoteNetwork.setRegion(com.microsoft.graph.beta.models.networkaccess.Region.CanadaEast);
LinkedList<com.microsoft.graph.beta.models.networkaccess.ForwardingProfile> forwardingProfiles = new LinkedList<com.microsoft.graph.beta.models.networkaccess.ForwardingProfile>();
com.microsoft.graph.beta.models.networkaccess.ForwardingProfile forwardingProfile = new com.microsoft.graph.beta.models.networkaccess.ForwardingProfile();
forwardingProfile.setId("1adaf535-1e31-4e14-983f-2270408162bf");
forwardingProfiles.add(forwardingProfile);
remoteNetwork.setForwardingProfiles(forwardingProfiles);
com.microsoft.graph.models.networkaccess.RemoteNetwork result = graphClient.networkAccess().connectivity().remoteNetworks().post(remoteNetwork);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const remoteNetwork = {
    name: 'Bellevue branch w/ fwd profile',
    region: 'canadaEast',
    forwardingProfiles: [
        {
            id: '1adaf535-1e31-4e14-983f-2270408162bf'
        }
    ]
};

await client.api('/networkAccess/connectivity/remoteNetworks')
	.version('beta')
	.post(remoteNetwork);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RemoteNetwork;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\Region;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\ForwardingProfile;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemoteNetwork();
$requestBody->setName('Bellevue branch w/ fwd profile');
$requestBody->setRegion(new Region('canadaEast'));
$forwardingProfilesForwardingProfile1 = new ForwardingProfile();
$forwardingProfilesForwardingProfile1->setId('1adaf535-1e31-4e14-983f-2270408162bf');
$forwardingProfilesArray []= $forwardingProfilesForwardingProfile1;
$requestBody->setForwardingProfiles($forwardingProfilesArray);


$result = $graphServiceClient->networkAccess()->connectivity()->remoteNetworks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "Bellevue branch w/ fwd profile"
	region = "canadaEast"
	forwardingProfiles = @(
		@{
			id = "1adaf535-1e31-4e14-983f-2270408162bf"
		}
	)
}

New-MgBetaNetworkAccessConnectivityRemoteNetwork -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.remote_network import RemoteNetwork
from msgraph_beta.generated.models.region import Region
from msgraph_beta.generated.models.networkaccess.forwarding_profile import ForwardingProfile
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemoteNetwork(
	name = "Bellevue branch w/ fwd profile",
	region = Region.CanadaEast,
	forwarding_profiles = [
		ForwardingProfile(
			id = "1adaf535-1e31-4e14-983f-2270408162bf",
		),
	],
)

result = await graph_client.network_access.connectivity.remote_networks.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks/$entity",
    "id": "6542b28c-5ba7-4b50-9576-e63a6210e481",
    "name": "Bellevue branch w/ fwd profile",
    "region": "canadaEast",
    "version": "1.0.0",
    "lastModifiedDateTime": "2024-02-01T00:54:45Z"
}
```

## Example 3: Create a remote network with device link and forwarding profile

To get the ID of forwarding profiles of your organization, refer to this article - [List forwardingProfiles](https://learn.microsoft.com/en-us/graph/api/networkaccess-networkaccessroot-list-forwardingprofiles?view=graph-rest-beta).

### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/networkAccess/connectivity/remoteNetworks
Content-Type: application/json

{
    "name": "Bellevue branch w/ device link",
    "region": "canadaEast",
    "forwardingProfiles": [
        {
            "id": "1adaf535-1e31-4e14-983f-2270408162bf"
        }
    ],
    "deviceLinks": [
        {
            "name": "CPE1",
            "ipAddress": "52.13.21.25",
            "bandwidthCapacityInMbps": "mbps500",
            "deviceVendor": "barracudaNetworks",
            "bgpConfiguration": {
                "localIpAddress": "192.168.1.2",
                "peerIpAddress": "10.1.1.2",
                "asn": 65533
            },
            "redundancyConfiguration": {
                "zoneLocalIpAddress": null,
                "redundancyTier": "noRedundancy"
            },
            "tunnelConfiguration": {
                "@odata.type": "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default",
                "preSharedKey": "test123"
            }
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.Networkaccess;

var requestBody = new RemoteNetwork
{
	Name = "Bellevue branch w/ device link",
	Region = Region.CanadaEast,
	ForwardingProfiles = new List<ForwardingProfile>
	{
		new ForwardingProfile
		{
			Id = "1adaf535-1e31-4e14-983f-2270408162bf",
		},
	},
	DeviceLinks = new List<DeviceLink>
	{
		new DeviceLink
		{
			Name = "CPE1",
			IpAddress = "52.13.21.25",
			BandwidthCapacityInMbps = BandwidthCapacityInMbps.Mbps500,
			DeviceVendor = DeviceVendor.BarracudaNetworks,
			BgpConfiguration = new BgpConfiguration
			{
				LocalIpAddress = "192.168.1.2",
				PeerIpAddress = "10.1.1.2",
				Asn = 65533,
			},
			RedundancyConfiguration = new RedundancyConfiguration
			{
				ZoneLocalIpAddress = null,
				RedundancyTier = RedundancyTier.NoRedundancy,
			},
			TunnelConfiguration = new TunnelConfigurationIKEv2Default
			{
				OdataType = "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default",
				PreSharedKey = "test123",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.NetworkAccess.Connectivity.RemoteNetworks.PostAsync(requestBody);
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

requestBody := graphmodelsnetworkaccess.NewRemoteNetwork()
name := "Bellevue branch w/ device link"
requestBody.SetName(&name) 
region := graphmodels.CANADAEAST_REGION 
requestBody.SetRegion(&region) 


forwardingProfile := graphmodelsnetworkaccess.NewForwardingProfile()
id := "1adaf535-1e31-4e14-983f-2270408162bf"
forwardingProfile.SetId(&id) 

forwardingProfiles := []graphmodelsnetworkaccess.ForwardingProfileable {
	forwardingProfile,
}
requestBody.SetForwardingProfiles(forwardingProfiles)


deviceLink := graphmodelsnetworkaccess.NewDeviceLink()
name := "CPE1"
deviceLink.SetName(&name) 
ipAddress := "52.13.21.25"
deviceLink.SetIpAddress(&ipAddress) 
bandwidthCapacityInMbps := graphmodels.MBPS500_BANDWIDTHCAPACITYINMBPS 
deviceLink.SetBandwidthCapacityInMbps(&bandwidthCapacityInMbps) 
deviceVendor := graphmodels.BARRACUDANETWORKS_DEVICEVENDOR 
deviceLink.SetDeviceVendor(&deviceVendor) 
bgpConfiguration := graphmodelsnetworkaccess.NewBgpConfiguration()
localIpAddress := "192.168.1.2"
bgpConfiguration.SetLocalIpAddress(&localIpAddress) 
peerIpAddress := "10.1.1.2"
bgpConfiguration.SetPeerIpAddress(&peerIpAddress) 
asn := int32(65533)
bgpConfiguration.SetAsn(&asn) 
deviceLink.SetBgpConfiguration(bgpConfiguration)
redundancyConfiguration := graphmodelsnetworkaccess.NewRedundancyConfiguration()
zoneLocalIpAddress := null
redundancyConfiguration.SetZoneLocalIpAddress(&zoneLocalIpAddress) 
redundancyTier := graphmodels.NOREDUNDANCY_REDUNDANCYTIER 
redundancyConfiguration.SetRedundancyTier(&redundancyTier) 
deviceLink.SetRedundancyConfiguration(redundancyConfiguration)
tunnelConfiguration := graphmodelsnetworkaccess.NewTunnelConfigurationIKEv2Default()
preSharedKey := "test123"
tunnelConfiguration.SetPreSharedKey(&preSharedKey) 
deviceLink.SetTunnelConfiguration(tunnelConfiguration)

deviceLinks := []graphmodelsnetworkaccess.DeviceLinkable {
	deviceLink,
}
requestBody.SetDeviceLinks(deviceLinks)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remoteNetworks, err := graphClient.NetworkAccess().Connectivity().RemoteNetworks().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.networkaccess.RemoteNetwork remoteNetwork = new com.microsoft.graph.beta.models.networkaccess.RemoteNetwork();
remoteNetwork.setName("Bellevue branch w/ device link");
remoteNetwork.setRegion(com.microsoft.graph.beta.models.networkaccess.Region.CanadaEast);
LinkedList<com.microsoft.graph.beta.models.networkaccess.ForwardingProfile> forwardingProfiles = new LinkedList<com.microsoft.graph.beta.models.networkaccess.ForwardingProfile>();
com.microsoft.graph.beta.models.networkaccess.ForwardingProfile forwardingProfile = new com.microsoft.graph.beta.models.networkaccess.ForwardingProfile();
forwardingProfile.setId("1adaf535-1e31-4e14-983f-2270408162bf");
forwardingProfiles.add(forwardingProfile);
remoteNetwork.setForwardingProfiles(forwardingProfiles);
LinkedList<com.microsoft.graph.beta.models.networkaccess.DeviceLink> deviceLinks = new LinkedList<com.microsoft.graph.beta.models.networkaccess.DeviceLink>();
com.microsoft.graph.beta.models.networkaccess.DeviceLink deviceLink = new com.microsoft.graph.beta.models.networkaccess.DeviceLink();
deviceLink.setName("CPE1");
deviceLink.setIpAddress("52.13.21.25");
deviceLink.setBandwidthCapacityInMbps(com.microsoft.graph.beta.models.networkaccess.BandwidthCapacityInMbps.Mbps500);
deviceLink.setDeviceVendor(com.microsoft.graph.beta.models.networkaccess.DeviceVendor.BarracudaNetworks);
com.microsoft.graph.beta.models.networkaccess.BgpConfiguration bgpConfiguration = new com.microsoft.graph.beta.models.networkaccess.BgpConfiguration();
bgpConfiguration.setLocalIpAddress("192.168.1.2");
bgpConfiguration.setPeerIpAddress("10.1.1.2");
bgpConfiguration.setAsn(65533);
deviceLink.setBgpConfiguration(bgpConfiguration);
com.microsoft.graph.beta.models.networkaccess.RedundancyConfiguration redundancyConfiguration = new com.microsoft.graph.beta.models.networkaccess.RedundancyConfiguration();
redundancyConfiguration.setZoneLocalIpAddress(null);
redundancyConfiguration.setRedundancyTier(com.microsoft.graph.beta.models.networkaccess.RedundancyTier.NoRedundancy);
deviceLink.setRedundancyConfiguration(redundancyConfiguration);
com.microsoft.graph.beta.models.networkaccess.TunnelConfigurationIKEv2Default tunnelConfiguration = new com.microsoft.graph.beta.models.networkaccess.TunnelConfigurationIKEv2Default();
tunnelConfiguration.setOdataType("#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default");
tunnelConfiguration.setPreSharedKey("test123");
deviceLink.setTunnelConfiguration(tunnelConfiguration);
deviceLinks.add(deviceLink);
remoteNetwork.setDeviceLinks(deviceLinks);
com.microsoft.graph.models.networkaccess.RemoteNetwork result = graphClient.networkAccess().connectivity().remoteNetworks().post(remoteNetwork);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const remoteNetwork = {
    name: 'Bellevue branch w/ device link',
    region: 'canadaEast',
    forwardingProfiles: [
        {
            id: '1adaf535-1e31-4e14-983f-2270408162bf'
        }
    ],
    deviceLinks: [
        {
            name: 'CPE1',
            ipAddress: '52.13.21.25',
            bandwidthCapacityInMbps: 'mbps500',
            deviceVendor: 'barracudaNetworks',
            bgpConfiguration: {
                localIpAddress: '192.168.1.2',
                peerIpAddress: '10.1.1.2',
                asn: 65533
            },
            redundancyConfiguration: {
                zoneLocalIpAddress: null,
                redundancyTier: 'noRedundancy'
            },
            tunnelConfiguration: {
                '@odata.type': '#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default',
                preSharedKey: 'test123'
            }
        }
    ]
};

await client.api('/networkAccess/connectivity/remoteNetworks')
	.version('beta')
	.post(remoteNetwork);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RemoteNetwork;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\Region;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\ForwardingProfile;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\DeviceLink;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\BandwidthCapacityInMbps;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\DeviceVendor;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\BgpConfiguration;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RedundancyConfiguration;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\RedundancyTier;
use Microsoft\Graph\Beta\Generated\Models\Networkaccess\TunnelConfigurationIKEv2Default;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemoteNetwork();
$requestBody->setName('Bellevue branch w/ device link');
$requestBody->setRegion(new Region('canadaEast'));
$forwardingProfilesForwardingProfile1 = new ForwardingProfile();
$forwardingProfilesForwardingProfile1->setId('1adaf535-1e31-4e14-983f-2270408162bf');
$forwardingProfilesArray []= $forwardingProfilesForwardingProfile1;
$requestBody->setForwardingProfiles($forwardingProfilesArray);

$deviceLinksDeviceLink1 = new DeviceLink();
$deviceLinksDeviceLink1->setName('CPE1');
$deviceLinksDeviceLink1->setIpAddress('52.13.21.25');
$deviceLinksDeviceLink1->setBandwidthCapacityInMbps(new BandwidthCapacityInMbps('mbps500'));
$deviceLinksDeviceLink1->setDeviceVendor(new DeviceVendor('barracudaNetworks'));
$deviceLinksDeviceLink1BgpConfiguration = new BgpConfiguration();
$deviceLinksDeviceLink1BgpConfiguration->setLocalIpAddress('192.168.1.2');
$deviceLinksDeviceLink1BgpConfiguration->setPeerIpAddress('10.1.1.2');
$deviceLinksDeviceLink1BgpConfiguration->setAsn(65533);
$deviceLinksDeviceLink1->setBgpConfiguration($deviceLinksDeviceLink1BgpConfiguration);
$deviceLinksDeviceLink1RedundancyConfiguration = new RedundancyConfiguration();
$deviceLinksDeviceLink1RedundancyConfiguration->setZoneLocalIpAddress(null);
$deviceLinksDeviceLink1RedundancyConfiguration->setRedundancyTier(new RedundancyTier('noRedundancy'));
$deviceLinksDeviceLink1->setRedundancyConfiguration($deviceLinksDeviceLink1RedundancyConfiguration);
$deviceLinksDeviceLink1TunnelConfiguration = new TunnelConfigurationIKEv2Default();
$deviceLinksDeviceLink1TunnelConfiguration->setOdataType('#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default');
$deviceLinksDeviceLink1TunnelConfiguration->setPreSharedKey('test123');
$deviceLinksDeviceLink1->setTunnelConfiguration($deviceLinksDeviceLink1TunnelConfiguration);
$deviceLinksArray []= $deviceLinksDeviceLink1;
$requestBody->setDeviceLinks($deviceLinksArray);


$result = $graphServiceClient->networkAccess()->connectivity()->remoteNetworks()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.NetworkAccess

$params = @{
	name = "Bellevue branch w/ device link"
	region = "canadaEast"
	forwardingProfiles = @(
		@{
			id = "1adaf535-1e31-4e14-983f-2270408162bf"
		}
	)
	deviceLinks = @(
		@{
			name = "CPE1"
			ipAddress = "52.13.21.25"
			bandwidthCapacityInMbps = "mbps500"
			deviceVendor = "barracudaNetworks"
			bgpConfiguration = @{
				localIpAddress = "192.168.1.2"
				peerIpAddress = "10.1.1.2"
				asn = 65533
			}
			redundancyConfiguration = @{
				zoneLocalIpAddress = $null
				redundancyTier = "noRedundancy"
			}
			tunnelConfiguration = @{
				"@odata.type" = "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default"
				preSharedKey = "test123"
			}
		}
	)
}

New-MgBetaNetworkAccessConnectivityRemoteNetwork -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.networkaccess.remote_network import RemoteNetwork
from msgraph_beta.generated.models.region import Region
from msgraph_beta.generated.models.networkaccess.forwarding_profile import ForwardingProfile
from msgraph_beta.generated.models.networkaccess.device_link import DeviceLink
from msgraph_beta.generated.models.bandwidth_capacity_in_mbps import BandwidthCapacityInMbps
from msgraph_beta.generated.models.device_vendor import DeviceVendor
from msgraph_beta.generated.models.networkaccess.bgp_configuration import BgpConfiguration
from msgraph_beta.generated.models.networkaccess.redundancy_configuration import RedundancyConfiguration
from msgraph_beta.generated.models.redundancy_tier import RedundancyTier
from msgraph_beta.generated.models.networkaccess.tunnel_configuration_i_k_ev2_default import TunnelConfigurationIKEv2Default
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemoteNetwork(
	name = "Bellevue branch w/ device link",
	region = Region.CanadaEast,
	forwarding_profiles = [
		ForwardingProfile(
			id = "1adaf535-1e31-4e14-983f-2270408162bf",
		),
	],
	device_links = [
		DeviceLink(
			name = "CPE1",
			ip_address = "52.13.21.25",
			bandwidth_capacity_in_mbps = BandwidthCapacityInMbps.Mbps500,
			device_vendor = DeviceVendor.BarracudaNetworks,
			bgp_configuration = BgpConfiguration(
				local_ip_address = "192.168.1.2",
				peer_ip_address = "10.1.1.2",
				asn = 65533,
			),
			redundancy_configuration = RedundancyConfiguration(
				zone_local_ip_address = None,
				redundancy_tier = RedundancyTier.NoRedundancy,
			),
			tunnel_configuration = TunnelConfigurationIKEv2Default(
				odata_type = "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default",
				pre_shared_key = "test123",
			),
		),
	],
)

result = await graph_client.network_access.connectivity.remote_networks.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/connectivity/remoteNetworks/$entity",
    "id": "5d2f5061-4876-4c1c-ba2d-5acc6a73742d",
    "name": "Bellevue branch w/ device link",
    "region": "canadaEast",
    "version": "1.0.0",
    "lastModifiedDateTime": "2024-02-01T01:02:25Z"
}
```
