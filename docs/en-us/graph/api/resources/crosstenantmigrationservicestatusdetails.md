<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationservicestatusdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# crossTenantMigrationServiceStatusDetails resource type

Namespace: microsoft.graph

Represents the status of a workload that participates in a [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errors | [error](https://learn.microsoft.com/en-us/graph/api/resources/error?view=graph-rest-1.0) collection | Errors associated with the migration for this service. |
| message | String | Service status message. |
| service | String | Service or workload associated with the status details. |
| status | crossTenantMigrationServiceStatus | Status of the migration for the service. The possible values are: `notStarted`, `valid`, `invalid`, `error`, `inProgress`, `completed`, `failed`, `cancelled`, `pendingCancel`, `syncing`, `synced`, `finalizing`, `forceComplete`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantMigrationServiceStatusDetails",
  "errors": [
    {
      "@odata.type": "microsoft.graph.error"
    }
  ],
  "message": "String",
  "service": "String",
  "status": "String"
}
```
