<!-- Source: https://learn.microsoft.com/en-us/graph/api/sharepointgroup-delete-members?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Delete sharePointGroupMember

Namespace: microsoft.graph

Delete a [sharePointGroupMember](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmember?view=graph-rest-1.0) object from a [sharePointGroup](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroup?view=graph-rest-1.0). The deleted member immediately loses the permissions they inherit from the **sharePointGroup**. It may take several minutes for substrate-related functionality, such as search and Copilot, to reflect the deletion of the **sharePointGroupMember**.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainer.Selected | Not available. |

Note

In addition to Microsoft Graph permissions, applications calling this API must at least have the `AddPermissions` container type-level permission on the container type of the corresponding containers. For more information, see [container types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container type-level permissions, see [SharePoint Embedded authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#authorization).

## HTTP request

```http
DELETE /storage/fileStorage/containers/{fileStorageContainerId}/sharePointGroups/{sharePointGroupId}/members/{sharePointGroupMemberId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

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
DELETE https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/sharePointGroups/ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0/members/aTowIy5mfG1lbWJlcnNoaXB8YWRtaW5AYTgzMGVkYWQ5MDUwODQ5c3Bncm91cHRlc3QyLm9ubWljcm9zb2Z0LmNvbQ
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Storage.FileStorage.Containers["{fileStorageContainer-id}"].SharePointGroups["{sharePointGroup-id}"].Members["{sharePointGroupMember-id}"].DeleteAsync();
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
graphClient.Storage().FileStorage().Containers().ByFileStorageContainerId("fileStorageContainer-id").SharePointGroups().BySharePointGroupId("sharePointGroup-id").Members().BySharePointGroupMemberId("sharePointGroupMember-id").Delete(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.storage().fileStorage().containers().byFileStorageContainerId("{fileStorageContainer-id}").sharePointGroups().bySharePointGroupId("{sharePointGroup-id}").members().bySharePointGroupMemberId("{sharePointGroupMember-id}").delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/sharePointGroups/ZGYwZTEzYTgtOTExOS00MjdmLWEzNjktOTdjOWM3YjNlYjcyXzE0/members/aTowIy5mfG1lbWJlcnNoaXB8YWRtaW5AYTgzMGVkYWQ5MDUwODQ5c3Bncm91cHRlc3QyLm9ubWljcm9zb2Z0LmNvbQ')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->storage()->fileStorage()->containers()->byFileStorageContainerId('fileStorageContainer-id')->sharePointGroups()->bySharePointGroupId('sharePointGroup-id')->members()->bySharePointGroupMemberId('sharePointGroupMember-id')->delete()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.storage.file_storage.containers.by_file_storage_container_id('fileStorageContainer-id').share_point_groups.by_share_point_group_id('sharePointGroup-id').members.by_share_point_group_member_id('sharePointGroupMember-id').delete()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
