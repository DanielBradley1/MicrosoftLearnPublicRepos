<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationinboundsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# crossTenantAccessPolicyM365CollaborationInboundSetting resource type

Namespace: microsoft.graph

Represents the inbound Microsoft 365 collaboration settings for a cross-tenant access policy that specify which users from external organizations can collaborate with your organization using Microsoft 365 apps.

This resource is used by the **m365CollaborationInbound** property of the [crossTenantAccessPolicyConfigurationDefault](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0) and [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| users | [crossTenantAccessPolicyTargetConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0) | Defines the target users from other organizations who are allowed inbound Microsoft 365 collaboration with your organization. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyM365CollaborationInboundSetting",
  "users": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"
  }
}
```
