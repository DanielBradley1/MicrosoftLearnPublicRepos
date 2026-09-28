<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailboxfolder-delete-items?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# Delete mailboxItem

Namespace: microsoft.graph

Delete a [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) from a [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) in a mailbox.

Use the **disposalType** query parameter to specify whether to soft-delete or hard-delete the item.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxItem.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MailboxItem.ReadWrite.All | Not available. |

## HTTP request

```http
DELETE /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}/items/{mailboxItemId}?disposalType={disposalType}
```

## Query parameters

In the request URL, provide the following required query parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| disposalType | String | Required. The type of delete operation to perform. The possible values are: `softDelete`, `hardDelete`. Use `softDelete` to follow Exchange soft-delete semantics, or `hardDelete` to permanently delete the item. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | \*\*\*\*\*\* Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

Note

When you use `hardDelete`, the Exchange service permanently deletes the item only when it's customer data that isn't protected by a legal hold, retention policy, audit, compliance, or system-item restriction. Otherwise, the request fails with a `403 Forbidden` error.

## Examples

### Example 1: Soft-delete a mailbox item

The following example shows how to soft-delete a mailbox item in a folder by using `disposalType=softDelete`.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
DELETE https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0648f21@aab09c93/folders/inbox/items/AAMkADk0MzI?disposalType=softDelete
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/admin/exchange/mailboxes/MBX:e0648f21@aab09c93/folders/inbox/items/AAMkADk0MzI?disposalType=softDelete')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Hard-delete a mailbox item

The following example shows how to hard-delete an eligible mailbox item in Recoverable Items by using `disposalType=hardDelete`.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
DELETE https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0648f21@aab09c93/folders/recoverableitemsdeletions/items/AAMkADk0MzI?disposalType=hardDelete
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/admin/exchange/mailboxes/MBX:e0648f21@aab09c93/folders/recoverableitemsdeletions/items/AAMkADk0MzI?disposalType=hardDelete')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
