<!-- Source: https://learn.microsoft.com/en-us/graph/api/calendar-permanentdelete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# calendar: permanentDelete

Namespace: microsoft.graph

Permanently delete a calendar folder and the events that it contains and remove them from the mailbox. For more information about item retention, see [Configure deleted item retention and recoverable items quotas](https://learn.microsoft.com/en-us/exchange/configure-deleted-item-retention-and-recoverable-items-quotas-exchange-2013-help).

Note

Folders aren't placed in the **purges** folder when they're permanently deleted. Permanently deleted folders are removed from the mailbox.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Calendars.ReadWrite | Not available. |

## HTTP request

```http
POST /users/{id | userPrincipalName}/calendars/{calendarId}/permanentDelete
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/users/b4c80c57-5c59-4a3d-912a-a83985988b82/calendars/permanentDelete
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/b4c80c57-5c59-4a3d-912a-a83985988b82/calendars/permanentDelete')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
