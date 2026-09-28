<!-- Source: https://learn.microsoft.com/en-us/graph/api/todotask-post-linkedresources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Create linkedResource

Namespace: microsoft.graph

Create a [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) object to associate a specified [task](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) with an item in a partner application. For example, you can associate a task with an email item in Outlook that spurred the task, and you can create a **linkedResource** object to track its association.

You can also create a **linkedResource** object while [creating a task](https://learn.microsoft.com/en-us/graph/api/todotasklist-post-tasks?view=graph-rest-beta&preserve-view=true&tabs=http#examples).

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
POST /me/todo/lists/{todoTaskListId}/tasks/{taskId}/linkedResources
POST /users/{id|userPrincipalName}/todo/lists/{todoTaskListId}/tasks/{taskId}/linkedResources
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Server generated Id for the linked entity Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) |
| webUrl | String | Deeplink to the linked entity |
| applicationName | String | Field indicating app name of the source that is sending the linked entity |
| displayName | String | Field indicating title of the linked entity. |
| externalId | String | Id of the object that is associated with this task on the third-party/partner system |

## Response

If successful, this method returns a `201 Created` response code and a [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/me/todo/lists/dfsdc-f9dfdfs-dcsda9/tasks/e2dc-f9cce2-dce29/linkedResources
Content-Type: application/json

{
  "webUrl": "https://microsoft.com",
  "applicationName": "Microsoft",
  "displayName": "Microsoft",
  "externalId": "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new LinkedResource
{
	WebUrl = "https://microsoft.com",
	ApplicationName = "Microsoft",
	DisplayName = "Microsoft",
	ExternalId = "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Todo.Lists["{todoTaskList-id}"].Tasks["{todoTask-id}"].LinkedResources.PostAsync(requestBody);
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

requestBody := graphmodels.NewLinkedResource()
webUrl := "https://microsoft.com"
requestBody.SetWebUrl(&webUrl) 
applicationName := "Microsoft"
requestBody.SetApplicationName(&applicationName) 
displayName := "Microsoft"
requestBody.SetDisplayName(&displayName) 
externalId := "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9"
requestBody.SetExternalId(&externalId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
linkedResources, err := graphClient.Me().Todo().Lists().ByTodoTaskListId("todoTaskList-id").Tasks().ByTodoTaskId("todoTask-id").LinkedResources().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LinkedResource linkedResource = new LinkedResource();
linkedResource.setWebUrl("https://microsoft.com");
linkedResource.setApplicationName("Microsoft");
linkedResource.setDisplayName("Microsoft");
linkedResource.setExternalId("dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9");
LinkedResource result = graphClient.me().todo().lists().byTodoTaskListId("{todoTaskList-id}").tasks().byTodoTaskId("{todoTask-id}").linkedResources().post(linkedResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const linkedResource = {
  webUrl: 'https://microsoft.com',
  applicationName: 'Microsoft',
  displayName: 'Microsoft',
  externalId: 'dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9'
};

await client.api('/me/todo/lists/dfsdc-f9dfdfs-dcsda9/tasks/e2dc-f9cce2-dce29/linkedResources')
	.post(linkedResource);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\LinkedResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LinkedResource();
$requestBody->setWebUrl('https://microsoft.com');
$requestBody->setApplicationName('Microsoft');
$requestBody->setDisplayName('Microsoft');
$requestBody->setExternalId('dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9');

$result = $graphServiceClient->me()->todo()->lists()->byTodoTaskListId('todoTaskList-id')->tasks()->byTodoTaskId('todoTask-id')->linkedResources()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	webUrl = "https://microsoft.com"
	applicationName = "Microsoft"
	displayName = "Microsoft"
	externalId = "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9"
}

# A UPN can also be used as -UserId.
New-MgUserTodoListTaskLinkedResource -UserId $userId -TodoTaskListId $todoTaskListId -TodoTaskId $todoTaskId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.linked_resource import LinkedResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LinkedResource(
	web_url = "https://microsoft.com",
	application_name = "Microsoft",
	display_name = "Microsoft",
	external_id = "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9",
)

result = await graph_client.me.todo.lists.by_todo_task_list_id('todoTaskList-id').tasks.by_todo_task_id('todoTask-id').linked_resources.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.linkedResource",
  "id": "f9cddce2-dce2-f9cd-e2dc-cdf9e2dccdf9",
  "webUrl": "http:://microsoft.com",
  "applicationName": "Microsoft",
  "displayName": "Microsoft",
  "externalId": "dk9cddce2-dce2-f9dd-e2dc-cdf9e2dccdf9"
}
```
