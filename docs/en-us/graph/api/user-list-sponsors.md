<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-list-sponsors?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-03 -->

# List sponsors

Namespace: microsoft.graph

Get a user's sponsors. Sponsors are users and groups that are responsible for this guest's privileges in the tenant and for keeping the guest's information and access up to date.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.Read | User.ReadWrite.All, AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy, User.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User.Read.All | User.ReadWrite.All, AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy |

Important

When an application queries a relationship that returns a **directoryObject** type collection, if it doesn't have permission to read a certain resource type, members of that type are returned but with limited information. For example, only the **@odata.type** property for the object type and the **id** is returned, while other properties are indicated as `null`. With this behavior, applications can request the least privileged permissions they need, rather than rely on the set of *Directory.*\* permissions. For details, see [Limited information returned for inaccessible member objects](https://learn.microsoft.com/en-us/graph/permissions-overview#limited-information-returned-for-inaccessible-member-objects).

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with the `microsoft.directory/users/sponsors/read` role permission. The following least privileged roles are supported for this operation:

- Guest Inviter
- Directory Readers
- Directory Writers
- User Administrator
- Agent ID Administrator - For agent users

## HTTP request

Get sponsors.

```http
GET /users/{id | userPrincipalName}/sponsors
```

## Optional query parameters

This method supports the `$select` and `$expand` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. You can specify `$select` inside `$expand` to select the individual sponsor's properties: `$expand=sponsors($select=id,displayName)`.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) and [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/users/025e5e3e-e5b7-4eb4-ba1f-4e5b0579f1a2/sponsors
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Sponsors.GetAsync();
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
sponsors, err := graphClient.Users().ByUserId("user-id").Sponsors().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DirectoryObjectCollectionResponse result = graphClient.users().byUserId("{user-id}").sponsors().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sponsors = await client.api('/users/025e5e3e-e5b7-4eb4-ba1f-4e5b0579f1a2/sponsors')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->sponsors()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

Get-MgUserSponsor -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').sponsors.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note**: The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
"@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryObjects",
    "value": [
        {
            "@odata.type": "#microsoft.graph.user",
            "id": "263a1289-8282-4bf7-91f7-550d9bba8c02",
            "displayName": "Sara Davis",
            "jobTitle": "Finance VP",
            "mail": "SaraD@contoso.com",
            "userPrincipalName": "SaraD@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.group",
            "id": "08143e93-989e-4771-ac78-803bcdac52d2",
            "mail": "groupforsponsors@contoso.com",
            "mailEnabled": true,
            "mailNickname": "groupforsponsors",
            "securityEnabled": true
        }
    ]
}
```
