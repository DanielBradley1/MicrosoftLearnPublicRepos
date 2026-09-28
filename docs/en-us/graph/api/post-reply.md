<!-- Source: https://learn.microsoft.com/en-us/graph/api/post-reply?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# post: reply

Namespace: microsoft.graph

Reply to a post and add a new post to the specified thread in a group conversation.

You can specify both the parent conversation and thread in the request, or, you can specify just the parent thread without the parent conversation.

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
| Application | Group.ReadWrite.All |

## HTTP request

```http
POST /groups/{id}/threads/{id}/posts/{id}/reply
POST /groups/{id}/conversations/{id}/threads/{id}/posts/{id}/reply
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| post | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | The new post that is being replied with. |

## Response

If successful, this method returns `202 Accepted` response code. It doesn't return anything in the response body.

## Example

Here is an example of how to call this API.

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
POST https://graph.microsoft.com/v1.0/groups/{id}/threads/{id}/posts/{id}/reply
Content-type: application/json

{
  "post": {
    "body": {
      "contentType": "",
      "content": "content-value"
    },
    "receivedDateTime": "datetime-value",
    "hasAttachments": true,
    "from": {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    },
    "sender": {
      "emailAddress": {
        "name": "name-value",
        "address": "address-value"
      }
    },
    "conversationThreadId": "conversationThreadId-value",
    "newParticipants": [
      {
        "emailAddress": {
          "name": "name-value",
          "address": "address-value"
        }
      }
    ],
    "conversationId": "conversationId-value",
    "createdDateTime": "datetime-value",
    "lastModifiedDateTime": "datetime-value",
    "changeKey": "changeKey-value",
    "categories": [
      "categories-value"
    ],
    "id": "id-value",
    "inReplyTo": {
    },
    "attachments": [
      {
        "@odata.type": "#microsoft.graph.fileAttachment",
        "lastModifiedDateTime": "datetime-value",
        "name": "name-value",
        "contentType": "contentType-value",
        "size": 99,
        "isInline": true,
        "id": "id-value"
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.Threads.Item.Posts.Item.Reply;
using Microsoft.Graph.Models;

var requestBody = new ReplyPostRequestBody
{
	Post = new Post
	{
		Body = new ItemBody
		{
			ContentType = BodyType.Text,
			Content = "content-value",
		},
		ReceivedDateTime = DateTimeOffset.Parse("datetime-value"),
		HasAttachments = true,
		From = new Recipient
		{
			EmailAddress = new EmailAddress
			{
				Name = "name-value",
				Address = "address-value",
			},
		},
		Sender = new Recipient
		{
			EmailAddress = new EmailAddress
			{
				Name = "name-value",
				Address = "address-value",
			},
		},
		ConversationThreadId = "conversationThreadId-value",
		NewParticipants = new List<Recipient>
		{
			new Recipient
			{
				EmailAddress = new EmailAddress
				{
					Name = "name-value",
					Address = "address-value",
				},
			},
		},
		ConversationId = "conversationId-value",
		CreatedDateTime = DateTimeOffset.Parse("datetime-value"),
		LastModifiedDateTime = DateTimeOffset.Parse("datetime-value"),
		ChangeKey = "changeKey-value",
		Categories = new List<string>
		{
			"categories-value",
		},
		Id = "id-value",
		InReplyTo = new Post
		{
		},
		Attachments = new List<Attachment>
		{
			new FileAttachment
			{
				OdataType = "#microsoft.graph.fileAttachment",
				LastModifiedDateTime = DateTimeOffset.Parse("datetime-value"),
				Name = "name-value",
				ContentType = "contentType-value",
				Size = 99,
				IsInline = true,
				Id = "id-value",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].Threads["{conversationThread-id}"].Posts["{post-id}"].Reply.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphgroups "github.com/microsoftgraph/msgraph-sdk-go/groups"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphgroups.NewReplyPostRequestBody()
post := graphmodels.NewPost()
body := graphmodels.NewItemBody()
contentType := graphmodels.TEXT_BODYTYPE 
body.SetContentType(&contentType) 
content := "content-value"
body.SetContent(&content) 
post.SetBody(body)
receivedDateTime , err := time.Parse(time.RFC3339, "datetime-value")
post.SetReceivedDateTime(&receivedDateTime) 
hasAttachments := true
post.SetHasAttachments(&hasAttachments) 
from := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
name := "name-value"
emailAddress.SetName(&name) 
address := "address-value"
emailAddress.SetAddress(&address) 
from.SetEmailAddress(emailAddress)
post.SetFrom(from)
sender := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
name := "name-value"
emailAddress.SetName(&name) 
address := "address-value"
emailAddress.SetAddress(&address) 
sender.SetEmailAddress(emailAddress)
post.SetSender(sender)
conversationThreadId := "conversationThreadId-value"
post.SetConversationThreadId(&conversationThreadId) 


recipient := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
name := "name-value"
emailAddress.SetName(&name) 
address := "address-value"
emailAddress.SetAddress(&address) 
recipient.SetEmailAddress(emailAddress)

newParticipants := []graphmodels.Recipientable {
	recipient,
}
post.SetNewParticipants(newParticipants)
conversationId := "conversationId-value"
post.SetConversationId(&conversationId) 
createdDateTime , err := time.Parse(time.RFC3339, "datetime-value")
post.SetCreatedDateTime(&createdDateTime) 
lastModifiedDateTime , err := time.Parse(time.RFC3339, "datetime-value")
post.SetLastModifiedDateTime(&lastModifiedDateTime) 
changeKey := "changeKey-value"
post.SetChangeKey(&changeKey) 
categories := []string {
	"categories-value",
}
post.SetCategories(categories)
id := "id-value"
post.SetId(&id) 
inReplyTo := graphmodels.NewPost()
post.SetInReplyTo(inReplyTo)


attachment := graphmodels.NewFileAttachment()
lastModifiedDateTime , err := time.Parse(time.RFC3339, "datetime-value")
attachment.SetLastModifiedDateTime(&lastModifiedDateTime) 
name := "name-value"
attachment.SetName(&name) 
contentType := "contentType-value"
attachment.SetContentType(&contentType) 
size := int32(99)
attachment.SetSize(&size) 
isInline := true
attachment.SetIsInline(&isInline) 
id := "id-value"
attachment.SetId(&id) 

attachments := []graphmodels.Attachmentable {
	attachment,
}
post.SetAttachments(attachments)
requestBody.SetPost(post)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").Threads().ByConversationThreadId("conversationThread-id").Posts().ByPostId("post-id").Reply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.threads.item.posts.item.reply.ReplyPostRequestBody replyPostRequestBody = new com.microsoft.graph.groups.item.threads.item.posts.item.reply.ReplyPostRequestBody();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Text);
body.setContent("content-value");
post.setBody(body);
OffsetDateTime receivedDateTime = OffsetDateTime.parse("datetime-value");
post.setReceivedDateTime(receivedDateTime);
post.setHasAttachments(true);
Recipient from = new Recipient();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setName("name-value");
emailAddress.setAddress("address-value");
from.setEmailAddress(emailAddress);
post.setFrom(from);
Recipient sender = new Recipient();
EmailAddress emailAddress1 = new EmailAddress();
emailAddress1.setName("name-value");
emailAddress1.setAddress("address-value");
sender.setEmailAddress(emailAddress1);
post.setSender(sender);
post.setConversationThreadId("conversationThreadId-value");
LinkedList<Recipient> newParticipants = new LinkedList<Recipient>();
Recipient recipient = new Recipient();
EmailAddress emailAddress2 = new EmailAddress();
emailAddress2.setName("name-value");
emailAddress2.setAddress("address-value");
recipient.setEmailAddress(emailAddress2);
newParticipants.add(recipient);
post.setNewParticipants(newParticipants);
post.setConversationId("conversationId-value");
OffsetDateTime createdDateTime = OffsetDateTime.parse("datetime-value");
post.setCreatedDateTime(createdDateTime);
OffsetDateTime lastModifiedDateTime = OffsetDateTime.parse("datetime-value");
post.setLastModifiedDateTime(lastModifiedDateTime);
post.setChangeKey("changeKey-value");
LinkedList<String> categories = new LinkedList<String>();
categories.add("categories-value");
post.setCategories(categories);
post.setId("id-value");
Post inReplyTo = new Post();
post.setInReplyTo(inReplyTo);
LinkedList<Attachment> attachments = new LinkedList<Attachment>();
FileAttachment attachment = new FileAttachment();
attachment.setOdataType("#microsoft.graph.fileAttachment");
OffsetDateTime lastModifiedDateTime1 = OffsetDateTime.parse("datetime-value");
attachment.setLastModifiedDateTime(lastModifiedDateTime1);
attachment.setName("name-value");
attachment.setContentType("contentType-value");
attachment.setSize(99);
attachment.setIsInline(true);
attachment.setId("id-value");
attachments.add(attachment);
post.setAttachments(attachments);
replyPostRequestBody.setPost(post);
graphClient.groups().byGroupId("{group-id}").threads().byConversationThreadId("{conversationThread-id}").posts().byPostId("{post-id}").reply().post(replyPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const reply = {
  post: {
    body: {
      contentType: '',
      content: 'content-value'
    },
    receivedDateTime: 'datetime-value',
    hasAttachments: true,
    from: {
      emailAddress: {
        name: 'name-value',
        address: 'address-value'
      }
    },
    sender: {
      emailAddress: {
        name: 'name-value',
        address: 'address-value'
      }
    },
    conversationThreadId: 'conversationThreadId-value',
    newParticipants: [
      {
        emailAddress: {
          name: 'name-value',
          address: 'address-value'
        }
      }
    ],
    conversationId: 'conversationId-value',
    createdDateTime: 'datetime-value',
    lastModifiedDateTime: 'datetime-value',
    changeKey: 'changeKey-value',
    categories: [
      'categories-value'
    ],
    id: 'id-value',
    inReplyTo: {
    },
    attachments: [
      {
        '@odata.type': '#microsoft.graph.fileAttachment',
        lastModifiedDateTime: 'datetime-value',
        name: 'name-value',
        contentType: 'contentType-value',
        size: 99,
        isInline: true,
        id: 'id-value'
      }
    ]
  }
};

await client.api('/groups/{id}/threads/{id}/posts/{id}/reply')
	.post(reply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\Threads\Item\Posts\Item\Reply\ReplyPostRequestBody;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Recipient;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\Attachment;
use Microsoft\Graph\Generated\Models\FileAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReplyPostRequestBody();
$post = new Post();
$postBody = new ItemBody();
$postBody->setContentType(new BodyType('text'));
$postBody->setContent('content-value');
$post->setBody($postBody);
$post->setReceivedDateTime(new \DateTime('datetime-value'));
$post->setHasAttachments(true);
$postFrom = new Recipient();
$postFromEmailAddress = new EmailAddress();
$postFromEmailAddress->setName('name-value');
$postFromEmailAddress->setAddress('address-value');
$postFrom->setEmailAddress($postFromEmailAddress);
$post->setFrom($postFrom);
$postSender = new Recipient();
$postSenderEmailAddress = new EmailAddress();
$postSenderEmailAddress->setName('name-value');
$postSenderEmailAddress->setAddress('address-value');
$postSender->setEmailAddress($postSenderEmailAddress);
$post->setSender($postSender);
$post->setConversationThreadId('conversationThreadId-value');
$newParticipantsRecipient1 = new Recipient();
$newParticipantsRecipient1EmailAddress = new EmailAddress();
$newParticipantsRecipient1EmailAddress->setName('name-value');
$newParticipantsRecipient1EmailAddress->setAddress('address-value');
$newParticipantsRecipient1->setEmailAddress($newParticipantsRecipient1EmailAddress);
$newParticipantsArray []= $newParticipantsRecipient1;
$post->setNewParticipants($newParticipantsArray);

$post->setConversationId('conversationId-value');
$post->setCreatedDateTime(new \DateTime('datetime-value'));
$post->setLastModifiedDateTime(new \DateTime('datetime-value'));
$post->setChangeKey('changeKey-value');
$post->setCategories(['categories-value', ]);
$post->setId('id-value');
$postInReplyTo = new Post();
$post->setInReplyTo($postInReplyTo);
$attachmentsAttachment1 = new FileAttachment();
$attachmentsAttachment1->setOdataType('#microsoft.graph.fileAttachment');
$attachmentsAttachment1->setLastModifiedDateTime(new \DateTime('datetime-value'));
$attachmentsAttachment1->setName('name-value');
$attachmentsAttachment1->setContentType('contentType-value');
$attachmentsAttachment1->setSize(99);
$attachmentsAttachment1->setIsInline(true);
$attachmentsAttachment1->setId('id-value');
$attachmentsArray []= $attachmentsAttachment1;
$post->setAttachments($attachmentsArray);

$requestBody->setPost($post);

$graphServiceClient->groups()->byGroupId('group-id')->threads()->byConversationThreadId('conversationThread-id')->posts()->byPostId('post-id')->reply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	post = @{
		body = @{
			contentType = ""
			content = "content-value"
		}
		receivedDateTime = [System.DateTime]::Parse("datetime-value")
		hasAttachments = $true
		from = @{
			emailAddress = @{
				name = "name-value"
				address = "address-value"
			}
		}
		sender = @{
			emailAddress = @{
				name = "name-value"
				address = "address-value"
			}
		}
		conversationThreadId = "conversationThreadId-value"
		newParticipants = @(
			@{
				emailAddress = @{
					name = "name-value"
					address = "address-value"
				}
			}
		)
		conversationId = "conversationId-value"
		createdDateTime = [System.DateTime]::Parse("datetime-value")
		lastModifiedDateTime = [System.DateTime]::Parse("datetime-value")
		changeKey = "changeKey-value"
		categories = @(
		"categories-value"
	)
	id = "id-value"
	inReplyTo = @{
	}
	attachments = @(
		@{
			"@odata.type" = "#microsoft.graph.fileAttachment"
			lastModifiedDateTime = [System.DateTime]::Parse("datetime-value")
			name = "name-value"
			contentType = "contentType-value"
			size = 99
			isInline = $true
			id = "id-value"
		}
	)
}
}

Invoke-MgReplyGroupThreadPost -GroupId $groupId -ConversationThreadId $conversationThreadId -PostId $postId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.threads.item.posts.item.reply.reply_post_request_body import ReplyPostRequestBody
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.recipient import Recipient
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.attachment import Attachment
from msgraph.generated.models.file_attachment import FileAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReplyPostRequestBody(
	post = Post(
		body = ItemBody(
			content_type = BodyType.Text,
			content = "content-value",
		),
		received_date_time = "datetime-value",
		has_attachments = True,
		from = Recipient(
			email_address = EmailAddress(
				name = "name-value",
				address = "address-value",
			),
		),
		sender = Recipient(
			email_address = EmailAddress(
				name = "name-value",
				address = "address-value",
			),
		),
		conversation_thread_id = "conversationThreadId-value",
		new_participants = [
			Recipient(
				email_address = EmailAddress(
					name = "name-value",
					address = "address-value",
				),
			),
		],
		conversation_id = "conversationId-value",
		created_date_time = "datetime-value",
		last_modified_date_time = "datetime-value",
		change_key = "changeKey-value",
		categories = [
			"categories-value",
		],
		id = "id-value",
		in_reply_to = Post(
		),
		attachments = [
			FileAttachment(
				odata_type = "#microsoft.graph.fileAttachment",
				last_modified_date_time = "datetime-value",
				name = "name-value",
				content_type = "contentType-value",
				size = 99,
				is_inline = True,
				id = "id-value",
			),
		],
	),
)

await graph_client.groups.by_group_id('group-id').threads.by_conversation_thread_id('conversationThread-id').posts.by_post_id('post-id').reply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
