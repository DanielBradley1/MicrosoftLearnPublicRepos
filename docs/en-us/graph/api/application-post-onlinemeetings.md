<!-- Source: https://learn.microsoft.com/en-us/graph/api/application-post-onlinemeetings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create onlineMeeting

Namespace: microsoft.graph

Create an online meeting on behalf of a user.

Tip

- This API creates a standalone meeting that isn't associated with any event on the user's calendar; therefore, meetings created via this API aren't shown on the user's calendar.
- This API doesn't create a Teams live event.
- To be able to retrieve meeting transcripts at a later stage, use the [Create event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0#example-4-create-and-enable-an-event-as-an-online-meeting) API that is calendar-backed.

Note

If you invite a contact list of more than 150 members to a meeting, they can only access the chat during the meeting. If some people in the contact list are required attendees and the rest are optional, add them directly as participants. If you add a contact list that makes the chat exceed 1,000 people, you aren't able to add the list. For more information, see [Chat in Microsoft Teams meetings](https://support.microsoft.com/office/chat-in-microsoft-teams-meetings-64e2cb91-8a11-4781-94ea-fbb23f2b922f).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Permissions for the following HTTP request:

```http
POST /me/onlineMeetings
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Permissions for the following HTTP request:

```http
POST /users/{userId}/onlineMeetings
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OnlineMeetings.ReadWrite.All | Not available. |

Note

To use application permission for this API, tenant administrators must create an [application access policy](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy) and grant it to a user to authorize the app configured in the policy to create online meetings on behalf of that user \(with user ID specified in the request path\).

## HTTP request

To create an online meeting with delegated \(`/me`\) and app \(`/users/{userId}`\) permission:

```http
POST /me/onlineMeetings
POST /users/{userId}/onlineMeetings
```

Note

- **userId** is the object ID of a user in [Microsoft Entra admin center > user management page](https://entra.microsoft.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade). For more details, see [Allow applications to access online meetings on behalf of a user](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| Accept-Language | Language. Optional. |

If the request contains an `Accept-Language` HTTP header, the `content` of `joinInformation` will be in the language and locale variant specified in the `Accept-Language` header. The default content is in English.

## Request body

In the request body, supply a JSON representation of an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object.

Caution

Assigning the `presenter` or `coorganizer` role to users who aren't registered in Microsoft Entra ID isn't currently supported.

## Response

If successful, this method returns a `201 Created` response code and an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Create an online meeting with user token

The following example creates an online meeting with a user token.

#### Request

Here's an example of a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/onlineMeetings
Content-Type: application/json

{
  "startDateTime":"2019-07-12T14:30:34.2444915-07:00",
  "endDateTime":"2019-07-12T15:00:34.2464912-07:00",
  "subject":"User Token Meeting"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	StartDateTime = DateTimeOffset.Parse("2019-07-12T14:30:34.2444915-07:00"),
	EndDateTime = DateTimeOffset.Parse("2019-07-12T15:00:34.2464912-07:00"),
	Subject = "User Token Meeting",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOnlineMeeting()
startDateTime , err := time.Parse(time.RFC3339, "2019-07-12T14:30:34.2444915-07:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2019-07-12T15:00:34.2464912-07:00")
requestBody.SetEndDateTime(&endDateTime) 
subject := "User Token Meeting"
requestBody.SetSubject(&subject) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
OffsetDateTime startDateTime = OffsetDateTime.parse("2019-07-12T14:30:34.2444915-07:00");
onlineMeeting.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2019-07-12T15:00:34.2464912-07:00");
onlineMeeting.setEndDateTime(endDateTime);
onlineMeeting.setSubject("User Token Meeting");
OnlineMeeting result = graphClient.me().onlineMeetings().post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  startDateTime: '2019-07-12T14:30:34.2444915-07:00',
  endDateTime: '2019-07-12T15:00:34.2464912-07:00',
  subject: 'User Token Meeting'
};

await client.api('/me/onlineMeetings')
	.post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$requestBody->setStartDateTime(new \DateTime('2019-07-12T14:30:34.2444915-07:00'));
$requestBody->setEndDateTime(new \DateTime('2019-07-12T15:00:34.2464912-07:00'));
$requestBody->setSubject('User Token Meeting');

$result = $graphServiceClient->me()->onlineMeetings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	startDateTime = [System.DateTime]::Parse("2019-07-12T14:30:34.2444915-07:00")
	endDateTime = [System.DateTime]::Parse("2019-07-12T15:00:34.2464912-07:00")
	subject = "User Token Meeting"
}

# A UPN can also be used as -UserId.
New-MgUserOnlineMeeting -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	start_date_time = "2019-07-12T14:30:34.2444915-07:00",
	end_date_time = "2019-07-12T15:00:34.2464912-07:00",
	subject = "User Token Meeting",
)

