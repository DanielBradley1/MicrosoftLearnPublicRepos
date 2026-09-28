<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcprovisioningpolicy-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Get cloudPcProvisioningPolicy

Namespace: microsoft.graph

Read the properties and relationships of a [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

## HTTP request

```http
GET /deviceManagement/virtualEndpoint/provisioningPolicies/{id}
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get the properties of the specified provisioning policy

The following example shows how to get the properties of the specified provisioning policy.

#### Request

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
GET https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/provisioningPolicies/1d164206-bf41-4fd2-8424-a3192d39ffff
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.ProvisioningPolicies["{cloudPcProvisioningPolicy-id}"].GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningPolicies, err := graphClient.DeviceManagement().VirtualEndpoint().ProvisioningPolicies().ByCloudPcProvisioningPolicyId("cloudPcProvisioningPolicy-id").Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcProvisioningPolicy result = graphClient.deviceManagement().virtualEndpoint().provisioningPolicies().byCloudPcProvisioningPolicyId("{cloudPcProvisioningPolicy-id}").get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let cloudPcProvisioningPolicy = await client.api('/deviceManagement/virtualEndpoint/provisioningPolicies/1d164206-bf41-4fd2-8424-a3192d39ffff')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->provisioningPolicies()->byCloudPcProvisioningPolicyId('cloudPcProvisioningPolicy-id')->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

Get-MgDeviceManagementVirtualEndpointProvisioningPolicy -CloudPcProvisioningPolicyId $cloudPcProvisioningPolicyId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.device_management.virtual_endpoint.provisioning_policies.by_cloud_pc_provisioning_policy_id('cloudPcProvisioningPolicy-id').get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcProvisioningPolicy",
  "displayName": "HR provisioning policy",
  "description": "Provisioning policy for India HR employees",
  "domainJoinConfigurations": [
    {
      "onPremisesConnectionId": "16ee6c71-fc10-438b-88ac-daa1ccafffff",
      "domainJoinType": "hybridAzureADJoin"
    },
    {
      "onPremisesConnectionId": "26e16c71-f210-438b-88ac-d481ccafffff",
      "domainJoinType": "hybridAzureADJoin"
    }
  ],
  "microsoftManagedDesktop": {
      "managedType": "starterManaged",
      "profile": null
  },
  "autopatch": {
      "autopatchGroupId": "91197a0b-3a74-408d-ba88-bce3fdc4e5eb"
  },
  "enableSingleSignOn": true,
  "id": "1d164206-bf41-4fd2-8424-a3192d39ffff",
  "imageDisplayName": "Image for India HR employees",
  "imageId": "6d1e37b1-dc44-42fb-9fa3-3f524832d987",
  "imageType": "custom",
  "windowsSetting": {
    "locale": "en-US"
  },
  "provisioningType": "dedicated"
}
```

### Example 2: Get the properties of the specified provisioning policy and expand on the assignments

The following example shows how to get the properties of the specified provisioning policy and expand on the assignments.

#### Request

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
GET https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/provisioningPolicies/1d164206-bf41-4fd2-8424-a3192d39ffff?$expand=assignments
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.ProvisioningPolicies["{cloudPcProvisioningPolicy-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "assignments" };
});
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

