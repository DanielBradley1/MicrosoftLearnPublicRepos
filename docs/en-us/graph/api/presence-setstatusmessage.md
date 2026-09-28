<!-- Source: https://learn.microsoft.com/en-us/graph/api/presence-setstatusmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# presence: setStatusMessage

Namespace: microsoft.graph

Set a presence status message for a user. An optional expiration date and time can be supplied.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Presence.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Presence.ReadWrite.All | Not available. |

## HTTP Request

```http
POST /users/{id}/presence/setStatusMessage
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| --- | --- | --- |
| `statusMessage` | [microsoft.graph.presenceStatusMessage](https://learn.microsoft.com/en-us/graph/api/resources/presencestatusmessage?view=graph-rest-1.0) | Contains the presence status message of the user. |

## Response

If successful, this method returns a `200 OK` response code.

## Examples

### Example 1: Set status message with expiry date

The following request sets the presence status message as "Hey I'm currently in a meeting." for user `fa8bf3dc-eca7-46b7-bad1-db199b62afc3`, with the expiration on `2022-10-18 at 17:05:33.2079781 Pacific Standard Time`.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
POST https://graph.microsoft.com/v1.0/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setStatusMessage
Content-Type: application/json

{
  "statusMessage": {
    "message": {
        "content": "Hey I'm currently in a meeting.",
        "contentType": "text"
    },
    "expiryDateTime": {
        "dateTime": "2022-10-18T17:05:33.2079781",
        "timeZone": "Pacific Standard Time"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Users.Item.Presence.SetStatusMessage;
using Microsoft.Graph.Models;

var requestBody = new SetStatusMessagePostRequestBody
{
	StatusMessage = new PresenceStatusMessage
	{
		Message = new ItemBody
		{
			Content = "Hey I'm currently in a meeting.",
			ContentType = BodyType.Text,
		},
		ExpiryDateTime = new DateTimeTimeZone
		{
			DateTime = "2022-10-18T17:05:33.2079781",
			TimeZone = "Pacific Standard Time",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].Presence.SetStatusMessage.PostAsync(requestBody);
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

requestBody := graphusers.NewSetStatusMessagePostRequestBody()
statusMessage := graphmodels.NewPresenceStatusMessage()
message := graphmodels.NewItemBody()
content := "Hey I'm currently in a meeting."
message.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
message.SetContentType(&contentType) 
statusMessage.SetMessage(message)
expiryDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2022-10-18T17:05:33.2079781"
expiryDateTime.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
expiryDateTime.SetTimeZone(&timeZone) 
statusMessage.SetExpiryDateTime(expiryDateTime)
requestBody.SetStatusMessage(statusMessage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").Presence().SetStatusMessage().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.presence.setstatusmessage.SetStatusMessagePostRequestBody setStatusMessagePostRequestBody = new com.microsoft.graph.users.item.presence.setstatusmessage.SetStatusMessagePostRequestBody();
PresenceStatusMessage statusMessage = new PresenceStatusMessage();
ItemBody message = new ItemBody();
message.setContent("Hey I'm currently in a meeting.");
message.setContentType(BodyType.Text);
statusMessage.setMessage(message);
DateTimeTimeZone expiryDateTime = new DateTimeTimeZone();
expiryDateTime.setDateTime("2022-10-18T17:05:33.2079781");
expiryDateTime.setTimeZone("Pacific Standard Time");
statusMessage.setExpiryDateTime(expiryDateTime);
setStatusMessagePostRequestBody.setStatusMessage(statusMessage);
graphClient.users().byUserId("{user-id}").presence().setStatusMessage().post(setStatusMessagePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setStatusMessage = {
  statusMessage: {
    message: {
        content: 'Hey I\'m currently in a meeting.',
        contentType: 'text'
    },
    expiryDateTime: {
        dateTime: '2022-10-18T17:05:33.2079781',
        timeZone: 'Pacific Standard Time'
    }
  }
};

await client.api('/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setStatusMessage')
	.post(setStatusMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Presence\SetStatusMessage\SetStatusMessagePostRequestBody;
use Microsoft\Graph\Generated\Models\PresenceStatusMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetStatusMessagePostRequestBody();
$statusMessage = new PresenceStatusMessage();
$statusMessageMessage = new ItemBody();
$statusMessageMessage->setContent('Hey I\'m currently in a meeting.');
$statusMessageMessage->setContentType(new BodyType('text'));
$statusMessage->setMessage($statusMessageMessage);
$statusMessageExpiryDateTime = new DateTimeTimeZone();
$statusMessageExpiryDateTime->setDateTime('2022-10-18T17:05:33.2079781');
$statusMessageExpiryDateTime->setTimeZone('Pacific Standard Time');
$statusMessage->setExpiryDateTime($statusMessageExpiryDateTime);
$requestBody->setStatusMessage($statusMessage);

$graphServiceClient->users()->byUserId('user-id')->presence()->setStatusMessage()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	statusMessage = @{
		message = @{
			content = "Hey I'm currently in a meeting."
			contentType = "text"
		}
		expiryDateTime = @{
			dateTime = "2022-10-18T17:05:33.2079781"
			timeZone = "Pacific Standard Time"
		}
	}
}

Set-MgUserPresenceStatusMessage -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.presence.set_status_message.set_status_message_post_request_body import SetStatusMessagePostRequestBody
from msgraph.generated.models.presence_status_message import PresenceStatusMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetStatusMessagePostRequestBody(
	status_message = PresenceStatusMessage(
		message = ItemBody(
			content = "Hey I'm currently in a meeting.",
			content_type = BodyType.Text,
		),
		expiry_date_time = DateTimeTimeZone(
			date_time = "2022-10-18T17:05:33.2079781",
			time_zone = "Pacific Standard Time",
		),
	),
)

await graph_client.users.by_user_id('user-id').presence.set_status_message.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

```http
HTTP/1.1 200 OK
```

### Example 2: Set status message of another user

The following request sets the presence status message as "Hey I am available now" for user `fa8bf3dc-eca7-46b7-bad1-db199b62afc3`. In Example 3, presence information for user `fa8bf3dc-eca7-46b7-bad1-db199b62afc3` is obtained on behalf of another user via a [getPresence](https://learn.microsoft.com/en-us/graph/api/presence-get?view=graph-rest-1.0) request.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
POST https://graph.microsoft.com/v1.0/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setStatusMessage
Content-Type: application/json

{
  "statusMessage": {
    "message": {
      "content": "Hey I am available now",
      "contentType": "text"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Users.Item.Presence.SetStatusMessage;
using Microsoft.Graph.Models;

var requestBody = new SetStatusMessagePostRequestBody
{
	StatusMessage = new PresenceStatusMessage
	{
		Message = new ItemBody
		{
			Content = "Hey I am available now",
			ContentType = BodyType.Text,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].Presence.SetStatusMessage.PostAsync(requestBody);
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

requestBody := graphusers.NewSetStatusMessagePostRequestBody()
statusMessage := graphmodels.NewPresenceStatusMessage()
message := graphmodels.NewItemBody()
content := "Hey I am available now"
message.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
message.SetContentType(&contentType) 
statusMessage.SetMessage(message)
requestBody.SetStatusMessage(statusMessage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").Presence().SetStatusMessage().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.presence.setstatusmessage.SetStatusMessagePostRequestBody setStatusMessagePostRequestBody = new com.microsoft.graph.users.item.presence.setstatusmessage.SetStatusMessagePostRequestBody();
PresenceStatusMessage statusMessage = new PresenceStatusMessage();
ItemBody message = new ItemBody();
message.setContent("Hey I am available now");
message.setContentType(BodyType.Text);
statusMessage.setMessage(message);
setStatusMessagePostRequestBody.setStatusMessage(statusMessage);
graphClient.users().byUserId("{user-id}").presence().setStatusMessage().post(setStatusMessagePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setStatusMessage = {
  statusMessage: {
    message: {
      content: 'Hey I am available now',
      contentType: 'text'
    }
  }
};

await client.api('/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setStatusMessage')
	.post(setStatusMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Presence\SetStatusMessage\SetStatusMessagePostRequestBody;
use Microsoft\Graph\Generated\Models\PresenceStatusMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetStatusMessagePostRequestBody();
$statusMessage = new PresenceStatusMessage();
$statusMessageMessage = new ItemBody();
$statusMessageMessage->setContent('Hey I am available now');
$statusMessageMessage->setContentType(new BodyType('text'));
$statusMessage->setMessage($statusMessageMessage);
$requestBody->setStatusMessage($statusMessage);

$graphServiceClient->users()->byUserId('user-id')->presence()->setStatusMessage()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	statusMessage = @{
		message = @{
			content = "Hey I am available now"
			contentType = "text"
		}
	}
}

Set-MgUserPresenceStatusMessage -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.presence.set_status_message.set_status_message_post_request_body import SetStatusMessagePostRequestBody
from msgraph.generated.models.presence_status_message import PresenceStatusMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetStatusMessagePostRequestBody(
	status_message = PresenceStatusMessage(
		message = ItemBody(
			content = "Hey I am available now",
			content_type = BodyType.Text,
		),
	),
)

await graph_client.users.by_user_id('user-id').presence.set_status_message.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

```http
HTTP/1.1 200 OK
```

### Example 3: Get another user presence

This example follows Example 2. Presence information for user `fa8bf3dc-eca7-46b7-bad1-db199b62afc3` is obtained on behalf of another user via a [getPresence](https://learn.microsoft.com/en-us/graph/api/presence-get?view=graph-rest-1.0) request.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Presence.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
presence, err := graphClient.Users().ByUserId("user-id").Presence().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Presence result = graphClient.users().byUserId("{user-id}").presence().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let presence = await client.api('/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->presence()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgUserPresence -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').presence.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

Because this request gets the presence status for another user, the `statusMessage.expiryDateTime` and `statusMessage.publishedDateTime` properties are not included in the response body.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "fa8bf3dc-eca7-46b7-bad1-db199b62afc3",
  "availability": "Available",
  "activity": "Available",
  "outOfOfficeSettings": {
    "message": null,
    "isOutOfOffice": false
  },
  "statusMessage": {
    "message": {
      "content": "Hey I am available now",
      "contentType": "text"
    }
  },
  "sequenceNumber": "A0129311063"
}
```
