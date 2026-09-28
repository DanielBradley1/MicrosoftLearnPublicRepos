<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreviewset-post-definitions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Create definitions

Namespace: microsoft.graph

Create a new [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AccessReview.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AccessReview.ReadWrite.All | Not available. |

The signed-in user must also be in a directory role that permits them to create an access review. For more details, see the role and permission requirements for [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0).

## HTTP request

```http
POST /identityGovernance/accessReviews/definitions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.

The following table shows the properties accepted to create an accessReview.

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalNotificationRecipients | [accessReviewNotificationRecipientItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewnotificationrecipientitem?view=graph-rest-1.0) collection | Defines the list of additional users or group members to be notified of the access review progress. |
| descriptionForAdmins | String | Context of the review provided to admins. Required. |
| descriptionForReviewers | String | Context of the review provided to reviewers in email notifications. Email notifications support up to 256 characters. Required. |
| displayName | String | Name of access review series. Required. |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | If provided, the fallback reviewers are asked to complete a review if the primary reviewers don't exist. For example, if managers are selected as `reviewers` and a principal under review doesn't have a manager in Microsoft Entra ID, the fallback reviewers are asked to review that principal.  <br>  <br>**NOTE:** The value of this property will be ignored if fallback reviewers are assigned through the **stageSettings** property. |
| instanceEnumerationScope | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) | In the case of an all groups review, this determines the scope of which groups will be reviewed. See [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) and also learn how to [configure the scope of your access review definition](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | Defines who the reviewers are. If none are specified, the review is a self-review \(users review their own access\). For examples of options for assigning reviewers, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-reviewers-concept).  <br>  <br>**NOTE:** The value of this property will be ignored if reviewers are assigned through the **stageSettings** property. |
| scope | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) | Defines the entities whose access is reviewed. See [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) and also learn how to [configure the scope of your access review definition](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). Required. |
| stageSettings | [accessReviewStageSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstagesettings?view=graph-rest-1.0) collection | Defines how many stages each instance of an access review series will have. Stages will be created sequentially based on the **dependsOn** property. Each stage can have different set of reviewer, fallback reviewers and settings.  <br>  <br>When this property is defined, its values are used instead of the corresponding values in the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object and its **settings** property. Optional. |
| settings | [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) | The settings for an access review series. Recurrence is determined here. See [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0). |

## Response

If successful, this method returns a `201 Created` response code and an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an access review on a group

The following example creates an access review with the following settings:

- The review reviews all members of a group with the **id** `02f3bafb-448c-487c-88c2-5fd65ce49a41`.
- A specific user with the user **id** `398164b1-5196-49dd-ada2-364b49f99b27` is the reviewer.
- It recurs weekly and continues indefinitely.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions
Content-type: application/json

{
  "displayName": "Test create",
  "descriptionForAdmins": "New scheduled access review",
  "descriptionForReviewers": "If you have any questions, contact jerry@contoso.com",
  "scope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers",
    "queryType": "MicrosoftGraph"
  },
  "reviewers": [
    {
      "query": "/users/398164b1-5196-49dd-ada2-364b49f99b27",
      "queryType": "MicrosoftGraph"
    }
  ],  
  "settings": {
    "mailNotificationsEnabled": true,
    "reminderNotificationsEnabled": true,
    "justificationRequiredOnApproval": true,
    "defaultDecisionEnabled": false,
    "defaultDecision": "None",
    "instanceDurationInDays": 1,
    "recommendationsEnabled": true,
    "recurrence": {
      "pattern": {
        "type": "weekly",
        "interval": 1
      },
      "range": {
        "type": "noEnd",
        "startDate": "2020-09-08T12:02:30.667Z"
      }
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessReviewScheduleDefinition
{
	DisplayName = "Test create",
	DescriptionForAdmins = "New scheduled access review",
	DescriptionForReviewers = "If you have any questions, contact jerry@contoso.com",
	Scope = new AccessReviewQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewQueryScope",
		Query = "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers",
		QueryType = "MicrosoftGraph",
	},
	Reviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "/users/398164b1-5196-49dd-ada2-364b49f99b27",
			QueryType = "MicrosoftGraph",
		},
	},
	Settings = new AccessReviewScheduleSettings
	{
		MailNotificationsEnabled = true,
		ReminderNotificationsEnabled = true,
		JustificationRequiredOnApproval = true,
		DefaultDecisionEnabled = false,
		DefaultDecision = "None",
		InstanceDurationInDays = 1,
		RecommendationsEnabled = true,
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				Type = RecurrencePatternType.Weekly,
				Interval = 1,
			},
			Range = new RecurrenceRange
			{
				Type = RecurrenceRangeType.NoEnd,
				StartDate = new Date(DateTime.Parse("2020-09-08T12:02:30.667Z")),
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessReviewScheduleDefinition()
displayName := "Test create"
requestBody.SetDisplayName(&displayName) 
descriptionForAdmins := "New scheduled access review"
requestBody.SetDescriptionForAdmins(&descriptionForAdmins) 
descriptionForReviewers := "If you have any questions, contact jerry@contoso.com"
requestBody.SetDescriptionForReviewers(&descriptionForReviewers) 
scope := graphmodels.NewAccessReviewQueryScope()
query := "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers"
scope.SetQuery(&query) 
queryType := "MicrosoftGraph"
scope.SetQueryType(&queryType) 
requestBody.SetScope(scope)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/users/398164b1-5196-49dd-ada2-364b49f99b27"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 

reviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
requestBody.SetReviewers(reviewers)
settings := graphmodels.NewAccessReviewScheduleSettings()
mailNotificationsEnabled := true
settings.SetMailNotificationsEnabled(&mailNotificationsEnabled) 
reminderNotificationsEnabled := true
settings.SetReminderNotificationsEnabled(&reminderNotificationsEnabled) 
justificationRequiredOnApproval := true
settings.SetJustificationRequiredOnApproval(&justificationRequiredOnApproval) 
defaultDecisionEnabled := false
settings.SetDefaultDecisionEnabled(&defaultDecisionEnabled) 
defaultDecision := "None"
settings.SetDefaultDecision(&defaultDecision) 
instanceDurationInDays := int32(1)
settings.SetInstanceDurationInDays(&instanceDurationInDays) 
recommendationsEnabled := true
settings.SetRecommendationsEnabled(&recommendationsEnabled) 
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.WEEKLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(1)
pattern.SetInterval(&interval) 
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
startDate := 2020-09-08T12:02:30.667Z
range.SetStartDate(&startDate) 
recurrence.SetRange(range)
settings.SetRecurrence(recurrence)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
definitions, err := graphClient.IdentityGovernance().AccessReviews().Definitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setDisplayName("Test create");
accessReviewScheduleDefinition.setDescriptionForAdmins("New scheduled access review");
accessReviewScheduleDefinition.setDescriptionForReviewers("If you have any questions, contact jerry@contoso.com");
AccessReviewQueryScope scope = new AccessReviewQueryScope();
scope.setOdataType("#microsoft.graph.accessReviewQueryScope");
scope.setQuery("/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers");
scope.setQueryType("MicrosoftGraph");
accessReviewScheduleDefinition.setScope(scope);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setQuery("/users/398164b1-5196-49dd-ada2-364b49f99b27");
accessReviewReviewerScope.setQueryType("MicrosoftGraph");
reviewers.add(accessReviewReviewerScope);
accessReviewScheduleDefinition.setReviewers(reviewers);
AccessReviewScheduleSettings settings = new AccessReviewScheduleSettings();
settings.setMailNotificationsEnabled(true);
settings.setReminderNotificationsEnabled(true);
settings.setJustificationRequiredOnApproval(true);
settings.setDefaultDecisionEnabled(false);
settings.setDefaultDecision("None");
settings.setInstanceDurationInDays(1);
settings.setRecommendationsEnabled(true);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.Weekly);
pattern.setInterval(1);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
LocalDate startDate = LocalDate.parse("2020-09-08T12:02:30.667Z");
range.setStartDate(startDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
accessReviewScheduleDefinition.setSettings(settings);
AccessReviewScheduleDefinition result = graphClient.identityGovernance().accessReviews().definitions().post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewScheduleDefinition = {
  displayName: 'Test create',
  descriptionForAdmins: 'New scheduled access review',
  descriptionForReviewers: 'If you have any questions, contact jerry@contoso.com',
  scope: {
    '@odata.type': '#microsoft.graph.accessReviewQueryScope',
    query: '/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers',
    queryType: 'MicrosoftGraph'
  },
  reviewers: [
    {
      query: '/users/398164b1-5196-49dd-ada2-364b49f99b27',
      queryType: 'MicrosoftGraph'
    }
  ],  
  settings: {
    mailNotificationsEnabled: true,
    reminderNotificationsEnabled: true,
    justificationRequiredOnApproval: true,
    defaultDecisionEnabled: false,
    defaultDecision: 'None',
    instanceDurationInDays: 1,
    recommendationsEnabled: true,
    recurrence: {
      pattern: {
        type: 'weekly',
        interval: 1
      },
      range: {
        type: 'noEnd',
        startDate: '2020-09-08T12:02:30.667Z'
      }
    }
  }
};

await client.api('/identityGovernance/accessReviews/definitions')
	.post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleDefinition;
use Microsoft\Graph\Generated\Models\AccessReviewQueryScope;
use Microsoft\Graph\Generated\Models\AccessReviewReviewerScope;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleSettings;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewScheduleDefinition();
$requestBody->setDisplayName('Test create');
$requestBody->setDescriptionForAdmins('New scheduled access review');
$requestBody->setDescriptionForReviewers('If you have any questions, contact jerry@contoso.com');
$scope = new AccessReviewQueryScope();
$scope->setOdataType('#microsoft.graph.accessReviewQueryScope');
$scope->setQuery('/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers');
$scope->setQueryType('MicrosoftGraph');
$requestBody->setScope($scope);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('/users/398164b1-5196-49dd-ada2-364b49f99b27');
$reviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$requestBody->setReviewers($reviewersArray);

$settings = new AccessReviewScheduleSettings();
$settings->setMailNotificationsEnabled(true);
$settings->setReminderNotificationsEnabled(true);
$settings->setJustificationRequiredOnApproval(true);
$settings->setDefaultDecisionEnabled(false);
$settings->setDefaultDecision('None');
$settings->setInstanceDurationInDays(1);
$settings->setRecommendationsEnabled(true);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('weekly'));
$settingsRecurrencePattern->setInterval(1);
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$settingsRecurrenceRange->setStartDate(new Date('2020-09-08T12:02:30.667Z'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$requestBody->setSettings($settings);

$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Test create"
	descriptionForAdmins = "New scheduled access review"
	descriptionForReviewers = "If you have any questions, contact jerry@contoso.com"
	scope = @{
		"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
		query = "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers"
		queryType = "MicrosoftGraph"
	}
	reviewers = @(
		@{
			query = "/users/398164b1-5196-49dd-ada2-364b49f99b27"
			queryType = "MicrosoftGraph"
		}
	)
	settings = @{
		mailNotificationsEnabled = $true
		reminderNotificationsEnabled = $true
		justificationRequiredOnApproval = $true
		defaultDecisionEnabled = $false
		defaultDecision = "None"
		instanceDurationInDays = 1
		recommendationsEnabled = $true
		recurrence = @{
			pattern = @{
				type = "weekly"
				interval = 1
			}
			range = @{
				type = "noEnd"
				startDate = "2020-09-08T12:02:30.667Z"
			}
		}
	}
}

New-MgIdentityGovernanceAccessReviewDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_review_schedule_definition import AccessReviewScheduleDefinition
from msgraph.generated.models.access_review_query_scope import AccessReviewQueryScope
from msgraph.generated.models.access_review_reviewer_scope import AccessReviewReviewerScope
from msgraph.generated.models.access_review_schedule_settings import AccessReviewScheduleSettings
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewScheduleDefinition(
	display_name = "Test create",
	description_for_admins = "New scheduled access review",
	description_for_reviewers = "If you have any questions, contact jerry@contoso.com",
	scope = AccessReviewQueryScope(
		odata_type = "#microsoft.graph.accessReviewQueryScope",
		query = "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers",
		query_type = "MicrosoftGraph",
	),
	reviewers = [
		AccessReviewReviewerScope(
			query = "/users/398164b1-5196-49dd-ada2-364b49f99b27",
			query_type = "MicrosoftGraph",
		),
	],
	settings = AccessReviewScheduleSettings(
		mail_notifications_enabled = True,
		reminder_notifications_enabled = True,
		justification_required_on_approval = True,
		default_decision_enabled = False,
		default_decision = "None",
		instance_duration_in_days = 1,
		recommendations_enabled = True,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.Weekly,
				interval = 1,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.NoEnd,
				start_date = "2020-09-08T12:02:30.667Z",
			),
		),
	),
)

result = await graph_client.identity_governance.access_reviews.definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "29f2d16e-9ca6-4052-bbfe-802c48944448",
  "displayName": "Test create",
  "createdDateTime": "0001-01-01T00:00:00Z",
  "lastModifiedDateTime": "0001-01-01T00:00:00Z",
  "status": "NotStarted",
  "descriptionForAdmins": "Test create",
  "descriptionForReviewers": "Test create",
  "instanceEnumerationScope": null,
  "createdBy": {
    "id": "957f1027-c0ee-460d-9269-b8444459e0fe",
    "displayName": "MOD Administrator",
    "userPrincipalName": "admin@contoso.com"
  },
  "scope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups/b74444cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers",
    "queryType": "MicrosoftGraph"
  },
  "reviewers": [
    {
      "query": "/users/7eae986b-d425-48b2-adf2-3c777f4444f3",
      "queryType": "MicrosoftGraph",
      "queryRoot": "decisions"
    }
  ],  
  "settings": {
    "mailNotificationsEnabled": true,
    "reminderNotificationsEnabled": true,
    "justificationRequiredOnApproval": true,
    "defaultDecisionEnabled": false,
    "defaultDecision": "None",
    "instanceDurationInDays": 1,
    "autoApplyDecisionsEnabled": false,
    "recommendationsEnabled": true,
    "recurrence": {
      "pattern": {
        "type": "weekly",
        "interval": 1,
        "month": 0,
        "dayOfMonth": 0,
        "daysOfWeek": [],
        "firstDayOfWeek": "sunday",
        "index": "first"
      },
      "range": {
        "type": "noEnd",
        "numberOfOccurrences": 0,
        "recurrenceTimeZone": null,
        "startDate": "2020-09-08",
        "endDate": null
      }
    },
  "applyActions": []
  },
  "additionalNotificationRecipients": []
}
```

### Example 2: Create an access review on all teams with inactive guest users

The following example creates an access review with the following settings:

- The review reviews all teams with inactive guest users. The period of inactivity is 30 days from the start date of the access review.
- The group owners are the reviewers and fallback reviewers are assigned.
- It recurs on the fifth day of every quarter and continues indefinitely.
- **autoApplyDecisionsEnabled** is set to `true` with the **defaultDecision** set to `Deny`.

#### Request

In the request body, supply a JSON representation of the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions
Content-type: application/json

{
  "displayName": "Review inactive guests on teams",
  "descriptionForAdmins": "Control guest user access to our teams.",
  "descriptionForReviewers": "Information security is everyone's responsibility. Review our access policy for more.",
  "instanceEnumerationScope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups?$filter=(groupTypes/any(c:c+eq+'Unified') and resourceProvisioningOptions/Any(x:x eq 'Team')')",
    "queryType": "MicrosoftGraph"
  },
  "scope": {
    "@odata.type": "#microsoft.graph.accessReviewInactiveUsersQueryScope",
    "query": "./members/microsoft.graph.user/?$filter=(userType eq 'Guest')",
    "queryType": "MicrosoftGraph",
    "inactiveDuration": "P30D"
    },
  "reviewers": [
    {
      "query": "./owners",
      "queryType": "MicrosoftGraph"
    }
  ],
  "fallbackReviewers": [
    {
      "query": "/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f",
      "queryType": "MicrosoftGraph"
    }
  ],
  "settings": {
    "mailNotificationsEnabled": true,
    "reminderNotificationsEnabled": true,
    "justificationRequiredOnApproval": true,
    "recommendationsEnabled": true,
    "instanceDurationInDays": 3,
    "recurrence": {
      "pattern": {
        "type": "absoluteMonthly",
        "dayOfMonth": 5,
        "interval": 3
      },
      "range": {
        "type": "noEnd",
        "startDate": "2020-05-04T00:00:00.000Z"
      }
    },
    "defaultDecisionEnabled": true,
    "defaultDecision": "Deny",
    "autoApplyDecisionsEnabled": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessReviewScheduleDefinition
{
	DisplayName = "Review inactive guests on teams",
	DescriptionForAdmins = "Control guest user access to our teams.",
	DescriptionForReviewers = "Information security is everyone's responsibility. Review our access policy for more.",
	InstanceEnumerationScope = new AccessReviewQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewQueryScope",
		Query = "/groups?$filter=(groupTypes/any(c:c+eq+'Unified') and resourceProvisioningOptions/Any(x:x eq 'Team')')",
		QueryType = "MicrosoftGraph",
	},
	Scope = new AccessReviewInactiveUsersQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewInactiveUsersQueryScope",
		Query = "./members/microsoft.graph.user/?$filter=(userType eq 'Guest')",
		QueryType = "MicrosoftGraph",
		InactiveDuration = TimeSpan.Parse("P30D"),
	},
	Reviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "./owners",
			QueryType = "MicrosoftGraph",
		},
	},
	FallbackReviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f",
			QueryType = "MicrosoftGraph",
		},
	},
	Settings = new AccessReviewScheduleSettings
	{
		MailNotificationsEnabled = true,
		ReminderNotificationsEnabled = true,
		JustificationRequiredOnApproval = true,
		RecommendationsEnabled = true,
		InstanceDurationInDays = 3,
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				Type = RecurrencePatternType.AbsoluteMonthly,
				DayOfMonth = 5,
				Interval = 3,
			},
			Range = new RecurrenceRange
			{
				Type = RecurrenceRangeType.NoEnd,
				StartDate = new Date(DateTime.Parse("2020-05-04T00:00:00.000Z")),
			},
		},
		DefaultDecisionEnabled = true,
		DefaultDecision = "Deny",
		AutoApplyDecisionsEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessReviewScheduleDefinition()
