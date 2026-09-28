<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestorage-list-containertyperegistrations?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List containerTypeRegistrations

Namespace: microsoft.graph

Get a list of the [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) objects and their properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainerTypeReg.Selected | FileStorageContainerTypeReg.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | FileStorageContainerTypeReg.Selected | Not available. |

> **Note:**
> 
> - When delegated tokens are used, either the SharePoint Embedded admin role or the Global admin role is required.
> - If the `FileStorageContainerTypeReg.Selected` permission is used, results are limited to [registrations](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) owned by the application that makes the call.

## HTTP request

```http
GET /storage/fileStorage/containerTypeRegistrations
```

## Optional query parameters

This method supports the `$filter`, `$select`, `$orderby`, `$count`, `$top`, and `$skip` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [fileStorageContainerTypeRegistration](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainertyperegistration?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows how to list **fileStorageContainerTypeRegistration** objects using delegated tokens with SharePoint Embedded admin permissions.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/storage/fileStorage/containerTypeRegistrations
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.ContainerTypeRegistrations.GetAsync();
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
containerTypeRegistrations, err := graphClient.Storage().FileStorage().ContainerTypeRegistrations().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

FileStorageContainerTypeRegistrationCollectionResponse result = graphClient.storage().fileStorage().containerTypeRegistrations().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let containerTypeRegistrations = await client.api('/storage/fileStorage/containerTypeRegistrations')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->storage()->fileStorage()->containerTypeRegistrations()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.storage.file_storage.container_type_registrations.get()
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
      "@odata.type": "#microsoft.graph.fileStorageContainerTypeRegistration",
      "id": "de988700-d700-020e-0a00-0831f3042f00",
      "name": "Container Type 1",
      "owningAppId": "11335700-9a00-4c00-84dd-0c210f203f00",
      "billingClassification": "trial",
      "billingStatus": "valid",
      "registeredDateTime": "01/20/2025",
      "expirationDateTime": "02/20/2025",
      "etag": "RVRhZw==",
      "settings": {
        "sharingCapability": "disabled",
        "urlTemplate": "https://app.contoso.com/redirect?tenant={tenant-id}&drive={drive-id}&folder={folder-id}&item={item-id}",
        "isDiscoverabilityEnabled": true,
        "isSearchEnabled": true,
        "isItemVersioningEnabled": true,
        "itemMajorVersionLimit": 50,
        "maxStoragePerContainerInBytes": 104857600,
        "isSharingRestricted": false
      },
      "applicationPermissionGrants": [
        {
          "appId": "11335700-9a00-4c00-84dd-0c210f203f00",
          "delegatedPermissions": [
            "none"
          ],
          "applicationPermissions": [
            "full"
          ]
        },
        {
          "appId": "d893fd02-3578-4c7f-bd85-12fc3358af48",
          "delegatedPermissions": [
            "full"
          ],
          "applicationPermissions": [
            "none"
          ]
        }
      ]
    },
    {
      "@odata.type": "#microsoft.graph.fileStorageContainerTypeRegistration",
      "id": "88aeae-d700-020e-0a00-0831f3042f01",
      "name": "Container Type 2",
      "owningAppId": "33225700-9a00-4c00-84dd-0c210f203f01",
      "billingClassification": "Standard",
      "billingStatus": "valid",
      "registeredDateTime": "01/20/2025",
      "expirationDateTime": null,
      "etag": "RVRhZw==",
      "settings": {
        "sharingCapability": "externalUserSharingOnly",
        "urlTemplate": "",
        "isDiscoverabilityEnabled": true,
        "isSearchEnabled": true,
        "isItemVersioningEnabled": true,
        "itemMajorVersionLimit": 50,
        "maxStoragePerContainerInBytes": 104857600,
        "isSharingRestricted": false
      },
      "applicationPermissionGrants": [
        {
          "appId": "33225700-9a00-4c00-84dd-0c210f203f01",
          "delegatedPermissions": [
            "full"
          ],
          "applicationPermissions": [
            "full"
          ]
        },
        {
          "appId": "cf9d52b8-1e33-4a35-a724-c3ae3c937892",
          "delegatedPermissions": [
            "full"
          ],
          "applicationPermissions": [
            "none"
          ]
        }
      ]
    }
  ]
}
```
