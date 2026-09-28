<!-- Source: https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-updatepolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# Create updatePolicy

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) object.

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
POST /admin/windows/updates/updatePolicies
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) object.

You can specify the following properties when you create an **updatePolicy**.

| Property | Type | Description |
| :--- | :--- | :--- |
| audience | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) | Specifies the audience to target. |
| complianceChanges | [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) collection | Compliance changes like content approvals which result in the automatic creation of deployments using the **audience** and **deploymentSettings** of the policy. |
| complianceChangeRules | [microsoft.graph.windowsUpdates.complianceChangeRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechangerule?view=graph-rest-beta) collection | Rules for governing the automatic creation of compliance changes. |
| deploymentSettings | [microsoft.graph.windowsUpdates.deploymentSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentsettings?view=graph-rest-beta) | Settings for governing how to deploy **content**. |

## Response

If successful, this method returns a `201 Created` response code and an [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) object in the response body.

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
POST https://graph.microsoft.com/beta/admin/windows/updates/updatePolicies
Content-Type: application/json
Content-length: 835

{
  "@odata.type": "#microsoft.graph.windowsUpdates.updatePolicy",
  "audience": {
    "id": "8c4eb1eb-d7a3-4633-8e2f-f926e82df08e"
  },
  "complianceChanges": [
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.contentApproval"
    }
  ],
  "complianceChangeRules": [
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.contentApprovalRule",
      "contentFilter": {
        "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateFilter"
      },
      "durationBeforeDeploymentStart": "P7D"
    }
  ],
  "deploymentSettings": {
    "@odata.type": "microsoft.graph.windowsUpdates.deploymentSettings",
    "schedule": {
      "gradualRollout": {
        "@odata.type": "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
        "durationBetweenOffers": "P1D",
        "devicePerOffer": 1000
      }
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.WindowsUpdates;

var requestBody = new UpdatePolicy
{
	OdataType = "#microsoft.graph.windowsUpdates.updatePolicy",
	Audience = new DeploymentAudience
	{
		Id = "8c4eb1eb-d7a3-4633-8e2f-f926e82df08e",
	},
	ComplianceChanges = new List<ComplianceChange>
	{
		new ContentApproval
		{
			OdataType = "#microsoft.graph.windowsUpdates.contentApproval",
		},
	},
	ComplianceChangeRules = new List<ComplianceChangeRule>
	{
		new ContentApprovalRule
		{
			OdataType = "#microsoft.graph.windowsUpdates.contentApprovalRule",
			ContentFilter = new DriverUpdateFilter
			{
				OdataType = "#microsoft.graph.windowsUpdates.driverUpdateFilter",
			},
			DurationBeforeDeploymentStart = TimeSpan.Parse("P7D"),
		},
	},
	DeploymentSettings = new DeploymentSettings
	{
		OdataType = "microsoft.graph.windowsUpdates.deploymentSettings",
		Schedule = new ScheduleSettings
		{
			GradualRollout = new RateDrivenRolloutSettings
			{
				OdataType = "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
				DurationBetweenOffers = TimeSpan.Parse("P1D"),
				AdditionalData = new Dictionary<string, object>
				{
					{
						"devicePerOffer" , 1000
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.UpdatePolicies.PostAsync(requestBody);
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

requestBody := graphmodelswindowsupdates.NewUpdatePolicy()
audience := graphmodelswindowsupdates.NewDeploymentAudience()
id := "8c4eb1eb-d7a3-4633-8e2f-f926e82df08e"
audience.SetId(&id) 
requestBody.SetAudience(audience)


complianceChange := graphmodelswindowsupdates.NewContentApproval()

complianceChanges := []graphmodelswindowsupdates.ComplianceChangeable {
	complianceChange,
}
requestBody.SetComplianceChanges(complianceChanges)


complianceChangeRule := graphmodelswindowsupdates.NewContentApprovalRule()
contentFilter := graphmodelswindowsupdates.NewDriverUpdateFilter()
complianceChangeRule.SetContentFilter(contentFilter)
durationBeforeDeploymentStart , err := abstractions.ParseISODuration("P7D")
complianceChangeRule.SetDurationBeforeDeploymentStart(&durationBeforeDeploymentStart) 

complianceChangeRules := []graphmodelswindowsupdates.ComplianceChangeRuleable {
	complianceChangeRule,
}
requestBody.SetComplianceChangeRules(complianceChangeRules)
deploymentSettings := graphmodelswindowsupdates.NewDeploymentSettings()
schedule := graphmodelswindowsupdates.NewScheduleSettings()
gradualRollout := graphmodelswindowsupdates.NewRateDrivenRolloutSettings()
durationBetweenOffers , err := abstractions.ParseISODuration("P1D")
gradualRollout.SetDurationBetweenOffers(&durationBetweenOffers) 
additionalData := map[string]interface{}{
	"devicePerOffer" : int32(1000) , 
}
gradualRollout.SetAdditionalData(additionalData)
schedule.SetGradualRollout(gradualRollout)
deploymentSettings.SetSchedule(schedule)
requestBody.SetDeploymentSettings(deploymentSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
updatePolicies, err := graphClient.Admin().Windows().Updates().UpdatePolicies().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.windowsupdates.UpdatePolicy updatePolicy = new com.microsoft.graph.beta.models.windowsupdates.UpdatePolicy();
updatePolicy.setOdataType("#microsoft.graph.windowsUpdates.updatePolicy");
com.microsoft.graph.beta.models.windowsupdates.DeploymentAudience audience = new com.microsoft.graph.beta.models.windowsupdates.DeploymentAudience();
audience.setId("8c4eb1eb-d7a3-4633-8e2f-f926e82df08e");
updatePolicy.setAudience(audience);
LinkedList<com.microsoft.graph.beta.models.windowsupdates.ComplianceChange> complianceChanges = new LinkedList<com.microsoft.graph.beta.models.windowsupdates.ComplianceChange>();
com.microsoft.graph.beta.models.windowsupdates.ContentApproval complianceChange = new com.microsoft.graph.beta.models.windowsupdates.ContentApproval();
complianceChange.setOdataType("#microsoft.graph.windowsUpdates.contentApproval");
complianceChanges.add(complianceChange);
updatePolicy.setComplianceChanges(complianceChanges);
LinkedList<com.microsoft.graph.beta.models.windowsupdates.ComplianceChangeRule> complianceChangeRules = new LinkedList<com.microsoft.graph.beta.models.windowsupdates.ComplianceChangeRule>();
com.microsoft.graph.beta.models.windowsupdates.ContentApprovalRule complianceChangeRule = new com.microsoft.graph.beta.models.windowsupdates.ContentApprovalRule();
complianceChangeRule.setOdataType("#microsoft.graph.windowsUpdates.contentApprovalRule");
com.microsoft.graph.beta.models.windowsupdates.DriverUpdateFilter contentFilter = new com.microsoft.graph.beta.models.windowsupdates.DriverUpdateFilter();
contentFilter.setOdataType("#microsoft.graph.windowsUpdates.driverUpdateFilter");
complianceChangeRule.setContentFilter(contentFilter);
PeriodAndDuration durationBeforeDeploymentStart = PeriodAndDuration.ofDuration(Duration.parse("P7D"));
complianceChangeRule.setDurationBeforeDeploymentStart(durationBeforeDeploymentStart);
complianceChangeRules.add(complianceChangeRule);
updatePolicy.setComplianceChangeRules(complianceChangeRules);
com.microsoft.graph.beta.models.windowsupdates.DeploymentSettings deploymentSettings = new com.microsoft.graph.beta.models.windowsupdates.DeploymentSettings();
deploymentSettings.setOdataType("microsoft.graph.windowsUpdates.deploymentSettings");
com.microsoft.graph.beta.models.windowsupdates.ScheduleSettings schedule = new com.microsoft.graph.beta.models.windowsupdates.ScheduleSettings();
com.microsoft.graph.beta.models.windowsupdates.RateDrivenRolloutSettings gradualRollout = new com.microsoft.graph.beta.models.windowsupdates.RateDrivenRolloutSettings();
gradualRollout.setOdataType("#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings");
PeriodAndDuration durationBetweenOffers = PeriodAndDuration.ofDuration(Duration.parse("P1D"));
gradualRollout.setDurationBetweenOffers(durationBetweenOffers);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("devicePerOffer", 1000);
gradualRollout.setAdditionalData(additionalData);
schedule.setGradualRollout(gradualRollout);
deploymentSettings.setSchedule(schedule);
updatePolicy.setDeploymentSettings(deploymentSettings);
com.microsoft.graph.models.windowsupdates.UpdatePolicy result = graphClient.admin().windows().updates().updatePolicies().post(updatePolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const updatePolicy = {
  '@odata.type': '#microsoft.graph.windowsUpdates.updatePolicy',
  audience: {
    id: '8c4eb1eb-d7a3-4633-8e2f-f926e82df08e'
  },
  complianceChanges: [
    {
      '@odata.type': '#microsoft.graph.windowsUpdates.contentApproval'
    }
  ],
  complianceChangeRules: [
    {
      '@odata.type': '#microsoft.graph.windowsUpdates.contentApprovalRule',
      contentFilter: {
        '@odata.type': '#microsoft.graph.windowsUpdates.driverUpdateFilter'
      },
      durationBeforeDeploymentStart: 'P7D'
    }
  ],
  deploymentSettings: {
    '@odata.type': 'microsoft.graph.windowsUpdates.deploymentSettings',
    schedule: {
      gradualRollout: {
        '@odata.type': '#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings',
        durationBetweenOffers: 'P1D',
        devicePerOffer: 1000
      }
    }
  }
};

await client.api('/admin/windows/updates/updatePolicies')
	.version('beta')
	.post(updatePolicy);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\UpdatePolicy;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\DeploymentAudience;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ComplianceChange;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ContentApproval;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ComplianceChangeRule;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ContentApprovalRule;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\DriverUpdateFilter;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\DeploymentSettings;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ScheduleSettings;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\RateDrivenRolloutSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new UpdatePolicy();
$requestBody->setOdataType('#microsoft.graph.windowsUpdates.updatePolicy');
$audience = new DeploymentAudience();
$audience->setId('8c4eb1eb-d7a3-4633-8e2f-f926e82df08e');
$requestBody->setAudience($audience);
$complianceChangesComplianceChange1 = new ContentApproval();
$complianceChangesComplianceChange1->setOdataType('#microsoft.graph.windowsUpdates.contentApproval');
$complianceChangesArray []= $complianceChangesComplianceChange1;
$requestBody->setComplianceChanges($complianceChangesArray);

$complianceChangeRulesComplianceChangeRule1 = new ContentApprovalRule();
$complianceChangeRulesComplianceChangeRule1->setOdataType('#microsoft.graph.windowsUpdates.contentApprovalRule');
$complianceChangeRulesComplianceChangeRule1ContentFilter = new DriverUpdateFilter();
$complianceChangeRulesComplianceChangeRule1ContentFilter->setOdataType('#microsoft.graph.windowsUpdates.driverUpdateFilter');
$complianceChangeRulesComplianceChangeRule1->setContentFilter($complianceChangeRulesComplianceChangeRule1ContentFilter);
$complianceChangeRulesComplianceChangeRule1->setDurationBeforeDeploymentStart(new \DateInterval('P7D'));
$complianceChangeRulesArray []= $complianceChangeRulesComplianceChangeRule1;
$requestBody->setComplianceChangeRules($complianceChangeRulesArray);

$deploymentSettings = new DeploymentSettings();
$deploymentSettings->setOdataType('microsoft.graph.windowsUpdates.deploymentSettings');
$deploymentSettingsSchedule = new ScheduleSettings();
$deploymentSettingsScheduleGradualRollout = new RateDrivenRolloutSettings();
$deploymentSettingsScheduleGradualRollout->setOdataType('#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings');
$deploymentSettingsScheduleGradualRollout->setDurationBetweenOffers(new \DateInterval('P1D'));
$additionalData = [
'devicePerOffer' => 1000,
];
$deploymentSettingsScheduleGradualRollout->setAdditionalData($additionalData);
$deploymentSettingsSchedule->setGradualRollout($deploymentSettingsScheduleGradualRollout);
$deploymentSettings->setSchedule($deploymentSettingsSchedule);
$requestBody->setDeploymentSettings($deploymentSettings);

$result = $graphServiceClient->admin()->windows()->updates()->updatePolicies()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	"@odata.type" = "#microsoft.graph.windowsUpdates.updatePolicy"
	audience = @{
		id = "8c4eb1eb-d7a3-4633-8e2f-f926e82df08e"
	}
	complianceChanges = @(
		@{
			"@odata.type" = "#microsoft.graph.windowsUpdates.contentApproval"
		}
	)
	complianceChangeRules = @(
		@{
			"@odata.type" = "#microsoft.graph.windowsUpdates.contentApprovalRule"
			contentFilter = @{
				"@odata.type" = "#microsoft.graph.windowsUpdates.driverUpdateFilter"
			}
			durationBeforeDeploymentStart = "P7D"
		}
	)
	deploymentSettings = @{
		"@odata.type" = "microsoft.graph.windowsUpdates.deploymentSettings"
		schedule = @{
			gradualRollout = @{
				"@odata.type" = "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings"
				durationBetweenOffers = "P1D"
				devicePerOffer = 
			}
		}
	}
}

New-MgBetaWindowsUpdatesUpdatePolicy -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.windows_updates.update_policy import UpdatePolicy
from msgraph_beta.generated.models.windows_updates.deployment_audience import DeploymentAudience
from msgraph_beta.generated.models.windows_updates.compliance_change import ComplianceChange
from msgraph_beta.generated.models.windows_updates.content_approval import ContentApproval
from msgraph_beta.generated.models.windows_updates.compliance_change_rule import ComplianceChangeRule
from msgraph_beta.generated.models.windows_updates.content_approval_rule import ContentApprovalRule
from msgraph_beta.generated.models.windows_updates.driver_update_filter import DriverUpdateFilter
from msgraph_beta.generated.models.windows_updates.deployment_settings import DeploymentSettings
from msgraph_beta.generated.models.windows_updates.schedule_settings import ScheduleSettings
from msgraph_beta.generated.models.windows_updates.rate_driven_rollout_settings import RateDrivenRolloutSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = UpdatePolicy(
	odata_type = "#microsoft.graph.windowsUpdates.updatePolicy",
	audience = DeploymentAudience(
		id = "8c4eb1eb-d7a3-4633-8e2f-f926e82df08e",
	),
	compliance_changes = [
		ContentApproval(
			odata_type = "#microsoft.graph.windowsUpdates.contentApproval",
		),
	],
	compliance_change_rules = [
		ContentApprovalRule(
			odata_type = "#microsoft.graph.windowsUpdates.contentApprovalRule",
			content_filter = DriverUpdateFilter(
				odata_type = "#microsoft.graph.windowsUpdates.driverUpdateFilter",
			),
			duration_before_deployment_start = "P7D",
		),
	],
	deployment_settings = DeploymentSettings(
		odata_type = "microsoft.graph.windowsUpdates.deploymentSettings",
		schedule = ScheduleSettings(
			gradual_rollout = RateDrivenRolloutSettings(
				odata_type = "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
				duration_between_offers = "P1D",
				additional_data = {
						"device_per_offer" : 1000,
				}
			),
		),
	),
)

result = await graph_client.admin.windows.updates.update_policies.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#admin/windows/updates/updatePolicies/$entity",
    "id": "1b35b81b-f839-4951-882a-1fbfc6446409",
    "createdDateTime": "String (timestamp)",
    "autoEnrollmentUpdateCategories": [],
    "complianceChangeRules": [
        {
            "@odata.type": "#microsoft.graph.windowsUpdates.contentApprovalRule",
            "createdDateTime": "String (timestamp)",
            "lastEvaluatedDateTime": "String (timestamp)",
            "lastModifiedDateTime": "String (timestamp)",
            "durationBeforeDeploymentStart": "P7D",
            "contentFilter": {
                "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateFilter"
            }
        }
    ],
    "deploymentSettings": {
        "monitoring": null,
        "contentApplicability": null,
        "userExperience": null,
        "expedite": null,
        "schedule": {
            "startDateTime": "String (timestamp)",
            "gradualRollout": {
                "@odata.type": "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
                "durationBetweenOffers": "P1D",
                "devicesPerOffer": 0
            }
        }
    }
}
```