displayName := "Review inactive guests on teams"
requestBody.SetDisplayName(&displayName) 
descriptionForAdmins := "Control guest user access to our teams."
requestBody.SetDescriptionForAdmins(&descriptionForAdmins) 
descriptionForReviewers := "Information security is everyone's responsibility. Review our access policy for more."
requestBody.SetDescriptionForReviewers(&descriptionForReviewers) 
instanceEnumerationScope := graphmodels.NewAccessReviewQueryScope()
query := "/groups?$filter=(groupTypes/any(c:c+eq+'Unified') and resourceProvisioningOptions/Any(x:x eq 'Team')')"
instanceEnumerationScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
instanceEnumerationScope.SetQueryType(&queryType) 
requestBody.SetInstanceEnumerationScope(instanceEnumerationScope)
scope := graphmodels.NewAccessReviewInactiveUsersQueryScope()
query := "./members/microsoft.graph.user/?$filter=(userType eq 'Guest')"
scope.SetQuery(&query) 
queryType := "MicrosoftGraph"
scope.SetQueryType(&queryType) 
inactiveDuration , err := abstractions.ParseISODuration("P30D")
scope.SetInactiveDuration(&inactiveDuration) 
requestBody.SetScope(scope)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "./owners"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 

reviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
requestBody.SetReviewers(reviewers)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 

fallbackReviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
requestBody.SetFallbackReviewers(fallbackReviewers)
settings := graphmodels.NewAccessReviewScheduleSettings()
mailNotificationsEnabled := true
settings.SetMailNotificationsEnabled(&mailNotificationsEnabled) 
reminderNotificationsEnabled := true
settings.SetReminderNotificationsEnabled(&reminderNotificationsEnabled) 
justificationRequiredOnApproval := true
settings.SetJustificationRequiredOnApproval(&justificationRequiredOnApproval) 
recommendationsEnabled := true
settings.SetRecommendationsEnabled(&recommendationsEnabled) 
instanceDurationInDays := int32(3)
settings.SetInstanceDurationInDays(&instanceDurationInDays) 
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.ABSOLUTEMONTHLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
dayOfMonth := int32(5)
pattern.SetDayOfMonth(&dayOfMonth) 
interval := int32(3)
pattern.SetInterval(&interval) 
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
startDate := 2020-05-04T00:00:00.000Z
range.SetStartDate(&startDate) 
recurrence.SetRange(range)
settings.SetRecurrence(recurrence)
defaultDecisionEnabled := true
settings.SetDefaultDecisionEnabled(&defaultDecisionEnabled) 
defaultDecision := "Deny"
settings.SetDefaultDecision(&defaultDecision) 
autoApplyDecisionsEnabled := true
settings.SetAutoApplyDecisionsEnabled(&autoApplyDecisionsEnabled) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
definitions, err := graphClient.IdentityGovernance().AccessReviews().Definitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setDisplayName("Review inactive guests on teams");
accessReviewScheduleDefinition.setDescriptionForAdmins("Control guest user access to our teams.");
accessReviewScheduleDefinition.setDescriptionForReviewers("Information security is everyone's responsibility. Review our access policy for more.");
AccessReviewQueryScope instanceEnumerationScope = new AccessReviewQueryScope();
instanceEnumerationScope.setOdataType("#microsoft.graph.accessReviewQueryScope");
instanceEnumerationScope.setQuery("/groups?$filter=(groupTypes/any(c:c+eq+'Unified') and resourceProvisioningOptions/Any(x:x eq 'Team')')");
instanceEnumerationScope.setQueryType("MicrosoftGraph");
accessReviewScheduleDefinition.setInstanceEnumerationScope(instanceEnumerationScope);
AccessReviewInactiveUsersQueryScope scope = new AccessReviewInactiveUsersQueryScope();
scope.setOdataType("#microsoft.graph.accessReviewInactiveUsersQueryScope");
scope.setQuery("./members/microsoft.graph.user/?$filter=(userType eq 'Guest')");
scope.setQueryType("MicrosoftGraph");
PeriodAndDuration inactiveDuration = PeriodAndDuration.ofDuration(Duration.parse("P30D"));
scope.setInactiveDuration(inactiveDuration);
accessReviewScheduleDefinition.setScope(scope);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setQuery("./owners");
accessReviewReviewerScope.setQueryType("MicrosoftGraph");
reviewers.add(accessReviewReviewerScope);
accessReviewScheduleDefinition.setReviewers(reviewers);
LinkedList<AccessReviewReviewerScope> fallbackReviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope1 = new AccessReviewReviewerScope();
accessReviewReviewerScope1.setQuery("/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f");
accessReviewReviewerScope1.setQueryType("MicrosoftGraph");
fallbackReviewers.add(accessReviewReviewerScope1);
accessReviewScheduleDefinition.setFallbackReviewers(fallbackReviewers);
AccessReviewScheduleSettings settings = new AccessReviewScheduleSettings();
settings.setMailNotificationsEnabled(true);
settings.setReminderNotificationsEnabled(true);
settings.setJustificationRequiredOnApproval(true);
settings.setRecommendationsEnabled(true);
settings.setInstanceDurationInDays(3);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.AbsoluteMonthly);
pattern.setDayOfMonth(5);
pattern.setInterval(3);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
LocalDate startDate = LocalDate.parse("2020-05-04T00:00:00.000Z");
range.setStartDate(startDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
settings.setDefaultDecisionEnabled(true);
settings.setDefaultDecision("Deny");
settings.setAutoApplyDecisionsEnabled(true);
accessReviewScheduleDefinition.setSettings(settings);
AccessReviewScheduleDefinition result = graphClient.identityGovernance().accessReviews().definitions().post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewScheduleDefinition = {
  displayName: 'Review inactive guests on teams',
  descriptionForAdmins: 'Control guest user access to our teams.',
  descriptionForReviewers: 'Information security is everyone\'s responsibility. Review our access policy for more.',
  instanceEnumerationScope: {
    '@odata.type': '#microsoft.graph.accessReviewQueryScope',
    query: '/groups?$filter=(groupTypes/any(c:c+eq+\'Unified\') and resourceProvisioningOptions/Any(x:x eq \'Team\')\')',
    queryType: 'MicrosoftGraph'
  },
  scope: {
    '@odata.type': '#microsoft.graph.accessReviewInactiveUsersQueryScope',
    query: './members/microsoft.graph.user/?$filter=(userType eq \'Guest\')',
    queryType: 'MicrosoftGraph',
    inactiveDuration: 'P30D'
    },
  reviewers: [
    {
      query: './owners',
      queryType: 'MicrosoftGraph'
    }
  ],
  fallbackReviewers: [
    {
      query: '/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f',
      queryType: 'MicrosoftGraph'
    }
  ],
  settings: {
    mailNotificationsEnabled: true,
    reminderNotificationsEnabled: true,
    justificationRequiredOnApproval: true,
    recommendationsEnabled: true,
    instanceDurationInDays: 3,
    recurrence: {
      pattern: {
        type: 'absoluteMonthly',
        dayOfMonth: 5,
        interval: 3
      },
      range: {
        type: 'noEnd',
        startDate: '2020-05-04T00:00:00.000Z'
      }
    },
    defaultDecisionEnabled: true,
    defaultDecision: 'Deny',
    autoApplyDecisionsEnabled: true
  }
};

await client.api('/identityGovernance/accessReviews/definitions')
	.post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleDefinition;
use Microsoft\Graph\Generated\Models\AccessReviewQueryScope;
use Microsoft\Graph\Generated\Models\AccessReviewInactiveUsersQueryScope;
use Microsoft\Graph\Generated\Models\AccessReviewReviewerScope;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleSettings;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewScheduleDefinition();
$requestBody->setDisplayName('Review inactive guests on teams');
$requestBody->setDescriptionForAdmins('Control guest user access to our teams.');
$requestBody->setDescriptionForReviewers('Information security is everyone\'s responsibility. Review our access policy for more.');
$instanceEnumerationScope = new AccessReviewQueryScope();
$instanceEnumerationScope->setOdataType('#microsoft.graph.accessReviewQueryScope');
$instanceEnumerationScope->setQuery('/groups?$filter=(groupTypes/any(c:c+eq+\'Unified\') and resourceProvisioningOptions/Any(x:x eq \'Team\')\')');
$instanceEnumerationScope->setQueryType('MicrosoftGraph');
$requestBody->setInstanceEnumerationScope($instanceEnumerationScope);
$scope = new AccessReviewInactiveUsersQueryScope();
$scope->setOdataType('#microsoft.graph.accessReviewInactiveUsersQueryScope');
$scope->setQuery('./members/microsoft.graph.user/?$filter=(userType eq \'Guest\')');
$scope->setQueryType('MicrosoftGraph');
$scope->setInactiveDuration(new \DateInterval('P30D'));
$requestBody->setScope($scope);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('./owners');
$reviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$requestBody->setReviewers($reviewersArray);

$fallbackReviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$fallbackReviewersAccessReviewReviewerScope1->setQuery('/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f');
$fallbackReviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$fallbackReviewersArray []= $fallbackReviewersAccessReviewReviewerScope1;
$requestBody->setFallbackReviewers($fallbackReviewersArray);

$settings = new AccessReviewScheduleSettings();
$settings->setMailNotificationsEnabled(true);
$settings->setReminderNotificationsEnabled(true);
$settings->setJustificationRequiredOnApproval(true);
$settings->setRecommendationsEnabled(true);
$settings->setInstanceDurationInDays(3);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('absoluteMonthly'));
$settingsRecurrencePattern->setDayOfMonth(5);
$settingsRecurrencePattern->setInterval(3);
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$settingsRecurrenceRange->setStartDate(new Date('2020-05-04T00:00:00.000Z'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$settings->setDefaultDecisionEnabled(true);
$settings->setDefaultDecision('Deny');
$settings->setAutoApplyDecisionsEnabled(true);
$requestBody->setSettings($settings);

$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Review inactive guests on teams"
	descriptionForAdmins = "Control guest user access to our teams."
	descriptionForReviewers = "Information security is everyone's responsibility. Review our access policy for more."
	instanceEnumerationScope = @{
		"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
		query = "/groups?$filter=(groupTypes/any(c:c+eq+'Unified') and resourceProvisioningOptions/Any(x:x eq 'Team')')"
		queryType = "MicrosoftGraph"
	}
	scope = @{
		"@odata.type" = "#microsoft.graph.accessReviewInactiveUsersQueryScope"
		query = "./members/microsoft.graph.user/?$filter=(userType eq 'Guest')"
		queryType = "MicrosoftGraph"
		inactiveDuration = "P30D"
	}
	reviewers = @(
		@{
			query = "./owners"
			queryType = "MicrosoftGraph"
		}
	)
	fallbackReviewers = @(
		@{
			query = "/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f"
			queryType = "MicrosoftGraph"
		}
	)
	settings = @{
		mailNotificationsEnabled = $true
		reminderNotificationsEnabled = $true
		justificationRequiredOnApproval = $true
		recommendationsEnabled = $true
		instanceDurationInDays = 3
		recurrence = @{
			pattern = @{
				type = "absoluteMonthly"
				dayOfMonth = 5
				interval = 3
			}
			range = @{
				type = "noEnd"
				startDate = "2020-05-04T00:00:00.000Z"
			}
		}
		defaultDecisionEnabled = $true
		defaultDecision = "Deny"
		autoApplyDecisionsEnabled = $true
	}
}

New-MgIdentityGovernanceAccessReviewDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_review_schedule_definition import AccessReviewScheduleDefinition
from msgraph.generated.models.access_review_query_scope import AccessReviewQueryScope
from msgraph.generated.models.access_review_inactive_users_query_scope import AccessReviewInactiveUsersQueryScope
from msgraph.generated.models.access_review_reviewer_scope import AccessReviewReviewerScope
from msgraph.generated.models.access_review_schedule_settings import AccessReviewScheduleSettings
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewScheduleDefinition(
	display_name = "Review inactive guests on teams",
	description_for_admins = "Control guest user access to our teams.",
	description_for_reviewers = "Information security is everyone's responsibility. Review our access policy for more.",
	instance_enumeration_scope = AccessReviewQueryScope(
		odata_type = "#microsoft.graph.accessReviewQueryScope",
		query = "/groups?$filter=(groupTypes/any(c:c+eq+'Unified') and resourceProvisioningOptions/Any(x:x eq 'Team')')",
		query_type = "MicrosoftGraph",
	),
	scope = AccessReviewInactiveUsersQueryScope(
		odata_type = "#microsoft.graph.accessReviewInactiveUsersQueryScope",
		query = "./members/microsoft.graph.user/?$filter=(userType eq 'Guest')",
		query_type = "MicrosoftGraph",
		inactive_duration = "P30D",
	),
	reviewers = [
		AccessReviewReviewerScope(
			query = "./owners",
			query_type = "MicrosoftGraph",
		),
	],
	fallback_reviewers = [
		AccessReviewReviewerScope(
			query = "/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f",
			query_type = "MicrosoftGraph",
		),
	],
	settings = AccessReviewScheduleSettings(
		mail_notifications_enabled = True,
		reminder_notifications_enabled = True,
		justification_required_on_approval = True,
		recommendations_enabled = True,
		instance_duration_in_days = 3,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.AbsoluteMonthly,
				day_of_month = 5,
				interval = 3,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.NoEnd,
				start_date = "2020-05-04T00:00:00.000Z",
			),
		),
		default_decision_enabled = True,
		default_decision = "Deny",
		auto_apply_decisions_enabled = True,
	),
)

