<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policydeletableitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-27 -->

# policyDeletableItem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents policy types in Microsoft Entra that support soft-delete functionality. When deleted, you can restore these policies within a 30-day window, after which they are automatically and permanently deleted.

This resource is an abstract type from which the following resources inherit:

- [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-beta)
- [crossTenantIdentitySyncPolicyPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-beta)
- [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-beta)
- [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-beta)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletedDateTime | DateTimeOffset | Shows the last date and time the policy was deleted. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyDeletableItem",
  "deletedDateTime": "String (timestamp)"
}
```
