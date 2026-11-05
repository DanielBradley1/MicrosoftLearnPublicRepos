<!-- Source: https://learn.microsoft.com/en-us/graph/api/migrationsroot-list-crosstenantmigrationjobs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# List crossTenantMigrationJobs

Namespace: microsoft.graph

Get a list of the [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) objects and their properties. By default, 20 objects are returned. You can retrieve more objects by using the **@odata.nextLink** URL provided in the response.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CrossTenantContentMigration.Read.All | CrossTenantContentMigration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CrossTenantContentMigration.Read.All | CrossTenantContentMigration.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Microsoft 365 Migration Administrator
- Global Administrator

## HTTP request

```http
GET /solutions/migrations/crossTenantMigrationJobs
```

## Optional query parameters

This method supports the `$select`, `$orderby`, `$count`, `$top`, and `$skiptoken` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response. The `$orderby` query parameter sorts only the current page, `$count` returns the number of objects in the current page, and `$top` can reduce the page size but can't return more than 20 objects. To retrieve the next page, use the **@odata.nextLink** URL provided in the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/solutions/migrations/crossTenantMigrationJobs
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#solutions/migrations/crossTenantMigrationJobs",
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/solutions/migrations/crossTenantMigrationJobs?$skiptoken=%5b%7B%22compositeToken%22%3a%7B%22token%22%3a%22%2bRID%3a~q1NPAJxLNS1QBAAAAAAAAA%3d%3d%23RT%3a1%23TRC%3a20%23RTD%3aHPJJmKT1uZqlBBnGyNSOBMHbIcd%5d",
  "value": [
    {
      "id": "012ec4f4-df7e-41ae-ba95-6d7ccb8f74a1",
      "displayName": "Contoso_migration_job",
      "status": "completed",
      "jobType": "migrate",
      "message": "The batch and all of its users have been successfully migrated with no failures.",
      "completeAfterDateTime": "2025-11-06T09:11:33.2115505Z",
      "sourceTenantId": "12345678-1234-1234-1234-123456789012",
      "targetTenantId": "87654321-4321-4321-4321-210987654321",
      "resourceType": "users",
      "resources": [],
      "workloads": [],
      "createdBy": "a0d9fdb1-171f-4e2b-8a82-06775ad24790",
      "createdDateTime": "2025-11-06T09:06:34.4773205Z",
      "lastUpdatedDateTime": "2025-11-06T11:26:00Z",
      "exchangeSettings": {
        "targetDeliveryDomain": "fabrikam.onmicrosoft.com",
        "sourceEndpoint": "EXOHandler"
      }
    },
    {
      "id": "0d1d9dbb-7676-4731-a601-5e8406fd7bcf",
      "displayName": "Contoso_validation_job",
      "status": "validatePassed",
      "jobType": "validate",
      "message": "Validation has completed successfully with no failures.",
      "completeAfterDateTime": "2025-05-22T17:14:52Z",
      "sourceTenantId": "12345678-1234-1234-1234-123456789012",
      "targetTenantId": "87654321-4321-4321-4321-210987654321",
      "resourceType": "users",
      "resources": [],
      "workloads": [
        "teams"
      ],
      "createdBy": "a0d9fdb1-171f-4e2b-8a82-06775ad24790",
      "createdDateTime": "2025-11-07T00:19:21.4810014Z",
      "lastUpdatedDateTime": "2025-11-07T00:22:03Z",
      "exchangeSettings": {
        "targetDeliveryDomain": "fabrikam.onmicrosoft.com",
        "sourceEndpoint": "EXOHandler"
      }
    }
  ]
}
```
