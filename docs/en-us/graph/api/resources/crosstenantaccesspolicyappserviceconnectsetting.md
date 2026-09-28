<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyappserviceconnectsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# crossTenantAccessPolicyAppServiceConnectSetting resource type

Namespace: microsoft.graph

Represents the inbound app service connect settings for a cross-tenant access policy that specify which applications can connect across tenant boundaries.

This resource is used by the **appServiceConnectInbound** property of the [crossTenantAccessPolicyConfigurationDefault](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0) and [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applications | [crossTenantAccessPolicyTargetConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0) | Defines the target applications that are allowed for inbound app service connect across tenant boundaries. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyAppServiceConnectSetting",
  "applications": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"
  }
}
```
