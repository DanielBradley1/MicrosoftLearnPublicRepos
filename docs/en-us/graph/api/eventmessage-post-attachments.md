<!-- Source: https://learn.microsoft.com/en-us/graph/api/eventmessage-post-attachments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Add attachment

Namespace: microsoft.graph

Use this API to create a new Attachment.

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

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Mail.ReadWrite | Not available. |
| Application | Mail.ReadWrite | Not available. |

## HTTP request

```http
POST /me/messages/{id}/attachments
POST /users/{id | userPrincipalName}/messages/{id}/attachments
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | Nature of the data in the body of an entity. Required. |

## Request body

In the request body, supply a JSON representation of [Attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) object.

## Response

If successful, this method returns `201 Created` response code and [Attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: File attachment

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
POST https://graph.microsoft.com/v1.0/me/messages/{id}/attachments
Content-type: application/json

{
  "@odata.type": "microsoft.graph.fileAttachment",
  "name": "name-value",
  "contentType": "contentType-value",
  "isInline": false,
  "contentLocation": "contentLocation-value",
  "contentBytes": "base64-contentBytes-value"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new FileAttachment
{
	OdataType = "microsoft.graph.fileAttachment",
	Name = "name-value",
	ContentType = "contentType-value",
	IsInline = false,
	ContentLocation = "contentLocation-value",
	ContentBytes = Convert.FromBase64String("base64-contentBytes-value"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages["{message-id}"].Attachments.PostAsync(requestBody);
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

requestBody := graphmodels.NewAttachment()
name := "name-value"
requestBody.SetName(&name) 
contentType := "contentType-value"
requestBody.SetContentType(&contentType) 
isInline := false
requestBody.SetIsInline(&isInline) 
contentLocation := "contentLocation-value"
requestBody.SetContentLocation(&contentLocation) 
contentBytes := []byte("base64-contentBytes-value")
requestBody.SetContentBytes(&contentBytes) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
attachments, err := graphClient.Me().Messages().ByMessageId("message-id").Attachments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileAttachment attachment = new FileAttachment();
attachment.setOdataType("microsoft.graph.fileAttachment");
attachment.setName("name-value");
attachment.setContentType("contentType-value");
attachment.setIsInline(false);
attachment.setContentLocation("contentLocation-value");
byte[] contentBytes = Base64.getDecoder().decode("base64-contentBytes-value");
attachment.setContentBytes(contentBytes);
Attachment result = graphClient.me().messages().byMessageId("{message-id}").attachments().post(attachment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const attachment = {
  '@odata.type': 'microsoft.graph.fileAttachment',
  name: 'name-value',
  contentType: 'contentType-value',
  isInline: false,
  contentLocation: 'contentLocation-value',
  contentBytes: 'base64-contentBytes-value'
};

await client.api('/me/messages/{id}/attachments')
	.post(attachment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\FileAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FileAttachment();
$requestBody->setOdataType('microsoft.graph.fileAttachment');
$requestBody->setName('name-value');
$requestBody->setContentType('contentType-value');
$requestBody->setIsInline(false);
$requestBody->setContentLocation('contentLocation-value');
$requestBody->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('base64-contentBytes-value')));

$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->attachments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	"@odata.type" = "microsoft.graph.fileAttachment"
	name = "name-value"
	contentType = "contentType-value"
	isInline = $false
	contentLocation = "contentLocation-value"
	contentBytes = "base64-contentBytes-value"
}

# A UPN can also be used as -UserId.
New-MgUserMessageAttachment -UserId $userId -MessageId $messageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.file_attachment import FileAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FileAttachment(
	odata_type = "microsoft.graph.fileAttachment",
	name = "name-value",
	content_type = "contentType-value",
	is_inline = False,
	content_location = "contentLocation-value",
	content_bytes = base64.urlsafe_b64decode("base64-contentBytes-value"),
)

result = await graph_client.me.messages.by_message_id('message-id').attachments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) object.

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
```

### Example 2: Item attachment

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
POST https://graph.microsoft.com/v1.0/me/events/{id}/attachments
Content-type: application/json

{
  "@odata.type": "#Microsoft.OutlookServices.ItemAttachment",
  "name": "name-value",
  "item": {
    "@odata.type": "microsoft.graph.message"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Attachment
{
	OdataType = "#Microsoft.OutlookServices.ItemAttachment",
	Name = "name-value",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"item" , new Message
			{
				OdataType = "microsoft.graph.message",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events["{event-id}"].Attachments.PostAsync(requestBody);
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

requestBody := graphmodels.NewAttachment()
name := "name-value"
requestBody.SetName(&name) 
additionalData := map[string]interface{}{
item := graphmodels.NewMessage()
	requestBody.SetItem(item)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
attachments, err := graphClient.Me().Events().ByEventId("event-id").Attachments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Attachment attachment = new Attachment();
attachment.setOdataType("#Microsoft.OutlookServices.ItemAttachment");
attachment.setName("name-value");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
Message item = new Message();
item.setOdataType("microsoft.graph.message");
additionalData.put("item", item);
attachment.setAdditionalData(additionalData);
Attachment result = graphClient.me().events().byEventId("{event-id}").attachments().post(attachment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const attachment = {
  '@odata.type': '#Microsoft.OutlookServices.ItemAttachment',
  name: 'name-value',
  item: {
    '@odata.type': 'microsoft.graph.message'
  }
};

await client.api('/me/events/{id}/attachments')
	.post(attachment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Attachment;
use Microsoft\Graph\Generated\Models\Message;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Attachment();
$requestBody->setOdataType('#Microsoft.OutlookServices.ItemAttachment');
$requestBody->setName('name-value');
$additionalData = [
	'item' => [
		'@odata.type' => 'microsoft.graph.message',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->me()->events()->byEventId('event-id')->attachments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "#Microsoft.OutlookServices.ItemAttachment"
	name = "name-value"
	item = @{
		"@odata.type" = "microsoft.graph.message"
	}
}

# A UPN can also be used as -UserId.
New-MgUserEventAttachment -UserId $userId -EventId $eventId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.attachment import Attachment
from msgraph.generated.models.message import Message
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Attachment(
	odata_type = "#Microsoft.OutlookServices.ItemAttachment",
	name = "name-value",
	additional_data = {
			"item" : {
					"@odata_type" : "microsoft.graph.message",
			},
	}
)

result = await graph_client.me.events.by_event_id('event-id').attachments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
```
