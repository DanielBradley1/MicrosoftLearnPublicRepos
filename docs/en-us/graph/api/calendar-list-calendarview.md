<!-- Source: https://learn.microsoft.com/en-us/graph/api/calendar-list-calendarview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List calendarView

Namespace: microsoft.graph

Get the occurrences, exceptions and single instances of events in a calendar view defined by a time range, from a user's default calendar `(../me/calendarView)` or some other calendar of the user's.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadBasic | Calendars.Read, Calendars.ReadWrite |
| Delegated \(personal Microsoft account\) | Calendars.ReadBasic | Calendars.Read, Calendars.ReadWrite |
| Application | Calendars.ReadBasic | Calendars.Read, Calendars.ReadWrite |

## HTTP request

A user's default [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0).

```http
GET /me/calendar/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/{id | userPrincipalName}/calendar/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
```

A user's [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) in the default [calendarGroup](https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0).

```http
GET /me/calendars/{id}/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/{id | userPrincipalName}/calendars/{id}/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
```

A user's [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) in a specific [calendarGroup](https://learn.microsoft.com/en-us/graph/api/resources/calendargroup?view=graph-rest-1.0).

```http
GET /me/calendarGroups/{id}/calendars/{id}/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/{id | userPrincipalName}/calendarGroups/{id}/calendars/{id}/calendarView?startDateTime={start_datetime}&endDateTime={end_datetime}
```

## Query parameters

In the request URL, provide the following required query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | String | The start date and time of the time range, represented in ISO 8601 format. For example, "2019-11-08T19:00:00-08:00". |
| endDateTime | String | The end date and time of the time range, represented in ISO 8601 format. For example, "2019-11-08T20:00:00-08:00". |

The values of `startDateTime` and `endDateTime` are interpreted using the timezone offset specified in the value and aren't impacted by the value of the `Prefer: outlook.timezone` header if present. If no timezone offset is included in the value, it is interpreted as UTC.

This method also supports some of the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

**CalendarView** with `$top` has a minimum value of 1 and maximum of 1000.

Note

The **createdDateTime** and **lastModifiedDateTime** properties of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) don't support `$select`. To get their values, simply query on **calendarView** without applying `$select`.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer: outlook.timezone | string | Use this to specify the time zone for start and end times in the response. If not specified, those time values are returned in UTC. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and collection of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) objects in the response body.

If the result set spans multiple pages, **calendarView** returns an **@odata.nextLink** property in the response that contains a URL to the next page of results. See [paging](https://learn.microsoft.com/en-us/graph/paging) for details.

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

```msgraph
GET https://graph.microsoft.com/v1.0/me/calendar/calendarView?startDateTime=2017-01-01T19:00:00-08:00&endDateTime=2017-01-07T19:00:00-08:00
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Calendar.CalendarView.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.StartDateTime = "2017-01-01T19:00:00-08:00";
	requestConfiguration.QueryParameters.EndDateTime = "2017-01-07T19:00:00-08:00";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)


requestStartDateTime := "2017-01-01T19:00:00-08:00"
requestEndDateTime := "2017-01-07T19:00:00-08:00"

requestParameters := &graphusers.CalendarCalendarViewRequestBuilderGetQueryParameters{
	StartDateTime: &requestStartDateTime,
	EndDateTime: &requestEndDateTime,
}
configuration := &graphusers.CalendarCalendarViewRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calendarView, err := graphClient.Me().Calendar().CalendarView().Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EventCollectionResponse result = graphClient.me().calendar().calendarView().get(requestConfiguration -> {
	requestConfiguration.queryParameters.startDateTime = "2017-01-01T19:00:00-08:00";
	requestConfiguration.queryParameters.endDateTime = "2017-01-07T19:00:00-08:00";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let calendarView = await client.api('/me/calendar/calendarView?startDateTime=2017-01-01T19:00:00-08:00&endDateTime=2017-01-07T19:00:00-08:00')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Calendar\CalendarView\CalendarViewRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new CalendarViewRequestBuilderGetRequestConfiguration();
$queryParameters = CalendarViewRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->startDateTime = "2017-01-01T19:00:00-08:00";
$queryParameters->endDateTime = "2017-01-07T19:00:00-08:00";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->calendar()->calendarView()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

# A UPN can also be used as -UserId.
Get-MgUserCalendarView -UserId $userId -Startdatetime "2017-01-01T19:00:00-08:00" -Enddatetime "2017-01-07T19:00:00-08:00" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.calendar.calendar_view.calendar_view_request_builder import CalendarViewRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = CalendarViewRequestBuilder.CalendarViewRequestBuilderGetQueryParameters(
		start_date_time = "2017-01-01T19:00:00-08:00",
		end_date_time = "2017-01-07T19:00:00-08:00",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.calendar.calendar_view.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "originalStartTimeZone": "originalStartTimeZone-value",
      "originalEndTimeZone": "originalEndTimeZone-value",
      "responseStatus": {
        "response": "response-value",
        "time": "datetime-value"
      },
      "iCalUId": "iCalUId-value",
      "reminderMinutesBeforeStart": 99,
      "isReminderOn": true
    }
  ]
}
```
