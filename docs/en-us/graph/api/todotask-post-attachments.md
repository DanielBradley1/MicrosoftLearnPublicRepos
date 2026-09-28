<!-- Source: https://learn.microsoft.com/en-us/graph/api/todotask-post-attachments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create taskFileAttachment

Namespace: microsoft.graph

Add a new [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) object to a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0).

This operation limits the size of the attachment you can add to under 3 MB. If the size of the file attachments is more than 3 MB, [create an upload session](https://learn.microsoft.com/en-us/graph/api/taskfileattachment-createuploadsession?view=graph-rest-1.0) to upload the attachments.

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
POST /me/todo/lists/{id}/tasks/{id}/attachments
POST /users/{id}/todo/lists/{id}/tasks/{id}/attachments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) object.

When you create a file attachment, include `"@odata.type": "#microsoft.graph.taskFileAttachment"` and the required properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | Binary | The base64-encoded contents of the file. Required. |
| contentType | String | The content type of the attachment. |
| name | String | The name of the text displayed under the icon that represents the embedded attachment. This doesn't need to be the actual file name. Required. |
| size | Int32 | The size in bytes of the attachment. |

## Response

If successful, this method returns a `201 Created` response code and a [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/me/todo/lists/AAMkpsDRVK=/tasks/AAKdfjhgsjhgJ=/attachments
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.taskFileAttachment",
  "name": "smile",
  "contentBytes": "a0b1c76de9f7=",
  "contentType": "image/gif"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TaskFileAttachment
{
	OdataType = "#microsoft.graph.taskFileAttachment",
	Name = "smile",
	ContentBytes = Convert.FromBase64String("a0b1c76de9f7="),
	ContentType = "image/gif",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Todo.Lists["{todoTaskList-id}"].Tasks["{todoTask-id}"].Attachments.PostAsync(requestBody);
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

requestBody := graphmodels.NewAttachmentBase()
name := "smile"
requestBody.SetName(&name) 
contentBytes := []byte("a0b1c76de9f7=")
requestBody.SetContentBytes(&contentBytes) 
contentType := "image/gif"
requestBody.SetContentType(&contentType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
attachments, err := graphClient.Me().Todo().Lists().ByTodoTaskListId("todoTaskList-id").Tasks().ByTodoTaskId("todoTask-id").Attachments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TaskFileAttachment attachmentBase = new TaskFileAttachment();
attachmentBase.setOdataType("#microsoft.graph.taskFileAttachment");
attachmentBase.setName("smile");
byte[] contentBytes = Base64.getDecoder().decode("a0b1c76de9f7=");
attachmentBase.setContentBytes(contentBytes);
attachmentBase.setContentType("image/gif");
AttachmentBase result = graphClient.me().todo().lists().byTodoTaskListId("{todoTaskList-id}").tasks().byTodoTaskId("{todoTask-id}").attachments().post(attachmentBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const attachmentBase = {
  '@odata.type': '#microsoft.graph.taskFileAttachment',
  name: 'smile',
  contentBytes: 'a0b1c76de9f7=',
  contentType: 'image/gif'
};

await client.api('/me/todo/lists/AAMkpsDRVK=/tasks/AAKdfjhgsjhgJ=/attachments')
	.post(attachmentBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TaskFileAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TaskFileAttachment();
$requestBody->setOdataType('#microsoft.graph.taskFileAttachment');
$requestBody->setName('smile');
$requestBody->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('a0b1c76de9f7=')));
$requestBody->setContentType('image/gif');

$result = $graphServiceClient->me()->todo()->lists()->byTodoTaskListId('todoTaskList-id')->tasks()->byTodoTaskId('todoTask-id')->attachments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	"@odata.type" = "#microsoft.graph.taskFileAttachment"
	name = "smile"
	contentBytes = "a0b1c76de9f7="
	contentType = "image/gif"
}

# A UPN can also be used as -UserId.
New-MgUserTodoListTaskAttachment -UserId $userId -TodoTaskListId $todoTaskListId -TodoTaskId $todoTaskId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.task_file_attachment import TaskFileAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TaskFileAttachment(
	odata_type = "#microsoft.graph.taskFileAttachment",
	name = "smile",
	content_bytes = base64.urlsafe_b64decode("a0b1c76de9f7="),
	content_type = "image/gif",
)

result = await graph_client.me.todo.lists.by_todo_task_list_id('todoTaskList-id').tasks.by_todo_task_id('todoTask-id').attachments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.taskFileAttachment",
  "id": "AAMkADNkN2R",
  "lastModifiedDateTime": "2017-01-26T08:48:28Z",
  "name": "smile",
  "contentType": "image/gif",
  "size": 1008
}
```
