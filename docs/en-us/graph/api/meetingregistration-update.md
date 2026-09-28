<!-- Source: https://learn.microsoft.com/en-us/graph/api/meetingregistration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update meetingRegistration \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The meeting registration API is deprecated and will stop returning data on **December 12, 2024**. Please use the new [webinar APIs](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-beta). For more information, see [Deprecation of the Microsoft Graph meeting registration beta APIs](https://devblogs.microsoft.com/microsoft365dev/deprecation-of-the-microsoft-graph-meeting-registration-beta-apis/).

Update the details of a [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object assciated with an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-beta) on behalf of the organizer.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /me/onlineMeetings/{id}/registration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply only the properties that need to be updated in a JSON representation of a [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object.

Tip

- All properties that are not read only can be updated, with the exception of the **allowedRegistrant** property.
- The **customQuestions** navigation property cannot be updated; use the [Update meetingRegistrationQuestion](https://learn.microsoft.com/en-us/graph/api/meetingregistrationquestion-update?view=graph-rest-beta) method to update it.
- When updating **speakers**, always supply a full list of speakers.

## Response

If successful, this method returns a `200 OK` response code and an updated [meetingRegistration](https://learn.microsoft.com/en-us/graph/api/resources/meetingregistration?view=graph-rest-beta) object in the response body.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/beta/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration
Content-Type: application/json

{
  "subject":"Microsoft Ignite: Day 1",
  "startDateTime":"2021-11-02T08:00:00-08:00",
  "endDateTime":"2021-11-02T15:45:00-08:00",
  "speakers": [
    {
      "displayName": "Henry Ross",
      "bio": "Chairman and Chief Executive Officer"
    },
    {
      "displayName": "Fred Ryan",
      "bio": "CVP"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new MeetingRegistration
{
	Subject = "Microsoft Ignite: Day 1",
	StartDateTime = DateTimeOffset.Parse("2021-11-02T08:00:00-08:00"),
	EndDateTime = DateTimeOffset.Parse("2021-11-02T15:45:00-08:00"),
	Speakers = new List<MeetingSpeaker>
	{
		new MeetingSpeaker
		{
			DisplayName = "Henry Ross",
			Bio = "Chairman and Chief Executive Officer",
		},
		new MeetingSpeaker
		{
			DisplayName = "Fred Ryan",
			Bio = "CVP",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.OnlineMeetings["{onlineMeeting-id}"].Registration.PatchAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewMeetingRegistration()
subject := "Microsoft Ignite: Day 1"
requestBody.SetSubject(&subject) 
startDateTime , err := time.Parse(time.RFC3339, "2021-11-02T08:00:00-08:00")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2021-11-02T15:45:00-08:00")
requestBody.SetEndDateTime(&endDateTime) 


meetingSpeaker := graphmodels.NewMeetingSpeaker()
displayName := "Henry Ross"
meetingSpeaker.SetDisplayName(&displayName) 
bio := "Chairman and Chief Executive Officer"
meetingSpeaker.SetBio(&bio) 
meetingSpeaker1 := graphmodels.NewMeetingSpeaker()
displayName := "Fred Ryan"
meetingSpeaker1.SetDisplayName(&displayName) 
bio := "CVP"
meetingSpeaker1.SetBio(&bio) 

speakers := []graphmodels.MeetingSpeakerable {
	meetingSpeaker,
	meetingSpeaker1,
}
requestBody.SetSpeakers(speakers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
registration, err := graphClient.Me().OnlineMeetings().ByOnlineMeetingId("onlineMeeting-id").Registration().Patch(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MeetingRegistration meetingRegistration = new MeetingRegistration();
meetingRegistration.setSubject("Microsoft Ignite: Day 1");
OffsetDateTime startDateTime = OffsetDateTime.parse("2021-11-02T08:00:00-08:00");
meetingRegistration.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2021-11-02T15:45:00-08:00");
meetingRegistration.setEndDateTime(endDateTime);
LinkedList<MeetingSpeaker> speakers = new LinkedList<MeetingSpeaker>();
MeetingSpeaker meetingSpeaker = new MeetingSpeaker();
meetingSpeaker.setDisplayName("Henry Ross");
meetingSpeaker.setBio("Chairman and Chief Executive Officer");
speakers.add(meetingSpeaker);
MeetingSpeaker meetingSpeaker1 = new MeetingSpeaker();
meetingSpeaker1.setDisplayName("Fred Ryan");
meetingSpeaker1.setBio("CVP");
speakers.add(meetingSpeaker1);
meetingRegistration.setSpeakers(speakers);
MeetingRegistration result = graphClient.me().onlineMeetings().byOnlineMeetingId("{onlineMeeting-id}").registration().patch(meetingRegistration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const meetingRegistration = {
  subject: 'Microsoft Ignite: Day 1',
  startDateTime: '2021-11-02T08:00:00-08:00',
  endDateTime: '2021-11-02T15:45:00-08:00',
  speakers: [
    {
      displayName: 'Henry Ross',
      bio: 'Chairman and Chief Executive Officer'
    },
    {
      displayName: 'Fred Ryan',
      bio: 'CVP'
    }
  ]
};

await client.api('/me/onlineMeetings/MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ/registration')
	.version('beta')
	.update(meetingRegistration);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MeetingRegistration;
use Microsoft\Graph\Beta\Generated\Models\MeetingSpeaker;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MeetingRegistration();
$requestBody->setSubject('Microsoft Ignite: Day 1');
$requestBody->setStartDateTime(new \DateTime('2021-11-02T08:00:00-08:00'));
$requestBody->setEndDateTime(new \DateTime('2021-11-02T15:45:00-08:00'));
$speakersMeetingSpeaker1 = new MeetingSpeaker();
$speakersMeetingSpeaker1->setDisplayName('Henry Ross');
$speakersMeetingSpeaker1->setBio('Chairman and Chief Executive Officer');
$speakersArray []= $speakersMeetingSpeaker1;
$speakersMeetingSpeaker2 = new MeetingSpeaker();
$speakersMeetingSpeaker2->setDisplayName('Fred Ryan');
$speakersMeetingSpeaker2->setBio('CVP');
$speakersArray []= $speakersMeetingSpeaker2;
$requestBody->setSpeakers($speakersArray);


$result = $graphServiceClient->me()->onlineMeetings()->byOnlineMeetingId('onlineMeeting-id')->registration()->patch($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.CloudCommunications

$params = @{
	subject = "Microsoft Ignite: Day 1"
	startDateTime = [System.DateTime]::Parse("2021-11-02T08:00:00-08:00")
	endDateTime = [System.DateTime]::Parse("2021-11-02T15:45:00-08:00")
	speakers = @(
		@{
			displayName = "Henry Ross"
			bio = "Chairman and Chief Executive Officer"
		}
		@{
			displayName = "Fred Ryan"
			bio = "CVP"
		}
	)
}

# A UPN can also be used as -UserId.
Update-MgBetaUserOnlineMeetingRegistration -UserId $userId -OnlineMeetingId $onlineMeetingId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.meeting_registration import MeetingRegistration
from msgraph_beta.generated.models.meeting_speaker import MeetingSpeaker
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MeetingRegistration(
	subject = "Microsoft Ignite: Day 1",
	start_date_time = "2021-11-02T08:00:00-08:00",
	end_date_time = "2021-11-02T15:45:00-08:00",
	speakers = [
		MeetingSpeaker(
			display_name = "Henry Ross",
			bio = "Chairman and Chief Executive Officer",
		),
		MeetingSpeaker(
			display_name = "Fred Ryan",
			bio = "CVP",
		),
	],
)

result = await graph_client.me.online_meetings.by_online_meeting_id('onlineMeeting-id').registration.patch(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('16664f75-11dc-4870-bec6-38c1aaa81431')/onlineMeetings('MSpkYzE3Njc0Yy04MWQ5LTRhZGItYmZ')/registration(customQuestions())/$entity",
  "id": "gWWckDBR6UOI8_yzWCzeNw,6pABiSU1bkGqzLnbHG_muA,bzLh6uR-5EGYsCvtvIvs6Q,luiTigKrcUGE6Cm33MyQgA,29OIGSH4skyQNu6mNxJr3w,m2bnpmqE_EqwV1Q8dr280E",
  "registrationPageWebUrl": "https://teams.microsoft.com/registration/gWWckDBR6UOI8_yzWCzeNw,6pABiSU1bkGqzLnbHG_muA,bzLh6uR-5EGYsCvtvIvs6Q,luiTigKrcUGE6Cm33MyQgA,29OIGSH4skyQNu6mNxJr3w,m2bnpmqE_EqwV1Q8dr280E?mode=read&tenantId=eefc0b3a-a334-4fb7-ac60-2f1cf13ec00d",
  "allowedRegistrant": "everyone",
  "subject": "Microsoft Ignite: Day 1",
  "description": "Join us November 2–4, 2021 to explore the latest tools, training sessions, technical expertise, networking opportunities, and more.",
  "startDateTime": "2021-11-02T16:00:00Z",
  "endDateTime": "2021-11-02T23:45:00Z",
  "registrationPageViewCount": null,
  "speakers": [
    {
      "displayName": "John Doe",
      "bio": "Chairman and Chief Executive Officer"
    },
    {
      "displayName": "Foo Bar",
      "bio": "CVP, Microsoft Security, Compliance & Identity"
    }
  ]
}
```
