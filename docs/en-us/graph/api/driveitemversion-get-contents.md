<!-- Source: https://learn.microsoft.com/en-us/graph/api/driveitemversion-get-contents?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-20 -->

# Download contents of a driveItemVersion resource

Namespace: microsoft.graph

Retrieve the contents of a specific [version](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) of a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

> **Note:** Getting the content of the current version is not supported. To do that, use the [Download the contents of a driveItem](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content?view=graph-rest-1.0) method.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.Read | Files.Read.All, Files.ReadWrite, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Files.Read | Files.Read.All, Files.ReadWrite, Files.ReadWrite.All |
| Application | Files.Read.All | Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |

Note

SharePoint Embedded requires the `FileStorageContainer.Selected` permission to access the content of the container. This permission is different from the ones mentioned previously. In addition to Microsoft Graph permissions, your app must have the necessary [container type permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#container-type-application-permissions) to call this API. For more information, see [SharePoint Embedded authentication and authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth).

## HTTP request

```http
GET /drives/{drive-id}/items/{item-id}/versions/{version-id}/content
GET /groups/{group-id}/drive/items/{item-id}/versions/{version-id}/content
GET /me/drive/items/{item-id}/versions/{version-id}/content
GET /sites/{site-id}/drive/items/{item-id}/versions/{version-id}/content
GET /users/{user-id}/drive/items/{item-id}/versions/{version-id}/content
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Response

Returns a `302 Found` response redirecting to a preauthenticated download URL for the bytes of the file.

To download the contents of the file your application needs to follow the `Location` header in the response. Many HTTP client libraries will automatically follow the 302 redirection and start downloading the file immediately.

Preauthenticated download URLs are only valid for a short period of time \(a few minutes\) and don't require an `Authorization` header to download.

## Examples

### Example 1: Download the contents of a previous version of a file

This example retrieves a version of a file in the current user's drive.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET /me/drive/items/{item-id}/versions/{version-id}/content
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Drives["{drive-id}"].Items["{driveItem-id}"].Versions["{driveItemVersion-id}"].Content.GetAsync();
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
graphClient.Drives().ByDriveId("drive-id").Items().ByDriveItemId("driveItem-id").Versions().ByDriveItemVersionId("driveItemVersion-id").Content().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.drives().byDriveId("{drive-id}").items().byDriveItemId("{driveItem-id}").versions().byDriveItemVersionId("{driveItemVersion-id}").content().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let stream = await client.api('/me/drive/items/{item-id}/versions/{version-id}/content')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->drives()->byDriveId('drive-id')->items()->byDriveItemId('driveItem-id')->versions()->byDriveItemVersionId('driveItemVersion-id')->content()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

Get-MgDriveItemVersionContent -DriveId $driveId -DriveItemId $driveItemId -DriveItemVersionId $driveItemVersionId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.drives.by_drive_id('drive-id').items.by_drive_item_id('driveItem-id').versions.by_drive_item_version_id('driveItemVersion-id').content.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The call returns a redirect to where the contents of the version can be downloaded.

```http
HTTP/1.1 302 Found
Location: https://onedrive.com/34FF49D6...
```

### Example 2: Download a partial range of bytes from a previous version of a file

To download a partial range of bytes from a **driveItemVersion**, your app can use the `Range` header as specified in [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt). You must append the `Range` header when following the redirect and not to the request for `/content`.

```http
GET https://onedrive.com/34FF49D6...
Range: bytes=0-1023
```

The call returns an `HTTP 206 Partial Content` response with the request range of bytes from the file. If the range can't be generated, then the `Range` header may be ignored and an `HTTP 200` response would be returned with the full contents of the file.

```http
HTTP/1.1 206 Partial Content
Content-Range: bytes 0-1023/2048

<first 1024 bytes of file>
```

## Remarks

OneDrive doesn't preserve the complete metadata for previous versions of a file.

When your app retrieves the list of available versions for a file, a [driveItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/driveitemversion?view=graph-rest-1.0) resource is returned that provides the available information about the specific version.