result = await graph_client.identity_governance.access_reviews.definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions/$entity",
  "id": "b0966e21-a01e-43c9-8f8b-9ba30ed5710a",
  "displayName": "Review inactive guests on teams",
  "createdDateTime": "2021-05-04T18:27:02.6719849Z",
  "lastModifiedDateTime": "2021-05-04T18:27:24.0889623Z",
  "status": "InProgress",
  "descriptionForAdmins": "Control guest user access to our teams.",
  "descriptionForReviewers": "Information security is everyone's responsibility. Review our access policy for more.",
  "createdBy": {
    "id": "fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f",
    "displayName": "MOD Administrator",
    "userPrincipalName": "admin@contoso.com"
  },
  "scope": {
    "@odata.type": "#microsoft.graph.accessReviewInactiveUsersQueryScope",
    "query": "./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')",
    "queryType": "MicrosoftGraph",
    "queryRoot": null,
    "inactiveDuration": "P30D"
  },
  "instanceEnumerationScope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups?$filter=(groupTypes/any(c:c+eq+'Unified') and resourceProvisioningOptions/Any(x:x eq 'Team'))&$count=true",
    "queryType": "MicrosoftGraph",
    "queryRoot": null
  },
  "reviewers": [
    {
      "query": "./owners",
      "queryType": "MicrosoftGraph",
      "queryRoot": null
    }
  ],
  "backupReviewers": [],
  "fallbackReviewers": [
    {
      "query": "/users/fc9a2c2b-1ddc-486d-a211-5fe8ca77fa1f",
      "queryType": "MicrosoftGraph",
      "queryRoot": null
    }
  ],
  "settings": {
    "mailNotificationsEnabled": true,
    "reminderNotificationsEnabled": true,
    "justificationRequiredOnApproval": true,
    "defaultDecisionEnabled": true,
    "defaultDecision": "Deny",
    "instanceDurationInDays": 3,
    "autoApplyDecisionsEnabled": true,
    "recommendationsEnabled": true,
    "recurrence": {
      "pattern": {
        "type": "absoluteMonthly",
        "interval": 3,
        "month": 0,
        "dayOfMonth": 5,
        "daysOfWeek": [],
        "firstDayOfWeek": "sunday",
        "index": "first"
      },
      "range": {
        "type": "noEnd",
        "numberOfOccurrences": 0,
        "recurrenceTimeZone": null,
        "startDate": "2021-05-05",
        "endDate": "null"
      }
    },
    "applyActions": []
  },
  "additionalNotificationRecipients": []
}
```

### Example 3: Create an access review of all users to an application

The following example creates an access review with the following settings:

- The review reviews user access to an application.
- The people managers are the reviewers and fallback reviewers are the members of a group.
- It recurs semi-annually and ends 1 year from the startDate.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions
Content-type: application/json

{
  "displayName": "Review employee access to LinkedIn",
  "descriptionForAdmins": "Review employee access to LinkedIn",
  "scope": {
    "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
    "principalScopes": [
      {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "/users",
        "queryType": "MicrosoftGraph"
      }
    ],
    "resourceScopes": [
      {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae",
        "queryType": "MicrosoftGraph"
      }
    ]
  },
  "reviewers": [
    {
      "query": "./manager",
      "queryType": "MicrosoftGraph",
      "queryRoot": "decisions"
    }
  ],
  "backupReviewers": [
    {
      "query": "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
      "queryType": "MicrosoftGraph"
    }
  ],
  "fallbackReviewers": [
    {
      "query": "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
      "queryType": "MicrosoftGraph"
    }
  ],
  "settings": {
    "mailNotificationsEnabled": true,
    "reminderNotificationsEnabled": true,
    "justificationRequiredOnApproval": true,
    "defaultDecisionEnabled": true,
    "defaultDecision": "Recommendation",
    "instanceDurationInDays": 180,
    "autoApplyDecisionsEnabled": true,
    "recommendationsEnabled": true,
    "recurrence": {
      "pattern": {
        "type": "absoluteMonthly",
        "interval": 6,
        "dayOfMonth": 0
      },
      "range": {
        "type": "numbered",
        "startDate": "2021-05-05",
        "endDate": "2022-05-05"
      }
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new AccessReviewScheduleDefinition
{
	DisplayName = "Review employee access to LinkedIn",
	DescriptionForAdmins = "Review employee access to LinkedIn",
	Scope = new PrincipalResourceMembershipsScope
	{
		OdataType = "#microsoft.graph.principalResourceMembershipsScope",
		PrincipalScopes = new List<AccessReviewScope>
		{
			new AccessReviewQueryScope
			{
				OdataType = "#microsoft.graph.accessReviewQueryScope",
				Query = "/users",
				QueryType = "MicrosoftGraph",
			},
		},
		ResourceScopes = new List<AccessReviewScope>
		{
			new AccessReviewQueryScope
			{
				OdataType = "#microsoft.graph.accessReviewQueryScope",
				Query = "/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae",
				QueryType = "MicrosoftGraph",
			},
		},
	},
	Reviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "./manager",
			QueryType = "MicrosoftGraph",
			QueryRoot = "decisions",
		},
	},
	FallbackReviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
			QueryType = "MicrosoftGraph",
		},
	},
	Settings = new AccessReviewScheduleSettings
	{
		MailNotificationsEnabled = true,
		ReminderNotificationsEnabled = true,
		JustificationRequiredOnApproval = true,
		DefaultDecisionEnabled = true,
		DefaultDecision = "Recommendation",
		InstanceDurationInDays = 180,
		AutoApplyDecisionsEnabled = true,
		RecommendationsEnabled = true,
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				Type = RecurrencePatternType.AbsoluteMonthly,
				Interval = 6,
				DayOfMonth = 0,
			},
			Range = new RecurrenceRange
			{
				Type = RecurrenceRangeType.Numbered,
				StartDate = new Date(DateTime.Parse("2021-05-05")),
				EndDate = new Date(DateTime.Parse("2022-05-05")),
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"backupReviewers" , new List<object>
			{
				new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"query", new UntypedString("/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers")
					},
					{
						"queryType", new UntypedString("MicrosoftGraph")
					},
				}),
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setDisplayName("Review employee access to LinkedIn");
accessReviewScheduleDefinition.setDescriptionForAdmins("Review employee access to LinkedIn");
PrincipalResourceMembershipsScope scope = new PrincipalResourceMembershipsScope();
scope.setOdataType("#microsoft.graph.principalResourceMembershipsScope");
LinkedList<AccessReviewScope> principalScopes = new LinkedList<AccessReviewScope>();
AccessReviewQueryScope accessReviewScope = new AccessReviewQueryScope();
accessReviewScope.setOdataType("#microsoft.graph.accessReviewQueryScope");
accessReviewScope.setQuery("/users");
accessReviewScope.setQueryType("MicrosoftGraph");
principalScopes.add(accessReviewScope);
scope.setPrincipalScopes(principalScopes);
LinkedList<AccessReviewScope> resourceScopes = new LinkedList<AccessReviewScope>();
AccessReviewQueryScope accessReviewScope1 = new AccessReviewQueryScope();
accessReviewScope1.setOdataType("#microsoft.graph.accessReviewQueryScope");
accessReviewScope1.setQuery("/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae");
accessReviewScope1.setQueryType("MicrosoftGraph");
resourceScopes.add(accessReviewScope1);
scope.setResourceScopes(resourceScopes);
accessReviewScheduleDefinition.setScope(scope);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setQuery("./manager");
accessReviewReviewerScope.setQueryType("MicrosoftGraph");
accessReviewReviewerScope.setQueryRoot("decisions");
reviewers.add(accessReviewReviewerScope);
accessReviewScheduleDefinition.setReviewers(reviewers);
LinkedList<AccessReviewReviewerScope> fallbackReviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope1 = new AccessReviewReviewerScope();
accessReviewReviewerScope1.setQuery("/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers");
accessReviewReviewerScope1.setQueryType("MicrosoftGraph");
fallbackReviewers.add(accessReviewReviewerScope1);
accessReviewScheduleDefinition.setFallbackReviewers(fallbackReviewers);
AccessReviewScheduleSettings settings = new AccessReviewScheduleSettings();
settings.setMailNotificationsEnabled(true);
settings.setReminderNotificationsEnabled(true);
settings.setJustificationRequiredOnApproval(true);
settings.setDefaultDecisionEnabled(true);
settings.setDefaultDecision("Recommendation");
settings.setInstanceDurationInDays(180);
settings.setAutoApplyDecisionsEnabled(true);
settings.setRecommendationsEnabled(true);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.AbsoluteMonthly);
pattern.setInterval(6);
pattern.setDayOfMonth(0);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.Numbered);
LocalDate startDate = LocalDate.parse("2021-05-05");
range.setStartDate(startDate);
LocalDate endDate = LocalDate.parse("2022-05-05");
range.setEndDate(endDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
accessReviewScheduleDefinition.setSettings(settings);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
LinkedList<Object> backupReviewers = new LinkedList<Object>();
 property = new ();
property.setQuery("/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers");
property.setQueryType("MicrosoftGraph");
backupReviewers.add(property);
additionalData.put("backupReviewers", backupReviewers);
accessReviewScheduleDefinition.setAdditionalData(additionalData);
AccessReviewScheduleDefinition result = graphClient.identityGovernance().accessReviews().definitions().post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewScheduleDefinition = {
  displayName: 'Review employee access to LinkedIn',
  descriptionForAdmins: 'Review employee access to LinkedIn',
  scope: {
    '@odata.type': '#microsoft.graph.principalResourceMembershipsScope',
    principalScopes: [
      {
        '@odata.type': '#microsoft.graph.accessReviewQueryScope',
        query: '/users',
        queryType: 'MicrosoftGraph'
      }
    ],
    resourceScopes: [
      {
        '@odata.type': '#microsoft.graph.accessReviewQueryScope',
        query: '/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae',
        queryType: 'MicrosoftGraph'
      }
    ]
  },
  reviewers: [
    {
      query: './manager',
      queryType: 'MicrosoftGraph',
      queryRoot: 'decisions'
    }
  ],
  backupReviewers: [
    {
      query: '/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers',
      queryType: 'MicrosoftGraph'
    }
  ],
  fallbackReviewers: [
    {
      query: '/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers',
      queryType: 'MicrosoftGraph'
    }
  ],
  settings: {
    mailNotificationsEnabled: true,
    reminderNotificationsEnabled: true,
    justificationRequiredOnApproval: true,
    defaultDecisionEnabled: true,
    defaultDecision: 'Recommendation',
    instanceDurationInDays: 180,
    autoApplyDecisionsEnabled: true,
    recommendationsEnabled: true,
    recurrence: {
      pattern: {
        type: 'absoluteMonthly',
        interval: 6,
        dayOfMonth: 0
      },
      range: {
        type: 'numbered',
        startDate: '2021-05-05',
        endDate: '2022-05-05'
      }
    }
  }
};

await client.api('/identityGovernance/accessReviews/definitions')
	.post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleDefinition;
use Microsoft\Graph\Generated\Models\PrincipalResourceMembershipsScope;
use Microsoft\Graph\Generated\Models\AccessReviewScope;
use Microsoft\Graph\Generated\Models\AccessReviewQueryScope;
use Microsoft\Graph\Generated\Models\AccessReviewReviewerScope;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleSettings;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewScheduleDefinition();
$requestBody->setDisplayName('Review employee access to LinkedIn');
$requestBody->setDescriptionForAdmins('Review employee access to LinkedIn');
$scope = new PrincipalResourceMembershipsScope();
$scope->setOdataType('#microsoft.graph.principalResourceMembershipsScope');
$principalScopesAccessReviewScope1 = new AccessReviewQueryScope();
$principalScopesAccessReviewScope1->setOdataType('#microsoft.graph.accessReviewQueryScope');
$principalScopesAccessReviewScope1->setQuery('/users');
$principalScopesAccessReviewScope1->setQueryType('MicrosoftGraph');
$principalScopesArray []= $principalScopesAccessReviewScope1;
$scope->setPrincipalScopes($principalScopesArray);

$resourceScopesAccessReviewScope1 = new AccessReviewQueryScope();
$resourceScopesAccessReviewScope1->setOdataType('#microsoft.graph.accessReviewQueryScope');
$resourceScopesAccessReviewScope1->setQuery('/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae');
$resourceScopesAccessReviewScope1->setQueryType('MicrosoftGraph');
$resourceScopesArray []= $resourceScopesAccessReviewScope1;
$scope->setResourceScopes($resourceScopesArray);

$requestBody->setScope($scope);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('./manager');
$reviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$reviewersAccessReviewReviewerScope1->setQueryRoot('decisions');
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$requestBody->setReviewers($reviewersArray);

$fallbackReviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$fallbackReviewersAccessReviewReviewerScope1->setQuery('/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers');
$fallbackReviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$fallbackReviewersArray []= $fallbackReviewersAccessReviewReviewerScope1;
$requestBody->setFallbackReviewers($fallbackReviewersArray);

$settings = new AccessReviewScheduleSettings();
$settings->setMailNotificationsEnabled(true);
$settings->setReminderNotificationsEnabled(true);
$settings->setJustificationRequiredOnApproval(true);
$settings->setDefaultDecisionEnabled(true);
$settings->setDefaultDecision('Recommendation');
$settings->setInstanceDurationInDays(180);
$settings->setAutoApplyDecisionsEnabled(true);
$settings->setRecommendationsEnabled(true);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('absoluteMonthly'));
$settingsRecurrencePattern->setInterval(6);
$settingsRecurrencePattern->setDayOfMonth(0);
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('numbered'));
$settingsRecurrenceRange->setStartDate(new Date('2021-05-05'));
$settingsRecurrenceRange->setEndDate(new Date('2022-05-05'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$requestBody->setSettings($settings);
$additionalData = [
'backupReviewers' => [
[
'query' => '/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers',
'queryType' => 'MicrosoftGraph',
],
],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Review employee access to LinkedIn"
	descriptionForAdmins = "Review employee access to LinkedIn"
	scope = @{
		"@odata.type" = "#microsoft.graph.principalResourceMembershipsScope"
		principalScopes = @(
			@{
				"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
				query = "/users"
				queryType = "MicrosoftGraph"
			}
		)
		resourceScopes = @(
			@{
				"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
				query = "/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae"
				queryType = "MicrosoftGraph"
			}
		)
	}
	reviewers = @(
		@{
			query = "./manager"
			queryType = "MicrosoftGraph"
			queryRoot = "decisions"
		}
	)
	backupReviewers = @(
		@{
			query = "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers"
			queryType = "MicrosoftGraph"
		}
	)
	fallbackReviewers = @(
		@{
			query = "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers"
			queryType = "MicrosoftGraph"
		}
	)
	settings = @{
		mailNotificationsEnabled = $true
		reminderNotificationsEnabled = $true
		justificationRequiredOnApproval = $true
		defaultDecisionEnabled = $true
		defaultDecision = "Recommendation"
		instanceDurationInDays = 180
		autoApplyDecisionsEnabled = $true
		recommendationsEnabled = $true
		recurrence = @{
			pattern = @{
				type = "absoluteMonthly"
				interval = 6
				dayOfMonth = 0
			}
			range = @{
				type = "numbered"
				startDate = "2021-05-05"
				endDate = "2022-05-05"
			}
		}
	}
}

New-MgIdentityGovernanceAccessReviewDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_review_schedule_definition import AccessReviewScheduleDefinition
from msgraph.generated.models.principal_resource_memberships_scope import PrincipalResourceMembershipsScope
from msgraph.generated.models.access_review_scope import AccessReviewScope
from msgraph.generated.models.access_review_query_scope import AccessReviewQueryScope
from msgraph.generated.models.access_review_reviewer_scope import AccessReviewReviewerScope
from msgraph.generated.models.access_review_schedule_settings import AccessReviewScheduleSettings
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewScheduleDefinition(
	display_name = "Review employee access to LinkedIn",
	description_for_admins = "Review employee access to LinkedIn",
	scope = PrincipalResourceMembershipsScope(
		odata_type = "#microsoft.graph.principalResourceMembershipsScope",
		principal_scopes = [
			AccessReviewQueryScope(
				odata_type = "#microsoft.graph.accessReviewQueryScope",
				query = "/users",
				query_type = "MicrosoftGraph",
			),
		],
		resource_scopes = [
			AccessReviewQueryScope(
				odata_type = "#microsoft.graph.accessReviewQueryScope",
				query = "/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae",
				query_type = "MicrosoftGraph",
			),
		],
	),
	reviewers = [
		AccessReviewReviewerScope(
			query = "./manager",
			query_type = "MicrosoftGraph",
			query_root = "decisions",
		),
	],
	fallback_reviewers = [
		AccessReviewReviewerScope(
			query = "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
			query_type = "MicrosoftGraph",
		),
	],
	settings = AccessReviewScheduleSettings(
		mail_notifications_enabled = True,
		reminder_notifications_enabled = True,
		justification_required_on_approval = True,
		default_decision_enabled = True,
		default_decision = "Recommendation",
		instance_duration_in_days = 180,
		auto_apply_decisions_enabled = True,
		recommendations_enabled = True,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.AbsoluteMonthly,
				interval = 6,
				day_of_month = 0,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.Numbered,
				start_date = "2021-05-05",
				end_date = "2022-05-05",
			),
		),
	),
	additional_data = {
			"backup_reviewers" : [
				{
						"query" : "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
						"query_type" : "MicrosoftGraph",
				},
			],
	}
)

result = await graph_client.identity_governance.access_reviews.definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions/$entity",
  "id": "1f79f34b-8667-40d9-875c-893b630b3dec",
  "scope": {
    "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
    "principalScopes": [
      {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "/users"
      }
    ],
    "resourceScopes": [
      {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "/servicePrincipals/bae11f90-7d5d-46ba-9f55-8112b59d92ae"
      }
    ]
  },
  "reviewers": [
    {
      "query": "./manager"
    }
  ],
  "fallbackReviewers": [
    {
      "query": "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers"
    }
  ]
}
```

