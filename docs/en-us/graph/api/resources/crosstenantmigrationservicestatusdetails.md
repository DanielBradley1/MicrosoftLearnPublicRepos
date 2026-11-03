<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationservicestatusdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# crossTenantMigrationServiceStatusDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the status and details of a migration done as part of a [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errors | [error](https://learn.microsoft.com/en-us/graph/api/resources/error?view=graph-rest-beta) collection | Errors associated with the migration for this service |
| message | String | Service status message |
| service | String | Service or workload the status details are associated with |
| status | crossTenantMigrationServiceStatus | Status of the migration for the service. The possible values are: `notStarted`, `valid`, `invalid`, `error`, `inProgress`, `completed`, `failed`, `cancelled`, `pendingCancel`, `syncing`, `synced`, `finalizing`, and `forceComplete`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantMigrationServiceStatusDetails",
  "service": "String",
  "status": "String",
  "message": "String",
  "errors": [
    {
      "@odata.type": "microsoft.graph.error"
    }
  ]
}
```
