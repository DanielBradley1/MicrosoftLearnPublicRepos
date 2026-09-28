<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-list-permissiongrants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# List permissionGrants of a user

Namespace: microsoft.graph

List all [resource-specific permission grants](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) of a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). This list specifies the Microsoft Entra apps that have access to the **user**, along with the corresponding resource-specific access that each app has.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ResourceSpecificPermissionGrant.ReadForUser | TeamsAppInstallation.ManageSelectedForUser, TeamsAppInstallation.ReadWriteAndConsentForUser, TeamsAppInstallation.ReadWriteAndConsentSelfForUser |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ResourceSpecificPermissionGrant.ReadForUser.All | TeamsAppInstallation.ManageSelectedForUser.All, TeamsAppInstallation.ReadWriteAndConsentForUser.All, TeamsAppInstallation.ReadWriteAndConsentSelfForUser.All |

## HTTP request

```http
GET /users/{user-id}/permissionGrants
```

## Optional query parameters

This operation doesn't support the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/users/2f39ffba-51ca-4d2d-a66f-a020a83ce208/permissionGrants
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].PermissionGrants.GetAsync();
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
permissionGrants, err := graphClient.Users().ByUserId("user-id").PermissionGrants().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ResourceSpecificPermissionGrantCollectionResponse result = graphClient.users().byUserId("{user-id}").permissionGrants().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let permissionGrants = await client.api('/users/2f39ffba-51ca-4d2d-a66f-a020a83ce208/permissionGrants')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->permissionGrants()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').permission_grants.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#permissionGrants",
  "value": [
    {
      "id": "Y2VkZGEyMWUtYTUwZS00ZDI3LWEyZjAtOTk0MTMwMGY3Y2I1IyNDaGF0U2V0dGluZ3MuUmVhZFdyaXRlLkNoYXQjI0FwcGxpY2F0aW9u",
      "clientAppId": "fdebf36e-8b3a-4b00-99fb-2e4d1da706d6",
      "resourceAppId": "00000003-0000-0000-c000-000000000000",
      "clientId": "771b9da9-2260-41eb-a587-4d936e4aa08c",
      "permissionType": "Application",
      "permission": "TeamsActivity.Send.User"
    }
  ]
}
```

## Related content

- [List permission grants of a chat](https://learn.microsoft.com/en-us/graph/api/chat-list-permissiongrants?view=graph-rest-1.0)
- [List permission grants of a group](https://learn.microsoft.com/en-us/graph/api/group-list-permissiongrants?view=graph-rest-1.0)
- [List permission grants of a team](https://learn.microsoft.com/en-us/graph/api/team-list-permissiongrants?view=graph-rest-1.0)
