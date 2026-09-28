<!-- Source: https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-batchrecorddecisions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# accessReviewInstance: batchRecordDecisions

Namespace: microsoft.graph

Enables reviewers to review all [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) objects in a specific [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) in batches by using **principalId**, **resourceId**, or neither.

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
POST /identityGovernance/accessReviews/definitions/{accessReviewScheduleDefinitionId}/instances/{accessReviewInstanceId}/batchRecordDecisions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0).

The following table lists the properties that you can use to review [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) objects.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| decision | String | Access decision for the entity being reviewed. The possible values are: `Approve`, `Deny`, `NotReviewed`, `DontKnow`. Required. |
| justification | String | Context of the review provided to admins. Required if **justificationRequiredOnApproval** of the settings property of the **accessReviewScheduleDefinition** is `true` . |
| principalId | String | If supplied, all the **accessReviewInstanceDecisionItems** with matching **principalId** values will be reviewed in this batch. If not supplied, all **accessReviewInstanceDecisionItems** will be reviewed. |
| resourceId | String | If supplied, all the **accessReviewInstanceDecisionItems** with matching **resourceId** will be reviewed in this batch. If not supplied, all **accessReviewInstanceDecisionItems** will be reviewed. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/identityGovernance/accessReviews/definitions/e6cafba0-cbf0-4748-8868-0810c7f4cc06/instances/1234fba0-cbf0-6778-8868-9999c7f4cc06/batchRecordDecisions
Content-type: application/json

{
  "decision": "Approve",
  "justification": "All principals with access need continued access to the resource (Marketing Group) as all the principals are on the marketing team",
  "resourceId": "a5c51e59-3fcd-4a37-87a1-835c0c21488a"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.IdentityGovernance.AccessReviews.Definitions.Item.Instances.Item.BatchRecordDecisions;

var requestBody = new BatchRecordDecisionsPostRequestBody
{
	Decision = "Approve",
	Justification = "All principals with access need continued access to the resource (Marketing Group) as all the principals are on the marketing team",
	ResourceId = "a5c51e59-3fcd-4a37-87a1-835c0c21488a",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.IdentityGovernance.AccessReviews.Definitions["{accessReviewScheduleDefinition-id}"].Instances["{accessReviewInstance-id}"].BatchRecordDecisions.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphidentitygovernance "github.com/microsoftgraph/msgraph-sdk-go/identitygovernance"
	  //other-imports
)

requestBody := graphidentitygovernance.NewBatchRecordDecisionsPostRequestBody()
decision := "Approve"
requestBody.SetDecision(&decision) 
justification := "All principals with access need continued access to the resource (Marketing Group) as all the principals are on the marketing team"
requestBody.SetJustification(&justification) 
resourceId := "a5c51e59-3fcd-4a37-87a1-835c0c21488a"
requestBody.SetResourceId(&resourceId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.IdentityGovernance().AccessReviews().Definitions().ByAccessReviewScheduleDefinitionId("accessReviewScheduleDefinition-id").Instances().ByAccessReviewInstanceId("accessReviewInstance-id").BatchRecordDecisions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.identitygovernance.accessreviews.definitions.item.instances.item.batchrecorddecisions.BatchRecordDecisionsPostRequestBody batchRecordDecisionsPostRequestBody = new com.microsoft.graph.identitygovernance.accessreviews.definitions.item.instances.item.batchrecorddecisions.BatchRecordDecisionsPostRequestBody();
batchRecordDecisionsPostRequestBody.setDecision("Approve");
batchRecordDecisionsPostRequestBody.setJustification("All principals with access need continued access to the resource (Marketing Group) as all the principals are on the marketing team");
batchRecordDecisionsPostRequestBody.setResourceId("a5c51e59-3fcd-4a37-87a1-835c0c21488a");
graphClient.identityGovernance().accessReviews().definitions().byAccessReviewScheduleDefinitionId("{accessReviewScheduleDefinition-id}").instances().byAccessReviewInstanceId("{accessReviewInstance-id}").batchRecordDecisions().post(batchRecordDecisionsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const batchRecordDecisions = {
  decision: 'Approve',
  justification: 'All principals with access need continued access to the resource (Marketing Group) as all the principals are on the marketing team',
  resourceId: 'a5c51e59-3fcd-4a37-87a1-835c0c21488a'
};

await client.api('/identityGovernance/accessReviews/definitions/e6cafba0-cbf0-4748-8868-0810c7f4cc06/instances/1234fba0-cbf0-6778-8868-9999c7f4cc06/batchRecordDecisions')
	.post(batchRecordDecisions);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\IdentityGovernance\AccessReviews\Definitions\Item\Instances\Item\BatchRecordDecisions\BatchRecordDecisionsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BatchRecordDecisionsPostRequestBody();
$requestBody->setDecision('Approve');
$requestBody->setJustification('All principals with access need continued access to the resource (Marketing Group) as all the principals are on the marketing team');
$requestBody->setResourceId('a5c51e59-3fcd-4a37-87a1-835c0c21488a');

$graphServiceClient->identityGovernance()->accessReviews()->definitions()->byAccessReviewScheduleDefinitionId('accessReviewScheduleDefinition-id')->instances()->byAccessReviewInstanceId('accessReviewInstance-id')->batchRecordDecisions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.identitygovernance.accessreviews.definitions.item.instances.item.batch_record_decisions.batch_record_decisions_post_request_body import BatchRecordDecisionsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BatchRecordDecisionsPostRequestBody(
	decision = "Approve",
	justification = "All principals with access need continued access to the resource (Marketing Group) as all the principals are on the marketing team",
	resource_id = "a5c51e59-3fcd-4a37-87a1-835c0c21488a",
)

await graph_client.identity_governance.access_reviews.definitions.by_access_review_schedule_definition_id('accessReviewScheduleDefinition-id').instances.by_access_review_instance_id('accessReviewInstance-id').batch_record_decisions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
