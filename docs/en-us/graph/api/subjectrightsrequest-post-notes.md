<!-- Source: https://learn.microsoft.com/en-us/graph/api/subjectrightsrequest-post-notes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# Create authoredNote

Namespace: microsoft.graph

Create a new [authoredNote](https://learn.microsoft.com/en-us/graph/api/resources/authorednote?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | SubjectRightsRequest.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

Caution

The subject rights request API under the `/privacy` node is deprecated and will stop returning data on March 30, 2025. Please use the new path under `/security`.

```http
POST /security/subjectRightsRequests/{subjectRightsRequestId}/notes
POST /privacy/subjectRightsRequests/{subjectRightsRequestId}/notes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [authoredNote](https://learn.microsoft.com/en-us/graph/api/resources/authorednote?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [authoredNote](https://learn.microsoft.com/en-us/graph/api/resources/authorednote?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [microsoft.graph.itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The note content for the request. |

## Response

If successful, this method returns a `201 Created` response code and an [authoredNote](https://learn.microsoft.com/en-us/graph/api/resources/authorednote?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/privacy/subjectRightsRequests/{subjectRightsRequestId}/notes
Content-Type: application/json

{
  "content": {
    "content": "Please take a look at the files tagged with follow up",
    "contentType": "text"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new AuthoredNote
{
	Content = new ItemBody
	{
		Content = "Please take a look at the files tagged with follow up",
		ContentType = BodyType.Text,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Privacy.SubjectRightsRequests["{subjectRightsRequest-id}"].Notes.PostAsync(requestBody);
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

requestBody := graphmodels.NewAuthoredNote()
content := graphmodels.NewItemBody()
content := "Please take a look at the files tagged with follow up"
content.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
content.SetContentType(&contentType) 
requestBody.SetContent(content)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
notes, err := graphClient.Privacy().SubjectRightsRequests().BySubjectRightsRequestId("subjectRightsRequest-id").Notes().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AuthoredNote authoredNote = new AuthoredNote();
ItemBody content = new ItemBody();
content.setContent("Please take a look at the files tagged with follow up");
content.setContentType(BodyType.Text);
authoredNote.setContent(content);
AuthoredNote result = graphClient.privacy().subjectRightsRequests().bySubjectRightsRequestId("{subjectRightsRequest-id}").notes().post(authoredNote);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const authoredNote = {
  content: {
    content: 'Please take a look at the files tagged with follow up',
    contentType: 'text'
  }
};

await client.api('/privacy/subjectRightsRequests/{subjectRightsRequestId}/notes')
	.post(authoredNote);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\AuthoredNote;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AuthoredNote();
$content = new ItemBody();
$content->setContent('Please take a look at the files tagged with follow up');
$content->setContentType(new BodyType('text'));
$requestBody->setContent($content);

$result = $graphServiceClient->privacy()->subjectRightsRequests()->bySubjectRightsRequestId('subjectRightsRequest-id')->notes()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Compliance

$params = @{
	content = @{
		content = "Please take a look at the files tagged with follow up"
		contentType = "text"
	}
}

New-MgPrivacySubjectRightsRequestNote -SubjectRightsRequestId $subjectRightsRequestId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.authored_note import AuthoredNote
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AuthoredNote(
	content = ItemBody(
		content = "Please take a look at the files tagged with follow up",
		content_type = BodyType.Text,
	),
)

result = await graph_client.privacy.subject_rights_requests.by_subject_rights_request_id('subjectRightsRequest-id').notes.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "D450C4F9-CC18-4784-9406-9372F4E05F7B",
  "createdDateTime": "2022-05-10T22:42:28Z",
  "author": {
    "user": {
      "id": "1B761ED2-AA7E-4D82-9CF5-C09D737B6167",
      "displayName": "srradmin@contoso.com"
    }
  },
  "content": {
    "content": "Please take a look at the files tagged with follow up",
    "contentType": "text"
  }
}
```
