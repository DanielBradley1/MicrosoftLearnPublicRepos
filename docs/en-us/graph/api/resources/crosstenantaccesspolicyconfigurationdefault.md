<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# crossTenantAccessPolicyConfigurationDefault resource type

Namespace: microsoft.graph

Represents the default configuration for cross-tenant access and tenant restrictions. Cross-tenant access settings include inbound and outbound settings of Microsoft Entra B2B collaboration and B2B direct connect.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationdefault-get?view=graph-rest-1.0) | [crossTenantAccessPolicyConfigurationDefault](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0) | Get the default configuration for B2B collaboration and B2B direct connect inbound and outbound settings. |
| [Update](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationdefault-update?view=graph-rest-1.0) | None | Update the default configuration for B2B collaboration and B2B direct connect inbound and outbound settings. |
| [Reset to system default](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationdefault-resettosystemdefault?view=graph-rest-1.0) | None | Reset the default configuration for a cross-tenant access policy to the system default settings. |
| [List Microsoft 365 capabilities](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationdefault-list-m365capabilities?view=graph-rest-1.0) | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) collection | Get a list of Microsoft 365 cross-tenant capabilities configured for the [default cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0). |
| [Create Microsoft 365 capability](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationdefault-post-m365capabilities?view=graph-rest-1.0) | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) | Create a new Microsoft 365 cross-tenant capability for the [default cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0). |
| [Update Microsoft 365 capability](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationdefault-update-m365capabilities?view=graph-rest-1.0) | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) | Update an existing Microsoft 365 cross-tenant capability for the [default cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appServiceConnectInbound | [crossTenantAccessPolicyAppServiceConnectSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyappserviceconnectsetting?view=graph-rest-1.0) | Defines your default configuration for inbound app service connect settings that control which applications can connect across tenant boundaries. |
| automaticUserConsentSettings | [inboundOutboundPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/inboundoutboundpolicyconfiguration?view=graph-rest-1.0) | Determines the default configuration for automatic user consent settings. The **inboundAllowed** and **outboundAllowed** properties are always `false` and can't be updated in the default configuration. Read-only. |
| b2bCollaborationInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. |
| b2bCollaborationOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. |
| b2bDirectConnectInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users from other organizations accessing your resources via Microsoft Entra B2B direct connect. |
| b2bDirectConnectOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your default configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. |
| inboundTrust | [crossTenantAccessPolicyInboundTrust](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyinboundtrust?view=graph-rest-1.0) | Determines the default configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. |
| invitationRedemptionIdentityProviderConfiguration | [defaultInvitationRedemptionIdentityProviderConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/defaultinvitationredemptionidentityproviderconfiguration?view=graph-rest-1.0) | Defines the priority order based on which an identity provider is selected during invitation redemption for a guest user. |
| isServiceDefault | Boolean | If `true`, the default configuration is set to the system default configuration. If `false`, the default settings are customized. |
| m365CollaborationInbound | [crossTenantAccessPolicyM365CollaborationInboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationinboundsetting?view=graph-rest-1.0) | Defines your default configuration for inbound Microsoft 365 collaboration settings that determine which users from other organizations can collaborate with your organization using Microsoft 365 apps. |
| m365CollaborationOutbound | [crossTenantAccessPolicyM365CollaborationOutboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationoutboundsetting?view=graph-rest-1.0) | Defines your default configuration for outbound Microsoft 365 collaboration settings that determine which users in your organization can collaborate with other organizations using Microsoft 365 apps. |
| tenantRestrictions | [crossTenantAccessPolicyTenantRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytenantrestrictions?view=graph-rest-1.0) | Defines the default tenant restrictions configuration for users in your organization who access an external organization on your network or devices. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| m365Capabilities | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) collection | Defines the default Microsoft 365 cross-tenant capabilities for inbound access from external organizations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyConfigurationDefault",
  "appServiceConnectInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyAppServiceConnectSetting"},
  "automaticUserConsentSettings": {"@odata.type": "microsoft.graph.inboundOutboundPolicyConfiguration"},
  "b2bCollaborationInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "b2bCollaborationOutbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "b2bDirectConnectInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "b2bDirectConnectOutbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "inboundTrust": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyInboundTrust"},
  "invitationRedemptionIdentityProviderConfiguration": {"@odata.type": "microsoft.graph.defaultInvitationRedemptionIdentityProviderConfiguration"},
  "isServiceDefault": "Boolean",
  "m365CollaborationInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyM365CollaborationInboundSetting"},
  "m365CollaborationOutbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyM365CollaborationOutboundSetting"},
  "tenantRestrictions": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyTenantRestrictions"}
}
```
