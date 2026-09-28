<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customermfainsight?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# customerMfaInsight resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains aggregate data from the customer's Entra tenant MFA policy configuration and usage.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compliantAdminsCount | Int64 | The number of admins that are compliant with the MFA requirements |
| compliantNonAdminsCount | Int64 | The number of users that are compliant with the MFA requirements |
| legacyPerUserMfaStatus | microsoft.graph.partner.security.policyStatus | The status of per-user MFA configuration to require MFA in the tenant. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| mfaConditionalAccessPolicyStatus | microsoft.graph.partner.security.policyStatus | The status of conditional access policies to require MFA in the tenant. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| securityDefaultsStatus | microsoft.graph.partner.security.policyStatus | The status of security defaults in the tenant. The possible values are: `enabled`, `disabled`, `unknownFutureValue`. |
| totalUsersCount | Int64 | The total number of users in the tenant |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.customerMfaInsight",
  "compliantAdminsCount": "Integer",
  "compliantNonAdminsCount": "Integer",
  "totalUsersCount": "Integer",
  "securityDefaultsStatus": "String",
  "mfaConditionalAccessPolicyStatus": "String",
  "legacyPerUserMfaStatus": "String"
}
```
