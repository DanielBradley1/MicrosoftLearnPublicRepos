<!-- Source: https://learn.microsoft.com/en-us/graph/api/timecard-post?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# Create timeCard

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-beta) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

```http
POST /teams/{teamId}/schedule/timeCards
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

Provide the new [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-beta) object in the request body for this method.

## Response

If successful, this method returns a `201 Created` response code and a [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-beta) object in the response body.

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

```http
POST https://graph.microsoft.com/beta/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards
Content-type: application/json

{
  "userId":"a3601044-a1b5-438e-b742-f78d01d68a67",
  "clockInEvent":{
     "dateTime":"2019-03-18T00:00:00.000Z",
     "isAtApprovedLocation":true,
     "notes": {
        "content": "Started late due to traffic in CA 237",
        "contentType": "text"
     },
  },
  "notes":{
        "content": "8 To 5 Inventory management",
        "contentType": "text"
   },
  "breaks":[
     {
       "breakId": "string",
        "notes":{
             "content": "Lunch break",
             "contentType": "text"
        },
        "start":{
           "dateTime":"2019-03-18T02:00:00.000Z",
           "isAtApprovedLocation":true,
           "notes": {
                "content": "Reduced break to make up for lost time",
                "contentType": "text"
             },
        }
     }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TimeCard
{
	UserId = "a3601044-a1b5-438e-b742-f78d01d68a67",
	ClockInEvent = new TimeCardEvent
	{
		DateTime = DateTimeOffset.Parse("2019-03-18T00:00:00.000Z"),
		IsAtApprovedLocation = true,
		Notes = new ItemBody
		{
			Content = "Started late due to traffic in CA 237",
			ContentType = BodyType.Text,
		},
	},
	Notes = new ItemBody
	{
		Content = "8 To 5 Inventory management",
		ContentType = BodyType.Text,
	},
	Breaks = new List<TimeCardBreak>
	{
		new TimeCardBreak
		{
			BreakId = "string",
			Notes = new ItemBody
			{
				Content = "Lunch break",
				ContentType = BodyType.Text,
			},
			Start = new TimeCardEvent
			{
				DateTime = DateTimeOffset.Parse("2019-03-18T02:00:00.000Z"),
				IsAtApprovedLocation = true,
				Notes = new ItemBody
				{
					Content = "Reduced break to make up for lost time",
					ContentType = BodyType.Text,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimeCards.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewTimeCard()
userId := "a3601044-a1b5-438e-b742-f78d01d68a67"
requestBody.SetUserId(&userId) 
clockInEvent := graphmodels.NewTimeCardEvent()
dateTime , err := time.Parse(time.RFC3339, "2019-03-18T00:00:00.000Z")
clockInEvent.SetDateTime(&dateTime) 
isAtApprovedLocation := true
clockInEvent.SetIsAtApprovedLocation(&isAtApprovedLocation) 
notes := graphmodels.NewItemBody()
content := "Started late due to traffic in CA 237"
notes.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
notes.SetContentType(&contentType) 
clockInEvent.SetNotes(notes)
requestBody.SetClockInEvent(clockInEvent)
notes := graphmodels.NewItemBody()
content := "8 To 5 Inventory management"
notes.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
notes.SetContentType(&contentType) 
requestBody.SetNotes(notes)


timeCardBreak := graphmodels.NewTimeCardBreak()
breakId := "string"
timeCardBreak.SetBreakId(&breakId) 
notes := graphmodels.NewItemBody()
content := "Lunch break"
notes.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
notes.SetContentType(&contentType) 
timeCardBreak.SetNotes(notes)
start := graphmodels.NewTimeCardEvent()
dateTime , err := time.Parse(time.RFC3339, "2019-03-18T02:00:00.000Z")
start.SetDateTime(&dateTime) 
isAtApprovedLocation := true
start.SetIsAtApprovedLocation(&isAtApprovedLocation) 
notes := graphmodels.NewItemBody()
content := "Reduced break to make up for lost time"
notes.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
notes.SetContentType(&contentType) 
start.SetNotes(notes)
timeCardBreak.SetStart(start)

breaks := []graphmodels.TimeCardBreakable {
	timeCardBreak,
}
requestBody.SetBreaks(breaks)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
timeCards, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimeCards().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TimeCard timeCard = new TimeCard();
timeCard.setUserId("a3601044-a1b5-438e-b742-f78d01d68a67");
TimeCardEvent clockInEvent = new TimeCardEvent();
OffsetDateTime dateTime = OffsetDateTime.parse("2019-03-18T00:00:00.000Z");
clockInEvent.setDateTime(dateTime);
clockInEvent.setIsAtApprovedLocation(true);
ItemBody notes = new ItemBody();
notes.setContent("Started late due to traffic in CA 237");
notes.setContentType(BodyType.Text);
clockInEvent.setNotes(notes);
timeCard.setClockInEvent(clockInEvent);
ItemBody notes1 = new ItemBody();
notes1.setContent("8 To 5 Inventory management");
notes1.setContentType(BodyType.Text);
timeCard.setNotes(notes1);
LinkedList<TimeCardBreak> breaks = new LinkedList<TimeCardBreak>();
TimeCardBreak timeCardBreak = new TimeCardBreak();
timeCardBreak.setBreakId("string");
ItemBody notes2 = new ItemBody();
notes2.setContent("Lunch break");
notes2.setContentType(BodyType.Text);
timeCardBreak.setNotes(notes2);
TimeCardEvent start = new TimeCardEvent();
OffsetDateTime dateTime1 = OffsetDateTime.parse("2019-03-18T02:00:00.000Z");
start.setDateTime(dateTime1);
start.setIsAtApprovedLocation(true);
ItemBody notes3 = new ItemBody();
notes3.setContent("Reduced break to make up for lost time");
notes3.setContentType(BodyType.Text);
start.setNotes(notes3);
timeCardBreak.setStart(start);
breaks.add(timeCardBreak);
timeCard.setBreaks(breaks);
TimeCard result = graphClient.teams().byTeamId("{team-id}").schedule().timeCards().post(timeCard);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeCard = {
  userId: 'a3601044-a1b5-438e-b742-f78d01d68a67',
  clockInEvent: {
     dateTime: '2019-03-18T00:00:00.000Z',
     isAtApprovedLocation: true,
     notes: {
        content: 'Started late due to traffic in CA 237',
        contentType: 'text'
     },
  },
  notes: {
        content: '8 To 5 Inventory management',
        contentType: 'text'
   },
  breaks: [
     {
       breakId: 'string',
        notes: {
             content: 'Lunch break',
             contentType: 'text'
        },
        start: {
           dateTime: '2019-03-18T02:00:00.000Z',
           isAtApprovedLocation: true,
           notes: {
                content: 'Reduced break to make up for lost time',
                contentType: 'text'
             },
        }
     }
  ]
};

await client.api('/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards')
	.version('beta')
	.post(timeCard);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\TimeCard;
use Microsoft\Graph\Beta\Generated\Models\TimeCardEvent;
use Microsoft\Graph\Beta\Generated\Models\ItemBody;
use Microsoft\Graph\Beta\Generated\Models\BodyType;
use Microsoft\Graph\Beta\Generated\Models\TimeCardBreak;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TimeCard();
$requestBody->setUserId('a3601044-a1b5-438e-b742-f78d01d68a67');
$clockInEvent = new TimeCardEvent();
$clockInEvent->setDateTime(new \DateTime('2019-03-18T00:00:00.000Z'));
$clockInEvent->setIsAtApprovedLocation(true);
$clockInEventNotes = new ItemBody();
$clockInEventNotes->setContent('Started late due to traffic in CA 237');
$clockInEventNotes->setContentType(new BodyType('text'));
$clockInEvent->setNotes($clockInEventNotes);
$requestBody->setClockInEvent($clockInEvent);
$notes = new ItemBody();
$notes->setContent('8 To 5 Inventory management');
$notes->setContentType(new BodyType('text'));
$requestBody->setNotes($notes);
$breaksTimeCardBreak1 = new TimeCardBreak();
$breaksTimeCardBreak1->setBreakId('string');
$breaksTimeCardBreak1Notes = new ItemBody();
$breaksTimeCardBreak1Notes->setContent('Lunch break');
$breaksTimeCardBreak1Notes->setContentType(new BodyType('text'));
$breaksTimeCardBreak1->setNotes($breaksTimeCardBreak1Notes);
$breaksTimeCardBreak1Start = new TimeCardEvent();
$breaksTimeCardBreak1Start->setDateTime(new \DateTime('2019-03-18T02:00:00.000Z'));
$breaksTimeCardBreak1Start->setIsAtApprovedLocation(true);
$breaksTimeCardBreak1StartNotes = new ItemBody();
$breaksTimeCardBreak1StartNotes->setContent('Reduced break to make up for lost time');
$breaksTimeCardBreak1StartNotes->setContentType(new BodyType('text'));
$breaksTimeCardBreak1Start->setNotes($breaksTimeCardBreak1StartNotes);
$breaksTimeCardBreak1->setStart($breaksTimeCardBreak1Start);
$breaksArray []= $breaksTimeCardBreak1;
$requestBody->setBreaks($breaksArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timeCards()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	userId = "a3601044-a1b5-438e-b742-f78d01d68a67"
	clockInEvent = @{
		dateTime = [System.DateTime]::Parse("2019-03-18T00:00:00.000Z")
		isAtApprovedLocation = $true
		notes = @{
			content = "Started late due to traffic in CA 237"
			contentType = "text"
		}
	}
	notes = @{
		content = "8 To 5 Inventory management"
		contentType = "text"
	}
	breaks = @(
		@{
			breakId = "string"
			notes = @{
				content = "Lunch break"
				contentType = "text"
			}
			start = @{
				dateTime = [System.DateTime]::Parse("2019-03-18T02:00:00.000Z")
				isAtApprovedLocation = $true
				notes = @{
					content = "Reduced break to make up for lost time"
					contentType = "text"
				}
			}
		}
	)
}

New-MgBetaTeamScheduleTimeCard -TeamId $teamId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.time_card import TimeCard
from msgraph_beta.generated.models.time_card_event import TimeCardEvent
from msgraph_beta.generated.models.item_body import ItemBody
from msgraph_beta.generated.models.body_type import BodyType
from msgraph_beta.generated.models.time_card_break import TimeCardBreak
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TimeCard(
	user_id = "a3601044-a1b5-438e-b742-f78d01d68a67",
	clock_in_event = TimeCardEvent(
		date_time = "2019-03-18T00:00:00.000Z",
		is_at_approved_location = True,
		notes = ItemBody(
			content = "Started late due to traffic in CA 237",
			content_type = BodyType.Text,
		),
	),
	notes = ItemBody(
		content = "8 To 5 Inventory management",
		content_type = BodyType.Text,
	),
	breaks = [
		TimeCardBreak(
			break_id = "string",
			notes = ItemBody(
				content = "Lunch break",
				content_type = BodyType.Text,
			),
			start = TimeCardEvent(
				date_time = "2019-03-18T02:00:00.000Z",
				is_at_approved_location = True,
				notes = ItemBody(
					content = "Reduced break to make up for lost time",
					content_type = BodyType.Text,
				),
			),
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').schedule.time_cards.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "3895809b-a618-4c0d-86a0-d42b25b7d74f",
  "userId": "a3601044-a1b5-438e-b742-f78d01d68a67",
  "createdDateTime": "2019-03-18T00:00:00.000Z",
  "createdBy": {
    "user": {
      "id": "a3601044-a1b5-438e-b742-f78d01d68a67",
      "displayName": "Dwight Schrute"
    }
  },
  "lastModifiedDateTime": "2019-03-18T00:00:00.000Z",
  "lastModifiedBy": {
    "user": {
      "id": "a3601044-a1b5-438e-b742-f78d01d68a67",
      "displayName": "Dwight Schrute"
    }
  },
  "state": "onBreak",
  "confirmationStatus": "notConfirmed",
  "originalEntry": {
    "clockInEvent": {
      "dateTime": "2019-03-18T00:00:00.000Z",
      "atApprovedLocation": true,
      "isAtApprovedLocation": true,
      "notes": {
        "content": "Started late due to traffic in CA 237",
        "contentType": "text"
      }
    },
    "clockOutEvent": null,
    "breaks": [
      {
        "breakId": "string",
        "notes": {
          "content": "Lunch break",
          "contentType": "text"
        },
        "start": {
          "dateTime": "2019-03-18T02:00:00.000Z",
          "atApprovedLocation": true,
          "isAtApprovedLocation": true,
          "notes": {
            "content": "Reduced break to make up for lost time",
            "contentType": "text"
          }
        },
        "end": null
      }
    ]
  },
  "clockInEvent": {
    "dateTime": "2019-03-18T00:00:00.000Z",
    "atApprovedLocation": true,
    "isAtApprovedLocation": true,
    "notes": {
      "content": "Started late due to traffic in CA 237",
      "contentType": "text"
    }
  },
  "clockOutEvent": null,
  "notes": {
    "content": "8 To 5 Inventory management",
    "contentType": "text"
  },
  "breaks": [
    {
      "breakId": "string",
      "notes": {
        "content": "Lunch break",
        "contentType": "text"
      },
      "start": {
        "dateTime": "2019-03-18T02:00:00.000Z",
        "atApprovedLocation": true,
        "isAtApprovedLocation": true,
        "notes": {
          "content": "Reduced break to make up for lost time",
          "contentType": "text"
        }
      },
      "end": null
    }
  ]
}
```
