<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-28 -->

# schedule: share

Namespace: microsoft.graph

Share a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) time range with schedule members.

This action makes the collections of [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0), [openshift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) and [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) items in the specified time range of the [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) viewable by the specified team members, including employees and managers.

Each [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0), [openshift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) and [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) supports a draft version and a shared version of the item. The draft version is viewable by only managers, and the shared version is viewable by employees and managers. For each [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0), [openshift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) and [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) instance in the specified time range, the share action updates the shared version from the draft version, so that in addition to managers, employees can also view the most current information about the item. The **notifyTeam** parameter further specifies which employees can view the item.

> **Note:** To streamline the user experience, update all draft properites and then share all pending changes within a date range as a single action. The draft versions of the properties must be empty before you can update the shared versions of the items.

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
POST /teams/{teamId}/schedule/share
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| --- | --- | --- |
| notifyTeam | `Boolean` | Indicates whether the entire team should get a visible notification of this action, or only employees that have a shift assigned to them that was shared. Required. |
| startDateTime | `DateTimeOffset` | The start time to share shifts on the schedule from. Required. |
| endDateTime | `DateTimeOffset` | The end time to share shifts on the schedule until. |

## Response

If successful, this method returns a `200 OK` response code. It doesn't return anything in the response body.

## Example

### Request

Here's an example of the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/share
Content-type: application/json

{
  "notifyTeam": true,
  "startDateTime": "2018-10-08T00:00:00.000Z",
  "endDateTime": "2018-10-15T00:00:00.000Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.Schedule.Share;

var requestBody = new SharePostRequestBody
{
	NotifyTeam = true,
	StartDateTime = DateTimeOffset.Parse("2018-10-08T00:00:00.000Z"),
	EndDateTime = DateTimeOffset.Parse("2018-10-15T00:00:00.000Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].Schedule.Share.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  //other-imports
)

requestBody := graphteams.NewSharePostRequestBody()
notifyTeam := true
requestBody.SetNotifyTeam(&notifyTeam) 
startDateTime , err := time.Parse(time.RFC3339, "2018-10-08T00:00:00.000Z")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2018-10-15T00:00:00.000Z")
requestBody.SetEndDateTime(&endDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").Schedule().Share().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.schedule.share.SharePostRequestBody sharePostRequestBody = new com.microsoft.graph.teams.item.schedule.share.SharePostRequestBody();
sharePostRequestBody.setNotifyTeam(true);
OffsetDateTime startDateTime = OffsetDateTime.parse("2018-10-08T00:00:00.000Z");
sharePostRequestBody.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2018-10-15T00:00:00.000Z");
sharePostRequestBody.setEndDateTime(endDateTime);
graphClient.teams().byTeamId("{team-id}").schedule().share().post(sharePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const share = {
  notifyTeam: true,
  startDateTime: '2018-10-08T00:00:00.000Z',
  endDateTime: '2018-10-15T00:00:00.000Z'
};

await client.api('/teams/{teamId}/schedule/share')
	.post(share);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Schedule\Share\SharePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SharePostRequestBody();
$requestBody->setNotifyTeam(true);
$requestBody->setStartDateTime(new \DateTime('2018-10-08T00:00:00.000Z'));
$requestBody->setEndDateTime(new \DateTime('2018-10-15T00:00:00.000Z'));

$graphServiceClient->teams()->byTeamId('team-id')->schedule()->share()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	notifyTeam = $true
	startDateTime = [System.DateTime]::Parse("2018-10-08T00:00:00.000Z")
	endDateTime = [System.DateTime]::Parse("2018-10-15T00:00:00.000Z")
}

Invoke-MgShareTeamSchedule -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.schedule.share.share_post_request_body import SharePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SharePostRequestBody(
	notify_team = True,
	start_date_time = "2018-10-08T00:00:00.000Z",
	end_date_time = "2018-10-15T00:00:00.000Z",
)

await graph_client.teams.by_team_id('team-id').schedule.share.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Here's an example of the response.

```http
HTTP/1.1 200 OK
```

## Related content

[Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