result = await graph_client.me.online_meetings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Here's an example of the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.onlineMeeting",
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('f4053e7-85f4-f0389ac980d6')/onlineMeetings/$entity",
  "audioConferencing": {
    "tollNumber": "+1252578",
    "tollFreeNumber": "+18588",
    "ConferenceId": "24999",
    "dialinUrl": "https://dialin.teams.microsoft.com/22f12faf--bc69-b8de580ba330?id=24299"
  },
  "chatInfo": {
    "threadId": "19:meeting_M2IzYzczNTItYzUtYmFiMjNlOTY4MGEz@thread.skype",
    "messageId": "0",
    "replyChainMessageId": "0"
  },
  "creationDateTime": "2019-07-11T02:17:17.6491364Z",
  "startDateTime": "2019-07-11T02:17:17.6491364Z",
  "endDateTime": "2019-07-11T02:47:17.651138Z",
  "id": "MSpkYzE3NjctYmZiMi04ZdFpHRTNaR1F6WGhyZWFkLnYy",
  "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_M2IzYzczNTItYmY3OC00MDlmLWJjMzUtYmFiMjNlOTY4MGEz%40thread.skype/0?context=%7b%22Tid%22%3a%2272f988bf-87cd011db47%22%2c%22Oid%22%3a%22550fae72-d251-43ec-868c-373732c2704f%22%7d",
  "participants": {
    "organizer": {
      "identity": {
        "user": {
          "id": "550fae72-d25-868c-373732c2704f",
          "displayName": "Heidi Steen"
        }
      },
      "upn": "upn-value"
    }
  },
  "subject": "User Token Meeting",
  "joinMeetingIdSettings": {
    "isPasscodeRequired": false,
    "joinMeetingId": "1234567890",
    "passcode": null
  },
  "meetingSpokenLanguageTag": "en-US"
}
```

Note

If 'Accept-Language: ja' is specified to indicate Japanese, for example, the response will include the following.

```json
    "joinInformation": {
        "content": "data%3Atext%2Fhtml%2C%0A++%3Cdiv+style%3D%22width%3A100%25%3Bheight%3A+20px%3B%22%3E%0A%09%09%3Cspan+style%3D%22white-space%3Anowrap%3Bcolor%3Agray%3Bopacity%3A.36%3B%22%3E________________________________________________________________________________%3C%2Fspan%3E%0A%09+%3C%2Fdiv%3E%0A++++%3Cdiv+class%3D%22me-email-text%22+style%3D%22color%3A%23252424%3Bfont-family%3A'Segoe+UI'%2C'Helvetica+Neue'%2CHelvetica%2CArial%2Csans-serif%3B%22%3E%0A+++%3Cdiv+style%3D%22margin-top%3A+24px%3B+margin-bottom%3A+10px%3B%22%3E%0A++++++++%3Ca+class%3D%22me-email-headline%22%0A++++++++++++++style%3D%22font-size%3A+18px%3Bfont-family%3A'Segoe+UI+Semibold'%2C'Segoe+UI'%2C'Helvetica+Neue'%2CHelvetica%2CArial%2Csans-serif%3Btext-decoration%3A+underline%3Bcolor%3A+%236264a7%3B%22%0A++++++++++++++href%3D%22https%3A%2F%2Fteams.microsoft.com%2Fl%2Fmeetup-join%2F19%253ameeting_NDRiZjRiMmUtODI5OC00MzRlLTk1ZWEtMGY1000000000000%2540thread.v2%2F0%3Fcontext%3D%257b%2522Tid%2522%253a%252279a788bf-86f1-41af-91ab-000000000000%2522%252c%2522Oid%2522%253a%2522d4a060b5-a8fc-450c-837b-000000000000%2522%257d%22%0A++++++++++++++target%3D%22_blank%22+rel%3D%22noreferrer+noopener%22%3EMicrosoft+Teams+%E4%BC%9A%E8%AD%B0%E3%81%AB%E5%8F%82%E5%8A%A0%3C%2Fa%3E%0A++++++%3C%2Fdiv%3E%0A%09+%3Cdiv%3E%0A++++%0A++++++%3Cdiv%3E%0A++++++++%3Ca+class%3D%22me-email-link%22+style%3D%22font-size%3A+14px%3Btext-decoration%3A+none%3Bcolor%3A+%236264a7%3B%22%0A++++++++++href%3D%22tel%3A%2B16477490000%2C%2C11160000%26%2335%3B+%22+target%3D%22_blank%22+rel%3D%22noreferrer+noopener%22%3E%2B16477490000%3C%2Fa%3E%0A++++++%3Cspan+style%3D%22font-size%3A+12px%3B%22%3E%26nbsp%3B++(%E6%9C%89%E6%96%99)+%3C%2Fspan%3E%0A++++++%3C%2Fdiv%3E%0A++++%0A++%3C%2Fdiv%3E%0A%0A%09+%0A++++++%3Cdiv+style%3D%22margin-top%3A+10px%3B+margin-bottom%3A+20px%3B%22%3E%0A++++++++%3Cspan+style%3D%22font-size%3A+12px%3B%22%3E%0A++++++++++%E4%BC%9A%E8%AD%B0+ID%3A%0A++++++++%3C%2Fspan%3E%0A++++++%3Cspan+style%3D%22font-size%3A+14px%3B%22%3E%0A++++++++111+000+00%23%0A++++++%3C%2Fspan%3E%0A++++%3C%2Fdiv%3E%0A++++%0A%09+%0A++++++++%3Cdiv+style%3D%22margin-bottom%3A+24px%3B%22%3E%0A++++++++++++++%3Ca+class%3D%22me-email-link%22+style%3D%22font-size%3A+12px%3Btext-decoration%3A+none%3Bcolor%3A+%236264a7%3B%22+target%3D%22_blank%22+href%3D%22https%3A%2F%2Fdialin.teams.microsoft.com%2F8bf6e654-57eb-4b85-aeaf-36c84429b2fe%3Fid%3D11160000%22+rel%3D%22noreferrer+noopener%22%3E%E6%9C%80%E5%AF%84%E3%82%8A%E3%81%AE%E5%9B%BD%E3%81%AE%E9%9B%BB%E8%A9%B1%E7%95%AA%E5%8F%B7%E3%82%92%E6%A4%9C%E7%B4%A2%3C%2Fa%3E%0A+++++++++%7C%0A++++++++++++++%3Ca+class%3D%22me-email-link%22+style%3D%22font-size%3A+12px%3Btext-decoration%3A+none%3Bcolor%3A+%236264a7%3B%22+target%3D%22_blank%22+href%3D%22https%3A%2F%2Fmysettings.lync.com%2Fpstnconferencing%22+rel%3D%22noreferrer+noopener%22%3E%0A++++++++PIN+%E3%82%92%E3%83%AA%E3%82%BB%E3%83%83%E3%83%88%3C%2Fa%3E%0A+++++++++%7C+%3Ca+class%3D%22me-email-link%22+style%3D%22font-size%3A+12px%3Btext-decoration%3A+none%3Bcolor%3A+%236264a7%3B%22+target%3D%22_blank%22+href%3D%22https%3A%2F%2Faka.ms%2FJoinTeamsMeeting%22+rel%3D%22noreferrer+noopener%22%3ETeams+%E3%81%AE%E8%A9%B3%E7%B4%B0%E3%82%92%E8%A1%A8%E7%A4%BA%3C%2Fa%3E%0A+++++%7C+%3Ca+class%3D%22me-email-link%22+style%3D%22font-size%3A+12px%3Btext-decoration%3A+none%3Bcolor%3A+%236264a7%3B%22+target%3D%22_blank%22+href%3D%22https%3A%2F%2Fteams.microsoft.com%2FmeetingOptions%2F%3ForganizerId%3Dd4a060b5-a8fc-450c-837b-000000000000%26tenantId%3D79a788bf-86f1-41af-91ab-000000000000%26threadId%3D19_meeting_NDRiZjRiMmUtODI5OC00MzRlLTk1ZWEtMGY1000000000000%40thread.v2%26messageId%3D0%26language%3Dja%22+rel%3D%22noreferrer+noopener%22%3E%E4%BC%9A%E8%AD%B0%E3%81%AE%E3%82%AA%E3%83%97%E3%82%B7%E3%83%A7%E3%83%B3%3C%2Fa%3E%0A++++%0A++++++++%3C%2Fdiv%3E%0A++++%0A+++++%0A++++++++%3Cdiv+style%3D%22font-size%3A+14px%3B+margin-bottom%3A+4px%3B%22%3E%0A++++++++++++%E3%83%93%E3%83%87%E3%82%AA%E4%BC%9A%E8%AD%B0%E3%83%87%E3%83%90%E3%82%A4%E3%82%B9%E3%81%A7%E5%8F%82%E5%8A%A0%0A++++++++%3C%2Fdiv%3E%0A%0A++++++++%3Cdiv+style%3D%22font-size%3A12px%3B+margin-bottom%3A+4px%3B%22%3E%0A++++++++++++%3Ca+class%3D%22me-email-link%22+style%3D%22text-decoration%3A+none%3Bcolor%3A+%236264a7%3B%22+href%3D%22%22%3E000000000%40t.abcd.vc%3C%2Fa%3E+VTC+%E4%BC%9A%E8%AD%B0+ID%3A+0180300000%0A++++++++%3C%2Fdiv%3E%0A%0A++++++++%3Cdiv+style%3D%22font-size%3A+12px%3B+margin-bottom%3A+20px%3B%22%3E%0A++++++++%3Ca+class%3D%22me-email-link%22+style%3D%22text-decoration%3A+none%3Bcolor%3A+%236264a7%3B%22+href%3D%22https%3A%2F%2Fdialin.abcd.vc%2Fteams%2F%3Fkey%3D000000000%26conf%3D0180308922%22%3E%E4%BB%A3%E6%9B%BF+VTC+%E3%81%AE%E3%83%80%E3%82%A4%E3%83%A4%E3%83%AB%E6%96%B9%E6%B3%95%3C%2Fa%3E%0A++++++++%3C%2Fdiv%3E%0A++++%0A+++++%0A++++++%3Cdiv+style%3D%22font-size%3A+14px%3B+margin-bottom%3A+4px%3B%22%3E%0A++++++++%0A++++++%3C%2Fdiv%3E%0A++++++%3Cdiv+style%3D%22font-size%3A+12px%3B%22%3E%0A++++++%0A++++++%3C%2Fdiv%3E%0A++++%0A+++++%3C%2Fdiv%3E%0A%09+%3Cdiv+style%3D%22width%3A100%25%3Bheight%3A+20px%3B%22%3E%0A%09%09%3Cspan+style%3D%22white-space%3Anowrap%3Bcolor%3Agray%3Bopacity%3A.36%3B%22%3E________________________________________________________________________________%3C%2Fspan%3E%0A++%3C%2Fdiv%3E%22%2C%0A",
        "contentType": "Html"
    }  
