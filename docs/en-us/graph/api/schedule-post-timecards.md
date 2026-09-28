<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-post-timecards?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create timeCard

Namespace: microsoft.graph

Create a [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

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
POST /teams/{teamsId}/schedule/timeCards
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

Provide the new [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) object in the request body for this method.

## Response

If successful, this method returns a `201 Created` response code and a [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards
Content-Type: application/json

{
  "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
  "clockInEvent": {
    "dateTime": "2025-01-07T21:00:00.000Z",
    "isAtApprovedLocation": true,
    "notes": {
      "content": "Started late due to traffic in CA 237",
      "contentType": "text"
    }
  },
  "clockOutEvent": {
    "dateTime": "2025-01-07T21:30:00.000Z",
    "isAtApprovedLocation": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TimeCard
{
	UserId = "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
	ClockInEvent = new TimeCardEvent
	{
		DateTime = DateTimeOffset.Parse("2025-01-07T21:00:00.000Z"),
		IsAtApprovedLocation = true,
		Notes = new ItemBody
		{
			Content = "Started late due to traffic in CA 237",
			ContentType = BodyType.Text,
		},
	},
	ClockOutEvent = new TimeCardEvent
	{
		DateTime = DateTimeOffset.Parse("2025-01-07T21:30:00.000Z"),
		IsAtApprovedLocation = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimeCards.PostAsync(requestBody);
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

requestBody := graphmodels.NewTimeCard()
userId := "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2"
requestBody.SetUserId(&userId) 
clockInEvent := graphmodels.NewTimeCardEvent()
dateTime , err := time.Parse(time.RFC3339, "2025-01-07T21:00:00.000Z")
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
clockOutEvent := graphmodels.NewTimeCardEvent()
dateTime , err := time.Parse(time.RFC3339, "2025-01-07T21:30:00.000Z")
clockOutEvent.SetDateTime(&dateTime) 
isAtApprovedLocation := true
clockOutEvent.SetIsAtApprovedLocation(&isAtApprovedLocation) 
requestBody.SetClockOutEvent(clockOutEvent)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
timeCards, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimeCards().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TimeCard timeCard = new TimeCard();
timeCard.setUserId("d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2");
TimeCardEvent clockInEvent = new TimeCardEvent();
OffsetDateTime dateTime = OffsetDateTime.parse("2025-01-07T21:00:00.000Z");
clockInEvent.setDateTime(dateTime);
clockInEvent.setIsAtApprovedLocation(true);
ItemBody notes = new ItemBody();
notes.setContent("Started late due to traffic in CA 237");
notes.setContentType(BodyType.Text);
clockInEvent.setNotes(notes);
timeCard.setClockInEvent(clockInEvent);
TimeCardEvent clockOutEvent = new TimeCardEvent();
OffsetDateTime dateTime1 = OffsetDateTime.parse("2025-01-07T21:30:00.000Z");
clockOutEvent.setDateTime(dateTime1);
clockOutEvent.setIsAtApprovedLocation(true);
timeCard.setClockOutEvent(clockOutEvent);
TimeCard result = graphClient.teams().byTeamId("{team-id}").schedule().timeCards().post(timeCard);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeCard = {
  userId: 'd56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2',
  clockInEvent: {
    dateTime: '2025-01-07T21:00:00.000Z',
    isAtApprovedLocation: true,
    notes: {
      content: 'Started late due to traffic in CA 237',
      contentType: 'text'
    }
  },
  clockOutEvent: {
    dateTime: '2025-01-07T21:30:00.000Z',
    isAtApprovedLocation: true
  }
};

await client.api('/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards')
	.post(timeCard);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TimeCard;
use Microsoft\Graph\Generated\Models\TimeCardEvent;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TimeCard();
$requestBody->setUserId('d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2');
$clockInEvent = new TimeCardEvent();
$clockInEvent->setDateTime(new \DateTime('2025-01-07T21:00:00.000Z'));
$clockInEvent->setIsAtApprovedLocation(true);
$clockInEventNotes = new ItemBody();
$clockInEventNotes->setContent('Started late due to traffic in CA 237');
$clockInEventNotes->setContentType(new BodyType('text'));
$clockInEvent->setNotes($clockInEventNotes);
$requestBody->setClockInEvent($clockInEvent);
$clockOutEvent = new TimeCardEvent();
$clockOutEvent->setDateTime(new \DateTime('2025-01-07T21:30:00.000Z'));
$clockOutEvent->setIsAtApprovedLocation(true);
$requestBody->setClockOutEvent($clockOutEvent);

$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timeCards()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	userId = "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2"
	clockInEvent = @{
		dateTime = [System.DateTime]::Parse("2025-01-07T21:00:00.000Z")
		isAtApprovedLocation = $true
		notes = @{
			content = "Started late due to traffic in CA 237"
			contentType = "text"
		}
	}
	clockOutEvent = @{
		dateTime = [System.DateTime]::Parse("2025-01-07T21:30:00.000Z")
		isAtApprovedLocation = $true
	}
}

New-MgTeamScheduleTimeCard -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.time_card import TimeCard
from msgraph.generated.models.time_card_event import TimeCardEvent
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TimeCard(
	user_id = "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
	clock_in_event = TimeCardEvent(
		date_time = "2025-01-07T21:00:00.000Z",
		is_at_approved_location = True,
		notes = ItemBody(
			content = "Started late due to traffic in CA 237",
			content_type = BodyType.Text,
		),
	),
	clock_out_event = TimeCardEvent(
		date_time = "2025-01-07T21:30:00.000Z",
		is_at_approved_location = True,
	),
)

result = await graph_client.teams.by_team_id('team-id').schedule.time_cards.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "TCK_18aeaf79-71c3-44a5-8a6c-236d25d0f726",
  "createdDateTime": "2025-01-07T21:30:20.487Z",
  "lastModifiedDateTime": "2025-01-07T21:30:20.487Z",
  "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
  "state": "clockedOut",
  "confirmedBy": "none",
  "notes": null,
  "lastModifiedBy": {
    "application": null,
    "device": null,
    "user": {
      "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "displayName": "Alice Bradford"
    }
  },
  "clockInEvent": {
    "dateTime": "2025-01-07T21:00:00Z",
    "isAtApprovedLocation": true,
    "notes": {
      "contentType": "text",
      "content": "Started late due to traffic in CA 237"
    }
  },
  "clockOutEvent": {
    "dateTime": "2025-01-07T21:30:00Z",
    "isAtApprovedLocation": true,
    "notes": null
  },
  "breaks": [],
  "originalEntry": {
    "clockInEvent": null,
    "clockOutEvent": null,
    "breaks": []
  },
  "createdBy": {
    "application": null,
    "device": null,
    "user": {
      "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "displayName": "Alice Bradford"
    }
  }
}
```
