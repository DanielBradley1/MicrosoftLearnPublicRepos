<!-- Source: https://learn.microsoft.com/en-us/graph/api/devicemanagement-alertrule-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# Create alertRule

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create an [alertRule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /deviceManagement/monitoring/alertRules
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
| alertRuleTemplate | microsoft.graph.deviceManagement.alertRuleTemplate | The rule template of the alert event. The possible values are: `cloudPcProvisionScenario`, `cloudPcImageUploadScenario`, `cloudPcOnPremiseNetworkConnectionCheckScenario`, `cloudPcInGracePeriodScenario`, `cloudPcFrontlineInsufficientLicensesScenario`, `cloudPcInaccessibleScenario`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `cloudPcInGracePeriodScenario`. |
| description | String | The rule description. |
| displayName | String | The display name of the rule. |
| enabled | Boolean | The status of the rule that indicates whether the rule is enabled or disabled. If `true`, the rule is enabled; otherwise, the rule is disabled. |
| isSystemRule | Boolean | A value that tells whether the rule is a system rule. If `true`, the rule is a system rule; otherwise, it's a custom-defined rule and can be edited. Only a few properties can be edited on built-in system rules. |
| notificationChannels | [microsoft.graph.deviceManagement.notificationChannel](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-notificationchannel?view=graph-rest-beta) collection | The notification channels of the rule selected by the user. |
| severity | microsoft.graph.deviceManagement.ruleSeverityType | The severity of the rule. The possible values are: `unknown`, `informational`, `warning`, `critical`, `unknownFutureValue`. |
| threshold | [microsoft.graph.deviceManagement.ruleThreshold](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-rulethreshold?view=graph-rest-beta) | The threshold of the rule. This property is deprecated. Use `conditions` instead. |
| conditions | [microsoft.graph.deviceManagement.ruleCondition](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-rulecondition?view=graph-rest-beta) collection | The conditions of the rule. Conditions determine when to send an alert. For example, you can set a condition so that an alert is sent when six or more Cloud PCs fail to provision. |

## Response

If successful, this method returns a `201 Created` response code and an [microsoft.graph.deviceManagement.alertRule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta) object in the response body.

## Example

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
POST https://graph.microsoft.com/beta/deviceManagement/monitoring/alertRules
Content-Type: application/json

{
  "id": "215c55cc-b1c9-4d36-a870-be5778101714",
  "displayName": "Azure network connection failure impacting Cloud PCs",
  "severity": "informational",
  "isSystemRule": true,
  "description": "Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs",
  "enabled": true,
  "alertRuleTemplate": "cloudPcOnPremiseNetworkConnectionCheckScenario",
  "threshold": {
      "aggregation": "count",
      "operator": "greaterOrEqual",
      "target": 90
  },
  "conditions": [
      {
        "relationshipType": "or",
        "conditionCategory": "azureNetworkConnectionCheckFailures",
        "aggregation": "count",
        "operator": "greaterOrEqual",
        "thresholdValue": "90"
      }
  ],
  "notificationChannels": [
      {
        "notificationChannelType": "portal",
        "notificationReceivers": []
      },
      {
        "notificationChannelType": "email",
        "notificationReceivers": [
            {
                "locale": "en-us",
                "contactInformation": "serena.davis@contoso.com"
            }
        ]
      }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models.DeviceManagement;

var requestBody = new AlertRule
{
	Id = "215c55cc-b1c9-4d36-a870-be5778101714",
	DisplayName = "Azure network connection failure impacting Cloud PCs",
	Severity = RuleSeverityType.Informational,
	IsSystemRule = true,
	Description = "Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs",
	Enabled = true,
	AlertRuleTemplate = AlertRuleTemplate.CloudPcOnPremiseNetworkConnectionCheckScenario,
	Threshold = new RuleThreshold
	{
		Aggregation = AggregationType.Count,
		Operator = OperatorType.GreaterOrEqual,
		Target = 90,
	},
	Conditions = new List<RuleCondition>
	{
		new RuleCondition
		{
			RelationshipType = RelationshipType.Or,
			ConditionCategory = ConditionCategory.AzureNetworkConnectionCheckFailures,
			Aggregation = AggregationType.Count,
			Operator = OperatorType.GreaterOrEqual,
			ThresholdValue = "90",
		},
	},
	NotificationChannels = new List<NotificationChannel>
	{
		new NotificationChannel
		{
			NotificationChannelType = NotificationChannelType.Portal,
			NotificationReceivers = new List<NotificationReceiver>
			{
			},
		},
		new NotificationChannel
		{
			NotificationChannelType = NotificationChannelType.Email,
			NotificationReceivers = new List<NotificationReceiver>
			{
				new NotificationReceiver
				{
					Locale = "en-us",
					ContactInformation = "serena.davis@contoso.com",
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.Monitoring.AlertRules.PostAsync(requestBody);
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
	  graphmodelsdevicemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/models/devicemanagement"
	  //other-imports
)

requestBody := graphmodelsdevicemanagement.NewAlertRule()
id := "215c55cc-b1c9-4d36-a870-be5778101714"
requestBody.SetId(&id) 
displayName := "Azure network connection failure impacting Cloud PCs"
requestBody.SetDisplayName(&displayName) 
severity := graphmodels.INFORMATIONAL_RULESEVERITYTYPE 
requestBody.SetSeverity(&severity) 
isSystemRule := true
requestBody.SetIsSystemRule(&isSystemRule) 
description := "Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs"
requestBody.SetDescription(&description) 
enabled := true
requestBody.SetEnabled(&enabled) 
alertRuleTemplate := graphmodels.CLOUDPCONPREMISENETWORKCONNECTIONCHECKSCENARIO_ALERTRULETEMPLATE 
requestBody.SetAlertRuleTemplate(&alertRuleTemplate) 
threshold := graphmodelsdevicemanagement.NewRuleThreshold()
aggregation := graphmodels.COUNT_AGGREGATIONTYPE 
threshold.SetAggregation(&aggregation) 
operator := graphmodels.GREATEROREQUAL_OPERATORTYPE 
threshold.SetOperator(&operator) 
target := int32(90)
threshold.SetTarget(&target) 
requestBody.SetThreshold(threshold)


ruleCondition := graphmodelsdevicemanagement.NewRuleCondition()
relationshipType := graphmodels.OR_RELATIONSHIPTYPE 
ruleCondition.SetRelationshipType(&relationshipType) 
conditionCategory := graphmodels.AZURENETWORKCONNECTIONCHECKFAILURES_CONDITIONCATEGORY 
ruleCondition.SetConditionCategory(&conditionCategory) 
aggregation := graphmodels.COUNT_AGGREGATIONTYPE 
ruleCondition.SetAggregation(&aggregation) 
operator := graphmodels.GREATEROREQUAL_OPERATORTYPE 
ruleCondition.SetOperator(&operator) 
thresholdValue := "90"
ruleCondition.SetThresholdValue(&thresholdValue) 

conditions := []graphmodelsdevicemanagement.RuleConditionable {
	ruleCondition,
}
requestBody.SetConditions(conditions)


notificationChannel := graphmodelsdevicemanagement.NewNotificationChannel()
notificationChannelType := graphmodels.PORTAL_NOTIFICATIONCHANNELTYPE 
notificationChannel.SetNotificationChannelType(&notificationChannelType) 
notificationReceivers := []graphmodelsdevicemanagement.NotificationReceiverable {

}
notificationChannel.SetNotificationReceivers(notificationReceivers)
notificationChannel1 := graphmodelsdevicemanagement.NewNotificationChannel()
notificationChannelType := graphmodels.EMAIL_NOTIFICATIONCHANNELTYPE 
notificationChannel1.SetNotificationChannelType(&notificationChannelType) 


notificationReceiver := graphmodelsdevicemanagement.NewNotificationReceiver()
locale := "en-us"
notificationReceiver.SetLocale(&locale) 
contactInformation := "serena.davis@contoso.com"
notificationReceiver.SetContactInformation(&contactInformation) 

notificationReceivers := []graphmodelsdevicemanagement.NotificationReceiverable {
	notificationReceiver,
}
notificationChannel1.SetNotificationReceivers(notificationReceivers)

notificationChannels := []graphmodelsdevicemanagement.NotificationChannelable {
	notificationChannel,
	notificationChannel1,
}
requestBody.SetNotificationChannels(notificationChannels)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
alertRules, err := graphClient.DeviceManagement().Monitoring().AlertRules().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.models.devicemanagement.AlertRule alertRule = new com.microsoft.graph.beta.models.devicemanagement.AlertRule();
alertRule.setId("215c55cc-b1c9-4d36-a870-be5778101714");
alertRule.setDisplayName("Azure network connection failure impacting Cloud PCs");
alertRule.setSeverity(com.microsoft.graph.beta.models.devicemanagement.RuleSeverityType.Informational);
alertRule.setIsSystemRule(true);
alertRule.setDescription("Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs");
alertRule.setEnabled(true);
alertRule.setAlertRuleTemplate(com.microsoft.graph.beta.models.devicemanagement.AlertRuleTemplate.CloudPcOnPremiseNetworkConnectionCheckScenario);
com.microsoft.graph.beta.models.devicemanagement.RuleThreshold threshold = new com.microsoft.graph.beta.models.devicemanagement.RuleThreshold();
threshold.setAggregation(com.microsoft.graph.beta.models.devicemanagement.AggregationType.Count);
threshold.setOperator(com.microsoft.graph.beta.models.devicemanagement.OperatorType.GreaterOrEqual);
threshold.setTarget(90);
alertRule.setThreshold(threshold);
LinkedList<com.microsoft.graph.beta.models.devicemanagement.RuleCondition> conditions = new LinkedList<com.microsoft.graph.beta.models.devicemanagement.RuleCondition>();
com.microsoft.graph.beta.models.devicemanagement.RuleCondition ruleCondition = new com.microsoft.graph.beta.models.devicemanagement.RuleCondition();
ruleCondition.setRelationshipType(com.microsoft.graph.beta.models.devicemanagement.RelationshipType.Or);
ruleCondition.setConditionCategory(com.microsoft.graph.beta.models.devicemanagement.ConditionCategory.AzureNetworkConnectionCheckFailures);
ruleCondition.setAggregation(com.microsoft.graph.beta.models.devicemanagement.AggregationType.Count);
ruleCondition.setOperator(com.microsoft.graph.beta.models.devicemanagement.OperatorType.GreaterOrEqual);
ruleCondition.setThresholdValue("90");
conditions.add(ruleCondition);
alertRule.setConditions(conditions);
LinkedList<com.microsoft.graph.beta.models.devicemanagement.NotificationChannel> notificationChannels = new LinkedList<com.microsoft.graph.beta.models.devicemanagement.NotificationChannel>();
com.microsoft.graph.beta.models.devicemanagement.NotificationChannel notificationChannel = new com.microsoft.graph.beta.models.devicemanagement.NotificationChannel();
notificationChannel.setNotificationChannelType(com.microsoft.graph.beta.models.devicemanagement.NotificationChannelType.Portal);
LinkedList<com.microsoft.graph.beta.models.devicemanagement.NotificationReceiver> notificationReceivers = new LinkedList<com.microsoft.graph.beta.models.devicemanagement.NotificationReceiver>();
notificationChannel.setNotificationReceivers(notificationReceivers);
notificationChannels.add(notificationChannel);
com.microsoft.graph.beta.models.devicemanagement.NotificationChannel notificationChannel1 = new com.microsoft.graph.beta.models.devicemanagement.NotificationChannel();
notificationChannel1.setNotificationChannelType(com.microsoft.graph.beta.models.devicemanagement.NotificationChannelType.Email);
LinkedList<com.microsoft.graph.beta.models.devicemanagement.NotificationReceiver> notificationReceivers1 = new LinkedList<com.microsoft.graph.beta.models.devicemanagement.NotificationReceiver>();
com.microsoft.graph.beta.models.devicemanagement.NotificationReceiver notificationReceiver = new com.microsoft.graph.beta.models.devicemanagement.NotificationReceiver();
notificationReceiver.setLocale("en-us");
notificationReceiver.setContactInformation("serena.davis@contoso.com");
notificationReceivers1.add(notificationReceiver);
notificationChannel1.setNotificationReceivers(notificationReceivers1);
notificationChannels.add(notificationChannel1);
alertRule.setNotificationChannels(notificationChannels);
com.microsoft.graph.models.devicemanagement.AlertRule result = graphClient.deviceManagement().monitoring().alertRules().post(alertRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const alertRule = {
  id: '215c55cc-b1c9-4d36-a870-be5778101714',
  displayName: 'Azure network connection failure impacting Cloud PCs',
  severity: 'informational',
  isSystemRule: true,
  description: 'Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs',
  enabled: true,
  alertRuleTemplate: 'cloudPcOnPremiseNetworkConnectionCheckScenario',
  threshold: {
      aggregation: 'count',
      operator: 'greaterOrEqual',
      target: 90
  },
  conditions: [
      {
        relationshipType: 'or',
        conditionCategory: 'azureNetworkConnectionCheckFailures',
        aggregation: 'count',
        operator: 'greaterOrEqual',
        thresholdValue: '90'
      }
  ],
  notificationChannels: [
      {
        notificationChannelType: 'portal',
        notificationReceivers: []
      },
      {
        notificationChannelType: 'email',
        notificationReceivers: [
            {
                locale: 'en-us',
                contactInformation: 'serena.davis@contoso.com'
            }
        ]
      }
  ]
};

await client.api('/deviceManagement/monitoring/alertRules')
	.version('beta')
	.post(alertRule);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\AlertRule;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\RuleSeverityType;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\AlertRuleTemplate;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\RuleThreshold;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\AggregationType;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\OperatorType;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\RuleCondition;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\RelationshipType;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\ConditionCategory;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\NotificationChannel;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\NotificationChannelType;
use Microsoft\Graph\Beta\Generated\Models\DeviceManagement\NotificationReceiver;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AlertRule();
$requestBody->setId('215c55cc-b1c9-4d36-a870-be5778101714');
$requestBody->setDisplayName('Azure network connection failure impacting Cloud PCs');
$requestBody->setSeverity(new RuleSeverityType('informational'));
$requestBody->setIsSystemRule(true);
$requestBody->setDescription('Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs');
$requestBody->setEnabled(true);
$requestBody->setAlertRuleTemplate(new AlertRuleTemplate('cloudPcOnPremiseNetworkConnectionCheckScenario'));
$threshold = new RuleThreshold();
$threshold->setAggregation(new AggregationType('count'));
$threshold->setOperator(new OperatorType('greaterOrEqual'));
$threshold->setTarget(90);
$requestBody->setThreshold($threshold);
$conditionsRuleCondition1 = new RuleCondition();
$conditionsRuleCondition1->setRelationshipType(new RelationshipType('or'));
$conditionsRuleCondition1->setConditionCategory(new ConditionCategory('azureNetworkConnectionCheckFailures'));
$conditionsRuleCondition1->setAggregation(new AggregationType('count'));
$conditionsRuleCondition1->setOperator(new OperatorType('greaterOrEqual'));
$conditionsRuleCondition1->setThresholdValue('90');
$conditionsArray []= $conditionsRuleCondition1;
$requestBody->setConditions($conditionsArray);

$notificationChannelsNotificationChannel1 = new NotificationChannel();
$notificationChannelsNotificationChannel1->setNotificationChannelType(new NotificationChannelType('portal'));
$notificationChannelsNotificationChannel1->setNotificationReceivers([]);
$notificationChannelsArray []= $notificationChannelsNotificationChannel1;
$notificationChannelsNotificationChannel2 = new NotificationChannel();
$notificationChannelsNotificationChannel2->setNotificationChannelType(new NotificationChannelType('email'));
$notificationReceiversNotificationReceiver1 = new NotificationReceiver();
$notificationReceiversNotificationReceiver1->setLocale('en-us');
$notificationReceiversNotificationReceiver1->setContactInformation('serena.davis@contoso.com');
$notificationReceiversArray []= $notificationReceiversNotificationReceiver1;
$notificationChannelsNotificationChannel2->setNotificationReceivers($notificationReceiversArray);

$notificationChannelsArray []= $notificationChannelsNotificationChannel2;
$requestBody->setNotificationChannels($notificationChannelsArray);


$result = $graphServiceClient->deviceManagement()->monitoring()->alertRules()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.DeviceManagement

$params = @{
	id = "215c55cc-b1c9-4d36-a870-be5778101714"
	displayName = "Azure network connection failure impacting Cloud PCs"
	severity = "informational"
	isSystemRule = $true
	description = "Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs"
	enabled = $true
	alertRuleTemplate = "cloudPcOnPremiseNetworkConnectionCheckScenario"
	threshold = @{
		aggregation = "count"
		operator = "greaterOrEqual"
		target = 90
	}
	conditions = @(
		@{
			relationshipType = "or"
			conditionCategory = "azureNetworkConnectionCheckFailures"
			aggregation = "count"
			operator = "greaterOrEqual"
			thresholdValue = "90"
		}
	)
	notificationChannels = @(
		@{
			notificationChannelType = "portal"
			notificationReceivers = @(
			)
		}
		@{
			notificationChannelType = "email"
			notificationReceivers = @(
				@{
					locale = "en-us"
					contactInformation = "serena.davis@contoso.com"
				}
			)
		}
	)
}

New-MgBetaDeviceManagementMonitoringAlertRule -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.device_management.alert_rule import AlertRule
from msgraph_beta.generated.models.rule_severity_type import RuleSeverityType
from msgraph_beta.generated.models.alert_rule_template import AlertRuleTemplate
from msgraph_beta.generated.models.device_management.rule_threshold import RuleThreshold
from msgraph_beta.generated.models.aggregation_type import AggregationType
from msgraph_beta.generated.models.operator_type import OperatorType
from msgraph_beta.generated.models.device_management.rule_condition import RuleCondition
from msgraph_beta.generated.models.relationship_type import RelationshipType
from msgraph_beta.generated.models.condition_category import ConditionCategory
from msgraph_beta.generated.models.device_management.notification_channel import NotificationChannel
from msgraph_beta.generated.models.notification_channel_type import NotificationChannelType
from msgraph_beta.generated.models.device_management.notification_receiver import NotificationReceiver
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AlertRule(
	id = "215c55cc-b1c9-4d36-a870-be5778101714",
	display_name = "Azure network connection failure impacting Cloud PCs",
	severity = RuleSeverityType.Informational,
	is_system_rule = True,
	description = "Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs",
	enabled = True,
	alert_rule_template = AlertRuleTemplate.CloudPcOnPremiseNetworkConnectionCheckScenario,
	threshold = RuleThreshold(
		aggregation = AggregationType.Count,
		operator = OperatorType.GreaterOrEqual,
		target = 90,
	),
	conditions = [
		RuleCondition(
			relationship_type = RelationshipType.Or,
			condition_category = ConditionCategory.AzureNetworkConnectionCheckFailures,
			aggregation = AggregationType.Count,
			operator = OperatorType.GreaterOrEqual,
			threshold_value = "90",
		),
	],
	notification_channels = [
		NotificationChannel(
			notification_channel_type = NotificationChannelType.Portal,
			notification_receivers = [
			],
		),
		NotificationChannel(
			notification_channel_type = NotificationChannelType.Email,
			notification_receivers = [
				NotificationReceiver(
					locale = "en-us",
					contact_information = "serena.davis@contoso.com",
				),
			],
		),
	],
)

result = await graph_client.device_management.monitoring.alert_rules.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#deviceManagement/monitoring/alertRules/$entity",
  "id": "215c55cc-b1c9-4d36-a870-be5778101714",
  "displayName": "Azure network connection failure impacting Cloud PCs",
  "severity": "informational",
  "isSystemRule": true,
  "description": "Azure network connection checks have failed and is potentially impacting existing Cloud PCs and blocking the provisioning of new Cloud PCs",
  "enabled": true,
  "alertRuleTemplate": "cloudPcOnPremiseNetworkConnectionCheckScenario",
  "threshold": {
      "aggregation": "count",
      "operator": "greaterOrEqual",
      "target": 90
  },
  "conditions": [
      {
        "relationshipType": "or",
        "conditionCategory": "azureNetworkConnectionCheckFailures",
        "aggregation": "count",
        "operator": "greaterOrEqual",
        "thresholdValue": "90"
      }
  ],
  "notificationChannels": [
      {
        "notificationChannelType": "portal",
        "notificationReceivers": []
      },
      {
        "notificationChannelType": "email",
        "notificationReceivers": [
            {
                "locale": "en-us",
                "contactInformation": "serena.davis@contoso.com"
            }
        ]
      }
  ]
}
```
