<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitycontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# identityContainer resource type

Namespace: microsoft.graph

Represents the entry point to different features in [External Identities](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/) for both Microsoft Entra ID and Azure AD B2C tenants.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| apiConnectors | [identityApiConnector](https://learn.microsoft.com/en-us/graph/api/resources/identityapiconnector?view=graph-rest-1.0) collection | Represents entry point for API connectors. |
| authenticationEventsFlows | [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow?view=graph-rest-1.0) collection | Represents the entry point for self-service sign-up and sign-in user flows in both Microsoft Entra workforce and external tenants. |
| authenticationEventListeners | [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener?view=graph-rest-1.0) collection | Represents listeners for custom authentication extension events in Azure AD for workforce and customers. |
| b2xUserFlows | [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow?view=graph-rest-1.0) collection | Represents entry point for B2X/self-service sign-up identity userflows. |
| conditionalAccess | [conditionalAccessRoot](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessroot?view=graph-rest-1.0) collection | the entry point for the Conditional Access \(CA\) object model. |
| customAuthenticationExtensions | [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) collection | Represents custom extensions to authentication flows in Azure AD for workforce and customers. |
| identityProvider | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0) collection | Represents entry point for identity provider base. |
| userFlowAttributes | [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0) collection | Represents entry point for identity userflow attributes. |
| riskPrevention | [riskPreventionContainer](https://learn.microsoft.com/en-us/graph/api/resources/riskpreventioncontainer?view=graph-rest-1.0) | Represents the entry point for fraud and risk prevention configurations in Microsoft Entra External ID, including third-party provider settings. |
| verifiedId | [identityVerifiedIdRoot](https://learn.microsoft.com/en-us/graph/api/resources/identityverifiedidroot?view=graph-rest-1.0) | Entry point for verified ID operations. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityContainer"
}
```
