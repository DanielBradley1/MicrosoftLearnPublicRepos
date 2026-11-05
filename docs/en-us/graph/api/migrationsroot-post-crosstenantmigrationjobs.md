<!-- Source: https://learn.microsoft.com/en-us/graph/api/migrationsroot-post-crosstenantmigrationjobs?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Create crossTenantMigrationJob

Namespace: microsoft.graph

Create a new [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) object. A job defines the migration batch but doesn't start validation or migration. After you create the job, call [validate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-validate?view=graph-rest-1.0) to verify tenant and resource configuration, then call [migrate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-migrate?view=graph-rest-1.0) to begin the actual migration.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

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
POST /solutions/migrations/crossTenantMigrationJobs
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) object.

You can specify the following properties when you create a **crossTenantMigrationJob**.

| Property | Type | Description |
| :--- | :--- | :--- |
| completeAfterDateTime | DateTimeOffset | Date and time when the migration batch should start. Required. |
| displayName | String | Name of the **crossTenantMigrationJob**. Must be unique per tenant. Required. |
| exchangeSettings | [exchangeOnlineCrossTenantMigrationSettings](https://learn.microsoft.com/en-us/graph/api/resources/exchangeonlinecrosstenantmigrationsettings?view=graph-rest-1.0) | Settings for Exchange Online migrations. Optional, but required if Exchange is a specified workload. |
| resources | String collection | Object IDs \(GUID\) of the resources to migrate. Limit of 2,000 resources per [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0). Required. |
| resourceType | String | Type of resources to migrate. Only `Users` is supported at this time. Required. |
| sourceTenantId | String | Tenant ID \(GUID\) of the source tenant for the migration. Required. |
| workloads | String collection | Workloads to migrate on the resources. Optional. If excluded, all available workloads are included in the migration. |

## Response

If successful, this method returns a `201 Created` response code and a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/v1.0/solutions/migrations/crossTenantMigrationJobs
Content-Type: application/json

{
  "displayName": "xtmigration_user_req_1",
  "completeAfterDateTime": "2024-12-09T22:48:03.092Z",
  "sourceTenantId": "12345678-1234-1234-1234-123456789012",
  "exchangeSettings": {
    "targetDeliveryDomain": "xtmigration.onmicrosoft.com",
    "sourceEndpoint": "sampleEndpointText"
  },
  "resources": [
    "4dd550d9-9ea2-4e71-a16b-60b1d1c4f506",
    "63f15b55-f61a-49cb-a599-2e3d233afb2c",
    "41d94bac-3a53-47d6-a89e-583830104e15"
  ],
  "resourceType": "Users",
  "workloads": [
    "Teams",
    "Exchange",
    "ODSP"
  ]
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#solutions/migrations/crossTenantMigrationJobs/$entity",
  "id": "add14989-2b21-4001-81bd-a18b0bac1dea",
  "displayName": "Contoso_migration_job",
  "jobType": "validate",
  "status": "submitted",
  "message": "",
  "completeAfterDateTime": "2023-12-17T20:38:04.101Z",
  "targetTenantId": "87654321-4321-4321-4321-210987654321",
  "sourceTenantId": "12345678-1234-1234-1234-123456789012",
  "exchangeSettings": {
    "targetDeliveryDomain": "fabrikam.onmicrosoft.com",
    "sourceEndpoint": "sampleEndpointText"
  },
  "resources": [
    "4dd550d9-9ea2-4e71-a16b-60b1d1c4f506",
    "63f15b55-f61a-49cb-a599-2e3d233afb2c",
    "41d94bac-3a53-47d6-a89e-583830104e15"
  ],
  "resourceType": "Users",
  "workloads": ["Teams", "Exchange", "ODSP"],
  "createdBy": "admin@fabrikam.onmicrosoft.com",
  "createdDateTime": "2025-11-14T20:55:10.5427196Z",
  "lastUpdatedDateTime": "2025-11-14T20:55:10.5427196Z"
}
```
