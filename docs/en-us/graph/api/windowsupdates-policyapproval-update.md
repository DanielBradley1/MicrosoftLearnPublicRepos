<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-policyapproval-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update policyApproval

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) object.

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
PATCH /admin/windows/updates/policies/{policyId}/approvals/{policyApprovalId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogEntryId | String | The catalog entry ID to approve. Optional. |
| status | microsoft.graph.windowsUpdates.approvalStatus | The approval status. The possible values are: `approved`, `suspended`, `unknownFutureValue`. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) object in the response body.

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
PATCH https://graph.microsoft.com/beta/admin/windows/updates/policies/45a01ef3-fb4b-8c1d-2428-1f060464033c/approvals/ab3a53f0-f7aa-10b1-04d4-8680584cbbb6
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.policyApproval",
  "catalogEntryId": "1d8864c1-531f-4d5b-8225-8653ef4316d8",
  "status": "suspended"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.WindowsUpdates;

var requestBody = new PolicyApproval
{
	OdataType = "#microsoft.graph.windowsUpdates.policyApproval",
	CatalogEntryId = "1d8864c1-531f-4d5b-8225-8653ef4316d8",
	Status = ApprovalStatus.Suspended,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.Policies["{policy-id}"].Approvals["{policyApproval-id}"].PatchAsync(requestBody);
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

requestBody := graphmodelswindowsupdates.NewPolicyApproval()
catalogEntryId := "1d8864c1-531f-4d5b-8225-8653ef4316d8"
requestBody.SetCatalogEntryId(&catalogEntryId) 
status := graphmodels.SUSPENDED_APPROVALSTATUS 
requestBody.SetStatus(&status) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
approvals, err := graphClient.Admin().Windows().Updates().Policies().ByPolicyId("policy-id").Approvals().ByPolicyApprovalId("policyApproval-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.windowsupdates.PolicyApproval policyApproval = new com.microsoft.graph.beta.models.windowsupdates.PolicyApproval();
policyApproval.setOdataType("#microsoft.graph.windowsUpdates.policyApproval");
policyApproval.setCatalogEntryId("1d8864c1-531f-4d5b-8225-8653ef4316d8");
policyApproval.setStatus(com.microsoft.graph.beta.models.windowsupdates.ApprovalStatus.Suspended);
com.microsoft.graph.models.windowsupdates.PolicyApproval result = graphClient.admin().windows().updates().policies().byPolicyId("{policy-id}").approvals().byPolicyApprovalId("{policyApproval-id}").patch(policyApproval);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const policyApproval = {
  '@odata.type': '#microsoft.graph.windowsUpdates.policyApproval',
  catalogEntryId: '1d8864c1-531f-4d5b-8225-8653ef4316d8',
  status: 'suspended'
};

await client.api('/admin/windows/updates/policies/45a01ef3-fb4b-8c1d-2428-1f060464033c/approvals/ab3a53f0-f7aa-10b1-04d4-8680584cbbb6')
	.version('beta')
	.update(policyApproval);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\PolicyApproval;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ApprovalStatus;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PolicyApproval();
$requestBody->setOdataType('#microsoft.graph.windowsUpdates.policyApproval');
$requestBody->setCatalogEntryId('1d8864c1-531f-4d5b-8225-8653ef4316d8');
$requestBody->setStatus(new ApprovalStatus('suspended'));

$result = $graphServiceClient->admin()->windows()->updates()->policies()->byPolicyId('policy-id')->approvals()->byPolicyApprovalId('policyApproval-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	"@odata.type" = "#microsoft.graph.windowsUpdates.policyApproval"
	catalogEntryId = "1d8864c1-531f-4d5b-8225-8653ef4316d8"
	status = "suspended"
}

Update-MgBetaWindowsUpdatesPolicyApproval -PolicyId $policyId -PolicyApprovalId $policyApprovalId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.windows_updates.policy_approval import PolicyApproval
from msgraph_beta.generated.models.approval_status import ApprovalStatus
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PolicyApproval(
	odata_type = "#microsoft.graph.windowsUpdates.policyApproval",
	catalog_entry_id = "1d8864c1-531f-4d5b-8225-8653ef4316d8",
	status = ApprovalStatus.Suspended,
)

result = await graph_client.admin.windows.updates.policies.by_policy_id('policy-id').approvals.by_policy_approval_id('policyApproval-id').patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.policyApproval",
  "catalogEntryId": "1d8864c1-531f-4d5b-8225-8653ef4316d8",
  "status": "suspended",
  "id": "ab3a53f0-f7aa-10b1-04d4-8680584cbbb6",
  "createdDateTime": "2020-06-09T10:00:00Z",
  "lastModifiedDateTime": "2020-06-09T10:00:00Z"
}
```
