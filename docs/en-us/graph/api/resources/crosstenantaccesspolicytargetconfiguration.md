<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# crossTenantAccessPolicyTargetConfiguration resource type

Namespace: microsoft.graph

Defines the target of a cross-tenant access policy setting configuration.

This resource is used by the following properties:

- **users** property of [crossTenantAccessPolicyM365CollaborationInboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationinboundsetting?view=graph-rest-1.0)
- **usersAndGroups** property of [crossTenantAccessPolicyM365CollaborationOutboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationoutboundsetting?view=graph-rest-1.0)
- **applications** property of [crossTenantAccessPolicyAppServiceConnectSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyappserviceconnectsetting?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessType | crossTenantAccessPolicyTargetConfigurationAccessType | Defines whether access is allowed or blocked. The possible values are: `allowed`, `blocked`, `unknownFutureValue`. |
| targets | [crossTenantAccessPolicyTarget](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytarget?view=graph-rest-1.0) collection | Specifies whether to target users, groups, or applications with this rule. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyTargetConfiguration",
  "accessType": "String",
  "targets": [
    {
      "@odata.type": "microsoft.graph.crossTenantAccessPolicyTarget"
    }
  ]
}
```
