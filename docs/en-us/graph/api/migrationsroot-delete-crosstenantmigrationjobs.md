<!-- Source: https://learn.microsoft.com/en-us/graph/api/migrationsroot-delete-crosstenantmigrationjobs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Delete crossTenantMigrationJob

Namespace: microsoft.graph

Delete a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) object. Delete requests are long-running and finish within 48 hours.

A [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) that is currently in progress can't be deleted. You can perform the deletion only after the [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) reaches a final state. If a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) isn't in a final state, a `409 Conflict` response is returned.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CrossTenantContentMigration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CrossTenantContentMigration.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Microsoft 365 Migration Administrator
- Global Administrator

## HTTP request

```http
DELETE /solutions/migrations/crossTenantMigrationJobs/{crossTenantMigrationJobId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `202 Accepted` response code.

If the [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) isn't in a terminal or final state, a `409 Conflict` response is returned.

## Examples

### Request

The following example shows a request.

```http
DELETE https://graph.microsoft.com/v1.0/solutions/migrations/crossTenantMigrationJobs/add14989-2b21-4001-81bd-a18b0bac1dea
```

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
