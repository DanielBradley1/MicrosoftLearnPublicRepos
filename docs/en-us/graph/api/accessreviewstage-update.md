<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreviewstage-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Update accessReviewStage

Namespace: microsoft.graph

Update the properties of an [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) object. Only the **reviewers** and **fallbackReviewers** properties can be updated. You can only add reviewers to the **fallbackReviewers** property but can't remove existing **fallbackReviewers**.

To update an **accessReviewStage**, its **status** must be `NotStarted`, `Initializing`, or `InProgress`.

Note

Updating an **accessReviewStage** will update only that stage. The parent **accessReviewInstance** and any future **accessReviewStage** objects won't change. To make updates that apply to all future instances and stages, update the parent [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.

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
PATCH /identityGovernance/accessReviews/definitions/{accessReviewScheduleDefinitionId}/instances/{accessReviewInstanceId}/stages/{accessReviewStageId}
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
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of access review scopes is used to define who the reviewers are. For examples of options for assigning reviewers, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of reviewer scopes is used to define the list of fallback reviewers. These fallback reviewers will be notified to take action if no users are found from the list of reviewers specified. This could occur when either the group owner is specified as the reviewer but the group owner doesn't exist, or manager is specified as reviewer but a user's manager doesn't exist. |

## Response

If successful, this method returns a `200 OK` response code and an updated [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) object in the response body.

Attempting to remove existing **fallbackReviewers** returns a `409 Conflict` response code.