### Example 4: Create an access review on a group with multiple stages

The following example creates an access review with the following settings:

- The review reviews all members of a group with the **id** `02f3bafb-448c-487c-88c2-5fd65ce49a41`.
- It has two stages:

  - A specific user with the user **id** `398164b1-5196-49dd-ada2-364b49f99b27` is the reviewer for the first stage.
  - The people managers are the reviewers and fallback reviewers for the second stage.

- It recurs weekly and continues indefinitely.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions
Content-type: application/json

{
  "displayName": "Group Multi-stage Access Review",
  "descriptionForAdmins": "New scheduled access review",
  "descriptionForReviewers": "If you have any questions, contact jerry@contoso.com",
  "scope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers",
    "queryType": "MicrosoftGraph"
  },
  "stageSettings": [
    {
      "stageId": "1",
      "durationInDays": 2,
      "recommendationsEnabled": false,
      "decisionsThatWillMoveToNextStage": [
          "NotReviewed",
          "Approve"
      ],
      "reviewers": [
        {
          "query": "/users/398164b1-5196-49dd-ada2-364b49f99b27",
          "queryType": "MicrosoftGraph"
        }
      ]
    },
    {
      "stageId": "2",
      "dependsOn": [
          "1"
      ],
      "durationInDays": 2,
      "recommendationsEnabled": true,
      "reviewers": [
        {
          "query": "./manager",
          "queryType": "MicrosoftGraph",
          "queryRoot": "decisions"
        }
      ],
      "fallbackReviewers": [
        {
          "query": "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
          "queryType": "MicrosoftGraph"
        }
      ]
    }
  ],
  "settings": {
    "instanceDurationInDays": 4,
    "recurrence": {
      "pattern": {
        "type": "weekly",
        "interval": 1
      },
      "range": {
        "type": "noEnd",
        "startDate": "2020-09-08T12:02:30.667Z"
      }
    },
    "decisionHistoriesForReviewersEnabled": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessReviewScheduleDefinition
{
	DisplayName = "Group Multi-stage Access Review",
	DescriptionForAdmins = "New scheduled access review",
	DescriptionForReviewers = "If you have any questions, contact jerry@contoso.com",
	Scope = new AccessReviewQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewQueryScope",
		Query = "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers",
		QueryType = "MicrosoftGraph",
	},
	StageSettings = new List<AccessReviewStageSettings>
	{
		new AccessReviewStageSettings
		{
			StageId = "1",
			DurationInDays = 2,
			RecommendationsEnabled = false,
			DecisionsThatWillMoveToNextStage = new List<string>
			{
				"NotReviewed",
				"Approve",
			},
			Reviewers = new List<AccessReviewReviewerScope>
			{
				new AccessReviewReviewerScope
				{
					Query = "/users/398164b1-5196-49dd-ada2-364b49f99b27",
					QueryType = "MicrosoftGraph",
				},
			},
		},
		new AccessReviewStageSettings
		{
			StageId = "2",
			DependsOn = new List<string>
			{
				"1",
			},
			DurationInDays = 2,
			RecommendationsEnabled = true,
			Reviewers = new List<AccessReviewReviewerScope>
			{
				new AccessReviewReviewerScope
				{
					Query = "./manager",
					QueryType = "MicrosoftGraph",
					QueryRoot = "decisions",
				},
			},
			FallbackReviewers = new List<AccessReviewReviewerScope>
			{
				new AccessReviewReviewerScope
				{
					Query = "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
					QueryType = "MicrosoftGraph",
				},
			},
		},
	},
	Settings = new AccessReviewScheduleSettings
	{
		InstanceDurationInDays = 4,
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				Type = RecurrencePatternType.Weekly,
				Interval = 1,
			},
			Range = new RecurrenceRange
			{
				Type = RecurrenceRangeType.NoEnd,
				StartDate = new Date(DateTime.Parse("2020-09-08T12:02:30.667Z")),
			},
		},
		DecisionHistoriesForReviewersEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessReviewScheduleDefinition()
