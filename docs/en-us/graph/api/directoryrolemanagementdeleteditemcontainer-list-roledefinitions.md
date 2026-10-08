<!-- Source: https://learn.microsoft.com/en-us/graph/api/directoryrolemanagementdeleteditemcontainer-list-roledefinitions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# List roleDefinitions

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

List custom [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) objects that have been soft-deleted from Microsoft Entra directory role management. Built-in role definitions can't be deleted and aren't returned.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | RoleManagement.Read.Directory | RoleManagement.ReadWrite.Directory |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | RoleManagement.Read.Directory | RoleManagement.ReadWrite.Directory |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Directory Readers
- Global Reader
- Privileged Role Administrator

## HTTP request

```http
GET /roleManagement/directory/deletedItems/roleDefinitions
```

## Optional query parameters

This method supports the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/beta/roleManagement/directory/deletedItems/roleDefinitions
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#roleManagement/directory/deletedItems/roleDefinitions",
  "value": [
    {
      "id": "a1b2c3d4-5678-90ab-cdef-1234567890ab",
      "description": "Can manage basic aspects of application registrations.",
      "displayName": "Application Support Administrator",
      "isBuiltIn": false,
      "isEnabled": true,
      "rolePermissions": [
        {
          "allowedResourceActions": [
            "microsoft.directory/applications/basic/update"
          ]
        }
      ]
    }
  ]
}
```
