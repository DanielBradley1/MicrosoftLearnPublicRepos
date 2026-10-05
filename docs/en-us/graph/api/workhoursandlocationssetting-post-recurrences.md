<!-- Source: https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-post-recurrences?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create workPlanRecurrence

Namespace: microsoft.graph

Create a new [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) object in your own work plan.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/settings/workHoursAndLocations/recurrences
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

When using the `/users/{id}` endpoint, the ID must be your own user ID.

```http
POST /users/{id | userPrincipalName}/settings/workHoursAndLocations/recurrences
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [workPlanRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanrecurrence?view=graph-rest-1.0) object in the response body.

## Examples

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
POST https://graph.microsoft.com/v1.0/me/settings/workHoursAndLocations/recurrences
Content-type: application/json

{
  "start": {
    "dateTime": "2025-12-11T09:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "end": {
    "dateTime": "2025-12-11T18:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "workLocationType": "office",
  "recurrence": {
    "pattern": {
      "type": "weekly",
      "interval": 1,
      "firstDayOfWeek": "sunday",
      "daysOfWeek": ["thursday"]
    },
    "range": {
      "type": "noEnd",
      "startDate": "2025-12-11",
      "recurrenceTimeZone": "Pacific Standard Time"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new WorkPlanRecurrence
{
	Start = new DateTimeTimeZone
	{
		DateTime = "2025-12-11T09:00:00.0000000",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2025-12-11T18:00:00.0000000",
		TimeZone = "Pacific Standard Time",
	},
	WorkLocationType = WorkLocationType.Office,
	Recurrence = new PatternedRecurrence
	{
		Pattern = new RecurrencePattern
		{
			Type = RecurrencePatternType.Weekly,
			Interval = 1,
			FirstDayOfWeek = DayOfWeekObject.Sunday,
			DaysOfWeek = new List<DayOfWeekObject?>
			{
				DayOfWeekObject.Thursday,
			},
		},
		Range = new RecurrenceRange
		{
			Type = RecurrenceRangeType.NoEnd,
			StartDate = new Date(DateTime.Parse("2025-12-11")),
			RecurrenceTimeZone = "Pacific Standard Time",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.WorkHoursAndLocations.Recurrences.PostAsync(requestBody);
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

requestBody := graphmodels.NewWorkPlanRecurrence()
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2025-12-11T09:00:00.0000000"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2025-12-11T18:00:00.0000000"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
requestBody.SetEnd(end)
workLocationType := graphmodels.OFFICE_WORKLOCATIONTYPE 
requestBody.SetWorkLocationType(&workLocationType) 
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.WEEKLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
interval := int32(1)
pattern.SetInterval(&interval) 
firstDayOfWeek := graphmodels.SUNDAY_DAYOFWEEK 
pattern.SetFirstDayOfWeek(&firstDayOfWeek) 
daysOfWeek := []graphmodels.DayOfWeekable {
	dayOfWeek := graphmodels.THURSDAY_DAYOFWEEK 
	pattern.SetDayOfWeek(&dayOfWeek)
}
pattern.SetDaysOfWeek(daysOfWeek)
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
startDate := 2025-12-11
range.SetStartDate(&startDate) 
recurrenceTimeZone := "Pacific Standard Time"
range.SetRecurrenceTimeZone(&recurrenceTimeZone) 
recurrence.SetRange(range)
requestBody.SetRecurrence(recurrence)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
recurrences, err := graphClient.Me().Settings().WorkHoursAndLocations().Recurrences().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkPlanRecurrence workPlanRecurrence = new WorkPlanRecurrence();
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2025-12-11T09:00:00.0000000");
start.setTimeZone("Pacific Standard Time");
workPlanRecurrence.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2025-12-11T18:00:00.0000000");
end.setTimeZone("Pacific Standard Time");
workPlanRecurrence.setEnd(end);
workPlanRecurrence.setWorkLocationType(WorkLocationType.Office);
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.Weekly);
pattern.setInterval(1);
pattern.setFirstDayOfWeek(DayOfWeek.Sunday);
LinkedList<DayOfWeek> daysOfWeek = new LinkedList<DayOfWeek>();
daysOfWeek.add(DayOfWeek.Thursday);
pattern.setDaysOfWeek(daysOfWeek);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
LocalDate startDate = LocalDate.parse("2025-12-11");
range.setStartDate(startDate);
range.setRecurrenceTimeZone("Pacific Standard Time");
recurrence.setRange(range);
workPlanRecurrence.setRecurrence(recurrence);
WorkPlanRecurrence result = graphClient.me().settings().workHoursAndLocations().recurrences().post(workPlanRecurrence);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workPlanRecurrence = {
  start: {
    dateTime: '2025-12-11T09:00:00.0000000',
    timeZone: 'Pacific Standard Time'
  },
  end: {
    dateTime: '2025-12-11T18:00:00.0000000',
    timeZone: 'Pacific Standard Time'
  },
  workLocationType: 'office',
  recurrence: {
    pattern: {
      type: 'weekly',
      interval: 1,
      firstDayOfWeek: 'sunday',
      daysOfWeek: ['thursday']
    },
    range: {
      type: 'noEnd',
      startDate: '2025-12-11',
      recurrenceTimeZone: 'Pacific Standard Time'
    }
  }
};

await client.api('/me/settings/workHoursAndLocations/recurrences')
	.post(workPlanRecurrence);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\WorkPlanRecurrence;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\WorkLocationType;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\DayOfWeek;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;
use Microsoft\Kiota\Abstractions\Types\Date;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkPlanRecurrence();
$start = new DateTimeTimeZone();
$start->setDateTime('2025-12-11T09:00:00.0000000');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2025-12-11T18:00:00.0000000');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$requestBody->setWorkLocationType(new WorkLocationType('office'));
$recurrence = new PatternedRecurrence();
$recurrencePattern = new RecurrencePattern();
$recurrencePattern->setType(new RecurrencePatternType('weekly'));
$recurrencePattern->setInterval(1);
$recurrencePattern->setFirstDayOfWeek(new DayOfWeek('sunday'));
$recurrencePattern->setDaysOfWeek([new DayOfWeek('thursday'),	]);
$recurrence->setPattern($recurrencePattern);
$recurrenceRange = new RecurrenceRange();
$recurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$recurrenceRange->setStartDate(new Date('2025-12-11'));
$recurrenceRange->setRecurrenceTimeZone('Pacific Standard Time');
$recurrence->setRange($recurrenceRange);
$requestBody->setRecurrence($recurrence);

$result = $graphServiceClient->me()->settings()->workHoursAndLocations()->recurrences()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	start = @{
		dateTime = "2025-12-11T09:00:00.0000000"
		timeZone = "Pacific Standard Time"
	}
	end = @{
		dateTime = "2025-12-11T18:00:00.0000000"
		timeZone = "Pacific Standard Time"
	}
	workLocationType = "office"
	recurrence = @{
		pattern = @{
			type = "weekly"
			interval = 1
			firstDayOfWeek = "sunday"
			daysOfWeek = @(
			"thursday"
		)
	}
	range = @{
		type = "noEnd"
		startDate = "2025-12-11"
		recurrenceTimeZone = "Pacific Standard Time"
	}
}
}

# A UPN can also be used as -UserId.
New-MgUserSettingWorkHourAndLocationRecurrence -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.work_plan_recurrence import WorkPlanRecurrence
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.work_location_type import WorkLocationType
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.day_of_week import DayOfWeek
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkPlanRecurrence(
	start = DateTimeTimeZone(
		date_time = "2025-12-11T09:00:00.0000000",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2025-12-11T18:00:00.0000000",
		time_zone = "Pacific Standard Time",
	),
	work_location_type = WorkLocationType.Office,
	recurrence = PatternedRecurrence(
		pattern = RecurrencePattern(
			type = RecurrencePatternType.Weekly,
			interval = 1,
			first_day_of_week = DayOfWeek.Sunday,
			days_of_week = [
				DayOfWeek.Thursday,
			],
		),
		range = RecurrenceRange(
			type = RecurrenceRangeType.NoEnd,
			start_date = "2025-12-11",
			recurrence_time_zone = "Pacific Standard Time",
		),
	),
)

result = await graph_client.me.settings.work_hours_and_locations.recurrences.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('15b9b296-dac5-43d0-8b94-93bb67eef619')/settings/workHoursAndLocations/recurrences/$entity",
  "id": "AAkALgAAAAAAHYQDEapmEc2byACqAC-EWg0A62lTFlb-Zkev22NJlM7SMwADxDWWKgAA",
  "workLocationType": "office",
  "placeId": null,
  "start": {
    "dateTime": "2025-12-11T09:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "end": {
    "dateTime": "2025-12-11T18:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "recurrence": {
    "pattern": {
      "type": "weekly",
      "interval": 1,
      "firstDayOfWeek": "sunday",
      "daysOfWeek": [
        "thursday"
      ],
      "month": 0,
      "dayOfMonth": 0,
      "index": "first"
    },
    "range": {
      "type": "noEnd",
      "startDate": "2025-12-11",
      "endDate": null,
      "recurrenceTimeZone": "Pacific Standard Time",
      "numberOfOccurrences": 0
    }
  }
}
```
