<!-- Source: https://learn.microsoft.com/en-us/graph/api/note-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Get note

Namespace: microsoft.graph

Read the properties and relationships of a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object.

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
GET /me/notes/{note-id}
GET /users/{id | userPrincipalName}/notes/{note-id}
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

Use `$expand=attachments` to include file attachments in the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get a note

The following example shows how to get a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object.

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/notes/AAMkAGI2THVSAAA=
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/notes/$entity",
  "id": "AAMkAGI2THVSAAA=",
  "changeKey": "CQAAABYAAABE",
  "createdDateTime": "2024-01-20T10:30:00Z",
  "lastModifiedDateTime": "2024-01-20T10:30:00Z",
  "categories": [],
  "subject": "Project Ideas",
  "body": {
    "contentType": "html",
    "content": "<html><body><p>Consider implementing automated testing framework</p></body></html>"
  },
  "bodyPreview": "Consider implementing automated testing framework",
  "isDeleted": false,
  "hasAttachments": false
}
```

### Example 2: Get a note with attachments

The following example shows how to get a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object using `$expand` to include attachments.

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/me/notes/AAMkAGI2THVSAAA=?$expand=attachments
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user-id')/notes/$entity",
  "id": "AAMkAGI2THVSAAA=",
  "changeKey": "CQAAABYAAABE",
  "createdDateTime": "2024-01-15T14:00:00Z",
  "lastModifiedDateTime": "2024-01-15T14:30:00Z",
  "categories": [],
  "subject": "Meeting Whiteboard",
  "body": {
    "contentType": "html",
    "content": "<html><body><p>Key discussion points:</p><img src=\"cid:image001\" /></body></html>"
  },
  "bodyPreview": "Key discussion points:",
  "isDeleted": false,
  "hasAttachments": true,
  "attachments": [
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
