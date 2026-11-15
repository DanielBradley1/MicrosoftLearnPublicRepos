<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-delete-settings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Delete conditionalAccessSettings

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Reset [Conditional Access settings](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssettings?view=graph-rest-beta) to their defaults. This operation clears user-action exclusions without deleting the settings singleton.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ConditionalAccess | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ConditionalAccess | Not available. |

## HTTP request

```http
DELETE /identity/conditionalAccess/settings
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

The following example shows a request.

```http
DELETE https://graph.microsoft.com/beta/identity/conditionalAccess/settings
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
