<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-post-notes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Create note

Namespace: microsoft.graph

Create a new [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) in the user's *Notes* folder.

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
POST /me/notes
POST /users/{id | userPrincipalName}/notes
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object.

You can specify the following properties when you create a **note**.

| Property | Type | Description |
| :--- | :--- | :--- |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The content of the note. Supports `text` or `html` content types. Required. |
| categories | String collection | The categories associated with the note. Optional. |
| subject | String | The title of the note. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/me/notes
Content-Type: application/json

{
  "subject": "Project Ideas",
  "body": {
    "contentType": "html",
    "content": "<html><body><p>Consider implementing automated testing framework</p></body></html>"
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
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
