<!-- Source: https://learn.microsoft.com/en-us/graph/api/note-list-attachments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# List note attachments

Namespace: microsoft.graph

Get the list of file attachments associated with a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0). Only inline image attachments \(image/png, image/jpeg, image/gif, or image/bmp\) are supported, with a maximum size of 3 MB per attachment.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ShortNotes.Read | ShortNotes.ReadWrite |
| Delegated \(personal Microsoft account\) | ShortNotes.Read | ShortNotes.ReadWrite |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /me/notes/{note-id}/attachments
GET /users/{id | userPrincipalName}/notes/{note-id}/attachments
```

## Optional query parameters

This method supports the `$filter`, `$select`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

You can use the `$expand` query parameter to include all of the note attachments inline with the rest of the note properties. For example:

```http
GET https://graph.microsoft.com/v1.0/me/notes/{note-id}?$expand=attachments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/notes/AAMkAGI2THVSAAA=/attachments
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.fileAttachment",
      "id": "AAMkAGI2attach1",
      "name": "whiteboard.png",
      "contentType": "image/png",
      "size": 45678,
      "isInline": true,
      "contentId": "image001",
      "lastModifiedDateTime": "2024-01-15T14:30:00Z"
    }
  ]
}
```
