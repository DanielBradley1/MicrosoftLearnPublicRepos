<!-- Source: https://learn.microsoft.com/en-us/graph/tutorial-accessreviews-m365group -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Review guest access to groups using access reviews APIs

The access reviews API in Microsoft Graph enables organizations to audit and attest to the access that identities \(also called *principals*\) are assigned to resources in the organization. With B2B collaboration, you can use Microsoft 365 groups to efficiently manage access for guests to resources such as files, notes, calendars, and even Teams conversations. And by using the access reviews API, organizations can periodically attest to principals that have access to such groups and by extension, other resources in the organization.

In this tutorial, you learn how to:

- Create a recurring access review of Microsoft 365 groups with guests.
- Investigate the decisions that are applied to access reviews.

## Prerequisites

To complete this tutorial, you need the following resources and privileges:

- A working Microsoft Entra tenant with a Microsoft Entra ID P2 or Microsoft Entra ID Governance license enabled.
- A test guest and a test Microsoft 365 group in your tenant. The guest should be a member of the Microsoft 365 group.
- Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) to call Microsoft Graph with an account that has at least the *Identity Governance Administrator* role.
- Grant yourself the following delegated permissions: `AccessReview.ReadWrite.All`.

## Step 1: Create an access review for all Microsoft 365 groups with guests

The following access review series uses these settings:

- It's a recurring access review and reviewed quarterly.
- The group owners are the decision makers.
- The review scope is limited to only Microsoft 365 groups with guests.
- It defines a user as the fallback reviewer who can review the access in case the group doesn't have any owners assigned.
- **autoApplyDecisionsEnabled** is set to `true`. In this case, decisions are applied automatically once the reviewer completes the access review or the access review duration ends. If not enabled, a user must apply the decisions manually after the review completes.
- **applyActions** is set to `removeAccessApplyAction`. This action removes denied guests from the group. The guest can still sign in to your tenant, but won't be members of the group or have the access privileges that are granted through the group.

### Request

In this call, replace these values:

