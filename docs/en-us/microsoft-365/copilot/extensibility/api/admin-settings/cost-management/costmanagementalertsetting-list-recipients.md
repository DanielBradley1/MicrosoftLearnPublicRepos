<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementalertsetting-list-recipients -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# List recipients

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get the list of [user](https://learn.microsoft.com/en-us/graph/api/resources/user) objects notified by a spending policy's [costManagementAlertSetting](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementalertsetting). You can read the recipients as `user` objects, or read the reference links with the `$ref` form.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Policy.Read.All | CopilotCostManagement-Policy.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings/recipients
GET /copilot/costManagement/spendingPolicies/{id}/emailThresholdSettings/recipients/$ref
```

## Optional query parameters

This method doesn't support any [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [user](https://learn.microsoft.com/en-us/graph/api/resources/user) objects in the response body. For the `$ref` form, the response body is a collection of reference links.

## Examples

### Example 1: List recipients as user objects

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/emailThresholdSettings/recipients
```

#### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#users",
  "value": [
    {
      "id": "9c4d1e2a-7f3b-4a11-8c60-2b7e5f0a91d4",
      "displayName": "Dana Finance",
      "userPrincipalName": "dana@contoso.com"
    }
  ]
}
```

### Example 2: List recipient reference links

#### Request

The following example shows a request that uses the `$ref` form to read the recipient reference links.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/emailThresholdSettings/recipients/$ref
```

#### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection($ref)",
  "value": [
    {
      "@odata.id": "https://graph.microsoft.com/beta/users/9c4d1e2a-7f3b-4a11-8c60-2b7e5f0a91d4"
    }
  ]
}
```
