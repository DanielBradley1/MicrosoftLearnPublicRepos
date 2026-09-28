<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantrelationshipaccesspolicybase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# tenantRelationshipAccessPolicyBase resource type

Namespace: microsoft.graph

The base type that defines a tenant relationship. This is an abstract type that's inherited by cross-tenant policy objects including [crossTenantAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-1.0).

Inherits from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definition \(deprecated\) | String collection | The raw JSON definition of the cross-tenant access policy. **Deprecated. Do not use.** |
| description | String | Description for this policy. Required. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| displayName | String collection | Display name for this policy. Required. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantRelationshipAccessPolicyBase",
  "definition": [
    "String"
  ],
  "description": "String",
  "displayName": "String"
}
```
