<!-- Source: https://learn.microsoft.com/en-us/graph/api/event-forward?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-28 -->

# event: forward

Namespace: microsoft.graph

This action allows the organizer or attendee of a meeting [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) to forward the meeting request to a new recipient.

If the meeting event is forwarded from an attendee's Microsoft 365 mailbox to another recipient, this action also sends a message to notify the organizer of the forwarding, and adds the recipient to the organizer's copy of the meeting event. This convenience is not available when forwarding from an Outlook.com account.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.Read | Not available. |
| Delegated \(personal Microsoft account\) | Calendars.Read | Not available. |
| Application | Calendars.Read | Not available. |

## HTTP request

```http
POST /me/events/{id}/forward
POST /users/{id | userPrincipalName}/events/{id}/forward
POST /groups/{id}/events/{id}/forward

POST /me/calendar/events/{id}/forward
POST /users/{id | userPrincipalName}/calendar/events/{id}/forward
POST /groups/{id}/calendar/events/{id}/forward

POST /me/calendars/{id}/events/{id}/forward
POST /users/{id | userPrincipalName}/calendars/{id}/events/{id}/forward

POST /me/calendarGroups/{id}/calendars/{id}/events/{id}/forward
POST /users/{id | userPrincipalName}/calendarGroups/{id}/calendars/{id}/events/{id}/forward
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | Nature of the data in the body of an entity. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| Comment | String | A comment to include. Can be an empty string. |
| ToRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The list of recipients to forward the event to. |

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
POST https://graph.microsoft.com/v1.0/me/events/{id}/forward
Content-type: application/json

{
  "ToRecipients":[
      {
        "EmailAddress": {
          "Address":"danas@contoso.com",
          "Name":"Dana Swope"
        }
      }
     ],
  "Comment": "Dana, hope you can make this meeting."
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Events.Item.Forward;
using Microsoft.Graph.Models;

var requestBody = new ForwardPostRequestBody
{
	ToRecipients = new List<Recipient>
	{
		new Recipient
		{
			EmailAddress = new EmailAddress
			{
				Address = "danas@contoso.com",
				Name = "Dana Swope",
			},
		},
	},
	Comment = "Dana, hope you can make this meeting.",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Events["{event-id}"].Forward.PostAsync(requestBody);
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

requestBody := graphusers.NewItemForwardPostRequestBody()


recipient := graphmodels.NewRecipient()
emailAddress := graphmodels.NewEmailAddress()
address := "danas@contoso.com"
emailAddress.SetAddress(&address) 
name := "Dana Swope"
emailAddress.SetName(&name) 
recipient.SetEmailAddress(emailAddress)

toRecipients := []graphmodels.Recipientable {
	recipient,
}
requestBody.SetToRecipients(toRecipients)
comment := "Dana, hope you can make this meeting."
requestBody.SetComment(&comment) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Events().ByEventId("event-id").Forward().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.events.item.forward.ForwardPostRequestBody forwardPostRequestBody = new com.microsoft.graph.users.item.events.item.forward.ForwardPostRequestBody();
LinkedList<Recipient> toRecipients = new LinkedList<Recipient>();
Recipient recipient = new Recipient();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("danas@contoso.com");
emailAddress.setName("Dana Swope");
recipient.setEmailAddress(emailAddress);
toRecipients.add(recipient);
forwardPostRequestBody.setToRecipients(toRecipients);
forwardPostRequestBody.setComment("Dana, hope you can make this meeting.");
graphClient.me().events().byEventId("{event-id}").forward().post(forwardPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const forward = {
  ToRecipients: [
      {
        EmailAddress: {
          Address: 'danas@contoso.com',
          Name: 'Dana Swope'
        }
      }
     ],
  Comment: 'Dana, hope you can make this meeting.'
};

await client.api('/me/events/{id}/forward')
	.post(forward);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\Forward\ForwardPostRequestBody;
use Microsoft\Graph\Generated\Models\Recipient;
use Microsoft\Graph\Generated\Models\EmailAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ForwardPostRequestBody();
$toRecipientsRecipient1 = new Recipient();
$toRecipientsRecipient1EmailAddress = new EmailAddress();
$toRecipientsRecipient1EmailAddress->setAddress('danas@contoso.com');
$toRecipientsRecipient1EmailAddress->setName('Dana Swope');
$toRecipientsRecipient1->setEmailAddress($toRecipientsRecipient1EmailAddress);
$toRecipientsArray []= $toRecipientsRecipient1;
$requestBody->setToRecipients($toRecipientsArray);

$requestBody->setComment('Dana, hope you can make this meeting.');

$graphServiceClient->me()->events()->byEventId('event-id')->forward()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	ToRecipients = @(
		@{
			EmailAddress = @{
				Address = "danas@contoso.com"
				Name = "Dana Swope"
			}
		}
	)
	Comment = "Dana, hope you can make this meeting."
}

# A UPN can also be used as -UserId.
Invoke-MgForwardUserEvent -UserId $userId -EventId $eventId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.forward.forward_post_request_body import ForwardPostRequestBody
from msgraph.generated.models.recipient import Recipient
from msgraph.generated.models.email_address import EmailAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ForwardPostRequestBody(
	to_recipients = [
		Recipient(
			email_address = EmailAddress(
				address = "danas@contoso.com",
				name = "Dana Swope",
			),
		),
	],
	comment = "Dana, hope you can make this meeting.",
)

await graph_client.me.events.by_event_id('event-id').forward.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
