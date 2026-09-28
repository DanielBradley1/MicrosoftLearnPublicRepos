<!-- Source: https://learn.microsoft.com/en-us/graph/api/plannertask-post-messages?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Create plannerTaskChatMessage

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta) on a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Tasks.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /planner/tasks/{task-id}/messages
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta) object.

The following table lists the properties that you can set when you create a **plannerTaskChatMessage**.

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of the chat message. This property supports plain text and sanitized HTML. Required. |
| mentions | [plannerTaskChatMention](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmention?view=graph-rest-beta) collection | The list of mentions in the message. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta) object in the response body.

This method can return any of the [HTTP status codes](https://learn.microsoft.com/en-us/graph/errors). The most common errors that apps should handle for this method are the 400, 403, and 404 responses. For more information about these errors, see [Common Planner error conditions](https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-beta#common-planner-error-conditions).

## Examples

### Example 1: Create a message

#### Request

The following example shows a request to create a chat message.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/planner/tasks/01gzSlKkIUSUl6DF_EilrmQAKDhh/messages
Content-type: application/json

{
  "content": "This is a new chat message"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PlannerTaskChatMessage
{
	Content = "This is a new chat message",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Tasks["{plannerTask-id}"].Messages.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlannerTaskChatMessage()
content := "This is a new chat message"
requestBody.SetContent(&content) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Planner().Tasks().ByPlannerTaskId("plannerTask-id").Messages().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerTaskChatMessage plannerTaskChatMessage = new PlannerTaskChatMessage();
plannerTaskChatMessage.setContent("This is a new chat message");
PlannerTaskChatMessage result = graphClient.planner().tasks().byPlannerTaskId("{plannerTask-id}").messages().post(plannerTaskChatMessage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const plannerTaskChatMessage = {
  content: 'This is a new chat message'
};

await client.api('/planner/tasks/01gzSlKkIUSUl6DF_EilrmQAKDhh/messages')
	.version('beta')
	.post(plannerTaskChatMessage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskChatMessage;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerTaskChatMessage();
$requestBody->setContent('This is a new chat message');

$result = $graphServiceClient->planner()->tasks()->byPlannerTaskId('plannerTask-id')->messages()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

$params = @{
	content = "This is a new chat message"
}

New-MgBetaPlannerTaskMessage -PlannerTaskId $plannerTaskId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.planner_task_chat_message import PlannerTaskChatMessage
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerTaskChatMessage(
	content = "This is a new chat message",
)

result = await graph_client.planner.tasks.by_planner_task_id('plannerTask-id').messages.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#planner/tasks('01gzSlKkIUSUl6DF_EilrmQAKDhh')/messages/$entity",
  "id": "5bde7bc8-d998-4e8a-8159-93d4d7ccc3b5",
  "messageType": "richTextHtml",
  "content": "This is a new chat message",
  "createdDateTime": "2025-12-05T17:49:39.593Z",
  "parentEntityId": "01gzSlKkIUSUl6DF_EilrmQAKDhh",
  "deletedTime": null,
  "editedTime": null,
  "mentions": [],
  "reactions": [],
  "createdBy": {
    "user": {
      "id": "6463a5ce-2119-4198-9f2a-628761df4a62"
    }
  }
}
```

### Example 2: Create a message with mentions

#### Request

The following example shows a request to create a chat message with a user mention.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/planner/tasks/01gzSlKkIUSUl6DF_EilrmQAKDhh/messages
Content-type: application/json

{
  "content": "<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>",
  "mentions": [
    {
      "mentioned": "6463a5ce-2119-4198-9f2a-628761df4a62",
      "position": 0,
      "mentionType": "user"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new PlannerTaskChatMessage
{
	Content = "<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>",
	Mentions = new List<PlannerTaskChatMention>
	{
		new PlannerTaskChatMention
		{
			Mentioned = "6463a5ce-2119-4198-9f2a-628761df4a62",
			Position = 0,
			MentionType = PlannerTaskChatMentionType.User,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Planner.Tasks["{plannerTask-id}"].Messages.PostAsync(requestBody);
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

requestBody := graphmodels.NewPlannerTaskChatMessage()
content := "<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>"
requestBody.SetContent(&content) 


plannerTaskChatMention := graphmodels.NewPlannerTaskChatMention()
mentioned := "6463a5ce-2119-4198-9f2a-628761df4a62"
plannerTaskChatMention.SetMentioned(&mentioned) 
position := int32(0)
plannerTaskChatMention.SetPosition(&position) 
mentionType := graphmodels.USER_PLANNERTASKCHATMENTIONTYPE 
plannerTaskChatMention.SetMentionType(&mentionType) 

mentions := []graphmodels.PlannerTaskChatMentionable {
	plannerTaskChatMention,
}
requestBody.SetMentions(mentions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Planner().Tasks().ByPlannerTaskId("plannerTask-id").Messages().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

PlannerTaskChatMessage plannerTaskChatMessage = new PlannerTaskChatMessage();
plannerTaskChatMessage.setContent("<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>");
LinkedList<PlannerTaskChatMention> mentions = new LinkedList<PlannerTaskChatMention>();
PlannerTaskChatMention plannerTaskChatMention = new PlannerTaskChatMention();
plannerTaskChatMention.setMentioned("6463a5ce-2119-4198-9f2a-628761df4a62");
plannerTaskChatMention.setPosition(0);
plannerTaskChatMention.setMentionType(PlannerTaskChatMentionType.User);
mentions.add(plannerTaskChatMention);
plannerTaskChatMessage.setMentions(mentions);
PlannerTaskChatMessage result = graphClient.planner().tasks().byPlannerTaskId("{plannerTask-id}").messages().post(plannerTaskChatMessage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const plannerTaskChatMessage = {
  content: '<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>',
  mentions: [
    {
      mentioned: '6463a5ce-2119-4198-9f2a-628761df4a62',
      position: 0,
      mentionType: 'user'
    }
  ]
};

await client.api('/planner/tasks/01gzSlKkIUSUl6DF_EilrmQAKDhh/messages')
	.version('beta')
	.post(plannerTaskChatMessage);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskChatMessage;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskChatMention;
use Microsoft\Graph\Beta\Generated\Models\PlannerTaskChatMentionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new PlannerTaskChatMessage();
$requestBody->setContent('<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>');
$mentionsPlannerTaskChatMention1 = new PlannerTaskChatMention();
$mentionsPlannerTaskChatMention1->setMentioned('6463a5ce-2119-4198-9f2a-628761df4a62');
$mentionsPlannerTaskChatMention1->setPosition(0);
$mentionsPlannerTaskChatMention1->setMentionType(new PlannerTaskChatMentionType('user'));
$mentionsArray []= $mentionsPlannerTaskChatMention1;
$requestBody->setMentions($mentionsArray);


$result = $graphServiceClient->planner()->tasks()->byPlannerTaskId('plannerTask-id')->messages()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Planner

$params = @{
	content = "<div><span itemid="0" itemtype="https://schema.skype.com/Mention/Person"></span> Please review this task</div>"
	mentions = @(
		@{
			mentioned = "6463a5ce-2119-4198-9f2a-628761df4a62"
			position = 0
			mentionType = "user"
		}
	)
}

New-MgBetaPlannerTaskMessage -PlannerTaskId $plannerTaskId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.planner_task_chat_message import PlannerTaskChatMessage
from msgraph_beta.generated.models.planner_task_chat_mention import PlannerTaskChatMention
from msgraph_beta.generated.models.planner_task_chat_mention_type import PlannerTaskChatMentionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = PlannerTaskChatMessage(
	content = "<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>",
	mentions = [
		PlannerTaskChatMention(
			mentioned = "6463a5ce-2119-4198-9f2a-628761df4a62",
			position = 0,
			mention_type = PlannerTaskChatMentionType.User,
		),
	],
)

result = await graph_client.planner.tasks.by_planner_task_id('plannerTask-id').messages.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#planner/tasks('01gzSlKkIUSUl6DF_EilrmQAKDhh')/messages/$entity",
  "id": "7cde8bc9-e109-5f9b-9260-04e5e8ddc4c6",
  "messageType": "richTextHtml",
  "content": "<div><span itemid=\"0\" itemtype=\"https://schema.skype.com/Mention/Person\"></span> Please review this task</div>",
  "createdDateTime": "2025-12-05T17:49:39.593Z",
  "parentEntityId": "01gzSlKkIUSUl6DF_EilrmQAKDhh",
  "deletedTime": null,
  "editedTime": null,
  "mentions": [
    {
      "mentioned": "6463a5ce-2119-4198-9f2a-628761df4a62",
      "position": 0,
      "mentionType": "user"
    }
  ],
  "reactions": [],
  "createdBy": {
    "user": {
      "id": "6463a5ce-2119-4198-9f2a-628761df4a62"
    }
  }
}
```
