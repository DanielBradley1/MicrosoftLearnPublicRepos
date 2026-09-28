<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationrequirementpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# authenticationRequirementPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Microsoft Entra ID can require users to pass an MFA check before accessing resources. If an MFA check is required, this resource identifies the policy that requires MFA. This object is configured in the **authenticationRequirementPolicies** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| detail | String | Provides additional detail on the feature identified in requirementProvider. |
| requirementProvider | requirementProvider | Identifies what Microsoft Entra feature requires MFA in this policy. The possible values are: `user`, `request`, `servicePrincipal`, `v1ConditionalAccess`, `multiConditionalAccess`, `tenantSessionRiskPolicy`, `accountCompromisePolicies`, `v1ConditionalAccessDependency`, `v1ConditionalAccessPolicyIdRequested`, `mfaRegistrationRequiredByIdentityProtectionPolicy`, `baselineProtection`, `mfaRegistrationRequiredByBaselineProtection`, `mfaRegistrationRequiredByMultiConditionalAccess`, `enforcedForCspAdmins`, `securityDefaults`, `mfaRegistrationRequiredBySecurityDefaults`, `proofUpCodeRequest`, `crossTenantOutboundRule`, `gpsLocationCondition`, `riskBasedPolicy`, `unknownFutureValue`, `scopeBasedAuthRequirementPolicy`, `authenticationStrengths` . Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `scopeBasedAuthRequirementPolicy`, `authenticationStrengths`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationRequirementPolicy",
  "requirementProvider": "String",
  "detail": "String"
}
```
