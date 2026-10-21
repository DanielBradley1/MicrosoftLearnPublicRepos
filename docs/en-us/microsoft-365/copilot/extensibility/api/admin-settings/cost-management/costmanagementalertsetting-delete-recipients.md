<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-delete-recipients -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Remove recipient

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Remove a [user](https://learn.microsoft.com/en-us/graph/api/resources/user) reference from the recipients of a spending policy's [costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertsetting). Removing the last recipient while alerting is enabled is refused with a `400 alertRecipientsRequired` response.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Policy.ReadWrite.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
DELETE /copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings/recipients/{userId}/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `If-Match` | The ETag of the parent spending policy. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/emailThresholdSettings/recipients/9c4d1e2a-7f3b-4a11-8c60-2b7e5f0a91d4/$ref
If-Match: W/"9"
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
ETag: W/"10"
```
