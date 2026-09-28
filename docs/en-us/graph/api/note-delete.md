<!-- Source: https://learn.microsoft.com/en-us/graph/api/note-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Delete note

Namespace: microsoft.graph

Delete a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object. Supports optimistic concurrency control via the `If-Match` header.

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
DELETE /me/notes/{note-id}
DELETE /users/{id | userPrincipalName}/notes/{note-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| If-Match | The **changeKey** value for the note is used for optimistic concurrency control. Optional. We recommend that you use this header to avoid conflicts. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

If the `If-Match` header doesn't match the current **changeKey**, this method returns a `412 Precondition Failed` response code.

## Examples

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/me/notes/AAMkAGI2THVSAAA=
If-Match: "CQAAABYAAABG"
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
