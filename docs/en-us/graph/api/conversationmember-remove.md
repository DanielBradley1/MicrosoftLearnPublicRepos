<!-- Source: https://learn.microsoft.com/en-us/graph/api/conversationmember-remove?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# conversationMember: remove

Namespace: microsoft.graph

Remove multiple members from a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) in a single request. The response provides details about which memberships could and couldn't be removed.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamMember.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamMember.ReadWrite.All | Not available. |

## HTTP request

This API is a bound action to remove multiple elements from a [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection in a single request.

```http
POST /teams/{team-id}/members/remove
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the JSON representation of the list of **conversationMember** derivatives to be removed from a team. A maximum of 20 **conversationMember** derivatives can be removed in a single request.

The following table shows the parameter that you can use with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| values | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | A list of conversation members to remove. |

## Response

If successful, this method returns either a `204 No Content` response if all specified members were successfully removed from the team or a `207 Multi-Status` response if only some members were removed. The caller should inspect the response payload to identify which member removals failed. The response body contains a collection of derivatives of the [actionResultPart](https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-1.0) resource. If the request fails, the API returns an error. For more information about Microsoft Graph errors, see [Microsoft Graph error responses and resource types](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Example 1: Remove members in bulk from a team

The following example shows how to remove multiple members from a team in a single request.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/teams/e4183b04-c9a2-417c-bde4-70e3ee46a6dc/members/remove
Content-Type: application/json

{
    "values": [
        {
            "@odata.type": "microsoft.graph.aadUserConversationMember",
            "user@odata.bind": "https://graph.microsoft.com/v1.0/users('18a80140-b0fb-4489-b360-2f6efaf225a0')"
        },
        {
            "@odata.type": "microsoft.graph.aadUserConversationMember",
            "user@odata.bind": "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.Members.Remove;
using Microsoft.Graph.Models;

var requestBody = new RemovePostRequestBody
{
	Values = new List<ConversationMember>
	{
		new AadUserConversationMember
		{
			OdataType = "microsoft.graph.aadUserConversationMember",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('18a80140-b0fb-4489-b360-2f6efaf225a0')"
				},
			},
		},
		new AadUserConversationMember
		{
			OdataType = "microsoft.graph.aadUserConversationMember",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Members.Remove.PostAsRemovePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewRemovePostRequestBody()


conversationMember := graphmodels.NewAadUserConversationMember()
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('18a80140-b0fb-4489-b360-2f6efaf225a0')", 
}
conversationMember.SetAdditionalData(additionalData)
conversationMember1 := graphmodels.NewAadUserConversationMember()
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')", 
}
conversationMember1.SetAdditionalData(additionalData)

values := []graphmodels.ConversationMemberable {
	conversationMember,
	conversationMember1,
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remove, err := graphClient.Teams().ByTeamId("team-id").Members().Remove().PostAsRemovePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.members.remove.RemovePostRequestBody removePostRequestBody = new com.microsoft.graph.teams.item.members.remove.RemovePostRequestBody();
LinkedList<ConversationMember> values = new LinkedList<ConversationMember>();
AadUserConversationMember conversationMember = new AadUserConversationMember();
conversationMember.setOdataType("microsoft.graph.aadUserConversationMember");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('18a80140-b0fb-4489-b360-2f6efaf225a0')");
conversationMember.setAdditionalData(additionalData);
values.add(conversationMember);
AadUserConversationMember conversationMember1 = new AadUserConversationMember();
conversationMember1.setOdataType("microsoft.graph.aadUserConversationMember");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')");
conversationMember1.setAdditionalData(additionalData1);
values.add(conversationMember1);
removePostRequestBody.setValues(values);
var result = graphClient.teams().byTeamId("{team-id}").members().remove().post(removePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const actionResultPart = {
    values: [
        {
            '@odata.type': 'microsoft.graph.aadUserConversationMember',
            'user@odata.bind': 'https://graph.microsoft.com/v1.0/users(\'18a80140-b0fb-4489-b360-2f6efaf225a0\')'
        },
        {
            '@odata.type': 'microsoft.graph.aadUserConversationMember',
            'user@odata.bind': 'https://graph.microsoft.com/v1.0/users(\'86503198-b81b-43fe-81ee-ad45b8848ac9\')'
        }
    ]
};

await client.api('/teams/e4183b04-c9a2-417c-bde4-70e3ee46a6dc/members/remove')
	.post(actionResultPart);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Members\Remove\RemovePostRequestBody;
use Microsoft\Graph\Generated\Models\ConversationMember;
use Microsoft\Graph\Generated\Models\AadUserConversationMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemovePostRequestBody();
$valuesConversationMember1 = new AadUserConversationMember();
$valuesConversationMember1->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'18a80140-b0fb-4489-b360-2f6efaf225a0\')',
];
$valuesConversationMember1->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember1;
$valuesConversationMember2 = new AadUserConversationMember();
$valuesConversationMember2->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'86503198-b81b-43fe-81ee-ad45b8848ac9\')',
];
$valuesConversationMember2->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember2;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->members()->remove()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.members.remove.remove_post_request_body import RemovePostRequestBody
from msgraph.generated.models.conversation_member import ConversationMember
from msgraph.generated.models.aad_user_conversation_member import AadUserConversationMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemovePostRequestBody(
	values = [
		AadUserConversationMember(
			odata_type = "microsoft.graph.aadUserConversationMember",
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('18a80140-b0fb-4489-b360-2f6efaf225a0')",
			}
		),
		AadUserConversationMember(
			odata_type = "microsoft.graph.aadUserConversationMember",
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')",
			}
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').members.remove.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Remove members in bulk from a team using user principal name

The following example shows how to remove multiple members from a team in a single request using their user principal names.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/teams/e4183b04-c9a2-417c-bde4-70e3ee46a6dc/members/remove
Content-Type: application/json

{
    "values": [
        {
            "@odata.type": "microsoft.graph.aadUserConversationMember",
            "user@odata.bind": "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')"
        },
        {
            "@odata.type": "microsoft.graph.aadUserConversationMember",
            "user@odata.bind": "https://graph.microsoft.com/v1.0/users('alex@contoso.com')"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.Members.Remove;
using Microsoft.Graph.Models;

var requestBody = new RemovePostRequestBody
{
	Values = new List<ConversationMember>
	{
		new AadUserConversationMember
		{
			OdataType = "microsoft.graph.aadUserConversationMember",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')"
				},
			},
		},
		new AadUserConversationMember
		{
			OdataType = "microsoft.graph.aadUserConversationMember",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('alex@contoso.com')"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Members.Remove.PostAsRemovePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewRemovePostRequestBody()


conversationMember := graphmodels.NewAadUserConversationMember()
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')", 
}
conversationMember.SetAdditionalData(additionalData)
conversationMember1 := graphmodels.NewAadUserConversationMember()
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('alex@contoso.com')", 
}
conversationMember1.SetAdditionalData(additionalData)

values := []graphmodels.ConversationMemberable {
	conversationMember,
	conversationMember1,
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remove, err := graphClient.Teams().ByTeamId("team-id").Members().Remove().PostAsRemovePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.members.remove.RemovePostRequestBody removePostRequestBody = new com.microsoft.graph.teams.item.members.remove.RemovePostRequestBody();
LinkedList<ConversationMember> values = new LinkedList<ConversationMember>();
AadUserConversationMember conversationMember = new AadUserConversationMember();
conversationMember.setOdataType("microsoft.graph.aadUserConversationMember");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')");
conversationMember.setAdditionalData(additionalData);
values.add(conversationMember);
AadUserConversationMember conversationMember1 = new AadUserConversationMember();
conversationMember1.setOdataType("microsoft.graph.aadUserConversationMember");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('alex@contoso.com')");
conversationMember1.setAdditionalData(additionalData1);
values.add(conversationMember1);
removePostRequestBody.setValues(values);
var result = graphClient.teams().byTeamId("{team-id}").members().remove().post(removePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const actionResultPart = {
    values: [
        {
            '@odata.type': 'microsoft.graph.aadUserConversationMember',
            'user@odata.bind': 'https://graph.microsoft.com/v1.0/users(\'jacob@contoso.com\')'
        },
        {
            '@odata.type': 'microsoft.graph.aadUserConversationMember',
            'user@odata.bind': 'https://graph.microsoft.com/v1.0/users(\'alex@contoso.com\')'
        }
    ]
};

await client.api('/teams/e4183b04-c9a2-417c-bde4-70e3ee46a6dc/members/remove')
	.post(actionResultPart);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Members\Remove\RemovePostRequestBody;
use Microsoft\Graph\Generated\Models\ConversationMember;
use Microsoft\Graph\Generated\Models\AadUserConversationMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemovePostRequestBody();
$valuesConversationMember1 = new AadUserConversationMember();
$valuesConversationMember1->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'jacob@contoso.com\')',
];
$valuesConversationMember1->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember1;
$valuesConversationMember2 = new AadUserConversationMember();
$valuesConversationMember2->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'alex@contoso.com\')',
];
$valuesConversationMember2->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember2;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->members()->remove()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.members.remove.remove_post_request_body import RemovePostRequestBody
from msgraph.generated.models.conversation_member import ConversationMember
from msgraph.generated.models.aad_user_conversation_member import AadUserConversationMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemovePostRequestBody(
	values = [
		AadUserConversationMember(
			odata_type = "microsoft.graph.aadUserConversationMember",
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')",
			}
		),
		AadUserConversationMember(
			odata_type = "microsoft.graph.aadUserConversationMember",
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('alex@contoso.com')",
			}
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').members.remove.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Remove members in bulk from a team with failed removals

The following example shows how to remove multiple members from a team when the removal of a member fails.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/teams/e4183b04-c9a2-417c-bde4-70e3ee46a6dc/members/remove
Content-Type: application/json

{
    "values": [
        {
            "@odata.type": "microsoft.graph.aadUserConversationMember",
            "user@odata.bind": "https://graph.microsoft.com/v1.0/users('c04f28bf-ab68-40a2-974b-e6af31fa78fb')"
        },
        {
            "@odata.type": "microsoft.graph.aadUserConversationMember",
            "user@odata.bind": "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.Members.Remove;
using Microsoft.Graph.Models;

var requestBody = new RemovePostRequestBody
{
	Values = new List<ConversationMember>
	{
		new AadUserConversationMember
		{
			OdataType = "microsoft.graph.aadUserConversationMember",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('c04f28bf-ab68-40a2-974b-e6af31fa78fb')"
				},
			},
		},
		new AadUserConversationMember
		{
			OdataType = "microsoft.graph.aadUserConversationMember",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Members.Remove.PostAsRemovePostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewRemovePostRequestBody()


conversationMember := graphmodels.NewAadUserConversationMember()
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('c04f28bf-ab68-40a2-974b-e6af31fa78fb')", 
}
conversationMember.SetAdditionalData(additionalData)
conversationMember1 := graphmodels.NewAadUserConversationMember()
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')", 
}
conversationMember1.SetAdditionalData(additionalData)

values := []graphmodels.ConversationMemberable {
	conversationMember,
	conversationMember1,
}
requestBody.SetValues(values)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
remove, err := graphClient.Teams().ByTeamId("team-id").Members().Remove().PostAsRemovePostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.members.remove.RemovePostRequestBody removePostRequestBody = new com.microsoft.graph.teams.item.members.remove.RemovePostRequestBody();
LinkedList<ConversationMember> values = new LinkedList<ConversationMember>();
AadUserConversationMember conversationMember = new AadUserConversationMember();
conversationMember.setOdataType("microsoft.graph.aadUserConversationMember");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('c04f28bf-ab68-40a2-974b-e6af31fa78fb')");
conversationMember.setAdditionalData(additionalData);
values.add(conversationMember);
AadUserConversationMember conversationMember1 = new AadUserConversationMember();
conversationMember1.setOdataType("microsoft.graph.aadUserConversationMember");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')");
conversationMember1.setAdditionalData(additionalData1);
values.add(conversationMember1);
removePostRequestBody.setValues(values);
var result = graphClient.teams().byTeamId("{team-id}").members().remove().post(removePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const actionResultPart = {
    values: [
        {
            '@odata.type': 'microsoft.graph.aadUserConversationMember',
            'user@odata.bind': 'https://graph.microsoft.com/v1.0/users(\'c04f28bf-ab68-40a2-974b-e6af31fa78fb\')'
        },
        {
            '@odata.type': 'microsoft.graph.aadUserConversationMember',
            'user@odata.bind': 'https://graph.microsoft.com/v1.0/users(\'86503198-b81b-43fe-81ee-ad45b8848ac9\')'
        }
    ]
};

await client.api('/teams/e4183b04-c9a2-417c-bde4-70e3ee46a6dc/members/remove')
	.post(actionResultPart);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Members\Remove\RemovePostRequestBody;
use Microsoft\Graph\Generated\Models\ConversationMember;
use Microsoft\Graph\Generated\Models\AadUserConversationMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new RemovePostRequestBody();
$valuesConversationMember1 = new AadUserConversationMember();
$valuesConversationMember1->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'c04f28bf-ab68-40a2-974b-e6af31fa78fb\')',
];
$valuesConversationMember1->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember1;
$valuesConversationMember2 = new AadUserConversationMember();
$valuesConversationMember2->setOdataType('microsoft.graph.aadUserConversationMember');
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'86503198-b81b-43fe-81ee-ad45b8848ac9\')',
];
$valuesConversationMember2->setAdditionalData($additionalData);
$valuesArray []= $valuesConversationMember2;
$requestBody->setValues($valuesArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->members()->remove()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.members.remove.remove_post_request_body import RemovePostRequestBody
from msgraph.generated.models.conversation_member import ConversationMember
from msgraph.generated.models.aad_user_conversation_member import AadUserConversationMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = RemovePostRequestBody(
	values = [
		AadUserConversationMember(
			odata_type = "microsoft.graph.aadUserConversationMember",
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('c04f28bf-ab68-40a2-974b-e6af31fa78fb')",
			}
		),
		AadUserConversationMember(
			odata_type = "microsoft.graph.aadUserConversationMember",
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('86503198-b81b-43fe-81ee-ad45b8848ac9')",
			}
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').members.remove.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 207 Multi-Status
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.aadUserConversationMemberResult)",
    "value": [
        {
            "@odata.type": "#microsoft.graph.aadUserConversationMemberResult",
            "userId": "c04f28bf-ab68-40a2-974b-e6af31fa78fb",
            "error": {
                "code": "NotFound",
                "message": "Could not find resource"
            }
        },
        {
            "@odata.type": "#microsoft.graph.aadUserConversationMemberResult",
            "userId": "86503198-b81b-43fe-81ee-ad45b8848ac9",
            "error": null
        }
    ]
}
```

## Related content

[Remove member from team](https://learn.microsoft.com/en-us/graph/api/team-delete-members?view=graph-rest-1.0)
