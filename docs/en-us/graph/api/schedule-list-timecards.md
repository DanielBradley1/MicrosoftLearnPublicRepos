<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-list-timecards?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# List timeCard

Namespace: microsoft.graph

Retrieve a list of [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) entries in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.Read.All | Schedule.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.Read.All | Schedule.ReadWrite.All |

## HTTP request

```http
GET /teams/{teamsId}/schedule/timeCards
```

## Optional query parameters

This method supports the `$filter`, `$orderby`, `$top`, `$skipToken` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimeCards.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
timeCards, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimeCards().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TimeCardCollectionResponse result = graphClient.teams().byTeamId("{team-id}").schedule().timeCards().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let timeCards = await client.api('/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timeCards()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgTeamScheduleTimeCard -TeamId $teamId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.teams.by_team_id('team-id').schedule.time_cards.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "TCK_ed816e2c-7c7a-44ff-9761-dc3df92a17ef",
      "createdDateTime": "2025-01-07T14:40:01.601Z",
      "lastModifiedDateTime": "2025-01-07T19:43:54.555Z",
      "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "state": "clockedOut",
      "confirmedBy": "none",
      "notes": null,
      "lastModifiedBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford",
        }
      },
      "clockInEvent": {
        "dateTime": "2025-01-07T14:40:01.601Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "clockOutEvent": {
        "dateTime": "2025-01-07T19:43:54.555Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "breaks": [
        {
          "breakId": "BRK_d659f765-8c16-4a40-a6c8-2a1cf407b859",
          "notes": null,
          "start": {
            "dateTime": "2025-01-07T16:42:35.406Z",
            "isAtApprovedLocation": null,
            "notes": null
          },
          "end": {
            "dateTime": "2025-01-07T16:53:40.671Z",
            "isAtApprovedLocation": null,
            "notes": null
          }
        }
      ],
      "originalEntry": {
        "clockInEvent": {
          "dateTime": "2025-01-07T14:40:01.601Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "clockOutEvent": {
          "dateTime": "2025-01-07T19:43:54.555Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "breaks": [
          {
            "breakId": "BRK_d659f765-8c16-4a40-a6c8-2a1cf407b859",
            "notes": null,
            "start": {
              "dateTime": "2025-01-07T16:42:35.406Z",
              "isAtApprovedLocation": null,
              "notes": null
            },
            "end": {
              "dateTime": "2025-01-07T16:53:40.671Z",
              "isAtApprovedLocation": null,
              "notes": null
            }
          }
        ]
      },
      "createdBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford"
        }
      }
    },
    {
      "id": "TCK_3e74d9a1-f45f-4da3-95df-be72a8af448d",
      "createdDateTime": "2025-01-08T15:44:09.545Z",
      "lastModifiedDateTime": "2025-01-08T19:45:25.048Z",
      "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "state": "clockedOut",
      "confirmedBy": "none",
      "notes": null,
      "lastModifiedBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford",
        }
      },
      "clockInEvent": {
        "dateTime": "2025-01-08T15:44:09.545Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "clockOutEvent": {
        "dateTime": "2025-01-07T19:45:25.048Z",
        "isAtApprovedLocation": null,
        "notes": null
      },
      "breaks": [],
      "originalEntry": {
        "clockInEvent": {
          "dateTime": "2025-01-07T15:44:09.545Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "clockOutEvent": {
          "dateTime": "2025-01-07T19:45:25.048Z",
          "isAtApprovedLocation": null,
          "notes": null
        },
        "breaks": []
      },
      "createdBy": {
        "application": null,
        "device": null,
        "user": {
          "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
          "displayName": "Alice Bradford",
        }
      }
    }
  ]
}
```
