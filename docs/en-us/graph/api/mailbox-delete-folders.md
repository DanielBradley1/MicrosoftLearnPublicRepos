<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailbox-delete-folders?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# Delete mailboxFolder

Namespace: microsoft.graph

Delete a [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) or a child **mailboxFolder** within a mailbox.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxFolder.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MailboxFolder.ReadWrite.All | Not available. |

## HTTP request

```http
DELETE /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}
DELETE /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}/childFolders/{mailboxFolderId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows how to delete a mailbox folder.

```http
DELETE https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0648f21@aab09c93/folders/AAMkAGVmMDEzM
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
