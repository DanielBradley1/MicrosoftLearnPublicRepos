<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policyroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# policyRoot resource type

Namespace: microsoft.graph

Resource type exposing navigation properties for the policies singleton. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activityBasedTimeoutPolicies | [activityBasedTimeoutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/activitybasedtimeoutpolicy?view=graph-rest-1.0) collection | The policy that controls the idle time out for web sessions for applications. |
| adminConsentRequestPolicy | [adminConsentRequestPolicy](https://learn.microsoft.com/en-us/graph/api/resources/adminconsentrequestpolicy?view=graph-rest-1.0) | The policy by which consent requests are created and managed for the entire tenant. |
| appManagementPolicies | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) collection | The policies that enforce app management restrictions for specific applications and service principals, overriding the defaultAppManagementPolicy. |
| authenticationFlowsPolicy | [authenticationFlowsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationflowspolicy?view=graph-rest-1.0) | The policy configuration of the self-service sign-up experience of external users. |
| authenticationMethodsPolicy | [authenticationMethodsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicy?view=graph-rest-1.0) | The authentication methods and the users that are allowed to use them to sign in and perform multifactor authentication \(MFA\) in Microsoft Entra ID. |
| authenticationStrengthPolicies | [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) collection | The authentication method combinations that are to be used in scenarios defined by Microsoft Entra Conditional Access. |
| authorizationPolicy | [authorizationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authorizationpolicy?view=graph-rest-1.0) collection | The policy that controls Microsoft Entra authorization settings. |
| claimsMappingPolicies | [claimsMappingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0) collection | The claim-mapping policies for WS-Fed, SAML, OAuth 2.0, and OpenID Connect protocols, for tokens issued to a specific application. |
| conditionalAccessPolicies | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) | The custom rules that define an access scenario. |
| crossTenantAccessPolicy | [crossTenantAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-1.0) | The custom rules that define an access scenario when interacting with external Microsoft Entra tenants. |
| defaultAppManagementPolicy | [tenantAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantappmanagementpolicy?view=graph-rest-1.0) | The tenant-wide policy that enforces app management restrictions for all applications and service principals. |
| featureRolloutPolicies | [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy?view=graph-rest-1.0) collection | The feature rollout policy associated with a directory object. |
| homeRealmDiscoveryPolicies | [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0) collection | The policy to control Microsoft Entra authentication behavior for federated users. |
| identitySecurityDefaultsEnforcementPolicy | [identitySecurityDefaultsEnforcementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitysecuritydefaultsenforcementpolicy?view=graph-rest-1.0) | The policy that represents the security defaults that protect against common attacks. |
| ownerlessGroupPolicy | [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) | The policy configuration for managing groups that have lost their sole owner. |
| permissionGrantPolicies | [permissionGrantPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy?view=graph-rest-1.0) collection | The policy that specifies the conditions under which consent can be granted. |
| roleManagementPolicies | [unifiedRoleManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicy?view=graph-rest-1.0) collection | Specifies the various policies associated with scopes and roles. |
| roleManagementPolicyAssignments | [unifiedRoleManagementPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrolemanagementpolicyassignment?view=graph-rest-1.0) collection | The assignment of a role management policy to a role definition object. |
| tokenIssuancePolicies | [tokenIssuancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0) collection | The policy that specifies the characteristics of SAML tokens issued by Microsoft Entra ID. |
| tokenLifetimePolicies | [tokenLifetimePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy?view=graph-rest-1.0) collection | The policy that controls the lifetime of a JWT access token, an ID token, or a SAML 1.1/2.0 token issued by Microsoft Entra ID. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyRoot",
  "id": "String (identifier)"
}
```
