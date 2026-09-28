<!-- Source: https://learn.microsoft.com/en-us/graph/api/chat-removeallaccessforuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# chat: removeAllAccessForUser

Namespace: microsoft.graph

Remove access to a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) for a user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Chat.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /chats/{chatsId}/removeAllAccessForUser
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| user | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) | User whose chat access to remove. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/chats/{chatsId}/removeAllAccessForUser
Content-Type: application/json

{
  "user": {
    "@odata.type": "microsoft.graph.teamworkUserIdentity",
    "id": "f47ac10b-58cc-4372-a567-0e02b2c3d479",
    "tenantId": "a1b2c3d4-e5f6-7890-1234-567890abcdef"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Chats.Item.RemoveAllAccessForUser;
using Microsoft.Graph.Models;

var requestBody = new RemoveAllAccessForUserPostRequestBody
{
	User = new TeamworkUserIdentity
	{
		OdataType = "microsoft.graph.teamworkUserIdentity",
		Id = "f47ac10b-58cc-4372-a567-0e02b2c3d479",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"tenantId" , "a1b2c3d4-e5f6-7890-1234-567890abcdef"
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Chats["{chat-id}"].RemoveAllAccessForUser.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphchats "github.com/microsoftgraph/msgraph-sdk-go/chats"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphchats.NewRemoveAllAccessForUserPostRequestBody()
user := graphmodels.NewTeamworkUserIdentity()
id := "f47ac10b-58cc-4372-a567-0e02b2c3d479"
user.SetId(&id) 
additionalData := map[string]interface{}{
	"tenantId" : "a1b2c3d4-e5f6-7890-1234-567890abcdef", 
}
user.SetAdditionalData(additionalData)
requestBody.SetUser(user)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Chats().ByChatId("chat-id").RemoveAllAccessForUser().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.chats.item.removeallaccessforuser.RemoveAllAccessForUserPostRequestBody removeAllAccessForUserPostRequestBody = new com.microsoft.graph.chats.item.removeallaccessforuser.RemoveAllAccessForUserPostRequestBody();
TeamworkUserIdentity user = new TeamworkUserIdentity();
user.setOdataType("microsoft.graph.teamworkUserIdentity");
user.setId("f47ac10b-58cc-4372-a567-0e02b2c3d479");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("tenantId", "a1b2c3d4-e5f6-7890-1234-567890abcdef");
user.setAdditionalData(additionalData);
removeAllAccessForUserPostRequestBody.setUser(user);
graphClient.chats().byChatId("{chat-id}").removeAllAccessForUser().post(removeAllAccessForUserPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const removeAllAccessForUser = {
  user: {
    '@odata.type': 'microsoft.graph.teamworkUserIdentity',
    id: 'f47ac10b-58cc-4372-a567-0e02b2c3d479',
    tenantId: 'a1b2c3d4-e5f6-7890-1234-567890abcdef'
  }
};

await client.api('/chats/{chatsId}/removeAllAccessForUser')
	.post(removeAllAccessForUser);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Chats\Item\RemoveAllAccessForUser\RemoveAllAccessForUserPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkUserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemoveAllAccessForUserPostRequestBody();
$user = new TeamworkUserIdentity();
$user->setOdataType('microsoft.graph.teamworkUserIdentity');
$user->setId('f47ac10b-58cc-4372-a567-0e02b2c3d479');
$additionalData = [
	'tenantId' => 'a1b2c3d4-e5f6-7890-1234-567890abcdef',
];
$user->setAdditionalData($additionalData);
$requestBody->setUser($user);

$graphServiceClient->chats()->byChatId('chat-id')->removeAllAccessForUser()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	user = @{
		"@odata.type" = "microsoft.graph.teamworkUserIdentity"
		id = "f47ac10b-58cc-4372-a567-0e02b2c3d479"
		tenantId = "a1b2c3d4-e5f6-7890-1234-567890abcdef"
	}
}

Remove-MgChatAccessForUser -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.chats.item.remove_all_access_for_user.remove_all_access_for_user_post_request_body import RemoveAllAccessForUserPostRequestBody
from msgraph.generated.models.teamwork_user_identity import TeamworkUserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemoveAllAccessForUserPostRequestBody(
	user = TeamworkUserIdentity(
		odata_type = "microsoft.graph.teamworkUserIdentity",
		id = "f47ac10b-58cc-4372-a567-0e02b2c3d479",
		additional_data = {
				"tenant_id" : "a1b2c3d4-e5f6-7890-1234-567890abcdef",
		}
	),
)

await graph_client.chats.by_chat_id('chat-id').remove_all_access_for_user.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
