<!-- Source: https://learn.microsoft.com/en-us/graph/api/group-list-owners?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-21 -->

# List group owners

Namespace: microsoft.graph

Retrieve a list of the group's owners. The owners are a set of users or service principals who are allowed to modify the group object. Owners are currently not available in Microsoft Graph for groups that were created in Exchange, distribution groups, or groups that are synchronized from an on-premises environment.

> **Note:** Currently, service principals are not listed as group owners due to the staged rollout of service principals to the Microsoft Graph v1.0 endpoint.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | GroupMember.Read.All | Group.ReadWrite.All, Directory.Read.All, Group.Read.All, GroupMember.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | GroupMember.Read.All | Group.ReadWrite.All, Directory.Read.All, Group.Read.All, GroupMember.ReadWrite.All |

Important

When an application queries a relationship that returns a **directoryObject** type collection, if it doesn't have permission to read a certain resource type, members of that type are returned but with limited information. For example, only the **@odata.type** property for the object type and the **id** is returned, while other properties are indicated as `null`. With this behavior, applications can request the least privileged permissions they need, rather than rely on the set of *Directory.*\* permissions. For details, see [Limited information returned for inaccessible member objects](https://learn.microsoft.com/en-us/graph/permissions-overview#limited-information-returned-for-inaccessible-member-objects).

In delegated scenarios, the signed-in user must also be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with the `microsoft.directory/groups/owners/read` role permission. The following least privileged roles are supported for this operation:

- Group owners
- "Member" users
- "Guest" users - have [limited read permissions](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions?context=graph/context#compare-member-and-guest-default-permissions)
- Directory Readers
- Directory Writers
- Groups Administrator
- User Administrator
- Exchange Administrator - for Microsoft 365 groups only
- SharePoint Administrator - for Microsoft 365 groups only
- Teams Administrator - for Microsoft 365 groups only
- Yammer Administrator - for Microsoft 365 groups only
- Intune Administrator - for security groups only

## HTTP request

```http
GET /groups/{id}/owners
```

## Optional query parameters

This method supports the `$filter`, `$count`, `$select`, `$search`, `$top`, and `$expand` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

- OData cast is enabled. For example, `/groups/{id}/members/microsoft.graph.user` retrieves group owners that are users.
- `$search` is supported on the **displayName** and **description** properties only.
- The use of query parameters with this API, except for `$expand`, is supported only with advanced query parameters. `$expand` isn't supported with advanced query parameters. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and collection of [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) objects in the response body.

## Example

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

```msgraph
GET https://graph.microsoft.com/v1.0/groups/02bd9fd6-8f93-4758-87c3-1fb73740a315/owners
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Owners.GetAsync();
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
owners, err := graphClient.Groups().ByGroupId("group-id").Owners().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

DirectoryObjectCollectionResponse result = graphClient.groups().byGroupId("{group-id}").owners().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let owners = await client.api('/groups/02bd9fd6-8f93-4758-87c3-1fb73740a315/owners')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->groups()->byGroupId('group-id')->owners()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Groups

Get-MgGroupOwner -GroupId $groupId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.groups.by_group_id('group-id').owners.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#directoryObjects",
    "value": [
        {
            "@odata.type": "#microsoft.graph.user",
            "id": "4562bcc8-c436-4f95-b7c0-4f8ce89dca5e",
            "accountEnabled": true,
            "displayName": "MOD Administrator",
            "userPrincipalName": "admin@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.user",
            "id": "f0206b06-7c5d-461c-ae24-08f68b7ef463",
            "accountEnabled": true,
            "displayName": "Megan Bowen",
            "userPrincipalName": "MeganB@contoso.com"
        },
        {
            "@odata.type": "#microsoft.graph.user",
            "id": "5c70937c-d9ea-4a47-8852-ab77630f803d",
            "accountEnabled": true,
            "displayName": "Diego Siciliani",
            "userPrincipalName": "DiegoS@contoso.com"
        }
    ]
}
```
