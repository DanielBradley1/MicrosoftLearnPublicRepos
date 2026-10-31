<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-delete-slapolicies?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# Delete slaPolicyDefinition

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Delete an [slaPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicydefinition?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CaseManagement.ConfigManage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CaseManagement.ConfigManage.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported built-in [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json), in addition to the `CaseManagement.ConfigManage.All` permission. **Security Administrator** is the least privileged role supported for this operation.

## HTTP request

```http
DELETE /security/caseManagement/caseTypeConfigurations/{caseTypeConfiguration-id}/slaPolicies/{slaPolicyDefinition-id}
```

Replace `{caseTypeConfiguration-id}` with the owning case type: `incidentCase`, `genericCase`, or `exposureCase`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

#### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/beta/security/caseManagement/caseTypeConfigurations/incidentCase/slaPolicies/8f3b6c2e-2f2a-4b8e-9a1e-2f1c4d5a6b7c
```

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
