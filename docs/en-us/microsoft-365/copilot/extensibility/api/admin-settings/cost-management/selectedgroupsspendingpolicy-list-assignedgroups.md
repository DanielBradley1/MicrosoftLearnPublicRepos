<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/selectedgroupsspendingpolicy-list-assignedgroups -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# List assignedGroups

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get the list of [group](https://learn.microsoft.com/en-us/graph/api/resources/group) objects assigned to a [selectedGroupsSpendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/selectedgroupsspendingpolicy) object. The `assignedGroups` relationship is declared only on the selected-groups subtype, so these routes use the `microsoft.graph.selectedGroupsSpendingPolicy` cast segment and return a `404` response against a tenant-wide policy.

You can read the assigned groups as `group` objects, or read the reference links with the `$ref` form.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CopilotCostManagement-Assignment.Read.All | CopilotCostManagement-Assignment.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
GET /copilot/costManagement/spendingPolicies/{id}/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups
GET /copilot/costManagement/spendingPolicies/{id}/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups/$ref
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

If successful, this method returns a `200 OK` response code and a collection of [group](https://learn.microsoft.com/en-us/graph/api/resources/group) objects in the response body. For the `$ref` form, the response body is a collection of reference links.

## Examples

### Example 1: List assigned groups as group objects

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups
```

#### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#groups",
  "value": [
    {
      "id": "11112222-3333-4444-5555-666677778888",
      "displayName": "Pilot group A"
    }
  ]
}
```

### Example 2: List assigned group reference links

#### Request

The following example shows a request that uses the `$ref` form to read the assigned-group reference links.

```http
GET https://graph.microsoft.com/beta/copilot/costManagement/spendingPolicies/3f9e2c1a-0000-0000-0000-00000000c21b/microsoft.graph.selectedGroupsSpendingPolicy/assignedGroups/$ref
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
      "@odata.id": "https://graph.microsoft.com/beta/groups/11112222-3333-4444-5555-666677778888"
    }
  ]
}
```
