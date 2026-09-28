<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualappointment-sendvirtualappointmentsms?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# virtualAppointment: sendVirtualAppointmentSms

Namespace: microsoft.graph

Send an SMS notification to external attendees when a Teams virtual appointment is confirmed, rescheduled, or canceled. This feature requires [Teams premium](https://learn.microsoft.com/en-us/microsoftteams/teams-add-on-licensing/licensing-enhance-teams). Attendees must have a valid United States phone number to receive these SMS notifications.

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
POST /me/onlineMeetings/{onlineMeetingId}/sendVirtualAppointmentSms
POST /users/{userId}/onlineMeetings/{onlineMeetingId}/sendVirtualAppointmentSms
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept-Language | Language. Optional. |

## Request body

In the request body, supply a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| attendees | [attendeeNotificationInfo](https://learn.microsoft.com/en-us/graph/api/resources/attendeenotificationinfo?view=graph-rest-1.0) collection | Represents the phone number and time zone of an external attendee. Required. |
| messageType | [virtualAppointmentMessageType](https://learn.microsoft.com/en-us/graph/api/resources/virtualappointmentmessagetype?view=graph-rest-1.0) collection | Indicates the type of SMS notification to send. The possible values are: `confirmation`, `reschedule`, and `cancellation`. Required. |

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
POST https://graph.microsoft.com/v1.0/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/sendVirtualAppointmentSms

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
    "messageType": "confirmation"
} 
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.OnlineMeetings.Item.SendVirtualAppointmentSms;
using Microsoft.Graph.Models;

var requestBody = new SendVirtualAppointmentSmsPostRequestBody
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
	MessageType = VirtualAppointmentMessageType.Confirmation,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].SendVirtualAppointmentSms.PostAsync(requestBody);
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

requestBody := graphusers.NewItemSendVirtualAppointmentSmsPostRequestBody()


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
messageType := graphmodels.CONFIRMATION_VIRTUALAPPOINTMENTMESSAGETYPE 
requestBody.SetMessageType(&messageType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").SendVirtualAppointmentSms().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.onlinemeetings.item.sendvirtualappointmentsms.SendVirtualAppointmentSmsPostRequestBody sendVirtualAppointmentSmsPostRequestBody = new com.microsoft.graph.users.item.onlinemeetings.item.sendvirtualappointmentsms.SendVirtualAppointmentSmsPostRequestBody();
LinkedList<AttendeeNotificationInfo> attendees = new LinkedList<AttendeeNotificationInfo>();
AttendeeNotificationInfo attendeeNotificationInfo = new AttendeeNotificationInfo();
attendeeNotificationInfo.setPhoneNumber("+13129224122");
attendeeNotificationInfo.setTimeZone("Pacific Standard Time");
attendees.add(attendeeNotificationInfo);
AttendeeNotificationInfo attendeeNotificationInfo1 = new AttendeeNotificationInfo();
attendeeNotificationInfo1.setPhoneNumber("+1242421412");
attendeeNotificationInfo1.setTimeZone("Eastern Standard Time");
attendees.add(attendeeNotificationInfo1);
sendVirtualAppointmentSmsPostRequestBody.setAttendees(attendees);
sendVirtualAppointmentSmsPostRequestBody.setMessageType(VirtualAppointmentMessageType.Confirmation);
graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").sendVirtualAppointmentSms().post(sendVirtualAppointmentSmsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendVirtualAppointmentSms = {
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
    messageType: 'confirmation'
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi/sendVirtualAppointmentSms')
	.post(sendVirtualAppointmentSms);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\OnlineMeetings\Item\SendVirtualAppointmentSms\SendVirtualAppointmentSmsPostRequestBody;
use Microsoft\Graph\Generated\Models\AttendeeNotificationInfo;
use Microsoft\Graph\Generated\Models\VirtualAppointmentMessageType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendVirtualAppointmentSmsPostRequestBody();
$attendeesAttendeeNotificationInfo1 = new AttendeeNotificationInfo();
$attendeesAttendeeNotificationInfo1->setPhoneNumber('+13129224122');
$attendeesAttendeeNotificationInfo1->setTimeZone('Pacific Standard Time');
$attendeesArray []= $attendeesAttendeeNotificationInfo1;
$attendeesAttendeeNotificationInfo2 = new AttendeeNotificationInfo();
$attendeesAttendeeNotificationInfo2->setPhoneNumber('+1242421412');
$attendeesAttendeeNotificationInfo2->setTimeZone('Eastern Standard Time');
$attendeesArray []= $attendeesAttendeeNotificationInfo2;
$requestBody->setAttendees($attendeesArray);

$requestBody->setMessageType(new VirtualAppointmentMessageType('confirmation'));

$graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->sendVirtualAppointmentSms()->post($requestBody)->wait();
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
	messageType = "confirmation"
}

# A UPN can also be used as -UserId.
Send-MgUserOnlineMeetingVirtualAppointmentSm -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.onlinemeetings.item.send_virtual_appointment_sms.send_virtual_appointment_sms_post_request_body import SendVirtualAppointmentSmsPostRequestBody
from msgraph.generated.models.attendee_notification_info import AttendeeNotificationInfo
from msgraph.generated.models.virtual_appointment_message_type import VirtualAppointmentMessageType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendVirtualAppointmentSmsPostRequestBody(
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
	message_type = VirtualAppointmentMessageType.Confirmation,
)

await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').send_virtual_appointment_sms.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted

{}
```