displayName := "Group Multi-stage Access Review"
requestBody.SetDisplayName(&displayName) 
descriptionForAdmins := "New scheduled access review"
requestBody.SetDescriptionForAdmins(&descriptionForAdmins) 
descriptionForReviewers := "If you have any questions, contact jerry@contoso.com"
requestBody.SetDescriptionForReviewers(&descriptionForReviewers) 
scope := graphmodels.NewAccessReviewQueryScope()
query := "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers"
scope.SetQuery(&query) 
queryType := "MicrosoftGraph"
scope.SetQueryType(&queryType) 
requestBody.SetScope(scope)


accessReviewStageSettings := graphmodels.NewAccessReviewStageSettings()
stageId := "1"
accessReviewStageSettings.SetStageId(&stageId) 
durationInDays := int32(2)
accessReviewStageSettings.SetDurationInDays(&durationInDays) 
recommendationsEnabled := false
accessReviewStageSettings.SetRecommendationsEnabled(&recommendationsEnabled) 
decisionsThatWillMoveToNextStage := []string {
	"NotReviewed",
	"Approve",
}
accessReviewStageSettings.SetDecisionsThatWillMoveToNextStage(decisionsThatWillMoveToNextStage)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/users/398164b1-5196-49dd-ada2-364b49f99b27"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 

reviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
accessReviewStageSettings.SetReviewers(reviewers)
accessReviewStageSettings1 := graphmodels.NewAccessReviewStageSettings()
stageId := "2"
accessReviewStageSettings1.SetStageId(&stageId) 
dependsOn := []string {
	"1",
}
accessReviewStageSettings1.SetDependsOn(dependsOn)
durationInDays := int32(2)
accessReviewStageSettings1.SetDurationInDays(&durationInDays) 
recommendationsEnabled := true
accessReviewStageSettings1.SetRecommendationsEnabled(&recommendationsEnabled) 


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "./manager"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 
queryRoot := "decisions"
accessReviewReviewerScope.SetQueryRoot(&queryRoot) 

reviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
accessReviewStageSettings1.SetReviewers(reviewers)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 

fallbackReviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
accessReviewStageSettings1.SetFallbackReviewers(fallbackReviewers)

stageSettings := []graphmodels.AccessReviewStageSettingsable {
	accessReviewStageSettings,
	accessReviewStageSettings1,
}
requestBody.SetStageSettings(stageSettings)
settings := graphmodels.NewAccessReviewScheduleSettings()
instanceDurationInDays := int32(4)
settings.SetInstanceDurationInDays(&instanceDurationInDays) 
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.WEEKLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(1)
pattern.SetInterval(&interval) 
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
startDate := 2020-09-08T12:02:30.667Z
range.SetStartDate(&startDate) 
recurrence.SetRange(range)
settings.SetRecurrence(recurrence)
decisionHistoriesForReviewersEnabled := true
settings.SetDecisionHistoriesForReviewersEnabled(&decisionHistoriesForReviewersEnabled) 
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
definitions, err := graphClient.IdentityGovernance().AccessReviews().Definitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setDisplayName("Group Multi-stage Access Review");
accessReviewScheduleDefinition.setDescriptionForAdmins("New scheduled access review");
accessReviewScheduleDefinition.setDescriptionForReviewers("If you have any questions, contact jerry@contoso.com");
AccessReviewQueryScope scope = new AccessReviewQueryScope();
scope.setOdataType("#microsoft.graph.accessReviewQueryScope");
scope.setQuery("/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers");
scope.setQueryType("MicrosoftGraph");
accessReviewScheduleDefinition.setScope(scope);
LinkedList<AccessReviewStageSettings> stageSettings = new LinkedList<AccessReviewStageSettings>();
AccessReviewStageSettings accessReviewStageSettings = new AccessReviewStageSettings();
accessReviewStageSettings.setStageId("1");
accessReviewStageSettings.setDurationInDays(2);
accessReviewStageSettings.setRecommendationsEnabled(false);
LinkedList<String> decisionsThatWillMoveToNextStage = new LinkedList<String>();
decisionsThatWillMoveToNextStage.add("NotReviewed");
decisionsThatWillMoveToNextStage.add("Approve");
accessReviewStageSettings.setDecisionsThatWillMoveToNextStage(decisionsThatWillMoveToNextStage);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setQuery("/users/398164b1-5196-49dd-ada2-364b49f99b27");
accessReviewReviewerScope.setQueryType("MicrosoftGraph");
reviewers.add(accessReviewReviewerScope);
accessReviewStageSettings.setReviewers(reviewers);
stageSettings.add(accessReviewStageSettings);
AccessReviewStageSettings accessReviewStageSettings1 = new AccessReviewStageSettings();
accessReviewStageSettings1.setStageId("2");
LinkedList<String> dependsOn = new LinkedList<String>();
dependsOn.add("1");
accessReviewStageSettings1.setDependsOn(dependsOn);
accessReviewStageSettings1.setDurationInDays(2);
accessReviewStageSettings1.setRecommendationsEnabled(true);
LinkedList<AccessReviewReviewerScope> reviewers1 = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope1 = new AccessReviewReviewerScope();
accessReviewReviewerScope1.setQuery("./manager");
accessReviewReviewerScope1.setQueryType("MicrosoftGraph");
accessReviewReviewerScope1.setQueryRoot("decisions");
reviewers1.add(accessReviewReviewerScope1);
accessReviewStageSettings1.setReviewers(reviewers1);
LinkedList<AccessReviewReviewerScope> fallbackReviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope2 = new AccessReviewReviewerScope();
accessReviewReviewerScope2.setQuery("/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers");
accessReviewReviewerScope2.setQueryType("MicrosoftGraph");
fallbackReviewers.add(accessReviewReviewerScope2);
accessReviewStageSettings1.setFallbackReviewers(fallbackReviewers);
stageSettings.add(accessReviewStageSettings1);
accessReviewScheduleDefinition.setStageSettings(stageSettings);
AccessReviewScheduleSettings settings = new AccessReviewScheduleSettings();
settings.setInstanceDurationInDays(4);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.Weekly);
pattern.setInterval(1);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
LocalDate startDate = LocalDate.parse("2020-09-08T12:02:30.667Z");
range.setStartDate(startDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
settings.setDecisionHistoriesForReviewersEnabled(true);
accessReviewScheduleDefinition.setSettings(settings);
AccessReviewScheduleDefinition result = graphClient.identityGovernance().accessReviews().definitions().post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewScheduleDefinition = {
  displayName: 'Group Multi-stage Access Review',
  descriptionForAdmins: 'New scheduled access review',
  descriptionForReviewers: 'If you have any questions, contact jerry@contoso.com',
  scope: {
    '@odata.type': '#microsoft.graph.accessReviewQueryScope',
    query: '/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers',
    queryType: 'MicrosoftGraph'
  },
  stageSettings: [
    {
      stageId: '1',
      durationInDays: 2,
      recommendationsEnabled: false,
      decisionsThatWillMoveToNextStage: [
          'NotReviewed',
          'Approve'
      ],
      reviewers: [
        {
          query: '/users/398164b1-5196-49dd-ada2-364b49f99b27',
          queryType: 'MicrosoftGraph'
        }
      ]
    },
    {
      stageId: '2',
      dependsOn: [
          '1'
      ],
      durationInDays: 2,
      recommendationsEnabled: true,
      reviewers: [
        {
          query: './manager',
          queryType: 'MicrosoftGraph',
          queryRoot: 'decisions'
        }
      ],
      fallbackReviewers: [
        {
          query: '/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers',
          queryType: 'MicrosoftGraph'
        }
      ]
    }
  ],
  settings: {
    instanceDurationInDays: 4,
    recurrence: {
      pattern: {
        type: 'weekly',
        interval: 1
      },
      range: {
        type: 'noEnd',
        startDate: '2020-09-08T12:02:30.667Z'
      }
    },
    decisionHistoriesForReviewersEnabled: true
  }
};

await client.api('/identityGovernance/accessReviews/definitions')
	.post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleDefinition;
use Microsoft\Graph\Generated\Models\AccessReviewQueryScope;
use Microsoft\Graph\Generated\Models\AccessReviewStageSettings;
use Microsoft\Graph\Generated\Models\AccessReviewReviewerScope;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleSettings;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewScheduleDefinition();
$requestBody->setDisplayName('Group Multi-stage Access Review');
$requestBody->setDescriptionForAdmins('New scheduled access review');
$requestBody->setDescriptionForReviewers('If you have any questions, contact jerry@contoso.com');
$scope = new AccessReviewQueryScope();
$scope->setOdataType('#microsoft.graph.accessReviewQueryScope');
$scope->setQuery('/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers');
$scope->setQueryType('MicrosoftGraph');
$requestBody->setScope($scope);
$stageSettingsAccessReviewStageSettings1 = new AccessReviewStageSettings();
$stageSettingsAccessReviewStageSettings1->setStageId('1');
$stageSettingsAccessReviewStageSettings1->setDurationInDays(2);
$stageSettingsAccessReviewStageSettings1->setRecommendationsEnabled(false);
$stageSettingsAccessReviewStageSettings1->setDecisionsThatWillMoveToNextStage(['NotReviewed', 'Approve', 	]);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('/users/398164b1-5196-49dd-ada2-364b49f99b27');
$reviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$stageSettingsAccessReviewStageSettings1->setReviewers($reviewersArray);

$stageSettingsArray []= $stageSettingsAccessReviewStageSettings1;
$stageSettingsAccessReviewStageSettings2 = new AccessReviewStageSettings();
$stageSettingsAccessReviewStageSettings2->setStageId('2');
$stageSettingsAccessReviewStageSettings2->setDependsOn(['1', ]);
$stageSettingsAccessReviewStageSettings2->setDurationInDays(2);
$stageSettingsAccessReviewStageSettings2->setRecommendationsEnabled(true);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('./manager');
$reviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$reviewersAccessReviewReviewerScope1->setQueryRoot('decisions');
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$stageSettingsAccessReviewStageSettings2->setReviewers($reviewersArray);

$fallbackReviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$fallbackReviewersAccessReviewReviewerScope1->setQuery('/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers');
$fallbackReviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$fallbackReviewersArray []= $fallbackReviewersAccessReviewReviewerScope1;
$stageSettingsAccessReviewStageSettings2->setFallbackReviewers($fallbackReviewersArray);

$stageSettingsArray []= $stageSettingsAccessReviewStageSettings2;
$requestBody->setStageSettings($stageSettingsArray);

$settings = new AccessReviewScheduleSettings();
$settings->setInstanceDurationInDays(4);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('weekly'));
$settingsRecurrencePattern->setInterval(1);
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$settingsRecurrenceRange->setStartDate(new Date('2020-09-08T12:02:30.667Z'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$settings->setDecisionHistoriesForReviewersEnabled(true);
$requestBody->setSettings($settings);

$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Group Multi-stage Access Review"
	descriptionForAdmins = "New scheduled access review"
	descriptionForReviewers = "If you have any questions, contact jerry@contoso.com"
	scope = @{
		"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
		query = "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers"
		queryType = "MicrosoftGraph"
	}
	stageSettings = @(
		@{
			stageId = "1"
			durationInDays = 2
			recommendationsEnabled = $false
			decisionsThatWillMoveToNextStage = @(
			"NotReviewed"
		"Approve"
	)
	reviewers = @(
		@{
			query = "/users/398164b1-5196-49dd-ada2-364b49f99b27"
			queryType = "MicrosoftGraph"
		}
	)
}
@{
	stageId = "2"
	dependsOn = @(
	"1"
)
durationInDays = 2
recommendationsEnabled = $true
reviewers = @(
	@{
		query = "./manager"
		queryType = "MicrosoftGraph"
		queryRoot = "decisions"
	}
)
fallbackReviewers = @(
	@{
		query = "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers"
		queryType = "MicrosoftGraph"
	}
)
}
)
settings = @{
instanceDurationInDays = 4
recurrence = @{
pattern = @{
	type = "weekly"
	interval = 1
}
range = @{
	type = "noEnd"
	startDate = "2020-09-08T12:02:30.667Z"
}
}
decisionHistoriesForReviewersEnabled = $true
}
}

New-MgIdentityGovernanceAccessReviewDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_review_schedule_definition import AccessReviewScheduleDefinition
from msgraph.generated.models.access_review_query_scope import AccessReviewQueryScope
from msgraph.generated.models.access_review_stage_settings import AccessReviewStageSettings
from msgraph.generated.models.access_review_reviewer_scope import AccessReviewReviewerScope
from msgraph.generated.models.access_review_schedule_settings import AccessReviewScheduleSettings
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewScheduleDefinition(
	display_name = "Group Multi-stage Access Review",
	description_for_admins = "New scheduled access review",
	description_for_reviewers = "If you have any questions, contact jerry@contoso.com",
	scope = AccessReviewQueryScope(
		odata_type = "#microsoft.graph.accessReviewQueryScope",
		query = "/groups/02f3bafb-448c-487c-88c2-5fd65ce49a41/transitiveMembers",
		query_type = "MicrosoftGraph",
	),
	stage_settings = [
		AccessReviewStageSettings(
			stage_id = "1",
			duration_in_days = 2,
			recommendations_enabled = False,
			decisions_that_will_move_to_next_stage = [
				"NotReviewed",
				"Approve",
			],
			reviewers = [
				AccessReviewReviewerScope(
					query = "/users/398164b1-5196-49dd-ada2-364b49f99b27",
					query_type = "MicrosoftGraph",
				),
			],
		),
		AccessReviewStageSettings(
			stage_id = "2",
			depends_on = [
				"1",
			],
			duration_in_days = 2,
			recommendations_enabled = True,
			reviewers = [
				AccessReviewReviewerScope(
					query = "./manager",
					query_type = "MicrosoftGraph",
					query_root = "decisions",
				),
			],
			fallback_reviewers = [
				AccessReviewReviewerScope(
					query = "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
					query_type = "MicrosoftGraph",
				),
			],
		),
	],
	settings = AccessReviewScheduleSettings(
		instance_duration_in_days = 4,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.Weekly,
				interval = 1,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.NoEnd,
				start_date = "2020-09-08T12:02:30.667Z",
			),
		),
		decision_histories_for_reviewers_enabled = True,
	),
)

