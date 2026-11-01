<!-- Source: https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-validate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# crossTenantMigrationJob: validate

Namespace: microsoft.graph

Validate the configuration of a [cross-tenant migration job](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) asynchronously. This action doesn't migrate any content, but goes through validation for the specified workloads to find any errors or misconfigurations that affect an actual migration job. The job must be in a `submitted` or `validateFailed` status before you can call this action.

This action is asynchronous. After you call the **validate** API, poll the [Get crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-get?view=graph-rest-1.0) endpoint to check for a terminal status of `validatePassed` or `validateFailed`.

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
POST /solutions/migrations/crossTenantMigrationJobs/{crossTenantMigrationJobId}/validate
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) in the response body.

This method can also return the following error codes in the response body.

| Status code | Description |
| :--- | :--- |
| `404 Not Found` | The specified **crossTenantMigrationJob** wasn't found. |
| `409 Conflict` | The job isn't in a valid status for validation. The job must be in `submitted` or `validateFailed` status. |

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/migrations/crossTenantMigrationJobs/add14989-2b21-4001-81bd-a18b0bac1dea/validate
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.crossTenantMigrationJob",
  "id": "add14989-2b21-4001-81bd-a18b0bac1dea",
  "displayName": "Contoso_migration_job",
  "status": "validateSubmitted",
  "jobType": "validate",
  "message": "Validation job has been submitted successfully",
  "completeAfterDateTime": "2026-05-22T17:14:52Z",
  "sourceTenantId": "12345678-1234-1234-1234-123456789012",
  "targetTenantId": "87654321-4321-4321-4321-210987654321",
  "resourceType": "users",
  "resources": [],
  "workloads": [
    "Teams",
    "Exchange",
    "ODSP"
  ],
  "createdBy": "admin@fabrikam.onmicrosoft.com",
  "createdDateTime": "2026-05-04T20:55:10.5427196Z",
  "lastUpdatedDateTime": "2026-05-04T20:55:10Z",
  "exchangeSettings": {
    "targetDeliveryDomain": "fabrikam.com",
    "sourceEndpoint": "EXOHandler"
  }
}
```
