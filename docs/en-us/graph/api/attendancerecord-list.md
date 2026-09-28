<!-- Source: https://learn.microsoft.com/en-us/graph/api/attendancerecord-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# List attendanceRecords

Namespace: microsoft.graph

Get a list of [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0) objects and their properties.

Tip

A more convenient way to retrieve attendance records is to get them in line with an attendance report by using the `expand` query option. For an example and more details, see [Get meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/meetingattendancereport-get?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetingArtifact.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OnlineMeetingArtifact.Read.All | OnlineMeetingArtifact.Read.Chat |

To use application permission for this API, tenant administrators must create an application access policy and grant it to a user. This authorizes the app configured in the policy to fetch online meetings and/or online meeting artifacts on behalf of that user \(with the user ID specified in the request path\). For more details, see [Allow applications to access online meetings on behalf of a user](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

Note

The `OnlineMeetingArtifact.Read.Chat` permission uses [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent). It is only applicable to attendance reports for town halls or webinars.

## HTTP request

To get attendance records of an attendance report with delegated \(`/me`\) and app \(`/users/{userId}`\) permission:

```http
GET /me/onlineMeetings/{meetingId}/attendanceReports/{reportId}/attendanceRecords
GET /users/{userId}/onlineMeetings/{meetingId}/attendanceReports/{reportId}/attendanceRecords
```

To get attendance records from the attendance report for a webinar session using delegated and application permissions:

```http
GET /solutions/virtualEvents/webinars/{webinarId}/sessions/{sessionId}/attendanceReports/{reportId}/attendanceRecords
```

To get attendance records from the attendance report for a town hall session using delegated and application permissions:

```http
GET /solutions/virtualEvents/townhalls/{townhallId}/sessions/{sessionId}/attendanceReports/{reportId}/attendanceRecords
```

Tip

- **userId** is the object ID of a user in [Microsoft Entra admin center > user management page](https://entra.microsoft.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade). For more details, see [Allow applications to access online meetings on behalf of a user](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).
- `meetingId` is the **id** of an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object.
- `reportId` is the **id** of a [meetingAttendanceReport](https://learn.microsoft.com/en-us/graph/api/resources/meetingattendancereport?view=graph-rest-1.0) object.
- `webinarId` is the **id** of a [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) object.
- `sessionId` is the **id** of a [virtualEventSession](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsession?view=graph-rest-1.0) object.
- `townhallId` is the **id** of a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) object.
- Only the webinar or townhall organizer or coorganizer can access this API.

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [attendanceRecord](https://learn.microsoft.com/en-us/graph/api/resources/attendancerecord?view=graph-rest-1.0) objects in the response body.

## Examples

### Example 1: List attendance records

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/attendanceReports/c9b6db1c-d5eb-427d-a5c0-20088d9b22d7/attendanceRecords
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].AttendanceReports["{meetingAttendanceReport-id}"].AttendanceRecords.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
attendanceRecords, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").AttendanceReports().ByMeetingAttendanceReportId("meetingAttendanceReport-id").AttendanceRecords().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AttendanceRecordCollectionResponse result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").attendanceReports().byMeetingAttendanceReportId("{meetingAttendanceReport-id}").attendanceRecords().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let attendanceRecords = await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/attendanceReports/c9b6db1c-d5eb-427d-a5c0-20088d9b22d7/attendanceRecords')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->attendanceReports()->byMeetingAttendanceReportId('meetingAttendanceReport-id')->attendanceRecords()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

# A UPN can also be used as -UserId.
Get-MgUserOnlineMeetingAttendanceReportAttendanceRecord -UserId $userId -OnlineMeetingId $onlineMeetingId -MeetingAttendanceReportId $meetingAttendanceReportId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').attendance_reports.by_meeting_attendance_report_id('meetingAttendanceReport-id').attendance_records.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "emailAddress": "frederick.cormier@contoso.com",
      "totalAttendanceInSeconds": 322,
      "role": "Organizer",
      "identity": {
        "id": "dc17674c-81d9-4adb-bfb2-8f6a442e4623",
        "displayName": "Frederick Cormier",
        "tenantId": null
      },
      "attendanceIntervals": [
        {
          "joinDateTime": "2021-10-05T04:38:27.6027225Z",
          "leaveDateTime": "2021-10-05T04:43:49.7702391Z",
          "durationInSeconds": 322
        }
      ]
    },
    {
      "emailAddress": "lisa.adkins@contoso.com",
      "totalAttendanceInSeconds": 314,
      "role": "Presenter",
      "identity": {
        "id": "57caaef9-5ed0-48d5-8862-e5abfa71b3e9",
        "displayName": "Lisa Adkins",
        "tenantId": null
      },
      "attendanceIntervals": [
        {
          "joinDateTime": "2021-10-04T23:13:43.3776519Z",
          "leaveDateTime": "2021-10-04T23:18:57.5639338Z",
          "durationInSeconds": 314
        }
      ]
    }
  ]
}
```

### Example 2: List attendance records of a webinar session's attendance report

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
GET https://graph.microsoft.com/v1.0/solutions/virtualEvents/webinars/336f94f4-3a81-5130-43e9-88f3-fcb3582cde37/sessions/8d62dd52-4dff-4c75-96a9-f905cc3ff942/attendanceReports/2c2454-7613-4d6e-9c7c-4c8/attendanceRecords
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Webinars["{virtualEventWebinar-id}"].Sessions["{virtualEventSession-id}"].AttendanceReports["{meetingAttendanceReport-id}"].AttendanceRecords.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
attendanceRecords, err := graphClient.Solutions().VirtualEvents().Webinars().ByVirtualEventWebinarId("virtualEventWebinar-id").Sessions().ByVirtualEventSessionId("virtualEventSession-id").AttendanceReports().ByMeetingAttendanceReportId("meetingAttendanceReport-id").AttendanceRecords().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AttendanceRecordCollectionResponse result = graphClient.solutions().virtualEvents().webinars().byVirtualEventWebinarId("{virtualEventWebinar-id}").sessions().byVirtualEventSessionId("{virtualEventSession-id}").attendanceReports().byMeetingAttendanceReportId("{meetingAttendanceReport-id}").attendanceRecords().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let attendanceRecords = await client.api('/solutions/virtualEvents/webinars/336f94f4-3a81-5130-43e9-88f3-fcb3582cde37/sessions/8d62dd52-4dff-4c75-96a9-f905cc3ff942/attendanceReports/2c2454-7613-4d6e-9c7c-4c8/attendanceRecords')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->virtualEvents()->webinars()->byVirtualEventWebinarId('virtualEventWebinar-id')->sessions()->byVirtualEventSessionId('virtualEventSession-id')->attendanceReports()->byMeetingAttendanceReportId('meetingAttendanceReport-id')->attendanceRecords()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

Get-MgVirtualEventWebinarSessionAttendanceReportAttendanceRecord -VirtualEventWebinarId $virtualEventWebinarId -VirtualEventSessionId $virtualEventSessionId -MeetingAttendanceReportId $meetingAttendanceReportId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.virtual_events.webinars.by_virtual_event_webinar_id('virtualEventWebinar-id').sessions.by_virtual_event_session_id('virtualEventSession-id').attendance_reports.by_meeting_attendance_report_id('meetingAttendanceReport-id').attendance_records.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#solutions/virtualEvents/webinars('336f94f4-3a81-5130-43e9-88f3-fcb3582cde37')/sessions('8d62dd52-4dff-4c75-96a9-f905cc3ff942')/attendanceReports('2c2454-7613-4d6e-9c7c-4c8')/attendanceRecords",
  "value": [
    {
      "emailAddress": "frederick.cormier@contoso.com",
      "totalAttendanceInSeconds": 322,
      "role": "Organizer",
      "registrantId": null,
      "registrationId": null,
      "identity": {
        "id": "dc17674c-81d9-4adb-bfb2-8f6a442e4623",
        "displayName": "Frederick Cormier",
        "tenantId": null
      },
      "attendanceIntervals": [
        {
          "joinDateTime": "2021-10-05T04:38:27.6027225Z",
          "leaveDateTime": "2021-10-05T04:43:49.7702391Z",
          "durationInSeconds": 322
        }
      ],
      "externalRegistrationInformation": {
        "referrer": "Fabrikam",
        "registrationId": "myExternalRegistrationId"
      }
    },
    {
      "emailAddress": "lisa.adkins@contoso.com",
      "totalAttendanceInSeconds": 314,
      "role": "Presenter",
      "registrantId": null,
      "registrationId": null,
      "identity": {
        "id": "57caaef9-5ed0-48d5-8862-e5abfa71b3e9",
        "displayName": "Lisa Adkins",
        "tenantId": null
      },
      "attendanceIntervals": [
        {
          "joinDateTime": "2021-10-04T23:13:43.3776519Z",
          "leaveDateTime": "2021-10-04T23:18:57.5639338Z",
          "durationInSeconds": 314
        }
      ],
      "externalRegistrationInformation": {
        "referrer": "Fabrikam",
        "registrationId": "anotherExternalRegistrationId"
      }
    }
  ]
}
```

