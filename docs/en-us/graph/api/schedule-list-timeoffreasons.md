<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedule-list-timeoffreasons?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List timeOffReasons

Namespace: microsoft.graph

Get the list of [timeOffReasons](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.Read.All | Schedule.ReadWrite.All, Group.Read.All, Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.Read.All | Schedule.ReadWrite.All |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they are not a member of.

## HTTP request

```http
GET /teams/{teamId}/schedule/timeOffReasons
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) objects in the response body.

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

```msgraph
GET https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/timeOffReasons
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.TimeOffReasons.GetAsync();
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
timeOffReasons, err := graphClient.Teams().ByTeamId("team-id").Schedule().TimeOffReasons().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TimeOffReasonCollectionResponse result = graphClient.teams().byTeamId("{team-id}").schedule().timeOffReasons().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let timeOffReasons = await client.api('/teams/{teamId}/schedule/timeOffReasons')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->timeOffReasons()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgTeamScheduleTimeOffReason -TeamId $teamId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.teams.by_team_id('team-id').schedule.time_off_reasons.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
        {
            "id": "TOR_7e5935da-7031-4dc1-850b-7304dbb822af",
            "createdDateTime": null,
            "lastModifiedDateTime": "2024-11-29T07:46:02.635Z",
            "displayName": "Parental Leave",
            "iconType": "cake",
            "isActive": false,
            "lastModifiedBy": {
                "application": null,
                "device": null,
                "user": {
                    "id": "24af8b1e-f894-491c-bde2-0c705ef3fbcd",
                    "displayName": "John Doe",
                    "userIdentityType": "aadUser",
                    "tenantId": null
                }
            },
            "code": "ParentalLeave"
        },
        {
            "id": "TOR_078523b9-8c8e-4a2b-8c20-3a3b52410975",
            "createdDateTime": null,
            "lastModifiedDateTime": "2024-11-29T07:34:58.879Z",
            "displayName": "Sick Day",
            "iconType": "doctor",
            "isActive": false,
            "lastModifiedBy": {
                "application": null,
                "device": null,
                "user": {
                    "id": "24af8b1e-f894-491c-bde2-0c705ef3fbcd",
                    "displayName": "John Doe",
                    "userIdentityType": "aadUser",
                    "tenantId": null
                }
            },
            "code": null
        }
    ]
}
```
