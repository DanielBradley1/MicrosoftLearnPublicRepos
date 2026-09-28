<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreview-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# Create accessReview \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

In the Microsoft Entra [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta) feature, create a new [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) object.

Before making this request, the caller must have previously [retrieved the list of business flow templates](https://learn.microsoft.com/en-us/graph/api/businessflowtemplate-list?view=graph-rest-beta), to have the value of **businessFlowTemplateId** to include in the request.

After making this request, the caller should [create a programControl](https://learn.microsoft.com/en-us/graph/api/programcontrol-create?view=graph-rest-beta), to link the access review to a program.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AccessReview.ReadWrite.Membership | AccessReview.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AccessReview.ReadWrite.Membership | Not available. |

The caller should also have ProgramControl.ReadWrite.All permission, so that after creating an access review, the caller can create a [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta). In addition, the signed in user must also be in a directory role that permits them to create an access review. For more details, see the role and permission requirements for [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta).

## HTTP request

```http
POST /accessReviews
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) object.

The following table shows the properties that are required when you create an accessReview.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The access review name. |
| startDateTime | DateTimeOffset | The DateTime when the review is scheduled to be start. This must be a date in the future. |
| endDateTime | DateTimeOffset | The DateTime when the review is scheduled to end. This must be at least one day later than the start date. |
| description | String | The description, to show to the reviewers. |
| businessFlowTemplateId | String | The business flow template identifier, obtained from a [businessFlowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/businessflowtemplate?view=graph-rest-beta). |
| reviewerType | String | The relationship type of reviewer to the access rights of the reviewed object, one of `self`, `delegated`, or `entityOwners`. |
| reviewedEntity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The object for which an access review is created, such as the membership of a group or the assignments of users to an application. |

If the **reviewerType** has the value `delegated`, then the caller must also include the **reviewers** property, with a collection of [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) objects representing the reviewers.

If your app is calling this API without a signed-in user, then the caller must also include the **createdBy** property, the value for which is a [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) of the user who will be identified as the creator of the review.

In addition, the caller can include **settings**, to create a recurring review series or to change from the default review behavior. In particular, to create a recurring review, the caller must include the [accessReviewRecurrenceSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewrecurrencesettings?view=graph-rest-beta) within the access review settings,

## Response

If successful, this method returns a `201 Created` response code and an [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) object in the response body.

## Example

This is an example of creating a one-time \(not recurring\) access review, explicitly specifying two users as the reviewers.

### Request

In the request body, supply a JSON representation of the [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) object.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/accessReviews
Content-type: application/json

{
    "displayName":"TestReview",
    "startDateTime":"2017-02-10T00:35:53.214Z",
    "endDateTime":"2017-03-12T00:35:53.214Z",
    "reviewedEntity": {
        "id": "99025615-a0b1-47ec-9117-35377b10998b"
    },
    "reviewerType" : "delegated",
    "businessFlowTemplateId": "6e4f3d20-c5c3-407f-9695-8460952bcc68",
    "description":"Sample description",
    "reviewers":
    [
        {
            "id":"f260246a-09b1-4fd5-8d18-daed736071ec"
        },
        {
            "id":"5a4e184c-4ee5-4883-96e9-b371f8da88e3"
        }
    ],
    "settings":
    {
        "mailNotificationsEnabled": true,
        "remindersEnabled": true,
        "justificationRequiredOnApproval":true,
        "autoReviewEnabled":false,
        "activityDurationInDays":30,
        "autoApplyReviewResultsEnabled":false,
        "accessRecommendationsEnabled":false,
        "recurrenceSettings":{
            "recurrenceType":"onetime",
            "recurrenceEndType":"endBy",
            "durationInDays":0,
            "recurrenceCount":0
        },
        "autoReviewSettings":{
            "notReviewedResult":"Deny"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new AccessReview
{
	DisplayName = "TestReview",
	StartDateTime = DateTimeOffset.Parse("2017-02-10T00:35:53.214Z"),
	EndDateTime = DateTimeOffset.Parse("2017-03-12T00:35:53.214Z"),
	ReviewedEntity = new Identity
	{
		Id = "99025615-a0b1-47ec-9117-35377b10998b",
	},
	ReviewerType = "delegated",
	BusinessFlowTemplateId = "6e4f3d20-c5c3-407f-9695-8460952bcc68",
	Description = "Sample description",
	Reviewers = new List<AccessReviewReviewer>
	{
		new AccessReviewReviewer
		{
			Id = "f260246a-09b1-4fd5-8d18-daed736071ec",
		},
		new AccessReviewReviewer
		{
			Id = "5a4e184c-4ee5-4883-96e9-b371f8da88e3",
		},
	},
	Settings = new AccessReviewSettings
	{
		MailNotificationsEnabled = true,
		RemindersEnabled = true,
		JustificationRequiredOnApproval = true,
		AutoReviewEnabled = false,
		ActivityDurationInDays = 30,
		AutoApplyReviewResultsEnabled = false,
		AccessRecommendationsEnabled = false,
		RecurrenceSettings = new AccessReviewRecurrenceSettings
		{
			RecurrenceType = "onetime",
			RecurrenceEndType = "endBy",
			DurationInDays = 0,
			RecurrenceCount = 0,
		},
		AutoReviewSettings = new AutoReviewSettings
		{
			NotReviewedResult = "Deny",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.AccessReviews.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessReview()
displayName := "TestReview"
requestBody.SetDisplayName(&displayName) 
startDateTime , err := time.Parse(time.RFC3339, "2017-02-10T00:35:53.214Z")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2017-03-12T00:35:53.214Z")
requestBody.SetEndDateTime(&endDateTime) 
reviewedEntity := graphmodels.NewIdentity()
id := "99025615-a0b1-47ec-9117-35377b10998b"
reviewedEntity.SetId(&id) 
requestBody.SetReviewedEntity(reviewedEntity)
reviewerType := "delegated"
requestBody.SetReviewerType(&reviewerType) 
businessFlowTemplateId := "6e4f3d20-c5c3-407f-9695-8460952bcc68"
requestBody.SetBusinessFlowTemplateId(&businessFlowTemplateId) 
description := "Sample description"
requestBody.SetDescription(&description) 


accessReviewReviewer := graphmodels.NewAccessReviewReviewer()
id := "f260246a-09b1-4fd5-8d18-daed736071ec"
accessReviewReviewer.SetId(&id) 
accessReviewReviewer1 := graphmodels.NewAccessReviewReviewer()
id := "5a4e184c-4ee5-4883-96e9-b371f8da88e3"
accessReviewReviewer1.SetId(&id) 

reviewers := []graphmodels.AccessReviewReviewerable {
	accessReviewReviewer,
	accessReviewReviewer1,
}
requestBody.SetReviewers(reviewers)
settings := graphmodels.NewAccessReviewSettings()
mailNotificationsEnabled := true
settings.SetMailNotificationsEnabled(&mailNotificationsEnabled) 
remindersEnabled := true
settings.SetRemindersEnabled(&remindersEnabled) 
justificationRequiredOnApproval := true
settings.SetJustificationRequiredOnApproval(&justificationRequiredOnApproval) 
autoReviewEnabled := false
settings.SetAutoReviewEnabled(&autoReviewEnabled) 
activityDurationInDays := int32(30)
settings.SetActivityDurationInDays(&activityDurationInDays) 
autoApplyReviewResultsEnabled := false
settings.SetAutoApplyReviewResultsEnabled(&autoApplyReviewResultsEnabled) 
accessRecommendationsEnabled := false
settings.SetAccessRecommendationsEnabled(&accessRecommendationsEnabled) 
recurrenceSettings := graphmodels.NewAccessReviewRecurrenceSettings()
recurrenceType := "onetime"
recurrenceSettings.SetRecurrenceType(&recurrenceType) 
recurrenceEndType := "endBy"
recurrenceSettings.SetRecurrenceEndType(&recurrenceEndType) 
durationInDays := int32(0)
recurrenceSettings.SetDurationInDays(&durationInDays) 
recurrenceCount := int32(0)
recurrenceSettings.SetRecurrenceCount(&recurrenceCount) 
settings.SetRecurrenceSettings(recurrenceSettings)
autoReviewSettings := graphmodels.NewAutoReviewSettings()
notReviewedResult := "Deny"
autoReviewSettings.SetNotReviewedResult(&notReviewedResult) 
settings.SetAutoReviewSettings(autoReviewSettings)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
accessReviews, err := graphClient.AccessReviews().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReview accessReview = new AccessReview();
accessReview.setDisplayName("TestReview");
OffsetDateTime startDateTime = OffsetDateTime.parse("2017-02-10T00:35:53.214Z");
accessReview.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2017-03-12T00:35:53.214Z");
accessReview.setEndDateTime(endDateTime);
Identity reviewedEntity = new Identity();
reviewedEntity.setId("99025615-a0b1-47ec-9117-35377b10998b");
accessReview.setReviewedEntity(reviewedEntity);
accessReview.setReviewerType("delegated");
accessReview.setBusinessFlowTemplateId("6e4f3d20-c5c3-407f-9695-8460952bcc68");
accessReview.setDescription("Sample description");
LinkedList<AccessReviewReviewer> reviewers = new LinkedList<AccessReviewReviewer>();
AccessReviewReviewer accessReviewReviewer = new AccessReviewReviewer();
accessReviewReviewer.setId("f260246a-09b1-4fd5-8d18-daed736071ec");
reviewers.add(accessReviewReviewer);
AccessReviewReviewer accessReviewReviewer1 = new AccessReviewReviewer();
accessReviewReviewer1.setId("5a4e184c-4ee5-4883-96e9-b371f8da88e3");
reviewers.add(accessReviewReviewer1);
accessReview.setReviewers(reviewers);
AccessReviewSettings settings = new AccessReviewSettings();
settings.setMailNotificationsEnabled(true);
settings.setRemindersEnabled(true);
settings.setJustificationRequiredOnApproval(true);
settings.setAutoReviewEnabled(false);
settings.setActivityDurationInDays(30);
settings.setAutoApplyReviewResultsEnabled(false);
settings.setAccessRecommendationsEnabled(false);
AccessReviewRecurrenceSettings recurrenceSettings = new AccessReviewRecurrenceSettings();
recurrenceSettings.setRecurrenceType("onetime");
recurrenceSettings.setRecurrenceEndType("endBy");
recurrenceSettings.setDurationInDays(0);
recurrenceSettings.setRecurrenceCount(0);
settings.setRecurrenceSettings(recurrenceSettings);
AutoReviewSettings autoReviewSettings = new AutoReviewSettings();
autoReviewSettings.setNotReviewedResult("Deny");
settings.setAutoReviewSettings(autoReviewSettings);
accessReview.setSettings(settings);
AccessReview result = graphClient.accessReviews().post(accessReview);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReview = {
    displayName: 'TestReview',
    startDateTime: '2017-02-10T00:35:53.214Z',
    endDateTime: '2017-03-12T00:35:53.214Z',
    reviewedEntity: {
        id: '99025615-a0b1-47ec-9117-35377b10998b'
    },
    reviewerType: 'delegated',
    businessFlowTemplateId: '6e4f3d20-c5c3-407f-9695-8460952bcc68',
    description: 'Sample description',
    reviewers: 
    [
        {
            id: 'f260246a-09b1-4fd5-8d18-daed736071ec'
        },
        {
            id: '5a4e184c-4ee5-4883-96e9-b371f8da88e3'
        }
    ],
    settings: 
    {
        mailNotificationsEnabled: true,
        remindersEnabled: true,
        justificationRequiredOnApproval: true,
        autoReviewEnabled: false,
        activityDurationInDays: 30,
        autoApplyReviewResultsEnabled: false,
        accessRecommendationsEnabled: false,
        recurrenceSettings: {
            recurrenceType: 'onetime',
            recurrenceEndType: 'endBy',
            durationInDays: 0,
            recurrenceCount: 0
        },
        autoReviewSettings: {
            notReviewedResult: 'Deny'
        }
    }
};

await client.api('/accessReviews')
	.version('beta')
	.post(accessReview);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\AccessReview;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\AccessReviewReviewer;
use Microsoft\Graph\Beta\Generated\Models\AccessReviewSettings;
use Microsoft\Graph\Beta\Generated\Models\AccessReviewRecurrenceSettings;
use Microsoft\Graph\Beta\Generated\Models\AutoReviewSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReview();
$requestBody->setDisplayName('TestReview');
$requestBody->setStartDateTime(new \DateTime('2017-02-10T00:35:53.214Z'));
$requestBody->setEndDateTime(new \DateTime('2017-03-12T00:35:53.214Z'));
$reviewedEntity = new Identity();
$reviewedEntity->setId('99025615-a0b1-47ec-9117-35377b10998b');
$requestBody->setReviewedEntity($reviewedEntity);
$requestBody->setReviewerType('delegated');
$requestBody->setBusinessFlowTemplateId('6e4f3d20-c5c3-407f-9695-8460952bcc68');
$requestBody->setDescription('Sample description');
$reviewersAccessReviewReviewer1 = new AccessReviewReviewer();
$reviewersAccessReviewReviewer1->setId('f260246a-09b1-4fd5-8d18-daed736071ec');
$reviewersArray []= $reviewersAccessReviewReviewer1;
$reviewersAccessReviewReviewer2 = new AccessReviewReviewer();
$reviewersAccessReviewReviewer2->setId('5a4e184c-4ee5-4883-96e9-b371f8da88e3');
$reviewersArray []= $reviewersAccessReviewReviewer2;
$requestBody->setReviewers($reviewersArray);

$settings = new AccessReviewSettings();
$settings->setMailNotificationsEnabled(true);
$settings->setRemindersEnabled(true);
$settings->setJustificationRequiredOnApproval(true);
$settings->setAutoReviewEnabled(false);
$settings->setActivityDurationInDays(30);
$settings->setAutoApplyReviewResultsEnabled(false);
$settings->setAccessRecommendationsEnabled(false);
$settingsRecurrenceSettings = new AccessReviewRecurrenceSettings();
$settingsRecurrenceSettings->setRecurrenceType('onetime');
$settingsRecurrenceSettings->setRecurrenceEndType('endBy');
$settingsRecurrenceSettings->setDurationInDays(0);
$settingsRecurrenceSettings->setRecurrenceCount(0);
$settings->setRecurrenceSettings($settingsRecurrenceSettings);
$settingsAutoReviewSettings = new AutoReviewSettings();
$settingsAutoReviewSettings->setNotReviewedResult('Deny');
$settings->setAutoReviewSettings($settingsAutoReviewSettings);
$requestBody->setSettings($settings);

$result = $graphServiceClient->accessReviews()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Identity.Governance

$params = @{
	displayName = "TestReview"
	startDateTime = [System.DateTime]::Parse("2017-02-10T00:35:53.214Z")
	endDateTime = [System.DateTime]::Parse("2017-03-12T00:35:53.214Z")
	reviewedEntity = @{
		id = "99025615-a0b1-47ec-9117-35377b10998b"
	}
	reviewerType = "delegated"
	businessFlowTemplateId = "6e4f3d20-c5c3-407f-9695-8460952bcc68"
	description = "Sample description"
	reviewers = @(
		@{
			id = "f260246a-09b1-4fd5-8d18-daed736071ec"
		}
		@{
			id = "5a4e184c-4ee5-4883-96e9-b371f8da88e3"
		}
	)
	settings = @{
		mailNotificationsEnabled = $true
		remindersEnabled = $true
		justificationRequiredOnApproval = $true
		autoReviewEnabled = $false
		activityDurationInDays = 30
		autoApplyReviewResultsEnabled = $false
		accessRecommendationsEnabled = $false
		recurrenceSettings = @{
			recurrenceType = "onetime"
			recurrenceEndType = "endBy"
			durationInDays = 0
			recurrenceCount = 0
		}
		autoReviewSettings = @{
			notReviewedResult = "Deny"
		}
	}
}

New-MgBetaAccessReview -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.access_review import AccessReview
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.access_review_reviewer import AccessReviewReviewer
from msgraph_beta.generated.models.access_review_settings import AccessReviewSettings
from msgraph_beta.generated.models.access_review_recurrence_settings import AccessReviewRecurrenceSettings
from msgraph_beta.generated.models.auto_review_settings import AutoReviewSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReview(
	display_name = "TestReview",
	start_date_time = "2017-02-10T00:35:53.214Z",
	end_date_time = "2017-03-12T00:35:53.214Z",
	reviewed_entity = Identity(
		id = "99025615-a0b1-47ec-9117-35377b10998b",
	),
	reviewer_type = "delegated",
	business_flow_template_id = "6e4f3d20-c5c3-407f-9695-8460952bcc68",
	description = "Sample description",
	reviewers = [
		AccessReviewReviewer(
			id = "f260246a-09b1-4fd5-8d18-daed736071ec",
		),
		AccessReviewReviewer(
			id = "5a4e184c-4ee5-4883-96e9-b371f8da88e3",
		),
	],
	settings = AccessReviewSettings(
		mail_notifications_enabled = True,
		reminders_enabled = True,
		justification_required_on_approval = True,
		auto_review_enabled = False,
		activity_duration_in_days = 30,
		auto_apply_review_results_enabled = False,
		access_recommendations_enabled = False,
		recurrence_settings = AccessReviewRecurrenceSettings(
			recurrence_type = "onetime",
			recurrence_end_type = "endBy",
			duration_in_days = 0,
			recurrence_count = 0,
		),
		auto_review_settings = AutoReviewSettings(
			not_reviewed_result = "Deny",
		),
	),
)

result = await graph_client.access_reviews.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "006111db-0810-4494-a6df-904d368bd81b",
    "displayName": "TestReview",
    "startDateTime": "2017-02-10T00:35:53.214Z",
    "endDateTime": "2017-03-12T00:35:53.214Z",
    "status": "Initializing",
    "businessFlowTemplateId": "6e4f3d20-c5c3-407f-9695-8460952bcc68",
    "reviewerType": "delegated",
    "description": "Sample description"
}
```
