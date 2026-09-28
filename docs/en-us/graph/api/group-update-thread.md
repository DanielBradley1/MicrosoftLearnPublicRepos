<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-update-thread?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Update conversation thread

Namespace: microsoft.graph Update a [thread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-Conversation.ReadWrite.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-Conversation.ReadWrite.All | Group.ReadWrite.All |

## HTTP request

```http
PATCH /groups/{id}/threads/{id}
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed.

## Response

If successful, this method returns a `204 No Content` response code.

## Example

#### Request

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
PATCH https://graph.microsoft.com/v1.0/groups/02bd9fd6-8f93-4758-87c3-1fb73740a315/threads/AAQkAGI5MWY5ZmUyLTJiNzYtNDE0ZC04OWEwLWM3M2FjYmM3NzNlZgMkABAAG5c7eC4NYEynIoXsuxXB9RAAG5c7eC4NYEynIoXsuxXB9Q==
Content-type: application/json

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "iCalUId": "iCalUId-value",
  "reminderMinutesBeforeStart": 99,
  "isReminderOn": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ConversationThread
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"originalStartTimeZone" , "originalStartTimeZone-value"
		},
		{
			"originalEndTimeZone" , "originalEndTimeZone-value"
		},
		{
			"responseStatus" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"response", new UntypedString("")
				},
				{
					"time", new UntypedString("datetime-value")
				},
			})
		},
		{
			"iCalUId" , "iCalUId-value"
		},
		{
			"reminderMinutesBeforeStart" , 99
		},
		{
			"isReminderOn" , true
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Threads["{conversationThread-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewConversationThread()
additionalData := map[string]interface{}{
	"originalStartTimeZone" : "originalStartTimeZone-value", 
	"originalEndTimeZone" : "originalEndTimeZone-value", 
responseStatus := graph.New()
response := ""
responseStatus.SetResponse(&response) 
time := "datetime-value"
responseStatus.SetTime(&time) 
	requestBody.SetResponseStatus(responseStatus)
	"iCalUId" : "iCalUId-value", 
	"reminderMinutesBeforeStart" : int32(99) , 
	isReminderOn := true
requestBody.SetIsReminderOn(&isReminderOn) 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
threads, err := graphClient.Groups().ByGroupId("group-id").Threads().ByConversationThreadId("conversationThread-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConversationThread conversationThread = new ConversationThread();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("originalStartTimeZone", "originalStartTimeZone-value");
additionalData.put("originalEndTimeZone", "originalEndTimeZone-value");
 responseStatus = new ();
responseStatus.setResponse("");
responseStatus.setTime("datetime-value");
additionalData.put("responseStatus", responseStatus);
additionalData.put("iCalUId", "iCalUId-value");
additionalData.put("reminderMinutesBeforeStart", 99);
additionalData.put("isReminderOn", true);
conversationThread.setAdditionalData(additionalData);
ConversationThread result = graphClient.groups().byGroupId("{group-id}").threads().byConversationThreadId("{conversationThread-id}").patch(conversationThread);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conversationThread = {
  originalStartTimeZone: 'originalStartTimeZone-value',
  originalEndTimeZone: 'originalEndTimeZone-value',
  responseStatus: {
    response: '',
    time: 'datetime-value'
  },
  iCalUId: 'iCalUId-value',
  reminderMinutesBeforeStart: 99,
  isReminderOn: true
};

await client.api('/groups/02bd9fd6-8f93-4758-87c3-1fb73740a315/threads/AAQkAGI5MWY5ZmUyLTJiNzYtNDE0ZC04OWEwLWM3M2FjYmM3NzNlZgMkABAAG5c7eC4NYEynIoXsuxXB9RAAG5c7eC4NYEynIoXsuxXB9Q==')
	.update(conversationThread);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConversationThread;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConversationThread();
$additionalData = [
	'originalStartTimeZone' => 'originalStartTimeZone-value',
	'originalEndTimeZone' => 'originalEndTimeZone-value',
	'responseStatus' => [
		'response' => '',
		'time' => 'datetime-value',
	],
	'iCalUId' => 'iCalUId-value',
	'reminderMinutesBeforeStart' => 99,
	'isReminderOn' => true,
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->groups()->byGroupId('group-id')->threads()->byConversationThreadId('conversationThread-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	originalStartTimeZone = "originalStartTimeZone-value"
	originalEndTimeZone = "originalEndTimeZone-value"
	responseStatus = @{
		response = ""
		time = "datetime-value"
	}
	iCalUId = "iCalUId-value"
	reminderMinutesBeforeStart = 
	isReminderOn = $true
}

Update-MgGroupThread -GroupId $groupId -ConversationThreadId $conversationThreadId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conversation_thread import ConversationThread
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConversationThread(
	additional_data = {
			"original_start_time_zone" : "originalStartTimeZone-value",
			"original_end_time_zone" : "originalEndTimeZone-value",
			"response_status" : {
					"response" : "",
					"time" : "datetime-value",
			},
			"i_cal_u_id" : "iCalUId-value",
			"reminder_minutes_before_start" : 99,
			"is_reminder_on" : True,
	}
)

result = await graph_client.groups.by_group_id('group-id').threads.by_conversation_thread_id('conversationThread-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
