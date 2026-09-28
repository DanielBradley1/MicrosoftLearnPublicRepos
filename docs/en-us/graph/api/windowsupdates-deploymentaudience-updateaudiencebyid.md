<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-updateaudiencebyid?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# deploymentAudience: updateAudienceById

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the members and exclusions collections of a [deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) with [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources of the same type.

Adding an [azureADDevice](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-azureaddevice?view=graph-rest-beta) to the members or exclusions collections of a deployment audience automatically creates a Microsoft Entra device object if it doesn't already exist.

If the same [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) gets included in the **exclusions** and **members** collections of a **deploymentAudience**, deployment will not apply to that asset.

You can also use the method [updateAudience](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-updateaudience?view=graph-rest-beta) to update the **deploymentAudience**.

Note

This API has a [known issue](https://learn.microsoft.com/en-us/graph/known-issues#accessing-and-updating-deployment-audiences-is-not-supported) related to deployments created via Intune.

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
POST /admin/windows/updates/deployments/{deploymentId}/audience/updateAudienceById
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| memberEntityType | String | The full type of the updatable assets. The possible values are: `#microsoft.graph.windowsUpdates.azureADDevice`, `#microsoft.graph.windowsUpdates.updatableAssetGroup`. |
| addMembers | String collection | List of identifiers corresponding to the updatable assets to add as members of the deployment audience. |
| removeMembers | String collection | List of identifiers corresponding to the updatable assets to remove as members of the deployment audience. |
| addExclusions | String collection | List of identifiers corresponding to the updatable assets to add as exclusions from the deployment audience. |
| removeExclusions | String collection | List of identifiers corresponding to the updatable assets to remove as exclusions from the deployment audience. |

## Response

If successful, this action returns a `202 Accepted` response code. It doesn't return anything in the response body.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/admin/windows/updates/deployments/b5171742-1742-b517-4217-17b5421717b5/audience/updateAudienceById
Content-Type: application/json

{
  "memberEntityType": "String",
  "addMembers": [
    "String"
  ],
  "removeMembers": [
    "String"
  ],
  "addExclusions": [
    "String"
  ],
  "removeExclusions": [
    "String"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Admin.Windows.Updates.Deployments.Item.Audience.MicrosoftGraphWindowsUpdatesUpdateAudienceById;

var requestBody = new UpdateAudienceByIdPostRequestBody
{
	MemberEntityType = "String",
	AddMembers = new List<string>
	{
		"String",
	},
	RemoveMembers = new List<string>
	{
		"String",
	},
	AddExclusions = new List<string>
	{
		"String",
	},
	RemoveExclusions = new List<string>
	{
		"String",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Admin.Windows.Updates.Deployments["{deployment-id}"].Audience.MicrosoftGraphWindowsUpdatesUpdateAudienceById.PostAsync(requestBody);
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
	  graphadmin "github.com/microsoftgraph/msgraph-beta-sdk-go/admin"
	  //other-imports
)

requestBody := graphadmin.NewUpdateAudienceByIdPostRequestBody()
memberEntityType := "String"
requestBody.SetMemberEntityType(&memberEntityType) 
addMembers := []string {
	"String",
}
requestBody.SetAddMembers(addMembers)
removeMembers := []string {
	"String",
}
requestBody.SetRemoveMembers(removeMembers)
addExclusions := []string {
	"String",
}
requestBody.SetAddExclusions(addExclusions)
removeExclusions := []string {
	"String",
}
requestBody.SetRemoveExclusions(removeExclusions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Admin().Windows().Updates().Deployments().ByDeploymentId("deployment-id").Audience().MicrosoftGraphWindowsUpdatesUpdateAudienceById().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.admin.windows.updates.deployments.item.audience.microsoftgraphwindowsupdatesupdateaudiencebyid.UpdateAudienceByIdPostRequestBody updateAudienceByIdPostRequestBody = new com.microsoft.graph.beta.admin.windows.updates.deployments.item.audience.microsoftgraphwindowsupdatesupdateaudiencebyid.UpdateAudienceByIdPostRequestBody();
updateAudienceByIdPostRequestBody.setMemberEntityType("String");
LinkedList<String> addMembers = new LinkedList<String>();
addMembers.add("String");
updateAudienceByIdPostRequestBody.setAddMembers(addMembers);
LinkedList<String> removeMembers = new LinkedList<String>();
removeMembers.add("String");
updateAudienceByIdPostRequestBody.setRemoveMembers(removeMembers);
LinkedList<String> addExclusions = new LinkedList<String>();
addExclusions.add("String");
updateAudienceByIdPostRequestBody.setAddExclusions(addExclusions);
LinkedList<String> removeExclusions = new LinkedList<String>();
removeExclusions.add("String");
updateAudienceByIdPostRequestBody.setRemoveExclusions(removeExclusions);
graphClient.admin().windows().updates().deployments().byDeploymentId("{deployment-id}").audience().microsoftGraphWindowsUpdatesUpdateAudienceById().post(updateAudienceByIdPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updateAudienceById = {
  memberEntityType: 'String',
  addMembers: [
    'String'
  ],
  removeMembers: [
    'String'
  ],
  addExclusions: [
    'String'
  ],
  removeExclusions: [
    'String'
  ]
};

await client.api('/admin/windows/updates/deployments/b5171742-1742-b517-4217-17b5421717b5/audience/updateAudienceById')
	.version('beta')
	.post(updateAudienceById);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Admin\Windows\Updates\Deployments\Item\Audience\MicrosoftGraphWindowsUpdatesUpdateAudienceById\UpdateAudienceByIdPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdateAudienceByIdPostRequestBody();
$requestBody->setMemberEntityType('String');
$requestBody->setAddMembers(['String', 	]);
$requestBody->setRemoveMembers(['String', 	]);
$requestBody->setAddExclusions(['String', 	]);
$requestBody->setRemoveExclusions(['String', 	]);

$graphServiceClient->admin()->windows()->updates()->deployments()->byDeploymentId('deployment-id')->audience()->microsoftGraphWindowsUpdatesUpdateAudienceById()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	memberEntityType = "String"
	addMembers = @(
	"String"
)
removeMembers = @(
"String"
)
addExclusions = @(
"String"
)
removeExclusions = @(
"String"
)
}

Update-MgBetaWindowsUpdatesDeploymentAudienceById -DeploymentId $deploymentId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.admin.windows.updates.deployments.item.audience.microsoft_graph_windows_updates_update_audience_by_id.update_audience_by_id_post_request_body import UpdateAudienceByIdPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdateAudienceByIdPostRequestBody(
	member_entity_type = "String",
	add_members = [
		"String",
	],
	remove_members = [
		"String",
	],
	add_exclusions = [
		"String",
	],
	remove_exclusions = [
		"String",
	],
)

await graph_client.admin.windows.updates.deployments.by_deployment_id('deployment-id').audience.microsoft_graph_windows_updates_update_audience_by_id.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 202 Accepted
```
