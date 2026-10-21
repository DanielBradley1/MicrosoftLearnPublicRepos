<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-post-assignedgroups -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Add assignedGroup

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Add a [group](https://learn.microsoft.com/en-us/graph/api/resources/group) reference to a [selectedGroupsSpendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/selectedgroupsspendingpolicy) object. Linking the first group can activate a disabled policy once its other requirements are met.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Assignment.ReadWrite.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /copilot/costManagement/spendingPolicies/{id}/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |
| `If-Match` | The ETag of the spending policy. Required. |

## Request body

In the request body, supply a JSON object with an `@odata.id` property set to the reference URL of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group) to add.

## Response

If successful, this method returns a `204 No Content` response code and an advanced `ETag` header. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups/$ref
If-Match: W/"1"
Content-Type: application/json

{
  "@odata.id": "https://graph.microsoft.com/beta/groups/11112222-3333-4444-5555-666677778888"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
ETag: W/"2"
```
