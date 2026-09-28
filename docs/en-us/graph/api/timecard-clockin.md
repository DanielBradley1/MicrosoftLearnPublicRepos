<!-- Source: https://learn.microsoft.com/en-us/graph/api/timecard-clockin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# timeCard: clockIn

Namespace: microsoft.graph

Clock in to start a [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0).

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
POST /teams/{teamId}/schedule/timeCards/clockIn
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| isAtApprovedLocation | Boolean | Indicates whether this action happens at an approved location. |
| notes | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Notes for the clock in. |
| onBehalfOfUserId | string | The ID of the user you are clocking in on behalf of. |

## Response

If successful, this method returns a `201 Created` response code and a [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Clock in as yourself

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

```http
POST https://graph.microsoft.com/v1.0/teams/fd15cad8-80f6-484f-9666-3caf695fbf32/schedule/timeCards/clockin
Content-type: application/json

{
  "isAtApprovedLocation": true,
  "notes": {
    "content": "Started late due to traffic",
    "contentType": "text"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.Schedule.TimeCards.ClockIn;
using Microsoft.Graph.Models;

var requestBody = new ClockInPostRequestBody
{
	IsAtApprovedLocation = true,
	Notes = new ItemBody
	{
		Content = "Started late due to traffic",
		ContentType = BodyType.Text,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimeCards.ClockIn.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewClockInPostRequestBody()
isAtApprovedLocation := true
requestBody.SetIsAtApprovedLocation(&isAtApprovedLocation) 
notes := graphmodels.NewItemBody()
content := "Started late due to traffic"
notes.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
notes.SetContentType(&contentType) 
requestBody.SetNotes(notes)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
clockIn, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimeCards().ClockIn().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.schedule.timecards.clockin.ClockInPostRequestBody clockInPostRequestBody = new com.microsoft.graph.teams.item.schedule.timecards.clockin.ClockInPostRequestBody();
clockInPostRequestBody.setIsAtApprovedLocation(true);
ItemBody notes = new ItemBody();
notes.setContent("Started late due to traffic");
notes.setContentType(BodyType.Text);
clockInPostRequestBody.setNotes(notes);
var result = graphClient.teams().byTeamId("{team-id}").schedule().timeCards().clockIn().post(clockInPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeCard = {
  isAtApprovedLocation: true,
  notes: {
    content: 'Started late due to traffic',
    contentType: 'text'
  }
};

await client.api('/teams/fd15cad8-80f6-484f-9666-3caf695fbf32/schedule/timeCards/clockin')
	.post(timeCard);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Schedule\TimeCards\ClockIn\ClockInPostRequestBody;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ClockInPostRequestBody();
$requestBody->setIsAtApprovedLocation(true);
$notes = new ItemBody();
$notes->setContent('Started late due to traffic');
$notes->setContentType(new BodyType('text'));
$requestBody->setNotes($notes);

$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timeCards()->clockIn()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	isAtApprovedLocation = $true
	notes = @{
		content = "Started late due to traffic"
		contentType = "text"
	}
}

Invoke-MgClockTeamScheduleTimeCardIn -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.schedule.timecards.clock_in.clock_in_post_request_body import ClockInPostRequestBody
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ClockInPostRequestBody(
	is_at_approved_location = True,
	notes = ItemBody(
		content = "Started late due to traffic",
		content_type = BodyType.Text,
	),
)

result = await graph_client.teams.by_team_id('team-id').schedule.time_cards.clock_in.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "TCK_95c44dff-bc12-4de2-8a9a-9772e4421eb4",
  "createdDateTime": "2025-01-07T21:35:36.311Z",
  "lastModifiedDateTime": "2025-01-07T21:35:36.311Z",
  "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
  "state": "clockedIn",
  "confirmedBy": "none",
  "clockOutEvent": null,
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
    "dateTime": "2025-01-07T21:35:36.311Z",
    "isAtApprovedLocation": true,
    "notes": {
      "contentType": "text",
      "content": "Started late due to traffic"
    }
  },
  "breaks": [],
  "originalEntry": {
    "clockOutEvent": null,
    "clockInEvent": {
      "dateTime": "2025-01-07T21:35:36.311Z",
      "isAtApprovedLocation": true,
      "notes": {
        "contentType": "text",
        "content": "Started late due to traffic"
      }
    },
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

### Example 2: Clock in on behalf of another user

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

```http
POST https://graph.microsoft.com/v1.0/teams/fd15cad8-80f6-484f-9666-3caf695fbf32/schedule/timeCards/clockin
Content-type: application/json

{
  "isAtApprovedLocation": true,
  "onBehalfOfUserId": "3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.Schedule.TimeCards.ClockIn;

var requestBody = new ClockInPostRequestBody
{
	IsAtApprovedLocation = true,
	OnBehalfOfUserId = "3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimeCards.ClockIn.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  //other-imports
)

requestBody := graphteams.NewClockInPostRequestBody()
isAtApprovedLocation := true
requestBody.SetIsAtApprovedLocation(&isAtApprovedLocation) 
onBehalfOfUserId := "3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e"
requestBody.SetOnBehalfOfUserId(&onBehalfOfUserId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
clockIn, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimeCards().ClockIn().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.schedule.timecards.clockin.ClockInPostRequestBody clockInPostRequestBody = new com.microsoft.graph.teams.item.schedule.timecards.clockin.ClockInPostRequestBody();
clockInPostRequestBody.setIsAtApprovedLocation(true);
clockInPostRequestBody.setOnBehalfOfUserId("3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e");
var result = graphClient.teams().byTeamId("{team-id}").schedule().timeCards().clockIn().post(clockInPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeCard = {
  isAtApprovedLocation: true,
  onBehalfOfUserId: '3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e'
};

await client.api('/teams/fd15cad8-80f6-484f-9666-3caf695fbf32/schedule/timeCards/clockin')
	.post(timeCard);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Schedule\TimeCards\ClockIn\ClockInPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ClockInPostRequestBody();
$requestBody->setIsAtApprovedLocation(true);
$requestBody->setOnBehalfOfUserId('3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e');

$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timeCards()->clockIn()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	isAtApprovedLocation = $true
	onBehalfOfUserId = "3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e"
}

Invoke-MgClockTeamScheduleTimeCardIn -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.schedule.timecards.clock_in.clock_in_post_request_body import ClockInPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ClockInPostRequestBody(
	is_at_approved_location = True,
	on_behalf_of_user_id = "3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e",
)

result = await graph_client.teams.by_team_id('team-id').schedule.time_cards.clock_in.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "TCK_95c44dff-bc12-4de2-8a9a-9772e4421eb4",
  "createdDateTime": "2025-05-07T21:35:36.311Z",
  "lastModifiedDateTime": "2025-05-07T21:35:36.311Z",
  "userId": "3f29c8e7-7a41-4d8e-99d6-2b1f76c9421e",
  "state": "clockedIn",
  "confirmedBy": "none",
  "clockOutEvent": null,
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
    "dateTime": "2025-05-07T21:35:36.311Z",
    "isAtApprovedLocation": true,
    "notes": null
  },
  "breaks": [],
  "originalEntry": {
    "clockOutEvent": null,
    "clockInEvent": {
      "dateTime": "2025-05-07T21:35:36.311Z",
      "isAtApprovedLocation": true,
      "notes": null
    },
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
