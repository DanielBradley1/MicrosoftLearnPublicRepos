<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# Create event

Namespace: microsoft.graph

Create an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) in the user's default calendar or specified calendar.

By default, the **allowNewTimeProposals** property is set to true when an event is created, which means invitees can propose a different date/time for the event. See [Propose new meeting times](https://learn.microsoft.com/en-us/graph/outlook-calendar-meeting-proposals) for more information on how to propose a time, and how to receive and accept a new time proposal.

You can specify the time zone for each of the start and end times of the event as part of their values, because the **start** and **end** properties are of [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) type. First [find the supported time zones](https://learn.microsoft.com/en-us/graph/api/outlookuser-supportedtimezones?view=graph-rest-1.0) to make sure you set only time zones that have been configured for the user's mailbox server.

When you create an event that includes attendees, the server sends invitations to all attendees. This ensures consistency between the organizer's and attendees' views of the event and can't be configured.

**Setting the location in an event**

An Exchange administrator can set up a mailbox and an email address for a resource such as a meeting room, or equipment like a projector. Users can then invite the resource as an attendee to a meeting. On behalf of the resource, the server accepts or rejects the meeting request based on the free/busy schedule of the resource. If the server accepts a meeting for the resource, it creates an event for the meeting in the resource's calendar. If the meeting is rescheduled, the server automatically updates the event in the resource's calendar.

Another advantage of setting up a mailbox for a resource is to control scheduling of the resource, for example, only executives or their delegates can book a private meeting room.

If you're organizing an event that involves a meeting location:

1. Set the **location** property of the **event** accordingly.
2. Set the optional **locationEmailAddress** property if the meeting location has an email address.

Additionally, if the meeting location has been set up as a resource, or if the event involves some equipment that has been set up as a resource:

3. Invite the resource as an [attendee](https://learn.microsoft.com/en-us/graph/api/resources/attendee?view=graph-rest-1.0).
4. Set the attendee **type** property as `resource`.
5. Set the attendee **emailAddress** as the resource email address.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite |
| Delegated \(personal Microsoft account\) | Calendars.ReadWrite |
| Application | Calendars.ReadWrite |

## HTTP request

```http
POST /me/events
POST /users/{id | userPrincipalName}/events

POST /me/calendar/events
POST /users/{id | userPrincipalName}/calendar/events

POST /me/calendars/{id}/events
POST /users/{id | userPrincipalName}/calendars/{id}/events
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object.

Since the **event** resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), you can use the `POST` operation and add custom properties with your own data to the event while creating it.

## Response

If successful, this method returns `201 Created` response code and [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an event in the specified time zone, and assign the event an optional transactionId value.

#### Request

The following example shows a request. It uses the `Prefer: outlook.timezone` request header to specify the time zone for the start and end times in the response. It also sets the **transactionId** property to reduce unnecessary retries on the server.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/events
Prefer: outlook.timezone="Pacific Standard Time"
Content-type: application/json

{
  "subject": "Let's go for lunch",
  "body": {
    "contentType": "HTML",
    "content": "Does noon work for you?"
  },
  "start": {
      "dateTime": "2017-04-15T12:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2017-04-15T14:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "location":{
      "displayName":"Harry's Bar"
  },
  "attendees": [
    {
      "emailAddress": {
        "address":"samanthab@contoso.com",
        "name": "Samantha Booth"
      },
      "type": "required"
    }
  ],
  "allowNewTimeProposals": true,
  "transactionId":"7E163156-7762-4BEB-A1C6-729EA81755A7"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Event
{
	Subject = "Let's go for lunch",
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Does noon work for you?",
	},
	Start = new DateTimeTimeZone
	{
		DateTime = "2017-04-15T12:00:00",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2017-04-15T14:00:00",
		TimeZone = "Pacific Standard Time",
	},
	Location = new Location
	{
		DisplayName = "Harry's Bar",
	},
	Attendees = new List<Attendee>
	{
		new Attendee
		{
			EmailAddress = new EmailAddress
			{
				Address = "samanthab@contoso.com",
				Name = "Samantha Booth",
			},
			Type = AttendeeType.Required,
		},
	},
	AllowNewTimeProposals = true,
	TransactionId = "7E163156-7762-4BEB-A1C6-729EA81755A7",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")

configuration := &graphusers.ItemEventsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewEvent()
subject := "Let's go for lunch"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Does noon work for you?"
body.SetContent(&content) 
requestBody.SetBody(body)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-04-15T12:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-04-15T14:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
requestBody.SetEnd(end)
location := graphmodels.NewLocation()
displayName := "Harry's Bar"
location.SetDisplayName(&displayName) 
requestBody.SetLocation(location)


attendee := graphmodels.NewAttendee()
emailAddress := graphmodels.NewEmailAddress()
address := "samanthab@contoso.com"
emailAddress.SetAddress(&address) 
name := "Samantha Booth"
emailAddress.SetName(&name) 
attendee.SetEmailAddress(emailAddress)
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendee.SetType(&type) 

attendees := []graphmodels.Attendeeable {
	attendee,
}
requestBody.SetAttendees(attendees)
allowNewTimeProposals := true
requestBody.SetAllowNewTimeProposals(&allowNewTimeProposals) 
transactionId := "7E163156-7762-4BEB-A1C6-729EA81755A7"
requestBody.SetTransactionId(&transactionId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event event = new Event();
event.setSubject("Let's go for lunch");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Does noon work for you?");
event.setBody(body);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2017-04-15T12:00:00");
start.setTimeZone("Pacific Standard Time");
event.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2017-04-15T14:00:00");
end.setTimeZone("Pacific Standard Time");
event.setEnd(end);
Location location = new Location();
location.setDisplayName("Harry's Bar");
event.setLocation(location);
LinkedList<Attendee> attendees = new LinkedList<Attendee>();
Attendee attendee = new Attendee();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("samanthab@contoso.com");
emailAddress.setName("Samantha Booth");
attendee.setEmailAddress(emailAddress);
attendee.setType(AttendeeType.Required);
attendees.add(attendee);
event.setAttendees(attendees);
event.setAllowNewTimeProposals(true);
event.setTransactionId("7E163156-7762-4BEB-A1C6-729EA81755A7");
Event result = graphClient.me().events().post(event, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = {
  subject: 'Let\'s go for lunch',
  body: {
    contentType: 'HTML',
    content: 'Does noon work for you?'
  },
  start: {
      dateTime: '2017-04-15T12:00:00',
      timeZone: 'Pacific Standard Time'
  },
  end: {
      dateTime: '2017-04-15T14:00:00',
      timeZone: 'Pacific Standard Time'
  },
  location: {
      displayName: 'Harry\'s Bar'
  },
  attendees: [
    {
      emailAddress: {
        address: 'samanthab@contoso.com',
        name: 'Samantha Booth'
      },
      type: 'required'
    }
  ],
  allowNewTimeProposals: true,
  transactionId: '7E163156-7762-4BEB-A1C6-729EA81755A7'
};

await client.api('/me/events')
	.post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\EventsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Models\Event;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\Location;
use Microsoft\Graph\Generated\Models\Attendee;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\AttendeeType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Event();
$requestBody->setSubject('Let\'s go for lunch');
$body = new ItemBody();
$body->setContentType(new BodyType('hTML'));
$body->setContent('Does noon work for you?');
$requestBody->setBody($body);
$start = new DateTimeTimeZone();
$start->setDateTime('2017-04-15T12:00:00');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2017-04-15T14:00:00');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$location = new Location();
$location->setDisplayName('Harry\'s Bar');
$requestBody->setLocation($location);
$attendeesAttendee1 = new Attendee();
$attendeesAttendee1EmailAddress = new EmailAddress();
$attendeesAttendee1EmailAddress->setAddress('samanthab@contoso.com');
$attendeesAttendee1EmailAddress->setName('Samantha Booth');
$attendeesAttendee1->setEmailAddress($attendeesAttendee1EmailAddress);
$attendeesAttendee1->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee1;
$requestBody->setAttendees($attendeesArray);

$requestBody->setAllowNewTimeProposals(true);
$requestBody->setTransactionId('7E163156-7762-4BEB-A1C6-729EA81755A7');
$requestConfiguration = new EventsRequestBuilderPostRequestConfiguration();
$headers = [
	'Prefer' => 'outlook.timezone="Pacific Standard Time"',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->me()->events()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	subject = "Let's go for lunch"
	body = @{
		contentType = "HTML"
		content = "Does noon work for you?"
	}
	start = @{
		dateTime = "2017-04-15T12:00:00"
		timeZone = "Pacific Standard Time"
	}
	end = @{
		dateTime = "2017-04-15T14:00:00"
		timeZone = "Pacific Standard Time"
	}
	location = @{
		displayName = "Harry's Bar"
	}
	attendees = @(
		@{
			emailAddress = @{
				address = "samanthab@contoso.com"
				name = "Samantha Booth"
			}
			type = "required"
		}
	)
	allowNewTimeProposals = $true
	transactionId = "7E163156-7762-4BEB-A1C6-729EA81755A7"
}

# A UPN can also be used as -UserId.
New-MgUserEvent -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.events_request_builder import EventsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.event import Event
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.location import Location
from msgraph.generated.models.attendee import Attendee
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.attendee_type import AttendeeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Event(
	subject = "Let's go for lunch",
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Does noon work for you?",
	),
	start = DateTimeTimeZone(
		date_time = "2017-04-15T12:00:00",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2017-04-15T14:00:00",
		time_zone = "Pacific Standard Time",
	),
	location = Location(
		display_name = "Harry's Bar",
	),
	attendees = [
		Attendee(
			email_address = EmailAddress(
				address = "samanthab@contoso.com",
				name = "Samantha Booth",
			),
			type = AttendeeType.Required,
		),
	],
	allow_new_time_proposals = True,
	transaction_id = "7E163156-7762-4BEB-A1C6-729EA81755A7",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")


result = await graph_client.me.events.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object.

#### Response

Here is an example of the response, which shows the **start** and **end** properties use the time zone specified in the `Prefer: outlook.timezone` header. Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#users('cd209b0b-3f83-4c35-82d2-d88a61820480')/events/$entity",
    "@odata.etag":"W/\"ZlnW4RIAV06KYYwlrfNZvQAALfZeRQ==\"",
    "id":"AAMkAGI1AAAt9AHjAAA=",
    "createdDateTime":"2017-04-15T03:00:50.7579581Z",
    "lastModifiedDateTime":"2017-04-15T03:00:51.245372Z",
    "changeKey":"ZlnW4RIAV06KYYwlrfNZvQAALfZeRQ==",
    "categories":[

    ],
    "originalStartTimeZone":"Pacific Standard Time",
    "originalEndTimeZone":"Pacific Standard Time",
    "iCalUId":"040000008200E00074C5B7101A82E00800000000DA2B357D94B5D201000000000000000010000000EC4597557F0CB34EA4CC2887EA7B17C3",
    "reminderMinutesBeforeStart":15,
    "isReminderOn":true,
    "hasAttachments":false,
    "hideAttendees": false,
    "subject":"Let's go brunch",
    "bodyPreview":"Does noon work for you?",
    "importance":"normal",
    "sensitivity":"normal",
    "isAllDay":false,
    "isCancelled":false,
    "isDraft": false,
    "isOrganizer":true,
    "responseRequested":true,
    "seriesMasterId":null,
    "transactionId":"7E163156-7762-4BEB-A1C6-729EA81755A7",
    "showAs":"busy",
    "type":"singleInstance",
    "webLink":"https://outlook.office365.com/owa/?itemid=AAMkAGI1AAAt9AHjAAA%3D&exvsurl=1&path=/calendar/item",
    "onlineMeetingUrl":null,
    "isOnlineMeeting":false,
    "onlineMeetingProvider":"unknown",
    "onlineMeeting":null,
    "allowNewTimeProposals": true,
    "responseStatus":{
        "response":"organizer",
        "time":"0001-01-01T00:00:00Z"
    },
    "body":{
        "contentType":"html",
        "content":"<html><head></head><body>Does late morning work for you?</body></html>"
    },
    "start":{
        "dateTime":"2017-04-15T11:00:00.0000000",
        "timeZone":"Pacific Standard Time"
    },
    "end":{
        "dateTime":"2017-04-15T12:00:00.0000000",
        "timeZone":"Pacific Standard Time"
    },
    "location": {
        "displayName": "Harry's Bar",
        "locationType": "default",
        "uniqueId": "Harry's Bar",
        "uniqueIdType": "private"
    },
    "locations": [
        {
            "displayName": "Harry's Bar",
            "locationType": "default",
            "uniqueIdType": "unknown"
        }
    ],
    "recurrence":null,
    "attendees":[
        {
            "type":"required",
            "status":{
                "response":"none",
                "time":"0001-01-01T00:00:00Z"
            },
            "emailAddress":{
                "name":"Samantha Booth",
                "address":"samanthab@contoso.com"
            }
        }
    ],
    "organizer":{
        "emailAddress":{
            "name":"Dana Swope",
            "address":"danas@contoso.com"
        }
    }
}
```

### Example 2: Create an event that occurs in multiple locations

#### Request

The next example request specifies 3 locations where the organizer and attendees can attend the meeting from.

In the request body, supply a JSON representation of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/events
Prefer: outlook.timezone="Pacific Standard Time"
Content-type: application/json

{
  "subject": "Plan summer company picnic",
  "body": {
    "contentType": "HTML",
    "content": "Let's kick-start this event planning!"
  },
  "start": {
      "dateTime": "2017-08-30T11:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2017-08-30T12:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "attendees": [
    {
      "emailAddress": {
        "address": "DanaS@contoso.com",
        "name": "Dana Swope"
      },
      "type": "Required"
    },
    {
      "emailAddress": {
        "address": "AlexW@contoso.com",
        "name": "Alex Wilber"
      },
      "type": "Required"
    }
  ],
  "location": {
    "displayName": "Conf Room 3; Fourth Coffee; Home Office",
    "locationType": "Default"
  },
  "locations": [
    {
      "displayName": "Conf Room 3"
    },
    {
      "displayName": "Fourth Coffee",
      "address": {
        "street": "4567 Main St",
        "city": "Redmond",
        "state": "WA",
        "countryOrRegion": "US",
        "postalCode": "32008"
      },
      "coordinates": {
        "latitude": 47.672,
        "longitude": -102.103
      }
    },
    {
      "displayName": "Home Office"
    }
  ],
  "allowNewTimeProposals": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Event
{
	Subject = "Plan summer company picnic",
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Let's kick-start this event planning!",
	},
	Start = new DateTimeTimeZone
	{
		DateTime = "2017-08-30T11:00:00",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2017-08-30T12:00:00",
		TimeZone = "Pacific Standard Time",
	},
	Attendees = new List<Attendee>
	{
		new Attendee
		{
			EmailAddress = new EmailAddress
			{
				Address = "DanaS@contoso.com",
				Name = "Dana Swope",
			},
			Type = AttendeeType.Required,
		},
		new Attendee
		{
			EmailAddress = new EmailAddress
			{
				Address = "AlexW@contoso.com",
				Name = "Alex Wilber",
			},
			Type = AttendeeType.Required,
		},
	},
	Location = new Location
	{
		DisplayName = "Conf Room 3; Fourth Coffee; Home Office",
		LocationType = LocationType.Default,
	},
	Locations = new List<Location>
	{
		new Location
		{
			DisplayName = "Conf Room 3",
		},
		new Location
		{
			DisplayName = "Fourth Coffee",
			Address = new PhysicalAddress
			{
				Street = "4567 Main St",
				City = "Redmond",
				State = "WA",
				CountryOrRegion = "US",
				PostalCode = "32008",
			},
			Coordinates = new OutlookGeoCoordinates
			{
				Latitude = 47.672d,
				Longitude = -102.103d,
			},
		},
		new Location
		{
			DisplayName = "Home Office",
		},
	},
	AllowNewTimeProposals = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")

configuration := &graphusers.ItemEventsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewEvent()
subject := "Plan summer company picnic"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Let's kick-start this event planning!"
body.SetContent(&content) 
requestBody.SetBody(body)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-08-30T11:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-08-30T12:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
requestBody.SetEnd(end)


attendee := graphmodels.NewAttendee()
emailAddress := graphmodels.NewEmailAddress()
address := "DanaS@contoso.com"
emailAddress.SetAddress(&address) 
name := "Dana Swope"
emailAddress.SetName(&name) 
attendee.SetEmailAddress(emailAddress)
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendee.SetType(&type) 
attendee1 := graphmodels.NewAttendee()
emailAddress := graphmodels.NewEmailAddress()
address := "AlexW@contoso.com"
emailAddress.SetAddress(&address) 
name := "Alex Wilber"
emailAddress.SetName(&name) 
attendee1.SetEmailAddress(emailAddress)
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendee1.SetType(&type) 

attendees := []graphmodels.Attendeeable {
	attendee,
	attendee1,
}
requestBody.SetAttendees(attendees)
location := graphmodels.NewLocation()
displayName := "Conf Room 3; Fourth Coffee; Home Office"
location.SetDisplayName(&displayName) 
locationType := graphmodels.DEFAULT_LOCATIONTYPE 
location.SetLocationType(&locationType) 
requestBody.SetLocation(location)


location := graphmodels.NewLocation()
displayName := "Conf Room 3"
location.SetDisplayName(&displayName) 
location1 := graphmodels.NewLocation()
displayName := "Fourth Coffee"
location1.SetDisplayName(&displayName) 
address := graphmodels.NewPhysicalAddress()
street := "4567 Main St"
address.SetStreet(&street) 
city := "Redmond"
address.SetCity(&city) 
state := "WA"
address.SetState(&state) 
countryOrRegion := "US"
address.SetCountryOrRegion(&countryOrRegion) 
postalCode := "32008"
address.SetPostalCode(&postalCode) 
location1.SetAddress(address)
coordinates := graphmodels.NewOutlookGeoCoordinates()
latitude := float64(47.672)
coordinates.SetLatitude(&latitude) 
longitude := float64(-102.103)
coordinates.SetLongitude(&longitude) 
location1.SetCoordinates(coordinates)
location2 := graphmodels.NewLocation()
displayName := "Home Office"
location2.SetDisplayName(&displayName) 

locations := []graphmodels.Locationable {
	location,
	location1,
	location2,
}
requestBody.SetLocations(locations)
allowNewTimeProposals := true
requestBody.SetAllowNewTimeProposals(&allowNewTimeProposals) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event event = new Event();
event.setSubject("Plan summer company picnic");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Let's kick-start this event planning!");
event.setBody(body);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2017-08-30T11:00:00");
start.setTimeZone("Pacific Standard Time");
event.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2017-08-30T12:00:00");
end.setTimeZone("Pacific Standard Time");
event.setEnd(end);
LinkedList<Attendee> attendees = new LinkedList<Attendee>();
Attendee attendee = new Attendee();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("DanaS@contoso.com");
emailAddress.setName("Dana Swope");
attendee.setEmailAddress(emailAddress);
attendee.setType(AttendeeType.Required);
attendees.add(attendee);
Attendee attendee1 = new Attendee();
EmailAddress emailAddress1 = new EmailAddress();
emailAddress1.setAddress("AlexW@contoso.com");
emailAddress1.setName("Alex Wilber");
attendee1.setEmailAddress(emailAddress1);
attendee1.setType(AttendeeType.Required);
attendees.add(attendee1);
event.setAttendees(attendees);
Location location = new Location();
location.setDisplayName("Conf Room 3; Fourth Coffee; Home Office");
location.setLocationType(LocationType.Default);
event.setLocation(location);
LinkedList<Location> locations = new LinkedList<Location>();
Location location1 = new Location();
location1.setDisplayName("Conf Room 3");
locations.add(location1);
Location location2 = new Location();
location2.setDisplayName("Fourth Coffee");
PhysicalAddress address2 = new PhysicalAddress();
address2.setStreet("4567 Main St");
address2.setCity("Redmond");
address2.setState("WA");
address2.setCountryOrRegion("US");
address2.setPostalCode("32008");
location2.setAddress(address2);
OutlookGeoCoordinates coordinates = new OutlookGeoCoordinates();
coordinates.setLatitude(47.672d);
coordinates.setLongitude(-102.103d);
location2.setCoordinates(coordinates);
locations.add(location2);
Location location3 = new Location();
location3.setDisplayName("Home Office");
locations.add(location3);
event.setLocations(locations);
event.setAllowNewTimeProposals(true);
Event result = graphClient.me().events().post(event, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = {
  subject: 'Plan summer company picnic',
  body: {
    contentType: 'HTML',
    content: 'Let\'s kick-start this event planning!'
  },
  start: {
      dateTime: '2017-08-30T11:00:00',
      timeZone: 'Pacific Standard Time'
  },
  end: {
      dateTime: '2017-08-30T12:00:00',
      timeZone: 'Pacific Standard Time'
  },
  attendees: [
    {
      emailAddress: {
        address: 'DanaS@contoso.com',
        name: 'Dana Swope'
      },
      type: 'Required'
    },
    {
      emailAddress: {
        address: 'AlexW@contoso.com',
        name: 'Alex Wilber'
      },
      type: 'Required'
    }
  ],
  location: {
    displayName: 'Conf Room 3; Fourth Coffee; Home Office',
    locationType: 'Default'
  },
  locations: [
    {
      displayName: 'Conf Room 3'
    },
    {
      displayName: 'Fourth Coffee',
      address: {
        street: '4567 Main St',
        city: 'Redmond',
        state: 'WA',
        countryOrRegion: 'US',
        postalCode: '32008'
      },
      coordinates: {
        latitude: 47.672,
        longitude: -102.103
      }
    },
    {
      displayName: 'Home Office'
    }
  ],
  allowNewTimeProposals: true
};

await client.api('/me/events')
	.post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\EventsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Models\Event;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\Attendee;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\AttendeeType;
use Microsoft\Graph\Generated\Models\Location;
use Microsoft\Graph\Generated\Models\LocationType;
use Microsoft\Graph\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Generated\Models\OutlookGeoCoordinates;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Event();
$requestBody->setSubject('Plan summer company picnic');
$body = new ItemBody();
$body->setContentType(new BodyType('hTML'));
$body->setContent('Let\'s kick-start this event planning!');
$requestBody->setBody($body);
$start = new DateTimeTimeZone();
$start->setDateTime('2017-08-30T11:00:00');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2017-08-30T12:00:00');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$attendeesAttendee1 = new Attendee();
$attendeesAttendee1EmailAddress = new EmailAddress();
$attendeesAttendee1EmailAddress->setAddress('DanaS@contoso.com');
$attendeesAttendee1EmailAddress->setName('Dana Swope');
$attendeesAttendee1->setEmailAddress($attendeesAttendee1EmailAddress);
$attendeesAttendee1->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee1;
$attendeesAttendee2 = new Attendee();
$attendeesAttendee2EmailAddress = new EmailAddress();
$attendeesAttendee2EmailAddress->setAddress('AlexW@contoso.com');
$attendeesAttendee2EmailAddress->setName('Alex Wilber');
$attendeesAttendee2->setEmailAddress($attendeesAttendee2EmailAddress);
$attendeesAttendee2->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee2;
$requestBody->setAttendees($attendeesArray);

$location = new Location();
$location->setDisplayName('Conf Room 3; Fourth Coffee; Home Office');
$location->setLocationType(new LocationType('default'));
$requestBody->setLocation($location);
$locationsLocation1 = new Location();
$locationsLocation1->setDisplayName('Conf Room 3');
$locationsArray []= $locationsLocation1;
$locationsLocation2 = new Location();
$locationsLocation2->setDisplayName('Fourth Coffee');
$locationsLocation2Address = new PhysicalAddress();
$locationsLocation2Address->setStreet('4567 Main St');
$locationsLocation2Address->setCity('Redmond');
$locationsLocation2Address->setState('WA');
$locationsLocation2Address->setCountryOrRegion('US');
$locationsLocation2Address->setPostalCode('32008');
$locationsLocation2->setAddress($locationsLocation2Address);
$locationsLocation2Coordinates = new OutlookGeoCoordinates();
$locationsLocation2Coordinates->setLatitude(47.672);
$locationsLocation2Coordinates->setLongitude(-102.103);
$locationsLocation2->setCoordinates($locationsLocation2Coordinates);
$locationsArray []= $locationsLocation2;
$locationsLocation3 = new Location();
$locationsLocation3->setDisplayName('Home Office');
$locationsArray []= $locationsLocation3;
$requestBody->setLocations($locationsArray);

$requestBody->setAllowNewTimeProposals(true);
$requestConfiguration = new EventsRequestBuilderPostRequestConfiguration();
$headers = [
'Prefer' => 'outlook.timezone="Pacific Standard Time"',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->me()->events()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.events_request_builder import EventsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.event import Event
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.attendee import Attendee
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.attendee_type import AttendeeType
from msgraph.generated.models.location import Location
from msgraph.generated.models.location_type import LocationType
from msgraph.generated.models.physical_address import PhysicalAddress
from msgraph.generated.models.outlook_geo_coordinates import OutlookGeoCoordinates
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Event(
	subject = "Plan summer company picnic",
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Let's kick-start this event planning!",
	),
	start = DateTimeTimeZone(
		date_time = "2017-08-30T11:00:00",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2017-08-30T12:00:00",
		time_zone = "Pacific Standard Time",
	),
	attendees = [
		Attendee(
			email_address = EmailAddress(
				address = "DanaS@contoso.com",
				name = "Dana Swope",
			),
			type = AttendeeType.Required,
		),
		Attendee(
			email_address = EmailAddress(
				address = "AlexW@contoso.com",
				name = "Alex Wilber",
			),
			type = AttendeeType.Required,
		),
	],
	location = Location(
		display_name = "Conf Room 3; Fourth Coffee; Home Office",
		location_type = LocationType.Default,
	),
	locations = [
		Location(
			display_name = "Conf Room 3",
		),
		Location(
			display_name = "Fourth Coffee",
			address = PhysicalAddress(
				street = "4567 Main St",
				city = "Redmond",
				state = "WA",
				country_or_region = "US",
				postal_code = "32008",
			),
			coordinates = OutlookGeoCoordinates(
				latitude = 47.672,
				longitude = -102.103,
			),
		),
		Location(
			display_name = "Home Office",
		),
	],
	allow_new_time_proposals = True,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")


result = await graph_client.me.events.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example response shows the created event that specifies information for the 3 locations for the meeting. Because of the `Prefer: outlook.timezone="Pacific Standard Time"` request header, the **start** and **end** properties are expressed in PST. Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#users('d1a2fae9-db66-4cc9-8133-2184c77af1b8')/events/$entity",
  "@odata.etag":"W/\"y53lbKh6jkaxHzFwGhgyxgAAw5zhug==\"",
  "id":"AAMkADAGAADDdm4NAAA=",
  "createdDateTime":"2017-08-30T07:06:33.8673345Z",
  "lastModifiedDateTime":"2017-08-30T07:06:34.5079772Z",
  "changeKey":"y53lbKh6jkaxHzFwGhgyxgAAz3IKMA==",
  "categories":[

  ],
  "originalStartTimeZone":"Pacific Standard Time",
  "originalEndTimeZone":"Pacific Standard Time",
  "iCalUId":"04000000820089190544",
  "reminderMinutesBeforeStart":15,
  "isReminderOn":true,
  "hasAttachments":false,
  "hideAttendees": false,
  "subject":"Plan summer company picnic",
  "bodyPreview":"Let's kick-start this event planning!",
  "importance":"normal",
  "sensitivity":"normal",
  "isAllDay":false,
  "isCancelled":false,
  "isDraft": false,
  "isOrganizer":true,
  "responseRequested":true,
  "seriesMasterId":null,
  "showAs":"busy",
  "type":"singleInstance",
  "webLink":"https://outlook.office365.com/owa/?itemid=AAMkADAGAADDdm4NAAA%3D&exvsurl=1&path=/calendar/item",
  "onlineMeetingUrl":null,
  "isOnlineMeeting":true,
  "onlineMeetingProvider":"unknown",
  "onlineMeeting":null,
  "allowNewTimeProposals": true,
  "responseStatus":{
    "response":"organizer",
    "time":"0001-01-01T00:00:00Z"
  },
  "body":{
    "contentType":"html",
    "content":"<html>\r\n<head>\r\n</head>\r\n<body>\r\nLet's kick-start this event planning!\r\n</body>\r\n</html>\r\n"
  },
  "start":{
    "dateTime":"2017-08-30T11:00:00.0000000",
    "timeZone":"Pacific Standard Time"
  },
  "end":{
    "dateTime":"2017-08-30T12:00:00.0000000",
    "timeZone":"Pacific Standard Time"
  },
  "location":{
    "displayName":"Conf Room 3; Fourth Coffee; Home Office",
    "locationType":"default",
    "uniqueId":"Conf Room 3; Fourth Coffee; Home Office",
    "uniqueIdType":"private"
  },
  "locations":[
    {
      "displayName":"Conf Room 3",
      "locationType":"default",
      "uniqueIdType":"unknown"
    },
    {
      "displayName":"Fourth Coffee",
      "locationType":"default",
      "uniqueId":"Fourth Coffee",
      "uniqueIdType":"private",
      "address":{
        "street":"4567 Main St",
        "city":"Redmond",
        "state":"WA",
        "countryOrRegion":"US",
        "postalCode":"32008"
      },
      "coordinates":{
        "latitude":47.672,
        "longitude":-102.103
      }
    },
    {
      "displayName":"Home Office",
      "locationType":"default",
      "uniqueIdType":"unknown"
    }
  ],
  "recurrence":null,
  "attendees":[
    {
      "type":"required",
      "status":{
        "response":"none",
        "time":"0001-01-01T00:00:00Z"
      },
      "emailAddress":{
        "name":"Dana Swope",
        "address":"DanaS@contoso.com"
      }
    },
    {
      "type":"required",
      "status":{
        "response":"none",
        "time":"0001-01-01T00:00:00Z"
      },
      "emailAddress":{
        "name":"Alex Wilber",
        "address":"AlexW@contoso.com"
      }
    }
  ],
  "organizer":{
    "emailAddress":{
      "name":"Adele Vance",
      "address":"AdeleV@contoso.com"
    }
  }
}
```

### Example 3: Create a recurring event

#### Request

The third example shows how to create a recurring event that occurs once a week. The event occurs from 12:00pm to 2:00pm, every Monday starting September 4, 2017, through the end of the year.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/me/events
Content-type: application/json

{
  "subject": "Let's go for lunch",
  "body": {
    "contentType": "HTML",
    "content": "Does noon time work for you?"
  },
  "start": {
      "dateTime": "2017-09-04T12:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2017-09-04T14:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "recurrence": {
    "pattern": {
      "type": "weekly",
      "interval": 1,
      "daysOfWeek": [ "Monday" ]
    },
    "range": {
      "type": "endDate",
      "startDate": "2017-09-04",
      "endDate": "2017-12-31"
    }
  },
  "location":{
      "displayName":"Harry's Bar"
  },
  "attendees": [
    {
      "emailAddress": {
        "address":"AdeleV@contoso.com",
        "name": "Adele Vance"
      },
      "type": "required"
    }
  ],
  "allowNewTimeProposals": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Event
{
	Subject = "Let's go for lunch",
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Does noon time work for you?",
	},
	Start = new DateTimeTimeZone
	{
		DateTime = "2017-09-04T12:00:00",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2017-09-04T14:00:00",
		TimeZone = "Pacific Standard Time",
	},
	Recurrence = new PatternedRecurrence
	{
		Pattern = new RecurrencePattern
		{
			Type = RecurrencePatternType.Weekly,
			Interval = 1,
			DaysOfWeek = new List<DayOfWeekObject?>
			{
				DayOfWeekObject.Monday,
			},
		},
		Range = new RecurrenceRange
		{
			Type = RecurrenceRangeType.EndDate,
			StartDate = new Date(DateTime.Parse("2017-09-04")),
			EndDate = new Date(DateTime.Parse("2017-12-31")),
		},
	},
	Location = new Location
	{
		DisplayName = "Harry's Bar",
	},
	Attendees = new List<Attendee>
	{
		new Attendee
		{
			EmailAddress = new EmailAddress
			{
				Address = "AdeleV@contoso.com",
				Name = "Adele Vance",
			},
			Type = AttendeeType.Required,
		},
	},
	AllowNewTimeProposals = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events.PostAsync(requestBody);
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
subject := "Let's go for lunch"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Does noon time work for you?"
body.SetContent(&content) 
requestBody.SetBody(body)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-09-04T12:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-09-04T14:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
requestBody.SetEnd(end)
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.WEEKLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(1)
pattern.SetInterval(&interval) 
daysOfWeek := []graphmodels.DayOfWeekable {
	dayOfWeek := graphmodels.MONDAY_DAYOFWEEK 
	pattern.SetDayOfWeek(&dayOfWeek)
}
pattern.SetDaysOfWeek(daysOfWeek)
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.ENDDATE_RECURRENCERANGETYPE 
range.SetType(&type) 
startDate := 2017-09-04
range.SetStartDate(&startDate) 
endDate := 2017-12-31
range.SetEndDate(&endDate) 
recurrence.SetRange(range)
requestBody.SetRecurrence(recurrence)
location := graphmodels.NewLocation()
displayName := "Harry's Bar"
location.SetDisplayName(&displayName) 
requestBody.SetLocation(location)


attendee := graphmodels.NewAttendee()
emailAddress := graphmodels.NewEmailAddress()
address := "AdeleV@contoso.com"
emailAddress.SetAddress(&address) 
name := "Adele Vance"
emailAddress.SetName(&name) 
attendee.SetEmailAddress(emailAddress)
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendee.SetType(&type) 

attendees := []graphmodels.Attendeeable {
	attendee,
}
requestBody.SetAttendees(attendees)
allowNewTimeProposals := true
requestBody.SetAllowNewTimeProposals(&allowNewTimeProposals) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event event = new Event();
event.setSubject("Let's go for lunch");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Does noon time work for you?");
event.setBody(body);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2017-09-04T12:00:00");
start.setTimeZone("Pacific Standard Time");
event.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2017-09-04T14:00:00");
end.setTimeZone("Pacific Standard Time");
event.setEnd(end);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.Weekly);
pattern.setInterval(1);
LinkedList<DayOfWeek> daysOfWeek = new LinkedList<DayOfWeek>();
daysOfWeek.add(DayOfWeek.Monday);
pattern.setDaysOfWeek(daysOfWeek);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.EndDate);
LocalDate startDate = LocalDate.parse("2017-09-04");
range.setStartDate(startDate);
LocalDate endDate = LocalDate.parse("2017-12-31");
range.setEndDate(endDate);
recurrence.setRange(range);
event.setRecurrence(recurrence);
Location location = new Location();
location.setDisplayName("Harry's Bar");
event.setLocation(location);
LinkedList<Attendee> attendees = new LinkedList<Attendee>();
Attendee attendee = new Attendee();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("AdeleV@contoso.com");
emailAddress.setName("Adele Vance");
attendee.setEmailAddress(emailAddress);
attendee.setType(AttendeeType.Required);
attendees.add(attendee);
event.setAttendees(attendees);
event.setAllowNewTimeProposals(true);
Event result = graphClient.me().events().post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = {
  subject: 'Let\'s go for lunch',
  body: {
    contentType: 'HTML',
    content: 'Does noon time work for you?'
  },
  start: {
      dateTime: '2017-09-04T12:00:00',
      timeZone: 'Pacific Standard Time'
  },
  end: {
      dateTime: '2017-09-04T14:00:00',
      timeZone: 'Pacific Standard Time'
  },
  recurrence: {
    pattern: {
      type: 'weekly',
      interval: 1,
      daysOfWeek: [ 'Monday' ]
    },
    range: {
      type: 'endDate',
      startDate: '2017-09-04',
      endDate: '2017-12-31'
    }
  },
  location: {
      displayName: 'Harry\'s Bar'
  },
  attendees: [
    {
      emailAddress: {
        address: 'AdeleV@contoso.com',
        name: 'Adele Vance'
      },
      type: 'required'
    }
  ],
  allowNewTimeProposals: true
};

await client.api('/me/events')
	.post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Event;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\DayOfWeek;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;
use Microsoft\Graph\Generated\Models\Location;
use Microsoft\Graph\Generated\Models\Attendee;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\AttendeeType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Event();
$requestBody->setSubject('Let\'s go for lunch');
$body = new ItemBody();
$body->setContentType(new BodyType('hTML'));
$body->setContent('Does noon time work for you?');
$requestBody->setBody($body);
$start = new DateTimeTimeZone();
$start->setDateTime('2017-09-04T12:00:00');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2017-09-04T14:00:00');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$recurrence = new PatternedRecurrence();
$recurrencePattern = new RecurrencePattern();
$recurrencePattern->setType(new RecurrencePatternType('weekly'));
$recurrencePattern->setInterval(1);
$recurrencePattern->setDaysOfWeek([new DayOfWeek('monday'),	]);
$recurrence->setPattern($recurrencePattern);
$recurrenceRange = new RecurrenceRange();
$recurrenceRange->setType(new RecurrenceRangeType('endDate'));
$recurrenceRange->setStartDate(new Date('2017-09-04'));
$recurrenceRange->setEndDate(new Date('2017-12-31'));
$recurrence->setRange($recurrenceRange);
$requestBody->setRecurrence($recurrence);
$location = new Location();
$location->setDisplayName('Harry\'s Bar');
$requestBody->setLocation($location);
$attendeesAttendee1 = new Attendee();
$attendeesAttendee1EmailAddress = new EmailAddress();
$attendeesAttendee1EmailAddress->setAddress('AdeleV@contoso.com');
$attendeesAttendee1EmailAddress->setName('Adele Vance');
$attendeesAttendee1->setEmailAddress($attendeesAttendee1EmailAddress);
$attendeesAttendee1->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee1;
$requestBody->setAttendees($attendeesArray);

$requestBody->setAllowNewTimeProposals(true);

$result = $graphServiceClient->me()->events()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	subject = "Let's go for lunch"
	body = @{
		contentType = "HTML"
		content = "Does noon time work for you?"
	}
	start = @{
		dateTime = "2017-09-04T12:00:00"
		timeZone = "Pacific Standard Time"
	}
	end = @{
		dateTime = "2017-09-04T14:00:00"
		timeZone = "Pacific Standard Time"
	}
	recurrence = @{
		pattern = @{
			type = "weekly"
			interval = 1
			daysOfWeek = @(
			"Monday"
		)
	}
	range = @{
		type = "endDate"
		startDate = "2017-09-04"
		endDate = "2017-12-31"
	}
}
location = @{
	displayName = "Harry's Bar"
}
attendees = @(
	@{
		emailAddress = @{
			address = "AdeleV@contoso.com"
			name = "Adele Vance"
		}
		type = "required"
	}
)
allowNewTimeProposals = $true
}

# A UPN can also be used as -UserId.
New-MgUserEvent -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.event import Event
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.day_of_week import DayOfWeek
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
from msgraph.generated.models.location import Location
from msgraph.generated.models.attendee import Attendee
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.attendee_type import AttendeeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Event(
	subject = "Let's go for lunch",
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Does noon time work for you?",
	),
	start = DateTimeTimeZone(
		date_time = "2017-09-04T12:00:00",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2017-09-04T14:00:00",
		time_zone = "Pacific Standard Time",
	),
	recurrence = PatternedRecurrence(
		pattern = RecurrencePattern(
			type = RecurrencePatternType.Weekly,
			interval = 1,
			days_of_week = [
				DayOfWeek.Monday,
			],
		),
		range = RecurrenceRange(
			type = RecurrenceRangeType.EndDate,
			start_date = "2017-09-04",
			end_date = "2017-12-31",
		),
	),
	location = Location(
		display_name = "Harry's Bar",
	),
	attendees = [
		Attendee(
			email_address = EmailAddress(
				address = "AdeleV@contoso.com",
				name = "Adele Vance",
			),
			type = AttendeeType.Required,
		),
	],
	allow_new_time_proposals = True,
)

result = await graph_client.me.events.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object.

#### Response

The following example shows the response. Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#users('919717da-0460-4cca-a6be-d25382429896')/events/$entity",
    "@odata.etag":"W/\"+T8RDneHMkKe2BGYEaQZ4wAA5a9Acw==\"",
    "id":"AAMkADQwMD",
    "createdDateTime":"2017-10-07T04:59:12.9698856Z",
    "lastModifiedDateTime":"2017-10-07T04:59:13.8136423Z",
    "changeKey":"+T8RDneHMkKe2BGYEaQZ4wAA5a9Acw==",
    "categories":[

    ],
    "originalStartTimeZone":"Pacific Standard Time",
    "originalEndTimeZone":"Pacific Standard Time",
    "iCalUId":"040000008200E00074C5B7101A82E0080000000028CEBE04293FD3010000000000000000100000009F85AB8AF8ED4D4FAC777FA89954BDB7",
    "reminderMinutesBeforeStart":15,
    "isReminderOn":true,
    "hasAttachments":false,
    "hideAttendees": false,
    "subject":"Let's go for lunch",
    "bodyPreview":"Does late morning work for you?",
    "importance":"normal",
    "sensitivity":"normal",
    "isAllDay":false,
    "isCancelled":false,
    "isDraft": false,
    "isOrganizer":true,
    "responseRequested":true,
    "seriesMasterId":null,
    "showAs":"busy",
    "type":"seriesMaster",
    "webLink":"https://outlook.office365.com/owa/?itemid=AAMkADQwMD&exvsurl=1&path=/calendar/item",
    "onlineMeetingUrl":null,
    "isOnlineMeeting":true,
    "onlineMeetingProvider":"unknown",
    "onlineMeeting":null,
    "allowNewTimeProposals": true,
    "responseStatus":{
        "response":"organizer",
        "time":"0001-01-01T00:00:00Z"
    },
    "body":{
        "contentType":"html",
        "content":"<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nDoes late morning work for you?\r\n</body>\r\n</html>\r\n"
    },
    "start":{
        "dateTime":"2017-09-04T12:00:00.0000000",
        "timeZone":"Pacific Standard Time"
    },
    "end":{
        "dateTime":"2017-09-04T14:00:00.0000000",
        "timeZone":"Pacific Standard Time"
    },
    "location":{
        "displayName":"Harry's Bar",
        "locationType":"default",
        "uniqueId":"Harry's Bar",
        "uniqueIdType":"private"
    },
    "locations":[
        {
            "displayName":"Harry's Bar",
            "locationType":"default",
            "uniqueIdType":"unknown"
        }
    ],
    "recurrence":{
        "pattern":{
            "type":"weekly",
            "interval":1,
            "month":0,
            "dayOfMonth":0,
            "daysOfWeek":[
                "monday"
            ],
            "firstDayOfWeek":"sunday",
            "index":"first"
        },
        "range":{
            "type":"endDate",
            "startDate":"2017-09-04",
            "endDate":"2017-12-31",
            "recurrenceTimeZone":"Pacific Standard Time",
            "numberOfOccurrences":0
        }
    },
    "attendees":[
        {
            "type":"required",
            "status":{
                "response":"none",
                "time":"0001-01-01T00:00:00Z"
            },
            "emailAddress":{
                "name":"Adele Vance",
                "address":"AdeleV@contoso.com"
            }
        }
    ],
    "organizer":{
        "emailAddress":{
            "name":"Alex Wilber",
            "address":"AlexW@contoso.com"
        }
    },
}
```

### Example 4: Create and enable an event as an online meeting

#### Request

The following example shows a request which creates an event and enables it as an online meeting. It uses the `Prefer: outlook.timezone` request header to specify the time zone for the **start** and **end** times in the response.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/me/events
Prefer: outlook.timezone="Pacific Standard Time"
Content-type: application/json

{
  "subject": "Let's go for lunch",
  "body": {
    "contentType": "HTML",
    "content": "Does noon work for you?"
  },
  "start": {
      "dateTime": "2017-04-15T12:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2017-04-15T14:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "location":{
      "displayName":"Harry's Bar"
  },
  "attendees": [
    {
      "emailAddress": {
        "address":"samanthab@contoso.com",
        "name": "Samantha Booth"
      },
      "type": "required"
    }
  ],
  "allowNewTimeProposals": true,
  "isOnlineMeeting": true,
  "onlineMeetingProvider": "teamsForBusiness"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Event
{
	Subject = "Let's go for lunch",
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Does noon work for you?",
	},
	Start = new DateTimeTimeZone
	{
		DateTime = "2017-04-15T12:00:00",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2017-04-15T14:00:00",
		TimeZone = "Pacific Standard Time",
	},
	Location = new Location
	{
		DisplayName = "Harry's Bar",
	},
	Attendees = new List<Attendee>
	{
		new Attendee
		{
			EmailAddress = new EmailAddress
			{
				Address = "samanthab@contoso.com",
				Name = "Samantha Booth",
			},
			Type = AttendeeType.Required,
		},
	},
	AllowNewTimeProposals = true,
	IsOnlineMeeting = true,
	OnlineMeetingProvider = OnlineMeetingProviderType.TeamsForBusiness,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")

configuration := &graphusers.ItemEventsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewEvent()
subject := "Let's go for lunch"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Does noon work for you?"
body.SetContent(&content) 
requestBody.SetBody(body)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-04-15T12:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2017-04-15T14:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
requestBody.SetEnd(end)
location := graphmodels.NewLocation()
displayName := "Harry's Bar"
location.SetDisplayName(&displayName) 
requestBody.SetLocation(location)


attendee := graphmodels.NewAttendee()
emailAddress := graphmodels.NewEmailAddress()
address := "samanthab@contoso.com"
emailAddress.SetAddress(&address) 
name := "Samantha Booth"
emailAddress.SetName(&name) 
attendee.SetEmailAddress(emailAddress)
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendee.SetType(&type) 

attendees := []graphmodels.Attendeeable {
	attendee,
}
requestBody.SetAttendees(attendees)
allowNewTimeProposals := true
requestBody.SetAllowNewTimeProposals(&allowNewTimeProposals) 
isOnlineMeeting := true
requestBody.SetIsOnlineMeeting(&isOnlineMeeting) 
onlineMeetingProvider := graphmodels.TEAMSFORBUSINESS_ONLINEMEETINGPROVIDERTYPE 
requestBody.SetOnlineMeetingProvider(&onlineMeetingProvider) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event event = new Event();
event.setSubject("Let's go for lunch");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Does noon work for you?");
event.setBody(body);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2017-04-15T12:00:00");
start.setTimeZone("Pacific Standard Time");
event.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2017-04-15T14:00:00");
end.setTimeZone("Pacific Standard Time");
event.setEnd(end);
Location location = new Location();
location.setDisplayName("Harry's Bar");
event.setLocation(location);
LinkedList<Attendee> attendees = new LinkedList<Attendee>();
Attendee attendee = new Attendee();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("samanthab@contoso.com");
emailAddress.setName("Samantha Booth");
attendee.setEmailAddress(emailAddress);
attendee.setType(AttendeeType.Required);
attendees.add(attendee);
event.setAttendees(attendees);
event.setAllowNewTimeProposals(true);
event.setIsOnlineMeeting(true);
event.setOnlineMeetingProvider(OnlineMeetingProviderType.TeamsForBusiness);
Event result = graphClient.me().events().post(event, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = {
  subject: 'Let\'s go for lunch',
  body: {
    contentType: 'HTML',
    content: 'Does noon work for you?'
  },
  start: {
      dateTime: '2017-04-15T12:00:00',
      timeZone: 'Pacific Standard Time'
  },
  end: {
      dateTime: '2017-04-15T14:00:00',
      timeZone: 'Pacific Standard Time'
  },
  location: {
      displayName: 'Harry\'s Bar'
  },
  attendees: [
    {
      emailAddress: {
        address: 'samanthab@contoso.com',
        name: 'Samantha Booth'
      },
      type: 'required'
    }
  ],
  allowNewTimeProposals: true,
  isOnlineMeeting: true,
  onlineMeetingProvider: 'teamsForBusiness'
};

await client.api('/me/events')
	.post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\EventsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Models\Event;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\Location;
use Microsoft\Graph\Generated\Models\Attendee;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\AttendeeType;
use Microsoft\Graph\Generated\Models\OnlineMeetingProviderType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Event();
$requestBody->setSubject('Let\'s go for lunch');
$body = new ItemBody();
$body->setContentType(new BodyType('hTML'));
$body->setContent('Does noon work for you?');
$requestBody->setBody($body);
$start = new DateTimeTimeZone();
$start->setDateTime('2017-04-15T12:00:00');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2017-04-15T14:00:00');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$location = new Location();
$location->setDisplayName('Harry\'s Bar');
$requestBody->setLocation($location);
$attendeesAttendee1 = new Attendee();
$attendeesAttendee1EmailAddress = new EmailAddress();
$attendeesAttendee1EmailAddress->setAddress('samanthab@contoso.com');
$attendeesAttendee1EmailAddress->setName('Samantha Booth');
$attendeesAttendee1->setEmailAddress($attendeesAttendee1EmailAddress);
$attendeesAttendee1->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee1;
$requestBody->setAttendees($attendeesArray);

$requestBody->setAllowNewTimeProposals(true);
$requestBody->setIsOnlineMeeting(true);
$requestBody->setOnlineMeetingProvider(new OnlineMeetingProviderType('teamsForBusiness'));
$requestConfiguration = new EventsRequestBuilderPostRequestConfiguration();
$headers = [
	'Prefer' => 'outlook.timezone="Pacific Standard Time"',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->me()->events()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	subject = "Let's go for lunch"
	body = @{
		contentType = "HTML"
		content = "Does noon work for you?"
	}
	start = @{
		dateTime = "2017-04-15T12:00:00"
		timeZone = "Pacific Standard Time"
	}
	end = @{
		dateTime = "2017-04-15T14:00:00"
		timeZone = "Pacific Standard Time"
	}
	location = @{
		displayName = "Harry's Bar"
	}
	attendees = @(
		@{
			emailAddress = @{
				address = "samanthab@contoso.com"
				name = "Samantha Booth"
			}
			type = "required"
		}
	)
	allowNewTimeProposals = $true
	isOnlineMeeting = $true
	onlineMeetingProvider = "teamsForBusiness"
}

# A UPN can also be used as -UserId.
New-MgUserEvent -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.events_request_builder import EventsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.event import Event
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.location import Location
from msgraph.generated.models.attendee import Attendee
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.attendee_type import AttendeeType
from msgraph.generated.models.online_meeting_provider_type import OnlineMeetingProviderType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Event(
	subject = "Let's go for lunch",
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Does noon work for you?",
	),
	start = DateTimeTimeZone(
		date_time = "2017-04-15T12:00:00",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2017-04-15T14:00:00",
		time_zone = "Pacific Standard Time",
	),
	location = Location(
		display_name = "Harry's Bar",
	),
	attendees = [
		Attendee(
			email_address = EmailAddress(
				address = "samanthab@contoso.com",
				name = "Samantha Booth",
			),
			type = AttendeeType.Required,
		),
	],
	allow_new_time_proposals = True,
	is_online_meeting = True,
	online_meeting_provider = OnlineMeetingProviderType.TeamsForBusiness,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")


result = await graph_client.me.events.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object.

#### Response

Here is an example of the response, which shows the **start** and **end** properties use the time zone specified in the `Prefer: outlook.timezone` header. Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#users('cd209b0b-3f83-4c35-82d2-d88a61820480')/events/$entity",
    "@odata.etag":"W/\"ZlnW4RIAV06KYYwlrfNZvQAALfZeRQ==\"",
    "id":"AAMkAGI1AAAt8AHjAAA=",
    "createdDateTime":"2017-04-15T03:00:50.7579581Z",
    "lastModifiedDateTime":"2017-04-15T03:00:51.245372Z",
    "changeKey":"ZlnW4RIAV06KYYwlrfNZvQAALfZeRQ==",
    "categories":[
    ],
    "originalStartTimeZone":"Pacific Standard Time",
    "originalEndTimeZone":"Pacific Standard Time",
    "iCalUId":"040000008200E00074C5B7101A82E00800000000DA2B357D94B5D201000000000000000010000000EC4597557F0CB34EA4CC2887EA7B17C3",
    "reminderMinutesBeforeStart":15,
    "isReminderOn":true,
    "hasAttachments":false,
    "hideAttendees": false,
    "subject":"Let's go brunch",
    "bodyPreview":"Does noon work for you?",
    "importance":"normal",
    "sensitivity":"normal",
    "isAllDay":false,
    "isCancelled":false,
    "isDraft": false,
    "isOrganizer":true,
    "responseRequested":true,
    "seriesMasterId":null,
    "showAs":"busy",
    "type":"singleInstance",
    "webLink":"https://outlook.office365.com/owa/?itemid=AAMkAGI1AAAt9AHjAAA%3D&exvsurl=1&path=/calendar/item",
    "onlineMeetingUrl":null,
    "isOnlineMeeting": true,
    "onlineMeetingProvider": "teamsForBusiness",
    "allowNewTimeProposals": true,
    "responseStatus":{
        "response":"organizer",
        "time":"0001-01-01T00:00:00Z"
    },
    "body":{
        "contentType":"html",
        "content":"<html><head></head><body>Does late morning work for you?</body></html>"
    },
    "start":{
        "dateTime":"2017-04-15T11:00:00.0000000",
        "timeZone":"Pacific Standard Time"
    },
    "end":{
        "dateTime":"2017-04-15T12:00:00.0000000",
        "timeZone":"Pacific Standard Time"
    },
    "location": {
        "displayName": "Harry's Bar",
        "locationType": "default",
        "uniqueId": "Harry's Bar",
        "uniqueIdType": "private"
    },
    "locations": [
        {
            "displayName": "Harry's Bar",
            "locationType": "default",
            "uniqueIdType": "unknown"
        }
    ],
    "recurrence":null,
    "attendees":[
        {
            "type":"required",
            "status":{
                "response":"none",
                "time":"0001-01-01T00:00:00Z"
            },
            "emailAddress":{
                "name":"Samantha Booth",
                "address":"samanthab@contoso.com"
            }
        }
    ],
    "organizer":{
        "emailAddress":{
            "name":"Dana Swope",
            "address":"danas@contoso.com"
        }
    },
    "onlineMeeting": {
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_NzIyNzhlMGEtM2YyZC00ZmY0LTlhNzUtZmZjNWFmZGNlNzE2%40thread.v2/0?context=%7b%22Tid%22%3a%2272f988bf-86f1-41af-91ab-2d7cd011db47%22%2c%22Oid%22%3a%22bc55b173-cff6-457d-b7a1-64bda7d7581a%22%7d",
        "conferenceId": "177513992",
        "tollNumber": "+1 425 555 0123"
    }
}
```

## Related content

- [Schedule repeating appointments as recurring events in Outlook](https://learn.microsoft.com/en-us/graph/outlook-schedule-recurring-events)
- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
