<!-- Source: https://learn.microsoft.com/en-us/graph/tutorial-accessreviews-roleassignments -->
<!-- Sitemap-Last-Modified: 2025-03-07 -->

# Review access to administrative roles using access reviews APIs

The access reviews APIs in Microsoft Graph enables organizations to audit and attest to the access that identities \(also called *principals*\) are assigned to resources in the organization. One of the most sensitive resources in an organization is administrative roles. Using the access reviews API, organizations can periodically attest to principals that have access to administrative roles as per the organization policy.

Contoso needs to ensure only the right assignees are assigned the administrative roles. System auditors should also audit the access review history to report on the effectiveness of Contoso's internal controls.

In this tutorial, you learn how to:

- Create a recurring access review of principals with active or eligible Microsoft Entra roles.
- Investigate the decisions that are applied to access reviews.
- Generate an access review history report

## Prerequisites

To complete this tutorial, you need these resources and privileges:

- A working Microsoft Entra tenant with a Microsoft Entra ID P2 or Microsoft Entra ID Governance license enabled.
- Sign in to an API client such as [Graph Explorer](https://aka.ms/ge) to call Microsoft Graph with an account that has at least the *Identity Governance Administrator* role.
- Principals, such as a security group and an individual user, with active or eligible assignments to a Microsoft Entra role, such as the *User Administrator* role. Their assignments are the scope of your access review. To assign administrative roles, see [Tutorial: Use the Privileged Identity Management \(PIM\) API to assign Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/tutorial-assign-azureadroles).
- Grant yourself the following delegated permissions: `AccessReview.ReadWrite.All`.

## Step 1: Create an access review of role assignments

The following access review schedule definition has theese settings:

- The review scope is groups and users \(**principalScopes** property\) with access to the User Administrator role.

  - An access review can be scoped to multiple principal types \(users and groups, or service principals\) and *only one* resource. To review access to multiple Microsoft Entra roles, create separate access reviews.
  - roleDefinitionId `fe930be7-5e62-47db-91af-98c3a49a38b1` is the global template identifier for the Microsoft Entra *User Administrator* role.

- Both active and eligible assignments to the User Administrator role are in review.
- The reviewer is an individual user. You can assign yourself as the reviewer.
- The approver must provide justification before they approve access to the Microsoft Entra role.
- The default decision is `None` when the reviewers don't respond to the access review request before the instance expires.
- **autoApplyDecisionsEnabled** isn't set and defaults to `false`. In this case, after the review completes, the decisions aren't automatically applied so you must manually apply them.
- The review recurs every three months over three days and doesn't end.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions
Content-type: application/json

{
    "displayName": "Review access of users and groups to privileged roles",
    "descriptionForAdmins": "Review access of users and groups to privileged roles",
    "scope": {
        "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
        "principalScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/users",
                "queryType": "MicrosoftGraph"
            },
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/groups",
                "queryType": "MicrosoftGraph"
            }
        ],
        "resourceScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1",
                "queryType": "MicrosoftGraph"
            }
        ]
    },
    "reviewers": [
        {
            "query": "/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8",
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
        "recommendationsEnabled": false,
        "recurrence": {
            "pattern": {
                "type": "absoluteMonthly",
                "interval": 3
            },
            "range": {
                "type": "noEnd",
                "startDate": "2024-03-25"
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
	DisplayName = "Review access of users and groups to privileged roles",
	DescriptionForAdmins = "Review access of users and groups to privileged roles",
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
			new AccessReviewQueryScope
			{
				OdataType = "#microsoft.graph.accessReviewQueryScope",
				Query = "/groups",
				QueryType = "MicrosoftGraph",
			},
		},
		ResourceScopes = new List<AccessReviewScope>
		{
			new AccessReviewQueryScope
			{
				OdataType = "#microsoft.graph.accessReviewQueryScope",
				Query = "/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1",
				QueryType = "MicrosoftGraph",
			},
		},
	},
	Reviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8",
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
		RecommendationsEnabled = false,
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				Type = RecurrencePatternType.AbsoluteMonthly,
				Interval = 3,
			},
			Range = new RecurrenceRange
			{
				Type = RecurrenceRangeType.NoEnd,
				StartDate = new Date(DateTime.Parse("2024-03-25")),
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
displayName := "Review access of users and groups to privileged roles"
requestBody.SetDisplayName(&displayName) 
descriptionForAdmins := "Review access of users and groups to privileged roles"
requestBody.SetDescriptionForAdmins(&descriptionForAdmins) 
scope := graphmodels.NewPrincipalResourceMembershipsScope()


accessReviewScope := graphmodels.NewAccessReviewQueryScope()
query := "/users"
accessReviewScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewScope.SetQueryType(&queryType) 
accessReviewScope1 := graphmodels.NewAccessReviewQueryScope()
query := "/groups"
accessReviewScope1.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewScope1.SetQueryType(&queryType) 

principalScopes := []graphmodels.AccessReviewScopeable {
	accessReviewScope,
	accessReviewScope1,
}
scope.SetPrincipalScopes(principalScopes)


accessReviewScope := graphmodels.NewAccessReviewQueryScope()
query := "/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1"
accessReviewScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewScope.SetQueryType(&queryType) 

resourceScopes := []graphmodels.AccessReviewScopeable {
	accessReviewScope,
}
scope.SetResourceScopes(resourceScopes)
requestBody.SetScope(scope)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8"
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
recommendationsEnabled := false
settings.SetRecommendationsEnabled(&recommendationsEnabled) 
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.ABSOLUTEMONTHLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(3)
pattern.SetInterval(&interval) 
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
startDate := 2024-03-25
range.SetStartDate(&startDate) 
recurrence.SetRange(range)
settings.SetRecurrence(recurrence)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
definitions, err := graphClient.IdentityGovernance().AccessReviews().Definitions().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setDisplayName("Review access of users and groups to privileged roles");
accessReviewScheduleDefinition.setDescriptionForAdmins("Review access of users and groups to privileged roles");
PrincipalResourceMembershipsScope scope = new PrincipalResourceMembershipsScope();
scope.setOdataType("#microsoft.graph.principalResourceMembershipsScope");
LinkedList<AccessReviewScope> principalScopes = new LinkedList<AccessReviewScope>();
AccessReviewQueryScope accessReviewScope = new AccessReviewQueryScope();
accessReviewScope.setOdataType("#microsoft.graph.accessReviewQueryScope");
accessReviewScope.setQuery("/users");
accessReviewScope.setQueryType("MicrosoftGraph");
principalScopes.add(accessReviewScope);
AccessReviewQueryScope accessReviewScope1 = new AccessReviewQueryScope();
accessReviewScope1.setOdataType("#microsoft.graph.accessReviewQueryScope");
accessReviewScope1.setQuery("/groups");
accessReviewScope1.setQueryType("MicrosoftGraph");
principalScopes.add(accessReviewScope1);
scope.setPrincipalScopes(principalScopes);
LinkedList<AccessReviewScope> resourceScopes = new LinkedList<AccessReviewScope>();
AccessReviewQueryScope accessReviewScope2 = new AccessReviewQueryScope();
accessReviewScope2.setOdataType("#microsoft.graph.accessReviewQueryScope");
accessReviewScope2.setQuery("/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1");
accessReviewScope2.setQueryType("MicrosoftGraph");
resourceScopes.add(accessReviewScope2);
scope.setResourceScopes(resourceScopes);
accessReviewScheduleDefinition.setScope(scope);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setQuery("/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8");
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
settings.setRecommendationsEnabled(false);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.AbsoluteMonthly);
pattern.setInterval(3);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
LocalDate startDate = LocalDate.parse("2024-03-25");
range.setStartDate(startDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
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
    displayName: 'Review access of users and groups to privileged roles',
    descriptionForAdmins: 'Review access of users and groups to privileged roles',
    scope: {
        '@odata.type': '#microsoft.graph.principalResourceMembershipsScope',
        principalScopes: [
            {
                '@odata.type': '#microsoft.graph.accessReviewQueryScope',
                query: '/users',
                queryType: 'MicrosoftGraph'
            },
            {
                '@odata.type': '#microsoft.graph.accessReviewQueryScope',
                query: '/groups',
                queryType: 'MicrosoftGraph'
            }
        ],
        resourceScopes: [
            {
                '@odata.type': '#microsoft.graph.accessReviewQueryScope',
                query: '/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1',
                queryType: 'MicrosoftGraph'
            }
        ]
    },
    reviewers: [
        {
            query: '/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8',
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
        recommendationsEnabled: false,
        recurrence: {
            pattern: {
                type: 'absoluteMonthly',
                interval: 3
            },
            range: {
                type: 'noEnd',
                startDate: '2024-03-25'
            }
        }
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
$requestBody->setDisplayName('Review access of users and groups to privileged roles');
$requestBody->setDescriptionForAdmins('Review access of users and groups to privileged roles');
$scope = new PrincipalResourceMembershipsScope();
$scope->setOdataType('#microsoft.graph.principalResourceMembershipsScope');
$principalScopesAccessReviewScope1 = new AccessReviewQueryScope();
$principalScopesAccessReviewScope1->setOdataType('#microsoft.graph.accessReviewQueryScope');
$principalScopesAccessReviewScope1->setQuery('/users');
$principalScopesAccessReviewScope1->setQueryType('MicrosoftGraph');
$principalScopesArray []= $principalScopesAccessReviewScope1;
$principalScopesAccessReviewScope2 = new AccessReviewQueryScope();
$principalScopesAccessReviewScope2->setOdataType('#microsoft.graph.accessReviewQueryScope');
$principalScopesAccessReviewScope2->setQuery('/groups');
$principalScopesAccessReviewScope2->setQueryType('MicrosoftGraph');
$principalScopesArray []= $principalScopesAccessReviewScope2;
$scope->setPrincipalScopes($principalScopesArray);

$resourceScopesAccessReviewScope1 = new AccessReviewQueryScope();
$resourceScopesAccessReviewScope1->setOdataType('#microsoft.graph.accessReviewQueryScope');
$resourceScopesAccessReviewScope1->setQuery('/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1');
$resourceScopesAccessReviewScope1->setQueryType('MicrosoftGraph');
$resourceScopesArray []= $resourceScopesAccessReviewScope1;
$scope->setResourceScopes($resourceScopesArray);

$requestBody->setScope($scope);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8');
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
$settings->setRecommendationsEnabled(false);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('absoluteMonthly'));
$settingsRecurrencePattern->setInterval(3);
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$settingsRecurrenceRange->setStartDate(new Date('2024-03-25'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$requestBody->setSettings($settings);

$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Review access of users and groups to privileged roles"
	descriptionForAdmins = "Review access of users and groups to privileged roles"
	scope = @{
		"@odata.type" = "#microsoft.graph.principalResourceMembershipsScope"
		principalScopes = @(
			@{
				"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
				query = "/users"
				queryType = "MicrosoftGraph"
			}
			@{
				"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
				query = "/groups"
				queryType = "MicrosoftGraph"
			}
		)
		resourceScopes = @(
			@{
				"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
				query = "/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1"
				queryType = "MicrosoftGraph"
			}
		)
	}
	reviewers = @(
		@{
			query = "/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8"
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
		recommendationsEnabled = $false
		recurrence = @{
			pattern = @{
				type = "absoluteMonthly"
				interval = 3
			}
			range = @{
				type = "noEnd"
				startDate = "2024-03-25"
			}
		}
	}
}

New-MgIdentityGovernanceAccessReviewDefinition -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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
	display_name = "Review access of users and groups to privileged roles",
	description_for_admins = "Review access of users and groups to privileged roles",
	scope = PrincipalResourceMembershipsScope(
		odata_type = "#microsoft.graph.principalResourceMembershipsScope",
		principal_scopes = [
			AccessReviewQueryScope(
				odata_type = "#microsoft.graph.accessReviewQueryScope",
				query = "/users",
				query_type = "MicrosoftGraph",
			),
			AccessReviewQueryScope(
				odata_type = "#microsoft.graph.accessReviewQueryScope",
				query = "/groups",
				query_type = "MicrosoftGraph",
			),
		],
		resource_scopes = [
			AccessReviewQueryScope(
				odata_type = "#microsoft.graph.accessReviewQueryScope",
				query = "/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1",
				query_type = "MicrosoftGraph",
			),
		],
	),
	reviewers = [
		AccessReviewReviewerScope(
			query = "/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8",
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
		recommendations_enabled = False,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.AbsoluteMonthly,
				interval = 3,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.NoEnd,
				start_date = "2024-03-25",
			),
		),
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
    "id": "02800b79-1a6f-40b7-8381-c0bebc3763bd",
    "displayName": "Review access of users and groups to privileged roles",
    "status": "NotStarted",
    "descriptionForAdmins": "Review access of users and groups to privileged roles",
    "scope": {
        "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
        "principalScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/users",
                "queryType": "MicrosoftGraph"
            },
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/groups",
                "queryType": "MicrosoftGraph"
            }
        ],
        "resourceScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                "query": "/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1",
                "queryType": "MicrosoftGraph"
            }
        ]
    },
    "reviewers": [
        {
            "query": "/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8",
            "queryType": "MicrosoftGraph"
        }
    ],
    "fallbackReviewers": [],
    "settings": {
        "mailNotificationsEnabled": true,
        "reminderNotificationsEnabled": true,
        "justificationRequiredOnApproval": true,
        "defaultDecisionEnabled": false,
        "defaultDecision": "None",
        "instanceDurationInDays": 1,
        "autoApplyDecisionsEnabled": false,
        "recommendationsEnabled": false,
        "recommendationLookBackDuration": null,
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
                "type": "noEnd",
                "numberOfOccurrences": 0,
                "recurrenceTimeZone": null,
                "startDate": "2024-03-25",
                "endDate": null
            }
        },
        "applyActions": [],
        "recommendationInsightSettings": []
    },
    "stageSettings": [],
    "additionalNotificationRecipients": []
}
```

## Step 2: Retrieve instances of the access review

Each access review instance represents *each recurrence with each unique resource* that is under review. Because you defined a recurring access review, the ID of the instance is different from the ID of the schedule definition in Step 1.

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
GET https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances
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

let instances = await client.api('/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances')
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

The status of this access review instance is `InProgress`, meaning the review instance is open for reviewers to submit decisions, and the period for this access review instance hasn't expired. You also received an email notification from Microsoft Azure requesting you to perform the access review.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions('02800b79-1a6f-40b7-8381-c0bebc3763bd')/instances",
    "@odata.count": 1,
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/accessReviews/definitions('<guid>')/instances?$select=endDateTime,fallbackReviewers",
    "value": [
        {
            "id": "30f0cb53-da42-402e-8be5-9005f9c374f7",
            "startDateTime": "2024-03-25T09:38:15.177Z",
            "endDateTime": "2024-03-26T09:38:15.177Z",
            "status": "InProgress",
            "scope": {
                "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
                "principalScopes": [
                    {
                        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                        "query": "/v1.0/users",
                        "queryType": "MicrosoftGraph"
                    },
                    {
                        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                        "query": "/v1.0/groups",
                        "queryType": "MicrosoftGraph"
                    }
                ],
                "resourceScopes": [
                    {
                        "@odata.type": "#microsoft.graph.accessReviewQueryScope",
                        "query": "/beta/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1",
                        "queryType": "MicrosoftGraph"
                    }
                ]
            },
            "reviewers": [
                {
                    "query": "/v1.0/users/2560f739-2e0e-4550-9fa0-1a1e67ae0ab8",
                    "queryType": "MicrosoftGraph"
                }
            ],
            "fallbackReviewers": []
        }
    ]
}
```

