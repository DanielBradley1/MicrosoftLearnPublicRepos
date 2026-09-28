<!-- Source: https://learn.microsoft.com/en-us/graph/api/unifiedroot-post-definitions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Create accessReviewScheduleDefinition

Namespace: microsoft.graph

Create a new user-centric \(catalog-scope\) [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object through the [unified](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroot?view=graph-rest-1.0) route. With a user-centric review, a reviewer evaluates a principal's access to every group and application contained in an [entitlement management catalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) in a single review. The catalog is identified in the **resourceScopes** collection of the [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AccessReview.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AccessReview.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- To write access reviews of a group or app: *User Administrator*, *Identity Governance Administrator*
- To write access reviews of a Microsoft Entra role: *Identity Governance Administrator*, *Privileged Role Administrator*

## HTTP request

```http
POST /identityGovernance/accessReviews/unified/definitions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. Set the **scope** to a [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0) whose **resourceScopes** collection contains a resource scope of `scopeType` `catalog` that identifies the catalog to review.

## Response

If successful, this method returns a `201 Created` response code and an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create a user-centric \(catalog\) access review definition

The following example creates a review in which the managers of all users review those users' access to every group and application contained in a catalog.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/unified/definitions
Content-type: application/json

{
    "displayName": "Catalog access review",
    "descriptionForAdmins": "Quarterly user-centric review of catalog resources",
    "scope": {
        "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
        "principalScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewPrincipalScope",
                "scopeType": "allUsers"
            }
        ],
        "resourceScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewResourceScope",
                "resourceId": "c6010d0c-ff41-4929-9776-fa03a03dd5ac",
                "scopeType": "catalog"
            }
        ]
    },
    "reviewers": [
        {
            "@odata.type": "#microsoft.graph.accessReviewReviewerScope",
            "scopeType": "manager"
        }
    ],
    "settings": {
        "mailNotificationsEnabled": true,
        "reminderNotificationsEnabled": true,
        "justificationRequiredOnApproval": true,
        "instanceDurationInDays": 6,
        "recommendationsEnabled": true,
        "recurrence": {
            "pattern": {
                "type": "absoluteMonthly",
                "interval": 1
            },
            "range": {
                "type": "noEnd",
                "startDate": "2026-08-31"
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
	DisplayName = "Catalog access review",
	DescriptionForAdmins = "Quarterly user-centric review of catalog resources",
	Scope = new PrincipalResourceMembershipsScope
	{
		OdataType = "#microsoft.graph.principalResourceMembershipsScope",
		PrincipalScopes = new List<AccessReviewScope>
		{
			new AccessReviewPrincipalScope
			{
				OdataType = "#microsoft.graph.accessReviewPrincipalScope",
				ScopeType = AccessReviewPrincipalScopeType.AllUsers,
			},
		},
		ResourceScopes = new List<AccessReviewScope>
		{
			new AccessReviewResourceScope
			{
				OdataType = "#microsoft.graph.accessReviewResourceScope",
				ResourceId = "c6010d0c-ff41-4929-9776-fa03a03dd5ac",
				ScopeType = AccessReviewResourceScopeType.Catalog,
			},
		},
	},
	Reviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			OdataType = "#microsoft.graph.accessReviewReviewerScope",
			ScopeType = AccessReviewReviewerScopeType.Manager,
		},
	},
	Settings = new AccessReviewScheduleSettings
	{
		MailNotificationsEnabled = true,
		ReminderNotificationsEnabled = true,
		JustificationRequiredOnApproval = true,
		InstanceDurationInDays = 6,
		RecommendationsEnabled = true,
		Recurrence = new PatternedRecurrence
		{
			Pattern = new RecurrencePattern
			{
				Type = RecurrencePatternType.AbsoluteMonthly,
				Interval = 1,
			},
			Range = new RecurrenceRange
			{
				Type = RecurrenceRangeType.NoEnd,
				StartDate = new Date(DateTime.Parse("2026-08-31")),
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Unified.Definitions.PostAsync(requestBody);
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
displayName := "Catalog access review"
requestBody.SetDisplayName(&displayName) 
descriptionForAdmins := "Quarterly user-centric review of catalog resources"
requestBody.SetDescriptionForAdmins(&descriptionForAdmins) 
scope := graphmodels.NewPrincipalResourceMembershipsScope()


accessReviewScope := graphmodels.NewAccessReviewPrincipalScope()
scopeType := graphmodels.ALLUSERS_ACCESSREVIEWPRINCIPALSCOPETYPE 
accessReviewScope.SetScopeType(&scopeType) 

principalScopes := []graphmodels.AccessReviewScopeable {
	accessReviewScope,
}
scope.SetPrincipalScopes(principalScopes)


accessReviewScope := graphmodels.NewAccessReviewResourceScope()
resourceId := "c6010d0c-ff41-4929-9776-fa03a03dd5ac"
accessReviewScope.SetResourceId(&resourceId) 
scopeType := graphmodels.CATALOG_ACCESSREVIEWRESOURCESCOPETYPE 
accessReviewScope.SetScopeType(&scopeType) 

resourceScopes := []graphmodels.AccessReviewScopeable {
	accessReviewScope,
}
scope.SetResourceScopes(resourceScopes)
requestBody.SetScope(scope)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
scopeType := graphmodels.MANAGER_ACCESSREVIEWREVIEWERSCOPETYPE 
accessReviewReviewerScope.SetScopeType(&scopeType) 

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
instanceDurationInDays := int32(6)
settings.SetInstanceDurationInDays(&instanceDurationInDays) 
recommendationsEnabled := true
settings.SetRecommendationsEnabled(&recommendationsEnabled) 
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.ABSOLUTEMONTHLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(1)
pattern.SetInterval(&interval) 
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
startDate := 2026-08-31
range.SetStartDate(&startDate) 
recurrence.SetRange(range)
settings.SetRecurrence(recurrence)
requestBody.SetSettings(settings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
definitions, err := graphClient.IdentityGovernance().AccessReviews().Unified().Definitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewScheduleDefinition accessReviewScheduleDefinition = new AccessReviewScheduleDefinition();
accessReviewScheduleDefinition.setDisplayName("Catalog access review");
accessReviewScheduleDefinition.setDescriptionForAdmins("Quarterly user-centric review of catalog resources");
PrincipalResourceMembershipsScope scope = new PrincipalResourceMembershipsScope();
scope.setOdataType("#microsoft.graph.principalResourceMembershipsScope");
LinkedList<AccessReviewScope> principalScopes = new LinkedList<AccessReviewScope>();
AccessReviewPrincipalScope accessReviewScope = new AccessReviewPrincipalScope();
accessReviewScope.setOdataType("#microsoft.graph.accessReviewPrincipalScope");
accessReviewScope.setScopeType(AccessReviewPrincipalScopeType.AllUsers);
principalScopes.add(accessReviewScope);
scope.setPrincipalScopes(principalScopes);
LinkedList<AccessReviewScope> resourceScopes = new LinkedList<AccessReviewScope>();
AccessReviewResourceScope accessReviewScope1 = new AccessReviewResourceScope();
accessReviewScope1.setOdataType("#microsoft.graph.accessReviewResourceScope");
accessReviewScope1.setResourceId("c6010d0c-ff41-4929-9776-fa03a03dd5ac");
accessReviewScope1.setScopeType(AccessReviewResourceScopeType.Catalog);
resourceScopes.add(accessReviewScope1);
scope.setResourceScopes(resourceScopes);
accessReviewScheduleDefinition.setScope(scope);
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setOdataType("#microsoft.graph.accessReviewReviewerScope");
accessReviewReviewerScope.setScopeType(AccessReviewReviewerScopeType.Manager);
reviewers.add(accessReviewReviewerScope);
accessReviewScheduleDefinition.setReviewers(reviewers);
AccessReviewScheduleSettings settings = new AccessReviewScheduleSettings();
settings.setMailNotificationsEnabled(true);
settings.setReminderNotificationsEnabled(true);
settings.setJustificationRequiredOnApproval(true);
settings.setInstanceDurationInDays(6);
settings.setRecommendationsEnabled(true);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.AbsoluteMonthly);
pattern.setInterval(1);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
LocalDate startDate = LocalDate.parse("2026-08-31");
range.setStartDate(startDate);
recurrence.setRange(range);
settings.setRecurrence(recurrence);
accessReviewScheduleDefinition.setSettings(settings);
AccessReviewScheduleDefinition result = graphClient.identityGovernance().accessReviews().unified().definitions().post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewScheduleDefinition = {
    displayName: 'Catalog access review',
    descriptionForAdmins: 'Quarterly user-centric review of catalog resources',
    scope: {
        '@odata.type': '#microsoft.graph.principalResourceMembershipsScope',
        principalScopes: [
            {
                '@odata.type': '#microsoft.graph.accessReviewPrincipalScope',
                scopeType: 'allUsers'
            }
        ],
        resourceScopes: [
            {
                '@odata.type': '#microsoft.graph.accessReviewResourceScope',
                resourceId: 'c6010d0c-ff41-4929-9776-fa03a03dd5ac',
                scopeType: 'catalog'
            }
        ]
    },
    reviewers: [
        {
            '@odata.type': '#microsoft.graph.accessReviewReviewerScope',
            scopeType: 'manager'
        }
    ],
    settings: {
        mailNotificationsEnabled: true,
        reminderNotificationsEnabled: true,
        justificationRequiredOnApproval: true,
        instanceDurationInDays: 6,
        recommendationsEnabled: true,
        recurrence: {
            pattern: {
                type: 'absoluteMonthly',
                interval: 1
            },
            range: {
                type: 'noEnd',
                startDate: '2026-08-31'
            }
        }
    }
};

await client.api('/identityGovernance/accessReviews/unified/definitions')
	.post(accessReviewScheduleDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleDefinition;
use Microsoft\Graph\Generated\Models\PrincipalResourceMembershipsScope;
use Microsoft\Graph\Generated\Models\AccessReviewScope;
use Microsoft\Graph\Generated\Models\AccessReviewPrincipalScope;
use Microsoft\Graph\Generated\Models\AccessReviewPrincipalScopeType;
use Microsoft\Graph\Generated\Models\AccessReviewResourceScope;
use Microsoft\Graph\Generated\Models\AccessReviewResourceScopeType;
use Microsoft\Graph\Generated\Models\AccessReviewReviewerScope;
use Microsoft\Graph\Generated\Models\AccessReviewReviewerScopeType;
use Microsoft\Graph\Generated\Models\AccessReviewScheduleSettings;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewScheduleDefinition();
$requestBody->setDisplayName('Catalog access review');
$requestBody->setDescriptionForAdmins('Quarterly user-centric review of catalog resources');
$scope = new PrincipalResourceMembershipsScope();
$scope->setOdataType('#microsoft.graph.principalResourceMembershipsScope');
$principalScopesAccessReviewScope1 = new AccessReviewPrincipalScope();
$principalScopesAccessReviewScope1->setOdataType('#microsoft.graph.accessReviewPrincipalScope');
$principalScopesAccessReviewScope1->setScopeType(new AccessReviewPrincipalScopeType('allUsers'));
$principalScopesArray []= $principalScopesAccessReviewScope1;
$scope->setPrincipalScopes($principalScopesArray);

$resourceScopesAccessReviewScope1 = new AccessReviewResourceScope();
$resourceScopesAccessReviewScope1->setOdataType('#microsoft.graph.accessReviewResourceScope');
$resourceScopesAccessReviewScope1->setResourceId('c6010d0c-ff41-4929-9776-fa03a03dd5ac');
$resourceScopesAccessReviewScope1->setScopeType(new AccessReviewResourceScopeType('catalog'));
$resourceScopesArray []= $resourceScopesAccessReviewScope1;
$scope->setResourceScopes($resourceScopesArray);

$requestBody->setScope($scope);
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setOdataType('#microsoft.graph.accessReviewReviewerScope');
$reviewersAccessReviewReviewerScope1->setScopeType(new AccessReviewReviewerScopeType('manager'));
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$requestBody->setReviewers($reviewersArray);

$settings = new AccessReviewScheduleSettings();
$settings->setMailNotificationsEnabled(true);
$settings->setReminderNotificationsEnabled(true);
$settings->setJustificationRequiredOnApproval(true);
$settings->setInstanceDurationInDays(6);
$settings->setRecommendationsEnabled(true);
$settingsRecurrence = new PatternedRecurrence();
$settingsRecurrencePattern = new RecurrencePattern();
$settingsRecurrencePattern->setType(new RecurrencePatternType('absoluteMonthly'));
$settingsRecurrencePattern->setInterval(1);
$settingsRecurrence->setPattern($settingsRecurrencePattern);
$settingsRecurrenceRange = new RecurrenceRange();
$settingsRecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$settingsRecurrenceRange->setStartDate(new Date('2026-08-31'));
$settingsRecurrence->setRange($settingsRecurrenceRange);
$settings->setRecurrence($settingsRecurrence);
$requestBody->setSettings($settings);

$result = $graphServiceClient->identityGovernance()->accessReviews()->unified()->definitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_review_schedule_definition import AccessReviewScheduleDefinition
from msgraph.generated.models.principal_resource_memberships_scope import PrincipalResourceMembershipsScope
from msgraph.generated.models.access_review_scope import AccessReviewScope
from msgraph.generated.models.access_review_principal_scope import AccessReviewPrincipalScope
from msgraph.generated.models.access_review_principal_scope_type import AccessReviewPrincipalScopeType
from msgraph.generated.models.access_review_resource_scope import AccessReviewResourceScope
from msgraph.generated.models.access_review_resource_scope_type import AccessReviewResourceScopeType
from msgraph.generated.models.access_review_reviewer_scope import AccessReviewReviewerScope
from msgraph.generated.models.access_review_reviewer_scope_type import AccessReviewReviewerScopeType
from msgraph.generated.models.access_review_schedule_settings import AccessReviewScheduleSettings
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewScheduleDefinition(
	display_name = "Catalog access review",
	description_for_admins = "Quarterly user-centric review of catalog resources",
	scope = PrincipalResourceMembershipsScope(
		odata_type = "#microsoft.graph.principalResourceMembershipsScope",
		principal_scopes = [
			AccessReviewPrincipalScope(
				odata_type = "#microsoft.graph.accessReviewPrincipalScope",
				scope_type = AccessReviewPrincipalScopeType.AllUsers,
			),
		],
		resource_scopes = [
			AccessReviewResourceScope(
				odata_type = "#microsoft.graph.accessReviewResourceScope",
				resource_id = "c6010d0c-ff41-4929-9776-fa03a03dd5ac",
				scope_type = AccessReviewResourceScopeType.Catalog,
			),
		],
	),
	reviewers = [
		AccessReviewReviewerScope(
			odata_type = "#microsoft.graph.accessReviewReviewerScope",
			scope_type = AccessReviewReviewerScopeType.Manager,
		),
	],
	settings = AccessReviewScheduleSettings(
		mail_notifications_enabled = True,
		reminder_notifications_enabled = True,
		justification_required_on_approval = True,
		instance_duration_in_days = 6,
		recommendations_enabled = True,
		recurrence = PatternedRecurrence(
			pattern = RecurrencePattern(
				type = RecurrencePatternType.AbsoluteMonthly,
				interval = 1,
			),
			range = RecurrenceRange(
				type = RecurrenceRangeType.NoEnd,
				start_date = "2026-08-31",
			),
		),
	),
)

result = await graph_client.identity_governance.access_reviews.unified.definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "id": "29f2d16e-9ca6-4052-bbfe-802c48944448",
    "displayName": "Catalog access review",
    "status": "NotStarted",
    "descriptionForAdmins": "Quarterly user-centric review of catalog resources",
    "scope": {
        "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
        "principalScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewPrincipalScope",
                "scopeType": "allUsers"
            }
        ],
        "resourceScopes": [
            {
                "@odata.type": "#microsoft.graph.accessReviewResourceScope",
                "resourceId": "c6010d0c-ff41-4929-9776-fa03a03dd5ac",
                "scopeType": "catalog"
            }
        ]
    },
    "reviewers": [
        {
            "@odata.type": "#microsoft.graph.accessReviewReviewerScope",
            "scopeType": "manager"
        }
    ]
}
```
