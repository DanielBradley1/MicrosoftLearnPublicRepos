<!-- Source: https://learn.microsoft.com/en-us/graph/api/channel-archive?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-14 -->

# channel: archive

Namespace: microsoft.graph

Archive a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) in a team. When a channel is archived, users can't send new messages or react to existing messages in the channel, edit the channel settings, or make other changes to the channel.

You can delete an archived channel or add and remove members from it. If you archive a team, its channels are also archived.

Archiving is an asynchronous operation; a channel is archived after the asynchronous archiving operation completes successfully, which might occur after the response returns.

A channel without an owner or that belongs to a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) that has no owner, can't be archived.

To restore a channel from its archived state, use the [channel: unarchive](https://learn.microsoft.com/en-us/graph/api/channel-unarchive?view=graph-rest-1.0) method. A channel can’t be archived or unarchived if its team is archived.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ChannelSettings.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ChannelSettings.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with the Global Administrator or Microsoft Teams service admin roles can access teams that they aren't members of.

## HTTP request

```http
POST /teams/{team-id}/channels/{channel-id}/archive
POST /groups/{team-id}/team/channels/{channel-id}/archive
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Optional. |

## Request body

In the request body, you can optionally provide a JSON object with the following parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| shouldSetSpoSiteReadOnlyForMembers | Boolean | Defines whether to set permissions for channel members to read-only on the SharePoint Online site associated with the team. If you set it to `false` or omit the parameter, this step is skipped. |

The following example shows the request body with **shouldSetSpoSiteReadOnlyForMembers** set to `true`.

```json
{
  "shouldSetSpoSiteReadOnlyForMembers": true
}
```

## Response

If archiving is started successfully, this method returns a `202 Accepted` response code. The response contains a `Location` header that specifies the location of the [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) that was created to handle the archiving of the channel in a team. Check the status of the archiving operation by making a GET request to this location.

## Examples

### Example 1: Archive a channel

The following example shows a request to archive a channel.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/teams/16dc05c0-2259-4540-a970-3580ff459721/channels/19:v32db348d9264477abcf18ffa2cf76dc@thread.tacv2/archive
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Archive.PostAsync(null);
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
graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Archive().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").archive().post(null);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/teams/16dc05c0-2259-4540-a970-3580ff459721/channels/19:v32db348d9264477abcf18ffa2cf76dc@thread.tacv2/archive')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->archive()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Invoke-MgArchiveTeamChannel -TeamId $teamId -ChannelId $channelId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').archive.post(None)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Location: /teams/16dc05c0-2259-4540-a970-3580ff459721/operations/b7ee702a-d87f-4cc6-82b9-e731c16d3aba
Content-Type: text/plain
Content-Length: 0
```

### Example 2: Archive a channel when the team is archived

The following example shows a request to archive a channel that fails because the team is archived; the team must be active to archive or unarchive a channel.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/teams/16dc05c0-2259-4540-a970-3580ff459721/channels/19:v32db348d9264477abcf18ffa2cf76dc@thread.tacv2/archive
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Archive.PostAsync(null);
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
graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Archive().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").archive().post(null);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/teams/16dc05c0-2259-4540-a970-3580ff459721/channels/19:v32db348d9264477abcf18ffa2cf76dc@thread.tacv2/archive')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->archive()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Invoke-MgArchiveTeamChannel -TeamId $teamId -ChannelId $channelId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').archive.post(None)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the `400 Bad Request` response code with a corresponding error message.

```http
http/1.1 400 Bad Request
Content-Type: application/json
Content-Length: 193

{
    "error": {
        "code": "BadRequest",
        "message": "Team has to be active, for channel to be archived or unarchived: {channel-id}",
        "innerError": {
            "message": "Team has to be active, for channel to be archived or unarchived: {channel-id}",
            "code": "Unknown",
            "innerError": {},
            "date": "2023-12-11T04:26:35",
            "request-id": "8f897345980-f6f3-49dd-83a8-a3064eeecdf8",
            "client-request-id": "50a0er33-4567-3f6c-01bf-04d144fc8bbe"
        }
    }
}
```
