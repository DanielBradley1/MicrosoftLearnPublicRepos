<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-large-attachments -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Attach large files to Outlook messages or events

Using the Microsoft Graph API, you can attach files up to 150 MB to an Outlook [message](https://learn.microsoft.com/en-us/graph/api/resources/message) or [event](https://learn.microsoft.com/en-us/graph/api/resources/event) item. Depending on the file size, choose one of two ways to attach the file:

- If the file size is under 3 MB, do a single POST on the **attachments** navigation property of the Outlook item; see how to do this [for a message](https://learn.microsoft.com/en-us/graph/api/message-post-attachments) or [for an event](https://learn.microsoft.com/en-us/graph/api/event-post-attachments). The successful `POST` response includes the ID of the file attachment.
- If the file size is between 3 MB and 150 MB, create an upload session, and iteratively use `PUT` to upload ranges of bytes of the file until you have uploaded the entire file. A header in the final successful `PUT` response includes a URL with the attachment ID.

To attach multiple files to a message, choose the approach for each file based on its file size and attach the files individually.

This article illustrates the second approach step by step, creating and using an upload session to add a large file attachment \(of size over 3 MB\) to an Outlook item. Each step shows the corresponding code for a message and for an event. Upon successfully uploading the entire file, the article shows getting a response header that contains an ID for the file attachment, and then using that attachment ID to get the raw attachment content or attachment metadata.

Important

Be aware of a [known issue](https://developer.microsoft.com/en-us/graph/known-issues/?search=13644) if you're attaching large files to a message or event in a shared or delegated mailbox.

## Step 1: Create an upload session

[Create an upload session](https://learn.microsoft.com/en-us/graph/api/attachment-createuploadsession) to attach a file to a message or event. Specify the file in the input parameter **AttachmentItem**.

A successful operation returns `HTTP 201 Created` and a new [uploadSession](https://learn.microsoft.com/en-us/graph/api/resources/uploadsession) instance, which contains an opaque URL that you can use in subsequent `PUT` operations to upload portions of the file. The **uploadSession** provides a temporary storage location where the bytes of the file are saved until you have uploaded the complete file.

The **uploadSession** object in the response also includes the **nextExpectedRanges** property, which indicates the initial upload starting location should be byte 0.

### Permissions

Make sure to request `Mail.ReadWrite` permission to create the **uploadSession** for a message, and `Calendars.ReadWrite` for an event.

The opaque URL, returned in the **uploadUrl** property of the new **uploadSession**, is pre-authenticated and contains the appropriate authorization token for subsequent `PUT` queries in the `https://outlook.office.com` domain. That token expires by **expirationDateTime**. Do not customize this URL for the `PUT` operations.

### Example: Create an upload session for a message

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/messages/AAMkADI5MAAIT3drCAAA=/attachments/createUploadSession
Content-type: application/json

{
  "AttachmentItem": {
    "attachmentType": "file",
    "name": "flower",
    "size": 3483322
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Messages.Item.Attachments.CreateUploadSession;
using Microsoft.Graph.Models;

var requestBody = new CreateUploadSessionPostRequestBody
{
	AttachmentItem = new AttachmentItem
	{
		AttachmentType = AttachmentType.File,
		Name = "flower",
		Size = 3483322L,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages["{message-id}"].Attachments.CreateUploadSession.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

requestBody := graphusers.NewItemCreateUploadSessionPostRequestBody()
attachmentItem := graphmodels.NewAttachmentItem()
attachmentType := graphmodels.FILE_ATTACHMENTTYPE 
attachmentItem.SetAttachmentType(&attachmentType) 
name := "flower"
attachmentItem.SetName(&name) 
size := int64(3483322)
attachmentItem.SetSize(&size) 
requestBody.SetAttachmentItem(attachmentItem)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createUploadSession, err := graphClient.Me().Messages().ByMessageId("message-id").Attachments().CreateUploadSession().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.messages.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody createUploadSessionPostRequestBody = new com.microsoft.graph.users.item.messages.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody();
AttachmentItem attachmentItem = new AttachmentItem();
attachmentItem.setAttachmentType(AttachmentType.File);
attachmentItem.setName("flower");
attachmentItem.setSize(3483322L);
createUploadSessionPostRequestBody.setAttachmentItem(attachmentItem);
var result = graphClient.me().messages().byMessageId("{message-id}").attachments().createUploadSession().post(createUploadSessionPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const uploadSession = {
  AttachmentItem: {
    attachmentType: 'file',
    name: 'flower',
    size: 3483322
  }
};

await client.api('/me/messages/AAMkADI5MAAIT3drCAAA=/attachments/createUploadSession')
	.post(uploadSession);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Messages\Item\Attachments\CreateUploadSession\CreateUploadSessionPostRequestBody;
use Microsoft\Graph\Generated\Models\AttachmentItem;
use Microsoft\Graph\Generated\Models\AttachmentType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateUploadSessionPostRequestBody();
$attachmentItem = new AttachmentItem();
$attachmentItem->setAttachmentType(new AttachmentType('file'));
$attachmentItem->setName('flower');
$attachmentItem->setSize(3483322);
$requestBody->setAttachmentItem($attachmentItem);

$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->attachments()->createUploadSession()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	AttachmentItem = @{
		attachmentType = "file"
		name = "flower"
		size = 3483322
	}
}

# A UPN can also be used as -UserId.
New-MgUserMessageAttachmentUploadSession -UserId $userId -MessageId $messageId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.messages.item.attachments.create_upload_session.create_upload_session_post_request_body import CreateUploadSessionPostRequestBody
from msgraph.generated.models.attachment_item import AttachmentItem
from msgraph.generated.models.attachment_type import AttachmentType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateUploadSessionPostRequestBody(
	attachment_item = AttachmentItem(
		attachment_type = AttachmentType.File,
		name = "flower",
		size = 3483322,
	),
)

result = await graph_client.me.messages.by_message_id('message-id').attachments.create_upload_session.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

The following example response shows the **uploadSession** resource returned for the message.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.uploadSession",
    "uploadUrl": "https://outlook.office.com/api/v2.0/Users('a8e8e219-4931-95c1-b73d-62626fd79c32@72aa88bf-76f0-494f-91ab-2d7cd730db47')/Messages('AAMkADI5MAAIT3drCAAA=')/AttachmentSessions('AAMkADI5MAAIT3k0tAAA=')?authtoken=eyJhbGciOiJSUzI1NiIsImtpZCI6IktmYUNIUlN6bllHMmNI",
    "expirationDateTime": "2019-09-25T01:09:30.7671707Z",
    "nextExpectedRanges": [
        "0-"
    ]
}
```

### Example: Create an upload session for an event

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/events/AAMkADU5CCmSAAA=/attachments/createUploadSession
Content-type: application/json

{
  "AttachmentItem": {
    "attachmentType": "file",
    "name": "flower",
    "size": 3483322
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Events.Item.Attachments.CreateUploadSession;
using Microsoft.Graph.Models;

var requestBody = new CreateUploadSessionPostRequestBody
{
	AttachmentItem = new AttachmentItem
	{
		AttachmentType = AttachmentType.File,
		Name = "flower",
		Size = 3483322L,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events["{event-id}"].Attachments.CreateUploadSession.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

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

requestBody := graphusers.NewItemCreateUploadSessionPostRequestBody()
attachmentItem := graphmodels.NewAttachmentItem()
attachmentType := graphmodels.FILE_ATTACHMENTTYPE 
attachmentItem.SetAttachmentType(&attachmentType) 
name := "flower"
attachmentItem.SetName(&name) 
size := int64(3483322)
attachmentItem.SetSize(&size) 
requestBody.SetAttachmentItem(attachmentItem)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createUploadSession, err := graphClient.Me().Events().ByEventId("event-id").Attachments().CreateUploadSession().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.events.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody createUploadSessionPostRequestBody = new com.microsoft.graph.users.item.events.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody();
AttachmentItem attachmentItem = new AttachmentItem();
attachmentItem.setAttachmentType(AttachmentType.File);
attachmentItem.setName("flower");
attachmentItem.setSize(3483322L);
createUploadSessionPostRequestBody.setAttachmentItem(attachmentItem);
var result = graphClient.me().events().byEventId("{event-id}").attachments().createUploadSession().post(createUploadSessionPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const uploadSession = {
  AttachmentItem: {
    attachmentType: 'file',
    name: 'flower',
    size: 3483322
  }
};

await client.api('/me/events/AAMkADU5CCmSAAA=/attachments/createUploadSession')
	.post(uploadSession);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\Attachments\CreateUploadSession\CreateUploadSessionPostRequestBody;
use Microsoft\Graph\Generated\Models\AttachmentItem;
use Microsoft\Graph\Generated\Models\AttachmentType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateUploadSessionPostRequestBody();
$attachmentItem = new AttachmentItem();
$attachmentItem->setAttachmentType(new AttachmentType('file'));
$attachmentItem->setName('flower');
$attachmentItem->setSize(3483322);
$requestBody->setAttachmentItem($attachmentItem);

$result = $graphServiceClient->me()->events()->byEventId('event-id')->attachments()->createUploadSession()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	AttachmentItem = @{
		attachmentType = "file"
		name = "flower"
		size = 3483322
	}
}

# A UPN can also be used as -UserId.
New-MgUserEventAttachmentUploadSession -UserId $userId -EventId $eventId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.attachments.create_upload_session.create_upload_session_post_request_body import CreateUploadSessionPostRequestBody
from msgraph.generated.models.attachment_item import AttachmentItem
from msgraph.generated.models.attachment_type import AttachmentType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateUploadSessionPostRequestBody(
	attachment_item = AttachmentItem(
		attachment_type = AttachmentType.File,
		name = "flower",
		size = 3483322,
	),
)

result = await graph_client.me.events.by_event_id('event-id').attachments.create_upload_session.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

#### Response

The following example response shows the **uploadSession** resource returned for the event.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.uploadSession",
    "uploadUrl": "https://outlook.office.com/api/v2.0/Users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69@98a79ebe-74bf-4e07-a017-7b410848cb32')/Events('AAMkADU5CCmSAAA=')/AttachmentSessions('AAMkADU5RpAACJlCs8AAA=')?authtoken=eyJhbGciOiJSUzI1NiIsImtpZCI6IktmYUNIBtw",
    "expirationDateTime": "2020-02-22T02:46:56.7410786Z",
    "nextExpectedRanges": [
        "0-"
    ]
}
```

## Step 2: Use the upload session to upload a range of bytes of the file

To upload the file, or a portion of the file, make a `PUT` request to the URL returned in step 1 in the **uploadUrl** property of the **uploadSession** resource. You can upload the entire file, or split the file into multiple byte ranges. For better performance, keep each byte range less than 4 MB.

Specify request headers and request body as described below.

### Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Content-Length | Int32 | The number of bytes being uploaded in this operation. For better performance, keep the upper limit of the number of bytes for each `PUT` operation to 4 MB. Required. |
| Content-Range | String | The 0-based byte range of the file being uploaded in this operation, expressed in the format `bytes {start}-{end}/{total}`. Required. |
| Content-Type | String | The MIME type. Specify `application/octet-stream`. Required. |

Do not specify an `Authorization` request header. The `PUT` query uses a pre-authenticated URL from the **uploadUrl** property, that allows access to the `https://outlook.office.com` domain.

### Request body

Specify the actual bytes of the file to be attached, that are in the location range specified by the `Content-Range` request header.

### Response

A successful upload returns `HTTP 200 OK` and an **uploadSession** object. Note the following in the response object:

- The **expirationDateTime** property indicates the expiration date/time for the auth token embedded in the **uploadUrl** property value. This expiration date/time remains the same as returned by the initial **uploadSession** in step 1.
- The **nextExpectedRanges** specifies the next byte location to start uploading from, for example, `"nextExpectedRanges":["2097152"]`. You must upload bytes in a file in order.

- The **uploadUrl** property is not explicitly returned, because all `PUT` operations of an upload session use the same URL returned when creating the session \(step 1\).

### Example: First upload to the message

#### Request

```http
PUT https://outlook.office.com/api/v2.0/Users('a8e8e219-4931-95c1-b73d-62626fd79c32@72aa88bf-76f0-494f-91ab-2d7cd730db47')/Messages('AAMkADI5MAAIT3drCAAA=')/AttachmentSessions('AAMkADI5MAAIT3k0tAAA=')?authtoken=eyJhbGciOiJSUzI1NiIsImtpZCI6IktmYUNIUlN6bllHMmNI
Content-Type: application/octet-stream
Content-Length: 2097152
Content-Range: bytes 0-2097151/3483322

{
  <bytes 0-2097151 of the file to be attached, in binary format>
}
```

#### Response

The following example response shows in the **nextExpectedRanges** property the start of the next byte range that the server expects.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Users('a8e8e219-4931-95c1-b73d-62626fd79c32%4072aa88bf-76f0-494f-91ab-2d7cd730db47')/Messages('AAMkADI5MAAIT3drCAAA%3D')/AttachmentSessions/$entity",
  "ExpirationDateTime":"2019-09-25T01:09:30.7671707Z",
  "nextExpectedRanges":["2097152"]
}
```

### Example: First upload to the event

#### Request

```http
PUT https://outlook.office.com/api/v2.0/Users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69@98a79ebe-74bf-4e07-a017-7b410848cb32')/Events('AAMkADU5CCmSAAA=')/AttachmentSessions('AAMkADU5RpAACJlCs8AAA=')?authtoken=eyJhbGciOiJSUzI1NiIsImtpZCI6IktmYUNIBtw
Content-Type: application/octet-stream
Content-Length: 2097152
Content-Range: bytes 0-2097151/3483322

{
  <bytes 0-2097151 of the file to be attached, in binary format>
}
```

#### Response

The following example response shows in the **nextExpectedRanges** property the start of the next byte range that the server expects.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context":"https://outlook.office.com/api/v2.0/$metadata#Users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69%4098a79ebe-74bf-4e07-a017-7b410848cb32')/Events('AAMkADU5CCmSAAA%3D')/AttachmentSessions/$entity",
    "ExpirationDateTime":"2020-02-22T02:46:56.7410786Z",
    "nextExpectedRanges":["2097152"]
}
```

## Step 3: Continue uploading byte ranges until the entire file has been uploaded

Following the initial upload in step 2, continue to upload the remaining portion of the file, using a similar `PUT` request as described in step 2, before you reach the expiration date/time for the session. Use the **nextExpectedRanges** collection to determine where to start the next byte range to upload. You might see multiple ranges specified, indicating parts of the file that the server has not yet received. This is useful if you need to resume a transfer that was interrupted and your client is unsure of the state on the service.

Once the last byte of the file has been successfully uploaded, the final `PUT` operation returns `HTTP 201 Created` and a `Location` header that indicates the URL to the file attachment in the `https://outlook.office.com` domain. You can get the attachment ID from the URL and save it for later use. Depending on your scenario, you can use that ID to [get the metadata of the attachment](https://learn.microsoft.com/en-us/graph/api/attachment-get), or [remove the attachment from the Outlook item](https://learn.microsoft.com/en-us/graph/api/attachment-delete) using the Microsoft Graph endpoint.

The following examples show uploading the last byte range of the file to the message and to the event in the preceding steps.

### Example: Final upload to the message

#### Request

```http
PUT https://outlook.office.com/api/v2.0/Users('a8e8e219-4931-95c1-b73d-62626fd79c32@72aa88bf-76f0-494f-91ab-2d7cd730db47')/Messages('AAMkADI5MAAIT3drCAAA=')/AttachmentSessions('AAMkADI5MAAIT3k0tAAA=')?authtoken=eyJhbGciOiJSUzI1NiIsImtpZCI6IktmYUNIUlN6bllHMmNI
Content-Type: application/octet-stream
Content-Length: 1386170
Content-Range: bytes 2097152-3483321/3483322

{
  <bytes 2097152-3483321 of the file to be attached, in binary format>
}
```

#### Response

The following example response shows a `Location` response header from which you can save the attachment ID \(`AAMkADI5MAAIT3drCAAABEgAQANAqbAe7qaROhYdTnUQwXm0=`\) for later use.

```http
HTTP/1.1 201 Created

Location: https://outlook.office.com/api/v2.0/Users('a8e8e219-4931-95c1-b73d-62626fd79c32@72aa88bf-76f0-494f-91ab-2d7cd730db47')/Messages('AAMkADI5MAAIT3drCAAA=')/Attachments('AAMkADI5MAAIT3drCAAABEgAQANAqbAe7qaROhYdTnUQwXm0=')
Content-Length: 0
```

### Example: Final upload to the event

#### Request

```http
PUT https://outlook.office.com/api/v2.0/Users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69@98a79ebe-74bf-4e07-a017-7b410848cb32')/Events('AAMkADU5CCmSAAA=')/AttachmentSessions('AAMkADU5RpAACJlCs8AAA=')?authtoken=eyJhbGciOiJSUzI1NiIsImtpZCI6IktmYUNIBtw
Content-Type: application/octet-stream
Content-Length: 1386170
Content-Range: bytes 2097152-3483321/3483322

{
  <bytes 2097152-3483321 of the file to be attached, in binary format>
}
```

#### Response

The following example response shows a `Location` response header from which you can save the attachment ID \(`AAMkADU5CCmSAAANZAlYPeyQByv7Y=`\) for later use.

```http
HTTP/1.1 201 Created

Location: https://outlook.office.com/api/v2.0/Users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69@98a79ebe-74bf-4e07-a017-7b410848cb32')/Events('AAMkADU5CCmSAAA=')/Attachments('AAMkADU5CCmSAAANZAlYPeyQByv7Y=')
Content-Length: 0
```

## Step 4 \(optional\): Get the file attachment from the Outlook item

As always, [getting an attachment](https://learn.microsoft.com/en-us/graph/api/attachment-get) from an Outlook item is not technically limited by attachment size.

However, getting a large file attachment in base64-encoded format affects API performance. If you expect a large attachment:

- As an alternative to getting the attachment content in base64 format, you can [get the raw data of the file attachment](https://learn.microsoft.com/en-us/graph/api/attachment-get#example-6-get-the-raw-contents-of-a-file-attachment-on-a-message).
- To [get the metadata of the file attachment](https://learn.microsoft.com/en-us/graph/api/attachment-get#example-1-get-the-properties-of-a-file-attachment), append a `$select` parameter to include only those metadata properties you want, excluding the **contentBytes** property which returns the file attachment in base64 format.

### Example: Get the raw file attached to the event

Following the event example and using the attachment ID returned in the `Location` header of the previous step, the example request in this section shows using a `$value` parameter to get the attachment raw content data.

#### Permissions

Use the least privileged delegated or application permission, `Calendars.Read`, as appropriate, for this operation. For more information, see [calendar permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

#### Request

```http
GET https://graph.microsoft.com/v1.0/Users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69@98a79ebe-74bf-4e07-a017-7b410848cb32')/Events('AAMkADU5CCmSAAA=')/Attachments('AAMkADU5CCmSAAANZAlYPeyQByv7Y=')/$value
```

#### Response

```http
HTTP/1.1 200 OK
content-length: 3483322
Content-type: image/jpeg

{Raw bytes of the file}
```

### Example: Get the metadata of the file attached to the message

Following the message example, the example request in this section shows using a `$select` parameter to get some of the metadata of a file attachment on a message, excluding **contentBytes**.

#### Permissions

Use the least privileged delegated or application permission, `Mail.Read`, as appropriate, for this operation. For more information, see [mail permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

#### Request

```http
GET https://graph.microsoft.com/api/v1.0/Users('a8e8e219-4931-95c1-b73d-62626fd79c32@72aa88bf-76f0-494f-91ab-2d7cd730db47')/Messages('AAMkADI5MAAIT3drCAAA=')/Attachments('AAMkADI5MAAIT3drCAAABEgAQANAqbAe7qaROhYdTnUQwXm0=')?$select=lastModifiedDateTime,name,contentType,size,isInline
```

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('a8e8e219-4931-95c1-b73d-62626fd79c32%4072aa88bf-76f0-494f-91ab-2d7cd730db47')/messages('AAMkADI5MAAIT3drCAAA%3D')/attachments/$entity",
    "@odata.type": "#microsoft.graph.fileAttachment",
    "@odata.mediaContentType": "image/jpeg",
    "id": "AAMkADI5MAAIT3drCAAABEgAQANAqbAe7qaROhYdTnUQwXm0=",
    "lastModifiedDateTime": "2019-09-24T23:27:43Z",
    "name": "flower",
    "contentType": "image/jpeg",
    "size": 3640066,
    "isInline": false
}
```

## Alternative: Cancel the upload session

At any point of time before the upload session expires, if you have to cancel the upload, you can use the same initial opaque URL to delete the upload session. A successful operation returns `HTTP 204 No Content`.

### Permissions

Because the initial opaque URL is pre-authenticated and contains the appropriate authorization token for subsequent queries for that upload session, do not specify an Authorization request header for this operation.

### Example: Cancel the upload session for the message

#### Request

```http
DELETE https://outlook.office.com/api/v2.0/Users('a8e8e219-4931-95c1-b73d-62626fd79c32@72aa88bf-76f0-494f-91ab-2d7cd730db47')/Messages('AAMkADI5MAAIT3drCAAA=')/AttachmentSessions('AAMkADI5MAAIT3k0tAAA=')?authtoken=eyJhbGciOiJSUzI1NiIsImtpZCI6IktmYUNIUlN6bllHMmNI
```

#### Response

```http
HTTP/1.1 204 No content
```

## Errors

### ErrorAttachmentSizeShouldNotBeLessThanMinimumSize

This error is returned when attempting to [create an upload session](https://learn.microsoft.com/en-us/graph/api/attachment-createuploadsession) to attach a file smaller than 3 MB. If the file size is under 3 MB, you should do a single POST on the **attachments** navigation property [of the message](https://learn.microsoft.com/en-us/graph/api/message-post-attachments) or [of the event](https://learn.microsoft.com/en-us/graph/api/event-post-attachments). The successful `POST` response includes the ID of the file attached to the message.
