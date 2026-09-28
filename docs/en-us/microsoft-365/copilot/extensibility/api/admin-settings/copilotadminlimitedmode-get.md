<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/copilotadminlimitedmode-get -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# Get copilotAdminLimitedMode

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Read the properties and relationships of a [copilotAdminLimitedMode](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadminlimitedmode) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotSettings-LimitedMode.Read | CopilotSettings-LimitedMode.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

Global Reader is the least privileged [administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) supported for this operation.

## HTTP request

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/settings/limitedMode
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/settings/limitedMode
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [copilotAdminLimitedMode](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotadminlimitedmode) object in the response body.

This API can also return more HTTP status codes, such as `403 Forbidden`, `500 Internal Server Error`, and `429 Too Many Requests`.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/copilot/admin/settings/limitedMode
```

```http
GET https://graph.microsoft.com/beta/copilot/admin/settings/limitedMode
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.copilotAdminLimitedMode",
  "isEnabledForGroup": true,
  "groupId": "4c563cdf-0efa-44c5-a384-dbf57db277df"
}
```