result = await graph_client.identity_governance.access_reviews.definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "29f2d16e-9ca6-4052-bbfe-802c48944448",
  "displayName": "Group Multi-stage Access Review",
  "createdDateTime": "0001-01-01T00:00:00Z",
  "lastModifiedDateTime": "0001-01-01T00:00:00Z",
  "status": "NotStarted",
  "descriptionForAdmins": "New scheduled access review",
  "descriptionForReviewers": "If you have any questions, contact jerry@contoso.com",
  "instanceEnumerationScope": null,
  "createdBy": {
    "id": "957f1027-c0ee-460d-9269-b8444459e0fe",
    "displayName": "MOD Administrator",
    "userPrincipalName": "admin@contoso.com"
  },
  "scope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups/b74444cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers",
    "queryType": "MicrosoftGraph"
  },
  "stageSettings": [
    {
      "stageId": "1",
      "durationInDays": 2,
      "recommendationsEnabled": false,
      "decisionsThatWillMoveToNextStage": [
          "NotReviewed",
          "Approve"
      ],
      "reviewers": [
        {
          "query": "/users/398164b1-5196-49dd-ada2-364b49f99b27",
          "queryType": "MicrosoftGraph"
        }
      ]
    },
    {
      "stageId": "2",
      "dependsOn": [
          "1"
      ],
      "durationInDays": 2,
      "recommendationsEnabled": true,
      "reviewers": [
        {
          "query": "./manager",
          "queryType": "MicrosoftGraph",
          "queryRoot": "decisions"
        }
      ],
      "fallbackReviewers": [
        {
          "query": "/groups/072ac5f4-3f13-4088-ab30-0a276f3e6322/transitiveMembers",
          "queryType": "MicrosoftGraph"
        }
      ]
    }
  ], 
  "settings": {
    "mailNotificationsEnabled": true,
    "reminderNotificationsEnabled": true,
    "justificationRequiredOnApproval": true,
    "defaultDecisionEnabled": false,
    "defaultDecision": "None",
    "instanceDurationInDays": 1,
    "autoApplyDecisionsEnabled": false,
    "recommendationsEnabled": false,
    "recurrence": {
      "pattern": {
        "type": "weekly",
        "interval": 1,
        "month": 0,
        "dayOfMonth": 0,
        "daysOfWeek": [],
        "firstDayOfWeek": "sunday",
        "index": "first"
      },
      "range": {
        "type": "noEnd",
        "numberOfOccurrences": 0,
        "recurrenceTimeZone": null,
        "startDate": "2020-09-08",
        "endDate": null
      }
    },
    "decisionHistoriesForReviewersEnabled": true,
    "applyActions": []
  },
  "additionalNotificationRecipients": []
}
```
