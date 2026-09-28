<!-- Source: https://learn.microsoft.com/en-us/graph/api/event-decline?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# event: decline

Namespace: microsoft.graph

Decline invitation to the specified [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) in a user [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0).

If the event allows proposals for new times, on declining the event, an invitee can choose to suggest an alternative time by including the **proposedNewTime** parameter. For more information on how to propose a time, and how to receive and accept a new time proposal, see [Propose new meeting times](https://learn.microsoft.com/en-us/graph/outlook-calendar-meeting-proposals).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Calendars.ReadWrite | Not available. |
| Application | Calendars.ReadWrite | Not available. |

## HTTP request

```http
POST /me/events/{id}/decline
POST /users/{id | userPrincipalName}/events/{id}/decline

POST /me/calendar/events/{id}/decline
POST /users/{id | userPrincipalName}/calendar/events/{id}/decline

POST /me/calendars/{id}/events/{id}/decline
POST /users/{id | userPrincipalName}/calendars/{id}/events/{id}/decline

POST /me/calendarGroups/{id}/calendars/{id}/events/{id}/decline
POST /users/{id | userPrincipalName}/calendarGroups/{id}/calendars/{id}/events/{id}/decline
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
| comment | String | Text included in the response. Optional. |
| proposedNewTime | [timeSlot](https://learn.microsoft.com/en-us/graph/api/resources/timeslot?view=graph-rest-1.0) | An alternate date/time proposed by an invitee for a meeting request to start and end. Valid only for events that allow new time proposals. Setting this parameter requires setting **sendResponse** to `true`. Optional. |
| sendResponse | Boolean | `true` if a response is to be sent to the organizer; otherwise, `false`. Optional. Default is `true`. |

## Response

If successful, this method returns `202 Accepted` response code. It doesn't return anything in the response body.

This action returns HTTP 400 if one or both of the following occur:

- The **proposedNewTime** parameter is included but the **allowNewTimeProposals** property of the **event** is `false`.
- The **proposedNewTime** parameter is included but the **sendResponse** parameter is set to `false`.

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
POST https://graph.microsoft.com/v1.0/me/events/{id}/decline
Content-type: application/json

{
  "comment": "I won't be able to make this week. How about next week?",
  "sendResponse": true,
  "proposedNewTime": {
      "start": { 
          "dateTime": "2019-12-02T18:00:00", 
          "timeZone": "Pacific Standard Time" 
      }, 
      "end": { 
          "dateTime": "2019-12-02T19:00:00", 
          "timeZone": "Pacific Standard Time" 
      }     
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Events.Item.Decline;
using Microsoft.Graph.Models;

var requestBody = new DeclinePostRequestBody
{
	Comment = "I won't be able to make this week. How about next week?",
	SendResponse = true,
	ProposedNewTime = new TimeSlot
	{
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
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Events["{event-id}"].Decline.PostAsync(requestBody);
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

requestBody := graphusers.NewItemDeclinePostRequestBody()
comment := "I won't be able to make this week. How about next week?"
requestBody.SetComment(&comment) 
sendResponse := true
requestBody.SetSendResponse(&sendResponse) 
proposedNewTime := graphmodels.NewTimeSlot()
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-12-02T18:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
proposedNewTime.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-12-02T19:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
proposedNewTime.SetEnd(end)
requestBody.SetProposedNewTime(proposedNewTime)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Events().ByEventId("event-id").Decline().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.events.item.decline.DeclinePostRequestBody declinePostRequestBody = new com.microsoft.graph.users.item.events.item.decline.DeclinePostRequestBody();
declinePostRequestBody.setComment("I won't be able to make this week. How about next week?");
declinePostRequestBody.setSendResponse(true);
TimeSlot proposedNewTime = new TimeSlot();
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2019-12-02T18:00:00");
start.setTimeZone("Pacific Standard Time");
proposedNewTime.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2019-12-02T19:00:00");
end.setTimeZone("Pacific Standard Time");
proposedNewTime.setEnd(end);
declinePostRequestBody.setProposedNewTime(proposedNewTime);
graphClient.me().events().byEventId("{event-id}").decline().post(declinePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const decline = {
  comment: 'I won\'t be able to make this week. How about next week?',
  sendResponse: true,
  proposedNewTime: {
      start: { 
          dateTime: '2019-12-02T18:00:00', 
          timeZone: 'Pacific Standard Time' 
      }, 
      end: { 
          dateTime: '2019-12-02T19:00:00', 
          timeZone: 'Pacific Standard Time' 
      }     
  }
};

await client.api('/me/events/{id}/decline')
	.post(decline);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\Decline\DeclinePostRequestBody;
use Microsoft\Graph\Generated\Models\TimeSlot;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DeclinePostRequestBody();
$requestBody->setComment('I won\'t be able to make this week. How about next week?');
$requestBody->setSendResponse(true);
$proposedNewTime = new TimeSlot();
$proposedNewTimeStart = new DateTimeTimeZone();
$proposedNewTimeStart->setDateTime('2019-12-02T18:00:00');
$proposedNewTimeStart->setTimeZone('Pacific Standard Time');
$proposedNewTime->setStart($proposedNewTimeStart);
$proposedNewTimeEnd = new DateTimeTimeZone();
$proposedNewTimeEnd->setDateTime('2019-12-02T19:00:00');
$proposedNewTimeEnd->setTimeZone('Pacific Standard Time');
$proposedNewTime->setEnd($proposedNewTimeEnd);
$requestBody->setProposedNewTime($proposedNewTime);

$graphServiceClient->me()->events()->byEventId('event-id')->decline()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	comment = "I won't be able to make this week. How about next week?"
	sendResponse = $true
	proposedNewTime = @{
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

# A UPN can also be used as -UserId.
Invoke-MgDeclineUserEvent -UserId $userId -EventId $eventId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.decline.decline_post_request_body import DeclinePostRequestBody
from msgraph.generated.models.time_slot import TimeSlot
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DeclinePostRequestBody(
	comment = "I won't be able to make this week. How about next week?",
	send_response = True,
	proposed_new_time = TimeSlot(
		start = DateTimeTimeZone(
			date_time = "2019-12-02T18:00:00",
			time_zone = "Pacific Standard Time",
		),
		end = DateTimeTimeZone(
			date_time = "2019-12-02T19:00:00",
			time_zone = "Pacific Standard Time",
		),
	),
)

await graph_client.me.events.by_event_id('event-id').decline.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

  


### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
