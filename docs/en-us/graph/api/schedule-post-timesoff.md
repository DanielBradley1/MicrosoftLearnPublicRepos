<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-post-timesoff?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# Create timeOff

Namespace: microsoft.graph

Create a new [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they aren't a member of.

## HTTP request

```http
POST /teams/{teamId}/schedule/timesOff
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of the modified [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) object.

The following table lists the properties that you can use when you create a **timeOff** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| draftTimeOff | [timeOffItem](https://learn.microsoft.com/en-us/graph/api/resources/timeoffitem?view=graph-rest-1.0) | The draft version of this **timeOff** item that is viewable by managers. It must be shared before it is visible to team members. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| isStagedForDeletion | Boolean | The **timeOff** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Optional |
| sharedTimeOff | [timeOffItem](https://learn.microsoft.com/en-us/graph/api/resources/timeoffitem?view=graph-rest-1.0) | The shared version of this **timeOff** that is viewable by both employees and managers. Updates to the **sharedTimeOff** property send notifications to users in the Teams client. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| userId | String | ID of the user assigned to the **timeOff**. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/timesOff
Content-type: application/json

{
  "userId": "aa162a04-bec6-4b81-ba99-96caa7b2b24d",
  "sharedTimeOff": {
    "timeOffReasonId": "TOR_29a5ba96-c7ef-4e76-bec6-055323746314",
    "startDateTime": "2024-10-10T19:00:00Z",
    "endDateTime": "2024-10-10T20:00:00Z",
    "theme": "blue"
  },
  "draftTimeOff": null,
  "isStagedForDeletion": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TimeOff
{
	UserId = "aa162a04-bec6-4b81-ba99-96caa7b2b24d",
	SharedTimeOff = new TimeOffItem
	{
		TimeOffReasonId = "TOR_29a5ba96-c7ef-4e76-bec6-055323746314",
		StartDateTime = DateTimeOffset.Parse("2024-10-10T19:00:00Z"),
		EndDateTime = DateTimeOffset.Parse("2024-10-10T20:00:00Z"),
		Theme = ScheduleEntityTheme.Blue,
	},
	DraftTimeOff = null,
	IsStagedForDeletion = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimesOff.PostAsync(requestBody);
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

requestBody := graphmodels.NewTimeOff()
userId := "aa162a04-bec6-4b81-ba99-96caa7b2b24d"
requestBody.SetUserId(&userId) 
sharedTimeOff := graphmodels.NewTimeOffItem()
timeOffReasonId := "TOR_29a5ba96-c7ef-4e76-bec6-055323746314"
sharedTimeOff.SetTimeOffReasonId(&timeOffReasonId) 
startDateTime , err := time.Parse(time.RFC3339, "2024-10-10T19:00:00Z")
sharedTimeOff.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2024-10-10T20:00:00Z")
sharedTimeOff.SetEndDateTime(&endDateTime) 
theme := graphmodels.BLUE_SCHEDULEENTITYTHEME 
sharedTimeOff.SetTheme(&theme) 
requestBody.SetSharedTimeOff(sharedTimeOff)
draftTimeOff := null
requestBody.SetDraftTimeOff(&draftTimeOff) 
isStagedForDeletion := false
requestBody.SetIsStagedForDeletion(&isStagedForDeletion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
timesOff, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimesOff().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TimeOff timeOff = new TimeOff();
timeOff.setUserId("aa162a04-bec6-4b81-ba99-96caa7b2b24d");
TimeOffItem sharedTimeOff = new TimeOffItem();
sharedTimeOff.setTimeOffReasonId("TOR_29a5ba96-c7ef-4e76-bec6-055323746314");
OffsetDateTime startDateTime = OffsetDateTime.parse("2024-10-10T19:00:00Z");
sharedTimeOff.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-10-10T20:00:00Z");
sharedTimeOff.setEndDateTime(endDateTime);
sharedTimeOff.setTheme(ScheduleEntityTheme.Blue);
timeOff.setSharedTimeOff(sharedTimeOff);
timeOff.setDraftTimeOff(null);
timeOff.setIsStagedForDeletion(false);
TimeOff result = graphClient.teams().byTeamId("{team-id}").schedule().timesOff().post(timeOff);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeOff = {
  userId: 'aa162a04-bec6-4b81-ba99-96caa7b2b24d',
  sharedTimeOff: {
    timeOffReasonId: 'TOR_29a5ba96-c7ef-4e76-bec6-055323746314',
    startDateTime: '2024-10-10T19:00:00Z',
    endDateTime: '2024-10-10T20:00:00Z',
    theme: 'blue'
  },
  draftTimeOff: null,
  isStagedForDeletion: false
};

await client.api('/teams/{teamId}/schedule/timesOff')
	.post(timeOff);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TimeOff;
use Microsoft\Graph\Generated\Models\TimeOffItem;
use Microsoft\Graph\Generated\Models\ScheduleEntityTheme;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TimeOff();
$requestBody->setUserId('aa162a04-bec6-4b81-ba99-96caa7b2b24d');
$sharedTimeOff = new TimeOffItem();
$sharedTimeOff->setTimeOffReasonId('TOR_29a5ba96-c7ef-4e76-bec6-055323746314');
$sharedTimeOff->setStartDateTime(new \DateTime('2024-10-10T19:00:00Z'));
$sharedTimeOff->setEndDateTime(new \DateTime('2024-10-10T20:00:00Z'));
$sharedTimeOff->setTheme(new ScheduleEntityTheme('blue'));
$requestBody->setSharedTimeOff($sharedTimeOff);
$requestBody->setDraftTimeOff(null);
$requestBody->setIsStagedForDeletion(false);

$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timesOff()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	userId = "aa162a04-bec6-4b81-ba99-96caa7b2b24d"
	sharedTimeOff = @{
		timeOffReasonId = "TOR_29a5ba96-c7ef-4e76-bec6-055323746314"
		startDateTime = [System.DateTime]::Parse("2024-10-10T19:00:00Z")
		endDateTime = [System.DateTime]::Parse("2024-10-10T20:00:00Z")
		theme = "blue"
	}
	draftTimeOff = $null
	isStagedForDeletion = $false
}

New-MgTeamScheduleTimeOff -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.time_off import TimeOff
from msgraph.generated.models.time_off_item import TimeOffItem
from msgraph.generated.models.schedule_entity_theme import ScheduleEntityTheme
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TimeOff(
	user_id = "aa162a04-bec6-4b81-ba99-96caa7b2b24d",
	shared_time_off = TimeOffItem(
		time_off_reason_id = "TOR_29a5ba96-c7ef-4e76-bec6-055323746314",
		start_date_time = "2024-10-10T19:00:00Z",
		end_date_time = "2024-10-10T20:00:00Z",
		theme = ScheduleEntityTheme.Blue,
	),
	draft_time_off = None,
	is_staged_for_deletion = False,
)

result = await graph_client.teams.by_team_id('team-id').schedule.times_off.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('48ba9e52-8d25-41c7-bbe7-5ee6346eec0d')/schedule/timesOff/$entity",
  "@odata.etag": "\"40021ee2-0000-0c00-0000-672ea2790000\"",
  "id": "SHFT_d0941bce-2229-43f5-b1cd-c9e2eaf592cf",
  "createdDateTime": "2024-11-08T23:44:56.913Z",
  "lastModifiedDateTime": "2024-11-08T23:44:56.913Z",
  "userId": "aa162a04-bec6-4b81-ba99-96caa7b2b24d",
  "draftTimeOff": null,
  "lastModifiedBy": {
    "application": null,
    "device": null,
    "user": {
      "id": "366c0b19-49b1-41b5-a03f-9f3887bd0ed8",
      "displayName": "John Doe",
      "userIdentityType": "aadUser",
      "tenantId": null
    }
  },
  "sharedTimeOff": {
    "timeOffReasonId": "TOR_29a5ba96-c7ef-4e76-bec6-055323746314",
    "startDateTime": "2024-10-10T19:00:00Z",
    "endDateTime": "2024-10-10T20:00:00Z",
    "theme": "blue"
  },
  "isStagedForDeletion": false
}
```
