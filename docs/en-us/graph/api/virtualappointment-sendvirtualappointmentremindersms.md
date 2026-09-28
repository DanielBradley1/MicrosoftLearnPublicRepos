<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualappointment-sendvirtualappointmentremindersms?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# virtualAppointment: sendVirtualAppointmentReminderSms

Namespace: microsoft.graph

Send an SMS reminder to external attendees for a Teams virtual appointment. This feature requires [Teams premium](https://learn.microsoft.com/en-us/microsoftteams/teams-add-on-licensing/licensing-enhance-teams) and attendees must have a valid United States phone number to receive SMS notifications.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | VirtualAppointmentNotification.Send | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/onlineMeetings/{onlineMeetingId}/sendVirtualAppointmentReminderSms
POST /users/{userId}/onlineMeetings/{onlineMeetingId}/sendVirtualAppointmentReminderSms
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept-Language | Language. Optional. |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| attendees | [attendeeNotificationInfo](https://learn.microsoft.com/en-us/graph/api/resources/attendeenotificationinfo?view=graph-rest-1.0) collection | Represents the phone number and time zone of an external attendee. Required. |
| remindBeforeTimeInMinutesType | [remindBeforeTimeInMinutesType](https://learn.microsoft.com/en-us/graph/api/resources/remindbeforetimeinminutestype?view=graph-rest-1.0) collection | Represents the reminder time interval. Required. |

## Response

If successful, this method returns a `202 Accepted` response code.

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
POST https://graph.microsoft.com/v1.0/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/sendVirtualAppointmentReminderSms

{ 
    "attendees": [ 
        {
            "phoneNumber":  "+13129224122",
            "timeZone": "Pacific Standard Time"
        },
        {
            "phoneNumber":  "+1242421412",
            "timeZone": "Eastern Standard Time"
        }
    ], 
    "remindBeforeTimeInMinutesType": "mins15"
} 
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.OnlineMeetings.Item.SendVirtualAppointmentReminderSms;
using Microsoft.Graph.Models;

var requestBody = new SendVirtualAppointmentReminderSmsPostRequestBody
{
	Attendees = new List<AttendeeNotificationInfo>
	{
		new AttendeeNotificationInfo
		{
			PhoneNumber = "+13129224122",
			TimeZone = "Pacific Standard Time",
		},
		new AttendeeNotificationInfo
		{
			PhoneNumber = "+1242421412",
			TimeZone = "Eastern Standard Time",
		},
	},
	RemindBeforeTimeInMinutesType = RemindBeforeTimeInMinutesType.Mins15,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].SendVirtualAppointmentReminderSms.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemSendVirtualAppointmentReminderSmsPostRequestBody()


attendeeNotificationInfo := graphmodels.NewAttendeeNotificationInfo()
phoneNumber := "+13129224122"
attendeeNotificationInfo.SetPhoneNumber(&phoneNumber) 
timeZone := "Pacific Standard Time"
attendeeNotificationInfo.SetTimeZone(&timeZone) 
attendeeNotificationInfo1 := graphmodels.NewAttendeeNotificationInfo()
phoneNumber := "+1242421412"
attendeeNotificationInfo1.SetPhoneNumber(&phoneNumber) 
timeZone := "Eastern Standard Time"
attendeeNotificationInfo1.SetTimeZone(&timeZone) 

attendees := []graphmodels.AttendeeNotificationInfoable {
	attendeeNotificationInfo,
	attendeeNotificationInfo1,
}
requestBody.SetAttendees(attendees)
remindBeforeTimeInMinutesType := graphmodels.MINS15_REMINDBEFORETIMEINMINUTESTYPE 
requestBody.SetRemindBeforeTimeInMinutesType(&remindBeforeTimeInMinutesType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").SendVirtualAppointmentReminderSms().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.onlinemeetings.item.sendvirtualappointmentremindersms.SendVirtualAppointmentReminderSmsPostRequestBody sendVirtualAppointmentReminderSmsPostRequestBody = new com.microsoft.graph.users.item.onlinemeetings.item.sendvirtualappointmentremindersms.SendVirtualAppointmentReminderSmsPostRequestBody();
LinkedList<AttendeeNotificationInfo> attendees = new LinkedList<AttendeeNotificationInfo>();
AttendeeNotificationInfo attendeeNotificationInfo = new AttendeeNotificationInfo();
attendeeNotificationInfo.setPhoneNumber("+13129224122");
attendeeNotificationInfo.setTimeZone("Pacific Standard Time");
attendees.add(attendeeNotificationInfo);
AttendeeNotificationInfo attendeeNotificationInfo1 = new AttendeeNotificationInfo();
attendeeNotificationInfo1.setPhoneNumber("+1242421412");
attendeeNotificationInfo1.setTimeZone("Eastern Standard Time");
attendees.add(attendeeNotificationInfo1);
sendVirtualAppointmentReminderSmsPostRequestBody.setAttendees(attendees);
sendVirtualAppointmentReminderSmsPostRequestBody.setRemindBeforeTimeInMinutesType(RemindBeforeTimeInMinutesType.Mins15);
graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").sendVirtualAppointmentReminderSms().post(sendVirtualAppointmentReminderSmsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendVirtualAppointmentReminderSms = {
    attendees: [ 
        {
            phoneNumber: '+13129224122',
            timeZone: 'Pacific Standard Time'
        },
        {
            phoneNumber: '+1242421412',
            timeZone: 'Eastern Standard Time'
        }
    ], 
    remindBeforeTimeInMinutesType: 'mins15'
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/sendVirtualAppointmentReminderSms')
	.post(sendVirtualAppointmentReminderSms);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\OnlineMeetings\Item\SendVirtualAppointmentReminderSms\SendVirtualAppointmentReminderSmsPostRequestBody;
use Microsoft\Graph\Generated\Models\AttendeeNotificationInfo;
use Microsoft\Graph\Generated\Models\RemindBeforeTimeInMinutesType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendVirtualAppointmentReminderSmsPostRequestBody();
$attendeesAttendeeNotificationInfo1 = new AttendeeNotificationInfo();
$attendeesAttendeeNotificationInfo1->setPhoneNumber('+13129224122');
$attendeesAttendeeNotificationInfo1->setTimeZone('Pacific Standard Time');
$attendeesArray []= $attendeesAttendeeNotificationInfo1;
$attendeesAttendeeNotificationInfo2 = new AttendeeNotificationInfo();
$attendeesAttendeeNotificationInfo2->setPhoneNumber('+1242421412');
$attendeesAttendeeNotificationInfo2->setTimeZone('Eastern Standard Time');
$attendeesArray []= $attendeesAttendeeNotificationInfo2;
$requestBody->setAttendees($attendeesArray);

$requestBody->setRemindBeforeTimeInMinutesType(new RemindBeforeTimeInMinutesType('mins15'));

$graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->sendVirtualAppointmentReminderSms()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	attendees = @(
		@{
			phoneNumber = "+13129224122"
			timeZone = "Pacific Standard Time"
		}
		@{
			phoneNumber = "+1242421412"
			timeZone = "Eastern Standard Time"
		}
	)
	remindBeforeTimeInMinutesType = "mins15"
}

# A UPN can also be used as -UserId.
Send-MgUserOnlineMeetingVirtualAppointmentReminderSm -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.onlinemeetings.item.send_virtual_appointment_reminder_sms.send_virtual_appointment_reminder_sms_post_request_body import SendVirtualAppointmentReminderSmsPostRequestBody
from msgraph.generated.models.attendee_notification_info import AttendeeNotificationInfo
from msgraph.generated.models.remind_before_time_in_minutes_type import RemindBeforeTimeInMinutesType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendVirtualAppointmentReminderSmsPostRequestBody(
	attendees = [
		AttendeeNotificationInfo(
			phone_number = "+13129224122",
			time_zone = "Pacific Standard Time",
		),
		AttendeeNotificationInfo(
			phone_number = "+1242421412",
			time_zone = "Eastern Standard Time",
		),
	],
	remind_before_time_in_minutes_type = RemindBeforeTimeInMinutesType.Mins15,
)

await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').send_virtual_appointment_reminder_sms.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted

{}
```
