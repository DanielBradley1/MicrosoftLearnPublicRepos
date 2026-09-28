<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpc-getprovisionedcloudpcs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPC: getProvisionedCloudPCs

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get all provisioned Cloud PCs of a specific service plan for users under a Microsoft Entra user group.

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
GET /deviceManagement/virtualEndpoint/cloudPCs/getProvisionedCloudPCs(groupId='{groupId}',servicePlanId='{servicePlanId}')
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. You can use `$select` to get specific properties, including those properties that aren't returned by default.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request parameter

| Parameter | Type | Description |
| :--- | :--- | :--- |
| groupId | String | The unique identifier for Microsoft Entra user group. |
| servicePlanId | String | The unique identifier of the service plan. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta) objects in the response body.

## Examples

### Example 1: Get all provisioned Cloud PCs and their default properties

The following example shows how to get all provisioned Cloud PCs and their default properties.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/getProvisionedCloudPCs(groupId='30d0e128-de93-41dc-89ec-33d84bb662a0',servicePlanId='9ecf691d-8b82-46cb-b254-cd061b2c02fb')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudPCs.GetProvisionedCloudPCsWithGroupIdWithServicePlanId("{groupId}","{servicePlanId}").GetAsGetProvisionedCloudPCsWithGroupIdWithServicePlanIdGetResponseAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groupId := "{groupId}"
servicePlanId := "{servicePlanId}"
getProvisionedCloudPCs, err := graphClient.DeviceManagement().VirtualEndpoint().CloudPCs().GetProvisionedCloudPCsWithGroupIdWithServicePlanId(&groupId, &servicePlanId).GetAsGetProvisionedCloudPCsWithGroupIdWithServicePlanIdGetResponse(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.deviceManagement().virtualEndpoint().cloudPCs().getProvisionedCloudPCsWithGroupIdWithServicePlanId("{groupId}", "{servicePlanId}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getProvisionedCloudPCs = await client.api('/deviceManagement/virtualEndpoint/cloudPCs/getProvisionedCloudPCs(groupId='30d0e128-de93-41dc-89ec-33d84bb662a0',servicePlanId='9ecf691d-8b82-46cb-b254-cd061b2c02fb')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudPCs()->getProvisionedCloudPCsWithGroupIdWithServicePlanId('{groupId}', '{servicePlanId}', )->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.device_management.virtual_endpoint.cloud_p_cs.get_provisioned_cloud_p_cs_with_group_id_with_service_plan_id("{groupId}","{servicePlanId}").get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. It includes only the default properties.

> **Note:** The response object shown here might be shortened for readability. All the default properties are returned in an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "value": [
        {
            "@odata.type": "#microsoft.graph.cloudPC",
            "id": "662009bc-7732-4f6f-8726-25883518b33e",
            "displayName": "Demo-0",
            "imageDisplayName": "Windows-10 19h1-evd",
            "aadDeviceId": "f5ff445f-7488-40f8-8ab9-ee784a9c1f33",
            "diskEncryptionState": "encryptedUsingCustomerManagedKey",
            "managedDeviceId": "bdc8e6dd-0455-4412-83d9-c818664fe1f1",
            "managedDeviceName": "CPC-ps1-SHYL-46",
            "provisioningPolicyId": "7ed725ad-0a00-4117-b557-d965c3732450",
            "servicePlanId": "9ecf691d-8b82-46cb-b254-cd061b2c02fb",
            "servicePlanName": "Cloud PC Enterprise 4vCPU/16GB/256GB",
            "servicePlanType": "enterprise",
            "status": "provisioned",
            "userPrincipalName": "pmitchell@contoso.com",
            "lastModifiedDateTime": "2020-07-23T10:29:57Z",
            "statusDetails": null,
            "provisioningType": "dedicated",
            "allotmentDisplayName": null,
            "deviceRegionName": "eastus2",
            "gracePeriodEndDateTime": null,
            "onPremisesConnectionName": "Test-OPNC",
            "partnerAgentInstallResults": null,
            "provisioningPolicyName": "Test-Policy"
        },
        {
            "@odata.type": "#microsoft.graph.cloudPC",
            "id": "ac74ae8b-85f7-4272-88cc-5419267403ed",
            "displayName": "Demo-1",
            "imageDisplayName": "Custom image name",
            "aadDeviceId": "61289490-ef06-4962-8f49-455329c8893c",
            "diskEncryptionState": "encryptedUsingCustomerManagedKey",
            "managedDeviceId": "e87f50c7-fa7f-4687-aade-dd45f3d65970",
            "managedDeviceName": "CPC-ps2-7ERZ-QE",
            "provisioningPolicyId": "13fa0778-ba00-438a-96d3-488c86029dff",
            "servicePlanId": "9ecf691d-8b82-46cb-b254-cd061b2c02fb",
            "servicePlanName": "Cloud PC Enterprise 4vCPU/16GB/256GB",
            "servicePlanType": "enterprise",
            "status": "provisioned",
            "userPrincipalName": "pmitchell@contoso.com",
            "lastModifiedDateTime": "2020-07-28T18:14:34Z",
            "statusDetails": null,
            "provisioningType": "dedicated",
            "allotmentDisplayName": null,
            "deviceRegionName": "eastus2",
            "gracePeriodEndDateTime": null,
            "onPremisesConnectionName": "Test-OPNC",
            "partnerAgentInstallResults": null,
            "provisioningPolicyName": "Test-Policy"
        }
    ]
}
```

### Example 2: Get all provisioned Cloud PCs and specific properties

The following example shows how to get all provisioned Cloud PCs and use `$select` to get specific properties, including those properties that aren't returned by default.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/getProvisionedCloudPCs(groupId='30d0e128-de93-41dc-89ec-33d84bb662a0',servicePlanId='9ecf691d-8b82-46cb-b254-cd061b2c02fb')?$select=id,displayName,powerState,connectivityResult,lastLoginResult,lastRemoteActionResult,osVersion,provisioningPolicyName,userAccountType,productType
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.CloudPCs.GetProvisionedCloudPCsWithGroupIdWithServicePlanId("{groupId}","{servicePlanId}").GetAsGetProvisionedCloudPCsWithGroupIdWithServicePlanIdGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "id","displayName","powerState","connectivityResult","lastLoginResult","lastRemoteActionResult","osVersion","provisioningPolicyName","userAccountType","productType" };
});
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
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/devicemanagement"
	  //other-imports
)

requestParameters := &graphdevicemanagement.VirtualEndpointCloudPCsGetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilderGetQueryParameters{
	Select: [] string {"id","displayName","powerState","connectivityResult","lastLoginResult","lastRemoteActionResult","osVersion","provisioningPolicyName","userAccountType","productType"},
}
configuration := &graphdevicemanagement.VirtualEndpointCloudPCsGetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
groupId := "{groupId}"
servicePlanId := "{servicePlanId}"
getProvisionedCloudPCs, err := graphClient.DeviceManagement().VirtualEndpoint().CloudPCs().GetProvisionedCloudPCsWithGroupIdWithServicePlanId(&groupId, &servicePlanId).GetAsGetProvisionedCloudPCsWithGroupIdWithServicePlanIdGetResponse(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.deviceManagement().virtualEndpoint().cloudPCs().getProvisionedCloudPCsWithGroupIdWithServicePlanId("{groupId}", "{servicePlanId}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"id", "displayName", "powerState", "connectivityResult", "lastLoginResult", "lastRemoteActionResult", "osVersion", "provisioningPolicyName", "userAccountType", "productType"};
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getProvisionedCloudPCs = await client.api('/deviceManagement/virtualEndpoint/cloudPCs/getProvisionedCloudPCs(groupId='30d0e128-de93-41dc-89ec-33d84bb662a0',servicePlanId='9ecf691d-8b82-46cb-b254-cd061b2c02fb')')
	.version('beta')
	.select('id,displayName,powerState,connectivityResult,lastLoginResult,lastRemoteActionResult,osVersion,provisioningPolicyName,userAccountType,productType')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\CloudPCs\GetProvisionedCloudPCs(groupId='{groupId}',servicePlanId='{servicePlanId}')\GetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilderGetRequestConfiguration();
$queryParameters = GetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["id","displayName","powerState","connectivityResult","lastLoginResult","lastRemoteActionResult","osVersion","provisioningPolicyName","userAccountType","productType"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->cloudPCs()->getProvisionedCloudPCsWithGroupIdWithServicePlanId('{groupId}', '{servicePlanId}', )->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.device_management.virtual_endpoint.cloud_p_cs.get_provisioned_cloud_p_cs(group_id='{group_id}',service_plan_id='{service_plan_id}').get_provisioned_cloud_p_cs_with_group_id_with_service_plan_id_request_builder import GetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilder.GetProvisionedCloudPCsWithGroupIdWithServicePlanIdRequestBuilderGetQueryParameters(
		select = ["id","displayName","powerState","connectivityResult","lastLoginResult","lastRemoteActionResult","osVersion","provisioningPolicyName","userAccountType","productType"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.device_management.virtual_endpoint.cloud_p_cs.get_provisioned_cloud_p_cs_with_group_id_with_service_plan_id("{groupId}","{servicePlanId}").get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudPC",
      "id": "662009bc-7732-4f6f-8726-25883518b33e",
      "displayName": "Demo-0",
      "powerState": "running",
      "connectivityResult": "",
      "lastLoginResult": "2020-07-23T10:29:57Z",
      "lastRemoteActionResult": "Succeed",
      "osVersion": null,
      "provisioningPolicyName": "Test-Policy",
      "userAccountType": null,
      "productType": null
    },
    {
      "@odata.type": "#microsoft.graph.cloudPC",
      "id": "ac74ae8b-85f7-4272-88cc-5419267403ed",
      "displayName": "Demo-1",
      "powerState": "running",
      "connectivityResult": "",
      "lastLoginResult": "2020-07-23T10:29:57Z",
      "lastRemoteActionResult": "Succeed",
      "osVersion": null,
      "provisioningPolicyName": "Test-Policy",
      "userAccountType": null,
      "productType": null
    }
  ]
}
```
