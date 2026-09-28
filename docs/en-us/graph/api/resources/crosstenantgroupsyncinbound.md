<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantgroupsyncinbound?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# crossTenantGroupSyncInbound resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines whether groups can be synchronized from a partner tenant, as defined in the **groupSyncInbound** property of [crossTenantIdentitySyncPolicyPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-beta) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isSyncAllowed | Boolean | Defines whether group objects should be synchronized from the partner tenant. `false` stops any current group synchronization from the source tenant to the target tenant. This property has no impact on existing groups that were synchronized. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantGroupSyncInbound",
  "isSyncAllowed": "Boolean"
}
```
