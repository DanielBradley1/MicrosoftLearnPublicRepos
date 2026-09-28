<!-- Source: https://learn.microsoft.com/en-us/graph/api/todotasklist-post-tasks?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Create todoTask

Namespace: microsoft.graph

Create a new task object in a specified [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0).

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
POST /me/todo/lists/{todoTaskListId}/tasks
POST /users/{id|userPrincipalName}/todo/lists/{todoTaskListId}/tasks
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) object.

The following table lists the properties that are required when you create the [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the task. By default, this value changes when the item is moved from one list to another. |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The task body that typically contains information about the task. |
| categories | String collection | The categories associated with the task. Each category corresponds to the **displayName** property of an [outlookCategory](https://learn.microsoft.com/en-us/graph/api/resources/outlookcategory?view=graph-rest-1.0) that the user has defined. |
| completedDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date in the specified time zone that the task was finished. |
| dueDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date in the specified time zone that the task is to be finished. |
| importance | importance | The importance of the task. The possible values are: `low`, `normal`, `high`. |
| isReminderOn | Boolean | Set to true if an alert is set to remind the user of the task. |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The recurrence pattern for the task. |
| reminderDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date and time for a reminder alert of the task to occur. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date in the specified time zone at which the task is scheduled to start. |
| status | taskStatus | Indicates the state or progress of the task. The possible values are: `notStarted`, `inProgress`, `completed`, `waitingOnOthers`, `deferred`. |
| title | String | A brief description of the task. |
| createdDateTime | DateTimeOffset | The date and time when the task was created. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the task was last modified. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |
| bodyLastModifiedDateTime | DateTimeOffset | The date and time when the task was last modified. By default, it is in UTC. You can provide a custom time zone in the request header. The property value uses ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2020 would look like this: '2020-01-01T00:00:00Z'. |

## Response

If successful, this method returns a `201 Created` response code and a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example creates a **todoTask** in the specified task list, and includes a [linkedResource](https://learn.microsoft.com/en-us/graph/api/resources/linkedresource?view=graph-rest-1.0).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/todo/lists/AQMkADAwATM0MDAAMS0yMDkyLWVjMzYtM/tasks
Content-Type: application/json

{
   "title":"A new task",
   "categories": ["Important"],
   "linkedResources":[
      {
         "webUrl":"http://microsoft.com",
         "applicationName":"Microsoft",
         "displayName":"Microsoft"
      }
   ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TodoTask
{
	Title = "A new task",
	Categories = new List<string>
	{
		"Important",
	},
	LinkedResources = new List<LinkedResource>
	{
		new LinkedResource
		{
			WebUrl = "http://microsoft.com",
			ApplicationName = "Microsoft",
			DisplayName = "Microsoft",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Todo.Lists["{todoTaskList-id}"].Tasks.PostAsync(requestBody);
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

requestBody := graphmodels.NewTodoTask()
title := "A new task"
requestBody.SetTitle(&title) 
categories := []string {
	"Important",
}
requestBody.SetCategories(categories)


linkedResource := graphmodels.NewLinkedResource()
webUrl := "http://microsoft.com"
linkedResource.SetWebUrl(&webUrl) 
applicationName := "Microsoft"
linkedResource.SetApplicationName(&applicationName) 
displayName := "Microsoft"
linkedResource.SetDisplayName(&displayName) 

linkedResources := []graphmodels.LinkedResourceable {
	linkedResource,
}
requestBody.SetLinkedResources(linkedResources)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tasks, err := graphClient.Me().Todo().Lists().ByTodoTaskListId("todoTaskList-id").Tasks().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TodoTask todoTask = new TodoTask();
todoTask.setTitle("A new task");
LinkedList<String> categories = new LinkedList<String>();
categories.add("Important");
todoTask.setCategories(categories);
LinkedList<LinkedResource> linkedResources = new LinkedList<LinkedResource>();
LinkedResource linkedResource = new LinkedResource();
linkedResource.setWebUrl("http://microsoft.com");
linkedResource.setApplicationName("Microsoft");
linkedResource.setDisplayName("Microsoft");
linkedResources.add(linkedResource);
todoTask.setLinkedResources(linkedResources);
TodoTask result = graphClient.me().todo().lists().byTodoTaskListId("{todoTaskList-id}").tasks().post(todoTask);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const todoTask = {
   title: 'A new task',
   categories: ['Important'],
   linkedResources: [
      {
         webUrl: 'http://microsoft.com',
         applicationName: 'Microsoft',
         displayName: 'Microsoft'
      }
   ]
};

await client.api('/me/todo/lists/AQMkADAwATM0MDAAMS0yMDkyLWVjMzYtM/tasks')
	.post(todoTask);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TodoTask;
use Microsoft\Graph\Generated\Models\LinkedResource;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TodoTask();
$requestBody->setTitle('A new task');
$requestBody->setCategories(['Important', 	]);
$linkedResourcesLinkedResource1 = new LinkedResource();
$linkedResourcesLinkedResource1->setWebUrl('http://microsoft.com');
$linkedResourcesLinkedResource1->setApplicationName('Microsoft');
$linkedResourcesLinkedResource1->setDisplayName('Microsoft');
$linkedResourcesArray []= $linkedResourcesLinkedResource1;
$requestBody->setLinkedResources($linkedResourcesArray);


$result = $graphServiceClient->me()->todo()->lists()->byTodoTaskListId('todoTaskList-id')->tasks()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	title = "A new task"
	categories = @(
	"Important"
)
linkedResources = @(
	@{
		webUrl = "http://microsoft.com"
		applicationName = "Microsoft"
		displayName = "Microsoft"
	}
)
}

# A UPN can also be used as -UserId.
New-MgUserTodoListTask -UserId $userId -TodoTaskListId $todoTaskListId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.todo_task import TodoTask
from msgraph.generated.models.linked_resource import LinkedResource
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TodoTask(
	title = "A new task",
	categories = [
		"Important",
	],
	linked_resources = [
		LinkedResource(
			web_url = "http://microsoft.com",
			application_name = "Microsoft",
			display_name = "Microsoft",
		),
	],
)

result = await graph_client.me.todo.lists.by_todo_task_list_id('todoTaskList-id').tasks.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

**Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
   "@odata.etag":"W/\"xzyPKP0BiUGgld+lMKXwbQAAnBoTIw==\"",
   "importance":"low",
   "isReminderOn":false,
   "status":"notStarted",
   "title":"A new task",
   "createdDateTime":"2020-08-18T09:03:05.8339192Z",
   "lastModifiedDateTime":"2020-08-18T09:03:06.0827766Z",
   "categories": ["Important"],
   "id":"AlMKXwbQAAAJws6wcAAAA=",
   "body":{
      "content":"",
      "contentType":"text"
   },
   "linkedResources":[
      {
         "id":"f9cddce2-dce2-f9cd-e2dc-cdf9e2dccdf9",
         "webUrl":"http://microsoft.com",
         "applicationName":"Microsoft",
         "displayName":"Microsoft"
      }
   ]
}
```
