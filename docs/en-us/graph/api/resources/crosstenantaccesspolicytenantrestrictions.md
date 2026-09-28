<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytenantrestrictions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-21 -->

# crossTenantAccessPolicyTenantRestrictions resource type

Namespace: microsoft.graph

Defines how to target your tenant restrictions settings. Tenant restrictions give you control over the external organizations that your users can access from your network or devices when they use external identities. Settings can be targeted to specific users, groups, or applications.

Inherits from [crossTenantAccessPolicyB2BSettings](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applications | [crossTenantAccessPolicyTargetConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0) | The list of applications targeted with your cross-tenant access policy. Inherited from [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0). |
| devices | [devicesFilter](https://learn.microsoft.com/en-us/graph/api/resources/devicesfilter?view=graph-rest-1.0) | Defines the rule for filtering devices and whether devices that satisfy the rule should be allowed or blocked. This property isn't supported on the server side yet. |
| usersAndGroups | [crossTenantAccessPolicyTargetConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0) | The list of users and groups targeted with your cross-tenant access policy. Inherited from [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyTenantRestrictions",
  "applications": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"},
  "devices": {"@odata.type": "microsoft.graph.devicesFilter"},
  "usersAndGroups": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"}
}
```

## Related content

[Set up tenant restrictions V2 \(Preview\)](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/tenant-restrictions-v2)