- `c9a5aff7-9298-4d71-adab-0a222e0a05e4` with the ID of the fallback reviewer.
- Value of **startDate** with today's date and value of **endDate** with a date one year from the start date.

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
    "displayName": "Guest access to marketing group",
    "scope": {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')",
        "queryType": "MicrosoftGraph"
    },
    "instanceEnumerationScope": {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "/v1.0/groups?$filter=(groupTypes/any(c:c+eq+'Unified'))&$count=true",
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
    "fallbackReviewers": [
        {
            "query": "/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4",
            "queryType": "MicrosoftGraph"
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
        "recommendationLookBackDuration": "P30D",
        "decisionHistoriesForReviewersEnabled": false,
        "recurrence": {
            "pattern": {
                "type": "absoluteMonthly",
                "interval": 3,
                "month": 0,
                "dayOfMonth": 0,
                "daysOfWeek": [],
                "firstDayOfWeek": "sunday",
                "index": "first"
            },
            "range": {
                "type": "endDate",
                "numberOfOccurrences": 0,
                "recurrenceTimeZone": null,
                "startDate": "2024-03-21",
                "endDate": "2025-03-21"
            }
        },
        "applyActions": [
            {
                "@odata.type": "#microsoft.graph.removeAccessApplyAction"
            }
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessReviewScheduleDefinition
{
	DisplayName = "Guest access to marketing group",
	Scope = new AccessReviewQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewQueryScope",
		Query = "./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')",
		QueryType = "MicrosoftGraph",
	},
	InstanceEnumerationScope = new AccessReviewQueryScope
	{
		OdataType = "#microsoft.graph.accessReviewQueryScope",
		Query = "/v1.0/groups?$filter=(groupTypes/any(c:c+eq+'Unified'))&$count=true",
		QueryType = "MicrosoftGraph",
		QueryRoot = null,
	},
	Reviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "./owners",
			QueryType = "MicrosoftGraph",
			QueryRoot = null,
		},
	},
	FallbackReviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4",
			QueryType = "MicrosoftGraph",
		},
	},
	Settings = new AccessReviewScheduleSettings
	{
		MailNotificationsEnabled = true,
		ReminderNotificationsEnabled = true,
		JustificationRequiredOnApproval = true,
		DefaultDecisionEnabled = true,
		DefaultDecision = "Deny",
		InstanceDurationInDays = 3,
		AutoApplyDecisionsEnabled = true,
		RecommendationsEnabled = true,
		RecommendationLookBackDuration = TimeSpan.Parse("P30D"),
		DecisionHistoriesForReviewersEnabled = false,
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				Type = RecurrencePatternType.AbsoluteMonthly,
				Interval = 3,
				Month = 0,
				DayOfMonth = 0,
				DaysOfWeek = new List<DayOfWeekObject>
				{
				},
				FirstDayOfWeek = DayOfWeekObject.Sunday,
				Index = WeekIndex.First,
			},
			Range = new RecurrenceRange
			{
				Type = RecurrenceRangeType.EndDate,
				NumberOfOccurrences = 0,
				RecurrenceTimeZone = null,
				StartDate = new Date(DateTime.Parse("2024-03-21")),
				EndDate = new Date(DateTime.Parse("2025-03-21")),
			},
		},
		ApplyActions = new List<AccessReviewApplyAction>
		{
			new RemoveAccessApplyAction
			{
				OdataType = "#microsoft.graph.removeAccessApplyAction",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
displayName := "Guest access to marketing group"
requestBody.SetDisplayName(&displayName) 
scope := graphmodels.NewAccessReviewQueryScope()
query := "./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')"
scope.SetQuery(&query) 
queryType := "MicrosoftGraph"
scope.SetQueryType(&queryType) 
requestBody.SetScope(scope)
instanceEnumerationScope := graphmodels.NewAccessReviewQueryScope()
query := "/v1.0/groups?$filter=(groupTypes/any(c:c+eq+'Unified'))&$count=true"
instanceEnumerationScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
instanceEnumerationScope.SetQueryType(&queryType) 
queryRoot := null
instanceEnumerationScope.SetQueryRoot(&queryRoot) 
requestBody.SetInstanceEnumerationScope(instanceEnumerationScope)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "./owners"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 
queryRoot := null
accessReviewReviewerScope.SetQueryRoot(&queryRoot) 

reviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
requestBody.SetReviewers(reviewers)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4"
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
defaultDecisionEnabled := true
settings.SetDefaultDecisionEnabled(&defaultDecisionEnabled) 
defaultDecision := "Deny"
settings.SetDefaultDecision(&defaultDecision) 
instanceDurationInDays := int32(3)
settings.SetInstanceDurationInDays(&instanceDurationInDays) 
autoApplyDecisionsEnabled := true
settings.SetAutoApplyDecisionsEnabled(&autoApplyDecisionsEnabled) 
recommendationsEnabled := true
settings.SetRecommendationsEnabled(&recommendationsEnabled) 
recommendationLookBackDuration , err := abstractions.ParseISODuration("P30D")
settings.SetRecommendationLookBackDuration(&recommendationLookBackDuration) 
decisionHistoriesForReviewersEnabled := false
settings.SetDecisionHistoriesForReviewersEnabled(&decisionHistoriesForReviewersEnabled) 
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.ABSOLUTEMONTHLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(3)
pattern.SetInterval(&interval) 
month := int32(0)
pattern.SetMonth(&month) 
dayOfMonth := int32(0)
pattern.SetDayOfMonth(&dayOfMonth) 
daysOfWeek := []graphmodels.DayOfWeekable {

}
pattern.SetDaysOfWeek(daysOfWeek)
firstDayOfWeek := graphmodels.SUNDAY_DAYOFWEEK 
pattern.SetFirstDayOfWeek(&firstDayOfWeek) 
index := graphmodels.FIRST_WEEKINDEX 
pattern.SetIndex(&index) 
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.ENDDATE_RECURRENCERANGETYPE 
range.SetType(&type) 
numberOfOccurrences := int32(0)
range.SetNumberOfOccurrences(&numberOfOccurrences) 
recurrenceTimeZone := null
range.SetRecurrenceTimeZone(&recurrenceTimeZone) 
startDate := 2024-03-21
range.SetStartDate(&startDate) 
endDate := 2025-03-21
range.SetEndDate(&endDate) 
recurrence.SetRange(range)
settings.SetRecurrence(recurrence)


accessReviewApplyAction := graphmodels.NewRemoveAccessApplyAction()

applyActions := []graphmodels.AccessReviewApplyActionable {
	accessReviewApplyAction,
}
settings.SetApplyActions(applyActions)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
definitions, err := graphClient.IdentityGovernance().AccessReviews().Definitions().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setDisplayName("Guest access to marketing group");
AccessReviewQueryScope scope = new AccessReviewQueryScope();
scope.setOdataType("#microsoft.graph.accessReviewQueryScope");
scope.setQuery("./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')");
scope.setQueryType("MicrosoftGraph");
accessReviewScheduleDefinition.setScope(scope);
AccessReviewQueryScope instanceEnumerationScope = new AccessReviewQueryScope();
instanceEnumerationScope.setOdataType("#microsoft.graph.accessReviewQueryScope");
instanceEnumerationScope.setQuery("/v1.0/groups?$filter=(groupTypes/any(c:c+eq+'Unified'))&$count=true");
instanceEnumerationScope.setQueryType("MicrosoftGraph");
instanceEnumerationScope.setQueryRoot(null);
accessReviewScheduleDefinition.setInstanceEnumerationScope(instanceEnumerationScope);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setQuery("./owners");
accessReviewReviewerScope.setQueryType("MicrosoftGraph");
accessReviewReviewerScope.setQueryRoot(null);
reviewers.add(accessReviewReviewerScope);
accessReviewScheduleDefinition.setReviewers(reviewers);
LinkedList<AccessReviewReviewerScope> fallbackReviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope1 = new AccessReviewReviewerScope();
accessReviewReviewerScope1.setQuery("/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4");
accessReviewReviewerScope1.setQueryType("MicrosoftGraph");
fallbackReviewers.add(accessReviewReviewerScope1);
accessReviewScheduleDefinition.setFallbackReviewers(fallbackReviewers);
AccessReviewScheduleSettings settings = new AccessReviewScheduleSettings();
settings.setMailNotificationsEnabled(true);
settings.setReminderNotificationsEnabled(true);
settings.setJustificationRequiredOnApproval(true);
settings.setDefaultDecisionEnabled(true);
settings.setDefaultDecision("Deny");
settings.setInstanceDurationInDays(3);
settings.setAutoApplyDecisionsEnabled(true);
settings.setRecommendationsEnabled(true);
PeriodAndDuration recommendationLookBackDuration = PeriodAndDuration.ofDuration(Duration.parse("P30D"));
settings.setRecommendationLookBackDuration(recommendationLookBackDuration);
settings.setDecisionHistoriesForReviewersEnabled(false);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.AbsoluteMonthly);
pattern.setInterval(3);
pattern.setMonth(0);
pattern.setDayOfMonth(0);
LinkedList<DayOfWeek> daysOfWeek = new LinkedList<DayOfWeek>();
pattern.setDaysOfWeek(daysOfWeek);
pattern.setFirstDayOfWeek(DayOfWeek.Sunday);
pattern.setIndex(WeekIndex.First);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.EndDate);
range.setNumberOfOccurrences(0);
range.setRecurrenceTimeZone(null);
LocalDate startDate = LocalDate.parse("2024-03-21");
range.setStartDate(startDate);
LocalDate endDate = LocalDate.parse("2025-03-21");
range.setEndDate(endDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
LinkedList<AccessReviewApplyAction> applyActions = new LinkedList<AccessReviewApplyAction>();
RemoveAccessApplyAction accessReviewApplyAction = new RemoveAccessApplyAction();
accessReviewApplyAction.setOdataType("#microsoft.graph.removeAccessApplyAction");
applyActions.add(accessReviewApplyAction);
settings.setApplyActions(applyActions);
accessReviewScheduleDefinition.setSettings(settings);
AccessReviewScheduleDefinition result = graphClient.identityGovernance().accessReviews().definitions().post(accessReviewScheduleDefinition);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewScheduleDefinition = {
    displayName: 'Guest access to marketing group',
    scope: {
        '@odata.type': '#microsoft.graph.accessReviewQueryScope',
        query: './members/microsoft.graph.user/?$count=true&$filter=(userType eq \'Guest\')',
        queryType: 'MicrosoftGraph'
    },
    instanceEnumerationScope: {
        '@odata.type': '#microsoft.graph.accessReviewQueryScope',
        query: '/v1.0/groups?$filter=(groupTypes/any(c:c+eq+\'Unified\'))&$count=true',
        queryType: 'MicrosoftGraph',
        queryRoot: null
    },
    reviewers: [
        {
            query: './owners',
            queryType: 'MicrosoftGraph',
            queryRoot: null
        }
    ],
    fallbackReviewers: [
        {
            query: '/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4',
            queryType: 'MicrosoftGraph'
        }
    ],
    settings: {
        mailNotificationsEnabled: true,
        reminderNotificationsEnabled: true,
        justificationRequiredOnApproval: true,
        defaultDecisionEnabled: true,
        defaultDecision: 'Deny',
        instanceDurationInDays: 3,
        autoApplyDecisionsEnabled: true,
        recommendationsEnabled: true,
        recommendationLookBackDuration: 'P30D',
        decisionHistoriesForReviewersEnabled: false,
        recurrence: {
            pattern: {
                type: 'absoluteMonthly',
                interval: 3,
                month: 0,
                dayOfMonth: 0,
                daysOfWeek: [],
                firstDayOfWeek: 'sunday',
                index: 'first'
            },
            range: {
                type: 'endDate',
                numberOfOccurrences: 0,
                recurrenceTimeZone: null,
                startDate: '2024-03-21',
                endDate: '2025-03-21'
            }
        },
        applyActions: [
            {
                '@odata.type': '#microsoft.graph.removeAccessApplyAction'
            }
        ]
    }
};

await client.api('/identityGovernance/accessReviews/definitions')
	.post(accessReviewScheduleDefinition);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
use Microsoft\Graph\Generated\Models\DayOfWeek;
use Microsoft\Graph\Generated\Models\WeekIndex;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;
use Microsoft\Graph\Generated\Models\AccessReviewApplyAction;
use Microsoft\Graph\Generated\Models\RemoveAccessApplyAction;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewScheduleDefinition();
$requestBody->setDisplayName('Guest access to marketing group');
$scope = new AccessReviewQueryScope();
$scope->setOdataType('#microsoft.graph.accessReviewQueryScope');
$scope->setQuery('./members/microsoft.graph.user/?$count=true&$filter=(userType eq \'Guest\')');
$scope->setQueryType('MicrosoftGraph');
$requestBody->setScope($scope);
$instanceEnumerationScope = new AccessReviewQueryScope();
$instanceEnumerationScope->setOdataType('#microsoft.graph.accessReviewQueryScope');
$instanceEnumerationScope->setQuery('/v1.0/groups?$filter=(groupTypes/any(c:c+eq+\'Unified\'))&$count=true');
$instanceEnumerationScope->setQueryType('MicrosoftGraph');
$instanceEnumerationScope->setQueryRoot(null);
$requestBody->setInstanceEnumerationScope($instanceEnumerationScope);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('./owners');
$reviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$reviewersAccessReviewReviewerScope1->setQueryRoot(null);
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$requestBody->setReviewers($reviewersArray);

$fallbackReviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$fallbackReviewersAccessReviewReviewerScope1->setQuery('/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4');
$fallbackReviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$fallbackReviewersArray []= $fallbackReviewersAccessReviewReviewerScope1;
$requestBody->setFallbackReviewers($fallbackReviewersArray);

$settings = new AccessReviewScheduleSettings();
$settings->setMailNotificationsEnabled(true);
$settings->setReminderNotificationsEnabled(true);
$settings->setJustificationRequiredOnApproval(true);
$settings->setDefaultDecisionEnabled(true);
$settings->setDefaultDecision('Deny');
$settings->setInstanceDurationInDays(3);
$settings->setAutoApplyDecisionsEnabled(true);
$settings->setRecommendationsEnabled(true);
$settings->setRecommendationLookBackDuration(new \DateInterval('P30D'));
$settings->setDecisionHistoriesForReviewersEnabled(false);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('absoluteMonthly'));
$settingsRecurrencePattern->setInterval(3);
$settingsRecurrencePattern->setMonth(0);
$settingsRecurrencePattern->setDayOfMonth(0);
$settingsRecurrencePattern->setDaysOfWeek([]);
$settingsRecurrencePattern->setFirstDayOfWeek(new DayOfWeek('sunday'));
$settingsRecurrencePattern->setIndex(new WeekIndex('first'));
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('endDate'));
$settingsRecurrenceRange->setNumberOfOccurrences(0);
$settingsRecurrenceRange->setRecurrenceTimeZone(null);
$settingsRecurrenceRange->setStartDate(new Date('2024-03-21'));
$settingsRecurrenceRange->setEndDate(new Date('2025-03-21'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$applyActionsAccessReviewApplyAction1 = new RemoveAccessApplyAction();
$applyActionsAccessReviewApplyAction1->setOdataType('#microsoft.graph.removeAccessApplyAction');
$applyActionsArray []= $applyActionsAccessReviewApplyAction1;
$settings->setApplyActions($applyActionsArray);

$requestBody->setSettings($settings);

$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Guest access to marketing group"
	scope = @{
		"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
		query = "./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')"
		queryType = "MicrosoftGraph"
	}
	instanceEnumerationScope = @{
		"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
		query = "/v1.0/groups?$filter=(groupTypes/any(c:c+eq+'Unified'))&$count=true"
		queryType = "MicrosoftGraph"
		queryRoot = $null
	}
	reviewers = @(
		@{
			query = "./owners"
			queryType = "MicrosoftGraph"
			queryRoot = $null
		}
	)
	fallbackReviewers = @(
		@{
			query = "/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4"
			queryType = "MicrosoftGraph"
		}
	)
	settings = @{
		mailNotificationsEnabled = $true
		reminderNotificationsEnabled = $true
		justificationRequiredOnApproval = $true
		defaultDecisionEnabled = $true
		defaultDecision = "Deny"
		instanceDurationInDays = 3
		autoApplyDecisionsEnabled = $true
		recommendationsEnabled = $true
		recommendationLookBackDuration = "P30D"
		decisionHistoriesForReviewersEnabled = $false
		recurrence = @{
			pattern = @{
				type = "absoluteMonthly"
				interval = 3
				month = 0
				dayOfMonth = 0
				daysOfWeek = @(
				)
				firstDayOfWeek = "sunday"
				index = "first"
			}
			range = @{
				type = "endDate"
				numberOfOccurrences = 0
				recurrenceTimeZone = $null
				startDate = "2024-03-21"
				endDate = "2025-03-21"
			}
		}
		applyActions = @(
			@{
				"@odata.type" = "#microsoft.graph.removeAccessApplyAction"
			}
		)
	}
}

New-MgIdentityGovernanceAccessReviewDefinition -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
from msgraph.generated.models.day_of_week import DayOfWeek
from msgraph.generated.models.week_index import WeekIndex
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
from msgraph.generated.models.access_review_apply_action import AccessReviewApplyAction
from msgraph.generated.models.remove_access_apply_action import RemoveAccessApplyAction
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewScheduleDefinition(
	display_name = "Guest access to marketing group",
	scope = AccessReviewQueryScope(
		odata_type = "#microsoft.graph.accessReviewQueryScope",
		query = "./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')",
		query_type = "MicrosoftGraph",
	),
	instance_enumeration_scope = AccessReviewQueryScope(
		odata_type = "#microsoft.graph.accessReviewQueryScope",
		query = "/v1.0/groups?$filter=(groupTypes/any(c:c+eq+'Unified'))&$count=true",
		query_type = "MicrosoftGraph",
		query_root = None,
	),
	reviewers = [
		AccessReviewReviewerScope(
			query = "./owners",
			query_type = "MicrosoftGraph",
			query_root = None,
		),
	],
	fallback_reviewers = [
		AccessReviewReviewerScope(
			query = "/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4",
			query_type = "MicrosoftGraph",
		),
	],
	settings = AccessReviewScheduleSettings(
		mail_notifications_enabled = True,
		reminder_notifications_enabled = True,
		justification_required_on_approval = True,
		default_decision_enabled = True,
		default_decision = "Deny",
		instance_duration_in_days = 3,
		auto_apply_decisions_enabled = True,
		recommendations_enabled = True,
		recommendation_look_back_duration = "P30D",
		decision_histories_for_reviewers_enabled = False,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.AbsoluteMonthly,
				interval = 3,
				month = 0,
				day_of_month = 0,
				days_of_week = [
				],
				first_day_of_week = DayOfWeek.Sunday,
				index = WeekIndex.First,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.EndDate,
				number_of_occurrences = 0,
				recurrence_time_zone = None,
				start_date = "2024-03-21",
				end_date = "2025-03-21",
			),
		),
		apply_actions = [
			RemoveAccessApplyAction(
				odata_type = "#microsoft.graph.removeAccessApplyAction",
			),
		],
	),
)

