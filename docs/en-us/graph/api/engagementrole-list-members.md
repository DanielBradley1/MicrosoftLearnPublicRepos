<!-- Source: https://learn.microsoft.com/en-us/graph/api/engagementrole-list-members?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-13 -->

# List members

Namespace: microsoft.graph

Get a list of users with assigned [roles](https://learn.microsoft.com/en-us/graph/api/resources/engagementrole?view=graph-rest-1.0) in Viva Engage.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EngagementRole.Read.All | EngagementRole.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EngagementRole.Read.All | EngagementRole.ReadWrite.All |

## HTTP request

```http
GET /employeeExperience/roles/{engagementRoleId}/members
```

## Optional query parameters

This method supports the `$filter` \(`eq`\), `$select`, and `$count` OData query parameters. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters). Only the **userId** and **id** properties support the `$filter` parameter.

The following table shows how you can use OData query parameters with this API.

| Description | HTTP request |
| :--- | :--- |
| Filter role members by user ID | `GET /employeeExperience/roles/{engagementRoleId}/members?$filter=userId eq 'e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01'` |
| Include the total count of role members | `GET /employeeExperience/roles/{engagementRoleId}/members?$count=true` |
| Get only the **id** and **createdDateTime** properties for a list of role members | `GET /employeeExperience/roles/{engagementRoleId}/members?$select=id,createdDateTime` |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [engagementRoleMember](https://learn.microsoft.com/en-us/graph/api/resources/engagementrolemember?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/employeeExperience/roles/a40473a5-0fb4-a250-e029-f6fe33d07733/members
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.Roles["{engagementRole-id}"].Members.GetAsync();
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
members, err := graphClient.EmployeeExperience().Roles().ByEngagementRoleId("engagementRole-id").Members().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EngagementRoleMemberCollectionResponse result = graphClient.employeeExperience().roles().byEngagementRoleId("{engagementRole-id}").members().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let members = await client.api('/employeeExperience/roles/a40473a5-0fb4-a250-e029-f6fe33d07733/members')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->employeeExperience()->roles()->byEngagementRoleId('engagementRole-id')->members()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.employee_experience.roles.by_engagement_role_id('engagementRole-id').members.get()
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
      "@odata.type": "#microsoft.graph.engagementRoleMember",
      "id": "a40473a5-0fb4-a250-e029-f6fe33d07733",
      "userId": "e8d9f6a2-1c34-4b7a-9f11-2a4d8b7c9e01",
      "createdDateTime": "2025-09-22T14:03:00Z"
    }
  ]
}
```
