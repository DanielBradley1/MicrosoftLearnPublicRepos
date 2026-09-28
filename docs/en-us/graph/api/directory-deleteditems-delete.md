<!-- Source: https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# Permanently delete item \(directory object\)

Namespace: microsoft.graph

Permanently delete a recently deleted directory object from [deleted items](https://learn.microsoft.com/en-us/graph/api/resources/directory?view=graph-rest-1.0). The following types are supported:

- [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0)
- [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0)
- [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0)
- [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0)
- [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0)
- [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0)
- [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0)
- [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0)
- [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0)
- [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)

After an item is permanently deleted, it **cannot** be restored.

Administrative units **cannot** be permanently deleted by using the **deletedItems** API. Soft-deleted administrative units will be permanently deleted 30 days after initial deletion unless they are restored.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following table shows the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) | Application.ReadWrite.All | Not supported. | Application.ReadWrite.OwnedBy |
| [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-1.0) | AgentIdentity.ReadWrite.All | Not supported. | AgentIdentity.ReadWrite.All |
| [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) | AgentIdentityBlueprint.ReadWrite.All | Not supported. | AgentIdentityBlueprint.ReadWrite.All |
| [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) | AgentIdentityBlueprintPrincipal.ReadWrite.All | Not supported. | AgentIdentityBlueprintPrincipal.ReadWrite.All |
| [agentUser](https://learn.microsoft.com/en-us/graph/api/resources/agentuser?view=graph-rest-1.0) | AgentIdUser.ReadWrite.IdentityParentedBy | Not supported. | AgentIdUser.ReadWrite.IdentityParentedBy |
| [certificateBasedAuthPki](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthpki?view=graph-rest-1.0) | PublicKeyInfrastructure.Read.All | Not supported. | PublicKeyInfrastructure.Read.All |
| [certificateAuthorityDetail](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthoritydetail?view=graph-rest-1.0) | PublicKeyInfrastructure.Read.All | Not supported. | PublicKeyInfrastructure.Read.All |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported. | Not supported. |
| [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Application.ReadWrite.All | Not supported. | Application.ReadWrite.OwnedBy |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.DeleteRestore.All | Not supported. | User.DeleteRestore.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Agent identities, agent identity blueprints, and agent identity blueprint principals: Agent ID Administrator
- Administrative units: Directory Readers \(read-only\), Global Readers \(read-only\), Privileged Role Administrator
- Applications: Hybrid Identity Administrator, Cloud Application Administrator, Application Administrator
- External user profiles: Global Reader \(read-only\), Skype for Business Administrator, Teams Administrator
- Groups: Groups Administrator \(except for role-assignable groups\), User Administrator \(except for role-assignable groups\), Privileged Role Administrator \(least privileged role for role-assignable groups\)
- Pending external user profiles: Global Reader \(read-only\), Skype for Business Administrator, Teams Administrator
- Service principals: Hybrid Identity Administrator, Cloud Application Administrator, Application Administrator
- Users: Authentication Administrator, Privileged Authentication Administrator, User Administrator. However, to restore users with privileged administrator roles:

  - In delegated scenarios, the app must be assigned the *Directory.AccessAsUser.All* delegated permission, and the calling user must also be assigned a higher privileged administrator role as indicated in [Who can perform sensitive actions?](https://learn.microsoft.com/en-us/graph/api/resources/users#who-can-perform-sensitive-actions).
  - In app-only scenarios and in addition to being granted the *User.ReadWrite.All* application permission, the app must be assigned a higher privileged administrator role as indicated in [Who can perform sensitive actions?](https://learn.microsoft.com/en-us/graph/api/resources/users#who-can-perform-sensitive-actions).

## HTTP request

```http
DELETE /directory/deletedItems/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
DELETE https://graph.microsoft.com/v1.0/directory/deletedItems/{object-id}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Directory.DeletedItems["{directoryObject-id}"].DeleteAsync();
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
graphClient.Directory().DeletedItems().ByDirectoryObjectId("directoryObject-id").Delete(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.directory().deletedItems().byDirectoryObjectId("{directoryObject-id}").delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/directory/deletedItems/{object-id}')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->directory()->deletedItems()->byDirectoryObjectId('directoryObject-id')->delete()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Identity.DirectoryManagement

Remove-MgDirectoryDeletedItem -DirectoryObjectId $directoryObjectId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.directory.deleted_items.by_directory_object_id('directoryObject-id').delete()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

Note: The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