result = await graph_client.identity_governance.access_reviews.definitions.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions/$entity",
    "id": "c22ae540-b89a-4d24-bac0-4ef35e6591ea",
    "displayName": "Guest access to marketing group",
    "createdDateTime": null,
    "lastModifiedDateTime": null,
    "status": "NotStarted",
    "descriptionForAdmins": null,
    "descriptionForReviewers": null,
    "scope": {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "./members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')",
        "queryType": "MicrosoftGraph",
        "queryRoot": null
    },
    "instanceEnumerationScope": {
        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
        "query": "/groups?$filter=(groupTypes/any(c:c+eq+'Unified'))&$count=true",
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
    "fallbackReviewers": [
        {
            "query": "/users/c9a5aff7-9298-4d71-adab-0a222e0a05e4",
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
        "recommendationLookBackDuration": "P30D",
        "decisionHistoriesForReviewersEnabled": false,
        "recurrence": {
            "pattern": {
                "type": "absoluteMonthly",
                "interval": 3,
                "month": 0,
                "dayOfMonth": 0,
                "daysOfWeek": [],
                "firstDayOfWeek": "sunday",
                "index": "first"
            },
            "range": {
                "type": "endDate",
                "numberOfOccurrences": 0,
                "recurrenceTimeZone": null,
                "startDate": "2024-03-21",
                "endDate": "2025-03-21"
            }
        },
        "applyActions": [
            {
                "@odata.type": "#microsoft.graph.removeAccessApplyAction"
            }
        ],
        "recommendationInsightSettings": []
    },
    "stageSettings": [],
    "additionalNotificationRecipients": []
}
```

## Step 2: List instances of the access review

The following query lists all instances of the access review definition. If there is more than one Microsoft 365 group with guests in your tenant, this request returns *one instance for each group*.

### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/c22ae540-b89a-4d24-bac0-4ef35e6591ea/instances
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions["{accessReviewScheduleDefinition-id}"].Instances.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
instances, err := graphClient.IdentityGovernance().AccessReviews().Definitions().ByAccessReviewScheduleDefinitionId("accessReviewScheduleDefinition-id").Instances().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewInstanceCollectionResponse result = graphClient.identityGovernance().accessReviews().definitions().byAccessReviewScheduleDefinitionId("{accessReviewScheduleDefinition-id}").instances().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let instances = await client.api('/identityGovernance/accessReviews/definitions/c22ae540-b89a-4d24-bac0-4ef35e6591ea/instances')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->byAccessReviewScheduleDefinitionId('accessReviewScheduleDefinition-id')->instances()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceAccessReviewDefinitionInstance -AccessReviewScheduleDefinitionId $accessReviewScheduleDefinitionId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.access_reviews.definitions.by_access_review_schedule_definition_id('accessReviewScheduleDefinition-id').instances.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

In this response, the scope includes the test group because it has a guest. The access review instance is currently `InProgress`. Because it's a quarterly review, a new review instance is created automatically every three months, and the reviewers can apply new decisions.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions('c22ae540-b89a-4d24-bac0-4ef35e6591ea')/instances",
    "value": [
        {
            "id": "6392b1a7-9c25-4844-83e5-34e23c88e16a",
            "startDateTime": "2024-03-21T17:00:36.96Z",
            "endDateTime": "2024-03-24T17:00:36.96Z",
            "status": "InProgress",
            "scope": {
                "query": "/groups/59ab642a-2776-4e32-9b68-9ff7a47b7f6a/members/microsoft.graph.user/?$count=true&$filter=(userType eq 'Guest')",
                "queryType": "MicrosoftGraph"
            }
        }
    ]
}
```

## Step 3: Get decisions

Get the decisions for the instance of an access review. In a quarterly review like this one, and as long as the access review is active:

- A new review instance is created every three months.
- Reviewers must apply new decisions for new instances.

### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/c22ae540-b89a-4d24-bac0-4ef35e6591ea/instances/6392b1a7-9c25-4844-83e5-34e23c88e16a/decisions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions["{accessReviewScheduleDefinition-id}"].Instances["{accessReviewInstance-id}"].Decisions.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
decisions, err := graphClient.IdentityGovernance().AccessReviews().Definitions().ByAccessReviewScheduleDefinitionId("accessReviewScheduleDefinition-id").Instances().ByAccessReviewInstanceId("accessReviewInstance-id").Decisions().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewInstanceDecisionItemCollectionResponse result = graphClient.identityGovernance().accessReviews().definitions().byAccessReviewScheduleDefinitionId("{accessReviewScheduleDefinition-id}").instances().byAccessReviewInstanceId("{accessReviewInstance-id}").decisions().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let decisions = await client.api('/identityGovernance/accessReviews/definitions/c22ae540-b89a-4d24-bac0-4ef35e6591ea/instances/6392b1a7-9c25-4844-83e5-34e23c88e16a/decisions')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->byAccessReviewScheduleDefinitionId('accessReviewScheduleDefinition-id')->instances()->byAccessReviewInstanceId('accessReviewInstance-id')->decisions()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Get-MgIdentityGovernanceAccessReviewDefinitionInstanceDecision -AccessReviewScheduleDefinitionId $accessReviewScheduleDefinitionId -AccessReviewInstanceId $accessReviewInstanceId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.identity_governance.access_reviews.definitions.by_access_review_schedule_definition_id('accessReviewScheduleDefinition-id').instances.by_access_review_instance_id('accessReviewInstance-id').decisions.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Response

The following response shows the decision for the instance of the review.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions('c22ae540-b89a-4d24-bac0-4ef35e6591ea')/instances('6392b1a7-9c25-4844-83e5-34e23c88e16a')/decisions",
    "@odata.count": 1,
    "value": [
        {
            "id": "0e76ee07-b4c6-469e-bc9d-e73fc9a8d660",
            "accessReviewId": "6392b1a7-9c25-4844-83e5-34e23c88e16a",
            "reviewedDateTime": "2021-02-10T17:06:26.147Z",
            "decision": "Approve",
            "justification": "",
            "appliedDateTime": null,
            "applyResult": "New",
            "recommendation": "Deny",
            "reviewedBy": {
                "id": "00000000-0000-0000-0000-000000000000",
                "displayName": "AAD Access Reviews",
                "userPrincipalName": "AAD Access Reviews"
            },
            "appliedBy": {
                "id": "00000000-0000-0000-0000-000000000000",
                "displayName": "",
                "userPrincipalName": ""
            },
            "target": {
                "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItemUserTarget",
                "userId": "baf1b0a0-1f9a-4a56-9884-6a30824f8d20",
                "userDisplayName": "John Doe (Tailspin Toys)",
                "userPrincipalName": "john@tailspintoys.com"
            },
            "principal": {
                "@odata.type": "#microsoft.graph.userIdentity",
                "id": "baf1b0a0-1f9a-4a56-9884-6a30824f8d20",
                "displayName": "John Doe (Tailspin Toys)",
                "userPrincipalName": "john@tailspintoys.com"
            }
        }
    ]
}
```

## Step 4: Clean up resources

In this step, delete the access review definition. Since the access review schedule definition is the blueprint for the access review, deleting the definition removes the related settings, instances, and decisions. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
DELETE https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/c22ae540-b89a-4d24-bac0-4ef35e6591ea
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.AccessReviews.Definitions["{accessReviewScheduleDefinition-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().AccessReviews().Definitions().ByAccessReviewScheduleDefinitionId("accessReviewScheduleDefinition-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.identityGovernance().accessReviews().definitions().byAccessReviewScheduleDefinitionId("{accessReviewScheduleDefinition-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identityGovernance/accessReviews/definitions/c22ae540-b89a-4d24-bac0-4ef35e6591ea')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->identityGovernance()->accessReviews()->definitions()->byAccessReviewScheduleDefinitionId('accessReviewScheduleDefinition-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Remove-MgIdentityGovernanceAccessReviewDefinition -AccessReviewScheduleDefinitionId $accessReviewScheduleDefinitionId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.identity_governance.access_reviews.definitions.by_access_review_schedule_definition_id('accessReviewScheduleDefinition-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

## Related content

- [Access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview)
- [What are Microsoft Entra access reviews?](https://learn.microsoft.com/en-us/entra/id-governance/access-reviews-overview)
- [Review access to groups and applications in Microsoft Entra access reviews](https://learn.microsoft.com/en-us/entra/id-governance/perform-access-review)
