<!-- Source: https://learn.microsoft.com/en-us/graph/api/message-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Update message

Namespace: microsoft.graph

Update the properties of a message object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Mail.ReadWrite |
| Delegated \(personal Microsoft account\) | Mail.ReadWrite |
| Application | Mail.ReadWrite |

## HTTP request

```http
PATCH /me/messages/{id}
PATCH /users/{id | userPrincipalName}/messages/{id}
PATCH /me/mailFolders/{id}/messages/{id}
PATCH /users/{id | userPrincipalName}/mailFolders/{id}/messages/{id}
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | Nature of the data in the body of an entity. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed. The following properties can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| bccRecipients | Recipient | The Bcc recipients for the message. Updatable only if **isDraft** = `true`. |
| body | ItemBody | The body of the message. Updatable only if **isDraft** = `true`. |
| categories | String collection | The categories associated with the message. |
| ccRecipients | Recipient collection | The Cc recipients for the message. Updatable only if **isDraft** = `true`. |
| flag | [followupFlag](https://learn.microsoft.com/en-us/graph/api/resources/followupflag?view=graph-rest-1.0) | The flag value that indicates the status, start date, due date, or completion date for the message. |
| from | Recipient | The mailbox owner and sender of the message. Must correspond to the actual mailbox used. |
| importance | String | The importance of the message. The possible values are: `Low`, `Normal`, `High`. |
| inferenceClassification | String | The classification of the message for the user, based on inferred relevance or importance, or on an explicit override. The possible values are: `focused` or `other`. |
| internetMessageId | String | The message ID in the format specified by [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). Updatable only if **isDraft** = `true`. |
| isDeliveryReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| isRead | Boolean | Indicates whether the message has been read. |
| isReadReceiptRequested | Boolean | Indicates whether a read receipt is requested for the message. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the message. Nullable. Updatable only if **isDraft** = `true`. |
| replyTo | Recipient collection | The email addresses to use when replying. Updatable only if **isDraft** = `true`. |
| sender | Recipient | The account that is actually used to generate the message. Updatable when sending a message from a [shared mailbox](https://learn.microsoft.com/en-us/exchange/collaboration/shared-mailboxes/shared-mailboxes), or sending a message as a [delegate](https://support.office.com/en-us/article/allow-someone-else-to-manage-your-mail-and-calendar-41c40c04-3bd1-4d22-963a-28eafec25926). In any case, the value must correspond to the actual mailbox used. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the message. Nullable. Updatable only if **isDraft** = `true`. |
| subject | String | The subject of the message. Updatable only if **isDraft** = `true`. |
| toRecipients | Recipient collection | The To recipients for the message. Updatable only if **isDraft** = `true`. |

Since the **message** resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), you can use the `PATCH` operation to add, update, or delete your own app-specific data in custom properties of an extension in an existing **message** instance.

## Response

If successful, this method returns a `200 OK` response code and updated [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/me/messages/{id}
Content-type: application/json

{
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "inferenceClassification": "other"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Message
{
	Subject = "subject-value",
	Body = new ItemBody
	{
		ContentType = BodyType.Text,
		Content = "content-value",
	},
	InferenceClassification = InferenceClassificationType.Other,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages["{message-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewMessage()
subject := "subject-value"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.TEXT_BODYTYPE 
body.SetContentType(&contentType) 
content := "content-value"
body.SetContent(&content) 
requestBody.SetBody(body)
inferenceClassification := graphmodels.OTHER_INFERENCECLASSIFICATIONTYPE 
requestBody.SetInferenceClassification(&inferenceClassification) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Me().Messages().ByMessageId("message-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Message message = new Message();
message.setSubject("subject-value");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Text);
body.setContent("content-value");
message.setBody(body);
message.setInferenceClassification(InferenceClassificationType.Other);
Message result = graphClient.me().messages().byMessageId("{message-id}").patch(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const message = {
  subject: 'subject-value',
  body: {
    contentType: '',
    content: 'content-value'
  },
  inferenceClassification: 'other'
};

await client.api('/me/messages/{id}')
	.update(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Message;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\InferenceClassificationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Message();
$requestBody->setSubject('subject-value');
$body = new ItemBody();
$body->setContentType(new BodyType('text'));
$body->setContent('content-value');
$requestBody->setBody($body);
$requestBody->setInferenceClassification(new InferenceClassificationType('other'));

$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	subject = "subject-value"
	body = @{
		contentType = ""
		content = "content-value"
	}
	inferenceClassification = "other"
}

# A UPN can also be used as -UserId.
Update-MgUserMessage -UserId $userId -MessageId $messageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.message import Message
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.inference_classification_type import InferenceClassificationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Message(
	subject = "subject-value",
	body = ItemBody(
		content_type = BodyType.Text,
		content = "content-value",
	),
	inference_classification = InferenceClassificationType.Other,
)

result = await graph_client.me.messages.by_message_id('message-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "receivedDateTime": "datetime-value",
  "sentDateTime": "datetime-value",
  "hasAttachments": true,
  "subject": "subject-value",
  "body": {
    "contentType": "",
    "content": "content-value"
  },
  "bodyPreview": "bodyPreview-value",
  "inferenceClassification": "other"
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions \(preview\)](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
