<!-- Source: https://learn.microsoft.com/en-us/graph/api/workplanoccurrence-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Update workPlanOccurrence

Namespace: microsoft.graph

Update the properties of a [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) object in a user's work plan. Updates require the full occurrence object to be provided \(PUT semantics\). PATCH isn't supported.

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
| Application | Calendars.ReadWrite.All | Not available. |

> **Note:** Application permissions are supported only when using the `/users/{id}` endpoint.

## HTTP request

```http
PUT /me/settings/workHoursAndLocations/occurrences/{id}
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

When using delegated permissions with the `/users/{id}` endpoint, the ID must be the signed-in user's ID.

```http
PUT /users/{id | userPrincipalName}/settings/workHoursAndLocations/occurrences/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `200 OK` response code and an updated [workPlanOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) object in the response body.

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
PUT https://graph.microsoft.com/v1.0/me/settings/workHoursAndLocations/occurrences/QAAuAAAAAB2EAxGqZhHNm8gAqgAvxFoNAOtpUxZW-2ZHr9tjSZTO0jMAA2iQN2IAABA=
Content-type: application/json

{
  "start": {
    "dateTime": "2025-12-15T08:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "end": {
    "dateTime": "2025-12-15T12:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "workLocationType": "timeOff",
  "timeOffDetails": {
    "subject": "Doctor Appointment",
    "isAllDay": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new WorkPlanOccurrence
{
	Start = new DateTimeTimeZone
	{
		DateTime = "2025-12-15T08:00:00.0000000",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2025-12-15T12:00:00.0000000",
		TimeZone = "Pacific Standard Time",
	},
	WorkLocationType = WorkLocationType.TimeOff,
	TimeOffDetails = new TimeOffDetails
	{
		Subject = "Doctor Appointment",
		IsAllDay = false,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.WorkHoursAndLocations.Occurrences["{workPlanOccurrence-id}"].PutAsync(requestBody);
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

requestBody := graphmodels.NewWorkPlanOccurrence()
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2025-12-15T08:00:00.0000000"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2025-12-15T12:00:00.0000000"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
requestBody.SetEnd(end)
workLocationType := graphmodels.TIMEOFF_WORKLOCATIONTYPE 
requestBody.SetWorkLocationType(&workLocationType) 
timeOffDetails := graphmodels.NewTimeOffDetails()
subject := "Doctor Appointment"
timeOffDetails.SetSubject(&subject) 
isAllDay := false
timeOffDetails.SetIsAllDay(&isAllDay) 
requestBody.SetTimeOffDetails(timeOffDetails)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
occurrences, err := graphClient.Me().Settings().WorkHoursAndLocations().Occurrences().ByWorkPlanOccurrenceId("workPlanOccurrence-id").Put(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkPlanOccurrence workPlanOccurrence = new WorkPlanOccurrence();
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2025-12-15T08:00:00.0000000");
start.setTimeZone("Pacific Standard Time");
workPlanOccurrence.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2025-12-15T12:00:00.0000000");
end.setTimeZone("Pacific Standard Time");
workPlanOccurrence.setEnd(end);
workPlanOccurrence.setWorkLocationType(WorkLocationType.TimeOff);
TimeOffDetails timeOffDetails = new TimeOffDetails();
timeOffDetails.setSubject("Doctor Appointment");
timeOffDetails.setIsAllDay(false);
workPlanOccurrence.setTimeOffDetails(timeOffDetails);
WorkPlanOccurrence result = graphClient.me().settings().workHoursAndLocations().occurrences().byWorkPlanOccurrenceId("{workPlanOccurrence-id}").put(workPlanOccurrence);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workPlanOccurrence = {
  start: {
    dateTime: '2025-12-15T08:00:00.0000000',
    timeZone: 'Pacific Standard Time'
  },
  end: {
    dateTime: '2025-12-15T12:00:00.0000000',
    timeZone: 'Pacific Standard Time'
  },
  workLocationType: 'timeOff',
  timeOffDetails: {
    subject: 'Doctor Appointment',
    isAllDay: false
  }
};

await client.api('/me/settings/workHoursAndLocations/occurrences/QAAuAAAAAB2EAxGqZhHNm8gAqgAvxFoNAOtpUxZW-2ZHr9tjSZTO0jMAA2iQN2IAABA=')
	.put(workPlanOccurrence);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\WorkPlanOccurrence;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\WorkLocationType;
use Microsoft\Graph\Generated\Models\TimeOffDetails;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkPlanOccurrence();
$start = new DateTimeTimeZone();
$start->setDateTime('2025-12-15T08:00:00.0000000');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2025-12-15T12:00:00.0000000');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$requestBody->setWorkLocationType(new WorkLocationType('timeOff'));
$timeOffDetails = new TimeOffDetails();
$timeOffDetails->setSubject('Doctor Appointment');
$timeOffDetails->setIsAllDay(false);
$requestBody->setTimeOffDetails($timeOffDetails);

$result = $graphServiceClient->me()->settings()->workHoursAndLocations()->occurrences()->byWorkPlanOccurrenceId('workPlanOccurrence-id')->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	start = @{
		dateTime = "2025-12-15T08:00:00.0000000"
		timeZone = "Pacific Standard Time"
	}
	end = @{
		dateTime = "2025-12-15T12:00:00.0000000"
		timeZone = "Pacific Standard Time"
	}
	workLocationType = "timeOff"
	timeOffDetails = @{
		subject = "Doctor Appointment"
		isAllDay = $false
	}
}

# A UPN can also be used as -UserId.
Set-MgUserSettingWorkHourAndLocationOccurrence -UserId $userId -WorkPlanOccurrenceId $workPlanOccurrenceId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.work_plan_occurrence import WorkPlanOccurrence
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.work_location_type import WorkLocationType
from msgraph.generated.models.time_off_details import TimeOffDetails
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkPlanOccurrence(
	start = DateTimeTimeZone(
		date_time = "2025-12-15T08:00:00.0000000",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2025-12-15T12:00:00.0000000",
		time_zone = "Pacific Standard Time",
	),
	work_location_type = WorkLocationType.TimeOff,
	time_off_details = TimeOffDetails(
		subject = "Doctor Appointment",
		is_all_day = False,
	),
)

result = await graph_client.me.settings.work_hours_and_locations.occurrences.by_work_plan_occurrence_id('workPlanOccurrence-id').put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAAiIsqMbYjsT5e-T7KzowPTAAABvv6cAAA=",
  "recurrenceId": null,
  "start": {
    "dateTime": "2025-12-15T08:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "end": {
    "dateTime": "2025-12-15T12:00:00.0000000",
    "timeZone": "Pacific Standard Time"
  },
  "workLocationType": "timeOff",
  "timeOffDetails": {
    "subject": "Doctor Appointment",
    "isAllDay": false
  }
}
```