### Example 3: List attendance records for the attendance report of a town hall session

The following example shows how to get a list of attendance records for the attendance report of a town hall session.

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
GET https://graph.microsoft.com/v1.0/solutions/virtualEvents/townhalls/f8ce2a5f-0e6a-4186-aa90-1f64bc023566/sessions/8d62dd52-4dff-4c75-96a9-f905cc3ff942/attendanceReports/2c2454-7613-4d6e-9c7c-4c8/attendanceRecords
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Townhalls["{virtualEventTownhall-id}"].Sessions["{virtualEventSession-id}"].AttendanceReports["{meetingAttendanceReport-id}"].AttendanceRecords.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
attendanceRecords, err := graphClient.Solutions().VirtualEvents().Townhalls().ByVirtualEventTownhallId("virtualEventTownhall-id").Sessions().ByVirtualEventSessionId("virtualEventSession-id").AttendanceReports().ByMeetingAttendanceReportId("meetingAttendanceReport-id").AttendanceRecords().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

AttendanceRecordCollectionResponse result = graphClient.solutions().virtualEvents().townhalls().byVirtualEventTownhallId("{virtualEventTownhall-id}").sessions().byVirtualEventSessionId("{virtualEventSession-id}").attendanceReports().byMeetingAttendanceReportId("{meetingAttendanceReport-id}").attendanceRecords().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let attendanceRecords = await client.api('/solutions/virtualEvents/townhalls/f8ce2a5f-0e6a-4186-aa90-1f64bc023566/sessions/8d62dd52-4dff-4c75-96a9-f905cc3ff942/attendanceReports/2c2454-7613-4d6e-9c7c-4c8/attendanceRecords')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->virtualEvents()->townhalls()->byVirtualEventTownhallId('virtualEventTownhall-id')->sessions()->byVirtualEventSessionId('virtualEventSession-id')->attendanceReports()->byMeetingAttendanceReportId('meetingAttendanceReport-id')->attendanceRecords()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

