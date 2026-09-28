<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantusersyncinbound?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# crossTenantUserSyncInbound resource type

Namespace: microsoft.graph

Defines whether users can be synchronized from the partner tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isSyncAllowed | Boolean | Defines whether user objects should be synchronized from the partner tenant. `false` causes any current user synchronization from the source tenant to the target tenant to stop. This property has no impact on existing users who have already been synchronized. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantUserSyncInbound",
  "isSyncAllowed": "Boolean"
}
```
