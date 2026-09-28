<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partner-security-customersmfaenforcedsecurityrequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-31 -->

# customersMfaEnforcedSecurityRequirement resource type

Namespace: microsoft.graph.partner.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This resource represents the customer MFA-enforced security requirement in the partner security score based on aggregate data from the partner's customers and their mfa policy compliance.

Inherits from [microsoft.graph.partner.security.securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionUrl | String | The link to the site where the admin can take action on the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| complianceStatus | microsoft.graph.partner.security.complianceStatus | Indicates whether the partner is compliant with this requirement. Inherited from securityRequirement\]\(../resources/partner-security-securityrequirement.md\). The possible values are: `compliant`, `noncomplaint`, `unknownFutureValue`. |
| compliantTenantCount | Int64 | The number of customer tenants that are compliant. |
| helpUrl | String | The link to documentation for the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| id | String | The unique identifier for the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| maxScore | Int64 | The maximum score possible for the requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| requirementType | microsoft.graph.partner.security.securityRequirementType | The value of this property is always `mfaEnforcedForAdminsOfCustomers` for this resource. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). The possible values are: `mfaEnforcedForAdmins`, `mfaEnforcedForAdminsOfCustomers`, `securityAlertsPromptlyResolved`, `securityContactProvided`, `spendingBudgetSetForCustomerAzureSubscriptions`, `unknownFutureValue`. |
| score | Int64 | The score received for this requirement. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |
| state | microsoft.graph.partner.security.securityRequirementState | Indicates whether the requirement is in preview or is fully released. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). The possible values are: `active`, `preview`, `unknownFutureValue`. |
| totalTenantCount | Int64 | The total number of customer tenants associated with this partner |
| updatedDateTime | DateTimeOffset | The date the requirement properties were last updated. Inherited from [securityRequirement](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-securityrequirement?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partner.security.customersMfaEnforcedSecurityRequirement",
  "id": "String (identifier)",
  "requirementType": "String",
  "complianceStatus": "String",
  "actionUrl": "String",
  "helpUrl": "String",
  "score": "Integer",
  "maxScore": "Integer",
  "state": "String",
  "updatedDateTime": "String (timestamp)",
  "totalTenantCount": "Integer",
  "compliantTenantCount": "Integer"
}
```
