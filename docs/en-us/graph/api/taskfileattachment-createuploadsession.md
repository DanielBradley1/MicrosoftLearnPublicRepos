<!-- Source: https://learn.microsoft.com/en-us/graph/api/taskfileattachment-createuploadsession?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# taskFileAttachment: createUploadSession

Namespace: microsoft.graph

Create an upload session to iteratively upload ranges of a file as an attachment to a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0).

As part of the response, this action returns an upload URL that you can use in subsequent sequential `PUT` queries. The request headers for each `PUT` operation let you specify the exact range of bytes to be uploaded. This allows the transfer to be resumed, in case the network connection is dropped during the upload.

The following are the steps to attach a file to a Microsoft To Do task using an upload session:

1. Create an upload session.
2. Within that upload session, iteratively upload ranges of bytes \(up to 4 MB each time\) until all the bytes of the file have been uploaded, and the file is attached to the **todoTask**.
3. Optional: Delete the upload session.

> **Note:** Use this approach to attach a file of any supported size between 0 MB to 25 MB.

For an example that describes the end-to-end attachment process, see [attach files to a To Do task](https://learn.microsoft.com/en-us/graph/todo-attachments).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Tasks.ReadWrite | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/todo/lists/{id}/tasks/{id}/attachments/createUploadSession
POST /users/{id}/todo/lists/{id}/tasks/{id}/attachments/createUploadSession
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameter that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| attachmentInfo | [attachmentInfo](https://learn.microsoft.com/en-us/graph/api/resources/attachmentinfo?view=graph-rest-1.0) | Represents attributes of the item to be uploaded and attached. At minimum, specify the attachment type \(`file`\), a name, and the size of the file. |

## Response

If successful, this action returns a `200 OK` response code and a new [uploadSession](https://learn.microsoft.com/en-us/graph/api/resources/uploadsession?view=graph-rest-1.0) in the response body.

## Examples

### Request

The following example shows a request to create an upload session.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/todo/lists/AAMDiFkfh=/tasks/AAMkADliMm=/attachments/createUploadSession
Content-Type: application/json

{
  "attachmentInfo": {
    "attachmentType": "file",
    "name": "flower",
    "size": 3483322
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Todo.Lists.Item.Tasks.Item.Attachments.CreateUploadSession;
using Microsoft.Graph.Models;

var requestBody = new CreateUploadSessionPostRequestBody
{
	AttachmentInfo = new AttachmentInfo
	{
		AttachmentType = AttachmentType.File,
		Name = "flower",
		Size = 3483322L,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Todo.Lists["{todoTaskList-id}"].Tasks["{todoTask-id}"].Attachments.CreateUploadSession.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemCreateUploadSessionPostRequestBody()
attachmentInfo := graphmodels.NewAttachmentInfo()
attachmentType := graphmodels.FILE_ATTACHMENTTYPE 
attachmentInfo.SetAttachmentType(&attachmentType) 
name := "flower"
attachmentInfo.SetName(&name) 
size := int64(3483322)
attachmentInfo.SetSize(&size) 
requestBody.SetAttachmentInfo(attachmentInfo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createUploadSession, err := graphClient.Me().Todo().Lists().ByTodoTaskListId("todoTaskList-id").Tasks().ByTodoTaskId("todoTask-id").Attachments().CreateUploadSession().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.todo.lists.item.tasks.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody createUploadSessionPostRequestBody = new com.microsoft.graph.users.item.todo.lists.item.tasks.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody();
AttachmentInfo attachmentInfo = new AttachmentInfo();
attachmentInfo.setAttachmentType(AttachmentType.File);
attachmentInfo.setName("flower");
attachmentInfo.setSize(3483322L);
createUploadSessionPostRequestBody.setAttachmentInfo(attachmentInfo);
var result = graphClient.me().todo().lists().byTodoTaskListId("{todoTaskList-id}").tasks().byTodoTaskId("{todoTask-id}").attachments().createUploadSession().post(createUploadSessionPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const uploadSession = {
  attachmentInfo: {
    attachmentType: 'file',
    name: 'flower',
    size: 3483322
  }
};

await client.api('/me/todo/lists/AAMDiFkfh=/tasks/AAMkADliMm=/attachments/createUploadSession')
	.post(uploadSession);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Todo\Lists\Item\Tasks\Item\Attachments\CreateUploadSession\CreateUploadSessionPostRequestBody;
use Microsoft\Graph\Generated\Models\AttachmentInfo;
use Microsoft\Graph\Generated\Models\AttachmentType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateUploadSessionPostRequestBody();
$attachmentInfo = new AttachmentInfo();
$attachmentInfo->setAttachmentType(new AttachmentType('file'));
$attachmentInfo->setName('flower');
$attachmentInfo->setSize(3483322);
$requestBody->setAttachmentInfo($attachmentInfo);

$result = $graphServiceClient->me()->todo()->lists()->byTodoTaskListId('todoTaskList-id')->tasks()->byTodoTaskId('todoTask-id')->attachments()->createUploadSession()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	attachmentInfo = @{
		attachmentType = "file"
		name = "flower"
		size = 3483322
	}
}

# A UPN can also be used as -UserId.
New-MgUserTodoListTaskAttachmentUploadSession -UserId $userId -TodoTaskListId $todoTaskListId -TodoTaskId $todoTaskId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.todo.lists.item.tasks.item.attachments.create_upload_session.create_upload_session_post_request_body import CreateUploadSessionPostRequestBody
from msgraph.generated.models.attachment_info import AttachmentInfo
from msgraph.generated.models.attachment_type import AttachmentType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateUploadSessionPostRequestBody(
	attachment_info = AttachmentInfo(
		attachment_type = AttachmentType.File,
		name = "flower",
		size = 3483322,
	),
)

result = await graph_client.me.todo.lists.by_todo_task_list_id('todoTaskList-id').tasks.by_todo_task_id('todoTask-id').attachments.create_upload_session.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.uploadSession",
    "uploadUrl": "https://graph.microsoft.com/v1.0/users/6f9a2a92-8527-4d64-837e-b5312852f36d/todo/lists/AAMDiFkfh=/tasks/AAMkADliMm=/attachmentSessions/AAMkADliMm=",
    "expirationDateTime": "2022-06-09T10:45:27.4324526Z",
    "nextExpectedRanges": [
        "0-"
    ]
}
```
