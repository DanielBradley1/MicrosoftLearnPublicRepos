<!-- Source: https://learn.microsoft.com/en-us/graph/api/todotask-delta?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# todoTask: delta

Namespace: microsoft.graph

Get a set of [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) resources that have been added, deleted, or updated in a specified [todoTaskList](https://learn.microsoft.com/en-us/graph/api/resources/todotasklist?view=graph-rest-1.0).

A **delta** function call for **todoTask** resources in a **todoTaskList** is similar to a GET request, except that by appropriately applying [state tokens](https://learn.microsoft.com/en-us/graph/delta-query-overview) in one or more of these calls, you can query for incremental changes in the **todoTask** in that **todoTaskList**. This allows you to maintain and synchronize a local store of a user's **todoTask** resources without having to fetch the entire set from the server every time.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.ReadWrite | Tasks.Read |
| Delegated \(personal Microsoft account\) | Tasks.ReadWrite | Tasks.Read |
| Application | Tasks.ReadWrite.All | Tasks.Read.All |

## HTTP request

```http
GET /me/todo/lists/{id}/tasks/delta
GET /users/{id|userPrincipalName}/todo/lists/{todoTaskListId}/tasks/delta
```

## Query parameters

Tracking changes in a **todoTask** collection incurs a round of one or more **delta** function calls. If you use any query parameter \(other than `$deltatoken` and `$skiptoken`\), you must specify it in the initial **delta** request. Microsoft Graph automatically encodes any specified parameters into the token portion of the `@odata.nextLink` or `@odata.deltaLink` URL provided in the response. You only need to specify any desired query parameters once upfront. In subsequent requests, simply copy and apply the `@odata.nextLink` or `@odata.deltaLink` URL from the previous response, as that URL already includes the encoded, desired parameters.

| Query parameter | Type | Description |
| :--- | :--- | :--- |
| $deltatoken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.deltaLink` URL of the previous **delta** function call for the same todoTask collection, indicating the completion of that round of change tracking. Save and apply the entire `@odata.deltaLink` URL including this token in the first request of the next round of change tracking for that collection. |
| $skiptoken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.nextLink` URL of the previous **delta** function call, indicating there are further changes to be tracked in the same todoTask collection. |

### OData query parameters

- You can use a `$select` query parameter as in any GET request to specify only the properties your need for best performance. The *id* property is always returned.
- Delta query support `$select`, `$top`, and `$expand` for todoTask.
- There is limited support for `$filter` and `$orderby`:

  - The only supported `$filter` expressions are `$filter=receivedDateTime+ge+{value}` or `$filter=receivedDateTime+gt+{value}`.
  - The only supported `$orderby` expression is `$orderby=receivedDateTime+desc`. If you don't include an `$orderby` expression, the return order is not guaranteed.

- There is no support for `$search`.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | application/json. Required. |
| Prefer | string | odata.maxpagesize={x}. Optional. |

## Response

If successful, this method returns a `200 OK` response code and [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) collection object in the response body.

## Example

### Request

To track changes in the **todoTask** resources in a **todoTaskList** since the last round of change tracking, you would make one or more **delta** function calls to get the set of incremental changes. The following example shows how to begin a next round of change tracking, using the URL in the `@odata.deltaLink` returned from the last **delta** function call of the last round, which contains a `deltaToken`. This **delta** function call limits the maximum number of **todoTask** in the response body to 2.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/todo/lists/gDbc8U7HGwADDZocJgAAAA==/tasks/delta?$deltatoken=w0vf2jHg2mBXU-I2AK0FSWl0dopNtG8u5YoM
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
// Note: The URI string parameter used with WithUrl() can be retrieved using the OdataNextLink or OdataDeltaLink property from a response object
var result = await graphClient.Me.Todo.Lists["{todoTaskList-id}"].Tasks.Delta.WithUrl("https://graph.microsoft.com/v1.0/me/todo/lists/gDbc8U7HGwADDZocJgAAAA==/tasks/delta?$deltatoken=w0vf2jHg2mBXU-I2AK0FSWl0dopNtG8u5YoM").GetAsDeltaGetResponseAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestDeltatoken := "w0vf2jHg2mBXU-I2AK0FSWl0dopNtG8u5YoM"

requestParameters := &graphusers.TodoListsItemTasksDeltaRequestBuilderGetQueryParameters{
	Deltatoken: &requestDeltatoken,
}
configuration := &graphusers.TodoListsItemTasksDeltaRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Me().Todo().Lists().ByTodoTaskListId("todoTaskList-id").Tasks().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.todo.lists.item.tasks.delta.DeltaRequestBuilder deltaRequestBuilder = new com.microsoft.graph.users.item.todo.lists.item.tasks.delta.DeltaRequestBuilder("https://graph.microsoft.com/v1.0/me/todo/lists/gDbc8U7HGwADDZocJgAAAA==/tasks/delta?$deltatoken=w0vf2jHg2mBXU-I2AK0FSWl0dopNtG8u5YoM", graphClient.getRequestAdapter());
com.microsoft.graph.users.item.todo.lists.item.tasks.delta.DeltaGetResponse result = deltaRequestBuilder.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/me/todo/lists/gDbc8U7HGwADDZocJgAAAA==/tasks/delta')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Todo\Lists\Item\Tasks\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->deltatoken = "w0vf2jHg2mBXU-I2AK0FSWl0dopNtG8u5YoM";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->todo()->lists()->byTodoTaskListId('todoTaskList-id')->tasks()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

# A UPN can also be used as -UserId.
Get-MgUserTodoTaskDelta -UserId $userId -TodoTaskListId $todoTaskListId -Deltatoken "w0vf2jHg2mBXU-I2AK0FSWl0dopNtG8u5YoM" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.todo.lists.item.tasks.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		deltatoken = "w0vf2jHg2mBXU-I2AK0FSWl0dopNtG8u5YoM",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.todo.lists.by_todo_task_list_id('todoTaskList-id').tasks.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

If the request is successful, the response would include a state token, which is either a *skipToken*  
\(in an *@odata.nextLink* response header\) or a *deltaToken* \(in an *@odata.deltaLink* response header\). Respectively, they indicate whether you should continue with the round or you have completed getting all the changes for that round.

The response below shows a *skipToken* in an *@odata.nextLink* response header.

Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
   "@odata.deltaLink":"https://graph.microsoft.com/v1.0/me/todo/lists/gDbc8U7HGwADDZocJgAAAA==/tasks/delta?$deltatoken=MoVMZ_DzHG4AhT3WE8VioVS1IXZJ-ArqK5fknOjnKFY",
   "value":[
      {
         "@odata.etag":"W/\"4rfRVIPi9EqXgDbc8U7HGwADLLQ9xQ==\"",
         "importance":"normal",
         "isReminderOn":false,
         "status":"notStarted",
         "title":"empty task3",
         "createdDateTime":"2020-08-12T04:54:29.1925206Z",
         "lastModifiedDateTime":"2020-08-12T04:54:29.4903939Z",
         "id":"AAMkADMwNTcyZjQzLTdkMGItNDdjMy04ZTYwLTJhYmUzNGI5ZDEwMwBGAAAAAAB5M0K0qlJySLOAgV22zPnuBwDit9FUg_L0SpeANtzxTscbAAMNmhwmAADit9FUg_L0SpeANtzxTscbAAMxlnrYAAA=",
         "body":{
            "content":"",
            "contentType":"text"
         }
      }
   ]
}
```

## Related content

- [Microsoft Graph delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview)