## Step 3: Retrieve access review decisions before recording any decisions

Before you can post decisions, let's first inspect the items waiting for your decision.

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
GET https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/decisions
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

let decisions = await client.api('/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/decisions')
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

The following response shows two decision items each corresponding to a decision required for each principal's access to the resource. Because recommendations weren't enabled in Step 1, no recommendations are available. As the reviewer, you can now submit your decisions for the access review instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/definitions('02800b79-1a6f-40b7-8381-c0bebc3763bd')/instances('30f0cb53-da42-402e-8be5-9005f9c374f7')/decisions",
    "@odata.count": 2,
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/accessReviews/definitions('<guid>')/instances('<guid>')/decisions?$select=accessReviewId,appliedBy",
    "value": [
        {
            "id": "25bf64c2-2396-4efc-9bb8-e9dc39ee0441",
            "accessReviewId": "30f0cb53-da42-402e-8be5-9005f9c374f7",
            "decision": "NotReviewed",
            "applyResult": "New",
            "recommendation": "NoInfoAvailable",
            "principalLink": "https://graph.microsoft.com/v1.0/users/ad20a697-7be8-410a-bb08-207a21e6400d",
            "resourceLink": "https://graph.microsoft.com/beta/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1",
            "reviewedBy": {
                "id": "00000000-0000-0000-0000-000000000000",
                "displayName": "",
                "type": null,
                "userPrincipalName": ""
            },
            "appliedBy": {
                "id": "00000000-0000-0000-0000-000000000000",
                "displayName": "",
                "type": null,
                "userPrincipalName": ""
            },
            "resource": {
                "id": "fe930be7-5e62-47db-91af-98c3a49a38b1",
                "displayName": "User Administrator",
                "type": "directoryRole"
            },
            "principal": {
                "@odata.type": "#microsoft.graph.userIdentity",
                "id": "ad20a697-7be8-410a-bb08-207a21e6400d",
                "displayName": "Adele Vance",
                "type": "user",
                "userPrincipalName": "AdeleV@contoso.com",
                "lastUserSignInDateTime": ""
            }
        },
        {
            "id": "888007fa-1d32-4000-a359-fd1d5876a3ed",
            "accessReviewId": "30f0cb53-da42-402e-8be5-9005f9c374f7",
            "decision": "NotReviewed",
            "applyResult": "New",
            "recommendation": "NoInfoAvailable",
            "principalLink": "https://graph.microsoft.com/v1.0/groups/df434df5-5b8e-4044-9fa3-ac9d6ea45156",
            "resourceLink": "https://graph.microsoft.com/beta/roleManagement/directory/roleDefinitions/fe930be7-5e62-47db-91af-98c3a49a38b1",
            "reviewedBy": {
                "id": "00000000-0000-0000-0000-000000000000",
                "displayName": "",
                "type": null,
                "userPrincipalName": ""
            },
            "appliedBy": {
                "id": "00000000-0000-0000-0000-000000000000",
                "displayName": "",
                "type": null,
                "userPrincipalName": ""
            },
            "resource": {
                "id": "fe930be7-5e62-47db-91af-98c3a49a38b1",
                "displayName": "User Administrator",
                "type": "directoryRole"
            },
            "principal": {
                "id": "df434df5-5b8e-4044-9fa3-ac9d6ea45156",
                "displayName": "User Administrators",
                "type": "group"
            }
        }
    ]
}
```

## Step 4: Record decisions

Assume that the company policy requires that access to administrative roles be granted through security groups and not directly to individual principals. In compliance with the company policy, you post a decision to deny Adele Vance access while approving access for the group.

### Approve the security group's role assignment

In the following request, you approve access for the IT Helpdesk group. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/decisions/888007fa-1d32-4000-a359-fd1d5876a3ed
Content-type: application/json

{
    "decision": "Approve",
    "justification": "The IT Helpdesk requires continued access to the User Administrator role to manage user account support requests, lifecycle, and access to resources"
}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewInstanceDecisionItem = {
    decision: 'Approve',
    justification: 'The IT Helpdesk requires continued access to the User Administrator role to manage user account support requests, lifecycle, and access to resources'
};

await client.api('/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/decisions/888007fa-1d32-4000-a359-fd1d5876a3ed')
	.post(accessReviewInstanceDecisionItem);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

### Deny the individual user their role assignment

In the following request, you deny access for Adele Vance. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/decisions/25bf64c2-2396-4efc-9bb8-e9dc39ee0441
Content-type: application/json

{
    "decision": "Deny",
    "justification": "Adele should join an allowed group to maintain access to the User Administrator role. For more details, refer to the company policy '#132487: Administrative roles'"
}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewInstanceDecisionItem = {
    decision: 'Deny',
    justification: 'Adele should join an allowed group to maintain access to the User Administrator role. For more details, refer to the company policy \'#132487: Administrative roles\''
};

await client.api('/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/decisions/25bf64c2-2396-4efc-9bb8-e9dc39ee0441')
	.post(accessReviewInstanceDecisionItem);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

When you retrieve the access review decisions \(repeat Step 3\), they have the following settings:

- The access review decision for the IT Helpdesk group is `Approve` while for Adele is `Deny`.
- The reviewedBy object contains your details as the reviewer.
- **applyResult** is `New` meaning the decisions haven't been applied.

While you recorded all the pending decisions for this instance, the decisions haven't been applied to the resource and principal objects. For example, Adele still has User Administrator privileges. You can verify this assignment by running the following query `https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignments?$filter=roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'`. This behavior is because the **autoApplyDecisionsEnabled** was set to `false`, you haven't stopped the review, or the instance period hasn't ended.

