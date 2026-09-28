<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-post-threads?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create conversation thread

Namespace: microsoft.graph

Start a new group conversation by first creating a thread.

A new conversation, conversation thread, and post are created in the group. Use [reply thread](https://learn.microsoft.com/en-us/graph/api/conversationthread-reply?view=graph-rest-1.0) or [reply post](https://learn.microsoft.com/en-us/graph/api/post-reply?view=graph-rest-1.0) to further post to that thread.

Note: You can also [start a new thread in an existing conversation](https://learn.microsoft.com/en-us/graph/api/conversation-post-threads?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | Not supported. |

## HTTP request

```http
POST /groups/{id}/threads
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) object containing a [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0).

## Response

If successful, this method returns `201 Created` response code and [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/groups/{id}/threads
Content-type: application/json

{
  "topic": "New Conversation Thread Topic",
  "posts": [{
    "body": {
      "contentType": "html",
      "content": "this is body content"
    },
    "newParticipants": [{
      "emailAddress": {
        "name": "Alex Darrow",
        "address": "alexd@contoso.com"
      }
    }]
  }]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ConversationThread
{
	Topic = "New Conversation Thread Topic",
	Posts = new List<Post>
	{
		new Post
		{
			Body = new ItemBody
			{
				ContentType = BodyType.Html,
				Content = "this is body content",
			},
			NewParticipants = new List<Recipient>
			{
				new Recipient
				{
					EmailAddress = new EmailAddress
					{
						Name = "Alex Darrow",
						Address = "alexd@contoso.com",
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Threads.PostAsync(requestBody);
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
topic := "New Conversation Thread Topic"
requestBody.SetTopic(&topic) 


post := graphmodels.NewPost()
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "this is body content"
body.SetContent(&content) 
post.SetBody(body)


recipient := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
name := "Alex Darrow"
emailAddress.SetName(&name) 
address := "alexd@contoso.com"
emailAddress.SetAddress(&address) 
recipient.SetEmailAddress(emailAddress)

newParticipants := []graphmodels.Recipientable {
	recipient,
}
post.SetNewParticipants(newParticipants)

posts := []graphmodels.Postable {
	post,
}
requestBody.SetPosts(posts)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
threads, err := graphClient.Groups().ByGroupId("group-id").Threads().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConversationThread conversationThread = new ConversationThread();
conversationThread.setTopic("New Conversation Thread Topic");
LinkedList<Post> posts = new LinkedList<Post>();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("this is body content");
post.setBody(body);
LinkedList<Recipient> newParticipants = new LinkedList<Recipient>();
Recipient recipient = new Recipient();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setName("Alex Darrow");
emailAddress.setAddress("alexd@contoso.com");
recipient.setEmailAddress(emailAddress);
newParticipants.add(recipient);
post.setNewParticipants(newParticipants);
posts.add(post);
conversationThread.setPosts(posts);
ConversationThread result = graphClient.groups().byGroupId("{group-id}").threads().post(conversationThread);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conversationThread = {
  topic: 'New Conversation Thread Topic',
  posts: [{
    body: {
      contentType: 'html',
      content: 'this is body content'
    },
    newParticipants: [{
      emailAddress: {
        name: 'Alex Darrow',
        address: 'alexd@contoso.com'
      }
    }]
  }]
};

await client.api('/groups/{id}/threads')
	.post(conversationThread);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ConversationThread;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Recipient;
use Microsoft\Graph\Generated\Models\EmailAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ConversationThread();
$requestBody->setTopic('New Conversation Thread Topic');
$postsPost1 = new Post();
$postsPost1Body = new ItemBody();
$postsPost1Body->setContentType(new BodyType('html'));
$postsPost1Body->setContent('this is body content');
$postsPost1->setBody($postsPost1Body);
$newParticipantsRecipient1 = new Recipient();
$newParticipantsRecipient1EmailAddress = new EmailAddress();
$newParticipantsRecipient1EmailAddress->setName('Alex Darrow');
$newParticipantsRecipient1EmailAddress->setAddress('alexd@contoso.com');
$newParticipantsRecipient1->setEmailAddress($newParticipantsRecipient1EmailAddress);
$newParticipantsArray []= $newParticipantsRecipient1;
$postsPost1->setNewParticipants($newParticipantsArray);

$postsArray []= $postsPost1;
$requestBody->setPosts($postsArray);


$result = $graphServiceClient->groups()->byGroupId('group-id')->threads()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	topic = "New Conversation Thread Topic"
	posts = @(
		@{
			body = @{
				contentType = "html"
				content = "this is body content"
			}
			newParticipants = @(
				@{
					emailAddress = @{
						name = "Alex Darrow"
						address = "alexd@contoso.com"
					}
				}
			)
		}
	)
}

New-MgGroupThread -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conversation_thread import ConversationThread
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.recipient import Recipient
from msgraph.generated.models.email_address import EmailAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ConversationThread(
	topic = "New Conversation Thread Topic",
	posts = [
		Post(
			body = ItemBody(
				content_type = BodyType.Html,
				content = "this is body content",
			),
			new_participants = [
				Recipient(
					email_address = EmailAddress(
						name = "Alex Darrow",
						address = "alexd@contoso.com",
					),
				),
			],
		),
	],
)

result = await graph_client.groups.by_group_id('group-id').threads.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "toRecipients": [
    {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    }
  ],
  "topic": "topic-value",
  "hasAttachments": true,
  "lastDeliveredDateTime": "datetime-value",
  "uniqueSenders": [
    "uniqueSenders-value"
  ],
  "ccRecipients": [
    {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    }
  ]
}
```
