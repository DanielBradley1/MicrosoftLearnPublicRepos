<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/reference-oidc-extensibility -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Microsoft identity platform OIDC extensibility reference

Use this reference to find every supported way to extend Microsoft identity platform OpenID Connect \(OIDC\) behavior. Each row links to the concept or how-to article in this repo and to the Microsoft Graph API resource that programs the surface.

Extensibility refers to changing how Microsoft Entra issues OIDC tokens or processes OIDC requests for apps you own — for example, adding claims from an external store, customizing token contents per app, or trusting tokens from external workload identities. Configuring an existing OIDC app \(such as GitHub, Salesforce, or another SaaS app\) to use Microsoft Entra for sign-in is *integration*, not extensibility. For app integration guidance, see [Microsoft Entra application gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/overview-application-gallery).

For the underlying endpoint contracts, see [OpenID Connect on the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols-oidc).

## Extensibility surfaces at a glance

| Capability | What it lets you do | Concept and how-to | Microsoft Graph API |
| --- | --- | --- | --- |
| Custom claims provider | Call an external REST API during token issuance to enrich tokens with claims from a remote store. | [Custom claims provider overview](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-overview), [Reference](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-reference) | [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension), [onTokenIssuanceStartListener](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartlistener) |
| Token issuance start event | Configure the event listener that triggers your custom claims provider during token issuance. | [Set up token issuance start event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-setup), [Configure](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration) | [onTokenIssuanceStartCustomExtension](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartcustomextension), [onTokenIssuanceStartHandler](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestarthandler), [onTokenIssuanceStartReturnClaim](https://learn.microsoft.com/en-us/graph/api/resources/ontokenissuancestartreturnclaim) |
| Optional claims | Add Microsoft Entra-sourced claims \(such as `groups`, `idtyp`, `login_hint`\) to ID, access, and SAML tokens. | [Provide optional claims to your app](https://learn.microsoft.com/en-us/entra/identity-platform/optional-claims), [Reference](https://learn.microsoft.com/en-us/entra/identity-platform/optional-claims-reference) | [optionalClaim](https://learn.microsoft.com/en-us/graph/api/resources/optionalclaim), [optionalClaims](https://learn.microsoft.com/en-us/graph/api/resources/optionalclaims) on [application](https://learn.microsoft.com/en-us/graph/api/resources/application) |
| Custom claims policy \(per-app\) | Map directory attributes to claims in tokens issued for a specific app, including transformations. | [JWT claims customization](https://learn.microsoft.com/en-us/entra/identity-platform/jwt-claims-customization), [SAML claims customization](https://learn.microsoft.com/en-us/entra/identity-platform/saml-claims-customization), [Custom claims policy](https://learn.microsoft.com/en-us/entra/identity-platform/claims-customization-custom-claims-policy) | [customClaimsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/customclaimspolicy), [claimsMappingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy) |
| Token lifetime policy | Configure access, refresh, and ID token lifetimes for an app or tenant. | [Configurable token lifetimes](https://learn.microsoft.com/en-us/entra/identity-platform/configurable-token-lifetimes), [Configure](https://learn.microsoft.com/en-us/entra/identity-platform/configure-token-lifetimes) | [tokenLifetimePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy) |
| Token issuance policy | Configure SAML token signing and encryption behavior at issuance. | [SAML claims customization](https://learn.microsoft.com/en-us/entra/identity-platform/saml-claims-customization) | [tokenIssuancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy) |
| Federated identity credentials | Trust tokens from external issuers \(GitHub, Kubernetes, other clouds\) instead of using a client secret or certificate. | [Workload identity federation](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation) | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential), [Federated identity credentials overview](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredentials-overview) |
| Application manifest | Declaratively configure redirect URIs, audiences, allowed grant types, and token settings. | [Application manifest reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-app-manifest) | [application](https://learn.microsoft.com/en-us/graph/api/resources/application), [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal) |
| Delegated permission grants | Authorize delegated scopes for a user or tenant. | [Permissions and consent overview](https://learn.microsoft.com/en-us/entra/identity-platform/permissions-consent-overview) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant) |
| App role assignments | Assign app roles to users, groups, or service principals for token-based authorization. | [App roles overview](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment) |
| Continuous access evaluation \(CAE\) | Enable token revocation in near real time for events such as user sign-out, password change, and risk detection. | [Continuous access evaluation](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation) | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy) |
| Claims challenge \(step-up\) | Request stronger authentication or fresher claims mid-session. | [Claims challenges](https://learn.microsoft.com/en-us/entra/identity-platform/claims-challenge), [Claims validation](https://learn.microsoft.com/en-us/entra/identity-platform/claims-validation) | N/A \(protocol-level; signaled in the `claims` request parameter\) |

## Choosing an extensibility surface

Use the following guidance to decide which surface fits your scenario:

- To add claims **sourced from Microsoft Entra ID**, use [optional claims](https://learn.microsoft.com/en-us/entra/identity-platform/optional-claims) or a [custom claims policy](https://learn.microsoft.com/en-us/entra/identity-platform/claims-customization-custom-claims-policy).
- To add claims **sourced from an external system**, use a [custom claims provider](https://learn.microsoft.com/en-us/entra/identity-platform/custom-claims-provider-overview) backed by an Azure Functions endpoint or other REST API.
- To **trust an external workload identity** instead of using a client secret or certificate, configure a [federated identity credential](https://learn.microsoft.com/en-us/entra/workload-id/workload-identity-federation).
- To **react to security events** \(revoked sessions, risk changes, password resets\) on existing tokens, enable [continuous access evaluation](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation).
- To **request fresher authentication** during a session, issue a [claims challenge](https://learn.microsoft.com/en-us/entra/identity-platform/claims-challenge).

## Programming model

Most surfaces in the table are configured through the [Microsoft Graph application](https://learn.microsoft.com/en-us/graph/api/resources/application) and [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal) resources or through the `policies` endpoint. Authentication libraries don't configure these surfaces; use Microsoft Graph SDKs, the [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview), or direct REST calls.

For an end-to-end example that combines a custom authentication extension with a token issuance start event, see [Configure a custom claim provider with a token issuance start event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration).

## Related content

- [OpenID Connect on the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols-oidc)
- [Application manifest reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-app-manifest)
- [Microsoft Graph application resource](https://learn.microsoft.com/en-us/graph/api/resources/application)
