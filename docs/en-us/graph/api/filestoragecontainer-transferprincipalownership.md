<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-transferprincipalownership?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# fileStorageContainer: transferPrincipalOwnership

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Transfer the principal ownership of a user-owned [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-beta) from one user to another. The principal owner is a special role whose lifecycle is tied to the container; when the principal owner is deleted from the tenant, the container is automatically deleted.

This action is restricted to enterprise \(non-MSA\) tenants and user-owned containers only. The caller must be a tenant administrator with either the Global Administrator or SharePoint Embedded Administrator role.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Note

In addition to Microsoft Graph permissions, your app must have the necessary container type-level permission or permissions to call this API. For more information, see [container types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container type-level permissions, see [SharePoint Embedded authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

Note

When delegated permissions are used, the caller must be a tenant administrator with either the Global Administrator or SharePoint Embedded Administrator role.

## HTTP request

```http
POST /storage/fileStorage/containers/{fileStorageContainerId}/transferPrincipalOwnership
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| transferTo | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the new principal owner. You can specify the user by either `user.id` or `user.userPrincipalName`. Required. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/beta/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/transferPrincipalOwnership
Content-Type: application/json

{
  "transferTo": {
    "user": {
      "userPrincipalName": "newowner@contoso.com"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Storage.FileStorage.Containers.Item.TransferPrincipalOwnership;
using Microsoft.Graph.Beta.Models;

var requestBody = new TransferPrincipalOwnershipPostRequestBody
{
	TransferTo = new IdentitySet
	{
		User = new Identity
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userPrincipalName" , "newowner@contoso.com"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Storage.FileStorage.Containers["{fileStorageContainer-id}"].TransferPrincipalOwnership.PostAsync(requestBody);
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
	  graphstorage "github.com/microsoftgraph/msgraph-beta-sdk-go/storage"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphstorage.NewTransferPrincipalOwnershipPostRequestBody()
transferTo := graphmodels.NewIdentitySet()
user := graphmodels.NewIdentity()
additionalData := map[string]interface{}{
	"userPrincipalName" : "newowner@contoso.com", 
}
user.SetAdditionalData(additionalData)
transferTo.SetUser(user)
requestBody.SetTransferTo(transferTo)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Storage().FileStorage().Containers().ByFileStorageContainerId("fileStorageContainer-id").TransferPrincipalOwnership().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.storage.filestorage.containers.item.transferprincipalownership.TransferPrincipalOwnershipPostRequestBody transferPrincipalOwnershipPostRequestBody = new com.microsoft.graph.beta.storage.filestorage.containers.item.transferprincipalownership.TransferPrincipalOwnershipPostRequestBody();
IdentitySet transferTo = new IdentitySet();
Identity user = new Identity();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userPrincipalName", "newowner@contoso.com");
user.setAdditionalData(additionalData);
transferTo.setUser(user);
transferPrincipalOwnershipPostRequestBody.setTransferTo(transferTo);
graphClient.storage().fileStorage().containers().byFileStorageContainerId("{fileStorageContainer-id}").transferPrincipalOwnership().post(transferPrincipalOwnershipPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const transferPrincipalOwnership = {
  transferTo: {
    user: {
      userPrincipalName: 'newowner@contoso.com'
    }
  }
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/transferPrincipalOwnership')
	.version('beta')
	.post(transferPrincipalOwnership);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Storage\FileStorage\Containers\Item\TransferPrincipalOwnership\TransferPrincipalOwnershipPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\IdentitySet;
use Microsoft\Graph\Beta\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TransferPrincipalOwnershipPostRequestBody();
$transferTo = new IdentitySet();
$transferToUser = new Identity();
$additionalData = [
	'userPrincipalName' => 'newowner@contoso.com',
];
$transferToUser->setAdditionalData($additionalData);
$transferTo->setUser($transferToUser);
$requestBody->setTransferTo($transferTo);

$graphServiceClient->storage()->fileStorage()->containers()->byFileStorageContainerId('fileStorageContainer-id')->transferPrincipalOwnership()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.storage.filestorage.containers.item.transfer_principal_ownership.transfer_principal_ownership_post_request_body import TransferPrincipalOwnershipPostRequestBody
from msgraph_beta.generated.models.identity_set import IdentitySet
from msgraph_beta.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TransferPrincipalOwnershipPostRequestBody(
	transfer_to = IdentitySet(
		user = Identity(
			additional_data = {
					"user_principal_name" : "newowner@contoso.com",
			}
		),
	),
)

await graph_client.storage.file_storage.containers.by_file_storage_container_id('fileStorageContainer-id').transfer_principal_ownership.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
