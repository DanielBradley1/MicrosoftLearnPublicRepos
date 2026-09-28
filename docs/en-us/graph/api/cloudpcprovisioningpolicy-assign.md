<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcprovisioningpolicy-assign?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudPcProvisioningPolicy: assign

Namespace: microsoft.graph

Assign a [cloudPcProvisioningPolicy](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicy?view=graph-rest-1.0) to user groups.

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
POST /deviceManagement/virtualEndpoint/provisioningPolicies/{id}/assign
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcProvisioningPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicyassignment?view=graph-rest-1.0) object.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| assignments | [cloudPcProvisioningPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcprovisioningpolicyassignment?view=graph-rest-1.0) collection | The collection of Cloud PC provisioning policy resources each to be assigned to the corresponding target group. Only Microsoft 365 groups and security groups in Microsoft Entra ID are currently supported. |

## Response

If successful, this method returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/provisioningPolicies/1d164206-bf41-4fd2-8424-a3192d39ffff/assign
Content-Type: application/json

{
  "assignments": [
    {
      "target": {
        "@odata.type": "microsoft.graph.cloudPcManagementGroupAssignmentTarget",
        "groupId": "64ff06de-9c00-4a5a-98b5-7f5abe26ffff"
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.DeviceManagement.VirtualEndpoint.ProvisioningPolicies.Item.Assign;
using Microsoft.Graph.Models;

var requestBody = new AssignPostRequestBody
{
	Assignments = new List<CloudPcProvisioningPolicyAssignment>
	{
		new CloudPcProvisioningPolicyAssignment
		{
			Target = new CloudPcManagementGroupAssignmentTarget
			{
				OdataType = "microsoft.graph.cloudPcManagementGroupAssignmentTarget",
				GroupId = "64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.ProvisioningPolicies["{cloudPcProvisioningPolicy-id}"].Assign.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-sdk-go/devicemanagement"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphdevicemanagement.NewAssignPostRequestBody()


cloudPcProvisioningPolicyAssignment := graphmodels.NewCloudPcProvisioningPolicyAssignment()
target := graphmodels.NewCloudPcManagementGroupAssignmentTarget()
groupId := "64ff06de-9c00-4a5a-98b5-7f5abe26ffff"
target.SetGroupId(&groupId) 
cloudPcProvisioningPolicyAssignment.SetTarget(target)

assignments := []graphmodels.CloudPcProvisioningPolicyAssignmentable {
	cloudPcProvisioningPolicyAssignment,
}
requestBody.SetAssignments(assignments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().ProvisioningPolicies().ByCloudPcProvisioningPolicyId("cloudPcProvisioningPolicy-id").Assign().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.devicemanagement.virtualendpoint.provisioningpolicies.item.assign.AssignPostRequestBody assignPostRequestBody = new com.microsoft.graph.devicemanagement.virtualendpoint.provisioningpolicies.item.assign.AssignPostRequestBody();
LinkedList<CloudPcProvisioningPolicyAssignment> assignments = new LinkedList<CloudPcProvisioningPolicyAssignment>();
CloudPcProvisioningPolicyAssignment cloudPcProvisioningPolicyAssignment = new CloudPcProvisioningPolicyAssignment();
CloudPcManagementGroupAssignmentTarget target = new CloudPcManagementGroupAssignmentTarget();
target.setOdataType("microsoft.graph.cloudPcManagementGroupAssignmentTarget");
target.setGroupId("64ff06de-9c00-4a5a-98b5-7f5abe26ffff");
cloudPcProvisioningPolicyAssignment.setTarget(target);
assignments.add(cloudPcProvisioningPolicyAssignment);
assignPostRequestBody.setAssignments(assignments);
graphClient.deviceManagement().virtualEndpoint().provisioningPolicies().byCloudPcProvisioningPolicyId("{cloudPcProvisioningPolicy-id}").assign().post(assignPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const assign = {
  assignments: [
    {
      target: {
        '@odata.type': 'microsoft.graph.cloudPcManagementGroupAssignmentTarget',
        groupId: '64ff06de-9c00-4a5a-98b5-7f5abe26ffff'
      }
    }
  ]
};

await client.api('/deviceManagement/virtualEndpoint/provisioningPolicies/1d164206-bf41-4fd2-8424-a3192d39ffff/assign')
	.post(assign);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DeviceManagement\VirtualEndpoint\ProvisioningPolicies\Item\Assign\AssignPostRequestBody;
use Microsoft\Graph\Generated\Models\CloudPcProvisioningPolicyAssignment;
use Microsoft\Graph\Generated\Models\CloudPcManagementGroupAssignmentTarget;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignPostRequestBody();
$assignmentsCloudPcProvisioningPolicyAssignment1 = new CloudPcProvisioningPolicyAssignment();
$assignmentsCloudPcProvisioningPolicyAssignment1Target = new CloudPcManagementGroupAssignmentTarget();
$assignmentsCloudPcProvisioningPolicyAssignment1Target->setOdataType('microsoft.graph.cloudPcManagementGroupAssignmentTarget');
$assignmentsCloudPcProvisioningPolicyAssignment1Target->setGroupId('64ff06de-9c00-4a5a-98b5-7f5abe26ffff');
$assignmentsCloudPcProvisioningPolicyAssignment1->setTarget($assignmentsCloudPcProvisioningPolicyAssignment1Target);
$assignmentsArray []= $assignmentsCloudPcProvisioningPolicyAssignment1;
$requestBody->setAssignments($assignmentsArray);


$graphServiceClient->deviceManagement()->virtualEndpoint()->provisioningPolicies()->byCloudPcProvisioningPolicyId('cloudPcProvisioningPolicy-id')->assign()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	assignments = @(
		@{
			target = @{
				"@odata.type" = "microsoft.graph.cloudPcManagementGroupAssignmentTarget"
				groupId = "64ff06de-9c00-4a5a-98b5-7f5abe26ffff"
			}
		}
	)
}

Set-MgDeviceManagementVirtualEndpointProvisioningPolicy -CloudPcProvisioningPolicyId $cloudPcProvisioningPolicyId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.devicemanagement.virtualendpoint.provisioningpolicies.item.assign.assign_post_request_body import AssignPostRequestBody
from msgraph.generated.models.cloud_pc_provisioning_policy_assignment import CloudPcProvisioningPolicyAssignment
from msgraph.generated.models.cloud_pc_management_group_assignment_target import CloudPcManagementGroupAssignmentTarget
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignPostRequestBody(
	assignments = [
		CloudPcProvisioningPolicyAssignment(
			target = CloudPcManagementGroupAssignmentTarget(
				odata_type = "microsoft.graph.cloudPcManagementGroupAssignmentTarget",
				group_id = "64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
			),
		),
	],
)

await graph_client.device_management.virtual_endpoint.provisioning_policies.by_cloud_pc_provisioning_policy_id('cloudPcProvisioningPolicy-id').assign.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
