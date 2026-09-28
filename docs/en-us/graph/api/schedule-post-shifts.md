<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-post-shifts?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create shift

Namespace: microsoft.graph

Create a new [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

The duration of a shift cannot be less than 1 minute or longer than 24 hours.

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

## HTTP request

```http
POST /teams/{teamId}/schedule/shifts
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of the modified [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) object.

The following table lists the properties that you can use when you create a **shift** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| draftShift | [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0) | Draft changes in the **shift**. Draft changes are only visible to managers. The changes are visible to employees when they're [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0), which copies the changes from the **draftShift** to the **sharedShift** property. Eiher **draShift** or **sharedShift** should be `null`. |
| isStagedForDeletion | Boolean | The **shift** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Optional. |
| schedulingGroupId | String | ID of the scheduling group the **shift** is part of. Required. |
| sharedShift | [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0) | The shared version of this **shift** that is viewable by both employees and managers. Updates to the **sharedShift** property send notifications to users in the Teams client. Eiher **draShift** or **sharedShift** should be `null`. |
| userId | String | ID of the user assigned to the **shift**. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) object in the response body.

## Example

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
POST https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/shifts
Content-type: application/json

{
  "userId": "5ca83ce7-291d-43b7-bf53-af79eef4bc1d",
  "draftShift": {
    "displayName": null,
    "startDateTime": "2024-10-08T15:00:00Z",
    "endDateTime": "2024-10-09T00:00:00Z",
    "theme": "blue",
    "notes": null,
    "activities": []
  },
  "sharedShift": null,
  "isStagedForDeletion": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Shift
{
	UserId = "5ca83ce7-291d-43b7-bf53-af79eef4bc1d",
	DraftShift = new ShiftItem
	{
		DisplayName = null,
		StartDateTime = DateTimeOffset.Parse("2024-10-08T15:00:00Z"),
		EndDateTime = DateTimeOffset.Parse("2024-10-09T00:00:00Z"),
		Theme = ScheduleEntityTheme.Blue,
		Notes = null,
		Activities = new List<ShiftActivity>
		{
		},
	},
	SharedShift = null,
	IsStagedForDeletion = false,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.Shifts.PostAsync(requestBody);
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

requestBody := graphmodels.NewShift()
userId := "5ca83ce7-291d-43b7-bf53-af79eef4bc1d"
requestBody.SetUserId(&userId) 
draftShift := graphmodels.NewShiftItem()
displayName := null
draftShift.SetDisplayName(&displayName) 
startDateTime , err := time.Parse(time.RFC3339, "2024-10-08T15:00:00Z")
draftShift.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2024-10-09T00:00:00Z")
draftShift.SetEndDateTime(&endDateTime) 
theme := graphmodels.BLUE_SCHEDULEENTITYTHEME 
draftShift.SetTheme(&theme) 
notes := null
draftShift.SetNotes(&notes) 
activities := []graphmodels.ShiftActivityable {

}
draftShift.SetActivities(activities)
requestBody.SetDraftShift(draftShift)
sharedShift := null
requestBody.SetSharedShift(&sharedShift) 
isStagedForDeletion := false
requestBody.SetIsStagedForDeletion(&isStagedForDeletion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
shifts, err := graphClient.Teams().ByTeamId("team-id").Schedule().Shifts().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Shift shift = new Shift();
shift.setUserId("5ca83ce7-291d-43b7-bf53-af79eef4bc1d");
ShiftItem draftShift = new ShiftItem();
draftShift.setDisplayName(null);
OffsetDateTime startDateTime = OffsetDateTime.parse("2024-10-08T15:00:00Z");
draftShift.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-10-09T00:00:00Z");
draftShift.setEndDateTime(endDateTime);
draftShift.setTheme(ScheduleEntityTheme.Blue);
draftShift.setNotes(null);
LinkedList<ShiftActivity> activities = new LinkedList<ShiftActivity>();
draftShift.setActivities(activities);
shift.setDraftShift(draftShift);
shift.setSharedShift(null);
shift.setIsStagedForDeletion(false);
Shift result = graphClient.teams().byTeamId("{team-id}").schedule().shifts().post(shift);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const shift = {
  userId: '5ca83ce7-291d-43b7-bf53-af79eef4bc1d',
  draftShift: {
    displayName: null,
    startDateTime: '2024-10-08T15:00:00Z',
    endDateTime: '2024-10-09T00:00:00Z',
    theme: 'blue',
    notes: null,
    activities: []
  },
  sharedShift: null,
  isStagedForDeletion: false
};

await client.api('/teams/{teamId}/schedule/shifts')
	.post(shift);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Shift;
use Microsoft\Graph\Generated\Models\ShiftItem;
use Microsoft\Graph\Generated\Models\ScheduleEntityTheme;
use Microsoft\Graph\Generated\Models\ShiftActivity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Shift();
$requestBody->setUserId('5ca83ce7-291d-43b7-bf53-af79eef4bc1d');
$draftShift = new ShiftItem();
$draftShift->setDisplayName(null);
$draftShift->setStartDateTime(new \DateTime('2024-10-08T15:00:00Z'));
$draftShift->setEndDateTime(new \DateTime('2024-10-09T00:00:00Z'));
$draftShift->setTheme(new ScheduleEntityTheme('blue'));
$draftShift->setNotes(null);
$draftShift->setActivities([	]);
$requestBody->setDraftShift($draftShift);
$requestBody->setSharedShift(null);
$requestBody->setIsStagedForDeletion(false);

$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->shifts()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	userId = "5ca83ce7-291d-43b7-bf53-af79eef4bc1d"
	draftShift = @{
		displayName = $null
		startDateTime = [System.DateTime]::Parse("2024-10-08T15:00:00Z")
		endDateTime = [System.DateTime]::Parse("2024-10-09T00:00:00Z")
		theme = "blue"
		notes = $null
		activities = @(
		)
	}
	sharedShift = $null
	isStagedForDeletion = $false
}

New-MgTeamScheduleShift -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.shift import Shift
from msgraph.generated.models.shift_item import ShiftItem
from msgraph.generated.models.schedule_entity_theme import ScheduleEntityTheme
from msgraph.generated.models.shift_activity import ShiftActivity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Shift(
	user_id = "5ca83ce7-291d-43b7-bf53-af79eef4bc1d",
	draft_shift = ShiftItem(
		display_name = None,
		start_date_time = "2024-10-08T15:00:00Z",
		end_date_time = "2024-10-09T00:00:00Z",
		theme = ScheduleEntityTheme.Blue,
		notes = None,
		activities = [
		],
	),
	shared_shift = None,
	is_staged_for_deletion = False,
)

result = await graph_client.teams.by_team_id('team-id').schedule.shifts.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "SHFT_0f004eda-32a6-4f0c-a076-18f76d997a55",
  "createdDateTime": "2024-11-08T23:49:13.877Z",
  "lastModifiedDateTime": "2024-11-08T23:49:13.877Z",
  "schedulingGroupId": "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a",
  "userId": "5ca83ce7-291d-43b7-bf53-af79eef4bc1d",
  "sharedShift": null,
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
  "draftShift": {
    "displayName": null,
    "startDateTime": "2024-10-08T15:00:00Z",
    "endDateTime": "2024-10-09T00:00:00Z",
    "theme": "blue",
    "notes": null,
    "activities": []
  },
  "isStagedForDeletion": false
}
```
