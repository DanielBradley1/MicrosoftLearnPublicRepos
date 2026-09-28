<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationpartnerconfigurationtemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# multiTenantOrganizationPartnerConfigurationTemplate resource type

Namespace: microsoft.graph

Defines an optional cross-tenant access policy template with inbound and outbound partner configuration settings for multitenant organization tenants. Each tenant has its own template. For more information, see [crossTenantAccessPolicyConfigurationPartner resource type](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0).

- If your tenant is joining a multitenant organization, the template is applicable to the partner configuration settings for all multitenant organization tenants.
- If another tenant joins your multitenant organization, the template is applicable only to the partner configuration settings of the newly joined multitenant organization tenant.

Whether the template is applied to the partner configuration settings of relevant tenants is configurable with the `templateApplicationLevel` property.

- If the template is configured to apply, it's only applied to partner configuration properties where the corresponding template property has a non-null value.

In its default and unconfigured state, where all template properties \(other than `templateApplicationLevel`\) are null, the template has no effect on partner configuration settings.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationpartnerconfigurationtemplate-get?view=graph-rest-1.0) | [multiTenantOrganizationPartnerConfigurationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationpartnerconfigurationtemplate?view=graph-rest-1.0) | Get the inbound and outbound partner configuration settings of the template. |
| [Update](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationpartnerconfigurationtemplate-update?view=graph-rest-1.0) | [multiTenantOrganizationPartnerConfigurationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationpartnerconfigurationtemplate?view=graph-rest-1.0) | Update the inbound and outbound partner configuration settings of the template. |
| [Reset](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationpartnerconfigurationtemplate-resettodefaultsettings?view=graph-rest-1.0) | None | Reset the inbound and outbound partner configuration settings of the template to the default values. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the template. Key. |
| automaticUserConsentSettings | [inboundOutboundPolicyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/inboundoutboundpolicyconfiguration?view=graph-rest-1.0) | Determines the partner-specific configuration for automatic user consent settings. Unless configured, the **inboundAllowed** and **outboundAllowed** properties are `null` and inherit from the default settings, which is always `false`. |
| b2bCollaborationInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. |
| b2bCollaborationOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. |
| b2bDirectConnectInbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users from other organizations accessing your resources via Azure B2B direct connect. |
| b2bDirectConnectOutbound | [crossTenantAccessPolicyB2BSetting](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyb2bsetting?view=graph-rest-1.0) | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. |
| inboundTrust | [crossTenantAccessPolicyInboundTrust](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyinboundtrust?view=graph-rest-1.0) | Determines the partner-specific configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. |
| templateApplicationLevel | templateApplicationLevel | Specifies whether the template will be applied to partner configuration settings of certain tenants. The possible values are: `none`, `newPartners`, `existingPartners`, `unknownFutureValue`. You can also specify multiple values like `newPartners,existingPartners` \(default\). `none` indicates the template isn't applied to any new or existing partner tenants. `newPartners` indicates the template is applied to new partner tenants. `existingPartners` indicates the template is applied to existing partner tenants, those who already had partner-specific partner configurations in place. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantOrganizationPartnerConfigurationTemplate",
  "inboundTrust": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyInboundTrust"
  },
  "b2bCollaborationOutbound": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"
  },
  "b2bCollaborationInbound": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"
  },
  "b2bDirectConnectOutbound": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"
  },
  "b2bDirectConnectInbound": {
    "@odata.type": "microsoft.graph.crossTenantAccessPolicyB2BSetting"
  },
  "automaticUserConsentSettings": {
    "@odata.type": "microsoft.graph.inboundOutboundPolicyConfiguration"
  },
  "templateApplicationLevel": "String"
}
```
