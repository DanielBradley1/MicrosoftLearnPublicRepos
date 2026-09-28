<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-labelsroot-post-retentionlabel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create retentionLabel

Namespace: microsoft.graph.security

Create a new [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object.

To create a [disposition review stage](https://learn.microsoft.com/en-us/graph/api/resources/security-dispositionreviewstage?view=graph-rest-1.0), include the **actionAfterRetentionPeriod** property in the request body with one of the possible values specified.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RecordsManagement.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /security/labels/retentionLabels
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object.

Specify the following properties when you create a **retentionLabel**.

| Property | Type | Description |
| :--- | :--- | :--- |
| actionAfterRetentionPeriod | microsoft.graph.security.actionAfterRetentionPeriod | Specifies the action to take on a document with this label applied during the retention period. The possible values are: `none`, `delete`, `startDispositionReview`, `unknownFutureValue`. |
| behaviorDuringRetentionPeriod | microsoft.graph.security.behaviorDuringRetentionPeriod | Specifies how the behavior of a document with this label should be during the retention period. The possible values are: `doNotRetain`, `retain`, `retainAsRecord`, `retainAsRegulatoryRecord`, `unknownFutureValue`. |
| descriptionForAdmins | String | Provides label information for the admin. Optional. |
| descriptionForUsers | String | Provides the label information for the user. Optional. |
| displayName | String | Unique string that defines a label name. |
| dispositionReviewStages | [microsoft.graph.security.dispositionReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/security-dispositionreviewstage?view=graph-rest-1.0) collection | Review stages during which reviewers are notified to determine whether a document must be deleted or retained. |
| retentionDuration | [microsoft.graph.security.retentionDuration](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionduration?view=graph-rest-1.0) | Specifies the number of days to retain the content. |
| retentionTrigger | microsoft.graph.security.retentionTrigger | Specifies whether the retention duration is calculated from the content creation date, labeled date, or last modification date. The possible values are: `dateLabeled`, `dateCreated`, `dateModified`, `dateOfEvent`, `unknownFutureValue`. |
| defaultRecordBehavior | microsoft.graph.security.defaultRecordBehavior | Specifies the locked or unlocked state of a record label when it's created. The possible values are: `startLocked`, `startUnlocked`, `unknownFutureValue`. |
| labelToBeApplied | String | Specifies the replacement label to be applied automatically after the retention period of the current label ends. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.security.retentionLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-retentionlabel?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/security/labels/retentionLabels
Content-Type: application/json
Content-length: 555

{
  "@odata.type": "#microsoft.graph.security.retentionLabel",
  "displayName": "Retention Schedule 10005",
  "behaviorDuringRetentionPeriod": "retain",
  "actionAfterRetentionPeriod": "startDispositionReview",
  "retentionTrigger": "dateOfEvent",
  "retentionEventType@odata.bind": "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes('e095f4fc-b966-4c40-94de-fb8a383658e4')",
  "retentionDuration": {
    "@odata.type": "microsoft.graph.security.retentionDurationInDays",
    "days": 2555
  },
   "dispositionReviewStages": [
    {
      "stageNumber" : 1,
      "name": "Stage1",
      "reviewersEmailAddresses ": [
        "Admin@contoso.onmicrosoft.com"
      ]
    }
  ],
  "descriptionForAdmins": "retain for 7 years",
  "descriptionForUsers": "retain for 7 years",
  "descriptors": {
    "authorityTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/authorities('fie3f4fc-b966-4c40-94de-fb8a383658e4')",
    "categoryTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/categories('0bjk8-b966-4c40-94de-fb8a383658e4')",
    "citationTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/citations('0e23f4fc-b966-4c40-94de-fb8a383658e4')",
    "departmentTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/departments('p99ef4fc-b966-4c40-94de-fb8a383658e4')",
    "filePlanReferenceTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/filePlanReferences('e095f4fc-b966-4c40-94de-fb8a383658e4')"
  },
  "defaultRecordBehavior":"startLocked",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models.Security;

var requestBody = new RetentionLabel
{
	OdataType = "#microsoft.graph.security.retentionLabel",
	DisplayName = "Retention Schedule 10005",
	BehaviorDuringRetentionPeriod = BehaviorDuringRetentionPeriod.Retain,
	ActionAfterRetentionPeriod = ActionAfterRetentionPeriod.StartDispositionReview,
	RetentionTrigger = RetentionTrigger.DateOfEvent,
	RetentionDuration = new RetentionDurationInDays
	{
		OdataType = "microsoft.graph.security.retentionDurationInDays",
		Days = 2555,
	},
	DispositionReviewStages = new List<DispositionReviewStage>
	{
		new DispositionReviewStage
		{
			StageNumber = 1,
			Name = "Stage1",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"reviewersEmailAddresses " , new List<string>
					{
						"Admin@contoso.onmicrosoft.com",
					}
				},
			},
		},
	},
	DescriptionForAdmins = "retain for 7 years",
	DescriptionForUsers = "retain for 7 years",
	Descriptors = new FilePlanDescriptor
	{
		AdditionalData = new Dictionary<string, object>
		{
			{
				"authorityTemplate@odata.bind" , "https://graph.microsoft.com/v1.0/security/labels/authorities('fie3f4fc-b966-4c40-94de-fb8a383658e4')"
			},
			{
				"categoryTemplate@odata.bind" , "https://graph.microsoft.com/v1.0/security/labels/categories('0bjk8-b966-4c40-94de-fb8a383658e4')"
			},
			{
				"citationTemplate@odata.bind" , "https://graph.microsoft.com/v1.0/security/labels/citations('0e23f4fc-b966-4c40-94de-fb8a383658e4')"
			},
			{
				"departmentTemplate@odata.bind" , "https://graph.microsoft.com/v1.0/security/labels/departments('p99ef4fc-b966-4c40-94de-fb8a383658e4')"
			},
			{
				"filePlanReferenceTemplate@odata.bind" , "https://graph.microsoft.com/v1.0/security/labels/filePlanReferences('e095f4fc-b966-4c40-94de-fb8a383658e4')"
			},
		},
	},
	DefaultRecordBehavior = DefaultRecordBehavior.StartLocked,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"retentionEventType@odata.bind" , "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes('e095f4fc-b966-4c40-94de-fb8a383658e4')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Security.Labels.RetentionLabels.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphmodelssecurity.NewRetentionLabel()
displayName := "Retention Schedule 10005"
requestBody.SetDisplayName(&displayName) 
behaviorDuringRetentionPeriod := graphmodels.RETAIN_BEHAVIORDURINGRETENTIONPERIOD 
requestBody.SetBehaviorDuringRetentionPeriod(&behaviorDuringRetentionPeriod) 
actionAfterRetentionPeriod := graphmodels.STARTDISPOSITIONREVIEW_ACTIONAFTERRETENTIONPERIOD 
requestBody.SetActionAfterRetentionPeriod(&actionAfterRetentionPeriod) 
retentionTrigger := graphmodels.DATEOFEVENT_RETENTIONTRIGGER 
requestBody.SetRetentionTrigger(&retentionTrigger) 
retentionDuration := graphmodelssecurity.NewRetentionDurationInDays()
days := int32(2555)
retentionDuration.SetDays(&days) 
requestBody.SetRetentionDuration(retentionDuration)


dispositionReviewStage := graphmodelssecurity.NewDispositionReviewStage()
stageNumber := int32(1)
dispositionReviewStage.SetStageNumber(&stageNumber) 
name := "Stage1"
dispositionReviewStage.SetName(&name) 
additionalData := map[string]interface{}{
	reviewersEmailAddresses  := []string {
		"Admin@contoso.onmicrosoft.com",
	}
}
dispositionReviewStage.SetAdditionalData(additionalData)

dispositionReviewStages := []graphmodelssecurity.DispositionReviewStageable {
	dispositionReviewStage,
}
requestBody.SetDispositionReviewStages(dispositionReviewStages)
descriptionForAdmins := "retain for 7 years"
requestBody.SetDescriptionForAdmins(&descriptionForAdmins) 
descriptionForUsers := "retain for 7 years"
requestBody.SetDescriptionForUsers(&descriptionForUsers) 
descriptors := graphmodelssecurity.NewFilePlanDescriptor()
additionalData := map[string]interface{}{
	"authorityTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/authorities('fie3f4fc-b966-4c40-94de-fb8a383658e4')", 
	"categoryTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/categories('0bjk8-b966-4c40-94de-fb8a383658e4')", 
	"citationTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/citations('0e23f4fc-b966-4c40-94de-fb8a383658e4')", 
	"departmentTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/departments('p99ef4fc-b966-4c40-94de-fb8a383658e4')", 
	"filePlanReferenceTemplate@odata.bind" : "https://graph.microsoft.com/v1.0/security/labels/filePlanReferences('e095f4fc-b966-4c40-94de-fb8a383658e4')", 
}
descriptors.SetAdditionalData(additionalData)
requestBody.SetDescriptors(descriptors)
defaultRecordBehavior := graphmodels.STARTLOCKED_DEFAULTRECORDBEHAVIOR 
requestBody.SetDefaultRecordBehavior(&defaultRecordBehavior) 
additionalData := map[string]interface{}{
	"retentionEventType@odata.bind" : "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes('e095f4fc-b966-4c40-94de-fb8a383658e4')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
retentionLabels, err := graphClient.Security().Labels().RetentionLabels().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.models.security.RetentionLabel retentionLabel = new com.microsoft.graph.models.security.RetentionLabel();
retentionLabel.setOdataType("#microsoft.graph.security.retentionLabel");
retentionLabel.setDisplayName("Retention Schedule 10005");
retentionLabel.setBehaviorDuringRetentionPeriod(com.microsoft.graph.models.security.BehaviorDuringRetentionPeriod.Retain);
retentionLabel.setActionAfterRetentionPeriod(com.microsoft.graph.models.security.ActionAfterRetentionPeriod.StartDispositionReview);
retentionLabel.setRetentionTrigger(com.microsoft.graph.models.security.RetentionTrigger.DateOfEvent);
com.microsoft.graph.models.security.RetentionDurationInDays retentionDuration = new com.microsoft.graph.models.security.RetentionDurationInDays();
retentionDuration.setOdataType("microsoft.graph.security.retentionDurationInDays");
retentionDuration.setDays(2555);
retentionLabel.setRetentionDuration(retentionDuration);
LinkedList<com.microsoft.graph.models.security.DispositionReviewStage> dispositionReviewStages = new LinkedList<com.microsoft.graph.models.security.DispositionReviewStage>();
com.microsoft.graph.models.security.DispositionReviewStage dispositionReviewStage = new com.microsoft.graph.models.security.DispositionReviewStage();
dispositionReviewStage.setStageNumber(1);
dispositionReviewStage.setName("Stage1");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<String> reviewersEmailAddresses = new LinkedList<String>();
reviewersEmailAddresses.add("Admin@contoso.onmicrosoft.com");
additionalData.put("reviewersEmailAddresses ", reviewersEmailAddresses);
dispositionReviewStage.setAdditionalData(additionalData);
dispositionReviewStages.add(dispositionReviewStage);
retentionLabel.setDispositionReviewStages(dispositionReviewStages);
retentionLabel.setDescriptionForAdmins("retain for 7 years");
retentionLabel.setDescriptionForUsers("retain for 7 years");
com.microsoft.graph.models.security.FilePlanDescriptor descriptors = new com.microsoft.graph.models.security.FilePlanDescriptor();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("authorityTemplate@odata.bind", "https://graph.microsoft.com/v1.0/security/labels/authorities('fie3f4fc-b966-4c40-94de-fb8a383658e4')");
additionalData1.put("categoryTemplate@odata.bind", "https://graph.microsoft.com/v1.0/security/labels/categories('0bjk8-b966-4c40-94de-fb8a383658e4')");
additionalData1.put("citationTemplate@odata.bind", "https://graph.microsoft.com/v1.0/security/labels/citations('0e23f4fc-b966-4c40-94de-fb8a383658e4')");
additionalData1.put("departmentTemplate@odata.bind", "https://graph.microsoft.com/v1.0/security/labels/departments('p99ef4fc-b966-4c40-94de-fb8a383658e4')");
additionalData1.put("filePlanReferenceTemplate@odata.bind", "https://graph.microsoft.com/v1.0/security/labels/filePlanReferences('e095f4fc-b966-4c40-94de-fb8a383658e4')");
descriptors.setAdditionalData(additionalData1);
retentionLabel.setDescriptors(descriptors);
retentionLabel.setDefaultRecordBehavior(com.microsoft.graph.models.security.DefaultRecordBehavior.StartLocked);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("retentionEventType@odata.bind", "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes('e095f4fc-b966-4c40-94de-fb8a383658e4')");
retentionLabel.setAdditionalData(additionalData2);
com.microsoft.graph.models.security.RetentionLabel result = graphClient.security().labels().retentionLabels().post(retentionLabel);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const retentionLabel = {
  '@odata.type': '#microsoft.graph.security.retentionLabel',
  displayName: 'Retention Schedule 10005',
  behaviorDuringRetentionPeriod: 'retain',
  actionAfterRetentionPeriod: 'startDispositionReview',
  retentionTrigger: 'dateOfEvent',
  'retentionEventType@odata.bind': 'https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes(\'e095f4fc-b966-4c40-94de-fb8a383658e4\')',
  retentionDuration: {
    '@odata.type': 'microsoft.graph.security.retentionDurationInDays',
    days: 2555
  },
   dispositionReviewStages: [
    {
      stageNumber: 1,
      name: 'Stage1',
      'reviewersEmailAddresses ': [
        'Admin@contoso.onmicrosoft.com'
      ]
    }
  ],
  descriptionForAdmins: 'retain for 7 years',
  descriptionForUsers: 'retain for 7 years',
  descriptors: {
    'authorityTemplate@odata.bind': 'https://graph.microsoft.com/v1.0/security/labels/authorities(\'fie3f4fc-b966-4c40-94de-fb8a383658e4\')',
    'categoryTemplate@odata.bind': 'https://graph.microsoft.com/v1.0/security/labels/categories(\'0bjk8-b966-4c40-94de-fb8a383658e4\')',
    'citationTemplate@odata.bind': 'https://graph.microsoft.com/v1.0/security/labels/citations(\'0e23f4fc-b966-4c40-94de-fb8a383658e4\')',
    'departmentTemplate@odata.bind': 'https://graph.microsoft.com/v1.0/security/labels/departments(\'p99ef4fc-b966-4c40-94de-fb8a383658e4\')',
    'filePlanReferenceTemplate@odata.bind': 'https://graph.microsoft.com/v1.0/security/labels/filePlanReferences(\'e095f4fc-b966-4c40-94de-fb8a383658e4\')'
  },
  defaultRecordBehavior: 'startLocked',
};

await client.api('/security/labels/retentionLabels')
	.post(retentionLabel);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Security\RetentionLabel;
use Microsoft\Graph\Generated\Models\Security\BehaviorDuringRetentionPeriod;
use Microsoft\Graph\Generated\Models\Security\ActionAfterRetentionPeriod;
use Microsoft\Graph\Generated\Models\Security\RetentionTrigger;
use Microsoft\Graph\Generated\Models\Security\RetentionDurationInDays;
use Microsoft\Graph\Generated\Models\Security\DispositionReviewStage;
use Microsoft\Graph\Generated\Models\Security\FilePlanDescriptor;
use Microsoft\Graph\Generated\Models\Security\DefaultRecordBehavior;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RetentionLabel();
$requestBody->setOdataType('#microsoft.graph.security.retentionLabel');
$requestBody->setDisplayName('Retention Schedule 10005');
$requestBody->setBehaviorDuringRetentionPeriod(new BehaviorDuringRetentionPeriod('retain'));
$requestBody->setActionAfterRetentionPeriod(new ActionAfterRetentionPeriod('startDispositionReview'));
$requestBody->setRetentionTrigger(new RetentionTrigger('dateOfEvent'));
$retentionDuration = new RetentionDurationInDays();
$retentionDuration->setOdataType('microsoft.graph.security.retentionDurationInDays');
$retentionDuration->setDays(2555);
$requestBody->setRetentionDuration($retentionDuration);
$dispositionReviewStagesDispositionReviewStage1 = new DispositionReviewStage();
$dispositionReviewStagesDispositionReviewStage1->setStageNumber(1);
$dispositionReviewStagesDispositionReviewStage1->setName('Stage1');
$additionalData = [
	'reviewersEmailAddresses ' => [
'Admin@contoso.onmicrosoft.com', ],
];
$dispositionReviewStagesDispositionReviewStage1->setAdditionalData($additionalData);
$dispositionReviewStagesArray []= $dispositionReviewStagesDispositionReviewStage1;
$requestBody->setDispositionReviewStages($dispositionReviewStagesArray);

$requestBody->setDescriptionForAdmins('retain for 7 years');
$requestBody->setDescriptionForUsers('retain for 7 years');
$descriptors = new FilePlanDescriptor();
$additionalData = [
'authorityTemplate@odata.bind' => 'https://graph.microsoft.com/v1.0/security/labels/authorities(\'fie3f4fc-b966-4c40-94de-fb8a383658e4\')',
'categoryTemplate@odata.bind' => 'https://graph.microsoft.com/v1.0/security/labels/categories(\'0bjk8-b966-4c40-94de-fb8a383658e4\')',
'citationTemplate@odata.bind' => 'https://graph.microsoft.com/v1.0/security/labels/citations(\'0e23f4fc-b966-4c40-94de-fb8a383658e4\')',
'departmentTemplate@odata.bind' => 'https://graph.microsoft.com/v1.0/security/labels/departments(\'p99ef4fc-b966-4c40-94de-fb8a383658e4\')',
'filePlanReferenceTemplate@odata.bind' => 'https://graph.microsoft.com/v1.0/security/labels/filePlanReferences(\'e095f4fc-b966-4c40-94de-fb8a383658e4\')',
];
$descriptors->setAdditionalData($additionalData);
$requestBody->setDescriptors($descriptors);
$requestBody->setDefaultRecordBehavior(new DefaultRecordBehavior('startLocked'));
$additionalData = [
'retentionEventType@odata.bind' => 'https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes(\'e095f4fc-b966-4c40-94de-fb8a383658e4\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->security()->labels()->retentionLabels()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	"@odata.type" = "#microsoft.graph.security.retentionLabel"
	displayName = "Retention Schedule 10005"
	behaviorDuringRetentionPeriod = "retain"
	actionAfterRetentionPeriod = "startDispositionReview"
	retentionTrigger = "dateOfEvent"
	"retentionEventType@odata.bind" = "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes('e095f4fc-b966-4c40-94de-fb8a383658e4')"
	retentionDuration = @{
		"@odata.type" = "microsoft.graph.security.retentionDurationInDays"
		days = 
	}
	dispositionReviewStages = @(
		@{
			stageNumber = 1
			name = "Stage1"
			"reviewersEmailAddresses " = @(
			"Admin@contoso.onmicrosoft.com"
		)
	}
)
descriptionForAdmins = "retain for 7 years"
descriptionForUsers = "retain for 7 years"
descriptors = @{
	"authorityTemplate@odata.bind" = "https://graph.microsoft.com/v1.0/security/labels/authorities('fie3f4fc-b966-4c40-94de-fb8a383658e4')"
	"categoryTemplate@odata.bind" = "https://graph.microsoft.com/v1.0/security/labels/categories('0bjk8-b966-4c40-94de-fb8a383658e4')"
	"citationTemplate@odata.bind" = "https://graph.microsoft.com/v1.0/security/labels/citations('0e23f4fc-b966-4c40-94de-fb8a383658e4')"
	"departmentTemplate@odata.bind" = "https://graph.microsoft.com/v1.0/security/labels/departments('p99ef4fc-b966-4c40-94de-fb8a383658e4')"
	"filePlanReferenceTemplate@odata.bind" = "https://graph.microsoft.com/v1.0/security/labels/filePlanReferences('e095f4fc-b966-4c40-94de-fb8a383658e4')"
}
defaultRecordBehavior = "startLocked"
}

New-MgSecurityLabelRetentionLabel -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.security.retention_label import RetentionLabel
from msgraph.generated.models.behavior_during_retention_period import BehaviorDuringRetentionPeriod
from msgraph.generated.models.action_after_retention_period import ActionAfterRetentionPeriod
from msgraph.generated.models.retention_trigger import RetentionTrigger
from msgraph.generated.models.security.retention_duration_in_days import RetentionDurationInDays
from msgraph.generated.models.security.disposition_review_stage import DispositionReviewStage
from msgraph.generated.models.security.file_plan_descriptor import FilePlanDescriptor
from msgraph.generated.models.default_record_behavior import DefaultRecordBehavior
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RetentionLabel(
	odata_type = "#microsoft.graph.security.retentionLabel",
	display_name = "Retention Schedule 10005",
	behavior_during_retention_period = BehaviorDuringRetentionPeriod.Retain,
	action_after_retention_period = ActionAfterRetentionPeriod.StartDispositionReview,
	retention_trigger = RetentionTrigger.DateOfEvent,
	retention_duration = RetentionDurationInDays(
		odata_type = "microsoft.graph.security.retentionDurationInDays",
		days = 2555,
	),
	disposition_review_stages = [
		DispositionReviewStage(
			stage_number = 1,
			name = "Stage1",
			additional_data = {
					"reviewers_email_addresses " : [
						"Admin@contoso.onmicrosoft.com",
					],
			}
		),
	],
	description_for_admins = "retain for 7 years",
	description_for_users = "retain for 7 years",
	descriptors = FilePlanDescriptor(
		additional_data = {
				"authority_template@odata_bind" : "https://graph.microsoft.com/v1.0/security/labels/authorities('fie3f4fc-b966-4c40-94de-fb8a383658e4')",
				"category_template@odata_bind" : "https://graph.microsoft.com/v1.0/security/labels/categories('0bjk8-b966-4c40-94de-fb8a383658e4')",
				"citation_template@odata_bind" : "https://graph.microsoft.com/v1.0/security/labels/citations('0e23f4fc-b966-4c40-94de-fb8a383658e4')",
				"department_template@odata_bind" : "https://graph.microsoft.com/v1.0/security/labels/departments('p99ef4fc-b966-4c40-94de-fb8a383658e4')",
				"file_plan_reference_template@odata_bind" : "https://graph.microsoft.com/v1.0/security/labels/filePlanReferences('e095f4fc-b966-4c40-94de-fb8a383658e4')",
		}
	),
	default_record_behavior = DefaultRecordBehavior.StartLocked,
	additional_data = {
			"retention_event_type@odata_bind" : "https://graph.microsoft.com/v1.0/security/triggerTypes/retentionEventTypes('e095f4fc-b966-4c40-94de-fb8a383658e4')",
	}
)

result = await graph_client.security.labels.retention_labels.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.retentionLabel",
  "id": "64a99fb4-07be-0481-8746-44c15c0eef1f",
  "displayName": "Retention Schedule 10005",
  "behaviorDuringRetentionPeriod": "retain",
  "actionAfterRetentionPeriod": "startDispositionReview",
  "retentionTrigger": "dateOfEvent",
  "retentionDuration": {
    "@odata.type": "microsoft.graph.security.retentionDurationInDays",
    "days": 2555
  },
  "dispositionReviewStages": [
    {
     "stageNumber" : 1,
      "name": "Stage1",
      "reviewersEmailAddresses ": [
        "Admin@contoso.onmicrosoft.com"
      ]
    }
  ],
  "isInUse": true,
  "descriptionForAdmins": "retain for 7 years",
  "descriptionForUsers": "retain for 7 years",
  "defaultRecordBehavior":"startLocked",
  "createdBy": {
   "user": {
      "id": "9563a605-e827-4324-a5a9-09efddff1e90",
      "displayName": "Admin"
    }
  },
  "createdDateTime": "2021-08-23T16:43:55Z",
  "labelToBeApplied": " ",
  "defaultRecordBehavior": "startLocked",
  "descriptors": {
    "authority": {
      "displayName": "Business"
    },
    "category": {
      "displayName": "Accounts Payable",
    },
    "citation": {
      "displayName" : "Contoso Company Policy",
      "citationUrl": "www.citationUrl.com",
      "citationJurisdiction": "Contoso"
    },
    "department": {
      "displayName" : "Finance"
    },
    "filePlanReference": {
      "displayName" : "FIN 01-02-001"
    }
  }
}
```