requestParameters := &graphdevicemanagement.VirtualEndpointProvisioningPoliciesItemRequestBuilderGetQueryParameters{
	Expand: [] string {"assignments"},
}
configuration := &graphdevicemanagement.VirtualEndpointProvisioningPoliciesItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningPolicies, err := graphClient.DeviceManagement().VirtualEndpoint().ProvisioningPolicies().ByCloudPcProvisioningPolicyId("cloudPcProvisioningPolicy-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcProvisioningPolicy result = graphClient.deviceManagement().virtualEndpoint().provisioningPolicies().byCloudPcProvisioningPolicyId("{cloudPcProvisioningPolicy-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"assignments"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let cloudPcProvisioningPolicy = await client.api('/deviceManagement/virtualEndpoint/provisioningPolicies/1d164206-bf41-4fd2-8424-a3192d39ffff')
	.expand('assignments')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DeviceManagement\VirtualEndpoint\ProvisioningPolicies\Item\CloudPcProvisioningPolicyItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new CloudPcProvisioningPolicyItemRequestBuilderGetRequestConfiguration();
$queryParameters = CloudPcProvisioningPolicyItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["assignments"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->provisioningPolicies()->byCloudPcProvisioningPolicyId('cloudPcProvisioningPolicy-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

Get-MgDeviceManagementVirtualEndpointProvisioningPolicy -CloudPcProvisioningPolicyId $cloudPcProvisioningPolicyId -ExpandProperty "assignments" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.device_management.virtual_endpoint.provisioning_policies.item.cloud_pc_provisioning_policy_item_request_builder import CloudPcProvisioningPolicyItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = CloudPcProvisioningPolicyItemRequestBuilder.CloudPcProvisioningPolicyItemRequestBuilderGetQueryParameters(
		expand = ["assignments"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.device_management.virtual_endpoint.provisioning_policies.by_cloud_pc_provisioning_policy_id('cloudPcProvisioningPolicy-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcProvisioningPolicy",
  "displayName": "HR provisioning policy",
  "description": "Provisioning policy for India HR employees",
  "domainJoinConfigurations": [
    {
      "onPremisesConnectionId": "16ee6c71-fc10-438b-88ac-daa1ccafffff",
      "domainJoinType": "hybridAzureADJoin"
    },
    {
      "onPremisesConnectionId": "26e16c71-f210-438b-88ac-d481ccafffff",
      "domainJoinType": "hybridAzureADJoin"
    }
  ],
  "microsoftManagedDesktop": {
      "managedType": "starterManaged",
      "profile": null
  },
  "autopatch": {
      "autopatchGroupId": "91197a0b-3a74-408d-ba88-bce3fdc4e5eb"
  },
  "enableSingleSignOn": true,
  "id": "1d164206-bf41-4fd2-8424-a3192d39ffff",
  "imageDisplayName": "IndiaHRImage",
  "imageId": "6d1e37b1-dc44-42fb-9fa3-3f524832d987",
  "imageType": "custom",
  "windowsSetting": {
    "locale": "en-US"
  },
  "assignments": [
    {
      "@odata.type": "microsoft.graph.cloudPcProvisioningPolicyAssignment",
      "id": "b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
      "target": {
        "@odata.type": "microsoft.graph.cloudPCManagementGroupAssignmentTarget",
        "groupId": "64ff06de-9c00-4a5a-98b5-7f5abe26bfd9"
      }
    }
  ],
  "provisioningType": "dedicated"
}
```

### Example 3: Get the selected properties of the specified provisioning policy

The following example shows a request that retrieves the selected properties of the specified provisioning policy.

#### Request

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
GET https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/provisioningPolicies/60b94f83-3e22-430e-a69d-440f65b922d6?$select=id,description,displayName,domainJoinConfigurations,imageDisplayName,imageId,imageType,windowsSetting,cloudPcGroupDisplayName,gracePeriodInHours,localAdminEnabled,alternateResourceUrl
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.ProvisioningPolicies["{cloudPcProvisioningPolicy-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","description","displayName","domainJoinConfigurations","imageDisplayName","imageId","imageType","windowsSetting","cloudPcGroupDisplayName","gracePeriodInHours","localAdminEnabled","alternateResourceUrl" };
});
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

requestParameters := &graphdevicemanagement.VirtualEndpointProvisioningPoliciesItemRequestBuilderGetQueryParameters{
	Select: [] string {"id","description","displayName","domainJoinConfigurations","imageDisplayName","imageId","imageType","windowsSetting","cloudPcGroupDisplayName","gracePeriodInHours","localAdminEnabled","alternateResourceUrl"},
}
configuration := &graphdevicemanagement.VirtualEndpointProvisioningPoliciesItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
provisioningPolicies, err := graphClient.DeviceManagement().VirtualEndpoint().ProvisioningPolicies().ByCloudPcProvisioningPolicyId("cloudPcProvisioningPolicy-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcProvisioningPolicy result = graphClient.deviceManagement().virtualEndpoint().provisioningPolicies().byCloudPcProvisioningPolicyId("{cloudPcProvisioningPolicy-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "description", "displayName", "domainJoinConfigurations", "imageDisplayName", "imageId", "imageType", "windowsSetting", "cloudPcGroupDisplayName", "gracePeriodInHours", "localAdminEnabled", "alternateResourceUrl"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let cloudPcProvisioningPolicy = await client.api('/deviceManagement/virtualEndpoint/provisioningPolicies/60b94f83-3e22-430e-a69d-440f65b922d6')
	.select('id,description,displayName,domainJoinConfigurations,imageDisplayName,imageId,imageType,windowsSetting,cloudPcGroupDisplayName,gracePeriodInHours,localAdminEnabled,alternateResourceUrl')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DeviceManagement\VirtualEndpoint\ProvisioningPolicies\Item\CloudPcProvisioningPolicyItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new CloudPcProvisioningPolicyItemRequestBuilderGetRequestConfiguration();
$queryParameters = CloudPcProvisioningPolicyItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","description","displayName","domainJoinConfigurations","imageDisplayName","imageId","imageType","windowsSetting","cloudPcGroupDisplayName","gracePeriodInHours","localAdminEnabled","alternateResourceUrl"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->provisioningPolicies()->byCloudPcProvisioningPolicyId('cloudPcProvisioningPolicy-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

Get-MgDeviceManagementVirtualEndpointProvisioningPolicy -CloudPcProvisioningPolicyId $cloudPcProvisioningPolicyId -Property "id,description,displayName,domainJoinConfigurations,imageDisplayName,imageId,imageType,windowsSetting,cloudPcGroupDisplayName,gracePeriodInHours,localAdminEnabled,alternateResourceUrl" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.device_management.virtual_endpoint.provisioning_policies.item.cloud_pc_provisioning_policy_item_request_builder import CloudPcProvisioningPolicyItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = CloudPcProvisioningPolicyItemRequestBuilder.CloudPcProvisioningPolicyItemRequestBuilderGetQueryParameters(
		select = ["id","description","displayName","domainJoinConfigurations","imageDisplayName","imageId","imageType","windowsSetting","cloudPcGroupDisplayName","gracePeriodInHours","localAdminEnabled","alternateResourceUrl"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.device_management.virtual_endpoint.provisioning_policies.by_cloud_pc_provisioning_policy_id('cloudPcProvisioningPolicy-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcProvisioningPolicy",
  "alternateResourceUrl": "https://ms.portal.azure.com/#contoso.com/resource/subscriptions/827f2432-9c7b-4637-b694-570b3c2f969c/resourceGroups/myResourceGroupName/providers/Microsoft.Fidalgo/projects/myProjectName/pools/myPoolName",
  "cloudPcGroupDisplayName": "WestUSEmployeesCloudPcGroup",
  "description": "The ProvisioningPolicy for West US employees.",
  "displayName": "WestUsPolicy",
  "domainJoinConfigurations": [
    {
      "onPremisesConnectionId": "16ee6c71-fc10-438b-88ac-daa1ccafffff",
      "domainJoinType": "hybridAzureADJoin"
    },
    {
      "onPremisesConnectionId": "26e16c71-f210-438b-88ac-d481ccafffff",
      "domainJoinType": "hybridAzureADJoin"
    }
  ],
  "enableSingleSignOn": true,
  "gracePeriodInHours": 2,
  "id": "1d164206-bf41-4fd2-8424-a3192d39ffff",
  "imageDisplayName": "WestUSEmployeesCustomImage",
  "imageId": "d4e0541a-f7bb-4bdf-ad8f-b92b915a229f",
  "imageType": "custom",
  "localAdminEnabled": true,
  "windowsSetting": {
    "locale": "en-US"
  },
  "provisioningType": "dedicated"
}
```
