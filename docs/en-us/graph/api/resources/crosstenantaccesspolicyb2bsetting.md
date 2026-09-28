<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# crossTenantAccessPolicyB2BSetting resource type

Namespace: microsoft.graph

Defines the inbound and outbound rulesets for Microsoft Entra B2B collaboration.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applications | [crossTenantAccessPolicyTargetConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0) | The list of applications targeted with your cross-tenant access policy. |
| usersAndGroups | [crossTenantAccessPolicyTargetConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0) | The list of users and groups targeted with your cross-tenant access policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyB2BSetting",
  "applications": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"
  },
  "usersAndGroups": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"
  }
}
```
