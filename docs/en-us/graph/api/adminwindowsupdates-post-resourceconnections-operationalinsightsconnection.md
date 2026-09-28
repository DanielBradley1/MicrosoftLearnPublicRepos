<!-- Source: https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-resourceconnections-operationalinsightsconnection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# Create operationalInsightsConnection

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
POST /admin/windows/updates/resourceConnections
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) object.

You must specify the following properties when you create an **operationalInsightsConnection**.

| Property | Type | Description |
| :--- | :--- | :--- |
| azureResourceGroupName | String | The name of the Azure resource group that contains the Log Analytics workspace. |
| azureSubscriptionId | String | The Azure subscription ID that contains the Log Analytics workspace. |
| workspaceName | String | The name of the Log Analytics workspace. |

## Response

If successful, this method returns a `201 Created` response code and an [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) object in the response body.

The following errors are possible:

| Response Code | Message |
| :--- | :--- |
| `400 Bad Request` | The specified workspace was not able to be linked. Verify that the key properties are correct. |
| `403 Forbidden` | The specified workspace was not able to be linked. Verify that the Azure subscription is active. |
| `409 Conflict` | The specified resource already exists. |

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
POST https://graph.microsoft.com/beta/admin/windows/updates/resourceConnections
Content-Type: application/json
Content-length: 97

{
  "@odata.type": "#microsoft.graph.windowsUpdates.operationalInsightsConnection",
  "azureSubscriptionId": "322ec614-e9c2-4cd5-a55c-5711fdecf02e",
  "azureResourceGroupName": "target-resource-group",
  "workspaceName": "my-workspace"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.WindowsUpdates;

var requestBody = new OperationalInsightsConnection
{
	OdataType = "#microsoft.graph.windowsUpdates.operationalInsightsConnection",
	AzureSubscriptionId = "322ec614-e9c2-4cd5-a55c-5711fdecf02e",
	AzureResourceGroupName = "target-resource-group",
	WorkspaceName = "my-workspace",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.ResourceConnections.PostAsync(requestBody);
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
	  graphmodelswindowsupdates "github.com/microsoftgraph/msgraph-beta-sdk-go/models/windowsupdates"
	  //other-imports
)

requestBody := graphmodelswindowsupdates.NewResourceConnection()
azureSubscriptionId := "322ec614-e9c2-4cd5-a55c-5711fdecf02e"
requestBody.SetAzureSubscriptionId(&azureSubscriptionId) 
azureResourceGroupName := "target-resource-group"
requestBody.SetAzureResourceGroupName(&azureResourceGroupName) 
workspaceName := "my-workspace"
requestBody.SetWorkspaceName(&workspaceName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
resourceConnections, err := graphClient.Admin().Windows().Updates().ResourceConnections().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.windowsupdates.OperationalInsightsConnection resourceConnection = new com.microsoft.graph.beta.models.windowsupdates.OperationalInsightsConnection();
resourceConnection.setOdataType("#microsoft.graph.windowsUpdates.operationalInsightsConnection");
resourceConnection.setAzureSubscriptionId("322ec614-e9c2-4cd5-a55c-5711fdecf02e");
resourceConnection.setAzureResourceGroupName("target-resource-group");
resourceConnection.setWorkspaceName("my-workspace");
com.microsoft.graph.models.windowsupdates.ResourceConnection result = graphClient.admin().windows().updates().resourceConnections().post(resourceConnection);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const resourceConnection = {
  '@odata.type': '#microsoft.graph.windowsUpdates.operationalInsightsConnection',
  azureSubscriptionId: '322ec614-e9c2-4cd5-a55c-5711fdecf02e',
  azureResourceGroupName: 'target-resource-group',
  workspaceName: 'my-workspace'
};

await client.api('/admin/windows/updates/resourceConnections')
	.version('beta')
	.post(resourceConnection);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\OperationalInsightsConnection;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OperationalInsightsConnection();
$requestBody->setOdataType('#microsoft.graph.windowsUpdates.operationalInsightsConnection');
$requestBody->setAzureSubscriptionId('322ec614-e9c2-4cd5-a55c-5711fdecf02e');
$requestBody->setAzureResourceGroupName('target-resource-group');
$requestBody->setWorkspaceName('my-workspace');

$result = $graphServiceClient->admin()->windows()->updates()->resourceConnections()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	"@odata.type" = "#microsoft.graph.windowsUpdates.operationalInsightsConnection"
	azureSubscriptionId = "322ec614-e9c2-4cd5-a55c-5711fdecf02e"
	azureResourceGroupName = "target-resource-group"
	workspaceName = "my-workspace"
}

New-MgBetaWindowsUpdatesResourceConnection -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.windows_updates.operational_insights_connection import OperationalInsightsConnection
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OperationalInsightsConnection(
	odata_type = "#microsoft.graph.windowsUpdates.operationalInsightsConnection",
	azure_subscription_id = "322ec614-e9c2-4cd5-a55c-5711fdecf02e",
	azure_resource_group_name = "target-resource-group",
	workspace_name = "my-workspace",
)

result = await graph_client.admin.windows.updates.resource_connections.post(request_body)
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
  "@odata.type": "#microsoft.graph.windowsUpdates.operationalInsightsConnection",
  "id": "85fbecb2-e407-34e9-9298-4d587857795d",
  "azureSubscriptionId": "322ec614-e9c2-4cd5-a55c-5711fdecf02e",
  "azureResourceGroupName": "target-resource-group",
  "workspaceName": "my-workspace",
  "state": "connected"
}
```