```

### Example 2: Create an online meeting that requires a passcode

The following example shows how to add a passcode to a meeting. The passcode is used when you join a meeting with a **joinMeetingId**. For more information, see [joinMeetingIdSettings](https://learn.microsoft.com/en-us/graph/api/resources/joinmeetingidsettings?view=graph-rest-1.0).

#### Request

Here's an example of a request.

> **Note:** The passcode is automatically generated and a custom passcode isn't supported.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/onlineMeetings
Content-Type: application/json

{
  "startDateTime":"2019-07-12T14:30:34.2444915-07:00",
  "endDateTime":"2019-07-12T15:00:34.2464912-07:00",
  "subject":"User meeting",
  "joinMeetingIdSettings": {
    "isPasscodeRequired": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	StartDateTime = DateTimeOffset.Parse("2019-07-12T14:30:34.2444915-07:00"),
	EndDateTime = DateTimeOffset.Parse("2019-07-12T15:00:34.2464912-07:00"),
	Subject = "User meeting",
	JoinMeetingIdSettings = new JoinMeetingIdSettings
	{
		IsPasscodeRequired = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOnlineMeeting()
startDateTime , err := time.Parse(time.RFC3339, "2019-07-12T14:30:34.2444915-07:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2019-07-12T15:00:34.2464912-07:00")
requestBody.SetEndDateTime(&endDateTime) 
subject := "User meeting"
requestBody.SetSubject(&subject) 
joinMeetingIdSettings := graphmodels.NewJoinMeetingIdSettings()
isPasscodeRequired := true
joinMeetingIdSettings.SetIsPasscodeRequired(&isPasscodeRequired) 
requestBody.SetJoinMeetingIdSettings(joinMeetingIdSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
OffsetDateTime startDateTime = OffsetDateTime.parse("2019-07-12T14:30:34.2444915-07:00");
onlineMeeting.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2019-07-12T15:00:34.2464912-07:00");
onlineMeeting.setEndDateTime(endDateTime);
onlineMeeting.setSubject("User meeting");
JoinMeetingIdSettings joinMeetingIdSettings = new JoinMeetingIdSettings();
joinMeetingIdSettings.setIsPasscodeRequired(true);
onlineMeeting.setJoinMeetingIdSettings(joinMeetingIdSettings);
OnlineMeeting result = graphClient.me().onlineMeetings().post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  startDateTime: '2019-07-12T14:30:34.2444915-07:00',
  endDateTime: '2019-07-12T15:00:34.2464912-07:00',
  subject: 'User meeting',
  joinMeetingIdSettings: {
    isPasscodeRequired: true
  }
};

await client.api('/me/onlineMeetings')
	.post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;
use Microsoft\Graph\Generated\Models\JoinMeetingIdSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$requestBody->setStartDateTime(new \DateTime('2019-07-12T14:30:34.2444915-07:00'));
$requestBody->setEndDateTime(new \DateTime('2019-07-12T15:00:34.2464912-07:00'));
$requestBody->setSubject('User meeting');
$joinMeetingIdSettings = new JoinMeetingIdSettings();
$joinMeetingIdSettings->setIsPasscodeRequired(true);
$requestBody->setJoinMeetingIdSettings($joinMeetingIdSettings);

$result = $graphServiceClient->me()->onlineMeetings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	startDateTime = [System.DateTime]::Parse("2019-07-12T14:30:34.2444915-07:00")
	endDateTime = [System.DateTime]::Parse("2019-07-12T15:00:34.2464912-07:00")
	subject = "User meeting"
	joinMeetingIdSettings = @{
		isPasscodeRequired = $true
	}
}

# A UPN can also be used as -UserId.
New-MgUserOnlineMeeting -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
from msgraph.generated.models.join_meeting_id_settings import JoinMeetingIdSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	start_date_time = "2019-07-12T14:30:34.2444915-07:00",
	end_date_time = "2019-07-12T15:00:34.2464912-07:00",
	subject = "User meeting",
	join_meeting_id_settings = JoinMeetingIdSettings(
		is_passcode_required = True,
	),
)

result = await graph_client.me.online_meetings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

Here's an example of the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('f4086-17cc-42e7-85f4-f03880d6')/onlineMeetings/$entity",
  "audioConferencing": {
    "tollNumber": "+12525478",
    "tollFreeNumber": "+18690588",
    "ConferenceId": "2999",
    "dialinUrl": "https://dialin.teams.microsoft.com/22fa0-499f-435b-bc69-b8dea330?id=2999"
  },
  "chatInfo": {
    "threadId": "19%3A3b523985568b776357c1dd79%40thread.skype",
    "messageId": "15629053",
    "replyChainMessageId": null
  },
  "creationDateTime": "2019-07-11T02:17:17.6491364Z",
  "startDateTime": "2019-07-11T02:17:17.6491364Z",
  "endDateTime": "2019-07-11T02:47:17.651138Z",
  "id": "MSpkYzE3Njc0Yy04MWQ5LTRhFpHRTNaR1F6WGhyZWFkLnYy",
  "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_M2IzYzczNTItYmY3iMjNlOTY4MGEz%40thread.skype/0?context=%7b%22Tid%22%3a%22f8bf-86f1-41af-91ab-2011db47%22%2c%22Oid%22%3a%20fae72-d251-43ec-86c-377304f%22%7d",
  "participants": {
    "organizer": {
      "identity": {
        "user": {
          "id": "5e72-d251-43ec-868c-3732704f",
          "tenantId": "72fbf-86f1-41af-91ab-2d71db47",
          "displayName": "Mario Rogers"
        }
      },
      "role": "presenter",
      "upn": "upn-value"
    }
  },
  "subject": "User meeting",
  "joinMeetingIdSettings": {
    "isPasscodeRequired": true,
    "joinMeetingId": "1234567890",
    "passcode": "123abc"
  }
}
```

