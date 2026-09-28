<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# crossTenantAccessPolicyConfigurationPartner resource type

Namespace: microsoft.graph

Represents the partner-specific configuration for cross-tenant access and tenant restrictions. Cross-tenant access settings include inbound and outbound settings of Microsoft Entra B2B collaboration and B2B direct connect.

For any partner-specific property that is `null`, these settings inherit the behavior configured in your [default cross-tenant access settings](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicy-list-partners?view=graph-rest-1.0) | [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) collection | Get a list of all partner-specific configurations. |
| [Create](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicy-post-partners?view=graph-rest-1.0) | [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) | Create a new partner-specific configuration. |
| [Get](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-get?view=graph-rest-1.0) | [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) | Read the partner-specific configuration settings. |
| [Update](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-update?view=graph-rest-1.0) | [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) | Update the properties of a partner-specific configuration. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-delete?view=graph-rest-1.0) | None | Delete the partner-specific configuration. |
| [List Microsoft 365 capabilities](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-list-m365capabilities?view=graph-rest-1.0) | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) collection | Get a list of Microsoft 365 cross-tenant capabilities configured for a partner organization in the [cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy-overview?view=graph-rest-1.0). |
| [Create Microsoft 365 capability](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-post-m365capabilities?view=graph-rest-1.0) | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) | Create a new Microsoft 365 cross-tenant capability for a partner organization in the [cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy-overview?view=graph-rest-1.0). |
| [Update Microsoft 365 capability](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-update-m365capabilities?view=graph-rest-1.0) | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) | Update an existing Microsoft 365 cross-tenant capability for a partner organization in the [cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy-overview?view=graph-rest-1.0). |
| [Delete Microsoft 365 capability](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicyconfigurationpartner-delete-m365capabilities?view=graph-rest-1.0) | None | Delete a Microsoft 365 cross-tenant capability from a partner organization in the [cross-tenant access policy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy-overview?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appServiceConnectInbound | [crossTenantAccessPolicyAppServiceConnectSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyappserviceconnectsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for inbound app service connect settings that control which applications can connect across tenant boundaries with the partner organization. |
| automaticUserConsentSettings | [inboundOutboundPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/inboundoutboundpolicyconfiguration?view=graph-rest-1.0) | Determines the partner-specific configuration for automatic user consent settings. Unless specifically configured, the **inboundAllowed** and **outboundAllowed** properties are `null` and inherit from the default settings, which is always `false`. |
| b2bCollaborationInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. |
| b2bCollaborationOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. |
| b2bDirectConnectInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Azure B2B direct connect. |
| b2bDirectConnectOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. |
| inboundTrust | [crossTenantAccessPolicyInboundTrust](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyinboundtrust?view=graph-rest-1.0) | Determines the partner-specific configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. |
| isInMultiTenantOrganization | Boolean | Identifies whether a tenant is a member of a multitenant organization. |
| isServiceProvider | Boolean | Identifies whether the partner-specific configuration is a Cloud Service Provider for your organization. |
| m365CollaborationInbound | [crossTenantAccessPolicyM365CollaborationInboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationinboundsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for inbound Microsoft 365 collaboration settings that determine which users from the partner organization can collaborate with your organization using Microsoft 365 apps. |
| m365CollaborationOutbound | [crossTenantAccessPolicyM365CollaborationOutboundSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicym365collaborationoutboundsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for outbound Microsoft 365 collaboration settings that determine which users in your organization can collaborate with the partner organization using Microsoft 365 apps. |
| tenantId | String | The tenant identifier for the partner Microsoft Entra organization. Read-only. Key. |
| tenantRestrictions | [crossTenantAccessPolicyTenantRestrictions](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicytenantrestrictions?view=graph-rest-1.0) | Defines the partner-specific tenant restrictions configuration for users in your organization who access a partner organization using partner supplied identities on your network or devices. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| identitySynchronization | [crossTenantIdentitySyncPolicyPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-1.0) | Defines the cross-tenant policy for the synchronization of users from a partner tenant. Use this user synchronization policy to streamline collaboration between users in a multitenant organization by automating the creation, update, and deletion of users from one tenant to another. |
| m365Capabilities | [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) collection | Defines the partner-specific Microsoft 365 cross-tenant capabilities for inbound access from the partner organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicyConfigurationPartner",
  "appServiceConnectInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyAppServiceConnectSetting"},
  "automaticUserConsentSettings": {"@odata.type": "microsoft.graph.inboundOutboundPolicyConfiguration"},
  "b2bCollaborationInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "b2bCollaborationOutbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "b2bDirectConnectInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "b2bDirectConnectOutbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"},
  "inboundTrust": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyInboundTrust"},
  "isInMultiTenantOrganization": "Boolean",
  "isServiceProvider": "Boolean",
  "m365CollaborationInbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyM365CollaborationInboundSetting"},
  "m365CollaborationOutbound": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyM365CollaborationOutboundSetting"},
  "tenantId": "String (identifier)",
  "tenantRestrictions": {"@odata.type": "microsoft.graph.crossTenantAccessPolicyTenantRestrictions"}
}
```
