<!-- Source: https://learn.microsoft.com/en-us/graph/api/site-post-documentprocessingjobs?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-06 -->

# Create documentProcessingJob

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [documentProcessingJob](https://learn.microsoft.com/en-us/graph/api/resources/documentprocessingjob?view=graph-rest-beta) object. The document processing job queues a document, or all documents in a folder, for processing by the applied content models.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.Manage.All | Not available. |

## HTTP request

```http
POST /sites/{sitesId}/documentProcessingJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [documentProcessingJob](https://learn.microsoft.com/en-us/graph/api/resources/documentprocessingjob?view=graph-rest-beta) object.

You can specify the following properties when you create a **documentProcessingJob**.

| Property | Type | Description |
| :--- | :--- | :--- |
| jobType | documentProcessingJobType | The document processing job type. The possible values are: `File`, `Folder`. Optional. |
| status | documentProcessingJobStatus | The document processing job status. The possible values are: `inProgress`, `completed`, `failed`, `notStarted`. Typically when a job is created, its initial status is `notStarted`. Optional. |
| createdDateTime | DateTimeOffset | Date and time of item creation. Read-only. Optional. |
| listItemUniqueId | String | The unique ID of the file or folder to process. To get the unique ID, use the [GET driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-beta) method and read the [sharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-beta) property. |

## Response

If successful, this method returns a `201 Created` response code and a [documentProcessingJob](https://learn.microsoft.com/en-us/graph/api/resources/documentprocessingjob?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/sites/ede4bb84-6c94-4c39-8acf-3d9dbb667fba/documentProcessingJobs
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.documentProcessingJob",
  "jobType": "File",
  "listItemUniqueId": "5955b119-99c1-4af9-97ed-3449e02de6f1",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new DocumentProcessingJob
{
	OdataType = "#microsoft.graph.documentProcessingJob",
	JobType = DocumentProcessingJobType.File,
	ListItemUniqueId = "5955b119-99c1-4af9-97ed-3449e02de6f1",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].DocumentProcessingJobs.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewDocumentProcessingJob()
jobType := graphmodels.FILE_DOCUMENTPROCESSINGJOBTYPE 
requestBody.SetJobType(&jobType) 
listItemUniqueId := "5955b119-99c1-4af9-97ed-3449e02de6f1"
requestBody.SetListItemUniqueId(&listItemUniqueId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
documentProcessingJobs, err := graphClient.Sites().BySiteId("site-id").DocumentProcessingJobs().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DocumentProcessingJob documentProcessingJob = new DocumentProcessingJob();
documentProcessingJob.setOdataType("#microsoft.graph.documentProcessingJob");
documentProcessingJob.setJobType(DocumentProcessingJobType.File);
documentProcessingJob.setListItemUniqueId("5955b119-99c1-4af9-97ed-3449e02de6f1");
DocumentProcessingJob result = graphClient.sites().bySiteId("{site-id}").documentProcessingJobs().post(documentProcessingJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const documentProcessingJob = {
  '@odata.type': '#microsoft.graph.documentProcessingJob',
  jobType: 'File',
  listItemUniqueId: '5955b119-99c1-4af9-97ed-3449e02de6f1',
};

await client.api('/sites/ede4bb84-6c94-4c39-8acf-3d9dbb667fba/documentProcessingJobs')
	.version('beta')
	.post(documentProcessingJob);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\DocumentProcessingJob;
use Microsoft\Graph\Beta\Generated\Models\DocumentProcessingJobType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DocumentProcessingJob();
$requestBody->setOdataType('#microsoft.graph.documentProcessingJob');
$requestBody->setJobType(new DocumentProcessingJobType('file'));
$requestBody->setListItemUniqueId('5955b119-99c1-4af9-97ed-3449e02de6f1');

$result = $graphServiceClient->sites()->bySiteId('site-id')->documentProcessingJobs()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.document_processing_job import DocumentProcessingJob
from msgraph_beta.generated.models.document_processing_job_type import DocumentProcessingJobType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DocumentProcessingJob(
	odata_type = "#microsoft.graph.documentProcessingJob",
	job_type = DocumentProcessingJobType.File,
	list_item_unique_id = "5955b119-99c1-4af9-97ed-3449e02de6f1",
)

result = await graph_client.sites.by_site_id('site-id').document_processing_jobs.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "11f99394-e5eb-45e9-b478-7c83eaeda224",
  "jobType": "File",
  "status": "notStarted",
  "createdDateTime": "2023-06-23T22:03:47",
  "listItemUniqueId": "5955b119-99c1-4af9-97ed-3449e02de6f1",
}
```