## Examples

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
PATCH https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/5dcfcc88-da88-4252-8629-a0807b4b076d/instances/720b8ee0-cee4-42ac-b164-894c48703acc/stages/7d244ab1-4ab1-7d24-b14a-247db14a247d
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.accessReviewStage",
  "reviewers": [
      {
          "query": "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
          "queryType": "MicrosoftGraph"
      }
  ],
  "fallbackReviewers": [
      {
          "query": "/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
          "queryType": "MicrosoftGraph"
      },
      {
          "query": "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
          "queryType": "MicrosoftGraph"
      }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AccessReviewStage
{
	OdataType = "#microsoft.graph.accessReviewStage",
	Reviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
			QueryType = "MicrosoftGraph",
		},
	},
	FallbackReviewers = new List<AccessReviewReviewerScope>
	{
		new AccessReviewReviewerScope
		{
			Query = "/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
			QueryType = "MicrosoftGraph",
		},
		new AccessReviewReviewerScope
		{
			Query = "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
			QueryType = "MicrosoftGraph",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.IdentityGovernance.AccessReviews.Definitions["{accessReviewScheduleDefinition-id}"].Instances["{accessReviewInstance-id}"].Stages["{accessReviewStage-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewAccessReviewStage()


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 

reviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
}
requestBody.SetReviewers(reviewers)


accessReviewReviewerScope := graphmodels.NewAccessReviewReviewerScope()
query := "/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e"
accessReviewReviewerScope.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope.SetQueryType(&queryType) 
accessReviewReviewerScope1 := graphmodels.NewAccessReviewReviewerScope()
query := "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5"
accessReviewReviewerScope1.SetQuery(&query) 
queryType := "MicrosoftGraph"
accessReviewReviewerScope1.SetQueryType(&queryType) 

fallbackReviewers := []graphmodels.AccessReviewReviewerScopeable {
	accessReviewReviewerScope,
	accessReviewReviewerScope1,
}
requestBody.SetFallbackReviewers(fallbackReviewers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
stages, err := graphClient.IdentityGovernance().AccessReviews().Definitions().ByAccessReviewScheduleDefinitionId("accessReviewScheduleDefinition-id").Instances().ByAccessReviewInstanceId("accessReviewInstance-id").Stages().ByAccessReviewStageId("accessReviewStage-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AccessReviewStage accessReviewStage = new AccessReviewStage();
accessReviewStage.setOdataType("#microsoft.graph.accessReviewStage");
LinkedList<AccessReviewReviewerScope> reviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope = new AccessReviewReviewerScope();
accessReviewReviewerScope.setQuery("/users/1ed8ac56-4827-4733-8f80-86adc2e67db5");
accessReviewReviewerScope.setQueryType("MicrosoftGraph");
reviewers.add(accessReviewReviewerScope);
accessReviewStage.setReviewers(reviewers);
LinkedList<AccessReviewReviewerScope> fallbackReviewers = new LinkedList<AccessReviewReviewerScope>();
AccessReviewReviewerScope accessReviewReviewerScope1 = new AccessReviewReviewerScope();
accessReviewReviewerScope1.setQuery("/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e");
accessReviewReviewerScope1.setQueryType("MicrosoftGraph");
fallbackReviewers.add(accessReviewReviewerScope1);
AccessReviewReviewerScope accessReviewReviewerScope2 = new AccessReviewReviewerScope();
accessReviewReviewerScope2.setQuery("/users/1ed8ac56-4827-4733-8f80-86adc2e67db5");
accessReviewReviewerScope2.setQueryType("MicrosoftGraph");
fallbackReviewers.add(accessReviewReviewerScope2);
accessReviewStage.setFallbackReviewers(fallbackReviewers);
AccessReviewStage result = graphClient.identityGovernance().accessReviews().definitions().byAccessReviewScheduleDefinitionId("{accessReviewScheduleDefinition-id}").instances().byAccessReviewInstanceId("{accessReviewInstance-id}").stages().byAccessReviewStageId("{accessReviewStage-id}").patch(accessReviewStage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const accessReviewStage = {
  '@odata.type': '#microsoft.graph.accessReviewStage',
  reviewers: [
      {
          query: '/users/1ed8ac56-4827-4733-8f80-86adc2e67db5',
          queryType: 'MicrosoftGraph'
      }
  ],
  fallbackReviewers: [
      {
          query: '/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e',
          queryType: 'MicrosoftGraph'
      },
      {
          query: '/users/1ed8ac56-4827-4733-8f80-86adc2e67db5',
          queryType: 'MicrosoftGraph'
      }
  ]
};

await client.api('/identityGovernance/accessReviews/definitions/5dcfcc88-da88-4252-8629-a0807b4b076d/instances/720b8ee0-cee4-42ac-b164-894c48703acc/stages/7d244ab1-4ab1-7d24-b14a-247db14a247d')
	.update(accessReviewStage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AccessReviewStage;
use Microsoft\Graph\Generated\Models\AccessReviewReviewerScope;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AccessReviewStage();
$requestBody->setOdataType('#microsoft.graph.accessReviewStage');
$reviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$reviewersAccessReviewReviewerScope1->setQuery('/users/1ed8ac56-4827-4733-8f80-86adc2e67db5');
$reviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$reviewersArray []= $reviewersAccessReviewReviewerScope1;
$requestBody->setReviewers($reviewersArray);

$fallbackReviewersAccessReviewReviewerScope1 = new AccessReviewReviewerScope();
$fallbackReviewersAccessReviewReviewerScope1->setQuery('/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e');
$fallbackReviewersAccessReviewReviewerScope1->setQueryType('MicrosoftGraph');
$fallbackReviewersArray []= $fallbackReviewersAccessReviewReviewerScope1;
$fallbackReviewersAccessReviewReviewerScope2 = new AccessReviewReviewerScope();
$fallbackReviewersAccessReviewReviewerScope2->setQuery('/users/1ed8ac56-4827-4733-8f80-86adc2e67db5');
$fallbackReviewersAccessReviewReviewerScope2->setQueryType('MicrosoftGraph');
$fallbackReviewersArray []= $fallbackReviewersAccessReviewReviewerScope2;
$requestBody->setFallbackReviewers($fallbackReviewersArray);


$result = $graphServiceClient->identityGovernance()->accessReviews()->definitions()->byAccessReviewScheduleDefinitionId('accessReviewScheduleDefinition-id')->instances()->byAccessReviewInstanceId('accessReviewInstance-id')->stages()->byAccessReviewStageId('accessReviewStage-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.Governance

$params = @{
	"@odata.type" = "#microsoft.graph.accessReviewStage"
	reviewers = @(
		@{
			query = "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5"
			queryType = "MicrosoftGraph"
		}
	)
	fallbackReviewers = @(
		@{
			query = "/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e"
			queryType = "MicrosoftGraph"
		}
		@{
			query = "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5"
			queryType = "MicrosoftGraph"
		}
	)
}

Update-MgIdentityGovernanceAccessReviewDefinitionInstanceStage -AccessReviewScheduleDefinitionId $accessReviewScheduleDefinitionId -AccessReviewInstanceId $accessReviewInstanceId -AccessReviewStageId $accessReviewStageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.access_review_stage import AccessReviewStage
from msgraph.generated.models.access_review_reviewer_scope import AccessReviewReviewerScope
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AccessReviewStage(
	odata_type = "#microsoft.graph.accessReviewStage",
	reviewers = [
		AccessReviewReviewerScope(
			query = "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
			query_type = "MicrosoftGraph",
		),
	],
	fallback_reviewers = [
		AccessReviewReviewerScope(
			query = "/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
			query_type = "MicrosoftGraph",
		),
		AccessReviewReviewerScope(
			query = "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
			query_type = "MicrosoftGraph",
		),
	],
)

result = await graph_client.identity_governance.access_reviews.definitions.by_access_review_schedule_definition_id('accessReviewScheduleDefinition-id').instances.by_access_review_instance_id('accessReviewInstance-id').stages.by_access_review_stage_id('accessReviewStage-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.accessReviewStage",
  "id": "7d244ab1-4ab1-7d24-b14a-247db14a247d",
  "startDateTime": "2021-12-14T11:15:43.207Z",
  "endDateTime": "2021-12-15T11:15:43.207Z",
  "status": "InProgress",
  "reviewers": [
      {
          "query": "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
          "queryType": "MicrosoftGraph"
      }
  ],
  "fallbackReviewers": [
      {
          "query": "/users/4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
          "queryType": "MicrosoftGraph"
      },
      {
          "query": "/users/1ed8ac56-4827-4733-8f80-86adc2e67db5",
          "queryType": "MicrosoftGraph"
      }
  ]
}
```
