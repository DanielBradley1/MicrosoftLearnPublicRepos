<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamwork-determineifinteractionisallowed?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-14 -->

# teamwork: determineIfInteractionIsAllowed

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Determine if a specified Microsoft Teams interaction is allowed between the signed-in user and specified users.

> **Note**: All requests to this API are logged in the Microsoft 365 audit logs of the tenants where the targeted users specified by the **users** parameter exist. For more information, see [Audit log activities](https://learn.microsoft.com/en-us/purview/audit-log-activities#microsoft-teams-activities).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkUserInteraction.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /teamwork/determineIfInteractionIsAllowed
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that you can use with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| interactionType | [teamworkInteractionType](https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-beta#teamworkinteractiontype-values) | The type of interaction on Microsoft Teams. |
| users | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) collection | The collection of target users with which the caller wants to determine whether interaction is allowed. The supported derived types are [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-beta) and [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-beta). |

## Response

If successful, this action returns a `200 OK` response code and a Boolean in the response body.

## Examples

### Example 1: Determine if the signed-in user can create a chat with another user in the same tenant using their ID

The following example shows a request that determines whether the signed-in user, authenticated via delegated context, can create a chat with another user in the same tenant by specifying the other user's ID.

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

```http
POST https://graph.microsoft.com/beta/teamwork/determineIfInteractionIsAllowed

{
  "users":
  [
    {
      "@odata.type": "microsoft.graph.teamworkUserIdentity",
      "id": "59b5bc69-ca73-4ffd-a2e0-88a79115d13b"
    }
  ],
  "interactionType": "createChat"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Teamwork.DetermineIfInteractionIsAllowed;
using Microsoft.Graph.Beta.Models;

var requestBody = new DetermineIfInteractionIsAllowedPostRequestBody
{
	Users = new List<Identity>
	{
		new TeamworkUserIdentity
		{
			OdataType = "microsoft.graph.teamworkUserIdentity",
			Id = "59b5bc69-ca73-4ffd-a2e0-88a79115d13b",
		},
	},
	InteractionType = TeamworkInteractionType.CreateChat,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teamwork.DetermineIfInteractionIsAllowed.PostAsDetermineIfInteractionIsAllowedPostResponseAsync(requestBody);
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
	  graphteamwork "github.com/microsoftgraph/msgraph-beta-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewDetermineIfInteractionIsAllowedPostRequestBody()


identity := graphmodels.NewTeamworkUserIdentity()
id := "59b5bc69-ca73-4ffd-a2e0-88a79115d13b"
identity.SetId(&id) 

users := []graphmodels.Identityable {
	identity,
}
requestBody.SetUsers(users)
interactionType := graphmodels.CREATECHAT_TEAMWORKINTERACTIONTYPE 
requestBody.SetInteractionType(&interactionType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
determineIfInteractionIsAllowed, err := graphClient.Teamwork().DetermineIfInteractionIsAllowed().PostAsDetermineIfInteractionIsAllowedPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody determineIfInteractionIsAllowedPostRequestBody = new com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody();
LinkedList<Identity> users = new LinkedList<Identity>();
TeamworkUserIdentity identity = new TeamworkUserIdentity();
identity.setOdataType("microsoft.graph.teamworkUserIdentity");
identity.setId("59b5bc69-ca73-4ffd-a2e0-88a79115d13b");
users.add(identity);
determineIfInteractionIsAllowedPostRequestBody.setUsers(users);
determineIfInteractionIsAllowedPostRequestBody.setInteractionType(TeamworkInteractionType.CreateChat);
var result = graphClient.teamwork().determineIfInteractionIsAllowed().post(determineIfInteractionIsAllowedPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _boolean = {
  users: 
  [
    {
      '@odata.type': 'microsoft.graph.teamworkUserIdentity',
      id: '59b5bc69-ca73-4ffd-a2e0-88a79115d13b'
    }
  ],
  interactionType: 'createChat'
};

await client.api('/teamwork/determineIfInteractionIsAllowed')
	.version('beta')
	.post(_boolean);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teamwork\DetermineIfInteractionIsAllowed\DetermineIfInteractionIsAllowedPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkUserIdentity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkInteractionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DetermineIfInteractionIsAllowedPostRequestBody();
$usersIdentity1 = new TeamworkUserIdentity();
$usersIdentity1->setOdataType('microsoft.graph.teamworkUserIdentity');
$usersIdentity1->setId('59b5bc69-ca73-4ffd-a2e0-88a79115d13b');
$usersArray []= $usersIdentity1;
$requestBody->setUsers($usersArray);

$requestBody->setInteractionType(new TeamworkInteractionType('createChat'));

$result = $graphServiceClient->teamwork()->determineIfInteractionIsAllowed()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	users = @(
		@{
			"@odata.type" = "microsoft.graph.teamworkUserIdentity"
			id = "59b5bc69-ca73-4ffd-a2e0-88a79115d13b"
		}
	)
	interactionType = "createChat"
}

Invoke-MgBetaDetermineTeamworkIfInteractionIsAllowed -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.teamwork.determine_if_interaction_is_allowed.determine_if_interaction_is_allowed_post_request_body import DetermineIfInteractionIsAllowedPostRequestBody
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.teamwork_user_identity import TeamworkUserIdentity
from msgraph_beta.generated.models.teamwork_interaction_type import TeamworkInteractionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DetermineIfInteractionIsAllowedPostRequestBody(
	users = [
		TeamworkUserIdentity(
			odata_type = "microsoft.graph.teamworkUserIdentity",
			id = "59b5bc69-ca73-4ffd-a2e0-88a79115d13b",
		),
	],
	interaction_type = TeamworkInteractionType.CreateChat,
)

result = await graph_client.teamwork.determine_if_interaction_is_allowed.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Edm.Boolean",
  "value": true
}
```

### Example 2: Determine if the signed-in user can create a chat with another user in a different tenant using their ID and tenant ID

The following example shows a request that determines whether the signed-in user, authenticated via delegated context, can create a chat with another user in a different tenant using the other user's ID and tenant ID.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/teamwork/determineIfInteractionIsAllowed

{
  "users":
  [
    {
      "@odata.type": "microsoft.graph.teamworkUserIdentity",
      "id": "59b5bc69-ca73-4ffd-a2e0-88a79115d13b",
      "tenantId": "b11186db-6149-4b3d-95ad-23c9e1bf6853"
    }
  ],
  "interactionType": "createChat"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Teamwork.DetermineIfInteractionIsAllowed;
using Microsoft.Graph.Beta.Models;

var requestBody = new DetermineIfInteractionIsAllowedPostRequestBody
{
	Users = new List<Identity>
	{
		new TeamworkUserIdentity
		{
			OdataType = "microsoft.graph.teamworkUserIdentity",
			Id = "59b5bc69-ca73-4ffd-a2e0-88a79115d13b",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"tenantId" , "b11186db-6149-4b3d-95ad-23c9e1bf6853"
				},
			},
		},
	},
	InteractionType = TeamworkInteractionType.CreateChat,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teamwork.DetermineIfInteractionIsAllowed.PostAsDetermineIfInteractionIsAllowedPostResponseAsync(requestBody);
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
	  graphteamwork "github.com/microsoftgraph/msgraph-beta-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewDetermineIfInteractionIsAllowedPostRequestBody()


identity := graphmodels.NewTeamworkUserIdentity()
id := "59b5bc69-ca73-4ffd-a2e0-88a79115d13b"
identity.SetId(&id) 
additionalData := map[string]interface{}{
	"tenantId" : "b11186db-6149-4b3d-95ad-23c9e1bf6853", 
}
identity.SetAdditionalData(additionalData)

users := []graphmodels.Identityable {
	identity,
}
requestBody.SetUsers(users)
interactionType := graphmodels.CREATECHAT_TEAMWORKINTERACTIONTYPE 
requestBody.SetInteractionType(&interactionType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
determineIfInteractionIsAllowed, err := graphClient.Teamwork().DetermineIfInteractionIsAllowed().PostAsDetermineIfInteractionIsAllowedPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody determineIfInteractionIsAllowedPostRequestBody = new com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody();
LinkedList<Identity> users = new LinkedList<Identity>();
TeamworkUserIdentity identity = new TeamworkUserIdentity();
identity.setOdataType("microsoft.graph.teamworkUserIdentity");
identity.setId("59b5bc69-ca73-4ffd-a2e0-88a79115d13b");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("tenantId", "b11186db-6149-4b3d-95ad-23c9e1bf6853");
identity.setAdditionalData(additionalData);
users.add(identity);
determineIfInteractionIsAllowedPostRequestBody.setUsers(users);
determineIfInteractionIsAllowedPostRequestBody.setInteractionType(TeamworkInteractionType.CreateChat);
var result = graphClient.teamwork().determineIfInteractionIsAllowed().post(determineIfInteractionIsAllowedPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _boolean = {
  users: 
  [
    {
      '@odata.type': 'microsoft.graph.teamworkUserIdentity',
      id: '59b5bc69-ca73-4ffd-a2e0-88a79115d13b',
      tenantId: 'b11186db-6149-4b3d-95ad-23c9e1bf6853'
    }
  ],
  interactionType: 'createChat'
};

await client.api('/teamwork/determineIfInteractionIsAllowed')
	.version('beta')
	.post(_boolean);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teamwork\DetermineIfInteractionIsAllowed\DetermineIfInteractionIsAllowedPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkUserIdentity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkInteractionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DetermineIfInteractionIsAllowedPostRequestBody();
$usersIdentity1 = new TeamworkUserIdentity();
$usersIdentity1->setOdataType('microsoft.graph.teamworkUserIdentity');
$usersIdentity1->setId('59b5bc69-ca73-4ffd-a2e0-88a79115d13b');
$additionalData = [
	'tenantId' => 'b11186db-6149-4b3d-95ad-23c9e1bf6853',
];
$usersIdentity1->setAdditionalData($additionalData);
$usersArray []= $usersIdentity1;
$requestBody->setUsers($usersArray);

$requestBody->setInteractionType(new TeamworkInteractionType('createChat'));

$result = $graphServiceClient->teamwork()->determineIfInteractionIsAllowed()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	users = @(
		@{
			"@odata.type" = "microsoft.graph.teamworkUserIdentity"
			id = "59b5bc69-ca73-4ffd-a2e0-88a79115d13b"
			tenantId = "b11186db-6149-4b3d-95ad-23c9e1bf6853"
		}
	)
	interactionType = "createChat"
}

Invoke-MgBetaDetermineTeamworkIfInteractionIsAllowed -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.teamwork.determine_if_interaction_is_allowed.determine_if_interaction_is_allowed_post_request_body import DetermineIfInteractionIsAllowedPostRequestBody
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.teamwork_user_identity import TeamworkUserIdentity
from msgraph_beta.generated.models.teamwork_interaction_type import TeamworkInteractionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DetermineIfInteractionIsAllowedPostRequestBody(
	users = [
		TeamworkUserIdentity(
			odata_type = "microsoft.graph.teamworkUserIdentity",
			id = "59b5bc69-ca73-4ffd-a2e0-88a79115d13b",
			additional_data = {
					"tenant_id" : "b11186db-6149-4b3d-95ad-23c9e1bf6853",
			}
		),
	],
	interaction_type = TeamworkInteractionType.CreateChat,
)

result = await graph_client.teamwork.determine_if_interaction_is_allowed.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Edm.Boolean",
  "value": true
}
```

### Example 3: Determine if the signed-in user can create a chat with another user using their user principal name

The following example shows a request that determines whether the signed-in user, authenticated via delegated context, can create a chat with another user by specifying the other user's user principal name. When you specify the user principal name of a user in another tenant, **tenantId** doesn't need to be specified.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/beta/teamwork/determineIfInteractionIsAllowed

{
  "users":
  [
    {
      "@odata.type": "microsoft.graph.teamworkUserIdentity",
      "userPrincipalName": "maia@contoso.com"
    }
  ],
  "interactionType": "createChat"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Teamwork.DetermineIfInteractionIsAllowed;
using Microsoft.Graph.Beta.Models;

var requestBody = new DetermineIfInteractionIsAllowedPostRequestBody
{
	Users = new List<Identity>
	{
		new TeamworkUserIdentity
		{
			OdataType = "microsoft.graph.teamworkUserIdentity",
			UserPrincipalName = "maia@contoso.com",
		},
	},
	InteractionType = TeamworkInteractionType.CreateChat,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teamwork.DetermineIfInteractionIsAllowed.PostAsDetermineIfInteractionIsAllowedPostResponseAsync(requestBody);
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
	  graphteamwork "github.com/microsoftgraph/msgraph-beta-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewDetermineIfInteractionIsAllowedPostRequestBody()


identity := graphmodels.NewTeamworkUserIdentity()
userPrincipalName := "maia@contoso.com"
identity.SetUserPrincipalName(&userPrincipalName) 

users := []graphmodels.Identityable {
	identity,
}
requestBody.SetUsers(users)
interactionType := graphmodels.CREATECHAT_TEAMWORKINTERACTIONTYPE 
requestBody.SetInteractionType(&interactionType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
determineIfInteractionIsAllowed, err := graphClient.Teamwork().DetermineIfInteractionIsAllowed().PostAsDetermineIfInteractionIsAllowedPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody determineIfInteractionIsAllowedPostRequestBody = new com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody();
LinkedList<Identity> users = new LinkedList<Identity>();
TeamworkUserIdentity identity = new TeamworkUserIdentity();
identity.setOdataType("microsoft.graph.teamworkUserIdentity");
identity.setUserPrincipalName("maia@contoso.com");
users.add(identity);
determineIfInteractionIsAllowedPostRequestBody.setUsers(users);
determineIfInteractionIsAllowedPostRequestBody.setInteractionType(TeamworkInteractionType.CreateChat);
var result = graphClient.teamwork().determineIfInteractionIsAllowed().post(determineIfInteractionIsAllowedPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _boolean = {
  users: 
  [
    {
      '@odata.type': 'microsoft.graph.teamworkUserIdentity',
      userPrincipalName: 'maia@contoso.com'
    }
  ],
  interactionType: 'createChat'
};

await client.api('/teamwork/determineIfInteractionIsAllowed')
	.version('beta')
	.post(_boolean);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teamwork\DetermineIfInteractionIsAllowed\DetermineIfInteractionIsAllowedPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkUserIdentity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkInteractionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DetermineIfInteractionIsAllowedPostRequestBody();
$usersIdentity1 = new TeamworkUserIdentity();
$usersIdentity1->setOdataType('microsoft.graph.teamworkUserIdentity');
$usersIdentity1->setUserPrincipalName('maia@contoso.com');
$usersArray []= $usersIdentity1;
$requestBody->setUsers($usersArray);

$requestBody->setInteractionType(new TeamworkInteractionType('createChat'));

$result = $graphServiceClient->teamwork()->determineIfInteractionIsAllowed()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	users = @(
		@{
			"@odata.type" = "microsoft.graph.teamworkUserIdentity"
			userPrincipalName = "maia@contoso.com"
		}
	)
	interactionType = "createChat"
}

Invoke-MgBetaDetermineTeamworkIfInteractionIsAllowed -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.teamwork.determine_if_interaction_is_allowed.determine_if_interaction_is_allowed_post_request_body import DetermineIfInteractionIsAllowedPostRequestBody
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.teamwork_user_identity import TeamworkUserIdentity
from msgraph_beta.generated.models.teamwork_interaction_type import TeamworkInteractionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DetermineIfInteractionIsAllowedPostRequestBody(
	users = [
		TeamworkUserIdentity(
			odata_type = "microsoft.graph.teamworkUserIdentity",
			user_principal_name = "maia@contoso.com",
		),
	],
	interaction_type = TeamworkInteractionType.CreateChat,
)

result = await graph_client.teamwork.determine_if_interaction_is_allowed.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Edm.Boolean",
  "value": true
}
```

### Example 4: Determine if the signed-in user can create a chat with another user using their email

The following example shows a request that determines whether the signed-in user, authenticated via delegated context, can create a chat with another user by specifying the other user's email.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/beta/teamwork/determineIfInteractionIsAllowed

{
  "users":
  [
    {
      "@odata.type": "microsoft.graph.emailIdentity",
      "email": "LauraW@contoso.com"
    }
  ],
  "interactionType": "createChat"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Teamwork.DetermineIfInteractionIsAllowed;
using Microsoft.Graph.Beta.Models;

var requestBody = new DetermineIfInteractionIsAllowedPostRequestBody
{
	Users = new List<Identity>
	{
		new EmailIdentity
		{
			OdataType = "microsoft.graph.emailIdentity",
			Email = "LauraW@contoso.com",
		},
	},
	InteractionType = TeamworkInteractionType.CreateChat,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teamwork.DetermineIfInteractionIsAllowed.PostAsDetermineIfInteractionIsAllowedPostResponseAsync(requestBody);
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
	  graphteamwork "github.com/microsoftgraph/msgraph-beta-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewDetermineIfInteractionIsAllowedPostRequestBody()


identity := graphmodels.NewEmailIdentity()
email := "LauraW@contoso.com"
identity.SetEmail(&email) 

users := []graphmodels.Identityable {
	identity,
}
requestBody.SetUsers(users)
interactionType := graphmodels.CREATECHAT_TEAMWORKINTERACTIONTYPE 
requestBody.SetInteractionType(&interactionType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
determineIfInteractionIsAllowed, err := graphClient.Teamwork().DetermineIfInteractionIsAllowed().PostAsDetermineIfInteractionIsAllowedPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody determineIfInteractionIsAllowedPostRequestBody = new com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody();
LinkedList<Identity> users = new LinkedList<Identity>();
EmailIdentity identity = new EmailIdentity();
identity.setOdataType("microsoft.graph.emailIdentity");
identity.setEmail("LauraW@contoso.com");
users.add(identity);
determineIfInteractionIsAllowedPostRequestBody.setUsers(users);
determineIfInteractionIsAllowedPostRequestBody.setInteractionType(TeamworkInteractionType.CreateChat);
var result = graphClient.teamwork().determineIfInteractionIsAllowed().post(determineIfInteractionIsAllowedPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _boolean = {
  users: 
  [
    {
      '@odata.type': 'microsoft.graph.emailIdentity',
      email: 'LauraW@contoso.com'
    }
  ],
  interactionType: 'createChat'
};

await client.api('/teamwork/determineIfInteractionIsAllowed')
	.version('beta')
	.post(_boolean);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teamwork\DetermineIfInteractionIsAllowed\DetermineIfInteractionIsAllowedPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\EmailIdentity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkInteractionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DetermineIfInteractionIsAllowedPostRequestBody();
$usersIdentity1 = new EmailIdentity();
$usersIdentity1->setOdataType('microsoft.graph.emailIdentity');
$usersIdentity1->setEmail('LauraW@contoso.com');
$usersArray []= $usersIdentity1;
$requestBody->setUsers($usersArray);

$requestBody->setInteractionType(new TeamworkInteractionType('createChat'));

$result = $graphServiceClient->teamwork()->determineIfInteractionIsAllowed()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	users = @(
		@{
			"@odata.type" = "microsoft.graph.emailIdentity"
			email = "LauraW@contoso.com"
		}
	)
	interactionType = "createChat"
}

Invoke-MgBetaDetermineTeamworkIfInteractionIsAllowed -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.teamwork.determine_if_interaction_is_allowed.determine_if_interaction_is_allowed_post_request_body import DetermineIfInteractionIsAllowedPostRequestBody
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.email_identity import EmailIdentity
from msgraph_beta.generated.models.teamwork_interaction_type import TeamworkInteractionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DetermineIfInteractionIsAllowedPostRequestBody(
	users = [
		EmailIdentity(
			odata_type = "microsoft.graph.emailIdentity",
			email = "LauraW@contoso.com",
		),
	],
	interaction_type = TeamworkInteractionType.CreateChat,
)

result = await graph_client.teamwork.determine_if_interaction_is_allowed.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Edm.Boolean",
  "value": true
}
```

### Example 5: Determine if the signed-in user can create a chat with three other users

The following example shows a request that determines whether the signed-in user, authenticated via delegated context, can create a chat with three other users. It uses a mix of the supported [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) types. In this example, the interaction isn't allowed.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/beta/teamwork/determineIfInteractionIsAllowed

{
  "users":
  [
    {
      "@odata.type": "microsoft.graph.emailIdentity",
      "email": "LauraW@foo.com"
    },
    {
      "@odata.type": "microsoft.graph.teamworkUserIdentity",
      "userPrincipalName": "MaiaR@foobar.com"
    },
    {
      "@odata.type": "microsoft.graph.teamworkUserIdentity",
      "id": "bd6a223f-59b5-46dd-90bc-0ddebaf3da5a"
    }
  ],
  "interactionType": "createChat"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Teamwork.DetermineIfInteractionIsAllowed;
using Microsoft.Graph.Beta.Models;

var requestBody = new DetermineIfInteractionIsAllowedPostRequestBody
{
	Users = new List<Identity>
	{
		new EmailIdentity
		{
			OdataType = "microsoft.graph.emailIdentity",
			Email = "LauraW@foo.com",
		},
		new TeamworkUserIdentity
		{
			OdataType = "microsoft.graph.teamworkUserIdentity",
			UserPrincipalName = "MaiaR@foobar.com",
		},
		new TeamworkUserIdentity
		{
			OdataType = "microsoft.graph.teamworkUserIdentity",
			Id = "bd6a223f-59b5-46dd-90bc-0ddebaf3da5a",
		},
	},
	InteractionType = TeamworkInteractionType.CreateChat,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teamwork.DetermineIfInteractionIsAllowed.PostAsDetermineIfInteractionIsAllowedPostResponseAsync(requestBody);
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
	  graphteamwork "github.com/microsoftgraph/msgraph-beta-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewDetermineIfInteractionIsAllowedPostRequestBody()


identity := graphmodels.NewEmailIdentity()
email := "LauraW@foo.com"
identity.SetEmail(&email) 
identity1 := graphmodels.NewTeamworkUserIdentity()
userPrincipalName := "MaiaR@foobar.com"
identity1.SetUserPrincipalName(&userPrincipalName) 
identity2 := graphmodels.NewTeamworkUserIdentity()
id := "bd6a223f-59b5-46dd-90bc-0ddebaf3da5a"
identity2.SetId(&id) 

users := []graphmodels.Identityable {
	identity,
	identity1,
	identity2,
}
requestBody.SetUsers(users)
interactionType := graphmodels.CREATECHAT_TEAMWORKINTERACTIONTYPE 
requestBody.SetInteractionType(&interactionType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
determineIfInteractionIsAllowed, err := graphClient.Teamwork().DetermineIfInteractionIsAllowed().PostAsDetermineIfInteractionIsAllowedPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody determineIfInteractionIsAllowedPostRequestBody = new com.microsoft.graph.beta.teamwork.determineifinteractionisallowed.DetermineIfInteractionIsAllowedPostRequestBody();
LinkedList<Identity> users = new LinkedList<Identity>();
EmailIdentity identity = new EmailIdentity();
identity.setOdataType("microsoft.graph.emailIdentity");
identity.setEmail("LauraW@foo.com");
users.add(identity);
TeamworkUserIdentity identity1 = new TeamworkUserIdentity();
identity1.setOdataType("microsoft.graph.teamworkUserIdentity");
identity1.setUserPrincipalName("MaiaR@foobar.com");
users.add(identity1);
TeamworkUserIdentity identity2 = new TeamworkUserIdentity();
identity2.setOdataType("microsoft.graph.teamworkUserIdentity");
identity2.setId("bd6a223f-59b5-46dd-90bc-0ddebaf3da5a");
users.add(identity2);
determineIfInteractionIsAllowedPostRequestBody.setUsers(users);
determineIfInteractionIsAllowedPostRequestBody.setInteractionType(TeamworkInteractionType.CreateChat);
var result = graphClient.teamwork().determineIfInteractionIsAllowed().post(determineIfInteractionIsAllowedPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const _boolean = {
  users: 
  [
    {
      '@odata.type': 'microsoft.graph.emailIdentity',
      email: 'LauraW@foo.com'
    },
    {
      '@odata.type': 'microsoft.graph.teamworkUserIdentity',
      userPrincipalName: 'MaiaR@foobar.com'
    },
    {
      '@odata.type': 'microsoft.graph.teamworkUserIdentity',
      id: 'bd6a223f-59b5-46dd-90bc-0ddebaf3da5a'
    }
  ],
  interactionType: 'createChat'
};

await client.api('/teamwork/determineIfInteractionIsAllowed')
	.version('beta')
	.post(_boolean);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teamwork\DetermineIfInteractionIsAllowed\DetermineIfInteractionIsAllowedPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\Identity;
use Microsoft\Graph\Beta\Generated\Models\EmailIdentity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkUserIdentity;
use Microsoft\Graph\Beta\Generated\Models\TeamworkInteractionType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DetermineIfInteractionIsAllowedPostRequestBody();
$usersIdentity1 = new EmailIdentity();
$usersIdentity1->setOdataType('microsoft.graph.emailIdentity');
$usersIdentity1->setEmail('LauraW@foo.com');
$usersArray []= $usersIdentity1;
$usersIdentity2 = new TeamworkUserIdentity();
$usersIdentity2->setOdataType('microsoft.graph.teamworkUserIdentity');
$usersIdentity2->setUserPrincipalName('MaiaR@foobar.com');
$usersArray []= $usersIdentity2;
$usersIdentity3 = new TeamworkUserIdentity();
$usersIdentity3->setOdataType('microsoft.graph.teamworkUserIdentity');
$usersIdentity3->setId('bd6a223f-59b5-46dd-90bc-0ddebaf3da5a');
$usersArray []= $usersIdentity3;
$requestBody->setUsers($usersArray);

$requestBody->setInteractionType(new TeamworkInteractionType('createChat'));

$result = $graphServiceClient->teamwork()->determineIfInteractionIsAllowed()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	users = @(
		@{
			"@odata.type" = "microsoft.graph.emailIdentity"
			email = "LauraW@foo.com"
		}
		@{
			"@odata.type" = "microsoft.graph.teamworkUserIdentity"
			userPrincipalName = "MaiaR@foobar.com"
		}
		@{
			"@odata.type" = "microsoft.graph.teamworkUserIdentity"
			id = "bd6a223f-59b5-46dd-90bc-0ddebaf3da5a"
		}
	)
	interactionType = "createChat"
}

Invoke-MgBetaDetermineTeamworkIfInteractionIsAllowed -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.teamwork.determine_if_interaction_is_allowed.determine_if_interaction_is_allowed_post_request_body import DetermineIfInteractionIsAllowedPostRequestBody
from msgraph_beta.generated.models.identity import Identity
from msgraph_beta.generated.models.email_identity import EmailIdentity
from msgraph_beta.generated.models.teamwork_user_identity import TeamworkUserIdentity
from msgraph_beta.generated.models.teamwork_interaction_type import TeamworkInteractionType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DetermineIfInteractionIsAllowedPostRequestBody(
	users = [
		EmailIdentity(
			odata_type = "microsoft.graph.emailIdentity",
			email = "LauraW@foo.com",
		),
		TeamworkUserIdentity(
			odata_type = "microsoft.graph.teamworkUserIdentity",
			user_principal_name = "MaiaR@foobar.com",
		),
		TeamworkUserIdentity(
			odata_type = "microsoft.graph.teamworkUserIdentity",
			id = "bd6a223f-59b5-46dd-90bc-0ddebaf3da5a",
		),
	],
	interaction_type = TeamworkInteractionType.CreateChat,
)

result = await graph_client.teamwork.determine_if_interaction_is_allowed.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Edm.Boolean",
  "value": false
}
```
