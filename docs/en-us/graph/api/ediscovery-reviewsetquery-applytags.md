<!-- Source: https://learn.microsoft.com/en-us/graph/api/ediscovery-reviewsetquery-applytags?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# reviewSetQuery: applyTags

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

Apply [tags](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) to documents that match the specified [reviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

## HTTP request

```http
POST /compliance/ediscovery/cases/{caseId}/reviewSets/{reviewSetId}/queries/{reviewSetQueryId}/applyTags
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| tagsToAdd | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | IDs of tags to add to the documents that match the query. |
| tagsToRemove | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) collection | IDs of tags to remove from the documents that match the query. |

## Response

If successful, this action returns a `202 Accepted` response code.

If the tagging operation is started successfully, this action returns a `202 Accepted` response code. The response will also contain a `Location` header, which contains the location of the [tagOperation](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tagoperation?view=graph-rest-beta) that was created to handle the tagging. Check the status of the tagging operation by making a GET request to the location, when successfully completed, the [status](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-caseoperation?view=graph-rest-beta#caseoperationstatus-values) will change to `succeeded`.

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
POST https://graph.microsoft.com/beta/compliance/ediscovery/cases/47746044-fd0b-4a30-acfc-5272b691ba5b/reviewsets/6c95c2a6-31fa-45a8-93ef-dd4531974783/queries/b4798d14-748d-468e-a1ec-96a2b1d49677/applyTags
Content-Type: application/json

{
    "tagsToAdd": [
        {
            "id": "b4798d14-748d-468e-a1ec-96a2b1d49677"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Compliance.Ediscovery.Cases.Item.ReviewSets.Item.Queries.Item.MicrosoftGraphEdiscoveryApplyTags;
using Microsoft.Graph.Beta.Models.Ediscovery;

var requestBody = new ApplyTagsPostRequestBody
{
	TagsToAdd = new List<Tag>
	{
		new Tag
		{
			Id = "b4798d14-748d-468e-a1ec-96a2b1d49677",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Compliance.Ediscovery.Cases["{case-id}"].ReviewSets["{reviewSet-id}"].Queries["{reviewSetQuery-id}"].MicrosoftGraphEdiscoveryApplyTags.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphcompliance "github.com/microsoftgraph/msgraph-beta-sdk-go/compliance"
	  graphmodelsediscovery "github.com/microsoftgraph/msgraph-beta-sdk-go/models/ediscovery"
	  //other-imports
)

requestBody := graphcompliance.NewApplyTagsPostRequestBody()


tag := graphmodelsediscovery.NewTag()
id := "b4798d14-748d-468e-a1ec-96a2b1d49677"
tag.SetId(&id) 

tagsToAdd := []graphmodelsediscovery.Tagable {
	tag,
}
requestBody.SetTagsToAdd(tagsToAdd)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Compliance().Ediscovery().Cases().ByCaseId("case-id").ReviewSets().ByReviewSetId("reviewSet-id").Queries().ByReviewSetQueryId("reviewSetQuery-id").MicrosoftGraphEdiscoveryApplyTags().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.compliance.ediscovery.cases.item.reviewsets.item.queries.item.microsoftgraphediscoveryapplytags.ApplyTagsPostRequestBody applyTagsPostRequestBody = new com.microsoft.graph.beta.compliance.ediscovery.cases.item.reviewsets.item.queries.item.microsoftgraphediscoveryapplytags.ApplyTagsPostRequestBody();
LinkedList<com.microsoft.graph.beta.models.ediscovery.Tag> tagsToAdd = new LinkedList<com.microsoft.graph.beta.models.ediscovery.Tag>();
com.microsoft.graph.beta.models.ediscovery.Tag tag = new com.microsoft.graph.beta.models.ediscovery.Tag();
tag.setId("b4798d14-748d-468e-a1ec-96a2b1d49677");
tagsToAdd.add(tag);
applyTagsPostRequestBody.setTagsToAdd(tagsToAdd);
graphClient.compliance().ediscovery().cases().byCaseId("{case-id}").reviewSets().byReviewSetId("{reviewSet-id}").queries().byReviewSetQueryId("{reviewSetQuery-id}").microsoftGraphEdiscoveryApplyTags().post(applyTagsPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const applyTags = {
    tagsToAdd: [
        {
            id: 'b4798d14-748d-468e-a1ec-96a2b1d49677'
        }
    ]
};

await client.api('/compliance/ediscovery/cases/47746044-fd0b-4a30-acfc-5272b691ba5b/reviewsets/6c95c2a6-31fa-45a8-93ef-dd4531974783/queries/b4798d14-748d-468e-a1ec-96a2b1d49677/applyTags')
	.version('beta')
	.post(applyTags);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Compliance\Ediscovery\Cases\Item\ReviewSets\Item\Queries\Item\MicrosoftGraphEdiscoveryApplyTags\ApplyTagsPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Ediscovery\Tag;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ApplyTagsPostRequestBody();
$tagsToAddTag1 = new Tag();
$tagsToAddTag1->setId('b4798d14-748d-468e-a1ec-96a2b1d49677');
$tagsToAddArray []= $tagsToAddTag1;
$requestBody->setTagsToAdd($tagsToAddArray);


$graphServiceClient->compliance()->ediscovery()->cases()->byCaseId('case-id')->reviewSets()->byReviewSetId('reviewSet-id')->queries()->byReviewSetQueryId('reviewSetQuery-id')->microsoftGraphEdiscoveryApplyTags()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Compliance

$params = @{
	tagsToAdd = @(
		@{
			id = "b4798d14-748d-468e-a1ec-96a2b1d49677"
		}
	)
}

Add-MgBetaComplianceEdiscoveryCaseReviewSetQueryTag -CaseId $caseId -ReviewSetId $reviewSetId -ReviewSetQueryId $reviewSetQueryId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.compliance.ediscovery.cases.item.reviewsets.item.queries.item.microsoft_graph_ediscovery_apply_tags.apply_tags_post_request_body import ApplyTagsPostRequestBody
from msgraph_beta.generated.models.ediscovery.tag import Tag
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ApplyTagsPostRequestBody(
	tags_to_add = [
		Tag(
			id = "b4798d14-748d-468e-a1ec-96a2b1d49677",
		),
	],
)

await graph_client.compliance.ediscovery.cases.by_case_id('case-id').review_sets.by_review_set_id('reviewSet-id').queries.by_review_set_query_id('reviewSetQuery-id').microsoft_graph_ediscovery_apply_tags.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 202 Accepted
cache-control: no-cache,
client-request-id: 56c9dd8b-d8f7-59ae-6733-38191862c9c9,
location: https://graph.microsoft.com/beta/compliance/ediscovery/cases('47746044-fd0b-4a30-acfc-5272b691ba5b')/operations('d77f7933e88842bab3221e280be9dc0b'),
request-id: c2397a81-e9c2-4851-b669-d87e0751e45a
```
