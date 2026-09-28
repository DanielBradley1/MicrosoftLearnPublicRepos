<!-- Source: https://learn.microsoft.com/en-us/graph/api/onlinemeeting-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-20 -->

# Update onlineMeeting

Namespace: microsoft.graph

Update the properties of the specified [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object.

For the list of properties that support updating, see the [Request body](#request-body) section.

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
PATCH /me/onlineMeetings/{meetingId}
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Permissions for the following HTTP request:

```http
PATCH /users/{userId}/onlineMeetings/{meetingId}
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OnlineMeetings.ReadWrite.All | Not available. |

Note

To use application permission for this API, tenant administrators must create an [application access policy](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy) and grant it to a user to authorize the app configured in the policy to update online meetings on behalf of that user \(with user ID specified in the request path\).

## HTTP request

To update the specified **onlineMeeting** using meeting ID with delegated \(`/me`\) and app \(`/users/{userId}/`\) permission:

```http
PATCH /me/onlineMeetings/{meetingId}
PATCH /users/{userId}/onlineMeetings/{meetingId}
```

Note

- `userId` is the object ID of a user in the [Microsoft Entra admin center > user management page](https://entra.microsoft.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade). For more information, see [application access policy](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).
- `meetingId` is the **id** of an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

The following table lists the properties that can be updated. In the request body, supply *only* the values for properties that should be updated, with the following exceptions:

- Adjusting the start or end date/time of an online meeting always requires both **startDateTime** and **endDateTime** properties in the request body.
- The **organizer** field of the **participants** property can't be updated. The organizer of the meeting can't be modified after the meeting is created.
- Adjusting the **attendees** field of the **participants** property, such as adding or removing an attendee to the meeting, always requires the full list of attendees in the request body.

The last column indicates whether updating this property will take effect for an in-progress meeting.

| Property | Type | Description | Applies to in-progress meetings? |
| --- | --- | --- | --- |
| allowAttendeeToEnableCamera | Boolean | Indicates whether attendees can turn on their camera. | Yes |
| allowAttendeeToEnableMic | Boolean | Indicates whether attendees can turn on their microphone. | Yes |
| allowBreakoutRooms | Boolean | Indicates whether breakout rooms are enabled for the meeting. | No |
| allowCopyingAndSharingMeetingContent | Boolean | Indicates whether the ability to copy and share meeting content is enabled for the meeting. | Yes |
| allowedLobbyAdmitters | [allowedLobbyAdmitterRoles](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0#allowedlobbyadmitterroles-values) | Specifies the users who can admit from the lobby. The possible values are: `organizerAndCoOrganizersAndPresenters`, `organizerAndCoOrganizers`, `unknownFutureValue`. | Yes |
| allowedPresenters | onlineMeetingPresenters | Specifies who can be a presenter in a meeting. | Yes |
| allowLiveShare | meetingLiveShareOptions | Indicates whether live share is enabled for the meeting. | No |
| allowMeetingChat | meetingChatMode | Specifies the mode of meeting chat. | Yes |
| allowPowerPointSharing | Boolean | Indicates whether PowerPoint live is enabled for the meeting. | No |
| allowRecording | Boolean | Indicates whether recording is enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). | Yes |
| allowTeamworkReactions | Boolean | Indicates whether Teams reactions are enabled for the meeting. | Yes |
| allowTranscription | Boolean | Indicates whether transcription is enabled for the meeting. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). | Yes |
| allowWhiteboard | Boolean | Indicates whether whiteboard is enabled for the meeting. | No |
| anonymizeIdentityForRoles | onlineMeetingRole collection | Specifies whose identity is anonymized in the meeting. The possible values are: `attendee`. The `attendee` value can't be removed through a PATCH operation once added. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). | No |
| endDateTime | DateTime | The meeting end time in UTC. | No |
| isEndToEndEncryptionEnabled | Boolean | Indicates whether end-to-end encryption \(E2EE\) is enabled for the meeting. | No |
| isEntryExitAnnounced | Boolean | Whether or not to announce when callers join or leave. | Yes |
| lobbyBypassSettings | [lobbyBypassSettings](https://learn.microsoft.com/en-us/graph/api/resources/lobbybypasssettings?view=graph-rest-1.0) | Specifies which participants can bypass the meeting lobby. | Yes |
| meetingSpokenLanguageTag | String | Specifies the spoken language used during the meeting for recording and transcription purposes. | No |
| participants | [meetingParticipants](https://learn.microsoft.com/en-us/graph/api/resources/meetingparticipants?view=graph-rest-1.0) | The participants associated with the online meeting. Only attendees can be updated. | No |
| recordAutomatically | Boolean | Indicates whether to record the meeting automatically. | No |
| sensitivityLabelAssignment | [onlineMeetingSensitivityLabelAssignment](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingsensitivitylabelassignment?view=graph-rest-1.0) | Specifies the sensitivity label applied to the Teams meeting. | No |
| startDateTime | DateTime | The meeting start time in UTC. | No |
| subject | String | The subject of the online meeting. | No |
| watermarkProtection | [watermarkProtectionValues](https://learn.microsoft.com/en-us/graph/api/resources/watermarkprotectionvalues?view=graph-rest-1.0) | Specifies whether the client application should apply a watermark to a content type. Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). Inherited from [onlineMeetingBase](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingbase?view=graph-rest-1.0). | No |
| broadcastSettings \(deprecated\) | [broadcastMeetingSettings](https://learn.microsoft.com/en-us/graph/api/resources/broadcastmeetingsettings?view=graph-rest-1.0) | Settings related to a live event. | No |

Note

- For the list of possible values for **allowedPresenters**, **allowLiveShare**, and **allowMeetingChat**, see [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0).
- When updating the value of **allowedPresenters** to `roleIsPresenter`, include a full list of **attendees** with specified attendees' **role** set to `presenter` in the request body.

## Response

If successful, this method returns a `200 OK` response code and an updated [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update the startDateTime, endDateTime and subject

#### Request

> **Note:** The meeting ID has been shortened for readability.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi
Content-Type: application/json 

{
  "startDateTime": "2020-09-09T14:33:30.8546353-07:00",
  "endDateTime": "2020-09-09T15:03:30.8566356-07:00",
  "subject": "Patch Meeting Subject",
  "meetingSpokenLanguageTag": "en-US"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	StartDateTime = DateTimeOffset.Parse("2020-09-09T14:33:30.8546353-07:00"),
	EndDateTime = DateTimeOffset.Parse("2020-09-09T15:03:30.8566356-07:00"),
	Subject = "Patch Meeting Subject",
	MeetingSpokenLanguageTag = "en-US",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].PatchAsync(requestBody);
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
startDateTime , err := time.Parse(time.RFC3339, "2020-09-09T14:33:30.8546353-07:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2020-09-09T15:03:30.8566356-07:00")
requestBody.SetEndDateTime(&endDateTime) 
subject := "Patch Meeting Subject"
requestBody.SetSubject(&subject) 
meetingSpokenLanguageTag := "en-US"
requestBody.SetMeetingSpokenLanguageTag(&meetingSpokenLanguageTag) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
OffsetDateTime startDateTime = OffsetDateTime.parse("2020-09-09T14:33:30.8546353-07:00");
onlineMeeting.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2020-09-09T15:03:30.8566356-07:00");
onlineMeeting.setEndDateTime(endDateTime);
onlineMeeting.setSubject("Patch Meeting Subject");
onlineMeeting.setMeetingSpokenLanguageTag("en-US");
OnlineMeeting result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").patch(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  startDateTime: '2020-09-09T14:33:30.8546353-07:00',
  endDateTime: '2020-09-09T15:03:30.8566356-07:00',
  subject: 'Patch Meeting Subject',
  meetingSpokenLanguageTag: 'en-US'
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi')
	.update(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$requestBody->setStartDateTime(new \DateTime('2020-09-09T14:33:30.8546353-07:00'));
$requestBody->setEndDateTime(new \DateTime('2020-09-09T15:03:30.8566356-07:00'));
$requestBody->setSubject('Patch Meeting Subject');
$requestBody->setMeetingSpokenLanguageTag('en-US');

$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	startDateTime = [System.DateTime]::Parse("2020-09-09T14:33:30.8546353-07:00")
	endDateTime = [System.DateTime]::Parse("2020-09-09T15:03:30.8566356-07:00")
	subject = "Patch Meeting Subject"
	meetingSpokenLanguageTag = "en-US"
}

# A UPN can also be used as -UserId.
Update-MgUserOnlineMeeting -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	start_date_time = "2020-09-09T14:33:30.8546353-07:00",
	end_date_time = "2020-09-09T15:03:30.8566356-07:00",
	subject = "Patch Meeting Subject",
	meeting_spoken_language_tag = "en-US",
)

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "id":"MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi",
   "creationDateTime":"2020-07-03T00:23:39.444642Z",
   "startDateTime":"2020-09-09T21:33:30.8546353Z",
   "endDateTime":"2020-09-09T22:03:30.8566356Z",
   "joinWebUrl":"url",
   "subject":"Patch Meeting Subject",
   "isBroadcast":false,
   "autoAdmittedUsers":"EveryoneInCompany",
   "participants":{
      "organizer":{
         "upn":"upn",
         "role": "presenter",
         "identity":{
            "azureApplicationInstance":null,
            "applicationInstance":null,
            "application":null,
            "device":null,
            "user":{
               "id":"8716745d-77a9-4be3-afff-009e4b81658e",
               "displayName":null,
               "tenantId":"0823831b-1f1b-424b-b90a-1caa345a742a",
               "identityProvider":"AAD"
            }
         }
      }
   },
    "sensitivityLabelAssignment": {
      "sensitivityLabelId": "c7f2d7a7-6a36-4a41-9a6b-0d2761a9f4f0"
    },
    "meetingSpokenLanguageTag": "en-US",
    "audioConferencing":{
      "conferenceId":"id",
      "tollNumber":"+1-900-555-0100",
      "tollFreeNumber":"+1-800-555-0100",
      "dialinUrl":"url"
   }
}
```

#### Example 2: Update the lobbyBypassSettings

> **Note:** The meeting ID has been shortened for readability.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi
Content-Type: application/json 

{
  "lobbyBypassSettings": {
      "isDialInBypassEnabled": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	LobbyBypassSettings = new LobbyBypassSettings
	{
		IsDialInBypassEnabled = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewOnlineMeeting()
lobbyBypassSettings := graphmodels.NewLobbyBypassSettings()
isDialInBypassEnabled := true
lobbyBypassSettings.SetIsDialInBypassEnabled(&isDialInBypassEnabled) 
requestBody.SetLobbyBypassSettings(lobbyBypassSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
LobbyBypassSettings lobbyBypassSettings = new LobbyBypassSettings();
lobbyBypassSettings.setIsDialInBypassEnabled(true);
onlineMeeting.setLobbyBypassSettings(lobbyBypassSettings);
OnlineMeeting result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").patch(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  lobbyBypassSettings: {
      isDialInBypassEnabled: true
  }
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi')
	.update(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;
use Microsoft\Graph\Generated\Models\LobbyBypassSettings;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$lobbyBypassSettings = new LobbyBypassSettings();
$lobbyBypassSettings->setIsDialInBypassEnabled(true);
$requestBody->setLobbyBypassSettings($lobbyBypassSettings);

$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	lobbyBypassSettings = @{
		isDialInBypassEnabled = $true
	}
}

# A UPN can also be used as -UserId.
Update-MgUserOnlineMeeting -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
from msgraph.generated.models.lobby_bypass_settings import LobbyBypassSettings
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	lobby_bypass_settings = LobbyBypassSettings(
		is_dial_in_bypass_enabled = True,
	),
)

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi",
    "creationDateTime":"2020-07-03T00:23:39.444642Z",
    "startDateTime":"2020-09-09T21:33:30.8546353Z",
    "endDateTime":"2020-09-09T22:03:30.8566356Z",
    "joinWebUrl":"(redacted)",
    "subject":"Patch Meeting Subject",
    "autoAdmittedUsers": "EveryoneInCompany",
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
        "attendees": [],
    },
    "sensitivityLabelAssignment": {
      "sensitivityLabelId": "c7f2d7a7-6a36-4a41-9a6b-0d2761a9f4f0"
    },
    "meetingSpokenLanguageTag": "en-US",
    "lobbyBypassSettings": {
        "scope": "organization",
        "isDialInBypassEnabled": true
    }
}
```

### Example 3: Enable end-to-end encryption on an existing online meeting

The following example shows how to enable end-to-end encryption on an existing online meeting.

> **Note:** The **isEndToEndEncryptionEnabled** property must be used with Teams policies to determine the final behavior, and policy updates can take up to 24 hours to apply. For more information, see [Require end-to-end encryption for sensitive Teams meetings](https://learn.microsoft.com/en-us/microsoftteams/end-to-end-encrypted-meetings).

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
PATCH https://graph.microsoft.com/v1.0/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi
Content-Type: application/json 

{
  "isEndToEndEncryptionEnabled": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OnlineMeeting
{
	IsEndToEndEncryptionEnabled = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewOnlineMeeting()
isEndToEndEncryptionEnabled := true
requestBody.SetIsEndToEndEncryptionEnabled(&isEndToEndEncryptionEnabled) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
onlineMeetings, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OnlineMeeting onlineMeeting = new OnlineMeeting();
onlineMeeting.setIsEndToEndEncryptionEnabled(true);
OnlineMeeting result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").patch(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
  isEndToEndEncryptionEnabled: true
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi')
	.update(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\OnlineMeeting;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OnlineMeeting();
$requestBody->setIsEndToEndEncryptionEnabled(true);

$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	isEndToEndEncryptionEnabled = $true
}

# A UPN can also be used as -UserId.
Update-MgUserOnlineMeeting -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.online_meeting import OnlineMeeting
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OnlineMeeting(
	is_end_to_end_encryption_enabled = True,
)

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "id": "MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZi",
  "creationDateTime": "2020-07-03T00:23:39.444642Z",
  "startDateTime": "2020-09-09T21:33:30.8546353Z",
  "endDateTime": "2020-09-09T22:03:30.8566356Z",
  "joinWebUrl": "(redacted)",
  "subject": "Patch Meeting Subject",
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
  "sensitivityLabelAssignment": {
    "sensitivityLabelId": "c7f2d7a7-6a36-4a41-9a6b-0d2761a9f4f0"
  },
  "meetingSpokenLanguageTag": "en-US",
  "lobbyBypassSettings": {
    "scope": "organization",
    "isDialInBypassEnabled": true
  }
}
```
