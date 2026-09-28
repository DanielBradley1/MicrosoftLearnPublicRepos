<!-- Source: https://learn.microsoft.com/en-us/graph/api/event-delta?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# event: delta

Namespace: microsoft.graph

Get a set of [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) resources that have been added, deleted, or updated in a **calendarView** \(a range of events defined by start and end dates\) of the user's primary calendar.

Typically, synchronizing events in a **calendarView** in a local store entails a round of multiple **delta** function calls. The initial call is a full synchronization, and every subsequent **delta** call in the same round gets the incremental changes \(additions, deletions, or updates\). This allows you to maintain and synchronize a local store of events in the specified **calendarView**, without having to fetch all the events of that calendar from the server every time.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.Read | Calendars.ReadBasic, Calendars.ReadWrite |
| Delegated \(personal Microsoft account\) | Calendars.Read | Calendars.ReadBasic, Calendars.ReadWrite |
| Application | Calendars.Read | Calendars.ReadBasic, Calendars.ReadWrite |

## HTTP request

```http
GET /me/calendarView/delta?startDateTime={start_datetime}&endDateTime={end_datetime}
GET /users/{id}/calendarView/delta?startDateTime={start_datetime}&endDateTime={end_datetime}
```

## Query parameters

Tracking changes in events incurs a round of one or more **delta** function calls. If you use any query parameter \(other than `$deltatoken` and `$skiptoken`\), you must specify it in the initial **delta** request. Microsoft Graph automatically encodes any specified parameters into the token portion of the `@odata.nextLink` or `@odata.deltaLink` URL provided in the response. You only need to specify any desired query parameters once upfront. In subsequent requests, simply copy and apply the `@odata.nextLink` or `@odata.deltaLink` URL from the previous response, as that URL already includes the encoded, desired parameters.

| Query parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | String | The start date and time of the time range, represented in ISO 8601 format. For example, "2015-11-08T19:00:00.0000000". |
| endDateTime | String | The end date and time of the time range, represented in ISO 8601 format. For example, "2015-11-08T20:00:00.0000000". |
| $deltatoken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.deltaLink` URL of the previous **delta** function call for the same calendar view, indicating the completion of that round of change tracking. Save and apply the entire `@odata.deltaLink` URL including this token in the first request of the next round of change tracking for that calendar view. |
| $skiptoken | string | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `@odata.nextLink` URL of the previous **delta** function call, indicating there are further changes to be tracked in the same calendar view. |

### OData query parameters

- Expect a **delta** function call on a **calendarView** to return the same properties you'd normally get from a `GET /calendarView` request. You cannot use `$select` to get only a subset of those properties.
- There are other OData query parameters that the **delta** function for **calendarView** doesn't support: `$expand`, `$filter`,`$orderby`, and `$search`.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | string | application/json. Required. |
| Prefer | string | odata.maxpagesize={x}. Optional. |
| Prefer | string | {Time zone}. Optional, UTC assumed if absent. |

## Response

If successful, this method returns a `200 OK` response code and [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) collection object in the response body.

Within a round of **delta** function calls bound by the date range of a **calendarView**, you may find a **delta** call returning two types of events under `@removed` with the reason `deleted`:

- Events that are within the date range and that have been deleted since the previous **delta** call.
- Events that are *outside* the date range and that have been added, deleted, or updated since the previous **delta** call.

Filter the events under `@removed` for the date range that your scenario requires.

## Example

### Request

The following example shows how to make a single **delta** function call, and limit the maximum number of events in the response body to 2.

To track changes in a calendar view, you would make one or more **delta** function calls, with appropriate [state tokens](https://learn.microsoft.com/en-us/graph/delta-query-overview), to get the set of incremental changes since the last delta query.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/calendarView/delta?startdatetime={start_datetime}&enddatetime={end_datetime}
Prefer: odata.maxpagesize=2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.CalendarView.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.StartDateTime = "{start_datetime}";
	requestConfiguration.QueryParameters.EndDateTime = "{end_datetime}";
	requestConfiguration.Headers.Add("Prefer", "odata.maxpagesize=2");
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
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "odata.maxpagesize=2")


requestStartDateTime := "{start_datetime}"
requestEndDateTime := "{end_datetime}"

requestParameters := &graphusers.CalendarViewDeltaRequestBuilderGetQueryParameters{
	StartDateTime: &requestStartDateTime,
	EndDateTime: &requestEndDateTime,
}
configuration := &graphusers.CalendarViewDeltaRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Me().CalendarView().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.me().calendarView().delta().get(requestConfiguration -> {
	requestConfiguration.queryParameters.startDateTime = "{start_datetime}";
	requestConfiguration.queryParameters.endDateTime = "{end_datetime}";
	requestConfiguration.headers.add("Prefer", "odata.maxpagesize=2");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/me/calendarView/delta?startdatetime={start_datetime}&enddatetime={end_datetime}')
	.header('Prefer','odata.maxpagesize=2')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\CalendarView\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$headers = [
		'Prefer' => 'odata.maxpagesize=2',
	];
$requestConfiguration->headers = $headers;

$queryParameters = DeltaRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->startDateTime = "{start_datetime}";
$queryParameters->endDateTime = "{end_datetime}";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->calendarView()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.calendar_view.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = DeltaRequestBuilder.DeltaRequestBuilderGetQueryParameters(
		start_date_time = "{start_datetime}",
		end_date_time = "{end_datetime}",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("Prefer", "odata.maxpagesize=2")


result = await graph_client.me.calendar_view.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

If the request is successful, the response would include a state token, which is either a *skipToken* \(in an *@odata.nextLink* response header\) or a *deltaToken* \(in an *@odata.deltaLink* response header\). Respectively, they indicate whether you should continue with the round or you have completed getting all the changes for that round.

The response below shows a *skipToken* in an *@odata.nextLink* response header.

Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.nextLink":"https://graph.microsoft.com/v1.0/me/calendarView/delta?$skiptoken={_skipToken_}",
  "value": [
    {
      "originalStartTimeZone": "originalStartTimeZone-value",
      "originalEndTimeZone": "originalEndTimeZone-value",
      "responseStatus": {
        "response": "response-value",
        "time": "datetime-value"
      },
      "transactionId": null,
      "iCalUId": "iCalUId-value",
      "reminderMinutesBeforeStart": 99,
      "isDraft": false,
      "isReminderOn": true
    }
  ]
}
```

## Related content

- [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview)
- [Get incremental changes to events in a calendar](https://learn.microsoft.com/en-us/graph/delta-query-events)
