<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-list-incomingchannels?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# List incomingChannels

Namespace: microsoft.graph

Get the list of incoming [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(channels shared with a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)\).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Channel.ReadBasic.All | ChannelSettings.Read.All, ChannelSettings.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Channel.ReadBasic.All | ChannelSettings.Read.All, ChannelSettings.ReadWrite.All |

> **Note**: This API supports admin permissions. Microsoft Teams service admins can access teams that they are not a member of.

## HTTP request

```http
GET /teams/{team-id}/incomingChannels
```

## Optional query parameters

This method supports the `$filter` and `$select` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) objects in the response body. The response also includes the **@odata.id** property which can be used to access the channel and run other operations on the [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) object.

When the result set spans multiple pages, the response includes an **@odata.nextLink** property with a URL for retrieving the next page of results. For details about how to page through results, see [Paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

Note

Currently, invoking the URL returned from the **@odata.id** property fails for cross-tenant shared channels. You can solve this issue if you remove the `/tenants/{tenant-id}` part from the URL before you call this API. For more details, see [Known issues with Microsoft Graph](https://learn.microsoft.com/en-us/graph/known-issues#unable-to-access-a-cross-tenant-shared-channel-when-the-request-url-contains-tenantscross-tenant-id).

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

```msgraph
GET https://graph.microsoft.com/v1.0/teams/893075dd-2487-4122-925f-022c42e20265/incomingChannels
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].IncomingChannels.GetAsync();
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
incomingChannels, err := graphClient.Teams().ByTeamId("team-id").IncomingChannels().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChannelCollectionResponse result = graphClient.teams().byTeamId("{team-id}").incomingChannels().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let incomingChannels = await client.api('/teams/893075dd-2487-4122-925f-022c42e20265/incomingChannels')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->teams()->byTeamId('team-id')->incomingChannels()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgTeamIncomingChannel -TeamId $teamId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.teams.by_team_id('team-id').incoming_channels.get()
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
      "@odata.id": "https://graph.microsoft.com/v1.0/tenants/b3246f44-b4gb-4627-96c6-25b18fa2c910/teams/893075dd-5678-4122-925f-022c42e20265/channels/19:561fbdbbfca848a484f0a6f00ce9dbbd@thread.tacv2",
      "id": "19:561fbdbbfca848a484f0a6f00ce9dbbd@thread.tacv2",
      "createdDateTime": "2020-05-27T19:22:25.692Z",
      "displayName": "Contoso Sales channel",
      "description": "channel created in Contoso to be shared with other teams/tenants.",
      "membershipType": "shared",
      "layoutType": null,
      "tenantId": "b3246f44-b4gb-4627-96c6-25b18fa2c910"
    }
  ]
}
```

Note

This API has a [known issue](https://learn.microsoft.com/en-us/graph/known-issues#layouttype-property-returns-null-when-listing-all-channels) related to listing channels. The **layoutType** property returns `null` when listing channels. To get the layout type of a specific channel, use the [Get channel](https://learn.microsoft.com/en-us/graph/api/channel-get?view=graph-rest-1.0) API. Full support for **layoutType** in list operations is planned for a future release.
