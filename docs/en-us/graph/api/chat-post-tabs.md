<!-- Source: https://learn.microsoft.com/en-us/graph/api/chat-post-tabs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Add tab to chat

Namespace: microsoft.graph

Add \(pin\) a [tab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) to the specified [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). The corresponding app must already be [installed in the chat](https://learn.microsoft.com/en-us/graph/api/chat-list-installedapps?view=graph-rest-1.0).

> **Notes**:
> 
> - If the chat is associated with an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) instance, then the tab is effectively added to the meeting.
> - If the app manifest for a given **appId** contains a static tab that matches the current scope \(`chat`/`groupChat`\), the static tab is pinned by default.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsTab.Create | TeamsTab.ReadWrite.All, TeamsTab.ReadWriteForChat, TeamsTab.ReadWriteSelfForChat |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsTab.Create | TeamsTab.Create.Chat, TeamsTab.ReadWrite.All, TeamsTab.ReadWrite.Chat, TeamsTab.ReadWriteForChat.All, TeamsTab.ReadWriteSelfForChat.All |

## HTTP request

```http
POST /chats/{chat-id}/tabs
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body include a JSON representation of a [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0).

Note

When you pin a static tab, Teams takes the **displayName** and **configuration** from the app manifest. If these properties are specified in the request body, this API returns a `400 Bad Request` response code.

## Response

If successful, this method returns a `201 Created` response code and an instance of the [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) resource in the body.

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
POST https://graph.microsoft.com/v1.0/chats/19:d65713bc498c4a428c71ef9353e6ce20@thread.v2/tabs
Content-Type: application/json

{
  "displayName": "My Contoso Tab",
  "teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8",
  "configuration": {
    "entityId": "2DCA2E6C7A10415CAF6B8AB6661B3154",
    "contentUrl": "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView",
    "websiteUrl": "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154",
    "removeUrl": "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new TeamsTab
{
	DisplayName = "My Contoso Tab",
	Configuration = new TeamsTabConfiguration
	{
		EntityId = "2DCA2E6C7A10415CAF6B8AB6661B3154",
		ContentUrl = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView",
		WebsiteUrl = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154",
		RemoveUrl = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab",
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Tabs.PostAsync(requestBody);
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

requestBody := graphmodels.NewTeamsTab()
displayName := "My Contoso Tab"
requestBody.SetDisplayName(&displayName) 
configuration := graphmodels.NewTeamsTabConfiguration()
entityId := "2DCA2E6C7A10415CAF6B8AB6661B3154"
configuration.SetEntityId(&entityId) 
contentUrl := "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView"
configuration.SetContentUrl(&contentUrl) 
websiteUrl := "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154"
configuration.SetWebsiteUrl(&websiteUrl) 
removeUrl := "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab"
configuration.SetRemoveUrl(&removeUrl) 
requestBody.SetConfiguration(configuration)
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
tabs, err := graphClient.Chats().ByChatId("chat-id").Tabs().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamsTab teamsTab = new TeamsTab();
teamsTab.setDisplayName("My Contoso Tab");
TeamsTabConfiguration configuration = new TeamsTabConfiguration();
configuration.setEntityId("2DCA2E6C7A10415CAF6B8AB6661B3154");
configuration.setContentUrl("https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView");
configuration.setWebsiteUrl("https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154");
configuration.setRemoveUrl("https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab");
teamsTab.setConfiguration(configuration);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8");
teamsTab.setAdditionalData(additionalData);
TeamsTab result = graphClient.chats().byChatId("{chat-id}").tabs().post(teamsTab);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const teamsTab = {
  displayName: 'My Contoso Tab',
  'teamsApp@odata.bind': 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8',
  configuration: {
    entityId: '2DCA2E6C7A10415CAF6B8AB6661B3154',
    contentUrl: 'https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView',
    websiteUrl: 'https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154',
    removeUrl: 'https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab'
  }
};

await client.api('/chats/19:d65713bc498c4a428c71ef9353e6ce20@thread.v2/tabs')
	.post(teamsTab);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\TeamsTab;
use Microsoft\Graph\Generated\Models\TeamsTabConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TeamsTab();
$requestBody->setDisplayName('My Contoso Tab');
$configuration = new TeamsTabConfiguration();
$configuration->setEntityId('2DCA2E6C7A10415CAF6B8AB6661B3154');
$configuration->setContentUrl('https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView');
$configuration->setWebsiteUrl('https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154');
$configuration->setRemoveUrl('https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab');
$requestBody->setConfiguration($configuration);
$additionalData = [
	'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->chats()->byChatId('chat-id')->tabs()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	displayName = "My Contoso Tab"
	"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8"
	configuration = @{
		entityId = "2DCA2E6C7A10415CAF6B8AB6661B3154"
		contentUrl = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView"
		websiteUrl = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154"
		removeUrl = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab"
	}
}

New-MgChatTab -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.teams_tab import TeamsTab
from msgraph.generated.models.teams_tab_configuration import TeamsTabConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TeamsTab(
	display_name = "My Contoso Tab",
	configuration = TeamsTabConfiguration(
		entity_id = "2DCA2E6C7A10415CAF6B8AB6661B3154",
		content_url = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView",
		website_url = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154",
		remove_url = "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab",
	),
	additional_data = {
			"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/06805b9e-77e3-4b93-ac81-525eb87513b8",
	}
)

result = await graph_client.chats.by_chat_id('chat-id').tabs.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "id": "794f0e4e-4d10-4bb5-9079-3a465a629eff",
  "displayName": "My Contoso Tab",
  "configuration": {
    "entityId": "2DCA2E6C7A10415CAF6B8AB6661B3154",
    "contentUrl": "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/tabView",
    "websiteUrl": "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154",
    "removeUrl": "https://www.contoso.com/Orders/2DCA2E6C7A10415CAF6B8AB6661B3154/uninstallTab"
  },
  "sortOrderIndex": "20",
  "webUrl": "https://teams.microsoft.com/l/entity/com.microsoft.teamspace.tab.web/_djb2_msteams_prefix_193fe248-24e6-478f-a66c-ede9ce6dd547?context=%7b%0d%0a++%22context%22%3a+%22chat%22%2c%0d%0a++%22chatId%22%3a+%2219%3ad65713bc498c4a428c71ef9353e6ce20%40thread.v2%22%2c%0d%0a++%22subEntityId%22%3a+null%0d%0a%7d&tenantId=139d16b4-7223-43ad-b9a8-674ba63c7924"
}
```

## Related content

- [Configuring the built-in tab types](https://learn.microsoft.com/en-us/graph/teams-configuring-builtin-tabs)
- [Add tab to channel](https://learn.microsoft.com/en-us/graph/api/channel-post-tabs?view=graph-rest-1.0)
- [Add app to chat](https://learn.microsoft.com/en-us/graph/api/chat-post-installedapps?view=graph-rest-1.0)
- [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
