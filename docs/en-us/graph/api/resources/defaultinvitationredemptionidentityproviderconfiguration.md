<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/defaultinvitationredemptionidentityproviderconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# defaultInvitationRedemptionIdentityProviderConfiguration resource type

Namespace: microsoft.graph

Defines the invitation redemption provider configuration to set redemption flow settings for Microsoft Entra ID B2B collaboration.

Inherits from [invitationRedemptionIdentityProviderConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/invitationredemptionidentityproviderconfiguration?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| primaryIdentityProviderPrecedenceOrder | b2bIdentityProvidersType collection | Collection of identity providers in priority order of preference to be used for guest invitation redemption. The possible values are: `azureActiveDirectory`, `externalFederation`, or `socialIdentityProviders`. |
| fallbackIdentityProvider | b2bIdentityProvidersType | The fallback identity provider to be used in case no primary identity provider can be used for guest invitation redemption. The possible values are: `defaultConfiguredIdp`, `emailOneTimePasscode`, or `microsoftAccount`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "primaryIdentityProviderPrecedenceOrder": ["String"],
  "fallbackIdentityProvider": "String"
}
```
