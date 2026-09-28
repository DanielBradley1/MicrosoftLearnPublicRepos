<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewsetquery-applytags?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# ediscoveryReviewSetQuery: applyTags

Namespace: microsoft.graph.security

Apply tags to files in an [eDiscovery review set](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0). For details, see [Tag documents in a review set in eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/tagging-documents).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to manage custodians and data sources for eDiscovery cases they create. However, eDiscovery Managers can only manage custodians for the cases they create. **This is the least privileged option for managing custodians in their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to manage custodians and data sources for all eDiscovery cases in the organization.

The Custodian role provides access to manage data sources \(mailboxes, SharePoint sites, and Teams\) associated with custodians in eDiscovery cases. This role is only available to members of the eDiscovery Manager role group.

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{ediscoveryCaseId}/reviewSets/{ediscoveryReviewSetId}/queries/{queryId}/applyTags
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
| tagsToAdd | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) collection | Tags to remove from the files in review set query. |
| tagsToRemove | [microsoft.graph.security.ediscoveryReviewTag](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewtag?view=graph-rest-1.0) collection | Tags to remove add the files in review set query. |

## Response

If successful, this action returns a `202 Accepted` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/reviewSets/63ef0fd7-0db2-45eb-a9d7-7d75c8239873/queries/5f426fdc-f027-40db-b7cc-453cf06dc996/applyTags
Content-Type: application/json

{
    "tagsToAdd": [
        {"id": "d3d99dc704a74801b792b3e1e722aa0d"}
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.ReviewSets.Item.Queries.Item.MicrosoftGraphSecurityApplyTags;
using Microsoft.Graph.Models.Security;

var requestBody = new ApplyTagsPostRequestBody
{
	TagsToAdd = new List<EdiscoveryReviewTag>
	{
		new EdiscoveryReviewTag
		{
			Id = "d3d99dc704a74801b792b3e1e722aa0d",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].ReviewSets["{ediscoveryReviewSet-id}"].Queries["{ediscoveryReviewSetQuery-id}"].MicrosoftGraphSecurityApplyTags.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsecurity "github.com/microsoftgraph/msgraph-sdk-go/security"
	  graphmodelssecurity "github.com/microsoftgraph/msgraph-sdk-go/models/security"
	  //other-imports
)

requestBody := graphsecurity.NewApplyTagsPostRequestBody()


ediscoveryReviewTag := graphmodelssecurity.NewEdiscoveryReviewTag()
id := "d3d99dc704a74801b792b3e1e722aa0d"
ediscoveryReviewTag.SetId(&id) 

tagsToAdd := []graphmodelssecurity.EdiscoveryReviewTagable {
	ediscoveryReviewTag,
}
requestBody.SetTagsToAdd(tagsToAdd)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").ReviewSets().ByEdiscoveryReviewSetId("ediscoveryReviewSet-id").Queries().ByEdiscoveryReviewSetQueryId("ediscoveryReviewSetQuery-id").MicrosoftGraphSecurityApplyTags().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.reviewsets.item.queries.item.microsoftgraphsecurityapplytags.ApplyTagsPostRequestBody applyTagsPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.reviewsets.item.queries.item.microsoftgraphsecurityapplytags.ApplyTagsPostRequestBody();
LinkedList<com.microsoft.graph.models.security.EdiscoveryReviewTag> tagsToAdd = new LinkedList<com.microsoft.graph.models.security.EdiscoveryReviewTag>();
com.microsoft.graph.models.security.EdiscoveryReviewTag ediscoveryReviewTag = new com.microsoft.graph.models.security.EdiscoveryReviewTag();
ediscoveryReviewTag.setId("d3d99dc704a74801b792b3e1e722aa0d");
tagsToAdd.add(ediscoveryReviewTag);
applyTagsPostRequestBody.setTagsToAdd(tagsToAdd);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").reviewSets().byEdiscoveryReviewSetId("{ediscoveryReviewSet-id}").queries().byEdiscoveryReviewSetQueryId("{ediscoveryReviewSetQuery-id}").microsoftGraphSecurityApplyTags().post(applyTagsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const applyTags = {
    tagsToAdd: [
        {id: 'd3d99dc704a74801b792b3e1e722aa0d'}
    ]
};

await client.api('/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/reviewSets/63ef0fd7-0db2-45eb-a9d7-7d75c8239873/queries/5f426fdc-f027-40db-b7cc-453cf06dc996/applyTags')
	.post(applyTags);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\ReviewSets\Item\Queries\Item\MicrosoftGraphSecurityApplyTags\ApplyTagsPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\EdiscoveryReviewTag;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ApplyTagsPostRequestBody();
$tagsToAddEdiscoveryReviewTag1 = new EdiscoveryReviewTag();
$tagsToAddEdiscoveryReviewTag1->setId('d3d99dc704a74801b792b3e1e722aa0d');
$tagsToAddArray []= $tagsToAddEdiscoveryReviewTag1;
$requestBody->setTagsToAdd($tagsToAddArray);


$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->reviewSets()->byEdiscoveryReviewSetId('ediscoveryReviewSet-id')->queries()->byEdiscoveryReviewSetQueryId('ediscoveryReviewSetQuery-id')->microsoftGraphSecurityApplyTags()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	tagsToAdd = @(
		@{
			id = "d3d99dc704a74801b792b3e1e722aa0d"
		}
	)
}

Add-MgSecurityCaseEdiscoveryCaseReviewSetQueryTag -EdiscoveryCaseId $ediscoveryCaseId -EdiscoveryReviewSetId $ediscoveryReviewSetId -EdiscoveryReviewSetQueryId $ediscoveryReviewSetQueryId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.reviewsets.item.queries.item.microsoft_graph_security_apply_tags.apply_tags_post_request_body import ApplyTagsPostRequestBody
from msgraph.generated.models.security.ediscovery_review_tag import EdiscoveryReviewTag
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ApplyTagsPostRequestBody(
	tags_to_add = [
		EdiscoveryReviewTag(
			id = "d3d99dc704a74801b792b3e1e722aa0d",
		),
	],
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').review_sets.by_ediscovery_review_set_id('ediscoveryReviewSet-id').queries.by_ediscovery_review_set_query_id('ediscoveryReviewSetQuery-id').microsoft_graph_security_apply_tags.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
