<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationcancelresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# crossTenantMigrationCancelResponse resource type

Namespace: microsoft.graph

Contains the result of a request to cancel a cross-tenant migration job or task.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| message | String | The description of the cancellation request. |
| status | String | The cancellation request status. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantMigrationCancelResponse",
  "message": "String",
  "status": "String"
}
```
