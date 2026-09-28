<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyinboundtrust?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-26 -->

# crossTenantAccessPolicyInboundTrust resource type

Namespace: microsoft.graph

Defines the Conditional Access claims you want to accept from other Microsoft Entra organizations via your cross-tenant access policy configuration. These can be configured in your default configuration, partner-specific configuration, or both.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isCompliantDeviceAccepted | Boolean | Specifies whether compliant devices from external Microsoft Entra organizations are trusted. |
| isHybridAzureADJoinedDeviceAccepted | Boolean | Specifies whether Microsoft Entra hybrid joined devices from external Microsoft Entra organizations are trusted. |
| isMfaAccepted | Boolean | Specifies whether MFA from external Microsoft Entra organizations is trusted. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyInboundTrust",
  "isCompliantDeviceAccepted": "Boolean",
  "isHybridAzureADJoinedDeviceAccepted": "Boolean",
  "isMfaAccepted": "Boolean"
}
```
