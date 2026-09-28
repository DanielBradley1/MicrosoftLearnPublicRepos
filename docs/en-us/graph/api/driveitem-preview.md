<!-- Source: https://learn.microsoft.com/en-us/graph/api/driveitem-preview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# driveItem: preview

Namespace: microsoft.graph

This action allows you to obtain a short-lived embeddable URL for an item in order to render a temporary preview.

If you want to obtain long-lived embeddable links, use the [createLink](https://learn.microsoft.com/en-us/graph/api/driveitem-createlink?view=graph-rest-1.0) API instead.

Note

The **preview** action is currently only available on SharePoint and OneDrive for Business.

Caution

The preview URL is intended for the caller's own use and shouldn't be shared with other users. The preview renders on behalf of the calling identity, and anyone who accesses the URL acts as the caller with the caller's permissions. This is particularly important in application permission scenarios where your app has `read-write access` to the file but you intend to provide end users with `read-only` access. In such cases, take precautions such as restricting DOM access to page internals and obtaining the preview URL using an application identity with read-only access.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Files.Read | Files.Read.All, Files.ReadWrite, Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Files.Read.All | Files.ReadWrite.All, Sites.Read.All, Sites.ReadWrite.All |

Note

SharePoint Embedded requires the `FileStorageContainer.Selected` permission to access the content of the container. This permission is different from the ones mentioned previously. In addition to Microsoft Graph permissions, your app must have the necessary [container type permissions](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/development/auth#container-type-application-permissions) to call this API. For more information, see [SharePoint Embedded authentication and authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth).

## HTTP request

```http
POST /drives/{driveId}/items/{itemId}/preview
POST /groups/{groupId}/drive/items/{itemId}/preview
POST /me/drive/items/{itemId}/preview
POST /sites/{siteId}/drive/items/{itemId}/preview
POST /users/{userId}/drive/items/{itemId}/preview
POST /shares/{shareId}/driveItem/preview
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

The body of the request defines properties of the embeddable URL your application is requesting. The request should be a JSON object with the following properties.

| Name | Type | Description |
| :--- | :--- | :--- |
| page | string/number | Optional. Page number of document to start at, if applicable. Specified as string for future use cases around file types such as ZIP. |
| zoom | number | Optional. Zoom level to start at, if applicable. |

## Response

```json
{
    "getUrl": "https://www.onedrive.com/embed?foo=bar&bar=baz",
    "postParameters": "param1=value&param2=another%20value",
    "postUrl": "https://www.onedrive.com/embed_by_post"
}
```

The response will be a JSON object containing the following properties:

| Name | Type | Description |
| :--- | :--- | :--- |
| getUrl | string | URL suitable for embedding using HTTP GET \(iframes, etc.\) |
| postUrl | string | URL suitable for embedding using HTTP POST \(form post, JS, etc.\) |
| postParameters | string | POST parameters to include if using postUrl |

Either getUrl, postUrl, or both might be returned depending on the current state of embed support for the specified options.

postParameters is a string formatted as `application/x-www-form-urlencoded`, and if performing a POST to the postUrl the content-type should be set accordingly. For example:

```
POST https://www.onedrive.com/embed_by_post
Content-Type: application/x-www-form-urlencoded

param1=value&param2=another%20value
```

### Page/zoom

The 'page' and 'zoom' options may not be available for all preview apps, but will be applied if the preview app supports it.
