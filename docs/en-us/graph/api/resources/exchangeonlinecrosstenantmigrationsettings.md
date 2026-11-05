<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exchangeonlinecrosstenantmigrationsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# exchangeOnlineCrossTenantMigrationSettings resource type

Namespace: microsoft.graph

Contains Exchange Online settings for a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sourceEndpoint | String | Name of the migration endpoint in the source tenant. |
| targetDeliveryDomain | String | Delivery domain on the target tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.exchangeOnlineCrossTenantMigrationSettings",
  "sourceEndpoint": "String",
  "targetDeliveryDomain": "String"
}
```
