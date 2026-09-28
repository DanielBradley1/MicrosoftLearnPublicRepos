<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# Update policy

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object.

You can use this method with the following child object type: [qualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatepolicy?view=graph-rest-beta).

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
PATCH /admin/windows/updates/policies/{policyId}
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
| approvalRules | [microsoft.graph.windowsUpdates.approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta) collection | The approved rule of the policy that determines which published content matches the rule on an ongoing basis. Optional. |
| description | String | The quality update policy description. The maximum length is 1,500 characters. Optional. |
| displayName | String | The quality update policy display name. The maximum length is 200 characters. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows how to update a quality update policy.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/admin/windows/updates/policies/f316bfd9-c84e-a334-cebe-071d3c64b2c1
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdatePolicy",
  "displayName": "Patch Tuesday Test",
  "description": "Quality update policy to test upcoming Patch Tuesday updates",
  "approvalRules": [
    {
      "@odata.type": "microsoft.graph.windowsUpdates.qualityUpdateApprovalRule",
      "deferralInDays": 0,
      "classification": "nonSecurity",
      "cadence": "outOfBand"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.WindowsUpdates;

var requestBody = new QualityUpdatePolicy
{
	OdataType = "#microsoft.graph.windowsUpdates.qualityUpdatePolicy",
	DisplayName = "Patch Tuesday Test",
	Description = "Quality update policy to test upcoming Patch Tuesday updates",
	ApprovalRules = new List<ApprovalRule>
	{
		new QualityUpdateApprovalRule
		{
			OdataType = "microsoft.graph.windowsUpdates.qualityUpdateApprovalRule",
			DeferralInDays = 0,
			Classification = QualityUpdateClassification.NonSecurity,
			Cadence = QualityUpdateCadence.OutOfBand,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.Policies["{policy-id}"].PatchAsync(requestBody);
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

requestBody := graphmodelswindowsupdates.NewPolicy()
displayName := "Patch Tuesday Test"
requestBody.SetDisplayName(&displayName) 
description := "Quality update policy to test upcoming Patch Tuesday updates"
requestBody.SetDescription(&description) 


approvalRule := graphmodelswindowsupdates.NewQualityUpdateApprovalRule()
deferralInDays := int32(0)
approvalRule.SetDeferralInDays(&deferralInDays) 
classification := graphmodels.NONSECURITY_QUALITYUPDATECLASSIFICATION 
approvalRule.SetClassification(&classification) 
cadence := graphmodels.OUTOFBAND_QUALITYUPDATECADENCE 
approvalRule.SetCadence(&cadence) 

approvalRules := []graphmodelswindowsupdates.ApprovalRuleable {
	approvalRule,
}
requestBody.SetApprovalRules(approvalRules)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
policies, err := graphClient.Admin().Windows().Updates().Policies().ByPolicyId("policy-id").Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.windowsupdates.QualityUpdatePolicy policy = new com.microsoft.graph.beta.models.windowsupdates.QualityUpdatePolicy();
policy.setOdataType("#microsoft.graph.windowsUpdates.qualityUpdatePolicy");
policy.setDisplayName("Patch Tuesday Test");
policy.setDescription("Quality update policy to test upcoming Patch Tuesday updates");
LinkedList<com.microsoft.graph.beta.models.windowsupdates.ApprovalRule> approvalRules = new LinkedList<com.microsoft.graph.beta.models.windowsupdates.ApprovalRule>();
com.microsoft.graph.beta.models.windowsupdates.QualityUpdateApprovalRule approvalRule = new com.microsoft.graph.beta.models.windowsupdates.QualityUpdateApprovalRule();
approvalRule.setOdataType("microsoft.graph.windowsUpdates.qualityUpdateApprovalRule");
approvalRule.setDeferralInDays(0);
approvalRule.setClassification(com.microsoft.graph.beta.models.windowsupdates.QualityUpdateClassification.NonSecurity);
approvalRule.setCadence(com.microsoft.graph.beta.models.windowsupdates.QualityUpdateCadence.OutOfBand);
approvalRules.add(approvalRule);
policy.setApprovalRules(approvalRules);
com.microsoft.graph.models.windowsupdates.Policy result = graphClient.admin().windows().updates().policies().byPolicyId("{policy-id}").patch(policy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const policy = {
  '@odata.type': '#microsoft.graph.windowsUpdates.qualityUpdatePolicy',
  displayName: 'Patch Tuesday Test',
  description: 'Quality update policy to test upcoming Patch Tuesday updates',
  approvalRules: [
    {
      '@odata.type': 'microsoft.graph.windowsUpdates.qualityUpdateApprovalRule',
      deferralInDays: 0,
      classification: 'nonSecurity',
      cadence: 'outOfBand'
    }
  ]
};

await client.api('/admin/windows/updates/policies/f316bfd9-c84e-a334-cebe-071d3c64b2c1')
	.version('beta')
	.update(policy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\QualityUpdatePolicy;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ApprovalRule;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\QualityUpdateApprovalRule;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\QualityUpdateClassification;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\QualityUpdateCadence;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new QualityUpdatePolicy();
$requestBody->setOdataType('#microsoft.graph.windowsUpdates.qualityUpdatePolicy');
$requestBody->setDisplayName('Patch Tuesday Test');
$requestBody->setDescription('Quality update policy to test upcoming Patch Tuesday updates');
$approvalRulesApprovalRule1 = new QualityUpdateApprovalRule();
$approvalRulesApprovalRule1->setOdataType('microsoft.graph.windowsUpdates.qualityUpdateApprovalRule');
$approvalRulesApprovalRule1->setDeferralInDays(0);
$approvalRulesApprovalRule1->setClassification(new QualityUpdateClassification('nonSecurity'));
$approvalRulesApprovalRule1->setCadence(new QualityUpdateCadence('outOfBand'));
$approvalRulesArray []= $approvalRulesApprovalRule1;
$requestBody->setApprovalRules($approvalRulesArray);


$result = $graphServiceClient->admin()->windows()->updates()->policies()->byPolicyId('policy-id')->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	"@odata.type" = "#microsoft.graph.windowsUpdates.qualityUpdatePolicy"
	displayName = "Patch Tuesday Test"
	description = "Quality update policy to test upcoming Patch Tuesday updates"
	approvalRules = @(
		@{
			"@odata.type" = "microsoft.graph.windowsUpdates.qualityUpdateApprovalRule"
			deferralInDays = 0
			classification = "nonSecurity"
			cadence = "outOfBand"
		}
	)
}

Update-MgBetaWindowsUpdatesPolicy -PolicyId $policyId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.windows_updates.quality_update_policy import QualityUpdatePolicy
from msgraph_beta.generated.models.windows_updates.approval_rule import ApprovalRule
from msgraph_beta.generated.models.windows_updates.quality_update_approval_rule import QualityUpdateApprovalRule
from msgraph_beta.generated.models.quality_update_classification import QualityUpdateClassification
from msgraph_beta.generated.models.quality_update_cadence import QualityUpdateCadence
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = QualityUpdatePolicy(
	odata_type = "#microsoft.graph.windowsUpdates.qualityUpdatePolicy",
	display_name = "Patch Tuesday Test",
	description = "Quality update policy to test upcoming Patch Tuesday updates",
	approval_rules = [
		QualityUpdateApprovalRule(
			odata_type = "microsoft.graph.windowsUpdates.qualityUpdateApprovalRule",
			deferral_in_days = 0,
			classification = QualityUpdateClassification.NonSecurity,
			cadence = QualityUpdateCadence.OutOfBand,
		),
	],
)

result = await graph_client.admin.windows.updates.policies.by_policy_id('policy-id').patch(request_body)
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
  "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdatePolicy",
  "displayName": "Patch Tuesday Test",
  "description": "Quality update policy to test upcoming Patch Tuesday updates",
  "approvalRules": [
    {
      "@odata.type": "microsoft.graph.windowsUpdates.qualityUpdateApprovalRule",
      "deferralInDays": 0,
      "classification": "nonSecurity",
      "cadence": "outOfBand"
    }
  ],
  "id": "f316bfd9-c84e-a334-cebe-071d3c64b2c1",
  "createdDateTime": "2020-06-09T10:00:00Z",
  "lastModifiedDateTime": "2020-06-09T10:00:00Z"
}
```
