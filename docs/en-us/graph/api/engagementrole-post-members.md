<!-- Source: https://learn.microsoft.com/en-us/graph/api/engagementrole-post-members?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# Create engagementRoleMember

Namespace: microsoft.graph

Create a new [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) object that assigns a Viva Engage role to a user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EngagementRole.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EngagementRole.ReadWrite.All | Not available. |

## HTTP request

```http
POST /employeeExperience/roles/{engagementRoleId}/members
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) object.

You can specify the following properties when you create an **engagementRoleMember**.

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the role was assigned to the user. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| userId | String | The Microsoft Entra ID of the user who has the role assigned. |

## Response

If successful, this method returns a `201 Created` response code and an [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) object in the response body.

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

```http
POST https://graph.microsoft.com/v1.0/employeeExperience/roles/a40473a5-0fb4-a250-e029-f6fe33d07733/members
Content-Type: application/json

{
  "user@odata.bind": "https://graph.microsoft.com/v1.0/users('e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01')"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EngagementRoleMember
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Roles["{engagementRole-id}"].Members.PostAsync(requestBody);
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

requestBody := graphmodels.NewEngagementRoleMember()
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
members, err := graphClient.EmployeeExperience().Roles().ByEngagementRoleId("engagementRole-id").Members().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EngagementRoleMember engagementRoleMember = new EngagementRoleMember();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01')");
engagementRoleMember.setAdditionalData(additionalData);
EngagementRoleMember result = graphClient.employeeExperience().roles().byEngagementRoleId("{engagementRole-id}").members().post(engagementRoleMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const engagementRoleMember = {
  'user@odata.bind': 'https://graph.microsoft.com/v1.0/users(\'e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01\')'
};

await client.api('/employeeExperience/roles/a40473a5-0fb4-a250-e029-f6fe33d07733/members')
	.post(engagementRoleMember);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EngagementRoleMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EngagementRoleMember();
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->employeeExperience()->roles()->byEngagementRoleId('engagementRole-id')->members()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.engagement_role_member import EngagementRoleMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EngagementRoleMember(
	additional_data = {
			"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01')",
	}
)

result = await graph_client.employee_experience.roles.by_engagement_role_id('engagementRole-id').members.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.engagementRoleMember",
  "id": "a40473a5-0fb4-a250-e029-f6fe33d07733",
  "userId": "e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01",
  "createdDateTime": "2025-09-22T14:03:00Z"
}
```
