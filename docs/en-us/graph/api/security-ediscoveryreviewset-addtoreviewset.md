<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoveryreviewset-addtoreviewset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# ediscoveryReviewSet: addToReviewSet

Namespace: microsoft.graph.security

Start the process of adding a collection from Microsoft 365 services to a [review set](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreviewset?view=graph-rest-1.0). After the operation is created, you can get the status of the operation by retrieving the `Location` parameter from the response headers. The location provides a URL that returns an [Add to review set operation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryaddtoreviewsetoperation?view=graph-rest-1.0).

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

- **eDiscovery Manager**. Allows members to access review sets in eDiscovery cases they create and are members of. **This is the least privileged option for accessing review sets in their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access review sets in all eDiscovery cases in the organization.
- **Reviewer**. Provides read-only access to review sets within eDiscovery cases where the user is a member. Reviewers can view and tag documents but cannot perform other case management tasks.

The Review role allows users to access review sets in eDiscovery cases they are members of. Users can view and tag documents in review sets but cannot preview search results or perform other search or case management tasks.

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
POST /security/cases/ediscoveryCases/{eDiscoveryCaseId}/reviewSets/{eDiscoveryReviewSetId}/addToReviewSet
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
| additionalDataOptions | [microsoft.graph.security.additionalDataOptions](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryaddtoreviewsetoperation?view=graph-rest-1.0#additionaldataoptions-values) | The options to add items to the review set. The possible values are: `allVersions`, `linkedFiles`, `unknownFutureValue`, `advancedIndexing`, `listAttachments`, `htmlTranscripts`, `messageConversationExpansion`, `locationsWithoutHits`, `allItemsInFolder`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `advancedIndexing`, `listAttachments`, `htmlTranscripts`, `messageConversationExpansion`, `locationsWithoutHits`, `allItemsInFolder`. The `locationsWithoutHits` and `advancedIndexing` values are only considered if **itemsToIncude** is set to `partiallyIndexed`. |
| cloudAttachmentVersion | microsoft.graph.security.cloudAttachmentVersion | Specifies the number of cloud attachment versions to collect. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. The default value is `latest`. |
| documentVersion | microsoft.graph.security.documentVersion | Specifies the number of document versions to collect. The possible values are: `latest`, `recent10`, `recent100`, `all`, `unknownFutureValue`. The default value is `latest`. |
| itemsToInclude | [microsoft.graph.security.itemsToInclude](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryaddtoreviewsetoperation?view=graph-rest-1.0#itemstoinclude-values) | The items to include in the review set. The possible values are: `searchHits`, `partiallyIndexed`, `unknownFutureValue`. |
| search | [microsoft.graph.security.ediscoverySearch](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverysearch?view=graph-rest-1.0) | The ID of the eDiscovery search you'd like to add to the review set. |

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
POST https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/reviewSets/63ef0fd7-0db2-45eb-a9d7-7d75c8239873/addToReviewSet
Content-Type: application/json

{
  "search": {
      "id": "c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7"
  },
  "additionalDataOptions": "linkedFiles",
  "cloudAttachmentVersion": "latest",
  "documentVersion": "recent10"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Security.Cases.EdiscoveryCases.Item.ReviewSets.Item.MicrosoftGraphSecurityAddToReviewSet;
using Microsoft.Graph.Models.Security;

var requestBody = new AddToReviewSetPostRequestBody
{
	Search = new EdiscoverySearch
	{
		Id = "c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7",
	},
	AdditionalDataOptions = AdditionalDataOptions.LinkedFiles,
	CloudAttachmentVersion = CloudAttachmentVersion.Latest,
	DocumentVersion = DocumentVersion.Recent10,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Security.Cases.EdiscoveryCases["{ediscoveryCase-id}"].ReviewSets["{ediscoveryReviewSet-id}"].MicrosoftGraphSecurityAddToReviewSet.PostAsync(requestBody);
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

requestBody := graphsecurity.NewAddToReviewSetPostRequestBody()
search := graphmodelssecurity.NewEdiscoverySearch()
id := "c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7"
search.SetId(&id) 
requestBody.SetSearch(search)
additionalDataOptions := graphmodels.LINKEDFILES_ADDITIONALDATAOPTIONS 
requestBody.SetAdditionalDataOptions(&additionalDataOptions) 
cloudAttachmentVersion := graphmodels.LATEST_CLOUDATTACHMENTVERSION 
requestBody.SetCloudAttachmentVersion(&cloudAttachmentVersion) 
documentVersion := graphmodels.RECENT10_DOCUMENTVERSION 
requestBody.SetDocumentVersion(&documentVersion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Security().Cases().EdiscoveryCases().ByEdiscoveryCaseId("ediscoveryCase-id").ReviewSets().ByEdiscoveryReviewSetId("ediscoveryReviewSet-id").MicrosoftGraphSecurityAddToReviewSet().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.security.cases.ediscoverycases.item.reviewsets.item.microsoftgraphsecurityaddtoreviewset.AddToReviewSetPostRequestBody addToReviewSetPostRequestBody = new com.microsoft.graph.security.cases.ediscoverycases.item.reviewsets.item.microsoftgraphsecurityaddtoreviewset.AddToReviewSetPostRequestBody();
com.microsoft.graph.models.security.EdiscoverySearch search = new com.microsoft.graph.models.security.EdiscoverySearch();
search.setId("c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7");
addToReviewSetPostRequestBody.setSearch(search);
addToReviewSetPostRequestBody.setAdditionalDataOptions(EnumSet.of(com.microsoft.graph.models.security.AdditionalDataOptions.LinkedFiles));
addToReviewSetPostRequestBody.setCloudAttachmentVersion(com.microsoft.graph.models.security.CloudAttachmentVersion.Latest);
addToReviewSetPostRequestBody.setDocumentVersion(com.microsoft.graph.models.security.DocumentVersion.Recent10);
graphClient.security().cases().ediscoveryCases().byEdiscoveryCaseId("{ediscoveryCase-id}").reviewSets().byEdiscoveryReviewSetId("{ediscoveryReviewSet-id}").microsoftGraphSecurityAddToReviewSet().post(addToReviewSetPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const addToReviewSet = {
  search: {
      id: 'c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7'
  },
  additionalDataOptions: 'linkedFiles',
  cloudAttachmentVersion: 'latest',
  documentVersion: 'recent10'
};

await client.api('/security/cases/ediscoveryCases/58399dff-cebe-478f-b1af-d3227f1fd645/reviewSets/63ef0fd7-0db2-45eb-a9d7-7d75c8239873/addToReviewSet')
	.post(addToReviewSet);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Security\Cases\EdiscoveryCases\Item\ReviewSets\Item\MicrosoftGraphSecurityAddToReviewSet\AddToReviewSetPostRequestBody;
use Microsoft\Graph\Generated\Models\Security\EdiscoverySearch;
use Microsoft\Graph\Generated\Models\Security\AdditionalDataOptions;
use Microsoft\Graph\Generated\Models\Security\CloudAttachmentVersion;
use Microsoft\Graph\Generated\Models\Security\DocumentVersion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AddToReviewSetPostRequestBody();
$search = new EdiscoverySearch();
$search->setId('c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7');
$requestBody->setSearch($search);
$requestBody->setAdditionalDataOptions(new AdditionalDataOptions('linkedFiles'));
$requestBody->setCloudAttachmentVersion(new CloudAttachmentVersion('latest'));
$requestBody->setDocumentVersion(new DocumentVersion('recent10'));

$graphServiceClient->security()->cases()->ediscoveryCases()->byEdiscoveryCaseId('ediscoveryCase-id')->reviewSets()->byEdiscoveryReviewSetId('ediscoveryReviewSet-id')->microsoftGraphSecurityAddToReviewSet()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Security

$params = @{
	search = @{
		id = "c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7"
	}
	additionalDataOptions = "linkedFiles"
	cloudAttachmentVersion = "latest"
	documentVersion = "recent10"
}

Add-MgSecurityCaseEdiscoveryCaseReviewSetToReviewSet -EdiscoveryCaseId $ediscoveryCaseId -EdiscoveryReviewSetId $ediscoveryReviewSetId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.security.cases.ediscoverycases.item.reviewsets.item.microsoft_graph_security_add_to_review_set.add_to_review_set_post_request_body import AddToReviewSetPostRequestBody
from msgraph.generated.models.security.ediscovery_search import EdiscoverySearch
from msgraph.generated.models.additional_data_options import AdditionalDataOptions
from msgraph.generated.models.cloud_attachment_version import CloudAttachmentVersion
from msgraph.generated.models.document_version import DocumentVersion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AddToReviewSetPostRequestBody(
	search = EdiscoverySearch(
		id = "c17e91d6-6bc0-4ecb-b388-269ea3d4ffb7",
	),
	additional_data_options = AdditionalDataOptions.LinkedFiles,
	cloud_attachment_version = CloudAttachmentVersion.Latest,
	document_version = DocumentVersion.Recent10,
)

await graph_client.security.cases.ediscovery_cases.by_ediscovery_case_id('ediscoveryCase-id').review_sets.by_ediscovery_review_set_id('ediscoveryReviewSet-id').microsoft_graph_security_add_to_review_set.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
