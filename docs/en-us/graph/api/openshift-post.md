<!-- Source: https://learn.microsoft.com/en-us/graph/api/openshift-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create openShift

Namespace: microsoft.graph

Create an instance of an [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Group.Read.All, Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they are not a member of.

## HTTP request

```http
POST /teams/{id}/schedule/openShifts
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of the modified [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) object.

The following table lists the properties that you can use when you create an **openShift** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| draftOpenShift | [openShiftItem](https://learn.microsoft.com/en-us/graph/api/resources/openshiftitem?view=graph-rest-1.0) | Draft changes in the **openShift** are only visible to managers until they're [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| isStagedForDeletion | Boolean | The **openShift** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Optional. |
| schedulingGroupId | String | The ID of the [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) that contains the **openShift**. |
| sharedOpenShift | [openShiftItem](https://learn.microsoft.com/en-us/graph/api/resources/openshiftitem?view=graph-rest-1.0) | The shared version of this **openShift** that is viewable by both employees and managers. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |

## Response

If successful, this method returns a `200 OK` response code and the created [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/teams/788b75d2-a911-48c0-a5e2-dc98480457e3/schedule/openShifts
Authorization: Bearer {token}
Content-type: application/json

{
  "schedulingGroupId": "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a",
  "sharedOpenShift": {
    "displayName": "Dayshift",
    "startDateTime": "2024-11-04T20:00:00Z",
    "endDateTime": "2024-11-04T21:00:00Z",
    "theme": "blue",
    "notes": "InventoryManagement",
    "openSlotCount": 1,
    "activities": []
  },
  "draftTimeOff": null,
  "isStagedForDeletion": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new OpenShift
{
	SchedulingGroupId = "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a",
	SharedOpenShift = new OpenShiftItem
	{
		DisplayName = "Dayshift",
		StartDateTime = DateTimeOffset.Parse("2024-11-04T20:00:00Z"),
		EndDateTime = DateTimeOffset.Parse("2024-11-04T21:00:00Z"),
		Theme = ScheduleEntityTheme.Blue,
		Notes = "InventoryManagement",
		OpenSlotCount = 1,
		Activities = new List<ShiftActivity>
		{
		},
	},
	IsStagedForDeletion = false,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"draftTimeOff" , null
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.OpenShifts.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Authorization", "Bearer {token}");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Authorization", "Bearer {token}")

configuration := &graphteams.ItemScheduleOpenShiftsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewOpenShift()
schedulingGroupId := "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a"
requestBody.SetSchedulingGroupId(&schedulingGroupId) 
sharedOpenShift := graphmodels.NewOpenShiftItem()
displayName := "Dayshift"
sharedOpenShift.SetDisplayName(&displayName) 
startDateTime , err := time.Parse(time.RFC3339, "2024-11-04T20:00:00Z")
sharedOpenShift.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2024-11-04T21:00:00Z")
sharedOpenShift.SetEndDateTime(&endDateTime) 
theme := graphmodels.BLUE_SCHEDULEENTITYTHEME 
sharedOpenShift.SetTheme(&theme) 
notes := "InventoryManagement"
sharedOpenShift.SetNotes(&notes) 
openSlotCount := int32(1)
sharedOpenShift.SetOpenSlotCount(&openSlotCount) 
activities := []graphmodels.ShiftActivityable {

}
sharedOpenShift.SetActivities(activities)
requestBody.SetSharedOpenShift(sharedOpenShift)
isStagedForDeletion := false
requestBody.SetIsStagedForDeletion(&isStagedForDeletion) 
additionalData := map[string]interface{}{
	draftTimeOff := null
requestBody.SetDraftTimeOff(&draftTimeOff) 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
openShifts, err := graphClient.Teams().ByTeamId("team-id").Schedule().OpenShifts().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

OpenShift openShift = new OpenShift();
openShift.setSchedulingGroupId("TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a");
OpenShiftItem sharedOpenShift = new OpenShiftItem();
sharedOpenShift.setDisplayName("Dayshift");
OffsetDateTime startDateTime = OffsetDateTime.parse("2024-11-04T20:00:00Z");
sharedOpenShift.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2024-11-04T21:00:00Z");
sharedOpenShift.setEndDateTime(endDateTime);
sharedOpenShift.setTheme(ScheduleEntityTheme.Blue);
sharedOpenShift.setNotes("InventoryManagement");
sharedOpenShift.setOpenSlotCount(1);
LinkedList<ShiftActivity> activities = new LinkedList<ShiftActivity>();
sharedOpenShift.setActivities(activities);
openShift.setSharedOpenShift(sharedOpenShift);
openShift.setIsStagedForDeletion(false);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("draftTimeOff", null);
openShift.setAdditionalData(additionalData);
OpenShift result = graphClient.teams().byTeamId("{team-id}").schedule().openShifts().post(openShift, requestConfiguration -> {
	requestConfiguration.headers.add("Authorization", "Bearer {token}");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const openShift = {
  schedulingGroupId: 'TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a',
  sharedOpenShift: {
    displayName: 'Dayshift',
    startDateTime: '2024-11-04T20:00:00Z',
    endDateTime: '2024-11-04T21:00:00Z',
    theme: 'blue',
    notes: 'InventoryManagement',
    openSlotCount: 1,
    activities: []
  },
  draftTimeOff: null,
  isStagedForDeletion: false
};

await client.api('/teams/788b75d2-a911-48c0-a5e2-dc98480457e3/schedule/openShifts')
	.post(openShift);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Schedule\OpenShifts\OpenShiftsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Models\OpenShift;
use Microsoft\Graph\Generated\Models\OpenShiftItem;
use Microsoft\Graph\Generated\Models\ScheduleEntityTheme;
use Microsoft\Graph\Generated\Models\ShiftActivity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new OpenShift();
$requestBody->setSchedulingGroupId('TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a');
$sharedOpenShift = new OpenShiftItem();
$sharedOpenShift->setDisplayName('Dayshift');
$sharedOpenShift->setStartDateTime(new \DateTime('2024-11-04T20:00:00Z'));
$sharedOpenShift->setEndDateTime(new \DateTime('2024-11-04T21:00:00Z'));
$sharedOpenShift->setTheme(new ScheduleEntityTheme('blue'));
$sharedOpenShift->setNotes('InventoryManagement');
$sharedOpenShift->setOpenSlotCount(1);
$sharedOpenShift->setActivities([	]);
$requestBody->setSharedOpenShift($sharedOpenShift);
$requestBody->setIsStagedForDeletion(false);
$additionalData = [
	'draftTimeOff' => null,
];
$requestBody->setAdditionalData($additionalData);
$requestConfiguration = new OpenShiftsRequestBuilderPostRequestConfiguration();
$headers = [
		'Authorization' => 'Bearer {token}',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->openShifts()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	schedulingGroupId = "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a"
	sharedOpenShift = @{
		displayName = "Dayshift"
		startDateTime = [System.DateTime]::Parse("2024-11-04T20:00:00Z")
		endDateTime = [System.DateTime]::Parse("2024-11-04T21:00:00Z")
		theme = "blue"
		notes = "InventoryManagement"
		openSlotCount = 1
		activities = @(
		)
	}
	draftTimeOff = $null
	isStagedForDeletion = $false
}

New-MgTeamScheduleOpenShift -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.schedule.open_shifts.open_shifts_request_builder import OpenShiftsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.open_shift import OpenShift
from msgraph.generated.models.open_shift_item import OpenShiftItem
from msgraph.generated.models.schedule_entity_theme import ScheduleEntityTheme
from msgraph.generated.models.shift_activity import ShiftActivity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = OpenShift(
	scheduling_group_id = "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a",
	shared_open_shift = OpenShiftItem(
		display_name = "Dayshift",
		start_date_time = "2024-11-04T20:00:00Z",
		end_date_time = "2024-11-04T21:00:00Z",
		theme = ScheduleEntityTheme.Blue,
		notes = "InventoryManagement",
		open_slot_count = 1,
		activities = [
		],
	),
	is_staged_for_deletion = False,
	additional_data = {
			"draft_time_off" : None,
	}
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Authorization", "Bearer {token}")


result = await graph_client.teams.by_team_id('team-id').schedule.open_shifts.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('48ba9e52-8d25-41c7-bbe7-5ee6346eec0d')/schedule/openShifts/$entity",
    "@odata.etag": "\"4002def0-0000-0c00-0000-672ea2ff0000\"",
    "id": "OPNSHFT_6f5e1d7c-3ebe-449f-abfc-d677d26f0b5c",
    "createdDateTime": "2024-11-08T23:47:11.605Z",
    "lastModifiedDateTime": "2024-11-08T23:47:11.605Z",
    "schedulingGroupId": "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a",
    "draftOpenShift": null,
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
    "sharedOpenShift": {
        "displayName": null,
        "startDateTime": "2024-11-04T20:00:00Z",
        "endDateTime": "2024-11-04T21:00:00Z",
        "theme": "blue",
        "notes": null,
        "openSlotCount": 1,
        "activities": []
    },
    "isStagedForDeletion": false
}
```
