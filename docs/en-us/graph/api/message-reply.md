<!-- Source: https://learn.microsoft.com/en-us/graph/api/message-reply?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# message: reply

Namespace: microsoft.graph

Reply to the sender of a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) using either JSON or MIME format.

When using JSON format:

- Specify either a comment or the **body** property of the `message` parameter. Specifying both will return an HTTP `400 Bad Request` error.
- If the original message specifies a recipient in the **replyTo** property, per Internet Message Format \([RFC 2822](https://www.rfc-editor.org/info/rfc2822)\), send the reply to the recipients in **replyTo** and not the recipient in the **from** property.

When using MIME format:

- Provide the applicable [Internet message headers](https://tools.ietf.org/html/rfc2076) and the [MIME content](https://tools.ietf.org/html/rfc2045), all encoded in **base64** format in the request body.
- Add any attachments and S/MIME properties to the MIME content.

This method saves the message in the **Sent Items** folder.

Alternatively, [create a draft to reply to an existing message](https://learn.microsoft.com/en-us/graph/api/message-createreply?view=graph-rest-1.0) and [send](https://learn.microsoft.com/en-us/graph/api/message-send?view=graph-rest-1.0) it later.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.Send | Not available. |
| Delegated \(personal Microsoft account\) | Mail.Send | Not available. |
| Application | Mail.Send | Not available. |

## HTTP request

```http
POST /me/messages/{id}/reply
POST /users/{id | userPrincipalName}/messages/{id}/reply
POST /me/mailFolders/{id}/messages/{id}/reply
POST /users/{id | userPrincipalName}/mailFolders/{id}/messages/{id}/reply
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required |
| Content-Type | string | Nature of the data in the body of an entity. Required  <br>Use `application/json` for a JSON object and `text/plain` for MIME content. |
| Prefer: outlook.timezone | string | Sets the time zone for the `Sent` field of the reply message in HTML that this API creates based on the request body. The value can be any of the [supportedTimeZones](https://learn.microsoft.com/en-us/graph/api/outlookuser-supportedtimezones?view=graph-rest-1.0) configured for the user. If not specified, that `Sent` field is in UTC.  <br>  <br>Use this header only if you're specifying the `Content-Type: application/json` header to create the reply message in HTML. If you use the `Content-Type: text/plain` header, this `Prefer` header doesn't have any effect. Optional. |

## Request body

When using JSON format, provide a JSON object in the request body with the following parameters.

| Parameter | Type | Description |
| --- | --- | --- |
| comment | String | A comment to include. Can be an empty string. |
| message | [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Any writeable properties to update in the reply message. |

When specifying the body in MIME format, provide the MIME content with the applicable Internet message headers, all encoded in **base64** format in the request body. This method uses the sender of the original message as recipient.

## Response

If successful, this method returns a `202 Accepted` response code. It doesn't return anything in the response body.

If the request body includes malformed MIME content, this method returns a `400 Bad Request` error code and the following error message: "Invalid base64 string for MIME content".

## Examples

### Example 1: Reply in JSON format to an existing message

The following example includes a comment and adds a recipient to the reply message.

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
POST https://graph.microsoft.com/v1.0/me/messages/AAMkADA1MTAAAAqldOAAA=/reply
Content-Type: application/json

{
  "message":{
    "toRecipients":[
      {
        "emailAddress": {
          "address":"samanthab@contoso.com",
          "name":"Samantha Booth"
        }
      },
      {
        "emailAddress":{
          "address":"randiw@contoso.com",
          "name":"Randi Welch"
        }
      }
     ]
  },
  "comment": "Samantha, Randi, would you name the group please?"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Messages.Item.Reply;
using Microsoft.Graph.Models;

var requestBody = new ReplyPostRequestBody
{
	Message = new Message
	{
		ToRecipients = new List<Recipient>
		{
			new Recipient
			{
				EmailAddress = new EmailAddress
				{
					Address = "samanthab@contoso.com",
					Name = "Samantha Booth",
				},
			},
			new Recipient
			{
				EmailAddress = new EmailAddress
				{
					Address = "randiw@contoso.com",
					Name = "Randi Welch",
				},
			},
		},
	},
	Comment = "Samantha, Randi, would you name the group please?",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Messages["{message-id}"].Reply.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemReplyPostRequestBody()
message := graphmodels.NewMessage()


recipient := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
address := "samanthab@contoso.com"
emailAddress.SetAddress(&address) 
name := "Samantha Booth"
emailAddress.SetName(&name) 
recipient.SetEmailAddress(emailAddress)
recipient1 := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
address := "randiw@contoso.com"
emailAddress.SetAddress(&address) 
name := "Randi Welch"
emailAddress.SetName(&name) 
recipient1.SetEmailAddress(emailAddress)

toRecipients := []graphmodels.Recipientable {
	recipient,
	recipient1,
}
message.SetToRecipients(toRecipients)
requestBody.SetMessage(message)
comment := "Samantha, Randi, would you name the group please?"
requestBody.SetComment(&comment) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Messages().ByMessageId("message-id").Reply().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.messages.item.reply.ReplyPostRequestBody replyPostRequestBody = new com.microsoft.graph.users.item.messages.item.reply.ReplyPostRequestBody();
Message message = new Message();
LinkedList<Recipient> toRecipients = new LinkedList<Recipient>();
Recipient recipient = new Recipient();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("samanthab@contoso.com");
emailAddress.setName("Samantha Booth");
recipient.setEmailAddress(emailAddress);
toRecipients.add(recipient);
Recipient recipient1 = new Recipient();
EmailAddress emailAddress1 = new EmailAddress();
emailAddress1.setAddress("randiw@contoso.com");
emailAddress1.setName("Randi Welch");
recipient1.setEmailAddress(emailAddress1);
toRecipients.add(recipient1);
message.setToRecipients(toRecipients);
replyPostRequestBody.setMessage(message);
replyPostRequestBody.setComment("Samantha, Randi, would you name the group please?");
graphClient.me().messages().byMessageId("{message-id}").reply().post(replyPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const reply = {
  message: {
    toRecipients: [
      {
        emailAddress: {
          address: 'samanthab@contoso.com',
          name: 'Samantha Booth'
        }
      },
      {
        emailAddress: {
          address: 'randiw@contoso.com',
          name: 'Randi Welch'
        }
      }
     ]
  },
  comment: 'Samantha, Randi, would you name the group please?'
};

await client.api('/me/messages/AAMkADA1MTAAAAqldOAAA=/reply')
	.post(reply);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Messages\Item\Reply\ReplyPostRequestBody;
use Microsoft\Graph\Generated\Models\Message;
use Microsoft\Graph\Generated\Models\Recipient;
use Microsoft\Graph\Generated\Models\EmailAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReplyPostRequestBody();
$message = new Message();
$toRecipientsRecipient1 = new Recipient();
$toRecipientsRecipient1EmailAddress = new EmailAddress();
$toRecipientsRecipient1EmailAddress->setAddress('samanthab@contoso.com');
$toRecipientsRecipient1EmailAddress->setName('Samantha Booth');
$toRecipientsRecipient1->setEmailAddress($toRecipientsRecipient1EmailAddress);
$toRecipientsArray []= $toRecipientsRecipient1;
$toRecipientsRecipient2 = new Recipient();
$toRecipientsRecipient2EmailAddress = new EmailAddress();
$toRecipientsRecipient2EmailAddress->setAddress('randiw@contoso.com');
$toRecipientsRecipient2EmailAddress->setName('Randi Welch');
$toRecipientsRecipient2->setEmailAddress($toRecipientsRecipient2EmailAddress);
$toRecipientsArray []= $toRecipientsRecipient2;
$message->setToRecipients($toRecipientsArray);

$requestBody->setMessage($message);
$requestBody->setComment('Samantha, Randi, would you name the group please?');

$graphServiceClient->me()->messages()->byMessageId('message-id')->reply()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	message = @{
		toRecipients = @(
			@{
				emailAddress = @{
					address = "samanthab@contoso.com"
					name = "Samantha Booth"
				}
			}
			@{
				emailAddress = @{
					address = "randiw@contoso.com"
					name = "Randi Welch"
				}
			}
		)
	}
	comment = "Samantha, Randi, would you name the group please?"
}

# A UPN can also be used as -UserId.
Invoke-MgReplyUserMessage -UserId $userId -MessageId $messageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.messages.item.reply.reply_post_request_body import ReplyPostRequestBody
from msgraph.generated.models.message import Message
from msgraph.generated.models.recipient import Recipient
from msgraph.generated.models.email_address import EmailAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReplyPostRequestBody(
	message = Message(
		to_recipients = [
			Recipient(
				email_address = EmailAddress(
					address = "samanthab@contoso.com",
					name = "Samantha Booth",
				),
			),
			Recipient(
				email_address = EmailAddress(
					address = "randiw@contoso.com",
					name = "Randi Welch",
				),
			),
		],
	),
	comment = "Samantha, Randi, would you name the group please?",
)

await graph_client.me.messages.by_message_id('message-id').reply.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

### Example 2: Reply in MIME format to an existing message

#### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/messages/AAMkADA1MTAAAAqldOAAA=/reply
Content-type: text/plain

Q29udGVudC1UeXBlOiBhcHBsaWNhdGlvbi9wa2NzNy1taW1lOw0KCW5hbWU9c21pbWUucDdtOw0KCXNtaW1lLXR5cGU9ZW52ZWxvcGVkLWRhdGENCk1pbWUtVmVyc2lvbjogMS4wIChNYWMgT1MgWCBNYWlsIDEzLjAgXCgzNjAxLjAuMTBcKSkNClN1YmplY3Q6IFJlOiBUZXN0aW5nIFMvTUlNRQ0KQ29udGVudC1EaXNwb3Np
```

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```

If the request body includes malformed MIME content, this method returns the following error message.

```http
HTTP/1.1 400 Bad Request
Content-type: application/json

{
    "error": {
        "code": "ErrorMimeContentInvalidBase64String",
        "message": "Invalid base64 string for MIME content."
    }
}
```
