<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-bulkactions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-27 -->

# Create cloudPcBulkAction

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object.

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
POST /deviceManagement/virtualEndpoint/bulkActions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object.

You can specify the following properties when you create a **cloudPcBulkAction**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name of this bulk action. Required. |
| cloudPcIds | String collection | IDs of the Cloud PCs the bulk action applies to. Required. |
| scheduledDuringMaintenanceWindow | Boolean | Indicates whether the bulk actions can be initiated during maintenance window. When `true`, bulk action will use maintenance window to schedule action, When `false` means bulk action will not use the maintenance window. Default value is `false`. |

## Response

If successful, this method returns a `201 Created` response code and a [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/bulkActions
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.cloudPcBulkAction",
  "displayName": "Bulk Power Off by Andy",
  "cloudPcIds": [
    "d6e0b8ee-8836-4b8d-b038-6130a97a3a9d",
    "85994912-197b-4927-b569-447bd81350ec"
  ],
  "scheduledDuringMaintenanceWindow": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CloudPcBulkAction
{
	OdataType = "#microsoft.graph.cloudPcBulkAction",
	DisplayName = "Bulk Power Off by Andy",
	CloudPcIds = new List<string>
	{
		"d6e0b8ee-8836-4b8d-b038-6130a97a3a9d",
		"85994912-197b-4927-b569-447bd81350ec",
	},
	ScheduledDuringMaintenanceWindow = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.BulkActions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCloudPcBulkAction()
displayName := "Bulk Power Off by Andy"
requestBody.SetDisplayName(&displayName) 
cloudPcIds := []string {
	"d6e0b8ee-8836-4b8d-b038-6130a97a3a9d",
	"85994912-197b-4927-b569-447bd81350ec",
}
requestBody.SetCloudPcIds(cloudPcIds)
scheduledDuringMaintenanceWindow := true
requestBody.SetScheduledDuringMaintenanceWindow(&scheduledDuringMaintenanceWindow) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bulkActions, err := graphClient.DeviceManagement().VirtualEndpoint().BulkActions().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CloudPcBulkAction cloudPcBulkAction = new CloudPcBulkAction();
cloudPcBulkAction.setOdataType("#microsoft.graph.cloudPcBulkAction");
cloudPcBulkAction.setDisplayName("Bulk Power Off by Andy");
LinkedList<String> cloudPcIds = new LinkedList<String>();
cloudPcIds.add("d6e0b8ee-8836-4b8d-b038-6130a97a3a9d");
cloudPcIds.add("85994912-197b-4927-b569-447bd81350ec");
cloudPcBulkAction.setCloudPcIds(cloudPcIds);
cloudPcBulkAction.setScheduledDuringMaintenanceWindow(true);
CloudPcBulkAction result = graphClient.deviceManagement().virtualEndpoint().bulkActions().post(cloudPcBulkAction);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcBulkAction = {
  '@odata.type': '#microsoft.graph.cloudPcBulkAction',
  displayName: 'Bulk Power Off by Andy',
  cloudPcIds: [
    'd6e0b8ee-8836-4b8d-b038-6130a97a3a9d',
    '85994912-197b-4927-b569-447bd81350ec'
  ],
  scheduledDuringMaintenanceWindow: true
};

await client.api('/deviceManagement/virtualEndpoint/bulkActions')
	.version('beta')
	.post(cloudPcBulkAction);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CloudPcBulkAction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CloudPcBulkAction();
$requestBody->setOdataType('#microsoft.graph.cloudPcBulkAction');
$requestBody->setDisplayName('Bulk Power Off by Andy');
$requestBody->setCloudPcIds(['d6e0b8ee-8836-4b8d-b038-6130a97a3a9d', '85994912-197b-4927-b569-447bd81350ec', 	]);
$requestBody->setScheduledDuringMaintenanceWindow(true);

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->bulkActions()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement.Administration

$params = @{
	"@odata.type" = "#microsoft.graph.cloudPcBulkAction"
	displayName = "Bulk Power Off by Andy"
	cloudPcIds = @(
	"d6e0b8ee-8836-4b8d-b038-6130a97a3a9d"
"85994912-197b-4927-b569-447bd81350ec"
)
scheduledDuringMaintenanceWindow = $true
}

New-MgBetaDeviceManagementVirtualEndpointBulkAction -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.cloud_pc_bulk_action import CloudPcBulkAction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CloudPcBulkAction(
	odata_type = "#microsoft.graph.cloudPcBulkAction",
	display_name = "Bulk Power Off by Andy",
	cloud_pc_ids = [
		"d6e0b8ee-8836-4b8d-b038-6130a97a3a9d",
		"85994912-197b-4927-b569-447bd81350ec",
	],
	scheduled_during_maintenance_window = True,
)

result = await graph_client.device_management.virtual_endpoint.bulk_actions.post(request_body)
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
  "@odata.type": "#microsoft.graph.cloudPcBulkAction",
  "id": "231ad98f-41b3-872b-dd37-c70bf22cbdac",
  "displayName": "Bulk Power Off by Andy",
  "cloudPcIds": [
    "d6e0b8ee-8836-4b8d-b038-6130a97a3a9d",
    "85994912-197b-4927-b569-447bd81350ec"
  ],
  "actionSummary": null,
  "initiatedByUserPrincipalName": "johnd@contoso.com",
  "scheduledDuringMaintenanceWindow": true,
  "status": "pending",
  "createdDateTime": "2024-02-05T10:29:57Z"
}
```