### Example 3: Create an online meeting that doesn't require a passcode

When **isPasscodeRequired** is set to `false` or when **joinMeetingIdSettings** isn't specified in the request, the generated online meeting won't have a passcode.

#### Request

Here's an example of a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/me/onlineMeetings
Content-Type: application/json

{
  "startDateTime":"2019-07-12T14:30:34.2444915-07:00",
  "endDateTime":"2019-07-12T15:00:34.2464912-07:00",
  "subject":"User meeting in Microsoft Teams channel.",
  "joinMeetingIdSettings": {
    "isPasscodeRequired": false
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	StartDateTime = DateTimeOffset.Parse("2019-07-12T14:30:34.2444915-07:00"),
	EndDateTime = DateTimeOffset.Parse("2019-07-12T15:00:34.2464912-07:00"),
	Subject = "User meeting in Microsoft Teams channel.",
	JoinMeetingIdSettings = new JoinMeetingIdSettings
	{
		IsPasscodeRequired = false,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOnlineMeeting()
startDateTime , err := time.Parse(time.RFC3339, "2019-07-12T14:30:34.2444915-07:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2019-07-12T15:00:34.2464912-07:00")
requestBody.SetEndDateTime(&endDateTime) 
subject := "User meeting in Microsoft Teams channel."
requestBody.SetSubject(&subject) 
joinMeetingIdSettings := graphmodels.NewJoinMeetingIdSettings()
isPasscodeRequired := false
joinMeetingIdSettings.SetIsPasscodeRequired(&isPasscodeRequired) 
requestBody.SetJoinMeetingIdSettings(joinMeetingIdSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
OffsetDateTime startDateTime = OffsetDateTime.parse("2019-07-12T14:30:34.2444915-07:00");
onlineMeeting.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2019-07-12T15:00:34.2464912-07:00");
onlineMeeting.setEndDateTime(endDateTime);
onlineMeeting.setSubject("User meeting in Microsoft Teams channel.");
JoinMeetingIdSettings joinMeetingIdSettings = new JoinMeetingIdSettings();
joinMeetingIdSettings.setIsPasscodeRequired(false);
onlineMeeting.setJoinMeetingIdSettings(joinMeetingIdSettings);
OnlineMeeting result = graphClient.me().onlineMeetings().post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  startDateTime: '2019-07-12T14:30:34.2444915-07:00',
  endDateTime: '2019-07-12T15:00:34.2464912-07:00',
  subject: 'User meeting in Microsoft Teams channel.',
  joinMeetingIdSettings: {
    isPasscodeRequired: false
  }
};

await client.api('/me/onlineMeetings')
	.post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;
use Microsoft\Graph\Generated\Models\JoinMeetingIdSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$requestBody->setStartDateTime(new \DateTime('2019-07-12T14:30:34.2444915-07:00'));
$requestBody->setEndDateTime(new \DateTime('2019-07-12T15:00:34.2464912-07:00'));
$requestBody->setSubject('User meeting in Microsoft Teams channel.');
$joinMeetingIdSettings = new JoinMeetingIdSettings();
$joinMeetingIdSettings->setIsPasscodeRequired(false);
$requestBody->setJoinMeetingIdSettings($joinMeetingIdSettings);

$result = $graphServiceClient->me()->onlineMeetings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	startDateTime = [System.DateTime]::Parse("2019-07-12T14:30:34.2444915-07:00")
	endDateTime = [System.DateTime]::Parse("2019-07-12T15:00:34.2464912-07:00")
	subject = "User meeting in Microsoft Teams channel."
	joinMeetingIdSettings = @{
		isPasscodeRequired = $false
	}
}

# A UPN can also be used as -UserId.
New-MgUserOnlineMeeting -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
from msgraph.generated.models.join_meeting_id_settings import JoinMeetingIdSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	start_date_time = "2019-07-12T14:30:34.2444915-07:00",
	end_date_time = "2019-07-12T15:00:34.2464912-07:00",
	subject = "User meeting in Microsoft Teams channel.",
	join_meeting_id_settings = JoinMeetingIdSettings(
		is_passcode_required = False,
	),
)

result = await graph_client.me.online_meetings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

OR

```http
POST https://graph.microsoft.com/v1.0/me/onlineMeetings
Content-Type: application/json

{
  "startDateTime":"2019-07-12T14:30:34.2444915-07:00",
  "endDateTime":"2019-07-12T15:00:34.2464912-07:00",
  "subject":"User meeting in Microsoft Teams channel."
}
```

#### Response

Here's an example of the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('f4053f86-17cc-85f4-f0389ac980d6')/onlineMeetings/$entity",
  "audioConferencing": {
    "tollNumber": "+12525478",
    "tollFreeNumber": "+186390588",
    "ConferenceId": "24999",
    "dialinUrl": "https://dialin.teams.microsoft.com/22f12fa0-45b-bc69-b8de580ba330?id=2425999"
  },
  "chatInfo": {
    "threadId": "19%3A3b52398f3c524556894b776357c1dd79%40thread.skype",
    "messageId": "1563302249053",
    "replyChainMessageId": null
  },
  "creationDateTime": "2019-07-11T02:17:17.6491364Z",
  "startDateTime": "2019-07-11T02:17:17.6491364Z",
  "endDateTime": "2019-07-11T02:47:17.651138Z",
  "id": "MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZiMi04ZdFpHRTNaR1F6WGhyZWFkLnYy",
  "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_M2IzYzczNTItYmY3OC00MDlmLWJjMzUtYmFiMjNlOTY4MGEz%40thread.skype/0?context=%7b%22Tid%22%3a%2272f988bf-86f1-1ab-2d7cd011db47%22%2c%22Oid%22%3a%22550fae72-d251-c-373732c2704f%22%7d",
  "participants": {
    "organizer": {
      "identity": {
        "user": {
          "id": "550fae72-d251-43ecc-373732c2704f",
          "tenantId": "72f98841af-91ab-2d7cd011db47",
          "displayName": "Tyler Stein"
        }
      },
      "role": "presenter",
      "upn": "upn-value"
    }
  },
  "subject": "User meeting in Microsoft Teams channel.",
  "joinMeetingIdSettings": {
    "isPasscodeRequired": false,
    "joinMeetingId": "1234567890",
    "passcode": null
  }
}
```

### Example 4: Create an online meeting with a meeting template

The following example shows how to create a meeting with a Microsoft Teams [meeting template](https://learn.microsoft.com/en-us/microsoftteams/create-custom-meeting-template). Microsoft Teams custom meeting templates allow you to specify values for many of the meeting options that are available to meeting organizers.

Caution

- The template might lock some meeting options in the Teams UI. The enforcement of the lock takes place on the server side.
- Subsequent updates to the **onlineMeeting** can't overwrite the **meetingTemplateId** or locked meeting options.
- Using a custom meeting template to create a meeting is a Teams Premium feature.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/me/onlineMeetings
Content-Type: application/json

{
  "startDateTime": "2019-07-12T14:30:34.2444915-07:00",
  "endDateTime": "2019-07-12T15:00:34.2464912-07:00",
  "subject": "User meeting",
  "meetingTemplateId": "05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	StartDateTime = DateTimeOffset.Parse("2019-07-12T14:30:34.2444915-07:00"),
	EndDateTime = DateTimeOffset.Parse("2019-07-12T15:00:34.2464912-07:00"),
	Subject = "User meeting",
	MeetingTemplateId = "05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOnlineMeeting()
startDateTime , err := time.Parse(time.RFC3339, "2019-07-12T14:30:34.2444915-07:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2019-07-12T15:00:34.2464912-07:00")
requestBody.SetEndDateTime(&endDateTime) 
subject := "User meeting"
requestBody.SetSubject(&subject) 
meetingTemplateId := "05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b"
requestBody.SetMeetingTemplateId(&meetingTemplateId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
OffsetDateTime startDateTime = OffsetDateTime.parse("2019-07-12T14:30:34.2444915-07:00");
onlineMeeting.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2019-07-12T15:00:34.2464912-07:00");
onlineMeeting.setEndDateTime(endDateTime);
onlineMeeting.setSubject("User meeting");
onlineMeeting.setMeetingTemplateId("05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b");
OnlineMeeting result = graphClient.me().onlineMeetings().post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  startDateTime: '2019-07-12T14:30:34.2444915-07:00',
  endDateTime: '2019-07-12T15:00:34.2464912-07:00',
  subject: 'User meeting',
  meetingTemplateId: '05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b'
};

await client.api('/me/onlineMeetings')
	.post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$requestBody->setStartDateTime(new \DateTime('2019-07-12T14:30:34.2444915-07:00'));
$requestBody->setEndDateTime(new \DateTime('2019-07-12T15:00:34.2464912-07:00'));
$requestBody->setSubject('User meeting');
$requestBody->setMeetingTemplateId('05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b');

$result = $graphServiceClient->me()->onlineMeetings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	startDateTime = [System.DateTime]::Parse("2019-07-12T14:30:34.2444915-07:00")
	endDateTime = [System.DateTime]::Parse("2019-07-12T15:00:34.2464912-07:00")
	subject = "User meeting"
	meetingTemplateId = "05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b"
}

# A UPN can also be used as -UserId.
New-MgUserOnlineMeeting -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	start_date_time = "2019-07-12T14:30:34.2444915-07:00",
	end_date_time = "2019-07-12T15:00:34.2464912-07:00",
	subject = "User meeting",
	meeting_template_id = "05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b",
)

result = await graph_client.me.online_meetings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('xxxxxxxx')/onlineMeetings/$entity",
  "audioConferencing": {
    "tollNumber": "+12345678",
    "tollFreeNumber": "+12345",
    "ConferenceId": "1234",
    "dialinUrl": "https://dialin.teams.microsoft.com/xxxxxxx?id=2999"
  },
  "chatInfo": {
    "threadId": "1xxxxxxxxxxxxxx%40thread.skype",
    "messageId": "15629053",
    "replyChainMessageId": null
  },
  "creationDateTime": "2019-07-11T02:17:17.6491364Z",
  "startDateTime": "2019-07-11T02:17:17.6491364Z",
  "endDateTime": "2019-07-11T02:47:17.651138Z",
  "id": "MSpkYzE3Njc0Yy04MWQ5LTRhFpHRTNaR1F6WGhyZWFkLnYy",
  "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_M2IzYzczNTItYmY3iMjNlOTY4MGEz%40thread.skype/0?context=%7b%22Tid%22%3a%22f8bf-86f1-41af-91ab-2011db47%22%2c%22Oid%22%3a%20fae72-d251-43ec-86c-377304f%22%7d",
  "participants": {
    "organizer": {
      "identity": {
        "user": {
          "id": "5e72-d251-43ec-868c-3732704f",
          "tenantId": "72fbf-86f1-41af-91ab-2d71db47",
          "displayName": "Mario Rogers"
        }
      },
      "role": "presenter",
      "upn": "upn-value"
    }
  },
  "subject": "User meeting",
  "meetingTemplateId": "05b9ed5f-2ac3-4470-aae9-f4a0c30b1a4b"
}
```

