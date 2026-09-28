<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationoutboundsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# crossTenantAccessPolicyM365CollaborationOutboundSetting resource type

Namespace: microsoft.graph

Represents the outbound Microsoft 365 collaboration settings for a cross-tenant access policy that specify which users in your organization can collaborate with external organizations using Microsoft 365 apps.

This resource is used by the **m365CollaborationOutbound** property of the [crossTenantAccessPolicyConfigurationDefault](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0) and [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| usersAndGroups | [crossTenantAccessPolicyTargetConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytargetconfiguration?view=graph-rest-1.0) | Defines the target users and groups in your organization who are allowed outbound Microsoft 365 collaboration with external organizations. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyM365CollaborationOutboundSetting",
  "usersAndGroups": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyTargetConfiguration"
  }
}
```
