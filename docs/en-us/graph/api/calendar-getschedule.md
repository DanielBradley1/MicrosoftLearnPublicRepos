<!-- Source: https://learn.microsoft.com/en-us/graph/api/calendar-getschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# calendar: getSchedule

Namespace: microsoft.graph

Get the free/busy availability information for a collection of users, distributions lists, or resources \(rooms or equipment\) for a specified time period.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadBasic | Calendars.Read, Calendars.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Calendars.ReadBasic | Calendars.Read, Calendars.ReadWrite |

## HTTP request

```http
POST /me/calendar/getSchedule
POST /users/{id|userPrincipalName}/calendar/getSchedule
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | Nature of the data in the body of an entity, which is application/json. Required. |
| Prefer: outlook.timezone | string | Use this to specify the time zone for start and end times in the response. If not specified, those time values are returned in UTC. Optional. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityViewInterval | Int32 | Represents the duration of a time slot in an **availabilityView** in the response. The default is 30 minutes, minimum is 5, maximum is 1440. Optional. |
| endTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that the period ends. |
| schedules | String collection | A collection of SMTP addresses of users, distribution lists, or resources to get availability information for. |
| startTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that the period starts. |

## Response

If successful, this method returns a `200 OK` response code and a collection of [scheduleInformation](https://learn.microsoft.com/en-us/graph/api/resources/scheduleinformation?view=graph-rest-1.0) objects for each object in the `schedules` parameter.

> **Note**: When the user's calendar has a time slot that contains more than 1000 entries, a `5006` response code with the message "The result set contains too many calendar entries. The allowed size is 1000; the actual size is ..." will be returned. For details, see [KB 2962513](https://learn.microsoft.com/en-us/exchange/troubleshoot/calendars/cannot-view-another-user-calendar-free-busy-information).

## Examples

### Request

The following example gets the availability information for two users for the specified date, time, and time zone.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/calendar/getSchedule
Prefer: outlook.timezone="Pacific Standard Time"
Content-Type: application/json

{
    "schedules": ["adelev@contoso.com", "meganb@contoso.com"],
    "startTime": {
        "dateTime": "2019-03-15T09:00:00",
        "timeZone": "Pacific Standard Time"
    },
    "endTime": {
        "dateTime": "2019-03-15T18:00:00",
        "timeZone": "Pacific Standard Time"
    },
    "availabilityViewInterval": 60
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Calendar.GetSchedule;
using Microsoft.Graph.Models;

var requestBody = new GetSchedulePostRequestBody
{
	Schedules = new List<string>
	{
		"adelev@contoso.com",
		"meganb@contoso.com",
	},
	StartTime = new DateTimeTimeZone
	{
		DateTime = "2019-03-15T09:00:00",
		TimeZone = "Pacific Standard Time",
	},
	EndTime = new DateTimeTimeZone
	{
		DateTime = "2019-03-15T18:00:00",
		TimeZone = "Pacific Standard Time",
	},
	AvailabilityViewInterval = 60,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Calendar.GetSchedule.PostAsGetSchedulePostResponseAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.CalendarGetScheduleRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewItemGetSchedulePostRequestBody()
schedules := []string {
	"adelev@contoso.com",
	"meganb@contoso.com",
}
requestBody.SetSchedules(schedules)
startTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-03-15T09:00:00"
startTime.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
startTime.SetTimeZone(&timeZone) 
requestBody.SetStartTime(startTime)
endTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2019-03-15T18:00:00"
endTime.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
endTime.SetTimeZone(&timeZone) 
requestBody.SetEndTime(endTime)
availabilityViewInterval := int32(60)
requestBody.SetAvailabilityViewInterval(&availabilityViewInterval) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getSchedule, err := graphClient.Me().Calendar().GetSchedule().PostAsGetSchedulePostResponse(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.calendar.getschedule.GetSchedulePostRequestBody getSchedulePostRequestBody = new com.microsoft.graph.users.item.calendar.getschedule.GetSchedulePostRequestBody();
LinkedList<String> schedules = new LinkedList<String>();
schedules.add("adelev@contoso.com");
schedules.add("meganb@contoso.com");
getSchedulePostRequestBody.setSchedules(schedules);
DateTimeTimeZone startTime = new DateTimeTimeZone();
startTime.setDateTime("2019-03-15T09:00:00");
startTime.setTimeZone("Pacific Standard Time");
getSchedulePostRequestBody.setStartTime(startTime);
DateTimeTimeZone endTime = new DateTimeTimeZone();
endTime.setDateTime("2019-03-15T18:00:00");
endTime.setTimeZone("Pacific Standard Time");
getSchedulePostRequestBody.setEndTime(endTime);
getSchedulePostRequestBody.setAvailabilityViewInterval(60);
var result = graphClient.me().calendar().getSchedule().post(getSchedulePostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const scheduleInformation = {
    schedules: ['adelev@contoso.com', 'meganb@contoso.com'],
    startTime: {
        dateTime: '2019-03-15T09:00:00',
        timeZone: 'Pacific Standard Time'
    },
    endTime: {
        dateTime: '2019-03-15T18:00:00',
        timeZone: 'Pacific Standard Time'
    },
    availabilityViewInterval: 60
};

await client.api('/me/calendar/getSchedule')
	.post(scheduleInformation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Calendar\GetSchedule\GetScheduleRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Users\Item\Calendar\GetSchedule\GetSchedulePostRequestBody;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetSchedulePostRequestBody();
$requestBody->setSchedules(['adelev@contoso.com', 'meganb@contoso.com', 	]);
$startTime = new DateTimeTimeZone();
$startTime->setDateTime('2019-03-15T09:00:00');
$startTime->setTimeZone('Pacific Standard Time');
$requestBody->setStartTime($startTime);
$endTime = new DateTimeTimeZone();
$endTime->setDateTime('2019-03-15T18:00:00');
$endTime->setTimeZone('Pacific Standard Time');
$requestBody->setEndTime($endTime);
$requestBody->setAvailabilityViewInterval(60);
$requestConfiguration = new GetScheduleRequestBuilderPostRequestConfiguration();
$headers = [
		'Prefer' => 'outlook.timezone="Pacific Standard Time"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->me()->calendar()->getSchedule()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.calendar.get_schedule.get_schedule_request_builder import GetScheduleRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.users.item.calendar.get_schedule.get_schedule_post_request_body import GetSchedulePostRequestBody
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetSchedulePostRequestBody(
	schedules = [
		"adelev@contoso.com",
		"meganb@contoso.com",
	],
	start_time = DateTimeTimeZone(
		date_time = "2019-03-15T09:00:00",
		time_zone = "Pacific Standard Time",
	),
	end_time = DateTimeTimeZone(
		date_time = "2019-03-15T18:00:00",
		time_zone = "Pacific Standard Time",
	),
	availability_view_interval = 60,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")


result = await graph_client.me.calendar.get_schedule.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.scheduleInformation)",
    "value": [
        {
            "scheduleId": "adelev@contoso.com",
            "availabilityView": "000220130",
            "scheduleItems": [
                {
                    "isPrivate": false,
                    "status": "busy",
                    "subject": "Let's go for lunch",
                    "location": "Harry's Bar",
                    "start": {
                        "dateTime": "2019-03-15T12:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T14:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "subject": "free is represented by 0 in availabilityView",
                    "status": "free",
                    "start": {
                        "dateTime": "2019-03-15T10:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T11:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "subject": "workingElsewhere is also represented by 0 in availabilityView",
                    "status": "workingElsewhere",
                    "start": {
                        "dateTime": "2019-03-15T11:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T12:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "subject": "tentative is represented by 1 in availabilityView",
                    "status": "tentative",
                    "start": {
                        "dateTime": "2019-03-15T15:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T16:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "subject": "oof is represented by 3 in availabilityView",
                    "status": "workingElsewhere",
                    "start": {
                        "dateTime": "2019-03-15T16:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T17:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                }
            ],
            "workingHours": {
                "daysOfWeek": [
                    "monday",
                    "tuesday",
                    "wednesday",
                    "thursday",
                    "friday"
                ],
                "startTime": "08:00:00.0000000",
                "endTime": "17:00:00.0000000",
                "timeZone": {
                    "name": "Pacific Standard Time"
                }
            }
        },
        {
            "scheduleId": "meganb@contoso.com",
            "availabilityView": "200120010",
            "scheduleItems": [
                {
                    "status": "busy",
                    "start": {
                        "dateTime": "2019-03-15T08:30:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T09:30:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "subject": "tentative is represented by 1 and overwritten by the busy-appointment (2) starting from 12 to 13.",
                    "status": "tentative",
                    "start": {
                        "dateTime": "2019-03-15T12:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T14:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "status": "busy",
                    "start": {
                        "dateTime": "2019-03-15T12:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T13:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "status": "busy",
                    "start": {
                        "dateTime": "2019-03-15T13:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T14:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                },
                {
                    "status": "tentative",
                    "start": {
                        "dateTime": "2019-03-15T16:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    },
                    "end": {
                        "dateTime": "2019-03-15T17:00:00.0000000",
                        "timeZone": "Pacific Standard Time"
                    }
                }
            ],
            "workingHours": {
                "daysOfWeek": [
                    "monday",
                    "tuesday",
                    "wednesday",
                    "thursday",
                    "friday"
                ],
                "startTime": "08:00:00.0000000",
                "endTime": "17:00:00.0000000",
                "timeZone": {
                    "@odata.type": "#microsoft.graph.customTimeZone",
                    "bias": 480,
                    "name": "Customized Time Zone",
                    "standardOffset": {
                        "time": "02:00:00.0000000",
                        "dayOccurrence": 1,
                        "dayOfWeek": "sunday",
                        "month": 11,
                        "year": 0
                    },
                    "daylightOffset": {
                        "daylightBias": -60,
                        "time": "02:00:00.0000000",
                        "dayOccurrence": 2,
                        "dayOfWeek": "sunday",
                        "month": 3,
                        "year": 0
                    }
                }
            }
        }
    ]
}
```
