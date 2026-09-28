<!-- Source: https://learn.microsoft.com/en-us/graph/api/timeoffrequest-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create timeOffRequest

Namespace: microsoft.graph

Create instance of a [timeoffrequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0) object.

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
POST /teams/{teamId}/schedule/timeOffRequests
```

## Optional query parameters

This method doesn't support OData query parameters to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, provide a JSON representation of a new [timeoffrequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0) object.

## Response

If successful, this method returns a 200 OK response code and the created [timeoffrequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/timeOffRequests

{
  "senderMessage": "Need a break",
  "timeOffReasonId": "TOR_08c42f26-9b83-492c-bf52-f3609eb083e3",
  "senderUserId": "3f2504e0-4f89-11d3-9a0c-0305e82c3301",
  "startDateTime": "2025-05-26T07:00:00Z",
  "endDateTime": "2025-05-27T07:00:00Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TimeOffRequest
{
	SenderMessage = "Need a break",
	TimeOffReasonId = "TOR_08c42f26-9b83-492c-bf52-f3609eb083e3",
	SenderUserId = "3f2504e0-4f89-11d3-9a0c-0305e82c3301",
	StartDateTime = DateTimeOffset.Parse("2025-05-26T07:00:00Z"),
	EndDateTime = DateTimeOffset.Parse("2025-05-27T07:00:00Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimeOffRequests.PostAsync(requestBody);
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

requestBody := graphmodels.NewTimeOffRequest()
senderMessage := "Need a break"
requestBody.SetSenderMessage(&senderMessage) 
timeOffReasonId := "TOR_08c42f26-9b83-492c-bf52-f3609eb083e3"
requestBody.SetTimeOffReasonId(&timeOffReasonId) 
senderUserId := "3f2504e0-4f89-11d3-9a0c-0305e82c3301"
requestBody.SetSenderUserId(&senderUserId) 
startDateTime , err := time.Parse(time.RFC3339, "2025-05-26T07:00:00Z")
requestBody.SetStartDateTime(&startDateTime) 
endDateTime , err := time.Parse(time.RFC3339, "2025-05-27T07:00:00Z")
requestBody.SetEndDateTime(&endDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
timeOffRequests, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimeOffRequests().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TimeOffRequest timeOffRequest = new TimeOffRequest();
timeOffRequest.setSenderMessage("Need a break");
timeOffRequest.setTimeOffReasonId("TOR_08c42f26-9b83-492c-bf52-f3609eb083e3");
timeOffRequest.setSenderUserId("3f2504e0-4f89-11d3-9a0c-0305e82c3301");
OffsetDateTime startDateTime = OffsetDateTime.parse("2025-05-26T07:00:00Z");
timeOffRequest.setStartDateTime(startDateTime);
OffsetDateTime endDateTime = OffsetDateTime.parse("2025-05-27T07:00:00Z");
timeOffRequest.setEndDateTime(endDateTime);
TimeOffRequest result = graphClient.teams().byTeamId("{team-id}").schedule().timeOffRequests().post(timeOffRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeOffRequest = {
  senderMessage: 'Need a break',
  timeOffReasonId: 'TOR_08c42f26-9b83-492c-bf52-f3609eb083e3',
  senderUserId: '3f2504e0-4f89-11d3-9a0c-0305e82c3301',
  startDateTime: '2025-05-26T07:00:00Z',
  endDateTime: '2025-05-27T07:00:00Z'
};

await client.api('/teams/{teamId}/schedule/timeOffRequests')
	.post(timeOffRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TimeOffRequest;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TimeOffRequest();
$requestBody->setSenderMessage('Need a break');
$requestBody->setTimeOffReasonId('TOR_08c42f26-9b83-492c-bf52-f3609eb083e3');
$requestBody->setSenderUserId('3f2504e0-4f89-11d3-9a0c-0305e82c3301');
$requestBody->setStartDateTime(new \DateTime('2025-05-26T07:00:00Z'));
$requestBody->setEndDateTime(new \DateTime('2025-05-27T07:00:00Z'));

$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timeOffRequests()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	senderMessage = "Need a break"
	timeOffReasonId = "TOR_08c42f26-9b83-492c-bf52-f3609eb083e3"
	senderUserId = "3f2504e0-4f89-11d3-9a0c-0305e82c3301"
	startDateTime = [System.DateTime]::Parse("2025-05-26T07:00:00Z")
	endDateTime = [System.DateTime]::Parse("2025-05-27T07:00:00Z")
}

New-MgTeamScheduleTimeOffRequest -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.time_off_request import TimeOffRequest
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TimeOffRequest(
	sender_message = "Need a break",
	time_off_reason_id = "TOR_08c42f26-9b83-492c-bf52-f3609eb083e3",
	sender_user_id = "3f2504e0-4f89-11d3-9a0c-0305e82c3301",
	start_date_time = "2025-05-26T07:00:00Z",
	end_date_time = "2025-05-27T07:00:00Z",
)

result = await graph_client.teams.by_team_id('team-id').schedule.time_off_requests.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "SREQ_54f7ae3c-dc28-4773-8135-811dd8db2121",
    "createdDateTime": "2025-05-22T20:50:26.796Z",
    "lastModifiedDateTime": "2025-05-22T20:50:26.796Z",
    "assignedTo": "manager",
    "state": "pending",
    "senderDateTime": "2025-05-22T20:50:26.796Z",
    "senderMessage": "Need a break",
    "senderUserId": "3f2504e0-4f89-11d3-9a0c-0305e82c3301",
    "managerActionDateTime": null,
    "managerActionMessage": null,
    "managerUserId": null,
    "startDateTime": "2025-05-26T07:00:00Z",
    "endDateTime": "2025-05-27T07:00:00Z",
    "timeOffReasonId": "TOR_08c42f26-9b83-492c-bf52-f3609eb083e3",
    "lastModifiedBy": {
        "user": {
            "id": "3f2504e0-4f89-11d3-9a0c-0305e82c3301",
            "displayName": "Ava Mitchell",
            "userIdentityType": "aadUser",
        }
    }
}
```
