<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-post-rings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create ring

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object.

You can use this method with the following child object type: [qualityUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatering?view=graph-rest-beta).

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
POST /admin/windows/updates/policies/{policyId}/rings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object.

You can specify the following properties when you create a **ring** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| deferralInDays | Int32 | The quality update deferral period in days. The value must be between `0` and `30`. Optional. |
| description | String | The ring description. The maximum length is 1,500 characters. Required. |
| displayName | String | The ring display name. The maximum length is 200 characters. Required. |
| excludedGroupAssignment | [microsoft.graph.windowsUpdates.excludedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-excludedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with excluded groups. Groups are logical containers of devices represented by Microsoft Entra groups. Required. |
| includedGroupAssignment | [microsoft.graph.windowsUpdates.includedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-includedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with included groups. Groups are logical containers of devices represented by Microsoft Entra groups. Required. |
| isPaused | Boolean | The pause action for the quality update ring policy. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows how to create a quality update ring.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/admin/windows/updates/policies/86364b9d-d04a-46f3-b2ee-7ef4157ab6fc/rings
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateRing",
  "displayName": "Ring0 - IT devices",
  "description": "First deployment ring to test updates before going to prod.",
  "includedGroupAssignment": {
    "@odata.type": "microsoft.graph.windowsUpdates.includedGroupAssignment"
  },
  "excludedGroupAssignment": {
    "@odata.type": "microsoft.graph.windowsUpdates.excludedGroupAssignment"
  },
  "deferralInDays": 5,
  "isPaused": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.WindowsUpdates;

var requestBody = new QualityUpdateRing
{
	OdataType = "#microsoft.graph.windowsUpdates.qualityUpdateRing",
	DisplayName = "Ring0 - IT devices",
	Description = "First deployment ring to test updates before going to prod.",
	IncludedGroupAssignment = new IncludedGroupAssignment
	{
		OdataType = "microsoft.graph.windowsUpdates.includedGroupAssignment",
	},
	ExcludedGroupAssignment = new ExcludedGroupAssignment
	{
		OdataType = "microsoft.graph.windowsUpdates.excludedGroupAssignment",
	},
	DeferralInDays = 5,
	IsPaused = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.Policies["{policy-id}"].Rings.PostAsync(requestBody);
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

requestBody := graphmodelswindowsupdates.NewRing()
displayName := "Ring0 - IT devices"
requestBody.SetDisplayName(&displayName) 
description := "First deployment ring to test updates before going to prod."
requestBody.SetDescription(&description) 
includedGroupAssignment := graphmodelswindowsupdates.NewIncludedGroupAssignment()
requestBody.SetIncludedGroupAssignment(includedGroupAssignment)
excludedGroupAssignment := graphmodelswindowsupdates.NewExcludedGroupAssignment()
requestBody.SetExcludedGroupAssignment(excludedGroupAssignment)
deferralInDays := int32(5)
requestBody.SetDeferralInDays(&deferralInDays) 
isPaused := false
requestBody.SetIsPaused(&isPaused) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rings, err := graphClient.Admin().Windows().Updates().Policies().ByPolicyId("policy-id").Rings().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.windowsupdates.QualityUpdateRing ring = new com.microsoft.graph.beta.models.windowsupdates.QualityUpdateRing();
ring.setOdataType("#microsoft.graph.windowsUpdates.qualityUpdateRing");
ring.setDisplayName("Ring0 - IT devices");
ring.setDescription("First deployment ring to test updates before going to prod.");
com.microsoft.graph.beta.models.windowsupdates.IncludedGroupAssignment includedGroupAssignment = new com.microsoft.graph.beta.models.windowsupdates.IncludedGroupAssignment();
includedGroupAssignment.setOdataType("microsoft.graph.windowsUpdates.includedGroupAssignment");
ring.setIncludedGroupAssignment(includedGroupAssignment);
com.microsoft.graph.beta.models.windowsupdates.ExcludedGroupAssignment excludedGroupAssignment = new com.microsoft.graph.beta.models.windowsupdates.ExcludedGroupAssignment();
excludedGroupAssignment.setOdataType("microsoft.graph.windowsUpdates.excludedGroupAssignment");
ring.setExcludedGroupAssignment(excludedGroupAssignment);
ring.setDeferralInDays(5);
ring.setIsPaused(false);
com.microsoft.graph.models.windowsupdates.Ring result = graphClient.admin().windows().updates().policies().byPolicyId("{policy-id}").rings().post(ring);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const ring = {
  '@odata.type': '#microsoft.graph.windowsUpdates.qualityUpdateRing',
  displayName: 'Ring0 - IT devices',
  description: 'First deployment ring to test updates before going to prod.',
  includedGroupAssignment: {
    '@odata.type': 'microsoft.graph.windowsUpdates.includedGroupAssignment'
  },
  excludedGroupAssignment: {
    '@odata.type': 'microsoft.graph.windowsUpdates.excludedGroupAssignment'
  },
  deferralInDays: 5,
  isPaused: false
};

await client.api('/admin/windows/updates/policies/86364b9d-d04a-46f3-b2ee-7ef4157ab6fc/rings')
	.version('beta')
	.post(ring);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\QualityUpdateRing;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\IncludedGroupAssignment;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ExcludedGroupAssignment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new QualityUpdateRing();
$requestBody->setOdataType('#microsoft.graph.windowsUpdates.qualityUpdateRing');
$requestBody->setDisplayName('Ring0 - IT devices');
$requestBody->setDescription('First deployment ring to test updates before going to prod.');
$includedGroupAssignment = new IncludedGroupAssignment();
$includedGroupAssignment->setOdataType('microsoft.graph.windowsUpdates.includedGroupAssignment');
$requestBody->setIncludedGroupAssignment($includedGroupAssignment);
$excludedGroupAssignment = new ExcludedGroupAssignment();
$excludedGroupAssignment->setOdataType('microsoft.graph.windowsUpdates.excludedGroupAssignment');
$requestBody->setExcludedGroupAssignment($excludedGroupAssignment);
$requestBody->setDeferralInDays(5);
$requestBody->setIsPaused(false);

$result = $graphServiceClient->admin()->windows()->updates()->policies()->byPolicyId('policy-id')->rings()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	"@odata.type" = "#microsoft.graph.windowsUpdates.qualityUpdateRing"
	displayName = "Ring0 - IT devices"
	description = "First deployment ring to test updates before going to prod."
	includedGroupAssignment = @{
		"@odata.type" = "microsoft.graph.windowsUpdates.includedGroupAssignment"
	}
	excludedGroupAssignment = @{
		"@odata.type" = "microsoft.graph.windowsUpdates.excludedGroupAssignment"
	}
	deferralInDays = 5
	isPaused = $false
}

New-MgBetaWindowsUpdatesPolicyRing -PolicyId $policyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.windows_updates.quality_update_ring import QualityUpdateRing
from msgraph_beta.generated.models.windows_updates.included_group_assignment import IncludedGroupAssignment
from msgraph_beta.generated.models.windows_updates.excluded_group_assignment import ExcludedGroupAssignment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = QualityUpdateRing(
	odata_type = "#microsoft.graph.windowsUpdates.qualityUpdateRing",
	display_name = "Ring0 - IT devices",
	description = "First deployment ring to test updates before going to prod.",
	included_group_assignment = IncludedGroupAssignment(
		odata_type = "microsoft.graph.windowsUpdates.includedGroupAssignment",
	),
	excluded_group_assignment = ExcludedGroupAssignment(
		odata_type = "microsoft.graph.windowsUpdates.excludedGroupAssignment",
	),
	deferral_in_days = 5,
	is_paused = False,
)

result = await graph_client.admin.windows.updates.policies.by_policy_id('policy-id').rings.post(request_body)
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
  "@odata.type": "#microsoft.graph.windowsUpdates.ring",
  "displayName": "Ring0 - IT devices",
  "description": "First deployment ring to test updates before going to prod.",
  "includedGroupAssignment": {
    "@odata.type": "microsoft.graph.windowsUpdates.includedGroupAssignment"
  },
  "excludedGroupAssignment": {
    "@odata.type": "microsoft.graph.windowsUpdates.excludedGroupAssignment"
  },
  "deferralInDays": 5,
  "isPaused": false,
  "id": "03f72335-b88c-519e-16e7-039fdab8670f",
  "createdDateTime": "2020-06-09T10:00:00Z",
  "lastModifiedDateTime": "2020-06-09T10:00:00Z"
}
```