### Example 5: Create an encrypted online meeting

The following example shows how to create an online meeting that is end-to-end encrypted.

> **Note:** The **isEndToEndEncryptionEnabled** property must be used with Teams policies to determine the final behavior, and policy updates can take up to 24 hours to apply. For more information, see [Require end-to-end encryption for sensitive Teams meetings](https://learn.microsoft.com/en-us/microsoftteams/end-to-end-encrypted-meetings).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
POST https://graph.microsoft.com/v1.0/me/onlineMeetings
Content-Type: application/json 

{
  "startDateTime":"2025-02-01T14:30:34.2444915-07:00",
  "endDateTime":"2025-02-01T15:00:34.2464912-07:00",
  "subject":"Encrypted Meeting",
  "isEndToEndEncryptionEnabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	StartDateTime = DateTimeOffset.Parse("2025-02-01T14:30:34.2444915-07:00"),
	EndDateTime = DateTimeOffset.Parse("2025-02-01T15:00:34.2464912-07:00"),
	Subject = "Encrypted Meeting",
	IsEndToEndEncryptionEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewOnlineMeeting()
startDateTime , err := time.Parse(time.RFC3339, "2025-02-01T14:30:34.2444915-07:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2025-02-01T15:00:34.2464912-07:00")
requestBody.SetEndDateTime(&endDateTime) 
subject := "Encrypted Meeting"
requestBody.SetSubject(&subject) 
isEndToEndEncryptionEnabled := true
requestBody.SetIsEndToEndEncryptionEnabled(&isEndToEndEncryptionEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
OffsetDateTime startDateTime = OffsetDateTime.parse("2025-02-01T14:30:34.2444915-07:00");
onlineMeeting.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2025-02-01T15:00:34.2464912-07:00");
onlineMeeting.setEndDateTime(endDateTime);
onlineMeeting.setSubject("Encrypted Meeting");
onlineMeeting.setIsEndToEndEncryptionEnabled(true);
OnlineMeeting result = graphClient.me().onlineMeetings().post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  startDateTime: '2025-02-01T14:30:34.2444915-07:00',
  endDateTime: '2025-02-01T15:00:34.2464912-07:00',
  subject: 'Encrypted Meeting',
  isEndToEndEncryptionEnabled: true
};

await client.api('/me/onlineMeetings')
	.post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$requestBody->setStartDateTime(new \DateTime('2025-02-01T14:30:34.2444915-07:00'));
$requestBody->setEndDateTime(new \DateTime('2025-02-01T15:00:34.2464912-07:00'));
$requestBody->setSubject('Encrypted Meeting');
$requestBody->setIsEndToEndEncryptionEnabled(true);

$result = $graphServiceClient->me()->onlineMeetings()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	startDateTime = [System.DateTime]::Parse("2025-02-01T14:30:34.2444915-07:00")
	endDateTime = [System.DateTime]::Parse("2025-02-01T15:00:34.2464912-07:00")
	subject = "Encrypted Meeting"
	isEndToEndEncryptionEnabled = $true
}

# A UPN can also be used as -UserId.
New-MgUserOnlineMeeting -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	start_date_time = "2025-02-01T14:30:34.2444915-07:00",
	end_date_time = "2025-02-01T15:00:34.2464912-07:00",
	subject = "Encrypted Meeting",
	is_end_to_end_encryption_enabled = True,
)

result = await graph_client.me.online_meetings.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi",
  "creationDateTime": "2020-07-03T00:23:39.444642Z",
  "startDateTime": "2025-02-01T14:30:34.2444915-07:00",
  "endDateTime": "2025-02-01T15:00:34.2464912-07:00",
  "joinWebUrl": "(redacted)",
  "subject": "Encrypted Meeting",
  "autoAdmittedUsers": "EveryoneInCompany",
  "isEndToEndEncryptionEnabled": true,
  "isEntryExitAnnounced": true,
  "allowedPresenters": "everyone",
  "videoTeleconferenceId": "(redacted)",
  "participants": {
    "organizer": {
      "upn": "(redacted)",
      "role": "presenter",
      "identity": {
        "user": {
          "id": "dc17674c-81d9-4adb-bfb2-8f6a442e4622",
          "displayName": null,
          "tenantId": "909c6581-5130-43e9-88f3-fcb3582cde38",
          "identityProvider": "AAD"
        }
      }
    },
    "attendees": []
  },
  "lobbyBypassSettings": {
    "scope": "organization",
    "isDialInBypassEnabled": true
  }
}
```
