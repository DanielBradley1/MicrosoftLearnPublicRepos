<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-post-conversations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create conversation

Namespace: microsoft.graph Create a new [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) by including a thread and a post.

Use [reply thread](https://learn.microsoft.com/en-us/graph/api/conversationthread-reply?view=graph-rest-1.0) or [reply post](https://learn.microsoft.com/en-us/graph/api/post-reply?view=graph-rest-1.0) to further post to that conversation.

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
POST /groups/{id}/conversations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) object containing a [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) and a [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0).

## Response

If successful, this method returns `201 Created` response code and [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) object in the response body.

The response includes the IDs for the new conversation and thread, which you can use in the [list posts](https://learn.microsoft.com/en-us/graph/api/conversationthread-list-posts?view=graph-rest-1.0) operation to get the new post as well.

## Example

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
POST https://graph.microsoft.com/v1.0/groups/29981b6a-0e57-42dc-94c9-cd24f5306196/conversations
Content-type: application/json

{
    "topic": "Take your wellness days and rest",
    "threads": [
        {
            "posts": [
                {
                    "body": {
                        "contentType": "html",
                        "content": "Contoso cares about you: Rest and Recharge"
                    },
                    "newParticipants": [
                        {
                            "emailAddress": {
                                "name": "Adele Vance",
                                "address": "AdeleV@contoso.com"
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Conversation
{
	Topic = "Take your wellness days and rest",
	Threads = new List<ConversationThread>
	{
		new ConversationThread
		{
			Posts = new List<Post>
			{
				new Post
				{
					Body = new ItemBody
					{
						ContentType = BodyType.Html,
						Content = "Contoso cares about you: Rest and Recharge",
					},
					NewParticipants = new List<Recipient>
					{
						new Recipient
						{
							EmailAddress = new EmailAddress
							{
								Name = "Adele Vance",
								Address = "AdeleV@contoso.com",
							},
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Conversations.PostAsync(requestBody);
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

requestBody := graphmodels.NewConversation()
topic := "Take your wellness days and rest"
requestBody.SetTopic(&topic) 


conversationThread := graphmodels.NewConversationThread()


post := graphmodels.NewPost()
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Contoso cares about you: Rest and Recharge"
body.SetContent(&content) 
post.SetBody(body)


recipient := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
name := "Adele Vance"
emailAddress.SetName(&name) 
address := "AdeleV@contoso.com"
emailAddress.SetAddress(&address) 
recipient.SetEmailAddress(emailAddress)

newParticipants := []graphmodels.Recipientable {
	recipient,
}
post.SetNewParticipants(newParticipants)

posts := []graphmodels.Postable {
	post,
}
conversationThread.SetPosts(posts)

threads := []graphmodels.ConversationThreadable {
	conversationThread,
}
requestBody.SetThreads(threads)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
conversations, err := graphClient.Groups().ByGroupId("group-id").Conversations().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Conversation conversation = new Conversation();
conversation.setTopic("Take your wellness days and rest");
LinkedList<ConversationThread> threads = new LinkedList<ConversationThread>();
ConversationThread conversationThread = new ConversationThread();
LinkedList<Post> posts = new LinkedList<Post>();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Contoso cares about you: Rest and Recharge");
post.setBody(body);
LinkedList<Recipient> newParticipants = new LinkedList<Recipient>();
Recipient recipient = new Recipient();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setName("Adele Vance");
emailAddress.setAddress("AdeleV@contoso.com");
recipient.setEmailAddress(emailAddress);
newParticipants.add(recipient);
post.setNewParticipants(newParticipants);
posts.add(post);
conversationThread.setPosts(posts);
threads.add(conversationThread);
conversation.setThreads(threads);
Conversation result = graphClient.groups().byGroupId("{group-id}").conversations().post(conversation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const conversation = {
    topic: 'Take your wellness days and rest',
    threads: [
        {
            posts: [
                {
                    body: {
                        contentType: 'html',
                        content: 'Contoso cares about you: Rest and Recharge'
                    },
                    newParticipants: [
                        {
                            emailAddress: {
                                name: 'Adele Vance',
                                address: 'AdeleV@contoso.com'
                            }
                        }
                    ]
                }
            ]
        }
    ]
};

await client.api('/groups/29981b6a-0e57-42dc-94c9-cd24f5306196/conversations')
	.post(conversation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Conversation;
use Microsoft\Graph\Generated\Models\ConversationThread;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Recipient;
use Microsoft\Graph\Generated\Models\EmailAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Conversation();
$requestBody->setTopic('Take your wellness days and rest');
$threadsConversationThread1 = new ConversationThread();
$postsPost1 = new Post();
$postsPost1Body = new ItemBody();
$postsPost1Body->setContentType(new BodyType('html'));
$postsPost1Body->setContent('Contoso cares about you: Rest and Recharge');
$postsPost1->setBody($postsPost1Body);
$newParticipantsRecipient1 = new Recipient();
$newParticipantsRecipient1EmailAddress = new EmailAddress();
$newParticipantsRecipient1EmailAddress->setName('Adele Vance');
$newParticipantsRecipient1EmailAddress->setAddress('AdeleV@contoso.com');
$newParticipantsRecipient1->setEmailAddress($newParticipantsRecipient1EmailAddress);
$newParticipantsArray []= $newParticipantsRecipient1;
$postsPost1->setNewParticipants($newParticipantsArray);

$postsArray []= $postsPost1;
$threadsConversationThread1->setPosts($postsArray);

$threadsArray []= $threadsConversationThread1;
$requestBody->setThreads($threadsArray);


$result = $graphServiceClient->groups()->byGroupId('group-id')->conversations()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	topic = "Take your wellness days and rest"
	threads = @(
		@{
			posts = @(
				@{
					body = @{
						contentType = "html"
						content = "Contoso cares about you: Rest and Recharge"
					}
					newParticipants = @(
						@{
							emailAddress = @{
								name = "Adele Vance"
								address = "AdeleV@contoso.com"
							}
						}
					)
				}
			)
		}
	)
}

New-MgGroupConversation -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.conversation import Conversation
from msgraph.generated.models.conversation_thread import ConversationThread
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.recipient import Recipient
from msgraph.generated.models.email_address import EmailAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Conversation(
	topic = "Take your wellness days and rest",
	threads = [
		ConversationThread(
			posts = [
				Post(
					body = ItemBody(
						content_type = BodyType.Html,
						content = "Contoso cares about you: Rest and Recharge",
					),
					new_participants = [
						Recipient(
							email_address = EmailAddress(
								name = "Adele Vance",
								address = "AdeleV@contoso.com",
							),
						),
					],
				),
			],
		),
	],
)

result = await graph_client.groups.by_group_id('group-id').conversations.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('4d81ce71-486c-41e9-afc5-e41bf2d0722a')/conversations/$entity",
    "id": "AAQkAGRhZmRhMWM3LTYwZTktNDZmYy1hNWU1LThhZWU4NzI2YTEyZgAQADamkjVbzvRKnUq1oBRdwhk=",
    "threads": [
        {
            "id": "AAQkAGRhZmRhMWM3LTYwZTktNDZmYy1hNWU1LThhZWU4NzI2YTEyZgMkABAANqaSNVvO9EqdSrWgFF3CGRAANqaSNVvO9EqdSrWgFF3CGQ=="
        }
    ]
}
```
