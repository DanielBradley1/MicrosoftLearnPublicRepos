<!-- Source: https://learn.microsoft.com/en-us/graph/api/driveitem-put-content?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Upload or replace the contents of a driveItem

Namespace: microsoft.graph

Provide the contents of a new file or update the contents of an existing file in a single API call. This method only supports files up to 250 MB in size.

To upload large files, see [Upload large files with an upload session](https://learn.microsoft.com/en-us/graph/api/driveitem-createuploadsession?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.ReadWrite | Files.ReadWrite.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Files.ReadWrite | Files.ReadWrite.All |
| Application | Files.ReadWrite.All | Sites.ReadWrite.All |

Note

Replacing the contents of a file protected with a sensitivity label is not supported with app-only authentication. Use delegated permissions \(user context\) instead.

Note

SharePoint Embedded requires the `FileStorageContainer.Selected` permission to access the content of the container. This permission is different from the ones mentioned previously. In addition to Microsoft Graph permissions, your app must have the necessary [container type permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#container-type-application-permissions) to call this API. For more information, see [SharePoint Embedded authentication and authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth).

## HTTP request

### To replace an existing item

```http
PUT /drives/{drive-id}/items/{item-id}/content
PUT /groups/{group-id}/drive/items/{item-id}/content
PUT /me/drive/items/{item-id}/content
PUT /sites/{site-id}/drive/items/{item-id}/content
PUT /users/{user-id}/drive/items/{item-id}/content
```

### To upload a new file

```http
PUT /drives/{drive-id}/items/{parent-id}:/{filename}:/content
PUT /groups/{group-id}/drive/items/{parent-id}:/{filename}:/content
PUT /me/drive/items/{parent-id}:/{filename}:/content
PUT /sites/{site-id}/drive/items/{parent-id}:/{filename}:/content
PUT /users/{user-id}/drive/items/{parent-id}:/{filename}:/content
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | text/plain. Required. |

## Request body

The contents of the request body should be the binary stream of the file to be uploaded.

## Response

If successful, this method returns a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) object in the response body for the newly created or updated file.

## Examples

### Example 1: Upload a new file

#### Request

This example uploads the string "The contents of the file goes here." to a file in the signed-in user's drive under FolderA named FileB.txt.

```http
PUT https://graph.microsoft.com/v1.0/me/drive/root:/FolderA/FileB.txt:/content
Content-Type: text/plain

The contents of the file goes here.
```

#### Response

If successful, this method returns an [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resource in the response body for the newly created file.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0123456789abc",
  "name": "FileB.txt",
  "size": 35,
  "file": { }
}
```

### Example 2: Updating an existing file

#### Request

This example replaces the contents of a file with a known ID.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)
- [PowerShell](#tabpanel_1_powershell)

```http
PUT https://graph.microsoft.com/v1.0/me/drive/items/{item-id}/content
Content-Type: text/plain

The contents of the file goes here.
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = The contents of the file goes here.;

await client.api('/me/drive/items/{item-id}/content')
	.put(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Files

$params = The contents of the file goes here.


Set-MgDriveItemContent -DriveId $driveId -DriveItemId $driveItemId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

If successful, this method returns an [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resource in the response body for the newly created file.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "id": "0123456789abc",
  "name": "FileB.txt",
  "size": 35,
  "file": { }
}
```

## Error responses

See [Error Responses](https://learn.microsoft.com/en-us/graph/errors) for details about how errors are returned.
