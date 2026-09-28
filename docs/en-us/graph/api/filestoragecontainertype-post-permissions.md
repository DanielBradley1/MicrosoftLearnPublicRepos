<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainertype-post-permissions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Create permission for a fileStorageContainerType

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a user [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-beta) object, which adds this permission to a [fileStorageContainerType](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertype?view=graph-rest-beta). Only existing owners \(users with the `owner` role in the **permissions** collection of the container type\), SharePoint Embedded Administrators, or Global Administrators can add permissions.

The following constraints apply:

- A maximum of **3** permissions per container type is allowed. Adding a fourth permission returns a `400 Bad Request` error.
- Duplicate permissions are treated as idempotent. If the specified user already has a permission on the container type, the service makes no changes and returns the existing permission resource in the response body with a `201 Created` status, even though no new permission is created.
- Currently only the `owner` role is supported.

Note

- Guest users can't be recipients of container type permissions.
- Guest users can't perform this operation.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainerType.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /storage/fileStorage/containerTypes/{fileStorageContainerTypeId}/permissions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-beta) object.

You can specify the following properties when you create a **permission**.

| Property | Type | Description |
| :--- | :--- | :--- |
| grantedToV2 | [sharePointIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/sharepointidentityset?view=graph-rest-beta) | The identity of the user to grant the permission to. Only the **user** property with the user's **id** is supported; group and application identities aren't supported. Required. |
| roles | String collection | The roles granted to the user. Currently only `owner` is supported. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-beta) object in the response body.

If the request exceeds the limit of three permissions per container type, this method returns a `400 Bad Request` response code.

## Examples

### Request

The following example shows a request to add an owner permission to a container type.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions
Content-Type: application/json

{
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "11111111-1111-1111-1111-111111111111"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new Permission
{
	Roles = new List<string>
	{
		"owner",
	},
	GrantedToV2 = new SharePointIdentitySet
	{
		User = new Identity
		{
			Id = "11111111-1111-1111-1111-111111111111",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypes["{fileStorageContainerType-id}"].Permissions.PostAsync(requestBody);
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewPermission()
roles := []string {
	"owner",
}
requestBody.SetRoles(roles)
grantedToV2 := graphmodels.NewSharePointIdentitySet()
user := graphmodels.NewIdentity()
id := "11111111-1111-1111-1111-111111111111"
user.SetId(&id) 
grantedToV2.SetUser(user)
requestBody.SetGrantedToV2(grantedToV2)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
permissions, err := graphClient.Storage().FileStorage().ContainerTypes().ByFileStorageContainerTypeId("fileStorageContainerType-id").Permissions().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Permission permission = new Permission();
LinkedList<String> roles = new LinkedList<String>();
roles.add("owner");
permission.setRoles(roles);
SharePointIdentitySet grantedToV2 = new SharePointIdentitySet();
Identity user = new Identity();
user.setId("11111111-1111-1111-1111-111111111111");
grantedToV2.setUser(user);
permission.setGrantedToV2(grantedToV2);
Permission result = graphClient.storage().fileStorage().containerTypes().byFileStorageContainerTypeId("{fileStorageContainerType-id}").permissions().post(permission);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const permission = {
  roles: ['owner'],
  grantedToV2: {
    user: {
      id: '11111111-1111-1111-1111-111111111111'
    }
  }
};

await client.api('/storage/fileStorage/containerTypes/de988700-d700-020e-0a00-0831f3042f00/permissions')
	.version('beta')
	.post(permission);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\Permission;
use Microsoft\Graph\Beta\Generated\Models\SharePointIdentitySet;
use Microsoft\Graph\Beta\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Permission();
$requestBody->setRoles(['owner', 	]);
$grantedToV2 = new SharePointIdentitySet();
$grantedToV2User = new Identity();
$grantedToV2User->setId('11111111-1111-1111-1111-111111111111');
$grantedToV2->setUser($grantedToV2User);
$requestBody->setGrantedToV2($grantedToV2);

$result = $graphServiceClient->storage()->fileStorage()->containerTypes()->byFileStorageContainerTypeId('fileStorageContainerType-id')->permissions()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.permission import Permission
from msgraph_beta.generated.models.share_point_identity_set import SharePointIdentitySet
from msgraph_beta.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Permission(
	roles = [
		"owner",
	],
	granted_to_v2 = SharePointIdentitySet(
		user = Identity(
			id = "11111111-1111-1111-1111-111111111111",
		),
	),
)

result = await graph_client.storage.file_storage.container_types.by_file_storage_container_type_id('fileStorageContainerType-id').permissions.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.permission",
  "id": "b3duZXJfMTExMTExMTEtMTExMS0xMTExLTExMTEtMTExMTExMTExMTEx",
  "roles": ["owner"],
  "grantedToV2": {
    "user": {
      "id": "11111111-1111-1111-1111-111111111111"
    }
  }
}
```
