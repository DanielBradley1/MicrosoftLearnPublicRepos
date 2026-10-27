<!-- Source: https://learn.microsoft.com/en-us/graph/api/privilegedaccessroot-delete-customextensions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# Delete roleManagementCustomCalloutExtension

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete a [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-beta) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | PrivilegedAccess-CustomExt.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | PrivilegedAccess-CustomExt.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Privileged Role Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
DELETE /identityGovernance/privilegedAccess/customExtensions/{roleManagementCustomCalloutExtensionId}
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

The following example deletes a custom extension.

```http
DELETE https://graph.microsoft.com/beta/identityGovernance/privilegedAccess/customExtensions/a1b2c3d4-e5f6-4a5b-8c9d-0e1f2a3b4c5d
```

### Response

```http
HTTP/1.1 204 No Content
```
