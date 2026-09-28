<!-- Source: https://learn.microsoft.com/en-us/graph/api/event-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Update event

Namespace: microsoft.graph

Update the properties of the [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

### Notes for updating specific properties

Note the following behaviors or recommendations when updating the corresponding properties:

- **attendees** property and meeting updates

  - An event update that includes only the **attendees** property in the request body sends a meeting update to only the attendees that have changed.
  - An event update that removes an attendee specified as a member of a distribution list sends a meeting update to all the attendees.

- **body** property and online meetings

  Before updating the body of an event that has been set up as an online meeting, be sure to first get the **body** property, apply the appropriate changes to the content, and preserve the meeting blob for online meeting. Inadvertently removing the meeting blob from the body would disable meeting online.
- **end** and **start** properties and their time zones

  When updating the time zone of the start or end time of an event, first [find the supported time zones](https://learn.microsoft.com/en-us/graph/api/outlookuser-supportedtimezones?view=graph-rest-1.0) to make sure you set only time zones that have been configured for the user's mailbox server.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite |
| Delegated \(personal Microsoft account\) | Calendars.ReadWrite |
| Application | Calendars.ReadWrite |

## HTTP request

```http
PATCH /me/events/{id}
PATCH /users/{id | userPrincipalName}/events/{id}
PATCH /groups/{id}/events/{id}

PATCH /me/calendar/events/{id}
PATCH /users/{id | userPrincipalName}/calendar/events/{id}
PATCH /groups/{id}/calendar/events/{id}

PATCH /me/calendars/{id}/events/{id}
PATCH /users/{id | userPrincipalName}/calendars/{id}/events/{id}

PATCH /me/calendarGroups/{id}/calendars/{id}/events/{id}
PATCH /users/{id | userPrincipalName}/calendarGroups/{id}/calendars/{id}/events/{id}
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| attendees | [Attendee](https://learn.microsoft.com/en-us/graph/api/resources/attendee?view=graph-rest-1.0) | The collection of attendees for the event. |
| body | [ItemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The body of the message associated with the event. |
| categories | String collection | The categories associated with the event. |
| end | DateTimeTimeZone | The date, time, and time zone that the event ends. |
| hideAttendees | Boolean | When set to `true`, each attendee only sees themselves in the meeting request and meeting **Tracking** list. Default is false. |
| importance | String | The importance of the event. The possible values are: `low`, `normal`, `high`. |
| isAllDay | Boolean | Set to true if the event lasts all day. |
| isOnlineMeeting | Boolean | `True` if this event has online meeting information, `false` otherwise. Default is false. Optional. |
| isReminderOn | Boolean | Set to true if an alert is set to remind the user of the event. |
| location | [Location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The location of the event. |
| locations | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) collection | The locations where the event is held or attended from. The **location** and **locations** properties always correspond with each other. If you update the **location** property, any prior locations in the **locations** collection would be removed and replaced by the new **location** value. |
| onlineMeetingProvider | onlineMeetingProviderType | Represents the online meeting service provider. The possible values are `teamsForBusiness`, `skypeForBusiness`, and `skypeForConsumer`. Optional. |
| recurrence | [PatternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | The recurrence pattern for the event. |
| reminderMinutesBeforeStart | Int32 | The number of minutes before the event start time that the reminder alert occurs. |
| responseRequested | Boolean | Set to true if the sender would like a response when the event is accepted or declined. |
| sensitivity | String | The possible values are: `normal`, `personal`, `private`, `confidential`. |
| showAs | String | The status to show. The possible values are: `free`, `tentative`, `busy`, `oof`, `workingElsewhere`, `unknown`. |
| start | DateTimeTimeZone | The start date, time, and time zone of the event. |
| subject | String | The text of the event's subject line. |

Because the **event** resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), you can use the `PATCH` operation to add, update, or delete your own app-specific data in custom properties of an extension in an existing **event** instance.

If the **event** you're updating is the master event of a recurring series, contains multiple attendees, and has instances that have been updated separately, multiple notification emails will be sent out: one for the master series and one per instance that has been updated.

## Response

If successful, this method returns a `200 OK` response code and updated [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object in the response body.

> **Note:** This method can return an HTTP 400 Bad Request response with an error code of `ErrorOccurrenceCrossingBoundary` and the following error message: Modified occurrence is crossing or overlapping adjacent occurrence. This indicates that the update violates the following Outlook restriction on recurrence exceptions: an occurrence cannot be moved to or before the day of the previous occurrence, and cannot be moved to or after the day of the following occurrence.

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
PATCH https://graph.microsoft.com/v1.0/me/events/{id}
Content-type: application/json

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "recurrence": null,
  "reminderMinutesBeforeStart": 99,
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "isReminderOn": true,
  "hideAttendees": false,
  "categories": ["Red category"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Event
{
	OriginalStartTimeZone = "originalStartTimeZone-value",
	OriginalEndTimeZone = "originalEndTimeZone-value",
	ResponseStatus = new ResponseStatus
	{
		Response = ResponseType.None,
		Time = DateTimeOffset.Parse("datetime-value"),
	},
	Recurrence = null,
	ReminderMinutesBeforeStart = 99,
	IsOnlineMeeting = true,
	OnlineMeetingProvider = OnlineMeetingProviderType.TeamsForBusiness,
	IsReminderOn = true,
	HideAttendees = false,
	Categories = new List<string>
	{
		"Red category",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events["{event-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewEvent()
originalStartTimeZone := "originalStartTimeZone-value"
requestBody.SetOriginalStartTimeZone(&originalStartTimeZone) 
originalEndTimeZone := "originalEndTimeZone-value"
requestBody.SetOriginalEndTimeZone(&originalEndTimeZone) 
responseStatus := graphmodels.NewResponseStatus()
response := graphmodels.NONE_RESPONSETYPE 
responseStatus.SetResponse(&response) 
time , err := time.Parse(time.RFC3339, "datetime-value")
responseStatus.SetTime(&time) 
requestBody.SetResponseStatus(responseStatus)
recurrence := null
requestBody.SetRecurrence(&recurrence) 
reminderMinutesBeforeStart := int32(99)
requestBody.SetReminderMinutesBeforeStart(&reminderMinutesBeforeStart) 
isOnlineMeeting := true
requestBody.SetIsOnlineMeeting(&isOnlineMeeting) 
onlineMeetingProvider := graphmodels.TEAMSFORBUSINESS_ONLINEMEETINGPROVIDERTYPE 
requestBody.SetOnlineMeetingProvider(&onlineMeetingProvider) 
isReminderOn := true
requestBody.SetIsReminderOn(&isReminderOn) 
hideAttendees := false
requestBody.SetHideAttendees(&hideAttendees) 
categories := []string {
	"Red category",
}
requestBody.SetCategories(categories)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().ByEventId("event-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event event = new Event();
event.setOriginalStartTimeZone("originalStartTimeZone-value");
event.setOriginalEndTimeZone("originalEndTimeZone-value");
ResponseStatus responseStatus = new ResponseStatus();
responseStatus.setResponse(ResponseType.None);
OffsetDateTime time = OffsetDateTime.parse("datetime-value");
responseStatus.setTime(time);
event.setResponseStatus(responseStatus);
event.setRecurrence(null);
event.setReminderMinutesBeforeStart(99);
event.setIsOnlineMeeting(true);
event.setOnlineMeetingProvider(OnlineMeetingProviderType.TeamsForBusiness);
event.setIsReminderOn(true);
event.setHideAttendees(false);
LinkedList<String> categories = new LinkedList<String>();
categories.add("Red category");
event.setCategories(categories);
Event result = graphClient.me().events().byEventId("{event-id}").patch(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = {
  originalStartTimeZone: 'originalStartTimeZone-value',
  originalEndTimeZone: 'originalEndTimeZone-value',
  responseStatus: {
    response: '',
    time: 'datetime-value'
  },
  recurrence: null,
  reminderMinutesBeforeStart: 99,
  isOnlineMeeting: true,
  onlineMeetingProvider: 'teamsForBusiness',
  isReminderOn: true,
  hideAttendees: false,
  categories: ['Red category']
};

await client.api('/me/events/{id}')
	.update(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Event;
use Microsoft\Graph\Generated\Models\ResponseStatus;
use Microsoft\Graph\Generated\Models\ResponseType;
use Microsoft\Graph\Generated\Models\OnlineMeetingProviderType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Event();
$requestBody->setOriginalStartTimeZone('originalStartTimeZone-value');
$requestBody->setOriginalEndTimeZone('originalEndTimeZone-value');
$responseStatus = new ResponseStatus();
$responseStatus->setResponse(new ResponseType('none'));
$responseStatus->setTime(new \DateTime('datetime-value'));
$requestBody->setResponseStatus($responseStatus);
$requestBody->setRecurrence(null);
$requestBody->setReminderMinutesBeforeStart(99);
$requestBody->setIsOnlineMeeting(true);
$requestBody->setOnlineMeetingProvider(new OnlineMeetingProviderType('teamsForBusiness'));
$requestBody->setIsReminderOn(true);
$requestBody->setHideAttendees(false);
$requestBody->setCategories(['Red category', 	]);

$result = $graphServiceClient->me()->events()->byEventId('event-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	originalStartTimeZone = "originalStartTimeZone-value"
	originalEndTimeZone = "originalEndTimeZone-value"
	responseStatus = @{
		response = ""
		time = [System.DateTime]::Parse("datetime-value")
	}
	recurrence = $null
	reminderMinutesBeforeStart = 99
	isOnlineMeeting = $true
	onlineMeetingProvider = "teamsForBusiness"
	isReminderOn = $true
	hideAttendees = $false
	categories = @(
	"Red category"
)
}

# A UPN can also be used as -UserId.
Update-MgUserEvent -UserId $userId -EventId $eventId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.event import Event
from msgraph.generated.models.response_status import ResponseStatus
from msgraph.generated.models.response_type import ResponseType
from msgraph.generated.models.online_meeting_provider_type import OnlineMeetingProviderType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Event(
	original_start_time_zone = "originalStartTimeZone-value",
	original_end_time_zone = "originalEndTimeZone-value",
	response_status = ResponseStatus(
		response = ResponseType.None,
		time = "datetime-value",
	),
	recurrence = None,
	reminder_minutes_before_start = 99,
	is_online_meeting = True,
	online_meeting_provider = OnlineMeetingProviderType.TeamsForBusiness,
	is_reminder_on = True,
	hide_attendees = False,
	categories = [
		"Red category",
	],
)

result = await graph_client.me.events.by_event_id('event-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "originalStartTimeZone": "originalStartTimeZone-value",
  "originalEndTimeZone": "originalEndTimeZone-value",
  "responseStatus": {
    "response": "",
    "time": "datetime-value"
  },
  "recurrence": null,
  "reminderMinutesBeforeStart": 99,
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness",
  "isReminderOn": true,
  "hideAttendees": false,
  "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NzIyNzhlMGEtM2YyZC00ZmY0LTlhNzUtZmZjNWFmZGNlNzE2%40thread.v2/0?context=%7b%22Tid%22%3a%2272f988bf-86f1-41af-91ab-2d7cd011db47%22%2c%22Oid%22%3a%22bc55b173-cff6-457d-b7a1-64bda7d7581a%22%7d",
        "conferenceId": "177513992",
        "tollNumber": "+91 22 6241 6885"
  }
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
