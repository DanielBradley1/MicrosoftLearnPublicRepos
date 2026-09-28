<!-- Source: https://learn.microsoft.com/en-us/graph/api/onlinemeeting-createorget?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# onlineMeeting: createOrGet

Namespace: microsoft.graph

Create an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object with a custom specified external ID. If the external ID already exists, this API will return the [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object with that external ID.

> **Note**: The meeting doesn't show on the user's calendar.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | OnlineMeetings.ReadWrite.All\* |

Important

\* Administrators must create an [application access policy](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy) and grant it to a user, authorizing the app configured in the policy to create or get an online meeting with external ID on behalf of that user \(user ID specified in the request path\).

## HTTP request

To call **createOrGet** API with delegated token:

```http
POST /me/onlineMeetings/createOrGet
```

To call **createOrGet** API with application token:

```http
POST /users/{userId}/onlineMeetings/createOrGet
```

Note

**userId** is the object ID of a user in [Microsoft Entra admin center > user management page](https://entra.microsoft.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade). See more details in [application access policy](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTime | The meeting end time in UTC. |
| externalId | String | The external ID. A custom ID. \(Required\) |
| participants | [meetingParticipants](https://learn.microsoft.com/en-us/graph/api/resources/meetingparticipants?view=graph-rest-1.0) | The participants associated with the online meeting. This includes the organizer and the attendees. |
| startDateTime | DateTime | The meeting start time in UTC. |
| subject | String | The subject of the online meeting. |

> **Notes:**
> 
> - If the **startDateTime** and **endDateTime** are not provided, the **startDateTime** will default to the current dateTime value and **endDateTime** value will equal the **startDateTime** + 1 hour.
> - If the **startDateTime** is provided, but **endDateTime** is not, the **endDateTime** value will equal the **startDateTime** + 1 hour.
> - An error is thrown if the **endDateTime** is provided without the **startDateTime** or if the **endDateTime** is earlier than the **startDateTime**.
> - When multiple users within the same tenant use the same **externalId** to run this query, different meeting instances are generated, each with its own unique ID. The combination of **tenantId**, **userId**, and **externalId** serves as the identifier for a meeting with an external ID.

## Response

If successful, this method returns a `201 Created` response code if a new meeting is created, or a `200 OK` response code if an existing meeting is retrieved. In both cases, an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) object is returned in the response body.

## Examples

### Request

The following example shows how to create or get an online meeting with an external ID.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/onlineMeetings/createOrGet
Content-Type: application/json

{
    "startDateTime": "2020-02-06T01:49:21.3524945+00:00",
    "endDateTime": "2020-02-06T02:19:21.3524945+00:00",
    "subject": "Create a meeting with customId provided",
    "externalId": "7eb8263f-d0e0-4149-bb1c-1f0476083c56",
    "participants": {
        "attendees": [
            {
                "identity": {
                    "user": {
                        "id": "1f35f2e6-9cab-44ad-8d5a-b74c14720000"
                    }
                },
                "upn": "test1@contoso.com"
            }
        ]
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.OnlineMeetings.CreateOrGet;
using Microsoft.Graph.Models;

var requestBody = new CreateOrGetPostRequestBody
{
	StartDateTime = DateTimeOffset.Parse("2020-02-06T01:49:21.3524945+00:00"),
	EndDateTime = DateTimeOffset.Parse("2020-02-06T02:19:21.3524945+00:00"),
	Subject = "Create a meeting with customId provided",
	ExternalId = "7eb8263f-d0e0-4149-bb1c-1f0476083c56",
	Participants = new MeetingParticipants
	{
		Attendees = new List<MeetingParticipantInfo>
		{
			new MeetingParticipantInfo
			{
				Identity = new IdentitySet
				{
					User = new Identity
					{
						Id = "1f35f2e6-9cab-44ad-8d5a-b74c14720000",
					},
				},
				Upn = "test1@contoso.com",
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings.CreateOrGet.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemCreateOrGetPostRequestBody()
startDateTime , err := time.Parse(time.RFC3339, "2020-02-06T01:49:21.3524945+00:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2020-02-06T02:19:21.3524945+00:00")
requestBody.SetEndDateTime(&endDateTime) 
subject := "Create a meeting with customId provided"
requestBody.SetSubject(&subject) 
externalId := "7eb8263f-d0e0-4149-bb1c-1f0476083c56"
requestBody.SetExternalId(&externalId) 
participants := graphmodels.NewMeetingParticipants()


meetingParticipantInfo := graphmodels.NewMeetingParticipantInfo()
identity := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
id := "1f35f2e6-9cab-44ad-8d5a-b74c14720000"
user.SetId(&id) 
identity.SetUser(user)
meetingParticipantInfo.SetIdentity(identity)
upn := "test1@contoso.com"
meetingParticipantInfo.SetUpn(&upn) 

attendees := []graphmodels.MeetingParticipantInfoable {
	meetingParticipantInfo,
}
participants.SetAttendees(attendees)
requestBody.SetParticipants(participants)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
createOrGet, err := graphClient.Me().OnlineMeetings().CreateOrGet().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.onlinemeetings.createorget.CreateOrGetPostRequestBody createOrGetPostRequestBody = new com.microsoft.graph.users.item.onlinemeetings.createorget.CreateOrGetPostRequestBody();
OffsetDateTime startDateTime = OffsetDateTime.parse("2020-02-06T01:49:21.3524945+00:00");
createOrGetPostRequestBody.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2020-02-06T02:19:21.3524945+00:00");
createOrGetPostRequestBody.setEndDateTime(endDateTime);
createOrGetPostRequestBody.setSubject("Create a meeting with customId provided");
createOrGetPostRequestBody.setExternalId("7eb8263f-d0e0-4149-bb1c-1f0476083c56");
MeetingParticipants participants = new MeetingParticipants();
LinkedList<MeetingParticipantInfo> attendees = new LinkedList<MeetingParticipantInfo>();
MeetingParticipantInfo meetingParticipantInfo = new MeetingParticipantInfo();
IdentitySet identity = new IdentitySet();
Identity user = new Identity();
user.setId("1f35f2e6-9cab-44ad-8d5a-b74c14720000");
identity.setUser(user);
meetingParticipantInfo.setIdentity(identity);
meetingParticipantInfo.setUpn("test1@contoso.com");
attendees.add(meetingParticipantInfo);
participants.setAttendees(attendees);
createOrGetPostRequestBody.setParticipants(participants);
var result = graphClient.me().onlineMeetings().createOrGet().post(createOrGetPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const onlineMeeting = {
    startDateTime: '2020-02-06T01:49:21.3524945+00:00',
    endDateTime: '2020-02-06T02:19:21.3524945+00:00',
    subject: 'Create a meeting with customId provided',
    externalId: '7eb8263f-d0e0-4149-bb1c-1f0476083c56',
    participants: {
        attendees: [
            {
                identity: {
                    user: {
                        id: '1f35f2e6-9cab-44ad-8d5a-b74c14720000'
                    }
                },
                upn: 'test1@contoso.com'
            }
        ]
    }
};

await client.api('/me/onlineMeetings/createOrGet')
	.post(onlineMeeting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\OnlineMeetings\CreateOrGet\CreateOrGetPostRequestBody;
use Microsoft\Graph\Generated\Models\MeetingParticipants;
use Microsoft\Graph\Generated\Models\MeetingParticipantInfo;
use Microsoft\Graph\Generated\Models\IdentitySet;
use Microsoft\Graph\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CreateOrGetPostRequestBody();
$requestBody->setStartDateTime(new \DateTime('2020-02-06T01:49:21.3524945+00:00'));
$requestBody->setEndDateTime(new \DateTime('2020-02-06T02:19:21.3524945+00:00'));
$requestBody->setSubject('Create a meeting with customId provided');
$requestBody->setExternalId('7eb8263f-d0e0-4149-bb1c-1f0476083c56');
$participants = new MeetingParticipants();
$attendeesMeetingParticipantInfo1 = new MeetingParticipantInfo();
$attendeesMeetingParticipantInfo1Identity = new IdentitySet();
$attendeesMeetingParticipantInfo1IdentityUser = new Identity();
$attendeesMeetingParticipantInfo1IdentityUser->setId('1f35f2e6-9cab-44ad-8d5a-b74c14720000');
$attendeesMeetingParticipantInfo1Identity->setUser($attendeesMeetingParticipantInfo1IdentityUser);
$attendeesMeetingParticipantInfo1->setIdentity($attendeesMeetingParticipantInfo1Identity);
$attendeesMeetingParticipantInfo1->setUpn('test1@contoso.com');
$attendeesArray []= $attendeesMeetingParticipantInfo1;
$participants->setAttendees($attendeesArray);

$requestBody->setParticipants($participants);

$result = $graphServiceClient->me()->onlineMeetings()->createOrGet()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.onlinemeetings.create_or_get.create_or_get_post_request_body import CreateOrGetPostRequestBody
from msgraph.generated.models.meeting_participants import MeetingParticipants
from msgraph.generated.models.meeting_participant_info import MeetingParticipantInfo
from msgraph.generated.models.identity_set import IdentitySet
from msgraph.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CreateOrGetPostRequestBody(
	start_date_time = "2020-02-06T01:49:21.3524945+00:00",
	end_date_time = "2020-02-06T02:19:21.3524945+00:00",
	subject = "Create a meeting with customId provided",
	external_id = "7eb8263f-d0e0-4149-bb1c-1f0476083c56",
	participants = MeetingParticipants(
		attendees = [
			MeetingParticipantInfo(
				identity = IdentitySet(
					user = Identity(
						id = "1f35f2e6-9cab-44ad-8d5a-b74c14720000",
					),
				),
				upn = "test1@contoso.com",
			),
		],
	),
)

result = await graph_client.me.online_meetings.create_or_get.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "id": "(redacted)",
    "creationDateTime": "2020-09-11T06:30:18.1909168Z",
    "startDateTime": "2020-09-11T06:30:18.0615989Z",
    "endDateTime": "2020-09-11T07:30:18.0615989Z",
    "joinWebUrl": "(redacted)",
    "subject": "Create a meeting with customId provided",
    "isBroadcast": false,
    "autoAdmittedUsers": "EveryoneInCompany",
    "isEntryExitAnnounced": true,
    "allowedPresenters": "everyone",
    "videoTeleconferenceId": "(redacted)",
    "externalId": "7eb8263f-d0e0-4149-bb1c-1f0476083c56",
    "participants": {
        "organizer": {
            "upn": "(redacted)",
            "role": "presenter",
            "identity": {
                "user": {
                    "id": "(redacted)",
                }
            }
        },
        "attendees": [
            {
                "upn": "test1@contoso.com",
                "role": null,
                "identity": {
                    "user": {
                        "id": "1f35f2e6-9cab-44ad-8d5a-b74c14720000",
                    }
                }
            }
        ],
        "producers": [],
        "contributors": []
    },
    "lobbyBypassSettings": {
        "scope": "organization",
        "isDialInBypassEnabled": false
    },
    "audioConferencing": {
        "conferenceId": "(redacted)",
        "tollNumber": "+1 206-485-3005",
        "tollFreeNumber": null,
        "dialinUrl": "https://dialin.teams.microsoft.com/0e73a853-1cc2-436c-b18c-9f53e0a97c24?id=(redacted)"
    },
    "chatInfo": {
        "threadId": "19:7ebda77322dd4505ac4dedb5b67df076@thread.tacv2",
        "messageId": "0",
        "replyChainMessageId": null
    },
}
```
