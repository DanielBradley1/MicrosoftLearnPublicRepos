<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-post-recipients -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Add recipient

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Add a [user](https://learn.microsoft.com/en-us/graph/api/resources/user) reference as a recipient of a spending policy's [costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertsetting). A reference that doesn't resolve to a user in the tenant is refused with a `400 alertRecipientNotFound` response.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Policy.ReadWrite.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings/recipients/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |
| `If-Match` | The ETag of the parent spending policy. Required. |

## Request body

In the request body, supply a JSON object with an `@odata.id` property set to the reference URL of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user) to add.

## Response

If successful, this method returns a `204 No Content` response code and an advanced `ETag` header. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/emailThresholdSettings/recipients/$ref
If-Match: W/"8"
Content-Type: application/json

{
  "@odata.id": "https://graph.microsoft.com/beta/users/9c4d1e2a-7f3b-4a11-8c60-2b7e5f0a91d4"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
ETag: W/"9"
```
