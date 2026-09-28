<!-- Source: https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-deployments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Create deployment

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) object.

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
POST /admin/windows/updates/deployments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) object.

The following table lists the properties that are required when you create the [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| audience | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) | Specifies the audience to target. |
| content | [microsoft.graph.windowsUpdates.deployableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployablecontent?view=graph-rest-beta) | Specifies what content to deploy. Deployable content should be provided as one of the following derived types: [catalogContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogcontent?view=graph-rest-beta). |

## Response

If successful, this method returns a `201 Created` response code and a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) object in the response body.

## Example

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
POST https://graph.microsoft.com/beta/admin/windows/updates/deployments
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.windowsUpdates.deployment",
    "content": {
        "@odata.type": "#microsoft.graph.windowsUpdates.catalogContent",
        "catalogEntry": {
            "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry",
            "id": "f341705b-0b15-4ce3-aaf2-6a1681d78606"
        }
    },
    "settings": {
        "@odata.type": "microsoft.graph.windowsUpdates.deploymentSettings",
        "schedule": {
            "gradualRollout": {
                "@odata.type": "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
                "durationBetweenOffers": "P7D",
                "devicesPerOffer": 100
            }
        },
        "monitoring": {
            "monitoringRules": [
                {
                    "signal": "rollback",
                    "threshold": 5,
                    "action": "pauseDeployment"
                }
            ]
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.WindowsUpdates;

var requestBody = new Deployment
{
	OdataType = "#microsoft.graph.windowsUpdates.deployment",
	Content = new CatalogContent
	{
		OdataType = "#microsoft.graph.windowsUpdates.catalogContent",
		CatalogEntry = new FeatureUpdateCatalogEntry
		{
			OdataType = "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry",
			Id = "f341705b-0b15-4ce3-aaf2-6a1681d78606",
		},
	},
	Settings = new DeploymentSettings
	{
		OdataType = "microsoft.graph.windowsUpdates.deploymentSettings",
		Schedule = new ScheduleSettings
		{
			GradualRollout = new RateDrivenRolloutSettings
			{
				OdataType = "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
				DurationBetweenOffers = TimeSpan.Parse("P7D"),
				DevicesPerOffer = 100,
			},
		},
		Monitoring = new MonitoringSettings
		{
			MonitoringRules = new List<MonitoringRule>
			{
				new MonitoringRule
				{
					Signal = MonitoringSignal.Rollback,
					Threshold = 5,
					Action = MonitoringAction.PauseDeployment,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Windows.Updates.Deployments.PostAsync(requestBody);
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

requestBody := graphmodelswindowsupdates.NewDeployment()
content := graphmodelswindowsupdates.NewCatalogContent()
catalogEntry := graphmodelswindowsupdates.NewFeatureUpdateCatalogEntry()
id := "f341705b-0b15-4ce3-aaf2-6a1681d78606"
catalogEntry.SetId(&id) 
content.SetCatalogEntry(catalogEntry)
requestBody.SetContent(content)
settings := graphmodelswindowsupdates.NewDeploymentSettings()
schedule := graphmodelswindowsupdates.NewScheduleSettings()
gradualRollout := graphmodelswindowsupdates.NewRateDrivenRolloutSettings()
durationBetweenOffers , err := abstractions.ParseISODuration("P7D")
gradualRollout.SetDurationBetweenOffers(&durationBetweenOffers) 
devicesPerOffer := int32(100)
gradualRollout.SetDevicesPerOffer(&devicesPerOffer) 
schedule.SetGradualRollout(gradualRollout)
settings.SetSchedule(schedule)
monitoring := graphmodelswindowsupdates.NewMonitoringSettings()


monitoringRule := graphmodelswindowsupdates.NewMonitoringRule()
signal := graphmodels.ROLLBACK_MONITORINGSIGNAL 
monitoringRule.SetSignal(&signal) 
threshold := int32(5)
monitoringRule.SetThreshold(&threshold) 
action := graphmodels.PAUSEDEPLOYMENT_MONITORINGACTION 
monitoringRule.SetAction(&action) 

monitoringRules := []graphmodelswindowsupdates.MonitoringRuleable {
	monitoringRule,
}
monitoring.SetMonitoringRules(monitoringRules)
settings.SetMonitoring(monitoring)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
deployments, err := graphClient.Admin().Windows().Updates().Deployments().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.windowsupdates.Deployment deployment = new com.microsoft.graph.beta.models.windowsupdates.Deployment();
deployment.setOdataType("#microsoft.graph.windowsUpdates.deployment");
com.microsoft.graph.beta.models.windowsupdates.CatalogContent content = new com.microsoft.graph.beta.models.windowsupdates.CatalogContent();
content.setOdataType("#microsoft.graph.windowsUpdates.catalogContent");
com.microsoft.graph.beta.models.windowsupdates.FeatureUpdateCatalogEntry catalogEntry = new com.microsoft.graph.beta.models.windowsupdates.FeatureUpdateCatalogEntry();
catalogEntry.setOdataType("#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry");
catalogEntry.setId("f341705b-0b15-4ce3-aaf2-6a1681d78606");
content.setCatalogEntry(catalogEntry);
deployment.setContent(content);
com.microsoft.graph.beta.models.windowsupdates.DeploymentSettings settings = new com.microsoft.graph.beta.models.windowsupdates.DeploymentSettings();
settings.setOdataType("microsoft.graph.windowsUpdates.deploymentSettings");
com.microsoft.graph.beta.models.windowsupdates.ScheduleSettings schedule = new com.microsoft.graph.beta.models.windowsupdates.ScheduleSettings();
com.microsoft.graph.beta.models.windowsupdates.RateDrivenRolloutSettings gradualRollout = new com.microsoft.graph.beta.models.windowsupdates.RateDrivenRolloutSettings();
gradualRollout.setOdataType("#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings");
PeriodAndDuration durationBetweenOffers = PeriodAndDuration.ofDuration(Duration.parse("P7D"));
gradualRollout.setDurationBetweenOffers(durationBetweenOffers);
gradualRollout.setDevicesPerOffer(100);
schedule.setGradualRollout(gradualRollout);
settings.setSchedule(schedule);
com.microsoft.graph.beta.models.windowsupdates.MonitoringSettings monitoring = new com.microsoft.graph.beta.models.windowsupdates.MonitoringSettings();
LinkedList<com.microsoft.graph.beta.models.windowsupdates.MonitoringRule> monitoringRules = new LinkedList<com.microsoft.graph.beta.models.windowsupdates.MonitoringRule>();
com.microsoft.graph.beta.models.windowsupdates.MonitoringRule monitoringRule = new com.microsoft.graph.beta.models.windowsupdates.MonitoringRule();
monitoringRule.setSignal(com.microsoft.graph.beta.models.windowsupdates.MonitoringSignal.Rollback);
monitoringRule.setThreshold(5);
monitoringRule.setAction(com.microsoft.graph.beta.models.windowsupdates.MonitoringAction.PauseDeployment);
monitoringRules.add(monitoringRule);
monitoring.setMonitoringRules(monitoringRules);
settings.setMonitoring(monitoring);
deployment.setSettings(settings);
com.microsoft.graph.models.windowsupdates.Deployment result = graphClient.admin().windows().updates().deployments().post(deployment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const deployment = {
    '@odata.type': '#microsoft.graph.windowsUpdates.deployment',
    content: {
        '@odata.type': '#microsoft.graph.windowsUpdates.catalogContent',
        catalogEntry: {
            '@odata.type': '#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry',
            id: 'f341705b-0b15-4ce3-aaf2-6a1681d78606'
        }
    },
    settings: {
        '@odata.type': 'microsoft.graph.windowsUpdates.deploymentSettings',
        schedule: {
            gradualRollout: {
                '@odata.type': '#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings',
                durationBetweenOffers: 'P7D',
                devicesPerOffer: 100
            }
        },
        monitoring: {
            monitoringRules: [
                {
                    signal: 'rollback',
                    threshold: 5,
                    action: 'pauseDeployment'
                }
            ]
        }
    }
};

await client.api('/admin/windows/updates/deployments')
	.version('beta')
	.post(deployment);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\Deployment;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\CatalogContent;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\FeatureUpdateCatalogEntry;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\DeploymentSettings;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\ScheduleSettings;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\RateDrivenRolloutSettings;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\MonitoringSettings;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\MonitoringRule;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\MonitoringSignal;
use Microsoft\Graph\Beta\Generated\Models\WindowsUpdates\MonitoringAction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Deployment();
$requestBody->setOdataType('#microsoft.graph.windowsUpdates.deployment');
$content = new CatalogContent();
$content->setOdataType('#microsoft.graph.windowsUpdates.catalogContent');
$contentCatalogEntry = new FeatureUpdateCatalogEntry();
$contentCatalogEntry->setOdataType('#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry');
$contentCatalogEntry->setId('f341705b-0b15-4ce3-aaf2-6a1681d78606');
$content->setCatalogEntry($contentCatalogEntry);
$requestBody->setContent($content);
$settings = new DeploymentSettings();
$settings->setOdataType('microsoft.graph.windowsUpdates.deploymentSettings');
$settingsSchedule = new ScheduleSettings();
$settingsScheduleGradualRollout = new RateDrivenRolloutSettings();
$settingsScheduleGradualRollout->setOdataType('#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings');
$settingsScheduleGradualRollout->setDurationBetweenOffers(new \DateInterval('P7D'));
$settingsScheduleGradualRollout->setDevicesPerOffer(100);
$settingsSchedule->setGradualRollout($settingsScheduleGradualRollout);
$settings->setSchedule($settingsSchedule);
$settingsMonitoring = new MonitoringSettings();
$monitoringRulesMonitoringRule1 = new MonitoringRule();
$monitoringRulesMonitoringRule1->setSignal(new MonitoringSignal('rollback'));
$monitoringRulesMonitoringRule1->setThreshold(5);
$monitoringRulesMonitoringRule1->setAction(new MonitoringAction('pauseDeployment'));
$monitoringRulesArray []= $monitoringRulesMonitoringRule1;
$settingsMonitoring->setMonitoringRules($monitoringRulesArray);

$settings->setMonitoring($settingsMonitoring);
$requestBody->setSettings($settings);

$result = $graphServiceClient->admin()->windows()->updates()->deployments()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.WindowsUpdates

$params = @{
	"@odata.type" = "#microsoft.graph.windowsUpdates.deployment"
	content = @{
		"@odata.type" = "#microsoft.graph.windowsUpdates.catalogContent"
		catalogEntry = @{
			"@odata.type" = "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry"
			id = "f341705b-0b15-4ce3-aaf2-6a1681d78606"
		}
	}
	settings = @{
		"@odata.type" = "microsoft.graph.windowsUpdates.deploymentSettings"
		schedule = @{
			gradualRollout = @{
				"@odata.type" = "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings"
				durationBetweenOffers = "P7D"
				devicesPerOffer = 
			}
		}
		monitoring = @{
			monitoringRules = @(
				@{
					signal = "rollback"
					threshold = 5
					action = "pauseDeployment"
				}
			)
		}
	}
}

New-MgBetaWindowsUpdatesDeployment -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.windows_updates.deployment import Deployment
from msgraph_beta.generated.models.windows_updates.catalog_content import CatalogContent
from msgraph_beta.generated.models.windows_updates.feature_update_catalog_entry import FeatureUpdateCatalogEntry
from msgraph_beta.generated.models.windows_updates.deployment_settings import DeploymentSettings
from msgraph_beta.generated.models.windows_updates.schedule_settings import ScheduleSettings
from msgraph_beta.generated.models.windows_updates.rate_driven_rollout_settings import RateDrivenRolloutSettings
from msgraph_beta.generated.models.windows_updates.monitoring_settings import MonitoringSettings
from msgraph_beta.generated.models.windows_updates.monitoring_rule import MonitoringRule
from msgraph_beta.generated.models.monitoring_signal import MonitoringSignal
from msgraph_beta.generated.models.monitoring_action import MonitoringAction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Deployment(
	odata_type = "#microsoft.graph.windowsUpdates.deployment",
	content = CatalogContent(
		odata_type = "#microsoft.graph.windowsUpdates.catalogContent",
		catalog_entry = FeatureUpdateCatalogEntry(
			odata_type = "#microsoft.graph.windowsUpdates.featureUpdateCatalogEntry",
			id = "f341705b-0b15-4ce3-aaf2-6a1681d78606",
		),
	),
	settings = DeploymentSettings(
		odata_type = "microsoft.graph.windowsUpdates.deploymentSettings",
		schedule = ScheduleSettings(
			gradual_rollout = RateDrivenRolloutSettings(
				odata_type = "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
				duration_between_offers = "P7D",
				devices_per_offer = 100,
			),
		),
		monitoring = MonitoringSettings(
			monitoring_rules = [
				MonitoringRule(
					signal = MonitoringSignal.Rollback,
					threshold = 5,
					action = MonitoringAction.PauseDeployment,
				),
			],
		),
	),
)

result = await graph_client.admin.windows.updates.deployments.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.deployment",
  "id": "b5171742-1742-b517-4217-17b5421717b5",
  "createdDateTime": "2023-01-26T05:08:38.118213Z",
  "lastModifiedDateTime": "2023-01-26T05:08:38Z",
  "state": {
    "value": "offering",
    "reasons": [],
    "requestedValue": "none",
  },
  "content": {
    "@odata.type": "microsoft.graph.windowsUpdates.catalogContent",
  },
  "settings": {
    "@odata.type": "microsoft.graph.windowsUpdates.deploymentSettings",
    "schedule": {
      "gradualRollout": {
        "@odata.type": "#microsoft.graph.windowsUpdates.rateDrivenRolloutSettings",
        "durationBetweenOffers": "P1D",
        "devicesPerOffer": 1000
      }
    },
    "monitoring": {
      "monitoringRules": [
        {
          "@odata.type": "#microsoft.graph.windowsUpdates.monitoringRule",
          "signal": "rollback",
          "threshold": 5,
          "action": "pauseDeployment"
        }
      ]
    },
    "userExperience": null,
    "safeguard": null
  },
}
```
