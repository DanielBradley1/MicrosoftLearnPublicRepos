<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-findmeetingtimes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# user: findMeetingTimes

Namespace: microsoft.graph

Suggest meeting times and locations based on organizer and attendee availability, and time or location constraints specified as parameters.

If **findMeetingTimes** cannot return any meeting suggestions, the response would indicate a reason in the **emptySuggestionsReason** property. Based on this value, you can better adjust the parameters and call **findMeetingTimes** again.

The algorithm used to suggest meeting times and locations undergoes fine-tuning from time to time. In scenarios like test environments where the input parameters and calendar data remain static, expect that the suggested results may differ over time.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.Read.Shared | Calendars.ReadWrite.Shared |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/findMeetingTimes
POST /users/{id|userPrincipalName}/findMeetingTimes
```

## Request headers

| Name | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer: outlook.timezone | A string representing a specific time zone for the response, for example, "Pacific Standard Time". Optional. UTC is used if this header is not specified. |

## Request body

All the supported parameters are listed below. Depending on your scenario, specify a JSON object for each of the necessary parameters in the request body.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| attendees | [attendeeBase](https://learn.microsoft.com/en-us/graph/api/resources/attendeebase?view=graph-rest-1.0) collection | A collection of attendees or resources for the meeting. Since findMeetingTimes assumes that any attendee who is a person is always required, specify `required` for a person and `resource` for a resource in the corresponding **type** property. An empty collection causes **findMeetingTimes** to look for free time slots for only the organizer. Optional. |
| isOrganizerOptional | Edm.Boolean | Specify `True` if the organizer doesn't necessarily have to attend. The default is `false`. Optional. |
| locationConstraint | [locationConstraint](https://learn.microsoft.com/en-us/graph/api/resources/locationconstraint?view=graph-rest-1.0) | The organizer's requirements about the meeting location, such as whether a suggestion for a meeting location is required, or there are specific locations only where the meeting can take place. Optional. |
| maxCandidates | Edm.Int32 | The maximum number of meeting time suggestions to be returned. Optional. |
| meetingDuration | Edm.Duration | The length of the meeting, denoted in [ISO8601](https://www.iso.org/iso/iso8601) format. For example, 1 hour is denoted as 'PT1H', where 'P' is the duration designator, 'T' is the time designator, and 'H' is the hour designator. Use M to indicate minutes for the duration; for example, 2 hours and 30 minutes would be 'PT2H30M'. If no meeting duration is specified, **findMeetingTimes** uses the default of 30 minutes. Optional. |
| minimumAttendeePercentage | Edm.Double | The minimum required [confidence](#the-confidence-of-a-meeting-suggestion) for a time slot to be returned in the response. It is a % value ranging from 0 to 100. Optional. |
| returnSuggestionReasons | Edm.Boolean | Specify `True` to return a reason for each meeting suggestion in the **suggestionReason** property. The default is `false` to not return that property. Optional. |
| timeConstraint | [timeConstraint](https://learn.microsoft.com/en-us/graph/api/resources/timeconstraint?view=graph-rest-1.0) | Any time restrictions for a meeting, which can include the nature of the meeting \(**activityDomain** property\) and possible meeting time periods \(**timeSlots** property\). **findMeetingTimes** assumes **activityDomain** as `work` if you don't specify this parameter. Optional. |

The following table describes the **activityDomain** restrictions you can further specify in the **timeConstraint** parameter.

| activityDomain value | Suggestions for meeting times |
| :--- | :--- |
| work | Suggestions are within the user's work hours which are defined in the user’s calendar configuration and can be customized by the user or administrator. The default work hours are Monday to Friday, 8am to 5pm in the time zone set for the mailbox. This is the default value if no **activityDomain** is specified. |
| personal | Suggestions are within the user's work hours, and Saturday and Sunday. The default is Monday to Sunday, 8am to 5pm, in the time zone setting for the mailbox. |
| unrestricted | Suggestions can be from all hours of a day, all days of a week. |
| unknown | Don't use this value as it will be deprecated in the future. Currently behaves the same as `work`. Change any existing code to use `work`, `personal` or `unrestricted` as appropriate. |

Based on the specified parameters,**findMeetingTimes** checks the free/busy status in the primary calendars of the organizer and attendees. The action calculates the best possible meeting times, and returns any meeting suggestions.

## Response

If successful, this method returns `200 OK` response code and a [meetingTimeSuggestionsResult](https://learn.microsoft.com/en-us/graph/api/resources/meetingtimesuggestionsresult?view=graph-rest-1.0) in the response body.

A **meetingTimeSuggestionsResult** includes a collection of meeting suggestions and an **emptySuggestionsReason** property. Each suggestion is defined as a [meetingTimeSuggestion](https://learn.microsoft.com/en-us/graph/api/resources/meetingtimesuggestion?view=graph-rest-1.0), with attendees having on the average a confidence level of 50% to attend, or a specific % that you have specified in the **minimumAttendeePercentage** parameter.

By default, each meeting time suggestion is returned in UTC.

If **findMeetingTimes** cannot return any meeting suggestions, the response would indicate a reason in the **emptySuggestionsReason** property. Based on this value, you can better adjust the parameters and call **findMeetingTimes** again.

### The confidence of a meeting suggestion

The **confidence** property of a **meetingTimeSuggestion** ranges from 0% to 100%, and represents the chance that all the attendees attend the meeting, based on each of their individual free/busy status:

- For each attendee, a free status for a specified meeting time period corresponds to 100% chance of attendance, unknown status 49%, and busy status 0%.
- The confidence of a meeting time suggestion is computed by averaging the chance of attendance over all the attendees specified for that meeting.
- You can use the **minimumAttendeePercentage** optional parameter for **findMeetingTimes** to specify only meeting time suggestions of at least certain confidence level should be returned. For example, you can specify a **minimumAttendeePercentage** of 80% if you want only suggestions that have an 80% chance or more that all the attendees are attending. If you don't specify **minimumAttendeePercentage**, **findMeetingTimes** assumes a value of 50%.
- If there are multiple meeting time suggestions, the **findMeetingTimes** action first orders the suggestions by their computed confidence value from high to low. If there are suggestions with the same confidence, the action then orders these suggestions chronologically.

As an example, if a meeting time suggestion involves 3 attendees with the following free/busy status:

| **Attendee** | **Free/busy status** | **% Chance of attendance** |
| :--- | :--- | :--- |
| Dana | Free | 100% |
| John | Unknown | 49% |
| Samantha | Busy | 0% |

Then the confidence of the meeting time suggestion, which is the average chance of attendance, is \(100% + 49% + 0%\)/3 = 49.66%.

If you specify a **minimumAttendeePercentage** of 80% in a **findMeetingTimes** operation, because 49.66% < 80%, the operation will not suggest this time in the response.

## Example

The following example shows how to find time to meet at a pre-determined location, and request a reason for each suggestion, by specifying the following parameters in the request body:

- **attendees**
- **locationConstraint**
- **timeConstraint**
- **isOrganizerOptional**
- **meetingDuration**
- **returnSuggestionReasons**
- **minimumAttendeePercentage**

By setting the **returnSuggestionReasons** parameter, you also get an explanation in the **suggestionReason** property for each suggestion, if **findMeetingTimes** returns any suggestion.

Notice that the request specifies time in the PST time zone. By default, the response returns meeting time suggestions in UTC. You can use the `Prefer: outlook.timezone` request header to specify PST as well for the time values in the response.

### Request

Here is the example request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/findMeetingTimes
Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json

{
  "attendees": [
    {
      "type": "required",
      "emailAddress": {
        "name": "Alex Wilbur",
        "address": "alexw@contoso.com"
      }
    }
  ],
  "locationConstraint": {
    "isRequired": false,
    "suggestLocation": false,
    "locations": [
      {
        "resolveAvailability": false,
        "displayName": "Conf room Hood"
      }
    ]
  },
  "timeConstraint": {
    "activityDomain":"work",
    "timeSlots": [
      {
        "start": {
          "dateTime": "2019-04-16T09:00:00",
          "timeZone": "Pacific Standard Time"
        },
        "end": {
          "dateTime": "2019-04-18T17:00:00",
          "timeZone": "Pacific Standard Time"
        }
      }
    ]
  },
  "isOrganizerOptional": "false",
  "meetingDuration": "PT1H",
  "returnSuggestionReasons": "true",
  "minimumAttendeePercentage": 100
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.FindMeetingTimes;
using Microsoft.Graph.Models;

var requestBody = new FindMeetingTimesPostRequestBody
{
	Attendees = new List<AttendeeBase>
	{
		new AttendeeBase
		{
			Type = AttendeeType.Required,
			EmailAddress = new EmailAddress
			{
				Name = "Alex Wilbur",
				Address = "alexw@contoso.com",
			},
		},
	},
	LocationConstraint = new LocationConstraint
	{
		IsRequired = false,
		SuggestLocation = false,
		Locations = new List<LocationConstraintItem>
		{
			new LocationConstraintItem
			{
				ResolveAvailability = false,
				DisplayName = "Conf room Hood",
			},
		},
	},
	TimeConstraint = new TimeConstraint
	{
		ActivityDomain = ActivityDomain.Work,
		TimeSlots = new List<TimeSlot>
		{
			new TimeSlot
			{
				Start = new DateTimeTimeZone
				{
					DateTime = "2019-04-16T09:00:00",
					TimeZone = "Pacific Standard Time",
				},
				End = new DateTimeTimeZone
				{
					DateTime = "2019-04-18T17:00:00",
					TimeZone = "Pacific Standard Time",
				},
			},
		},
	},
	IsOrganizerOptional = false,
	MeetingDuration = TimeSpan.Parse("PT1H"),
	ReturnSuggestionReasons = true,
	MinimumAttendeePercentage = 100d,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.FindMeetingTimes.PostAsync(requestBody, (requestConfiguration) =>
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
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")

configuration := &graphusers.ItemFindMeetingTimesRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewItemFindMeetingTimesPostRequestBody()


attendeeBase := graphmodels.NewAttendeeBase()
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendeeBase.SetType(&type) 
emailAddress := graphmodels.NewEmailAddress()
name := "Alex Wilbur"
emailAddress.SetName(&name) 
address := "alexw@contoso.com"
emailAddress.SetAddress(&address) 
attendeeBase.SetEmailAddress(emailAddress)

attendees := []graphmodels.AttendeeBaseable {
	attendeeBase,
}
requestBody.SetAttendees(attendees)
locationConstraint := graphmodels.NewLocationConstraint()
isRequired := false
locationConstraint.SetIsRequired(&isRequired) 
suggestLocation := false
locationConstraint.SetSuggestLocation(&suggestLocation) 


locationConstraintItem := graphmodels.NewLocationConstraintItem()
resolveAvailability := false
locationConstraintItem.SetResolveAvailability(&resolveAvailability) 
displayName := "Conf room Hood"
locationConstraintItem.SetDisplayName(&displayName) 

locations := []graphmodels.LocationConstraintItemable {
	locationConstraintItem,
}
locationConstraint.SetLocations(locations)
requestBody.SetLocationConstraint(locationConstraint)
timeConstraint := graphmodels.NewTimeConstraint()
activityDomain := graphmodels.WORK_ACTIVITYDOMAIN 
timeConstraint.SetActivityDomain(&activityDomain) 


timeSlot := graphmodels.NewTimeSlot()
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-04-16T09:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
timeSlot.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-04-18T17:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
timeSlot.SetEnd(end)

timeSlots := []graphmodels.TimeSlotable {
	timeSlot,
}
timeConstraint.SetTimeSlots(timeSlots)
requestBody.SetTimeConstraint(timeConstraint)
isOrganizerOptional := false
requestBody.SetIsOrganizerOptional(&isOrganizerOptional) 
meetingDuration , err := abstractions.ParseISODuration("PT1H")
requestBody.SetMeetingDuration(&meetingDuration) 
returnSuggestionReasons := true
requestBody.SetReturnSuggestionReasons(&returnSuggestionReasons) 
minimumAttendeePercentage := float64(100)
requestBody.SetMinimumAttendeePercentage(&minimumAttendeePercentage) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
findMeetingTimes, err := graphClient.Me().FindMeetingTimes().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.findmeetingtimes.FindMeetingTimesPostRequestBody findMeetingTimesPostRequestBody = new com.microsoft.graph.users.item.findmeetingtimes.FindMeetingTimesPostRequestBody();
LinkedList<AttendeeBase> attendees = new LinkedList<AttendeeBase>();
AttendeeBase attendeeBase = new AttendeeBase();
attendeeBase.setType(AttendeeType.Required);
EmailAddress emailAddress = new EmailAddress();
emailAddress.setName("Alex Wilbur");
emailAddress.setAddress("alexw@contoso.com");
attendeeBase.setEmailAddress(emailAddress);
attendees.add(attendeeBase);
findMeetingTimesPostRequestBody.setAttendees(attendees);
LocationConstraint locationConstraint = new LocationConstraint();
locationConstraint.setIsRequired(false);
locationConstraint.setSuggestLocation(false);
LinkedList<LocationConstraintItem> locations = new LinkedList<LocationConstraintItem>();
LocationConstraintItem locationConstraintItem = new LocationConstraintItem();
locationConstraintItem.setResolveAvailability(false);
locationConstraintItem.setDisplayName("Conf room Hood");
locations.add(locationConstraintItem);
locationConstraint.setLocations(locations);
findMeetingTimesPostRequestBody.setLocationConstraint(locationConstraint);
TimeConstraint timeConstraint = new TimeConstraint();
timeConstraint.setActivityDomain(ActivityDomain.Work);
LinkedList<TimeSlot> timeSlots = new LinkedList<TimeSlot>();
TimeSlot timeSlot = new TimeSlot();
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2019-04-16T09:00:00");
start.setTimeZone("Pacific Standard Time");
timeSlot.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2019-04-18T17:00:00");
end.setTimeZone("Pacific Standard Time");
timeSlot.setEnd(end);
timeSlots.add(timeSlot);
timeConstraint.setTimeSlots(timeSlots);
findMeetingTimesPostRequestBody.setTimeConstraint(timeConstraint);
findMeetingTimesPostRequestBody.setIsOrganizerOptional(false);
PeriodAndDuration meetingDuration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
findMeetingTimesPostRequestBody.setMeetingDuration(meetingDuration);
findMeetingTimesPostRequestBody.setReturnSuggestionReasons(true);
findMeetingTimesPostRequestBody.setMinimumAttendeePercentage(100d);
var result = graphClient.me().findMeetingTimes().post(findMeetingTimesPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const meetingTimeSuggestionsResult = {
  attendees: [
    {
      type: 'required',
      emailAddress: {
        name: 'Alex Wilbur',
        address: 'alexw@contoso.com'
      }
    }
  ],
  locationConstraint: {
    isRequired: false,
    suggestLocation: false,
    locations: [
      {
        resolveAvailability: false,
        displayName: 'Conf room Hood'
      }
    ]
  },
  timeConstraint: {
    activityDomain: 'work',
    timeSlots: [
      {
        start: {
          dateTime: '2019-04-16T09:00:00',
          timeZone: 'Pacific Standard Time'
        },
        end: {
          dateTime: '2019-04-18T17:00:00',
          timeZone: 'Pacific Standard Time'
        }
      }
    ]
  },
  isOrganizerOptional: 'false',
  meetingDuration: 'PT1H',
  returnSuggestionReasons: 'true',
  minimumAttendeePercentage: 100
};

await client.api('/me/findMeetingTimes')
	.post(meetingTimeSuggestionsResult);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\FindMeetingTimes\FindMeetingTimesRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Users\Item\FindMeetingTimes\FindMeetingTimesPostRequestBody;
use Microsoft\Graph\Generated\Models\AttendeeBase;
use Microsoft\Graph\Generated\Models\AttendeeType;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\LocationConstraint;
use Microsoft\Graph\Generated\Models\LocationConstraintItem;
use Microsoft\Graph\Generated\Models\TimeConstraint;
use Microsoft\Graph\Generated\Models\ActivityDomain;
use Microsoft\Graph\Generated\Models\TimeSlot;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new FindMeetingTimesPostRequestBody();
$attendeesAttendeeBase1 = new AttendeeBase();
$attendeesAttendeeBase1->setType(new AttendeeType('required'));
$attendeesAttendeeBase1EmailAddress = new EmailAddress();
$attendeesAttendeeBase1EmailAddress->setName('Alex Wilbur');
$attendeesAttendeeBase1EmailAddress->setAddress('alexw@contoso.com');
$attendeesAttendeeBase1->setEmailAddress($attendeesAttendeeBase1EmailAddress);
$attendeesArray []= $attendeesAttendeeBase1;
$requestBody->setAttendees($attendeesArray);

$locationConstraint = new LocationConstraint();
$locationConstraint->setIsRequired(false);
$locationConstraint->setSuggestLocation(false);
$locationsLocationConstraintItem1 = new LocationConstraintItem();
$locationsLocationConstraintItem1->setResolveAvailability(false);
$locationsLocationConstraintItem1->setDisplayName('Conf room Hood');
$locationsArray []= $locationsLocationConstraintItem1;
$locationConstraint->setLocations($locationsArray);

$requestBody->setLocationConstraint($locationConstraint);
$timeConstraint = new TimeConstraint();
$timeConstraint->setActivityDomain(new ActivityDomain('work'));
$timeSlotsTimeSlot1 = new TimeSlot();
$timeSlotsTimeSlot1Start = new DateTimeTimeZone();
$timeSlotsTimeSlot1Start->setDateTime('2019-04-16T09:00:00');
$timeSlotsTimeSlot1Start->setTimeZone('Pacific Standard Time');
$timeSlotsTimeSlot1->setStart($timeSlotsTimeSlot1Start);
$timeSlotsTimeSlot1End = new DateTimeTimeZone();
$timeSlotsTimeSlot1End->setDateTime('2019-04-18T17:00:00');
$timeSlotsTimeSlot1End->setTimeZone('Pacific Standard Time');
$timeSlotsTimeSlot1->setEnd($timeSlotsTimeSlot1End);
$timeSlotsArray []= $timeSlotsTimeSlot1;
$timeConstraint->setTimeSlots($timeSlotsArray);

$requestBody->setTimeConstraint($timeConstraint);
$requestBody->setIsOrganizerOptional(false);
$requestBody->setMeetingDuration(new \DateInterval('PT1H'));
$requestBody->setReturnSuggestionReasons(true);
$requestBody->setMinimumAttendeePercentage(100);
$requestConfiguration = new FindMeetingTimesRequestBuilderPostRequestConfiguration();
$headers = [
'Prefer' => 'outlook.timezone="Pacific Standard Time"',
];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->me()->findMeetingTimes()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users.Actions

$params = @{
	attendees = @(
		@{
			type = "required"
			emailAddress = @{
				name = "Alex Wilbur"
				address = "alexw@contoso.com"
			}
		}
	)
	locationConstraint = @{
		isRequired = $false
		suggestLocation = $false
		locations = @(
			@{
				resolveAvailability = $false
				displayName = "Conf room Hood"
			}
		)
	}
	timeConstraint = @{
		activityDomain = "work"
		timeSlots = @(
			@{
				start = @{
					dateTime = "2019-04-16T09:00:00"
					timeZone = "Pacific Standard Time"
				}
				end = @{
					dateTime = "2019-04-18T17:00:00"
					timeZone = "Pacific Standard Time"
				}
			}
		)
	}
	isOrganizerOptional = "false"
	meetingDuration = "PT1H"
	returnSuggestionReasons = "true"
	minimumAttendeePercentage = 100
}

# A UPN can also be used as -UserId.
Find-MgUserMeetingTime -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.find_meeting_times.find_meeting_times_request_builder import FindMeetingTimesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.users.item.find_meeting_times.find_meeting_times_post_request_body import FindMeetingTimesPostRequestBody
from msgraph.generated.models.attendee_base import AttendeeBase
from msgraph.generated.models.attendee_type import AttendeeType
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.location_constraint import LocationConstraint
from msgraph.generated.models.location_constraint_item import LocationConstraintItem
from msgraph.generated.models.time_constraint import TimeConstraint
from msgraph.generated.models.activity_domain import ActivityDomain
from msgraph.generated.models.time_slot import TimeSlot
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = FindMeetingTimesPostRequestBody(
	attendees = [
		AttendeeBase(
			type = AttendeeType.Required,
			email_address = EmailAddress(
				name = "Alex Wilbur",
				address = "alexw@contoso.com",
			),
		),
	],
	location_constraint = LocationConstraint(
		is_required = False,
		suggest_location = False,
		locations = [
			LocationConstraintItem(
				resolve_availability = False,
				display_name = "Conf room Hood",
			),
		],
	),
	time_constraint = TimeConstraint(
		activity_domain = ActivityDomain.Work,
		time_slots = [
			TimeSlot(
				start = DateTimeTimeZone(
					date_time = "2019-04-16T09:00:00",
					time_zone = "Pacific Standard Time",
				),
				end = DateTimeTimeZone(
					date_time = "2019-04-18T17:00:00",
					time_zone = "Pacific Standard Time",
				),
			),
		],
	),
	is_organizer_optional = False,
	meeting_duration = "PT1H",
	return_suggestion_reasons = True,
	minimum_attendee_percentage = 100,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")


result = await graph_client.me.find_meeting_times.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Here is an example response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json
Preference-Applied: outlook.timezone="Pacific Standard Time"

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.meetingTimeSuggestionsResult",
    "emptySuggestionsReason": "",
    "meetingTimeSuggestions": [
        {
            "confidence": 100,
            "order": 1,
            "organizerAvailability": "free",
            "suggestionReason": "Suggested because it is one of the nearest times when all attendees are available.",
            "attendeeAvailability": [
                {
                    "availability": "free",
                    "attendee": {
                        "emailAddress": {
                            "address": "alexw@contoso.com"
                        }
                    }
                }
            ],
            "locations": [
                {
                    "displayName": "Conf room Hood"
                }
            ],
            "meetingTimeSlot": {
                "start": {
                    "dateTime": "2019-04-18T16:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                },
                "end": {
                    "dateTime": "2019-04-18T17:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                }
            }
        },
        {
            "confidence": 100,
            "order": 2,
            "organizerAvailability": "free",
            "suggestionReason": "Suggested because it is one of the nearest times when all attendees are available.",
            "attendeeAvailability": [
                {
                    "availability": "free",
                    "attendee": {
                        "emailAddress": {
                            "address": "alexw@contoso.com"
                        }
                    }
                }
            ],
            "locations": [
                {
                    "displayName": "Conf room Hood"
                }
            ],
            "meetingTimeSlot": {
                "start": {
                    "dateTime": "2019-04-18T08:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                },
                "end": {
                    "dateTime": "2019-04-18T09:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                }
            }
        },
        {
            "confidence": 100,
            "order": 3,
            "organizerAvailability": "tentative",
            "suggestionReason": "Suggested because it is one of the nearest times when all attendees are available.",
            "attendeeAvailability": [
                {
                    "availability": "free",
                    "attendee": {
                        "emailAddress": {
                            "address": "alexw@contoso.com"
                        }
                    }
                }
            ],
            "locations": [
                {
                    "displayName": "Conf room Hood"
                }
            ],
            "meetingTimeSlot": {
                "start": {
                    "dateTime": "2019-04-18T15:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                },
                "end": {
                    "dateTime": "2019-04-18T16:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                }
            }
        },
        {
            "confidence": 100,
            "order": 4,
            "organizerAvailability": "tentative",
            "suggestionReason": "Suggested because it is one of the nearest times when all attendees are available.",
            "attendeeAvailability": [
                {
                    "availability": "free",
                    "attendee": {
                        "emailAddress": {
                            "address": "alexw@contoso.com"
                        }
                    }
                }
            ],
            "locations": [
                {
                    "displayName": "Conf room Hood"
                }
            ],
            "meetingTimeSlot": {
                "start": {
                    "dateTime": "2019-04-18T09:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                },
                "end": {
                    "dateTime": "2019-04-18T10:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                }
            }
        },
        {
            "confidence": 100,
            "order": 5,
            "organizerAvailability": "tentative",
            "suggestionReason": "Suggested because it is one of the nearest times when all attendees are available.",
            "attendeeAvailability": [
                {
                    "availability": "free",
                    "attendee": {
                        "emailAddress": {
                            "address": "alexw@contoso.com"
                        }
                    }
                }
            ],
            "locations": [
                {
                    "displayName": "Conf room Hood"
                }
            ],
            "meetingTimeSlot": {
                "start": {
                    "dateTime": "2019-04-18T12:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                },
                "end": {
                    "dateTime": "2019-04-18T13:00:00.0000000",
                    "timeZone": "Pacific Standard Time"
                }
            }
        }
    ]
}
```
