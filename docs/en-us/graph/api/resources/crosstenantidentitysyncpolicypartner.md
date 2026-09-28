<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-20 -->

# crossTenantIdentitySyncPolicyPartner resource type

Namespace: microsoft.graph

Defines the cross-tenant policy for synchronization of users from a partner tenant. Use this user synchronization policy to streamline collaboration between users in a multi-tenant organization by automating the creation, update, and deletion of users from one tenant to another.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-put-identitysynchronization?view=graph-rest-1.0) | None | Create a cross-tenant user synchronization policy for a partner-specific configuration. |
| [Get](https://learn.microsoft.com/en-us/graph/api/crosstenantidentitysyncpolicypartner-get?view=graph-rest-1.0) | [crossTenantIdentitySyncPolicyPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-1.0) | Get the user synchronization policy of a partner-specific configuration. |
| [Update](https://learn.microsoft.com/en-us/graph/api/crosstenantidentitysyncpolicypartner-update?view=graph-rest-1.0) | None | Update the user synchronization policy of a partner-specific configuration. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/crosstenantidentitysyncpolicypartner-delete?view=graph-rest-1.0) | None | Delete the user synchronization policy for a partner-specific configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name for the cross-tenant user synchronization policy. Use the name of the partner Microsoft Entra tenant to easily identify the policy. Optional. |
| tenantId | String | Tenant identifier for the partner Microsoft Entra organization. Read-only. |
| userSyncInbound | [crossTenantUserSyncInbound](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantusersyncinbound?view=graph-rest-1.0) | Defines whether users can be synchronized from the partner tenant. Key. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantIdentitySyncPolicyPartner",
  "displayName": "String",
  "tenantId": "String (identifier)",
  "userSyncInbound": {
    "@odata.type": "microsoft.graph.crossTenantUserSyncInbound"
  }
}
```
