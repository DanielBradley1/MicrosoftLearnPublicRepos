<!-- Source: https://learn.microsoft.com/en-us/graph/api/event-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-21 -->

# Get event

Namespace: microsoft.graph

Get the properties and relationships of the specified [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object.

Currently, this operation returns event bodies in only HTML format.

There are two scenarios where an app can get an event in another user's calendar:

- If the app has application permissions, or,
- If the app has the appropriate delegated [permissions](#permissions) from one user, and another user has shared a calendar with that user, or, has given delegated access to that user. See [details and an example](https://learn.microsoft.com/en-us/graph/outlook-get-shared-events-calendars).

Since the **event** resource supports [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview), you can also use the `GET` operation to get custom properties and extension data in an **event** instance.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

### Support various time zones

For all GET operations that return events, you can use the `Prefer: outlook.timezone` header to specify the time zone for the event start and end times in the response.

For example, the following `Prefer: outlook.timezone` header sets the start and end times in the response to Eastern Standard Time.

```http
Prefer: outlook.timezone="Eastern Standard Time"
```

If the event was created in a different time zone, the start and end times will be adjusted to the time zone specified in that `Prefer` header. For the supported time zone names, see [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0). If the `Prefer: outlook.timezone` header is not specified, the start and end times are returned in UTC.

You can use the **OriginalStartTimeZone** and **OriginalEndTimeZone** properties on the **event** resource to find out the time zone used when the event was created.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadBasic, Calendars.Read |
| Delegated \(personal Microsoft account\) | Calendars.ReadBasic, Calendars.Read |
| Application | Calendars.ReadBasic, Calendars.Read |

## HTTP request

```http
GET /me/events/{id}
GET /users/{id | userPrincipalName}/events/{id}
GET /groups/{id}/events/{id}

GET /me/calendar/events/{id}
GET /users/{id | userPrincipalName}/calendar/events/{id}
GET /groups/{id}/calendar/events/{id}

GET /me/calendars/{id}/events/{id}
GET /users/{id | userPrincipalName}/calendars/{id}/events/{id}

GET /me/calendarGroups/{id}/calendars/{id}/events/{id}
GET /users/{id | userPrincipalName}/calendarGroups/{id}/calendars/{id}/events/{id}
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer: outlook.timezone | string | Use this to specify the time zone for start and end times in the response. If not specified, those time values are returned in UTC. Optional. |
| Prefer: outlook.body-content-type | string | The format of the **body** property to be returned in. Values can be "text" or "html". A `Preference-Applied` header is returned as confirmation if this `Prefer` header is specified. If the header is not specified, the **body** property is returned in HTML format. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get a specified event

The following example gets the specified event. It specifies the following:

- A `Prefer: outlook.timezone` header to get date time values returned in Pacific Standard Time.
- A `$select` query parameter to return specific properties. Without a `$select` parameter, all of the event properties are returned.

#### Request

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
GET https://graph.microsoft.com/v1.0/me/events/AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAAiIsqMbYjsT5e-T7KzowPTAAAa_WKzAAA=?$select=subject,body,bodyPreview,organizer,attendees,start,end,location,hideAttendees
Prefer: outlook.timezone="Pacific Standard Time"
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events["{event-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "subject","body","bodyPreview","organizer","attendees","start","end","location","hideAttendees" };
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
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")

requestParameters := &graphusers.EventsItemRequestBuilderGetQueryParameters{
	Select: [] string {"subject","body","bodyPreview","organizer","attendees","start","end","location","hideAttendees"},
}
configuration := &graphusers.EventsItemRequestBuilderGetRequestConfiguration{
	Headers: headers,
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().ByEventId("event-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event result = graphClient.me().events().byEventId("{event-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"subject", "body", "bodyPreview", "organizer", "attendees", "start", "end", "location", "hideAttendees"};
	requestConfiguration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let event = await client.api('/me/events/AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAAiIsqMbYjsT5e-T7KzowPTAAAa_WKzAAA=')
	.header('Prefer','outlook.timezone="Pacific Standard Time"')
	.select('subject,body,bodyPreview,organizer,attendees,start,end,location,hideAttendees')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\EventItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new EventItemRequestBuilderGetRequestConfiguration();
$headers = [
		'Prefer' => 'outlook.timezone="Pacific Standard Time"',
	];
$requestConfiguration->headers = $headers;

$queryParameters = EventItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["subject","body","bodyPreview","organizer","attendees","start","end","location","hideAttendees"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->events()->byEventId('event-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

# A UPN can also be used as -UserId.
Get-MgUserEvent -UserId $userId -EventId $eventId -Property "subject,body,bodyPreview,organizer,attendees,start,end,location,hideAttendees" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.event_item_request_builder import EventItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = EventItemRequestBuilder.EventItemRequestBuilderGetQueryParameters(
		select = ["subject","body","bodyPreview","organizer","attendees","start","end","location","hideAttendees"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)
request_configuration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")


result = await graph_client.me.events.by_event_id('event-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **body** property is returned in the default format of HTML.

```http
HTTP/1.1 200 OK
Content-type: application/json
Preference-Applied: outlook.timezone="Pacific Standard Time"

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('48d31887-5fad-4d73-a9f5-3c356e68a038')/events(subject,body,bodyPreview,organizer,attendees,start,end,location,hideAttendees)/$entity",
    "@odata.etag": "W/\"IiLKjG2I7E+Xv0+ys6MD0wAEd5/kNQ==\"",
    "id": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAAiIsqMbYjsT5e-T7KzowPTAAAa_WKzAAA=",
    "subject": "New Product Regulations Touchpoint",
    "bodyPreview": "New Product Regulations Strategy Online Touchpoint MeetingYou're receiving this message because you're a member of the Engineering group. If you don't want to receive any messages or events from this group, stop following it in your inbox.View g",
    "hideAttendees": false,
    "body": {
        "contentType": "html",
        "content": "<html><head><meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\"></head><body>New Product Regulations Strategy Online Touchpoint Meeting<div id=\"a59ada49-a492-4f1d-ac57-74be3a4194fc\" style=\"display:inline-block\"><table cellspacing=\"0\" style=\"table-layout:fixed; width:50px; border:0 none black\"><tbody><tr><td style=\"height:18px; padding:0; border-width:0 0 1px 0; border-style:none none solid none; border-color:#EAEAEA\">&nbsp;</td></tr></tbody></table><table cellspacing=\"0\" style=\"table-layout:fixed; width:90%; line-height:17px; border:0 none black\"><tbody><tr><td style=\"height:17px; padding:0; border:0 none black\">&nbsp;</td></tr><tr><td style=\"padding:0; border:0 none black; color:#666666; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\">You're receiving this message because you're a member of the <a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=conversations\" style=\"color:#0072C6; text-decoration:none; font-size:12px; font-family:'Segoe UI Semibold','Segoe WP Semibold','Segoe UI','Segoe WP',sans-serif\">Engineering</a> group. If you don't want to receive any messages or events from this group,<a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=unsubscribe\" id=\"BD5134C6-8D33-4ABA-A0C4-08581FDF89DB\" style=\"color:#0072C6; text-decoration:none; font-size:12px; font-family:'Segoe UI Semibold','Segoe WP Semibold','Segoe UI','Segoe WP',sans-serif\">stop following it in your inbox</a>.</td></tr><tr><td style=\"height:17px; padding:0; border:0 none black\">&nbsp;</td></tr><tr><td style=\"padding:0; border:0 none black; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\"><span style=\"display:inline-block\"><a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=conversations\" style=\"color:#666666; text-decoration:none; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\">View group conversations</a></span><span style=\"color:#C8C8C8\">&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;</span><span style=\"display:inline-block\"><a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=files\" style=\"color:#666666; text-decoration:none; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\">View group files</a></span></td></tr><tr><td style=\"height:17px; padding:0; border:0 none black\">&nbsp;</td></tr></tbody></table></div></body></html>"
    },
    "start": {
        "dateTime": "2014-11-03T17:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2014-11-03T17:30:00.0000000",
        "timeZone": "UTC"
    },
    "location": {
        "displayName": "Conf Room Rainier",
        "locationType": "default",
        "uniqueId": "Conf Room Rainier",
        "uniqueIdType": "private"
    },
    "attendees": [
        {
            "type": "required",
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "emailAddress": {
                "name": "Engineering",
                "address": "engineering@contoso.com"
            }
        },
        {
            "type": "required",
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "emailAddress": {
                "name": "Irvin Sayers",
                "address": "IrvinS@contoso.com"
            }
        }
    ],
    "organizer": {
        "emailAddress": {
            "name": "Engineering",
            "address": "engineering@contoso.com"
        }
    },
    "calendar@odata.associationLink": "https://graph.microsoft.com/v1.0/users('48d31887-5fad-4d73-a9f5-3c356e68a038')/calendars('AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OAAuAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAA=')/$ref",
    "calendar@odata.navigationLink": "https://graph.microsoft.com/v1.0/users('48d31887-5fad-4d73-a9f5-3c356e68a038')/calendars('AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OAAuAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAA=')"
}
```

### Example 2: Get an event that specifies more than one location

The following example shows how to get an event that specifies more than one location. The request specifies a `$select` query parameter to return specific properties.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/events/AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAAiIsqMbYjsT5e-T7KzowPTAAAa_WKzAAA=?$select=subject,body,bodyPreview,organizer,attendees,start,end,location,locations
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events["{event-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "subject","body","bodyPreview","organizer","attendees","start","end","location","locations" };
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

requestParameters := &graphusers.EventsItemRequestBuilderGetQueryParameters{
	Select: [] string {"subject","body","bodyPreview","organizer","attendees","start","end","location","locations"},
}
configuration := &graphusers.EventsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().ByEventId("event-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event result = graphClient.me().events().byEventId("{event-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"subject", "body", "bodyPreview", "organizer", "attendees", "start", "end", "location", "locations"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let event = await client.api('/me/events/AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAAiIsqMbYjsT5e-T7KzowPTAAAa_WKzAAA=')
	.select('subject,body,bodyPreview,organizer,attendees,start,end,location,locations')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\EventItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new EventItemRequestBuilderGetRequestConfiguration();
$queryParameters = EventItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["subject","body","bodyPreview","organizer","attendees","start","end","location","locations"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->events()->byEventId('event-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

# A UPN can also be used as -UserId.
Get-MgUserEvent -UserId $userId -EventId $eventId -Property "subject,body,bodyPreview,organizer,attendees,start,end,location,locations" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.event_item_request_builder import EventItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = EventItemRequestBuilder.EventItemRequestBuilderGetQueryParameters(
		select = ["subject","body","bodyPreview","organizer","attendees","start","end","location","locations"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.events.by_event_id('event-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **locations** property includes details for the three locations that the event is organized for.

Because the request doesn't specify any `Prefer: outlook.timezone` header, the **start** and **end** properties are displayed in the default UTC time zone.

The event body is in the default HTML format.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('48d31887-5fad-4d73-a9f5-3c356e68a038')/events(subject,body,bodyPreview,organizer,attendees,start,end,location,locations)/$entity",
    "@odata.etag": "W/\"IiLKjG2I7E+Xv0+ys6MD0wAEd5/kNQ==\"",
    "id": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURBwAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAAiIsqMbYjsT5e-T7KzowPTAAAa_WKzAAA=",
    "subject": "New Product Regulations Touchpoint",
    "bodyPreview": "New Product Regulations Strategy Online Touchpoint MeetingYou're receiving this message because you're a member of the Engineering group. If you don't want to receive any messages or events from this group, stop following it in your inbox.View g",
    "body": {
        "contentType": "html",
        "content": "<html><head><meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\"></head><body>New Product Regulations Strategy Online Touchpoint Meeting<div id=\"a59ada49-a492-4f1d-ac57-74be3a4194fc\" style=\"display:inline-block\"><table cellspacing=\"0\" style=\"table-layout:fixed; width:50px; border:0 none black\"><tbody><tr><td style=\"height:18px; padding:0; border-width:0 0 1px 0; border-style:none none solid none; border-color:#EAEAEA\">&nbsp;</td></tr></tbody></table><table cellspacing=\"0\" style=\"table-layout:fixed; width:90%; line-height:17px; border:0 none black\"><tbody><tr><td style=\"height:17px; padding:0; border:0 none black\">&nbsp;</td></tr><tr><td style=\"padding:0; border:0 none black; color:#666666; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\">You're receiving this message because you're a member of the <a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=conversations\" style=\"color:#0072C6; text-decoration:none; font-size:12px; font-family:'Segoe UI Semibold','Segoe WP Semibold','Segoe UI','Segoe WP',sans-serif\">Engineering</a> group. If you don't want to receive any messages or events from this group,<a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=unsubscribe\" id=\"BD5134C6-8D33-4ABA-A0C4-08581FDF89DB\" style=\"color:#0072C6; text-decoration:none; font-size:12px; font-family:'Segoe UI Semibold','Segoe WP Semibold','Segoe UI','Segoe WP',sans-serif\">stop following it in your inbox</a>.</td></tr><tr><td style=\"height:17px; padding:0; border:0 none black\">&nbsp;</td></tr><tr><td style=\"padding:0; border:0 none black; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\"><span style=\"display:inline-block\"><a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=conversations\" style=\"color:#666666; text-decoration:none; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\">View group conversations</a></span><span style=\"color:#C8C8C8\">&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;</span><span style=\"display:inline-block\"><a href=\"https://outlook.office365.com/owa/engineering@contoso.com/groupsubscription.ashx?realm=contoso.com&amp;source=EscalatedMessage&amp;action=files\" style=\"color:#666666; text-decoration:none; font-size:12px; font-family:'Segoe UI','Segoe WP',sans-serif\">View group files</a></span></td></tr><tr><td style=\"height:17px; padding:0; border:0 none black\">&nbsp;</td></tr></tbody></table></div></body></html>"
    },
    "start": {
        "dateTime": "2014-11-03T17:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2014-11-03T17:30:00.0000000",
        "timeZone": "UTC"
    },
    "location": {
        "displayName": "Conf Room Rainier",
        "locationType": "default",
        "uniqueId": "Conf Room Rainier",
        "uniqueIdType": "private"
    },
    "locations": [
        {
            "displayName": "Conf Room Rainier",
            "locationType": "default",
            "uniqueId": "",
            "uniqueIdType": "unknown"
        }
    ],
    "attendees": [
        {
            "type": "required",
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "emailAddress": {
                "name": "Engineering",
                "address": "engineering@contoso.com"
            }
        },
        {
            "type": "required",
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "emailAddress": {
                "name": "Irvin Sayers",
                "address": "IrvinS@contoso.com"
            }
        }
    ],
    "organizer": {
        "emailAddress": {
            "name": "Engineering",
            "address": "engineering@contoso.com"
        }
    },
    "calendar@odata.associationLink": "https://graph.microsoft.com/v1.0/users('48d31887-5fad-4d73-a9f5-3c356e68a038')/calendars('AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OAAuAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAA=')/$ref",
    "calendar@odata.navigationLink": "https://graph.microsoft.com/v1.0/users('48d31887-5fad-4d73-a9f5-3c356e68a038')/calendars('AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OAAuAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAENAAA=')"
}
```

### Example 3: Expand a series master event

The following example shows how to expand a series master event of a recurring series with exceptions and cancelled occurences. The request specifies a `$select` query parameter to return specific properties.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/events/AAMkADAGAADDdm4NAAA=?$select=subject,start,end,occurrenceId,exceptionOccurrences,cancelledOccurrences&$expand=exceptionOccurrences
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events["{event-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Select = new string []{ "subject","start","end","occurrenceId","exceptionOccurrences","cancelledOccurrences" };
	requestConfiguration.QueryParameters.Expand = new string []{ "exceptionOccurrences" };
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

requestParameters := &graphusers.EventsItemRequestBuilderGetQueryParameters{
	Select: [] string {"subject","start","end","occurrenceId","exceptionOccurrences","cancelledOccurrences"},
	Expand: [] string {"exceptionOccurrences"},
}
configuration := &graphusers.EventsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().ByEventId("event-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event result = graphClient.me().events().byEventId("{event-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.select = new String []{"subject", "start", "end", "occurrenceId", "exceptionOccurrences", "cancelledOccurrences"};
	requestConfiguration.queryParameters.expand = new String []{"exceptionOccurrences"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let event = await client.api('/me/events/AAMkADAGAADDdm4NAAA=')
	.expand('exceptionOccurrences,cancelledOccurrences')
	.select('subject,start,end,occurrenceId,exceptionOccurrences,cancelledOccurrences')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\EventItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new EventItemRequestBuilderGetRequestConfiguration();
$queryParameters = EventItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->select = ["subject","start","end","occurrenceId","exceptionOccurrences","cancelledOccurrences"];
$queryParameters->expand = ["exceptionOccurrences"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->events()->byEventId('event-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

# A UPN can also be used as -UserId.
Get-MgUserEvent -UserId $userId -EventId $eventId -Property "subject,start,end,occurrenceId,exceptionOccurrences,cancelledOccurrences" -ExpandProperty "exceptionOccurrences" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.event_item_request_builder import EventItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = EventItemRequestBuilder.EventItemRequestBuilderGetQueryParameters(
		select = ["subject","start","end","occurrenceId","exceptionOccurrences","cancelledOccurrences"],
		expand = ["exceptionOccurrences"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.events.by_event_id('event-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The GET operation returns the selected properties for the series master event. Specifically, for events in the **exceptionOccurrences** collection, the operation returns the **id** property, and the applicable, selected properties \(**subject**, **start**, **end**, **occurrenceId**\). As for events in the **cancelledOccurrences** collection, because the events no longer exist, the operation returns only their **occurrenceId** property values.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('d1a2fae9-db66-4cc9-8133-2184c77af1b8')/events(subject,start,end,occurrenceId,exceptionOccurrences,cancelledOccurrences)/$entity",
  "@odata.etag": "W/\"y53lbKh6jkaxHzFwGhgyxgAAw5zhug==\"",
  "id": "AAMkADAGAADDdm4NAAA=",
  "iCalUId": "040000008200E00074=",
  "uid": "040000008200E00074C=",
  "subject": "Daily stand-up",
  "cancelledOccurrences": [
    "OID.AAMkADAGAADDdm4NAAA=.2020-04-30",
    "OID.AAMkADAGAADDdm4NAAA=.2020-05-07",
    "OID.AAMkADAGAADDdm4NAAA=.2020-05-14"
  ],
  "occurrenceId": null,
  "start": {
    "dateTime": "2020-04-23T11:30:00.0000000",
    "timeZone": "UTC"
  },
  "end": {
    "dateTime": "2020-04-23T12:00:00.0000000",
    "timeZone": "UTC"
  },
  "exceptionOccurrences": [
    {
      "id": "AAMkADM0ZGRhMjdjLTA==",
      "Subject": "SM update 24",
      "occurrenceId": "OID.AAMkADAGAADDdm4NAAA=.2020-05-21",
      "start": {
        "dateTime": "2020-05-21T11:30:00.0000000",
        "timeZone": "UTC"
      },
      "end": {
        "dateTime": "2020-05-21T12:00:00.0000000",
        "timeZone": "UTC"
      }
    }
  ]
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
