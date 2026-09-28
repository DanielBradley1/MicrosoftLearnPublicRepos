<!-- Source: https://learn.microsoft.com/en-us/graph/api/post-post-attachments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Add attachment

Namespace: microsoft.graph

Add an [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) when creating a group post.

This operation limits the size of the attachment you can add to under 3 MB.

An attachment can be one of the following types:

- A file \([fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0) resource\).
- An item \(contact, event or message, represented by an [itemAttachment](https://learn.microsoft.com/en-us/graph/api/resources/itemattachment?view=graph-rest-1.0) resource\).
- A link to a file \([referenceAttachment](https://learn.microsoft.com/en-us/graph/api/resources/referenceattachment?view=graph-rest-1.0) resource\).

All these types of attachment resources are derived from the [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) resource.

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

Include an attachment when creating a [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) in a [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) of a group. Specifying the parent [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) is optional.

```http
POST /groups/{id}/threads/{id}/reply
POST /groups/{id}/conversations/{id}/threads/{id}/reply
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, provide a JSON object that includes a **post** parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| post | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | The new post that is being replied with, which includes one or more attachments in an [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection. |

## Response

If successful, this method returns `202 Accepted` response code. It doesn't return a response body.

## Examples

### Example 1: Include a file attachment

#### Request

The following example shows a request that includes a file as an attachment when creating a post.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/groups/1848753d-185d-4c08-a4e4-6ee40521d115/threads/AAQkADJUdfolA==/reply
Content-type: application/json

{
  "post": {
    "body": {
      "contentType": "text",
      "content": "Which quarter does that file cover? See my attachment."
    },
    "attachments": [{
      "@odata.type": "#microsoft.graph.fileAttachment",
      "name": "Another file as attachment",
      "contentBytes": "VGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu"
    } ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.Threads.Item.Reply;
using Microsoft.Graph.Models;

var requestBody = new ReplyPostRequestBody
{
	Post = new Post
	{
		Body = new ItemBody
		{
			ContentType = BodyType.Text,
			Content = "Which quarter does that file cover? See my attachment.",
		},
		Attachments = new List<Attachment>
		{
			new FileAttachment
			{
				OdataType = "#microsoft.graph.fileAttachment",
				Name = "Another file as attachment",
				ContentBytes = Convert.FromBase64String("VGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu"),
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].Threads["{conversationThread-id}"].Reply.PostAsync(requestBody);
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
content := "Which quarter does that file cover? See my attachment."
body.SetContent(&content) 
post.SetBody(body)


attachment := graphmodels.NewFileAttachment()
name := "Another file as attachment"
attachment.SetName(&name) 
contentBytes := []byte("vGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu")
attachment.SetContentBytes(&contentBytes) 

attachments := []graphmodels.Attachmentable {
	attachment,
}
post.SetAttachments(attachments)
requestBody.SetPost(post)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").Threads().ByConversationThreadId("conversationThread-id").Reply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.threads.item.reply.ReplyPostRequestBody replyPostRequestBody = new com.microsoft.graph.groups.item.threads.item.reply.ReplyPostRequestBody();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Text);
body.setContent("Which quarter does that file cover? See my attachment.");
post.setBody(body);
LinkedList<Attachment> attachments = new LinkedList<Attachment>();
FileAttachment attachment = new FileAttachment();
attachment.setOdataType("#microsoft.graph.fileAttachment");
attachment.setName("Another file as attachment");
byte[] contentBytes = Base64.getDecoder().decode("VGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu");
attachment.setContentBytes(contentBytes);
attachments.add(attachment);
post.setAttachments(attachments);
replyPostRequestBody.setPost(post);
graphClient.groups().byGroupId("{group-id}").threads().byConversationThreadId("{conversationThread-id}").reply().post(replyPostRequestBody);
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
      contentType: 'text',
      content: 'Which quarter does that file cover? See my attachment.'
    },
    attachments: [{
      '@odata.type': '#microsoft.graph.fileAttachment',
      name: 'Another file as attachment',
      contentBytes: 'VGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu'
    } ]
  }
};

await client.api('/groups/1848753d-185d-4c08-a4e4-6ee40521d115/threads/AAQkADJUdfolA==/reply')
	.post(reply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\Threads\Item\Reply\ReplyPostRequestBody;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Attachment;
use Microsoft\Graph\Generated\Models\FileAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReplyPostRequestBody();
$post = new Post();
$postBody = new ItemBody();
$postBody->setContentType(new BodyType('text'));
$postBody->setContent('Which quarter does that file cover? See my attachment.');
$post->setBody($postBody);
$attachmentsAttachment1 = new FileAttachment();
$attachmentsAttachment1->setOdataType('#microsoft.graph.fileAttachment');
$attachmentsAttachment1->setName('Another file as attachment');
$attachmentsAttachment1->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('VGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu')));
$attachmentsArray []= $attachmentsAttachment1;
$post->setAttachments($attachmentsArray);

$requestBody->setPost($post);

$graphServiceClient->groups()->byGroupId('group-id')->threads()->byConversationThreadId('conversationThread-id')->reply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	post = @{
		body = @{
			contentType = "text"
			content = "Which quarter does that file cover? See my attachment."
		}
		attachments = @(
			@{
				"@odata.type" = "#microsoft.graph.fileAttachment"
				name = "Another file as attachment"
				contentBytes = "VGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu"
			}
		)
	}
}

Invoke-MgReplyGroupThread -GroupId $groupId -ConversationThreadId $conversationThreadId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.threads.item.reply.reply_post_request_body import ReplyPostRequestBody
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.attachment import Attachment
from msgraph.generated.models.file_attachment import FileAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReplyPostRequestBody(
	post = Post(
		body = ItemBody(
			content_type = BodyType.Text,
			content = "Which quarter does that file cover? See my attachment.",
		),
		attachments = [
			FileAttachment(
				odata_type = "#microsoft.graph.fileAttachment",
				name = "Another file as attachment",
				content_bytes = base64.urlsafe_b64decode("VGhpcyBpcyBhIGZpbGUgdG8gYmUgYXR0YWNoZWQu"),
			),
		],
	),
)

await graph_client.groups.by_group_id('group-id').threads.by_conversation_thread_id('conversationThread-id').reply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

### Example 2: Include an item attachment

#### Request

The following example shows a request that includes an event as an attachment when creating a post.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/groups/1848753d-185d-4c08-a4e4-6ee40521d115/threads/AAQkADJUdfolA==/reply
Content-type: application/json

{
  "post": {
    "body": {
      "contentType": "text",
      "content": "I attached an event."
    },
    "attachments": [{
      "@odata.type": "#microsoft.graph.itemAttachment",
      "name": "Holiday event", 
      "item": {
          "@odata.type": "microsoft.graph.event",
          "subject": "Discuss gifts for children",
          "body": {
              "contentType": "HTML",
              "content": "Let's look for funding!"
          },
          "start": {
              "dateTime": "2019-12-02T18:00:00",
              "timeZone": "Pacific Standard Time"
          },
          "end": {
              "dateTime": "2019-12-02T19:00:00",
              "timeZone": "Pacific Standard Time"
          }
      }
    } ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.Threads.Item.Reply;
using Microsoft.Graph.Models;

var requestBody = new ReplyPostRequestBody
{
	Post = new Post
	{
		Body = new ItemBody
		{
			ContentType = BodyType.Text,
			Content = "I attached an event.",
		},
		Attachments = new List<Attachment>
		{
			new ItemAttachment
			{
				OdataType = "#microsoft.graph.itemAttachment",
				Name = "Holiday event",
				Item = new Event
				{
					OdataType = "microsoft.graph.event",
					Subject = "Discuss gifts for children",
					Body = new ItemBody
					{
						ContentType = BodyType.Html,
						Content = "Let's look for funding!",
					},
					Start = new DateTimeTimeZone
					{
						DateTime = "2019-12-02T18:00:00",
						TimeZone = "Pacific Standard Time",
					},
					End = new DateTimeTimeZone
					{
						DateTime = "2019-12-02T19:00:00",
						TimeZone = "Pacific Standard Time",
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].Threads["{conversationThread-id}"].Reply.PostAsync(requestBody);
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
content := "I attached an event."
body.SetContent(&content) 
post.SetBody(body)


attachment := graphmodels.NewItemAttachment()
name := "Holiday event"
attachment.SetName(&name) 
item := graphmodels.NewEvent()
subject := "Discuss gifts for children"
item.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Let's look for funding!"
body.SetContent(&content) 
item.SetBody(body)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-12-02T18:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
item.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-12-02T19:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
item.SetEnd(end)
attachment.SetItem(item)

attachments := []graphmodels.Attachmentable {
	attachment,
}
post.SetAttachments(attachments)
requestBody.SetPost(post)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").Threads().ByConversationThreadId("conversationThread-id").Reply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.threads.item.reply.ReplyPostRequestBody replyPostRequestBody = new com.microsoft.graph.groups.item.threads.item.reply.ReplyPostRequestBody();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Text);
body.setContent("I attached an event.");
post.setBody(body);
LinkedList<Attachment> attachments = new LinkedList<Attachment>();
ItemAttachment attachment = new ItemAttachment();
attachment.setOdataType("#microsoft.graph.itemAttachment");
attachment.setName("Holiday event");
Event item = new Event();
item.setOdataType("microsoft.graph.event");
item.setSubject("Discuss gifts for children");
ItemBody body1 = new ItemBody();
body1.setContentType(BodyType.Html);
body1.setContent("Let's look for funding!");
item.setBody(body1);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2019-12-02T18:00:00");
start.setTimeZone("Pacific Standard Time");
item.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2019-12-02T19:00:00");
end.setTimeZone("Pacific Standard Time");
item.setEnd(end);
attachment.setItem(item);
attachments.add(attachment);
post.setAttachments(attachments);
replyPostRequestBody.setPost(post);
graphClient.groups().byGroupId("{group-id}").threads().byConversationThreadId("{conversationThread-id}").reply().post(replyPostRequestBody);
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
      contentType: 'text',
      content: 'I attached an event.'
    },
    attachments: [{
      '@odata.type': '#microsoft.graph.itemAttachment',
      name: 'Holiday event', 
      item: {
          '@odata.type': 'microsoft.graph.event',
          subject: 'Discuss gifts for children',
          body: {
              contentType: 'HTML',
              content: 'Let\'s look for funding!'
          },
          start: {
              dateTime: '2019-12-02T18:00:00',
              timeZone: 'Pacific Standard Time'
          },
          end: {
              dateTime: '2019-12-02T19:00:00',
              timeZone: 'Pacific Standard Time'
          }
      }
    } ]
  }
};

await client.api('/groups/1848753d-185d-4c08-a4e4-6ee40521d115/threads/AAQkADJUdfolA==/reply')
	.post(reply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\Threads\Item\Reply\ReplyPostRequestBody;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Attachment;
use Microsoft\Graph\Generated\Models\ItemAttachment;
use Microsoft\Graph\Generated\Models\Event;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReplyPostRequestBody();
$post = new Post();
$postBody = new ItemBody();
$postBody->setContentType(new BodyType('text'));
$postBody->setContent('I attached an event.');
$post->setBody($postBody);
$attachmentsAttachment1 = new ItemAttachment();
$attachmentsAttachment1->setOdataType('#microsoft.graph.itemAttachment');
$attachmentsAttachment1->setName('Holiday event');
$attachmentsAttachment1Item = new Event();
$attachmentsAttachment1Item->setOdataType('microsoft.graph.event');
$attachmentsAttachment1Item->setSubject('Discuss gifts for children');
$attachmentsAttachment1ItemBody = new ItemBody();
$attachmentsAttachment1ItemBody->setContentType(new BodyType('hTML'));
$attachmentsAttachment1ItemBody->setContent('Let\'s look for funding!');
$attachmentsAttachment1Item->setBody($attachmentsAttachment1ItemBody);
$attachmentsAttachment1ItemStart = new DateTimeTimeZone();
$attachmentsAttachment1ItemStart->setDateTime('2019-12-02T18:00:00');
$attachmentsAttachment1ItemStart->setTimeZone('Pacific Standard Time');
$attachmentsAttachment1Item->setStart($attachmentsAttachment1ItemStart);
$attachmentsAttachment1ItemEnd = new DateTimeTimeZone();
$attachmentsAttachment1ItemEnd->setDateTime('2019-12-02T19:00:00');
$attachmentsAttachment1ItemEnd->setTimeZone('Pacific Standard Time');
$attachmentsAttachment1Item->setEnd($attachmentsAttachment1ItemEnd);
$attachmentsAttachment1->setItem($attachmentsAttachment1Item);
$attachmentsArray []= $attachmentsAttachment1;
$post->setAttachments($attachmentsArray);

$requestBody->setPost($post);

$graphServiceClient->groups()->byGroupId('group-id')->threads()->byConversationThreadId('conversationThread-id')->reply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	post = @{
		body = @{
			contentType = "text"
			content = "I attached an event."
		}
		attachments = @(
			@{
				"@odata.type" = "#microsoft.graph.itemAttachment"
				name = "Holiday event"
				item = @{
					"@odata.type" = "microsoft.graph.event"
					subject = "Discuss gifts for children"
					body = @{
						contentType = "HTML"
						content = "Let's look for funding!"
					}
					start = @{
						dateTime = "2019-12-02T18:00:00"
						timeZone = "Pacific Standard Time"
					}
					end = @{
						dateTime = "2019-12-02T19:00:00"
						timeZone = "Pacific Standard Time"
					}
				}
			}
		)
	}
}

Invoke-MgReplyGroupThread -GroupId $groupId -ConversationThreadId $conversationThreadId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.threads.item.reply.reply_post_request_body import ReplyPostRequestBody
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.attachment import Attachment
from msgraph.generated.models.item_attachment import ItemAttachment
from msgraph.generated.models.event import Event
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReplyPostRequestBody(
	post = Post(
		body = ItemBody(
			content_type = BodyType.Text,
			content = "I attached an event.",
		),
		attachments = [
			ItemAttachment(
				odata_type = "#microsoft.graph.itemAttachment",
				name = "Holiday event",
				item = Event(
					odata_type = "microsoft.graph.event",
					subject = "Discuss gifts for children",
					body = ItemBody(
						content_type = BodyType.Html,
						content = "Let's look for funding!",
					),
					start = DateTimeTimeZone(
						date_time = "2019-12-02T18:00:00",
						time_zone = "Pacific Standard Time",
					),
					end = DateTimeTimeZone(
						date_time = "2019-12-02T19:00:00",
						time_zone = "Pacific Standard Time",
					),
				),
			),
		],
	),
)

await graph_client.groups.by_group_id('group-id').threads.by_conversation_thread_id('conversationThread-id').reply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

### Example 3: Include a reference attachment

#### Request

The following example shows a request that includes a reference attachment when creating a post. The attachment points to a folder on OneDrive.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/groups/1848753d-185d-4c08-a4e4-6ee40521d115/threads/AAQkADJUdfolA==/reply
Content-type: application/json

{
  "post": {
    "body": {
      "contentType": "text",
      "content": "I attached a reference to a file on OneDrive."
    },
    "attachments": [{
      "@odata.type": "#microsoft.graph.referenceAttachment", 
      "name": "Personal pictures", 
      "sourceUrl": "https://contoso.com/personal/mario_contoso_net/Documents/Pics", 
      "providerType": "oneDriveConsumer", 
      "permission": "Edit", 
      "isFolder": "True"
    } ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Groups.Item.Threads.Item.Reply;
using Microsoft.Graph.Models;

var requestBody = new ReplyPostRequestBody
{
	Post = new Post
	{
		Body = new ItemBody
		{
			ContentType = BodyType.Text,
			Content = "I attached a reference to a file on OneDrive.",
		},
		Attachments = new List<Attachment>
		{
			new ReferenceAttachment
			{
				OdataType = "#microsoft.graph.referenceAttachment",
				Name = "Personal pictures",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"sourceUrl" , "https://contoso.com/personal/mario_contoso_net/Documents/Pics"
					},
					{
						"providerType" , "oneDriveConsumer"
					},
					{
						"permission" , "Edit"
					},
					{
						"isFolder" , "True"
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Groups["{group-id}"].Threads["{conversationThread-id}"].Reply.PostAsync(requestBody);
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
content := "I attached a reference to a file on OneDrive."
body.SetContent(&content) 
post.SetBody(body)


attachment := graphmodels.NewReferenceAttachment()
name := "Personal pictures"
attachment.SetName(&name) 
additionalData := map[string]interface{}{
	"sourceUrl" : "https://contoso.com/personal/mario_contoso_net/Documents/Pics", 
	"providerType" : "oneDriveConsumer", 
	"permission" : "Edit", 
	"isFolder" : "True", 
}
attachment.SetAdditionalData(additionalData)

attachments := []graphmodels.Attachmentable {
	attachment,
}
post.SetAttachments(attachments)
requestBody.SetPost(post)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Groups().ByGroupId("group-id").Threads().ByConversationThreadId("conversationThread-id").Reply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.groups.item.threads.item.reply.ReplyPostRequestBody replyPostRequestBody = new com.microsoft.graph.groups.item.threads.item.reply.ReplyPostRequestBody();
Post post = new Post();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Text);
body.setContent("I attached a reference to a file on OneDrive.");
post.setBody(body);
LinkedList<Attachment> attachments = new LinkedList<Attachment>();
ReferenceAttachment attachment = new ReferenceAttachment();
attachment.setOdataType("#microsoft.graph.referenceAttachment");
attachment.setName("Personal pictures");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("sourceUrl", "https://contoso.com/personal/mario_contoso_net/Documents/Pics");
additionalData.put("providerType", "oneDriveConsumer");
additionalData.put("permission", "Edit");
additionalData.put("isFolder", "True");
attachment.setAdditionalData(additionalData);
attachments.add(attachment);
post.setAttachments(attachments);
replyPostRequestBody.setPost(post);
graphClient.groups().byGroupId("{group-id}").threads().byConversationThreadId("{conversationThread-id}").reply().post(replyPostRequestBody);
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
      contentType: 'text',
      content: 'I attached a reference to a file on OneDrive.'
    },
    attachments: [{
      '@odata.type': '#microsoft.graph.referenceAttachment', 
      name: 'Personal pictures', 
      sourceUrl: 'https://contoso.com/personal/mario_contoso_net/Documents/Pics', 
      providerType: 'oneDriveConsumer', 
      permission: 'Edit', 
      isFolder: 'True'
    } ]
  }
};

await client.api('/groups/1848753d-185d-4c08-a4e4-6ee40521d115/threads/AAQkADJUdfolA==/reply')
	.post(reply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Groups\Item\Threads\Item\Reply\ReplyPostRequestBody;
use Microsoft\Graph\Generated\Models\Post;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\Attachment;
use Microsoft\Graph\Generated\Models\ReferenceAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReplyPostRequestBody();
$post = new Post();
$postBody = new ItemBody();
$postBody->setContentType(new BodyType('text'));
$postBody->setContent('I attached a reference to a file on OneDrive.');
$post->setBody($postBody);
$attachmentsAttachment1 = new ReferenceAttachment();
$attachmentsAttachment1->setOdataType('#microsoft.graph.referenceAttachment');
$attachmentsAttachment1->setName('Personal pictures');
$additionalData = [
	'sourceUrl' => 'https://contoso.com/personal/mario_contoso_net/Documents/Pics',
	'providerType' => 'oneDriveConsumer',
	'permission' => 'Edit',
	'isFolder' => 'True',
];
$attachmentsAttachment1->setAdditionalData($additionalData);
$attachmentsArray []= $attachmentsAttachment1;
$post->setAttachments($attachmentsArray);

$requestBody->setPost($post);

$graphServiceClient->groups()->byGroupId('group-id')->threads()->byConversationThreadId('conversationThread-id')->reply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

$params = @{
	post = @{
		body = @{
			contentType = "text"
			content = "I attached a reference to a file on OneDrive."
		}
		attachments = @(
			@{
				"@odata.type" = "#microsoft.graph.referenceAttachment"
				name = "Personal pictures"
				sourceUrl = "https://contoso.com/personal/mario_contoso_net/Documents/Pics"
				providerType = "oneDriveConsumer"
				permission = "Edit"
				isFolder = "True"
			}
		)
	}
}

Invoke-MgReplyGroupThread -GroupId $groupId -ConversationThreadId $conversationThreadId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.groups.item.threads.item.reply.reply_post_request_body import ReplyPostRequestBody
from msgraph.generated.models.post import Post
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.attachment import Attachment
from msgraph.generated.models.reference_attachment import ReferenceAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReplyPostRequestBody(
	post = Post(
		body = ItemBody(
			content_type = BodyType.Text,
			content = "I attached a reference to a file on OneDrive.",
		),
		attachments = [
			ReferenceAttachment(
				odata_type = "#microsoft.graph.referenceAttachment",
				name = "Personal pictures",
				additional_data = {
						"source_url" : "https://contoso.com/personal/mario_contoso_net/Documents/Pics",
						"provider_type" : "oneDriveConsumer",
						"permission" : "Edit",
						"is_folder" : "True",
				}
			),
		],
	),
)

await graph_client.groups.by_group_id('group-id').threads.by_conversation_thread_id('conversationThread-id').reply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
