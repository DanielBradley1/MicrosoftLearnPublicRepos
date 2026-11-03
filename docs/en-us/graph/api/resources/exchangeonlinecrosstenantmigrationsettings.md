<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/exchangeonlinecrosstenantmigrationsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# exchangeOnlineCrossTenantMigrationSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Settings used when migrating Exchange Online content during a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| sourceEndpoint | String | Name of the Migration Endpoint in the source tenant |
| targetDeliveryDomain | String | Delivery domain on the target tenant |

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
