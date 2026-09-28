<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-getopenshifts?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# team: getOpenShifts

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get all [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-beta) objects across all teams a user is a direct member of.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.Read.All | Schedule.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.Read.All | Schedule.ReadWrite.All |

## HTTP request

```http
GET /me/joinedTeams/getOpenShifts
GET /users/{id | user-principal-name}/joinedTeams/getOpenShifts
```

## Optional query parameters

This method supports the `$top` and `$filter` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

Note

The `$filter` parameter supports the **sharedOpenShift/startDateTime**, **sharedOpenShift/endDateTime**, and **teamInfo/teamId** properties. It doesn't support the use of the same property more than once in a query. For example, the following query doesn't work: `sharedOpenShift/startDateTime ge 2024-05-09T00:00:00Z and sharedOpenShift/startDateTime le 2024-05-09T23:59:59Z`; however, the following query works: `sharedOpenShift/startDateTime ge 2024-05-09T00:00:00Z and sharedOpenShift/endDateTime le 2024-05-09T23:59:59Z`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/me/joinedTeams/getOpenShifts
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.JoinedTeams["{team-id}"].GetAsync();
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
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
joinedTeams, err := graphClient.Me().JoinedTeams().ByTeamId("team-id").Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team result = graphClient.me().joinedTeams().byTeamId("{team-id}").get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getOpenShifts = await client.api('/me/joinedTeams/getOpenShifts')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->joinedTeams()->byTeamId('team-id')->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.joined_teams.by_team_id('team-id').get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "createdDateTime": "2019-03-14T04:32:51.451Z",
      "draftOpenShift": {
        "activities": [
          {
            "code": "Break",
            "displayName": "Lunch",
            "endDateTime": "2018-10-04T07:58:45.332Z",
            "isPaid": true,
            "startDateTime": "2018-10-04T00:58:45.340Z"
          }
        ],
        "displayName": "Day shift",
        "endDateTime": "2018-10-04T08:58:45.340Z",
        "notes": "Inventory Management",
        "openSlotCount": 3,
        "startDateTime": "2018-10-04T00:58:45.332Z",
        "theme": "white"
      },
      "id": "OPNSHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8",
      "lastModifiedBy": {
        "application": null,
        "conversation": null,
        "device": null,
        "user": {
          "displayName": "John Doe",
          "id": "366c0b19-49b1-41b5-a03f-9f3887bd0ed8"
        }
      },
      "lastModifiedDateTime": "2019-03-14T05:32:51.451Z",
      "schedulingGroupId": "TAG_228940ed-ff84-4e25-b129-1b395cf78be0",
      "sharedOpenShift": {
        "activities": [
          {
            "code": "",
            "displayName": "Lunch",
            "endDateTime": "2018-10-04T01:58:45.340Z",
            "isPaid": true,
            "startDateTime": "2018-10-04T00:58:45.340Z"
          }
        ],
        "displayName": "Day shift",
        "endDateTime": "2018-10-04T09:50:45.332Z",
        "notes": "Inventory Management",
        "openSlotCount": 2,
        "startDateTime": "2018-10-04T00:58:45.340Z",
        "theme": "white"
      },
      "schedulingGroupInfo": {
        "displayName": "Cashiers",
        "schedulingGroupId": "TAG_228940ed-ff84-4e25-b129-1b395cf78be0"
      },
      "teamInfo": {
        "displayName": "Contoso Team",
        "teamId": "172b0cce-e65d-44ce-9a49-91d9f2e8493a"
      }
    }
  ]
}
```
