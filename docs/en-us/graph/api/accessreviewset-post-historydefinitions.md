<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreviewset-post-historydefinitions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Create historyDefinitions

Namespace: microsoft.graph

Create a new [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object.

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

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- To write access reviews of a group or app: *User Administrator*, *Identity Governance Administrator*
- To write access reviews of a Microsoft Entra role: *Identity Governance Administrator*, *Privileged Role Administrator*

## HTTP request

```http
POST /identityGovernance/accessReviews/historyDefinitions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object.

The following table shows the required properties used to create an [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Name for the access review history data collection. Required. |
| reviewHistoryPeriodStartDateTime | DateTimeOffset | A timestamp. Reviews starting on or after this date will be included in the fetched history data. Only required if **scheduleSettings** isn't defined. |
| reviewHistoryPeriodEndDateTime | DateTimeOffset | A timestamp. Reviews starting on or before this date will be included in the fetched history data. Only required if **scheduleSettings** isn't defined. |
| scopes | [accessReviewQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0) collection | Used to filter which reviews are included in the fetched history data. Fetches reviews whose scope matches with this provided scope. Required.  <br>For more, see [Supported scope queries for accessReviewHistoryDefinition](#supported-scope-queries-for-accessreviewhistorydefinition). |
| scheduleSettings | [accessReviewHistoryScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryschedulesettings?view=graph-rest-1.0) | **Not supported yet.** The settings for a recurring access review history definition series. Only required if **reviewHistoryPeriodStartDateTime** or **reviewHistoryPeriodEndDateTime** aren't defined. |

### Supported scope queries for accessReviewHistoryDefinition

The **scopes** property of [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) is based on **accessReviewQueryScope**, a resource that allows you to configure different resources in it's **query** property. These resources then represent the scope of the history definition and dictate the type of review history data that is included in the downloadable CSV file that is generated when the history definition's [accessReviewHistoryInstances](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) are created.

The `$filter` query parameter with the `contains` operator is supported on the **scope** property of **accessReviewScheduleDefinition**. Use the following format for the request:

```http
/identityGovernance/accessReviews/definitions?$filter=contains(scope/microsoft.graph.accessReviewQueryScope/query, '{object}')
```

The `{object}` can have one of the following values:

| Value | Description |
| :--- | :--- |
| `/groups` | List every accessReviewScheduleDefinition on individual groups \(excludes definitions scoped to all Microsoft 365 groups with guests\). |
| `/groups/{group id}` | List every accessReviewScheduleDefinition on a specific group \(excludes definitions scoped to all Microsoft 365 groups with guests\). |
| `./members` | List every accessReviewScheduleDefinition scoped to all Microsoft 365 groups with guests. |
| `accessPackageAssignments` | List every accessReviewScheduleDefinition on an access package. |
| `roleAssignmentScheduleInstances` | List every accessReviewScheduleDefinition for principals that are assigned to a privileged role. |

The `$filter` query parameter isn't supported on **accessReviewInactiveUserQueryScope** or **principalResourceMembershipScope**.

## Response

If successful, this method returns a `201 Created` response code and an [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object in the response body.

## Examples

The following example shows how to create an access review history definition scoped to access reviews on access packages and groups, running between the start date of 01/01/2021 and end date of 04/05/2021.

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
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/historyDefinitions
Content-Type: application/json

{
  "displayName": "Last quarter's group reviews April 2021",
  "decisions": [
    "approve",
    "deny",
    "dontKnow",
    "notReviewed",
    "notNotified"
  ],
  "reviewHistoryPeriodStartDateTime": "2021-01-01T00:00:00Z",
  "reviewHistoryPeriodEndDateTime": "2021-04-30T23:59:59Z",
  "scopes": [
    {
      "@odata.type": "#microsoft.graph.accessReviewQueryScope",
      "queryType": "MicrosoftGraph",     
      "query": "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'accessPackageAssignments')",
      "queryRoot": null
    },  
    {
      "@odata.type": "#microsoft.graph.accessReviewQueryScope",
      "queryType": "MicrosoftGraph",     
      "query": "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, '/groups')",
      "queryRoot": null
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessReviewHistoryDefinition
{
	DisplayName = "Last quarter's group reviews April 2021",
	Decisions = new List<AccessReviewHistoryDecisionFilter?>
	{
		AccessReviewHistoryDecisionFilter.Approve,
		AccessReviewHistoryDecisionFilter.Deny,
		AccessReviewHistoryDecisionFilter.DontKnow,
		AccessReviewHistoryDecisionFilter.NotReviewed,
		AccessReviewHistoryDecisionFilter.NotNotified,
	},
	ReviewHistoryPeriodStartDateTime = DateTimeOffset.Parse("2021-01-01T00:00:00Z"),
	ReviewHistoryPeriodEndDateTime = DateTimeOffset.Parse("2021-04-30T23:59:59Z"),
	Scopes = new List<AccessReviewScope>
	{
		new AccessReviewQueryScope
		{
			OdataType = "#microsoft.graph.accessReviewQueryScope",
			QueryType = "MicrosoftGraph",
			Query = "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'accessPackageAssignments')",
			QueryRoot = null,
		},
		new AccessReviewQueryScope
		{
			OdataType = "#microsoft.graph.accessReviewQueryScope",
			QueryType = "MicrosoftGraph",
			Query = "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, '/groups')",
			QueryRoot = null,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.HistoryDefinitions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewAccessReviewHistoryDefinition()
displayName := "Last quarter's group reviews April 2021"
requestBody.SetDisplayName(&displayName) 
decisions := []graphmodels.AccessReviewHistoryDecisionFilterable {
	accessReviewHistoryDecisionFilter := graphmodels.APPROVE_ACCESSREVIEWHISTORYDECISIONFILTER 
	requestBody.SetAccessReviewHistoryDecisionFilter(&accessReviewHistoryDecisionFilter) 
	accessReviewHistoryDecisionFilter := graphmodels.DENY_ACCESSREVIEWHISTORYDECISIONFILTER 
	requestBody.SetAccessReviewHistoryDecisionFilter(&accessReviewHistoryDecisionFilter) 
	accessReviewHistoryDecisionFilter := graphmodels.DONTKNOW_ACCESSREVIEWHISTORYDECISIONFILTER 
	requestBody.SetAccessReviewHistoryDecisionFilter(&accessReviewHistoryDecisionFilter) 
	accessReviewHistoryDecisionFilter := graphmodels.NOTREVIEWED_ACCESSREVIEWHISTORYDECISIONFILTER 
	requestBody.SetAccessReviewHistoryDecisionFilter(&accessReviewHistoryDecisionFilter) 
	accessReviewHistoryDecisionFilter := graphmodels.NOTNOTIFIED_ACCESSREVIEWHISTORYDECISIONFILTER 
	requestBody.SetAccessReviewHistoryDecisionFilter(&accessReviewHistoryDecisionFilter)
}
requestBody.SetDecisions(decisions)
reviewHistoryPeriodStartDateTime , err := time.Parse(time.RFC3339, "2021-01-01T00:00:00Z")
requestBody.SetReviewHistoryPeriodStartDateTime(&reviewHistoryPeriodStartDateTime) 
reviewHistoryPeriodEndDateTime , err := time.Parse(time.RFC3339, "2021-04-30T23:59:59Z")
requestBody.SetReviewHistoryPeriodEndDateTime(&reviewHistoryPeriodEndDateTime) 


accessReviewScope := graphmodels.NewAccessReviewQueryScope()
queryType := "MicrosoftGraph"
accessReviewScope.SetQueryType(&queryType) 
query := "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'accessPackageAssignments')"
accessReviewScope.SetQuery(&query) 
queryRoot := null
accessReviewScope.SetQueryRoot(&queryRoot) 
accessReviewScope1 := graphmodels.NewAccessReviewQueryScope()
queryType := "MicrosoftGraph"
accessReviewScope1.SetQueryType(&queryType) 
query := "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, '/groups')"
accessReviewScope1.SetQuery(&query) 
queryRoot := null
accessReviewScope1.SetQueryRoot(&queryRoot) 

scopes := []graphmodels.AccessReviewScopeable {
	accessReviewScope,
	accessReviewScope1,
}
requestBody.SetScopes(scopes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
historyDefinitions, err := graphClient.IdentityGovernance().AccessReviews().HistoryDefinitions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewHistoryDefinition accessReviewHistoryDefinition = new AccessReviewHistoryDefinition();
accessReviewHistoryDefinition.setDisplayName("Last quarter's group reviews April 2021");
LinkedList<AccessReviewHistoryDecisionFilter> decisions = new LinkedList<AccessReviewHistoryDecisionFilter>();
decisions.add(AccessReviewHistoryDecisionFilter.Approve);
decisions.add(AccessReviewHistoryDecisionFilter.Deny);
decisions.add(AccessReviewHistoryDecisionFilter.DontKnow);
decisions.add(AccessReviewHistoryDecisionFilter.NotReviewed);
decisions.add(AccessReviewHistoryDecisionFilter.NotNotified);
accessReviewHistoryDefinition.setDecisions(decisions);
OffsetDateTime reviewHistoryPeriodStartDateTime = OffsetDateTime.parse("2021-01-01T00:00:00Z");
accessReviewHistoryDefinition.setReviewHistoryPeriodStartDateTime(reviewHistoryPeriodStartDateTime);
OffsetDateTime reviewHistoryPeriodEndDateTime = OffsetDateTime.parse("2021-04-30T23:59:59Z");
accessReviewHistoryDefinition.setReviewHistoryPeriodEndDateTime(reviewHistoryPeriodEndDateTime);
LinkedList<AccessReviewScope> scopes = new LinkedList<AccessReviewScope>();
AccessReviewQueryScope accessReviewScope = new AccessReviewQueryScope();
accessReviewScope.setOdataType("#microsoft.graph.accessReviewQueryScope");
accessReviewScope.setQueryType("MicrosoftGraph");
accessReviewScope.setQuery("/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'accessPackageAssignments')");
accessReviewScope.setQueryRoot(null);
scopes.add(accessReviewScope);
AccessReviewQueryScope accessReviewScope1 = new AccessReviewQueryScope();
accessReviewScope1.setOdataType("#microsoft.graph.accessReviewQueryScope");
accessReviewScope1.setQueryType("MicrosoftGraph");
accessReviewScope1.setQuery("/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, '/groups')");
accessReviewScope1.setQueryRoot(null);
scopes.add(accessReviewScope1);
accessReviewHistoryDefinition.setScopes(scopes);
AccessReviewHistoryDefinition result = graphClient.identityGovernance().accessReviews().historyDefinitions().post(accessReviewHistoryDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewHistoryDefinition = {
  displayName: 'Last quarter\'s group reviews April 2021',
  decisions: [
    'approve',
    'deny',
    'dontKnow',
    'notReviewed',
    'notNotified'
  ],
  reviewHistoryPeriodStartDateTime: '2021-01-01T00:00:00Z',
  reviewHistoryPeriodEndDateTime: '2021-04-30T23:59:59Z',
  scopes: [
    {
      '@odata.type': '#microsoft.graph.accessReviewQueryScope',
      queryType: 'MicrosoftGraph',     
      query: '/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, \'accessPackageAssignments\')',
      queryRoot: null
    },  
    {
      '@odata.type': '#microsoft.graph.accessReviewQueryScope',
      queryType: 'MicrosoftGraph',     
      query: '/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, \'/groups\')',
      queryRoot: null
    }
  ]
};

await client.api('/identityGovernance/accessReviews/historyDefinitions')
	.post(accessReviewHistoryDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessReviewHistoryDefinition;
use Microsoft\Graph\Generated\Models\AccessReviewHistoryDecisionFilter;
use Microsoft\Graph\Generated\Models\AccessReviewScope;
use Microsoft\Graph\Generated\Models\AccessReviewQueryScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewHistoryDefinition();
$requestBody->setDisplayName('Last quarter\'s group reviews April 2021');
$requestBody->setDecisions([new AccessReviewHistoryDecisionFilter('approve'),new AccessReviewHistoryDecisionFilter('deny'),new AccessReviewHistoryDecisionFilter('dontKnow'),new AccessReviewHistoryDecisionFilter('notReviewed'),new AccessReviewHistoryDecisionFilter('notNotified'),	]);
$requestBody->setReviewHistoryPeriodStartDateTime(new \DateTime('2021-01-01T00:00:00Z'));
$requestBody->setReviewHistoryPeriodEndDateTime(new \DateTime('2021-04-30T23:59:59Z'));
$scopesAccessReviewScope1 = new AccessReviewQueryScope();
$scopesAccessReviewScope1->setOdataType('#microsoft.graph.accessReviewQueryScope');
$scopesAccessReviewScope1->setQueryType('MicrosoftGraph');
$scopesAccessReviewScope1->setQuery('/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, \'accessPackageAssignments\')');
$scopesAccessReviewScope1->setQueryRoot(null);
$scopesArray []= $scopesAccessReviewScope1;
$scopesAccessReviewScope2 = new AccessReviewQueryScope();
$scopesAccessReviewScope2->setOdataType('#microsoft.graph.accessReviewQueryScope');
$scopesAccessReviewScope2->setQueryType('MicrosoftGraph');
$scopesAccessReviewScope2->setQuery('/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, \'/groups\')');
$scopesAccessReviewScope2->setQueryRoot(null);
$scopesArray []= $scopesAccessReviewScope2;
$requestBody->setScopes($scopesArray);


$result = $graphServiceClient->identityGovernance()->accessReviews()->historyDefinitions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	displayName = "Last quarter's group reviews April 2021"
	decisions = @(
	"approve"
"deny"
"dontKnow"
"notReviewed"
"notNotified"
)
reviewHistoryPeriodStartDateTime = [System.DateTime]::Parse("2021-01-01T00:00:00Z")
reviewHistoryPeriodEndDateTime = [System.DateTime]::Parse("2021-04-30T23:59:59Z")
scopes = @(
@{
"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
queryType = "MicrosoftGraph"
query = "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'accessPackageAssignments')"
queryRoot = $null
}
@{
"@odata.type" = "#microsoft.graph.accessReviewQueryScope"
queryType = "MicrosoftGraph"
query = "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, '/groups')"
queryRoot = $null
}
)
}

New-MgIdentityGovernanceAccessReviewHistoryDefinition -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_review_history_definition import AccessReviewHistoryDefinition
from msgraph.generated.models.access_review_history_decision_filter import AccessReviewHistoryDecisionFilter
from msgraph.generated.models.access_review_scope import AccessReviewScope
from msgraph.generated.models.access_review_query_scope import AccessReviewQueryScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewHistoryDefinition(
	display_name = "Last quarter's group reviews April 2021",
	decisions = [
		AccessReviewHistoryDecisionFilter.Approve,
		AccessReviewHistoryDecisionFilter.Deny,
		AccessReviewHistoryDecisionFilter.DontKnow,
		AccessReviewHistoryDecisionFilter.NotReviewed,
		AccessReviewHistoryDecisionFilter.NotNotified,
	],
	review_history_period_start_date_time = "2021-01-01T00:00:00Z",
	review_history_period_end_date_time = "2021-04-30T23:59:59Z",
	scopes = [
		AccessReviewQueryScope(
			odata_type = "#microsoft.graph.accessReviewQueryScope",
			query_type = "MicrosoftGraph",
			query = "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'accessPackageAssignments')",
			query_root = None,
		),
		AccessReviewQueryScope(
			odata_type = "#microsoft.graph.accessReviewQueryScope",
			query_type = "MicrosoftGraph",
			query = "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, '/groups')",
			query_root = None,
		),
	],
)

result = await graph_client.identity_governance.access_reviews.history_definitions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.accessReviewHistoryDefinition",
    "id": "b2cb022f-b7e1-40f3-9854-c65a40861c38",
    "displayName": "Last quarter's group reviews April 2021",
    "reviewHistoryPeriodStartDateTime": "2021-01-01T00:00:00Z",
    "reviewHistoryPeriodEndDateTime": "2021-04-30T23:59:59Z",
    "decisions": [
        "approve",
        "deny",
        "dontKnow",
        "notReviewed",
        "notNotified"
    ],
    "status": "requested",
    "createdDateTime": "2021-04-14T00:22:48.9392594Z",
    "createdBy": {
        "id": "957f1027-c0ee-460d-9269-b8444459e0fe",
        "displayName": "MOD Administrator",
        "userPrincipalName": "admin@contoso.com"
    },
    "scopes": [
        {
            "@odata.type": "#microsoft.graph.accessReviewQueryScope",
            "queryType": "MicrosoftGraph",
            "query": "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, 'accessPackageAssignments')",
            "queryRoot": null
        },
        {
            "@odata.type": "#microsoft.graph.accessReviewQueryScope",
            "queryType": "MicrosoftGraph",
            "query": "/identityGovernance/accessReviews/definitions?$filter=contains(scope/query, '/groups')",
            "queryRoot": null
        }
    ]
}
```
