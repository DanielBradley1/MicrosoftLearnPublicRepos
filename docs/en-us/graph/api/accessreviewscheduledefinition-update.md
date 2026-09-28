<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update accessReviewScheduleDefinition

Namespace: microsoft.graph

Update an existing [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object to change one or more of its properties.

Note

Any updates made to an accessReviewScheduleDefinition only apply to future instances. Currently running instances cannot be updated. Additionally, this API is not intended to update properties, including decisions, on the accessReviewInstance level. See [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) for more information on instances.

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

## HTTP request

```http
PUT /identityGovernance/accessReviews/definitions/{review-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.

The following table shows the properties accepted to update an accessReviewScheduleDefinition.

| Property | Type | Description |
| :--- | :--- | :--- |
| descriptionForAdmins | String | Context of the review provided to admins. |
| descriptionForReviewers | String | Context of the review provided to reviewers. |
| displayName | String | Name of access review series. |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | A collection of reviewer scopes used to define the list of fallback reviewers who are notified to take action if no users are found from the list of reviewers specified. This could occur when either the group owner is specified as the reviewer but the group owner doesn't exist, or manager is specified as reviewer but a user's manager doesn't exist. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | Defines who the reviewers are. If none are specified, the review is a self-review \(users review their own access\). The **reviewers** property is only updatable if individual users are assigned as reviewers. See [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0). |
| stageSettings | [accessReviewStageSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstagesettings?view=graph-rest-1.0) collection | Defines how many stages each instance of an access review series will have. Stages will be created sequentially based on the **dependsOn** property. Each stage can have different set of reviewer, fallback reviewers and settings. Only reviewers and fallback reviewers are updatable. See [accessReviewStageSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstagesettings?view=graph-rest-1.0). |
| settings | [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) | The settings for an access review series. See [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0). |

A **PUT** request expects the full object to be passed in, which includes all writable properties, not just the properties being updated.

## Response

If successful, this method returns a `204 No Content` response code and no response body.

## Examples

This is an example of updating the displayName of an existing access review series.

### Request

In the request body, supply a JSON representation of the new properties of the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PUT https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/60860cdd-fb4d-4054-91ba-f75e04444aa6
Content-type: application/json

{
  "id": "60860cdd-fb4d-4054-91ba-f75e04444aa6",
  "displayName": "Test world UPDATED NAME!",
  "descriptionForAdmins": "Test world",
  "descriptionForReviewers": "Test world",
  "scope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers",
    "queryType": "MicrosoftGraph"
  },
  "instanceEnumerationScope": {
    "@odata.type": "#microsoft.graph.accessReviewQueryScope",
    "query": "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f",
    "queryType": "MicrosoftGraph"
  },
  "reviewers": [],
  "settings": {
    "mailNotificationsEnabled": true,
    "reminderNotificationsEnabled": true,
    "justificationRequiredOnApproval": true,
    "defaultDecisionEnabled": false,
    "defaultDecision": "None",
    "instanceDurationInDays": 3,
    "autoApplyDecisionsEnabled": false,
    "recommendationsEnabled": true,
    "recurrence": {
      "pattern": {
        "type": "weekly",
        "interval": 1
      },
      "range": {
        "type": "noEnd",
        "startDate": "2020-09-15"
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
	Id = "60860cdd-fb4d-4054-91ba-f75e04444aa6",
	DisplayName = "Test world UPDATED NAME!",
	DescriptionForAdmins = "Test world",
	DescriptionForReviewers = "Test world",
	Scope = new AccessReviewQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewQueryScope",
		Query = "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers",
		QueryType = "MicrosoftGraph",
	},
	InstanceEnumerationScope = new AccessReviewQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewQueryScope",
		Query = "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f",
		QueryType = "MicrosoftGraph",
	},
	Reviewers = new List<AccessReviewReviewerScope>
	{
	},
	Settings = new AccessReviewScheduleSettings
	{
		MailNotificationsEnabled = true,
		ReminderNotificationsEnabled = true,
		JustificationRequiredOnApproval = true,
		DefaultDecisionEnabled = false,
		DefaultDecision = "None",
		InstanceDurationInDays = 3,
		AutoApplyDecisionsEnabled = false,
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
				StartDate = new Date(DateTime.Parse("2020-09-15")),
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions["{accessReviewScheduleDefinition-id}"].PutAsync(requestBody);
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
id := "60860cdd-fb4d-4054-91ba-f75e04444aa6"
requestBody.SetId(&id) 
displayName := "Test world UPDATED NAME!"
requestBody.SetDisplayName(&displayName) 
descriptionForAdmins := "Test world"
requestBody.SetDescriptionForAdmins(&descriptionForAdmins) 
descriptionForReviewers := "Test world"
requestBody.SetDescriptionForReviewers(&descriptionForReviewers) 
scope := graphmodels.NewAccessReviewQueryScope()
query := "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers"
scope.SetQuery(&query) 
queryType := "MicrosoftGraph"
scope.SetQueryType(&queryType) 
requestBody.SetScope(scope)
instanceEnumerationScope := graphmodels.NewAccessReviewQueryScope()
query := "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f"
instanceEnumerationScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
instanceEnumerationScope.SetQueryType(&queryType) 
requestBody.SetInstanceEnumerationScope(instanceEnumerationScope)
reviewers := []graphmodels.AccessReviewReviewerScopeable {

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
instanceDurationInDays := int32(3)
settings.SetInstanceDurationInDays(&instanceDurationInDays) 
autoApplyDecisionsEnabled := false
settings.SetAutoApplyDecisionsEnabled(&autoApplyDecisionsEnabled) 
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
startDate := 2020-09-15
range.SetStartDate(&startDate) 
recurrence.SetRange(range)
settings.SetRecurrence(recurrence)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
definitions, err := graphClient.IdentityGovernance().AccessReviews().Definitions().ByAccessReviewScheduleDefinitionId("accessReviewScheduleDefinition-id").Put(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setId("60860cdd-fb4d-4054-91ba-f75e04444aa6");
accessReviewScheduleDefinition.setDisplayName("Test world UPDATED NAME!");
accessReviewScheduleDefinition.setDescriptionForAdmins("Test world");
accessReviewScheduleDefinition.setDescriptionForReviewers("Test world");
AccessReviewQueryScope scope = new AccessReviewQueryScope();
scope.setOdataType("#microsoft.graph.accessReviewQueryScope");
scope.setQuery("/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers");
scope.setQueryType("MicrosoftGraph");
accessReviewScheduleDefinition.setScope(scope);
AccessReviewQueryScope instanceEnumerationScope = new AccessReviewQueryScope();
instanceEnumerationScope.setOdataType("#microsoft.graph.accessReviewQueryScope");
instanceEnumerationScope.setQuery("/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f");
instanceEnumerationScope.setQueryType("MicrosoftGraph");
accessReviewScheduleDefinition.setInstanceEnumerationScope(instanceEnumerationScope);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
accessReviewScheduleDefinition.setReviewers(reviewers);
AccessReviewScheduleSettings settings = new AccessReviewScheduleSettings();
settings.setMailNotificationsEnabled(true);
settings.setReminderNotificationsEnabled(true);
settings.setJustificationRequiredOnApproval(true);
settings.setDefaultDecisionEnabled(false);
settings.setDefaultDecision("None");
settings.setInstanceDurationInDays(3);
settings.setAutoApplyDecisionsEnabled(false);
settings.setRecommendationsEnabled(true);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.Weekly);
pattern.setInterval(1);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
LocalDate startDate = LocalDate.parse("2020-09-15");
range.setStartDate(startDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
accessReviewScheduleDefinition.setSettings(settings);
AccessReviewScheduleDefinition result = graphClient.identityGovernance().accessReviews().definitions().byAccessReviewScheduleDefinitionId("{accessReviewScheduleDefinition-id}").put(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewScheduleDefinition = {
  id: '60860cdd-fb4d-4054-91ba-f75e04444aa6',
  displayName: 'Test world UPDATED NAME!',
  descriptionForAdmins: 'Test world',
  descriptionForReviewers: 'Test world',
  scope: {
    '@odata.type': '#microsoft.graph.accessReviewQueryScope',
    query: '/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers',
    queryType: 'MicrosoftGraph'
  },
  instanceEnumerationScope: {
    '@odata.type': '#microsoft.graph.accessReviewQueryScope',
    query: '/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f',
    queryType: 'MicrosoftGraph'
  },
  reviewers: [],
  settings: {
    mailNotificationsEnabled: true,
    reminderNotificationsEnabled: true,
    justificationRequiredOnApproval: true,
    defaultDecisionEnabled: false,
    defaultDecision: 'None',
    instanceDurationInDays: 3,
    autoApplyDecisionsEnabled: false,
    recommendationsEnabled: true,
    recurrence: {
      pattern: {
        type: 'weekly',
        interval: 1
      },
      range: {
        type: 'noEnd',
        startDate: '2020-09-15'
      }
    }
  }
};

await client.api('/identityGovernance/accessReviews/definitions/60860cdd-fb4d-4054-91ba-f75e04444aa6')
	.put(accessReviewScheduleDefinition);
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
$requestBody->setId('60860cdd-fb4d-4054-91ba-f75e04444aa6');
$requestBody->setDisplayName('Test world UPDATED NAME!');
$requestBody->setDescriptionForAdmins('Test world');
$requestBody->setDescriptionForReviewers('Test world');
$scope = new AccessReviewQueryScope();
$scope->setOdataType('#microsoft.graph.accessReviewQueryScope');
$scope->setQuery('/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers');
$scope->setQueryType('MicrosoftGraph');
$requestBody->setScope($scope);
$instanceEnumerationScope = new AccessReviewQueryScope();
$instanceEnumerationScope->setOdataType('#microsoft.graph.accessReviewQueryScope');
$instanceEnumerationScope->setQuery('/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f');
$instanceEnumerationScope->setQueryType('MicrosoftGraph');
$requestBody->setInstanceEnumerationScope($instanceEnumerationScope);
$requestBody->setReviewers([	]);
$settings = new AccessReviewScheduleSettings();
$settings->setMailNotificationsEnabled(true);
$settings->setReminderNotificationsEnabled(true);
$settings->setJustificationRequiredOnApproval(true);
$settings->setDefaultDecisionEnabled(false);
$settings->setDefaultDecision('None');
$settings->setInstanceDurationInDays(3);
$settings->setAutoApplyDecisionsEnabled(false);
$settings->setRecommendationsEnabled(true);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('weekly'));
$settingsRecurrencePattern->setInterval(1);
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$settingsRecurrenceRange->setStartDate(new Date('2020-09-15'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$requestBody->setSettings($settings);

$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->byAccessReviewScheduleDefinitionId('accessReviewScheduleDefinition-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	id = "60860cdd-fb4d-4054-91ba-f75e04444aa6"
	displayName = "Test world UPDATED NAME!"
	descriptionForAdmins = "Test world"
	descriptionForReviewers = "Test world"
	scope = @{
		"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
		query = "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers"
		queryType = "MicrosoftGraph"
	}
	instanceEnumerationScope = @{
		"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
		query = "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f"
		queryType = "MicrosoftGraph"
	}
	reviewers = @(
	)
	settings = @{
		mailNotificationsEnabled = $true
		reminderNotificationsEnabled = $true
		justificationRequiredOnApproval = $true
		defaultDecisionEnabled = $false
		defaultDecision = "None"
		instanceDurationInDays = 3
		autoApplyDecisionsEnabled = $false
		recommendationsEnabled = $true
		recurrence = @{
			pattern = @{
				type = "weekly"
				interval = 1
			}
			range = @{
				type = "noEnd"
				startDate = "2020-09-15"
			}
		}
	}
}

Set-MgIdentityGovernanceAccessReviewDefinition -AccessReviewScheduleDefinitionId $accessReviewScheduleDefinitionId -BodyParameter $params
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
	id = "60860cdd-fb4d-4054-91ba-f75e04444aa6",
	display_name = "Test world UPDATED NAME!",
	description_for_admins = "Test world",
	description_for_reviewers = "Test world",
	scope = AccessReviewQueryScope(
		odata_type = "#microsoft.graph.accessReviewQueryScope",
		query = "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f/transitiveMembers",
		query_type = "MicrosoftGraph",
	),
	instance_enumeration_scope = AccessReviewQueryScope(
		odata_type = "#microsoft.graph.accessReviewQueryScope",
		query = "/groups/b7a059cb-038a-4802-8fc9-b9d1ed0cf11f",
		query_type = "MicrosoftGraph",
	),
	reviewers = [
	],
	settings = AccessReviewScheduleSettings(
		mail_notifications_enabled = True,
		reminder_notifications_enabled = True,
		justification_required_on_approval = True,
		default_decision_enabled = False,
		default_decision = "None",
		instance_duration_in_days = 3,
		auto_apply_decisions_enabled = False,
		recommendations_enabled = True,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.Weekly,
				interval = 1,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.NoEnd,
				start_date = "2020-09-15",
			),
		),
	),
)

result = await graph_client.identity_governance.access_reviews.definitions.by_access_review_schedule_definition_id('accessReviewScheduleDefinition-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
