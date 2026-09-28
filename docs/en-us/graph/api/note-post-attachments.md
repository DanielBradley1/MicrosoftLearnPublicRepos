<!-- Source: https://learn.microsoft.com/en-us/graph/api/note-post-attachments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Create attachment

Namespace: microsoft.graph

Create a [fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0) object, which adds an inline image attachment to a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0). Only image file types \(image/png, image/jpeg, image/gif, or image/bmp\) are supported, with a maximum size of 3 MB per attachment. Use the **contentId** property to reference the attachment in the HTML body of a note by using `<img src="cid:{contentId}" />`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ShortNotes.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | ShortNotes.ReadWrite | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /me/notes/{note-id}/attachments
POST /users/{id | userPrincipalName}/notes/{note-id}/attachments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0) object.

You can specify the following properties when you create an attachment.

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | The OData type of the attachment resource. Required. Set to `#microsoft.graph.fileAttachment`. |
| name | String | The file name of the attachment. Required. |
| contentType | String | The MIME type of the attachment. Must be an image type: `image/png`, `image/jpeg`, `image/gif`, or `image/bmp`. Required. |
| contentBytes | String | The base64-encoded contents of the file. Required. |
| contentId | String | The ID used for referencing the attachment in the HTML body via `cid:`. Required. |
| isInline | Boolean | Indicates whether the attachment is an inline attachment. Must be set to `true` for note attachments. Required. |

## Response

If successful, this method returns a `201 Created` response code and an [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/notes/AAMkAGI2THVSAAA=/attachments
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileAttachment",
  "name": "screenshot.png",
  "contentType": "image/png",
  "contentBytes": "iVBORw0KGgoAAAANSUhEUgAAAAUA...",
  "contentId": "screenshot-001",
  "isInline": true
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.fileAttachment",
  "id": "AAMkAGI2attach2",
  "name": "screenshot.png",
  "contentType": "image/png",
  "size": 12456,
  "isInline": true,
  "contentId": "screenshot-001",
  "lastModifiedDateTime": "2024-01-29T11:30:00Z"
}
```