Get-MgVirtualEventTownhallSessionAttendanceReportAttendanceRecord -VirtualEventTownhallId $virtualEventTownhallId -VirtualEventSessionId $virtualEventSessionId -MeetingAttendanceReportId $meetingAttendanceReportId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.virtual_events.townhalls.by_virtual_event_townhall_id('virtualEventTownhall-id').sessions.by_virtual_event_session_id('virtualEventSession-id').attendance_reports.by_meeting_attendance_report_id('meetingAttendanceReport-id').attendance_records.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#solutions/virtualEvents/townhalls('8ce2a5f-0e6a-4186-aa90-1f64bc023566')/sessions('8d62dd52-4dff-4c75-96a9-f905cc3ff942')/attendanceReports('2c2454-7613-4d6e-9c7c-4c8')/attendancerecords",
   "value": [
    {
      "emailAddress": "frederick.cormier@contoso.com",
      "totalAttendanceInSeconds": 322,
      "role": "Organizer",
      "registrantId": null,
      "registrationId": null,
      "identity": {
        "id": "dc17674c-81d9-4adb-bfb2-8f6a442e4623",
        "displayName": "Frederick Cormier",
        "tenantId": null
      },
      "attendanceIntervals": [
        {
          "joinDateTime": "2021-10-05T04:38:27.6027225Z",
          "leaveDateTime": "2021-10-05T04:43:49.7702391Z",
          "durationInSeconds": 322
        }
      ]
    },
    {
      "emailAddress": "lisa.adkins@contoso.com",
      "totalAttendanceInSeconds": 314,
      "role": "Presenter",
      "registrantId": null,
      "registrationId": null,
      "identity": {
        "id": "57caaef9-5ed0-48d5-8862-e5abfa71b3e9",
        "displayName": "Lisa Adkins",
        "tenantId": null
      },
      "attendanceIntervals": [
        {
          "joinDateTime": "2021-10-04T23:13:43.3776519Z",
          "leaveDateTime": "2021-10-04T23:18:57.5639338Z",
          "durationInSeconds": 314
        }
      ]
    }
  ]
}
```
