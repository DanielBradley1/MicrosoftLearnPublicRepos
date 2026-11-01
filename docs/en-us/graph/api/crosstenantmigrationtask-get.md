<!-- Source: https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationtask-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Get crossTenantMigrationTask

Namespace: microsoft.graph

Read the properties and relationships of a [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) object that provides details about the migration task for a single user in a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0). The [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) contains the [status details](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationservicestatusdetails?view=graph-rest-1.0) of migrations for the workloads specified in the **crossTenantMigrationJob**.

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
GET /solutions/migrations/crossTenantMigrationJobs/{crossTenantMigrationJobId}/users/{crossTenantMigrationTaskId}
```

## Optional query parameters

This method doesn't support [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/solutions/migrations/crossTenantMigrationJobs/012ec4f4-df7e-41ae-ba95-6d7ccb8f74a1/users/6a88de8d-7027-44c1-8674-03f826aa1704
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#solutions/migrations/crossTenantMigrationJobs('012ec4f4-df7e-41ae-ba95-6d7ccb8f74a1')/users/$entity",
  "id": "6a88de8d-7027-44c1-8674-03f826aa1704",
  "lastUpdatedDateTime": "2025-11-06T11:25:36Z",
  "currentStatus": [
    {
      "service": "ODSP",
      "status": "completed",
      "message": "",
      "errors": []
    },
    {
      "service": "Meeting",
      "status": "completed",
      "message": "",
      "errors": []
    },
    {
      "service": "Teams",
      "status": "completed",
      "message": "",
      "errors": []
    },
    {
      "service": "Exchange",
      "status": "completed",
      "message": "",
      "errors": []
    }
  ]
}
```
