<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-cloudpcpools?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-27 -->

# Create cloudPcPool

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/cloudPcPools
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object.

The **@odata.type** property is required in the request body to specify the derived type. The supported value is `#microsoft.graph.cloudPcAgentPool`.

The following table lists the properties that are required when you create a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| billingConfiguration | [cloudPcAgentPoolBillingConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolbillingconfiguration?view=graph-rest-beta) | Required. The billing configuration for the agent pool, including billing type and billing plan identifier. Applies to the [cloudPcAgentPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpool?view=graph-rest-beta) derived type. |
| capabilities | [cloudPcPoolCapabilityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpoolcapabilityconfiguration?view=graph-rest-beta) | Required. The capabilities configuration for the pool, including single sign-on settings. |
| cloudPcConfiguration | [cloudPcConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconfiguration?view=graph-rest-beta) | Required. The Cloud PC specification, including image and operating system locale settings for provisioning. |
| description | String | Optional. The description of the pool. The maximum length is 512 characters. |
| displayName | String | Required. The display name of the pool. The name is unique across Cloud PC pools in an organization. The maximum length is 60 characters. |
| networkConfiguration | [cloudPcNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcnetworkconfiguration?view=graph-rest-beta) | Required. The network configuration for the pool. Supported derived types: [cloudPcMicrosoftHostedNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmicrosofthostednetworkconfiguration?view=graph-rest-beta). |
| scalingPolicy | [cloudPcAgentPoolScalingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpoolscalingpolicy?view=graph-rest-beta) | Required. The scaling policy defining minimum and maximum Cloud PC counts for the pool. Applies to the [cloudPcAgentPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcagentpool?view=graph-rest-beta) derived type. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudPcPool](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcpool?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPcPools
Content-Type: application/json

{
  "@odata.type":"#microsoft.graph.cloudPcAgentPool",
  "displayName": "Contoso Development Pool",
  "cloudPcConfiguration": {
    "imageId": "microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365",
    "imageType": "gallery",
    "osLocale": "en-US"
  },
  "networkConfiguration": {
    "@odata.type": "#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration",
    "geographicLocationType": "usWest",
    "regionGroups": [
      {
        "regionGroup": "usWest",
        "regions": ["westus2", "westus3"]
      }
    ]
  },
  "billingConfiguration": {
    "billingType": "payAsYouGo",
    "billingPlanId": "00000000-0000-0000-0000-000000000001"
  },
  "scalingPolicy": {
    "minimumCount": 2,
    "maximumCount": 10
  },
  "capabilities": {
    "@odata.type": "#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration",
    "enableSingleSignOn": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcAgentPool
{
	OdataType = "#microsoft.graph.cloudPcAgentPool",
	DisplayName = "Contoso Development Pool",
	CloudPcConfiguration = new CloudPcConfiguration
	{
		ImageId = "microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365",
		ImageType = CloudPcProvisioningPolicyImageType.Gallery,
		OsLocale = "en-US",
	},
	NetworkConfiguration = new CloudPcMicrosoftHostedNetworkConfiguration
	{
		OdataType = "#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration",
		GeographicLocationType = CloudPcGeographicLocationType.UsWest,
		RegionGroups = new List<CloudPcRegionGroupConfiguration>
		{
			new CloudPcRegionGroupConfiguration
			{
				RegionGroup = CloudPcRegionGroup.UsWest,
				Regions = new List<string>
				{
					"westus2",
					"westus3",
				},
			},
		},
	},
	BillingConfiguration = new CloudPcAgentPoolBillingConfiguration
	{
		BillingType = CloudPcAgentPoolBillingType.PayAsYouGo,
		BillingPlanId = "00000000-0000-0000-0000-000000000001",
	},
	ScalingPolicy = new CloudPcAgentPoolScalingPolicy
	{
		MinimumCount = 2,
		MaximumCount = 10,
	},
	Capabilities = new CloudPcAgentPoolCapabilityConfiguration
	{
		OdataType = "#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration",
		EnableSingleSignOn = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudPcPools.PostAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcPool()
displayName := "Contoso Development Pool"
requestBody.SetDisplayName(&displayName) 
cloudPcConfiguration := graphmodels.NewCloudPcConfiguration()
imageId := "microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365"
cloudPcConfiguration.SetImageId(&imageId) 
imageType := graphmodels.GALLERY_CLOUDPCPROVISIONINGPOLICYIMAGETYPE 
cloudPcConfiguration.SetImageType(&imageType) 
osLocale := "en-US"
cloudPcConfiguration.SetOsLocale(&osLocale) 
requestBody.SetCloudPcConfiguration(cloudPcConfiguration)
networkConfiguration := graphmodels.NewCloudPcMicrosoftHostedNetworkConfiguration()
geographicLocationType := graphmodels.USWEST_CLOUDPCGEOGRAPHICLOCATIONTYPE 
networkConfiguration.SetGeographicLocationType(&geographicLocationType) 


cloudPcRegionGroupConfiguration := graphmodels.NewCloudPcRegionGroupConfiguration()
regionGroup := graphmodels.USWEST_CLOUDPCREGIONGROUP 
cloudPcRegionGroupConfiguration.SetRegionGroup(&regionGroup) 
regions := []string {
	"westus2",
	"westus3",
}
cloudPcRegionGroupConfiguration.SetRegions(regions)

regionGroups := []graphmodels.CloudPcRegionGroupConfigurationable {
	cloudPcRegionGroupConfiguration,
}
networkConfiguration.SetRegionGroups(regionGroups)
requestBody.SetNetworkConfiguration(networkConfiguration)
billingConfiguration := graphmodels.NewCloudPcAgentPoolBillingConfiguration()
billingType := graphmodels.PAYASYOUGO_CLOUDPCAGENTPOOLBILLINGTYPE 
billingConfiguration.SetBillingType(&billingType) 
billingPlanId := "00000000-0000-0000-0000-000000000001"
billingConfiguration.SetBillingPlanId(&billingPlanId) 
requestBody.SetBillingConfiguration(billingConfiguration)
scalingPolicy := graphmodels.NewCloudPcAgentPoolScalingPolicy()
minimumCount := int32(2)
scalingPolicy.SetMinimumCount(&minimumCount) 
maximumCount := int32(10)
scalingPolicy.SetMaximumCount(&maximumCount) 
requestBody.SetScalingPolicy(scalingPolicy)
capabilities := graphmodels.NewCloudPcAgentPoolCapabilityConfiguration()
enableSingleSignOn := true
capabilities.SetEnableSingleSignOn(&enableSingleSignOn) 
requestBody.SetCapabilities(capabilities)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
cloudPcPools, err := graphClient.DeviceManagement().VirtualEndpoint().CloudPcPools().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcAgentPool cloudPcPool = new CloudPcAgentPool();
cloudPcPool.setOdataType("#microsoft.graph.cloudPcAgentPool");
cloudPcPool.setDisplayName("Contoso Development Pool");
CloudPcConfiguration cloudPcConfiguration = new CloudPcConfiguration();
cloudPcConfiguration.setImageId("microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365");
cloudPcConfiguration.setImageType(CloudPcProvisioningPolicyImageType.Gallery);
cloudPcConfiguration.setOsLocale("en-US");
cloudPcPool.setCloudPcConfiguration(cloudPcConfiguration);
CloudPcMicrosoftHostedNetworkConfiguration networkConfiguration = new CloudPcMicrosoftHostedNetworkConfiguration();
networkConfiguration.setOdataType("#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration");
networkConfiguration.setGeographicLocationType(CloudPcGeographicLocationType.UsWest);
LinkedList<CloudPcRegionGroupConfiguration> regionGroups = new LinkedList<CloudPcRegionGroupConfiguration>();
CloudPcRegionGroupConfiguration cloudPcRegionGroupConfiguration = new CloudPcRegionGroupConfiguration();
cloudPcRegionGroupConfiguration.setRegionGroup(CloudPcRegionGroup.UsWest);
LinkedList<String> regions = new LinkedList<String>();
regions.add("westus2");
regions.add("westus3");
cloudPcRegionGroupConfiguration.setRegions(regions);
regionGroups.add(cloudPcRegionGroupConfiguration);
networkConfiguration.setRegionGroups(regionGroups);
cloudPcPool.setNetworkConfiguration(networkConfiguration);
CloudPcAgentPoolBillingConfiguration billingConfiguration = new CloudPcAgentPoolBillingConfiguration();
billingConfiguration.setBillingType(CloudPcAgentPoolBillingType.PayAsYouGo);
billingConfiguration.setBillingPlanId("00000000-0000-0000-0000-000000000001");
cloudPcPool.setBillingConfiguration(billingConfiguration);
CloudPcAgentPoolScalingPolicy scalingPolicy = new CloudPcAgentPoolScalingPolicy();
scalingPolicy.setMinimumCount(2);
scalingPolicy.setMaximumCount(10);
cloudPcPool.setScalingPolicy(scalingPolicy);
CloudPcAgentPoolCapabilityConfiguration capabilities = new CloudPcAgentPoolCapabilityConfiguration();
capabilities.setOdataType("#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration");
capabilities.setEnableSingleSignOn(true);
cloudPcPool.setCapabilities(capabilities);
CloudPcPool result = graphClient.deviceManagement().virtualEndpoint().cloudPcPools().post(cloudPcPool);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcPool = {
  '@odata.type':'#microsoft.graph.cloudPcAgentPool',
  displayName: 'Contoso Development Pool',
  cloudPcConfiguration: {
    imageId: 'microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365',
    imageType: 'gallery',
    osLocale: 'en-US'
  },
  networkConfiguration: {
    '@odata.type': '#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration',
    geographicLocationType: 'usWest',
    regionGroups: [
      {
        regionGroup: 'usWest',
        regions: ['westus2', 'westus3']
      }
    ]
  },
  billingConfiguration: {
    billingType: 'payAsYouGo',
    billingPlanId: '00000000-0000-0000-0000-000000000001'
  },
  scalingPolicy: {
    minimumCount: 2,
    maximumCount: 10
  },
  capabilities: {
    '@odata.type': '#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration',
    enableSingleSignOn: true
  }
};

await client.api('/deviceManagement/virtualEndpoint/cloudPcPools')
	.version('beta')
	.post(cloudPcPool);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAgentPool;
use Microsoft\Graph\Beta\Generated\Models\CloudPcConfiguration;
use Microsoft\Graph\Beta\Generated\Models\CloudPcProvisioningPolicyImageType;
use Microsoft\Graph\Beta\Generated\Models\CloudPcMicrosoftHostedNetworkConfiguration;
use Microsoft\Graph\Beta\Generated\Models\CloudPcGeographicLocationType;
use Microsoft\Graph\Beta\Generated\Models\CloudPcRegionGroupConfiguration;
use Microsoft\Graph\Beta\Generated\Models\CloudPcRegionGroup;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAgentPoolBillingConfiguration;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAgentPoolBillingType;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAgentPoolScalingPolicy;
use Microsoft\Graph\Beta\Generated\Models\CloudPcAgentPoolCapabilityConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcAgentPool();
$requestBody->setOdataType('#microsoft.graph.cloudPcAgentPool');
$requestBody->setDisplayName('Contoso Development Pool');
$cloudPcConfiguration = new CloudPcConfiguration();
$cloudPcConfiguration->setImageId('microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365');
$cloudPcConfiguration->setImageType(new CloudPcProvisioningPolicyImageType('gallery'));
$cloudPcConfiguration->setOsLocale('en-US');
$requestBody->setCloudPcConfiguration($cloudPcConfiguration);
$networkConfiguration = new CloudPcMicrosoftHostedNetworkConfiguration();
$networkConfiguration->setOdataType('#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration');
$networkConfiguration->setGeographicLocationType(new CloudPcGeographicLocationType('usWest'));
$regionGroupsCloudPcRegionGroupConfiguration1 = new CloudPcRegionGroupConfiguration();
$regionGroupsCloudPcRegionGroupConfiguration1->setRegionGroup(new CloudPcRegionGroup('usWest'));
$regionGroupsCloudPcRegionGroupConfiguration1->setRegions(['westus2', 'westus3', 	]);
$regionGroupsArray []= $regionGroupsCloudPcRegionGroupConfiguration1;
$networkConfiguration->setRegionGroups($regionGroupsArray);

$requestBody->setNetworkConfiguration($networkConfiguration);
$billingConfiguration = new CloudPcAgentPoolBillingConfiguration();
$billingConfiguration->setBillingType(new CloudPcAgentPoolBillingType('payAsYouGo'));
$billingConfiguration->setBillingPlanId('00000000-0000-0000-0000-000000000001');
$requestBody->setBillingConfiguration($billingConfiguration);
$scalingPolicy = new CloudPcAgentPoolScalingPolicy();
$scalingPolicy->setMinimumCount(2);
$scalingPolicy->setMaximumCount(10);
$requestBody->setScalingPolicy($scalingPolicy);
$capabilities = new CloudPcAgentPoolCapabilityConfiguration();
$capabilities->setOdataType('#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration');
$capabilities->setEnableSingleSignOn(true);
$requestBody->setCapabilities($capabilities);

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudPcPools()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_agent_pool import CloudPcAgentPool
from msgraph_beta.generated.models.cloud_pc_configuration import CloudPcConfiguration
from msgraph_beta.generated.models.cloud_pc_provisioning_policy_image_type import CloudPcProvisioningPolicyImageType
from msgraph_beta.generated.models.cloud_pc_microsoft_hosted_network_configuration import CloudPcMicrosoftHostedNetworkConfiguration
from msgraph_beta.generated.models.cloud_pc_geographic_location_type import CloudPcGeographicLocationType
from msgraph_beta.generated.models.cloud_pc_region_group_configuration import CloudPcRegionGroupConfiguration
from msgraph_beta.generated.models.cloud_pc_region_group import CloudPcRegionGroup
from msgraph_beta.generated.models.cloud_pc_agent_pool_billing_configuration import CloudPcAgentPoolBillingConfiguration
from msgraph_beta.generated.models.cloud_pc_agent_pool_billing_type import CloudPcAgentPoolBillingType
from msgraph_beta.generated.models.cloud_pc_agent_pool_scaling_policy import CloudPcAgentPoolScalingPolicy
from msgraph_beta.generated.models.cloud_pc_agent_pool_capability_configuration import CloudPcAgentPoolCapabilityConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcAgentPool(
	odata_type = "#microsoft.graph.cloudPcAgentPool",
	display_name = "Contoso Development Pool",
	cloud_pc_configuration = CloudPcConfiguration(
		image_id = "microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365",
		image_type = CloudPcProvisioningPolicyImageType.Gallery,
		os_locale = "en-US",
	),
	network_configuration = CloudPcMicrosoftHostedNetworkConfiguration(
		odata_type = "#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration",
		geographic_location_type = CloudPcGeographicLocationType.UsWest,
		region_groups = [
			CloudPcRegionGroupConfiguration(
				region_group = CloudPcRegionGroup.UsWest,
				regions = [
					"westus2",
					"westus3",
				],
			),
		],
	),
	billing_configuration = CloudPcAgentPoolBillingConfiguration(
		billing_type = CloudPcAgentPoolBillingType.PayAsYouGo,
		billing_plan_id = "00000000-0000-0000-0000-000000000001",
	),
	scaling_policy = CloudPcAgentPoolScalingPolicy(
		minimum_count = 2,
		maximum_count = 10,
	),
	capabilities = CloudPcAgentPoolCapabilityConfiguration(
		odata_type = "#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration",
		enable_single_sign_on = True,
	),
)

result = await graph_client.device_management.virtual_endpoint.cloud_pc_pools.post(request_body)
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
  "id": "00000000-0000-0000-0000-000000000000",
  "displayName": "Contoso Development Pool",
  "cloudPcConfiguration": {
    "imageId": "microsoftwindowsdesktop_windows-ent-cpc_win11-23h2-ent-cpc-m365",
    "imageType": "gallery",
    "osLocale": "en-US"
  },
  "networkConfiguration": {
    "@odata.type": "#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration",
    "geographicLocationType": "usWest",
    "regionGroups": [
      {
        "regionGroup": "usWest",
        "regions": [
          "westus2",
          "westus3"
        ]
      }
    ]
  },
  "billingConfiguration": {
    "billingType": "payAsYouGo",
    "billingPlanId": "00000000-0000-0000-0000-000000000001"
  },
  "scalingPolicy": {
    "minimumCount": 2,
    "maximumCount": 10
  },
  "capabilities": {
    "@odata.type": "#microsoft.graph.cloudPcAgentPoolCapabilityConfiguration",
    "enableSingleSignOn": true
  }
}
```
