<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcusersetting-assign?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# cloudPcUserSetting: assign

Namespace: microsoft.graph

Assign a [cloudPcUserSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersetting?view=graph-rest-1.0) to user groups.

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
POST /deviceManagement/virtualEndpoint/userSettings/{id}/assign
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcUserSettingAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingassignment?view=graph-rest-1.0) object.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| assignments | [cloudPcUserSettingAssignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcusersettingassignment?view=graph-rest-1.0) collection | The collection of Cloud PC user setting resources each to be assigned to the corresponding target group. Only Microsoft 365 groups and security groups in Microsoft Entra ID are currently supported. |

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
POST https://graph.microsoft.com/v1.0/deviceManagement/virtualEndpoint/userSettings/b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff/assign
Content-Type: application/json

{
  "assignments": [
    {
      "id": "b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
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
using Microsoft.Graph.DeviceManagement.VirtualEndpoint.UserSettings.Item.Assign;
using Microsoft.Graph.Models;

var requestBody = new AssignPostRequestBody
{
	Assignments = new List<CloudPcUserSettingAssignment>
	{
		new CloudPcUserSettingAssignment
		{
			Id = "b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
			Target = new CloudPcManagementGroupAssignmentTarget
			{
				OdataType = "microsoft.graph.cloudPcManagementGroupAssignmentTarget",
				GroupId = "64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.DeviceManagement.VirtualEndpoint.UserSettings["{cloudPcUserSetting-id}"].Assign.PostAsync(requestBody);
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


cloudPcUserSettingAssignment := graphmodels.NewCloudPcUserSettingAssignment()
id := "b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff"
cloudPcUserSettingAssignment.SetId(&id) 
target := graphmodels.NewCloudPcManagementGroupAssignmentTarget()
groupId := "64ff06de-9c00-4a5a-98b5-7f5abe26ffff"
target.SetGroupId(&groupId) 
cloudPcUserSettingAssignment.SetTarget(target)

assignments := []graphmodels.CloudPcUserSettingAssignmentable {
	cloudPcUserSettingAssignment,
}
requestBody.SetAssignments(assignments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.DeviceManagement().VirtualEndpoint().UserSettings().ByCloudPcUserSettingId("cloudPcUserSetting-id").Assign().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.devicemanagement.virtualendpoint.usersettings.item.assign.AssignPostRequestBody assignPostRequestBody = new com.microsoft.graph.devicemanagement.virtualendpoint.usersettings.item.assign.AssignPostRequestBody();
LinkedList<CloudPcUserSettingAssignment> assignments = new LinkedList<CloudPcUserSettingAssignment>();
CloudPcUserSettingAssignment cloudPcUserSettingAssignment = new CloudPcUserSettingAssignment();
cloudPcUserSettingAssignment.setId("b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff");
CloudPcManagementGroupAssignmentTarget target = new CloudPcManagementGroupAssignmentTarget();
target.setOdataType("microsoft.graph.cloudPcManagementGroupAssignmentTarget");
target.setGroupId("64ff06de-9c00-4a5a-98b5-7f5abe26ffff");
cloudPcUserSettingAssignment.setTarget(target);
assignments.add(cloudPcUserSettingAssignment);
assignPostRequestBody.setAssignments(assignments);
graphClient.deviceManagement().virtualEndpoint().userSettings().byCloudPcUserSettingId("{cloudPcUserSetting-id}").assign().post(assignPostRequestBody);
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
      id: 'b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff',
      target: {
        '@odata.type': 'microsoft.graph.cloudPcManagementGroupAssignmentTarget',
        groupId: '64ff06de-9c00-4a5a-98b5-7f5abe26ffff'
      }
    }
  ]
};

await client.api('/deviceManagement/virtualEndpoint/userSettings/b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff/assign')
	.post(assign);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\DeviceManagement\VirtualEndpoint\UserSettings\Item\Assign\AssignPostRequestBody;
use Microsoft\Graph\Generated\Models\CloudPcUserSettingAssignment;
use Microsoft\Graph\Generated\Models\CloudPcManagementGroupAssignmentTarget;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AssignPostRequestBody();
$assignmentsCloudPcUserSettingAssignment1 = new CloudPcUserSettingAssignment();
$assignmentsCloudPcUserSettingAssignment1->setId('b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff');
$assignmentsCloudPcUserSettingAssignment1Target = new CloudPcManagementGroupAssignmentTarget();
$assignmentsCloudPcUserSettingAssignment1Target->setOdataType('microsoft.graph.cloudPcManagementGroupAssignmentTarget');
$assignmentsCloudPcUserSettingAssignment1Target->setGroupId('64ff06de-9c00-4a5a-98b5-7f5abe26ffff');
$assignmentsCloudPcUserSettingAssignment1->setTarget($assignmentsCloudPcUserSettingAssignment1Target);
$assignmentsArray []= $assignmentsCloudPcUserSettingAssignment1;
$requestBody->setAssignments($assignmentsArray);


$graphServiceClient->deviceManagement()->virtualEndpoint()->userSettings()->byCloudPcUserSettingId('cloudPcUserSetting-id')->assign()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.DeviceManagement.Administration

$params = @{
	assignments = @(
		@{
			id = "b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff"
			target = @{
				"@odata.type" = "microsoft.graph.cloudPcManagementGroupAssignmentTarget"
				groupId = "64ff06de-9c00-4a5a-98b5-7f5abe26ffff"
			}
		}
	)
}

Set-MgDeviceManagementVirtualEndpointUserSetting -CloudPcUserSettingId $cloudPcUserSettingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.devicemanagement.virtualendpoint.usersettings.item.assign.assign_post_request_body import AssignPostRequestBody
from msgraph.generated.models.cloud_pc_user_setting_assignment import CloudPcUserSettingAssignment
from msgraph.generated.models.cloud_pc_management_group_assignment_target import CloudPcManagementGroupAssignmentTarget
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AssignPostRequestBody(
	assignments = [
		CloudPcUserSettingAssignment(
			id = "b0c2d35f-3385-46c8-a6f5-6c3dfad7708b_64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
			target = CloudPcManagementGroupAssignmentTarget(
				odata_type = "microsoft.graph.cloudPcManagementGroupAssignmentTarget",
				group_id = "64ff06de-9c00-4a5a-98b5-7f5abe26ffff",
			),
		),
	],
)

await graph_client.device_management.virtual_endpoint.user_settings.by_cloud_pc_user_setting_id('cloudPcUserSetting-id').assign.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