In this tutorial, you won't stop the instance manually, but you let it end automatically and then apply the decisions.

Tip

1. Until the **status** of the access review instance is marked as `Completed`, you can still change the decisions. Rerun step 4 to apply different decisions for the principals.
2. You can also manually stop the access review instance so that you can expedite your progress to Step 5.

## Step 5: Apply access review decisions

As an admin, after the **status** of the access review instance is set to `Completed`, you can apply the decisions. The request returns a `204 No Content` response code.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/applyDecisions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.AccessReviews.Definitions["{accessReviewScheduleDefinition-id}"].Instances["{accessReviewInstance-id}"].ApplyDecisions.PostAsync();
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
graphClient.IdentityGovernance().AccessReviews().Definitions().ByAccessReviewScheduleDefinitionId("accessReviewScheduleDefinition-id").Instances().ByAccessReviewInstanceId("accessReviewInstance-id").ApplyDecisions().Post(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.identityGovernance().accessReviews().definitions().byAccessReviewScheduleDefinitionId("{accessReviewScheduleDefinition-id}").instances().byAccessReviewInstanceId("{accessReviewInstance-id}").applyDecisions().post();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd/instances/30f0cb53-da42-402e-8be5-9005f9c374f7/applyDecisions')
	.post();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->identityGovernance()->accessReviews()->definitions()->byAccessReviewScheduleDefinitionId('accessReviewScheduleDefinition-id')->instances()->byAccessReviewInstanceId('accessReviewInstance-id')->applyDecisions()->post()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Identity.Governance

Add-MgIdentityGovernanceAccessReviewDefinitionInstanceDecision -AccessReviewScheduleDefinitionId $accessReviewScheduleDefinitionId -AccessReviewInstanceId $accessReviewInstanceId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.identity_governance.access_reviews.definitions.by_access_review_schedule_definition_id('accessReviewScheduleDefinition-id').instances.by_access_review_instance_id('accessReviewInstance-id').apply_decisions.post()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Adele has lost access to the User Administrator role while the IT Helpdesk group has maintained its access. You can verify this state of role assignment by running the following query ` GET https://graph.microsoft.com/v1.0/roleManagement/directory/roleAssignments?$filter=roleDefinitionId eq 'fe930be7-5e62-47db-91af-98c3a49a38b1'`.

The **status** of the access review instance is now `Applied`. Also, because the access review is recurring, a new instance is immediately created. Its start date is three months from the **endDateTime** of the current review instance.

## Step 6: Retrieve access review history definitions

Contoso's auditors also want to review the access review history for the last quarter. In this example, you generate an access review history report for all **accessReviewScheduleDefinition** objects scoped to directory role assignments \(roleAssignmentScheduleInstances\). This query includes access reviews with all decisions in the history report.

First, you define the scope of the history report. Then, you generate a download URI that the auditors use to download the report. The download URI is active for only 24 hours. So, after expiry, you can regenerate another download URI from the previously defined history report.

### Define the scope of the access review history data

#### Request

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/historyDefinitions

{
    "displayName": "Last quarter's access reviews for administrative roles - User Administrator",
    "decisions": [],
    "reviewHistoryPeriodStartDateTime": "2024-03-24T00:00:00Z",
    "reviewHistoryPeriodEndDateTime": "9999-12-31T00:00:00Z",
    "scopes": [
        {
            "@odata.type": "#microsoft.graph.accessReviewQueryScope",
            "queryType": "MicrosoftGraph",
            "query": "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'roleAssignmentScheduleInstances')"
        }
    ]
}
```

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/historyDefinitions/$entity",
    "id": "841fc5d5-b89e-42cd-9f76-3343689aaabf",
    "displayName": "Last quarter's access reviews for administrative roles - User Administrator",
    "reviewHistoryPeriodStartDateTime": "2024-03-24T00:00:00Z",
    "reviewHistoryPeriodEndDateTime": "9999-12-31T00:00:00Z",
    "decisions": [
        "approve",
        "deny",
        "dontKnow",
        "notReviewed",
        "notNotified"
    ],
    "status": "requested",
    "createdDateTime": "2024-03-25T17:15:45.1940174Z",
    "createdBy": {
        "id": "2560f739-2e0e-4550-9fa0-1a1e67ae0ab8",
        "displayName": "MOD Administrator",
        "type": null,
        "userPrincipalName": "admin@contoso.com"
    },
    "scopes": [
        {
            "@odata.type": "#microsoft.graph.accessReviewQueryScope",
            "query": "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'roleAssignmentScheduleInstances')",
            "queryType": "MicrosoftGraph",
            "queryRoot": null
        }
    ]
}
```

### Retrieve the instances of the access review history

#### Request

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/historyDefinitions/841fc5d5-b89e-42cd-9f76-3343689aaabf/instances
```

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#identityGovernance/accessReviews/historyDefinitions('841fc5d5-b89e-42cd-9f76-3343689aaabf')/instances",
    "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET identityGovernance/accessReviews/historyDefinitions('<guid>')/instances?$select=downloadUri,expirationDateTime",
    "value": [
        {
            "id": "841fc5d5-b89e-42cd-9f76-3343689aaabf",
            "reviewHistoryPeriodStartDateTime": "2024-03-24T00:00:00Z",
            "reviewHistoryPeriodEndDateTime": "9999-12-31T00:00:00Z",
            "status": "done",
            "runDateTime": "2024-03-25T17:15:45.1940174Z",
            "fulfilledDateTime": "2024-03-25T17:16:06.5812358Z",
            "downloadUri": null
        }
    ]
}
```

### Generate a link to download the history report from the instance of the access review history

#### Request

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/historyDefinitions/841fc5d5-b89e-42cd-9f76-3343689aaabf/instances/841fc5d5-b89e-42cd-9f76-3343689aaabf/microsoft.graph.generateDownloadUri
```

#### Response

The **downloadUri** property contains a link to download the history report in an Excel file format. This link is active for only 24 hours.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.accessReviewHistoryInstance",
    "id": "841fc5d5-b89e-42cd-9f76-3343689aaabf",
    "reviewHistoryPeriodStartDateTime": "2024-03-24T00:00:00Z",
    "reviewHistoryPeriodEndDateTime": "9999-12-31T00:00:00Z",
    "status": "done",
    "runDateTime": "2024-03-25T17:15:45.1940174Z",
    "fulfilledDateTime": "2024-03-25T17:16:06.5812358Z",
    "downloadUri": "https://ermconsolreportusc.blob.core.windows.net/erm-reports/Last quarter's access reviews for administrative roles - User Administrator-841fc5d5-b89e-42cd-9f76-3343689aaabf.csv?skoid=4ad0868b-7b78-4869-abb7-8f29151d8428&sktid=33e01921-4d64-4f8c-a055-5bdaffd5e33d&skt=2024-03-25T17:17:40Z&ske=2024-03-25T17:19:40Z&sks=b&skv=2021-08-06&sv=2021-08-06&st=2024-03-25T17:17:40Z&se=2024-03-26T17:17:40Z&sr=b&sp=r&sig=g%2BlQj2PxFG1lAYDuUt5VWO8tvLPQebA7GLnqz%2FQb%2BbQ%3D"
}
```

## Step 7: Clean up resources

In this step, you delete the access review definition. Since the access review schedule definition is the blueprint for the access review, deleting the definition removes the related settings, instances, and decisions. The request returns a `204 No Content` response.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
DELETE https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd
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

await client.api('/identityGovernance/accessReviews/definitions/02800b79-1a6f-40b7-8381-c0bebc3763bd')
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

## Conclusion

You learned how to review access to administrative roles and generate an auditable access review history report for compliance reporting. Your organization can use the access reviews APIs to continually govern privileged access to its resources, including both Microsoft Entra roles and Azure resource roles. In addition to users and groups, you can also review access by applications and service principals to administrative roles.

## Related content

- [Access reviews API Reference](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview)
- [Configure the scope of your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept)
